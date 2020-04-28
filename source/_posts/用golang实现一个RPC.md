---
title: 用golang实现一个RPC
date: 2018-07-11 15:15:43
tags: go golang rpc
---

使用 golang 实现一个简单的 json rpc，提供乘除功能

### server.go

```go
package main

import (
	"fmt"
	"net"
	"net/rpc"
	"net/rpc/jsonrpc"
	"os"

	"github.com/pkg/errors"
)

type Args struct {
	A, B int
}

type Math int

type Quot struct {
	Quo, Rem int
}

func (m *Math) Multiply(args *Args, reply *int) error {
	*reply = args.A * args.B
	return nil
}

func (m *Math) Divide(args *Args, quo *Quot) error {
	if args.B == 0 {
		return errors.New("divide by zero")
	}

	quo.Quo = args.A / args.B
	quo.Rem = args.A % args.B

	return nil
}

func main() {

	math := new(Math)
	rpc.Register(math)

	tcpAddr, err := net.ResolveTCPAddr("tcp", ":1234")
	if err != nil {
		fmt.Println("Fatal error:", err)
		os.Exit(2)
	}

	listener, err := net.ListenTCP("tcp", tcpAddr)
	if err != nil {
		fmt.Println("Fatal error:", err)
		os.Exit(2)
	}

	for {
		conn, err := listener.Accept()
		if err != nil {
			fmt.Println("conn error:", err)
		}

		jsonrpc.ServeConn(conn)
	}

}
```

### client.go

```go
package main

import (
	"fmt"
	"log"
	"net/rpc/jsonrpc"
	"os"
)

type Args struct {
	A, B int
}

type Quotient struct {
	Quo, Rem int
}

func main() {
	if len(os.Args) != 2 {
		fmt.Println("usage: ", os.Args[0], "server")
		os.Exit(1)
	}

	serverAddr := os.Args[1]

	client, err := jsonrpc.Dial("tcp", serverAddr+":1234")
	if err != nil {
		log.Fatal("dialing:", err)
	}

	args := Args{27, 2}
	var reply int
	err = client.Call("Math.Multiply", args, &reply)
	if err != nil {
		log.Fatal("Math error:", err)
	}
	fmt.Printf("Math: %d * %d = %d \n", args.A, args.B, reply)

	var quo Quotient
	err = client.Call("Math.Divide", args, &quo)
	if err != nil {
		log.Fatal("Math errr:", err)
	}

	fmt.Printf("Math: %d / %d = %d ... %d \n", args.A, args.B, quo.Quo, quo.Rem)

}
```
