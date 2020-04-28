---
title: 用PHP实现一个简单的二叉树
date: 2018-08-05 12:00:37
tags: [php]
---

```php

class BinaryTree
{
    private $tree = null;

    public function createNode($key)
    {
        return [
            'key' => $key,
            'left' => null,
            'right' => null
        ];
    }

    public function insertNode(&$node, $new)
    {
        if ($new['key'] < $node['key']) {
            if ($node['left'] === null) {
                $node['left'] = $new;
            } else {
                $this->insertNode($node['left'], $new);
            }
        } else {
            if ($node['right'] === null) {
                $node['right'] = $new;
            } else {
                $this->insertNode($node['right'], $new);
            }
        }
    }

    public function insert($key)
    {
        $new = $this->createNode($key);
        if ($this->tree === null) {
            $this->tree = $new;
        } else {
            $this->insertNode($this->tree, $new);
        }
    }

    public function print()
    {
        var_dump($this->tree);
    }
}

$data = [6, 9, 1, 4, 5, 7, 2, 3, 8, 0];
$tree = new BinaryTree();
foreach ($data as $val) {
    $tree->insert($val);
}

$tree->print();
```
