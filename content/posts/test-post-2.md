---
title: "代码测试"
date: 2024-01-20T11:00:00+08:00
lastMod: 2024-01-20T11:00:00+08:00
tags: ["编程", "Go"]
---

今天学习了 Go 语言的并发编程：

```go
func main() {
    ch := make(chan int)
    go func() {
        ch <- 42
    }()
    fmt.Println(<-ch)
}
```

Go 的 channel 机制真的很优雅！ 
为什么呢？

我理解是的