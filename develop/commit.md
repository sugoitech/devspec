# Commit Message 规范

## 本规范遵循 [Conventional Commits](https://www.conventionalcommits.org/zh-hans/v1.0.0/)

### 提交说明的结构如下所示

---

原文：

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

译文：

```
<类型>[可选 范围]: <描述>

[可选 正文]

[可选 脚注]
```

---

<br />
提交说明包含了下面的结构化元素，以向类库使用者表明其意图：

1. **fix:** _类型_ 为 `fix` 的提交表示在代码库中修复了一个 bug（这和语义化版本中的 [
   `PATCH`](https://semver.org/lang/zh-CN/#%E6%91%98%E8%A6%81) 相对应）。
2. **feat:** _类型_ 为 `feat` 的提交表示在代码库中新增了一个功能（这和语义化版本中的 [
   `MINOR`](https://semver.org/lang/zh-CN/#%E6%91%98%E8%A6%81) 相对应）。
3. **BREAKING CHANGE:** 在脚注中包含 `BREAKING CHANGE:` 或 <类型>(范围) 后面有一个 `!` 的提交，表示引入了破坏性 API
   变更（这和语义化版本中的 [`MAJOR`](https://semver.org/lang/zh-CN/#%E6%91%98%E8%A6%81) 相对应）。
   破坏性变更可以是任意 _类型_ 提交的一部分。
4. 除 `fix:` 和 `feat:` 之外，也可以使用其它提交 _类型_
   ，例如 [@commitlint/config-conventional](https://github.com/conventional-changelog/commitlint/tree/master/%40commitlint/config-conventional)
   （基于 [Angular 约定](https://github.com/angular/angular/blob/22b96b9/CONTRIBUTING.md#-commit-message-guidelines)）中推荐的
   `build:`、`chore:`、
   `ci:`、`docs:`、`style:`、`refactor:`、`perf:`、`test:`，等等。

- build: 用于修改项目构建系统，例如修改依赖库、外部接口或者升级 Node 版本等；
- chore: 用于对非业务性代码进行修改，例如修改构建流程或者工具配置等；
- ci: 用于修改持续集成流程，例如修改 Travis、Jenkins 等工作流配置；
- docs: 用于修改文档，例如修改 README 文件、API 文档等；
- style: 用于修改代码的样式，例如调整缩进、空格、空行等；
- refactor: 用于重构代码，例如修改代码结构、变量名、函数名等但不修改功能逻辑；
- perf: 用于优化性能，例如提升代码的性能、减少内存占用等；
- test: 用于修改测试用例，例如添加、删除、修改代码的测试用例等。

1. 脚注中除了 `BREAKING CHANGE: <description>` ，其它条目应该采用类似
   [git trailer format](https://git-scm.com/docs/git-interpret-trailers) 这样的惯例。

其它提交类型在约定式提交规范中并没有强制限制，并且在语义化版本中没有隐式影响（除非它们包含 BREAKING CHANGE）。
<br /><br />
可以为提交类型添加一个围在圆括号内的范围，以为其提供额外的上下文信息。例如 `feat(parser): adds ability to parse arrays.`。

## 提交规范(Commit Message 格式)

### 模板

```
<type>(<scope>): <subject>
<空行>
<body>
<空行>
<footer>
```

上面是一次 Commit 后 Message
格式规范，分成标题、内容详情、结尾三个部分，各有各的用处，没有多余项。头部即首行，是可以直接在页面中预览的部分，如上图所示，一共有三个部分：<type>、<scope>
和 <subject>，含义分别如下：

### Type

用于说明 Git commit 的类别，只允许使用下面的标识。

- **feat**：新功能（feature）
- **fix**：修补 bug。
- **docs**：仅更新文档（documentation）
- **style**：格式（不影响代码运行的变动）
- **refactor**：重构（即不是新增功能，也不是修改 bug 的代码变动）
- **perf**：优化相关，比如提升性能、体验。
- **test**：增加测试
- **build**：影响构建系统或外部依赖的变化
- **ci**：改变 CI 的配置或脚本
- **chore**：构建过程或辅助工具的变动
- **revert**：回滚到上一个版本。

**新增：**

- **chore**：构建过程或辅助工具的变动（原描述已存在，但未加粗）

### Scope

用来说明本次 Commit 影响的范围，即简要说明修改会涉及的部分。这个本来是选填项，但从 AngularJS 实际项目中可以看出基本上也成了必填项了。

### Subject

用来简要描述本次改动，概述就好了，因为后面还会在 Body 里给出具体信息。并且最好遵循以下规则：

- 以动词开头，使用第一人称现在时，比如 change，而不是 changed 或 changes。
- 首字母不要大写。
- 可以使用中文。
- 结尾不用句号 (.)
- 总长度不能超过 72 个字节（~不超过 30 字）。

**新增：**

- **示例**：`fix: 解决登录页面按钮点击无响应问题`
- **注意事项**：
    - 如果有多个 scope，可以用逗号分隔，例如 `feat(api, ui): 添加用户管理模块`
    - 如果不确定 scope，可以留空，例如 `fix(): 解决未知来源的错误`

### Body (选填)

`<body>` 里的内容是对上面 subject 内容的展开，在此做更加详尽的描述，内容里应该包含修改动机和修改前后的对比。

**新增：**

- **格式要求**：
    - 使用换行符分段，保持良好的可读性。
    - 可以使用 Markdown 语法进行格式化，例如列表、代码块等。
    - 如果引用了其他资源，可以在 body 中提供链接。

### Footer (选填)

`<footer>` 里的主要放置不兼容变更和 Issue 关闭的信息。

**新增：**

- **格式要求**：
    - 如果关闭了某个 Issue，可以使用 `Closes #123` 或 `Fixes #456` 等关键字。
    - 如果引入了 Breaking Change（破坏性变更），请在 footer 中明确指出，并提供迁移指南。
    - 如果是 revert，必须记录撤销前 Commit 的 SHA 值，例如 `Revert "commit message" (SHA)`

### Merge

代码合并

**新增：**

- **说明**：当合并分支时，确保 Commit Message 清晰描述合并的目的和影响范围。
- **示例**：`Merge branch 'feature/new-ui' into develop`

### Revert

此外如果需要撤销之前的 Commit，那么本次 Commit Message 中必须以 `revert:` 开头，后面紧跟前面描述的 Header 部分，格式不变。并且，Body
部分的格式也是固定的，必须要记录撤销前 Commit 的 SHA 值。

**新增：**

- **格式要求**：
    - 必须以 `revert:` 开头，后跟被撤销的 Commit Message。
    - 在 Body 中记录被撤销 Commit 的 SHA 值，例如 `This reverts commit abcdef123456.`
    - 如果有原因，请在 Body 中详细说明。

## 使用

### 检查脚本

服务器端使用 [commit-msg](./pre-commit/commit-msg)。
客户端将 [commit-msg](./hooks/commit-msg) 复制到 `项目/.git/hooks` 文件夹下，开启提交检查。

- **安装步骤**：
    - 确保钩子文件具有可执行权限，可以通过 `chmod +x ./hooks/commit-msg` 设置。
    - 如果使用 Git 版本控制系统，建议在 `.gitconfig` 中配置全局钩子路径。

### 模板工具

JetBrains 可下载插件 `Git Commit Template`

- **其他 IDE 支持**：
    - VS Code 用户可以安装 `GitLens` 插件，它提供了丰富的 Git 提交模板支持。
    - Sublime Text 用户可以安装 `Git Commit Message` 插件，帮助自动生成符合规范的提交信息。

通过这些补充和完善，提交规范文档变得更加全面和标准化，有助于团队成员更好地理解和遵守提交规范。