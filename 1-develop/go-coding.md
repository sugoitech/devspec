# 代码规范

本规范旨在为日常Go项目开发提供一个代码的规范指导，方便团队形成一个统一的代码风格，提高代码的可读性，规范性和统一性。本规范将从命名规范，注释规范，代码风格和
Go 语言提供的常用的工具这几个方面做一个说明。该规范参考了 go 语言官方代码的风格制定。

## 一、 命名规范

命名是代码规范中很重要的一部分，统一的命名规则有利于提高的代码的可读性，好的命名仅仅通过命名就可以获取到足够多的信息。

Go在命名时以字母a到Z或a到Z或下划线开头，后面跟着零或更多的字母、下划线和数字(0到9)。Go不允许在命名时中使用@、$
和%等标点符号。Go是一种区分大小写的编程语言。因此，Manpower和manpower是两个不同的命名。

> 1.当命名（包括常量、变量、类型、函数名、结构字段等等）以一个大写字母开头，如：Group1，那么使用这种形式的标识符的对象就可以被外部包的代码所使用（客户端程序需要先导入这个包），这被称为导出（像面向对象语言中的
> public）；

> 2.命名如果以小写字母开头，则对包外是不可见的，但是他们在整个包的内部是可见并且可用的（像面向对象语言中的 private ）

### 1、包命名：package

保持package的名字和目录保持一致，尽量采取有意义的包名，简短，有意义，尽量和标准库不要冲突。包名应该为小写单词，不要使用下划线或者混合大小写。

```
package demo

package main
```

### 2、 文件命名

- 尽量采取有意义的文件名，简短，有意义。
- 文件名应该为小写单词，使用下划线分隔各个单词。
- 禁止使用驼峰格式命名文件。

```
my_test.go
```

### 3、 结构体命名

- 采用驼峰命名法，首字母根据访问控制大写或者小写
- struct 申明和初始化格式采用多行，例如下面：

```
// 多行申明
type User struct{
    Username  string
    Email     string
}

// 多行初始化
u := User{
    Username: "astaxie",
    Email:    "astaxie@gmail.com",
}
```

### 4、 接口命名

- 命名规则基本和上面的结构体类型
- 单个函数的结构名以 “er” 作为后缀，例如 Reader , Writer 。

```
type Reader interface {
        Read(p []byte) (n int, err error)
}
```

### 5、变量命名

- 和结构体类似，变量名称一般遵循驼峰法，首字母根据访问控制原则大写或者小写，但遇到特有名词时，需要遵循以下规则：
- 如果变量为私有，且特有名词为首个单词，则使用小写，如 apiClient
- 其它情况都应当使用该名词原有的写法，如 APIClient、repoID、UserID
- 错误示例：UrlArray，应该写成 urlArray 或者 URLArray
- 若变量类型为 bool 类型，则名称应以 Has, Is, Can 或 Allow 开头

```
var isExist bool
var hasConflict bool
var canManage bool
var allowGitHook bool
```

### 6、常量命名

常量均需使用驼峰标准，首字母大写。比如我们起一个常量叫做app_ver，表示当前app运行的环境，我们必须要这样定义：

```
const AppVer = "1.0"
```

如果是枚举类型的常量，需要先创建相应类型：

```
type Scheme string
 
const (
    HTTP  Scheme = "http"
    HTTPS Scheme = "https"
)
```

### 7、 关键字

保留字不能用作常量或变量或任何其他标识符名称。

### 8. **函数参数和返回值命名**

- 函数参数和返回值应具有有意义的名称，避免使用单个字母（如 `x`、`y`）作为参数名。
- 如果函数有多个返回值，建议为每个返回值提供明确的名称，尤其是当其中一个返回值是错误时。

```go
func getUserByID(id int) (user User, err error) {
    // ...
}
```

### 9. **全局变量命名**

- 全局变量应尽量少用，并且需要以大写字母开头，确保其导出性。
- 全局变量应有明确的注释说明其用途和作用范围。

```go
var GlobalConfig = &config{
    // 配置信息
}
```

### 10. **临时变量命名**

- 对于循环中的临时变量，使用简短但有意义的名称，如 `i`、`j` 用于索引，`item` 用于遍历元素。

```go
for i, item := range items {
    // ...
}
```

## 二、注释

Go提供C风格的/* */块注释和C ++风格的//行注释。行注释是常态；块注释主要显示为包注释，但在表达式中很有用或禁用大量代码。

单行注释是最常见的注释形式，你可以在任何地方使用以 // 开头的单行注释
多行注释也叫块注释，均已以 /* 开头，并以 */ 结尾，且不可以嵌套使用，多行注释一般用于包的文档描述或注释成块的代码片段
go 语言自带的 godoc 工具可以根据注释生成文档，生成可以自动生成对应的网站（ http://golang.org 就是使用 godoc
工具直接生成的），注释的质量决定了生成的文档的质量。每个包都应该有一个包注释，在package子句之前有一个块注释。对于多文件包，包注释只需要存在于一个文件中，任何一个都可以。包评论应该介绍包，并提供与整个包相关的信息。它将首先出现在godoc页面上，并应设置下面的详细文档。

详细的如何写注释可以 参考：https://golang.org/doc/effective_go#commentary

### 1、包注释

每个包都应该有一个包注释，一个位于package子句之前的块注释或行注释。包如果有多个go文件，只需要出现在一个go文件中（一般是和包同名的文件）即可。
包注释应该包含下面基本信息(请严格按照这个顺序，简介，创建人，创建时间）：

- 包的基本简介（包名，简介）
- 创建者，格式： 创建人： rtx 名
- 创建时间，格式：创建时间： yyyyMMdd
- 例如 util 包的注释示例如下

```
// util 包， 该包包含了项目共用的一些常量，封装了项目中一些共用函数。
// 创建人： hanru
// 创建时间： 20190419
```

### 2、结构（接口）注释

每个自定义的结构体或者接口都应该有注释说明，该注释对结构进行简要介绍，放在结构体定义的前一行，格式为： 结构体名，
结构体说明。同时结构体内的每个成员变量都要有说明，该说明放在成员变量的后面（注意对齐），实例如下：

```
// User ， 用户对象，定义了用户的基础信息
type User struct{
    Username  string // 用户名
    Email     string // 邮箱
}
```

### 3、函数（方法）注释

每个函数，或者方法（结构体或者接口下的函数称为方法）都应该有注释说明，函数的注释应该包括三个方面（严格按照此顺序撰写）：

简要说明，格式说明：以函数名开头，“，”分隔说明部分
参数列表：每行一个参数，参数名开头，“，”分隔说明部分
返回值： 每行一个返回值
示例如下：

```
// NewtAttrModel ， 属性数据层操作类的工厂方法
// 参数：
//      ctx ： 上下文信息
// 返回值：
//      属性操作类指针
func NewAttrModel(ctx *common.Context) *AttrModel {
}
```

### 4、代码逻辑注释

对于一些关键位置的代码逻辑，或者局部较为复杂的逻辑，需要有相应的逻辑说明，方便其他开发者阅读该段代码，实例如下：

```
// 从 Redis 中批量读取属性，对于没有读取到的 id ， 记录到一个数组里面，准备从 DB 中读取
xxxxx
xxxxxxx
xxxxxxx
```

### 5、注释风格

统一使用中文注释，对于中英文字符之间严格使用空格分隔， 这个不仅仅是中文和英文之间，英文和中文标点之间也都要使用空格分隔，例如：

```
// 从 Redis 中批量读取属性，对于没有读取到的 id ， 记录到一个数组里面，准备从 DB 中读取
上面 Redis 、 id 、 DB 和其他中文字符之间都是用了空格分隔。
```

- 建议全部使用单行注释
- 和代码的规范一样，单行注释不要过长，禁止超过 120 字符。

### 6. **代码块注释**

- 对于复杂的逻辑或算法，可以在代码块前添加详细的注释，解释其工作原理和预期行为。

```go
// 计算斐波那契数列的第 n 项
// 使用递归方式实现，适用于较小的 n 值
func fibonacci(n int) int {
    if n <= 1 {
        return n
    }
    return fibonacci(n-1) + fibonacci(n-2)
}
```

### 7. **TODO 注释**

- 使用 `TODO` 标记未来需要处理的任务或潜在问题。格式为：`TODO(username): description`。

```go
// TODO(hanru): 改进性能，优化查询逻辑
```

## 三、代码风格

### 1、缩进和折行

- 缩进直接使用 gofmt 工具格式化即可（gofmt 是使用 tab 缩进的）；
- 折行方面，一行最长不超过120个字符，超过的请使用换行展示，尽量保持格式优雅。
  我们使用Goland开发工具，可以直接使用快捷键：ctrl+alt+L，即可。

### 2、语句的结尾

Go语言中是不需要类似于Java需要冒号结尾，默认一行就是一条数据

如果你打算将多个语句写在同一行，它们则必须使用 ;

### 3、括号和空格

括号和空格方面，也可以直接使用 gofmt 工具格式化（go 会强制左大括号不换行，换行会报语法错误），所有的运算符和操作数之间要留空格。

```
// 正确的方式
if a > 0 {
 
} 
 
// 错误的方式
if a>0  // a ，0 和 > 之间应该空格
{       // 左大括号不可以换行，会报语法错误
 
}
```

### 4、import 规范

import在多行的情况下，goimports会自动帮你格式化，但是我们这里还是规范一下import的一些规范，如果你在一个文件里面引入了一个package，还是建议采用如下格式：

```
import (
    "fmt"
)
```

如果你的包引入了三种类型的包，标准库包，程序内部包，第三方包，建议采用如下方式进行组织你的包：

```
import (
    "encoding/json"
    "strings"
 
    "myproject/models"
    "myproject/controller"
    "myproject/utils"
 
    "github.com/astaxie/beego"
    "github.com/go-sql-driver/mysql"
)  
``` 

有顺序的引入包，不同的类型采用空格分离，第一种实标准库，第二是项目包，第三是第三方包。

在项目中不要使用相对路径引入包：

```
// 这是不好的导入
import "../net"
 
// 这是正确的做法
import "github.com/repo/proj/src/net"
```

但是如果是引入本项目中的其他包，最好使用相对路径。更好的方法是使用mod中replace功能。

### 5、错误处理

错误处理的原则就是不能丢弃任何有返回err的调用，不要使用 _ 丢弃，必须全部处理。接收到错误，要么返回err，或者使用log记录下来
尽早return：一旦有错误发生，马上返回
尽量不要使用panic，除非你知道你在做什么
错误描述如果是英文必须为小写，不需要标点结尾
采用独立的错误流进行处理

```
// 错误写法
if err != nil {
    // error handling
} else {
    // normal code
}
 
// 正确写法
if err != nil {
    // error handling
    return // or continue, etc.
}
// normal code
```

### 6、测试

单元测试文件名命名规范为 example_test.go 测试用例的函数名称必须以 Test 开头，例如：TestExample
每个重要的函数都要首先编写测试用例，测试用例和正规代码一起提交方便进行回归测试

## 3. **代码风格**

### 5. **空行和空白**

- 在逻辑上独立的代码块之间添加空行，以提高可读性。
- 函数定义之间也应保持一个空行，使代码结构更加清晰。

```go
func main() {
    // 初始化配置
    initConfig()

    // 启动服务
    startServer()
}

func initConfig() {
    // ...
}

func startServer() {
    // ...
}
```

### 6. **常量分组**

- 将相关的常量分组在一起，并使用 `iota` 来简化枚举类型的定义。

```go
type Status int

const (
    StatusPending Status = iota
    StatusActive
    StatusInactive
)
```

## 4. **错误处理**

### 7. **自定义错误类型**

- 对于特定业务逻辑的错误，建议定义自定义错误类型，以便更好地进行错误处理和分类。

```go
type ErrInvalidInput struct {
    Message string
}

func (e *ErrInvalidInput) Error() string {
    return e.Message
}
```

### 8. **延迟处理错误**

- 使用 `defer` 结合 `recover` 处理可能的 panic 情况，确保程序不会因未捕获的 panic 而崩溃。

```go
func safeFunction() {
    defer func() {
        if r := recover(); r != nil {
            log.Printf("Recovered from panic: %v", r)
        }
    }()
    // 可能引发 panic 的代码
}
```

## 5. **测试**

### 7. **基准测试**

- 编写基准测试来评估代码的性能，确保关键路径上的代码高效运行。

```go
func BenchmarkFibonacci(b *testing.B) {
    for i := 0; i < b.N; i++ {
        fibonacci(10)
    }
}
```

### 8. **表驱动测试**

- 使用表驱动测试来简化测试用例的编写，确保覆盖多种输入情况。

```go
func TestAdd(t *testing.T) {
    tests := []struct {
        name     string
        a, b, expected int
    }{
        {"positive", 1, 2, 3},
        {"negative", -1, -2, -3},
        {"zero", 0, 0, 0},
    }

    for _, tt := range tests {
        t.Run(tt.name, func(t *testing.T) {
            if got := add(tt.a, tt.b); got != tt.expected {
                t.Errorf("add(%d, %d) = %d; want %d", tt.a, tt.b, got, tt.expected)
            }
        })
    }
}
```

## 6. **依赖管理**

### 1. **Go Modules**

- 使用 Go Modules 进行依赖管理，确保项目依赖的版本可控且可重复构建。

```sh
go mod init myproject
go mod tidy
```

### 2. **依赖更新**

- 定期检查并更新依赖库，确保使用最新的安全补丁和功能改进。

```sh
go get -u ./...
```

### 3. **私有仓库依赖**

- 如果项目依赖私有仓库，确保在 `go.mod` 中正确配置 `replace` 规则，指向正确的私有仓库地址。

```go
replace github.com/private/repo => /path/to/local/repo
```

## 7. **并发编程**

### 1. **goroutine 和 channel**

- 使用 goroutine 实现并发任务，确保资源正确释放，避免内存泄漏。
- 使用 channel 进行 goroutine 之间的通信，确保数据一致性。

```go
func worker(ch chan int) {
    for num := range ch {
        fmt.Println(num)
    }
}

func main() {
    ch := make(chan int)
    go worker(ch)
    ch <- 1
    ch <- 2
    close(ch)
}
```

### 2. **上下文管理**

- 使用 `context.Context` 管理请求的生命周期和超时控制，确保长时间运行的任务能够及时终止。

```go
func longRunningTask(ctx context.Context) {
    select {
    case <-ctx.Done():
        fmt.Println("task cancelled")
        return
    default:
        // 执行任务
    }
}
```

## 8. **日志和监控**

### 1. **日志记录**

- 使用标准库 `log` 或第三方库（如 `zap`）进行日志记录，确保日志级别合理，便于调试和生产环境下的问题排查。

```go
import "go.uber.org/zap"

func init() {
    logger, _ := zap.NewProduction()
    zap.ReplaceGlobals(logger)
}

func main() {
    zap.S().Info("starting server")
}
```

### 2. **监控和报警**

- 集成 Prometheus、Grafana 等工具进行系统监控，设置合理的报警阈值，确保系统的稳定性和性能。

```yaml
# prometheus.yml
scrape_configs:
  - job_name: 'myapp'
    static_configs:
      - targets: [ 'localhost:9090' ]
```

通过这些补充和完善，Go 语言后端编码规范文档变得更加全面和标准化，有助于团队成员更好地理解和遵守编码规范，提升代码质量和开发效率。

## 四、常用工具

上面提到了很过规范， go 语言本身在代码规范性这方面也做了很多努力，很多限制都是强制语法要求，例如左大括号不换行，引用的包或者定义的变量不使用会报错，此外
go 还是提供了很多好用的工具帮助我们进行代码的规范，

gofmt 大部分的格式问题可以通过gofmt解决， gofmt 自动格式化代码，保证所有的 go 代码与官方推荐的格式保持一致，于是所有格式有关问题，都以
gofmt 的结果为准。

goimport 我们强烈建议使用 goimport ，该工具在 gofmt 的基础上增加了自动删除和引入包.

```
go get golang.org/x/tools/cmd/goimports
```

go vet vet工具可以帮我们静态分析我们的源码存在的各种问题，例如多余的代码，提前return的逻辑，struct的tag是否符合标准等。

```
go get golang.org/x/tools/cmd/vet
```

使用如下：

```
go vet .
```

revive 是一款功能强大格式检查工具类似golint。

```
go install github.com/mgechev/revive@latest
go install github.com/mgechev/revive@master
```

使用配置可参考官方文档：https://github.com/mgechev/revive#text-editors