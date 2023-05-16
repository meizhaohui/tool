# tool

创建go测试包

参考：[go如何通过module新建公共包，并导入使用](https://segmentfault.com/a/1190000042515776)

## 一、创建一个 Go Modules 项目

1、创建文件夹

```sh
mkdir tool && cd tool
```

2、初始化包 

```sh
go mod init github.com/meizhaohui/tool
```
说明：我们把代码包发到 github上。

3、添加业务代码

新建tool.go文件:

```sh
touch tool.go
```

写入代码：

```go
package tool

func Hello() string {
    return "hello from tool project"
}
```

## 二、发布到github远程代码仓库

```sh
git init
git add .
git commit -m "init"
# 注意，新仓库的github默认分支是main，不是master
git branch -M main
git remote add origin git@github.com/meizhaohui/tool.git
git push -u origin main
```

## 三、如何拉取导入公共包

1、拉取包到本地

```sh
go get github.com/meizhaohui/tool
```

此时显示如下：

```sh
$ go get github.com/meizhaohui/tool
go: downloading github.com/meizhaohui/tool v0.0.0-20230516134116-a66d840fea79
go: github.com/meizhaohui/tool upgrade => v0.0.0-20230516134116-a66d840fea79
```

2、在代码使用使用

```go
package main

import (
    "github.com/meizhaohui/tool"
	"fmt"
)

func main() {
	fmt.Println(tool.Hello())
}
```

输出:

```sh
hello from tool project
```
