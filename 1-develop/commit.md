# Commit Message 规范

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

Jetbrain 可下载插件 `Git Commit Template`

- **其他 IDE 支持**：
    - VS Code 用户可以安装 `GitLens` 插件，它提供了丰富的 Git 提交模板支持。
    - Sublime Text 用户可以安装 `Git Commit Message` 插件，帮助自动生成符合规范的提交信息。

通过这些补充和完善，提交规范文档变得更加全面和标准化，有助于团队成员更好地理解和遵守提交规范。