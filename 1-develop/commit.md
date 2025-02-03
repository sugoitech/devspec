# 提交规范(Commit Message 格式)

## 模板

```
<type>(<scope>): <subject>
<空行>
<body>
<空行>
<footer>
```

上面是一次Commit后Message格式规范，分成标题，内容详情，结尾三个部分，各有各的用处，没有多余项。
头部即首行，是可以直接在页面中预览的部分，入上面图中所示，一共有三个部分<type>，<scope>，<subject>，含义分别如下

### Type

用于说明git commit的类别，只允许使用下面的标识。

- feat：新功能（feature）
- fix：修补bug。
- docs：仅更新文档（documentation）
- style： 格式（不影响代码运行的变动）
- refactor：重构（即不是新增功能，也不是修改bug的代码变动）
- perf：优化相关，比如提升性能、体验。
- test：增加测试
- build：影响构建系统或外部依赖的变化
- ci: 改变CI的配置或脚本
- chore：构建过程或辅助工具的变动
- revert：回滚到上一个版本。

### Scope

用来说明本次Commit影响的范围，即简要说明修改会涉及的部分。这个本来是选填项，但从AngularJS实际项目中可以看出基本上也成了必填项了。

### Subject

用来简要描述本次改动，概述就好了，因为后面还会在Body里给出具体信息。并且最好遵循下面三条:

以动词开头，使用第一人称现在时，比如change，而不是changed或changes

- 首字母不要大写
- 可以使用中文
- 结尾不用句号(.)
- 总长度不能超过72个字节（~不超过30字）

### Body(选填)

<body>里的内容是对上面subject里内容的展开，在此做更加详尽的描述，内容里应该包含修改动机和修改前后的对比。

### Footer(选填)

`<footer>`里的主要放置不兼容变更和Issue关闭的信息。

### Merge

代码合并

### Revert

此外如果需要撤销之前的Commit，那么本次Commit
Message中必须以revert：开头，后面紧跟前面描述的Header部分，格式不变。并且，Body部分的格式也是固定的，必须要记录撤销前Commit的SHA值。

## 使用

### 检查脚本

服务器端使用[commit-msg](./pre-commit/commit-msg)。
客户端将[commit-msg](./hooks/commit-msg)复制到`项目/.git/hooks`文件夹下，开启提交检查。

### 模板工具

Jetbrain可下载插件`Git Commit Template`
