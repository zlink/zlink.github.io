---
title: 为Git设置代理规则
date: 2018-07-18 23:38:03
tags: [git, proxy]
---

```bash
git config --global http.proxy 'socks5://127.0.0.1:1080'

git config --global https.proxy 'socks5://127.0.0.1:1080'

// or 为单独的域名设置代理
[http "https://example.com"]
proxy = socks5://127.0.0.1:2080
```
