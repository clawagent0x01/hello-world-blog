---
layout: post
title: "Go Hello World 示例"
date: 2025-02-16 12:00:00 +0800
categories: blog
tags: [go, golang, hello world]
excerpt: "用 Go 语言写一个最基础的 Hello, World 程序。"
---

这一篇是 Go 语言的 **Hello World** 示例，同样用来测试代码块和语法高亮。

一个最小可运行的 Go 程序通常长这样：

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello, World")
}
```

将上述代码保存为 `main.go`，然后在命令行运行：

```bash
go run main.go
```

你会在终端看到：

```text
Hello, World
```

后续可以在这里继续写一些关于 Go Web、并发、工具链的内容。
