# 目录结构 (structure.md)

```
├─.devcontainer
├─.github
│  ├─config
│  ├─ISSUE_TEMPLATE
│  └─profile
├─config
├─dist
│  └─static
│      ├─css
│      ├─image
│      └─js
│          └─async
├─node_modules
├─public
│  └─static
│      └─js
├─resources
│  └─openapi
└─src
    ├─app
    │  ├─MainLayout
    │  └─System
    ├─assets
    │  ├─icons
    │  └─static
    ├─components
    │  ├─custom
    │  ├─DataTable
    │  ├─Field
    │  ├─FileUpload
    │  ├─KBar
    │  ├─Loading
    │  ├─NavUser
    │  ├─Sidebar
    │  ├─Theme
    │  └─ui
    ├─context
    ├─hooks
    ├─lib
    ├─mocks
    │  └─user
    ├─pages
    │  ├─apps
    │  ├─auth
    │  │  ├─ForgotPassword
    │  │  │  └─components
    │  │  ├─Otp
    │  │  │  └─components
    │  │  ├─SignIn
    │  │  │  └─components
    │  │  ├─SignIn2
    │  │  └─SignUp
    │  │      └─components
    │  ├─dashboard
    │  │  ├─Customers
    │  │  │  └─components
    │  │  ├─Monitor
    │  │  ├─Overview
    │  │  │  └─components
    │  │  ├─Products
    │  │  │  └─components
    │  │  └─Settings
    │  │      └─components
    │  ├─errors
    │  ├─examples
    │  │  ├─form
    │  │  │  ├─advanced
    │  │  │  ├─basic
    │  │  │  └─simple
    │  │  └─list
    │  ├─extra-components
    │  ├─login
    │  ├─settings
    │  │  ├─account
    │  │  ├─appearance
    │  │  ├─components
    │  │  ├─display
    │  │  ├─error-example
    │  │  ├─notifications
    │  │  └─profile
    │  ├─system
    │  │  ├─permissions
    │  │  ├─protected-route
    │  │  ├─roles
    │  │  ├─settings
    │  │  ├─user
    │  │  └─users
    │  │      └─components
    │  └─tasks
    │      ├─components
    │      └─data
    ├─routes
    │  ├─(Auth)
    │  ├─(Errors)
    │  └─_authorization
    │      ├─apps
    │      ├─dashboard
    │      ├─examples
    │      │  ├─form
    │      │  └─list
    │      ├─system
    │      └─tasks
    ├─services
    │  └─system
    ├─styles
    ├─types
    │  └─system
    └─utils
```

### 项目根目录

```
├─.devcontainer
├─.github
│  ├─config
│  ├─ISSUE_TEMPLATE
│  └─profile
├─config
├─dist
│  └─static
│      ├─css
│      ├─image
│      └─js
│          └─async
├─node_modules
├─public
│  └─static
│      └─js
├─resources
│  └─openapi
└─src
```

#### .devcontainer

- **用途**：用于配置开发容器（Dev Container），确保所有开发者使用一致的开发环境。
- **内容**：包含 Dockerfile 和其他配置文件，定义了开发环境所需的工具和依赖项。

#### .github

- **用途**：存放 GitHub 相关配置文件和工作流。
- **内容**：
    - `config`：GitHub 配置文件。
    - `ISSUE_TEMPLATE`：自定义的 Issue 模板，帮助用户提交高质量的问题报告。
    - `profile`：GitHub 仓库主页配置文件。

#### config

- **用途**：存放项目的配置文件，如环境变量、API 端点等。
- **内容**：各种配置文件，如 `.env` 文件、API 配置文件等。

#### dist

- **用途**：存放构建后的静态资源文件。
- **内容**：
    - `static`：静态资源文件夹，包含 CSS、图片、JavaScript 文件等。
        - `css`：样式文件。
        - `image`：图片资源。
        - `js`：JavaScript 文件，包括异步加载的模块。

#### node_modules

- **用途**：存放 npm 或 yarn 安装的第三方库和依赖项。
- **内容**：自动管理，通常不需手动修改。

#### public

- **用途**：存放公共静态资源文件，这些文件会直接复制到构建输出目录中。
- **内容**：
    - `static`：公共静态资源文件夹，包含 JavaScript 文件等。

#### resources

- **用途**：存放项目所需的各种资源文件，如 OpenAPI 规范文件。
- **内容**：
    - `openapi`：OpenAPI 规范文件，用于 API 文档生成和验证。

#### src

- **用途**：存放项目的源代码。
- **内容**：见下文详细说明。

#### app

- **用途**：存放应用程序的核心组件和布局。
- **内容**：
    - `MainLayout`：主布局组件，包含导航栏、侧边栏等。
    - `System`：系统相关组件，如全局状态管理等。

#### assets

- **用途**：存放静态资源文件，如图标和静态图片。
- **内容**：
    - `icons`：图标文件。
    - `static`：其他静态资源文件。

#### components

- **用途**：存放可复用的 UI 组件。
- **内容**：
    - `DataTable`：表格组件。
    - `Field`：表单字段组件。
    - `FileUpload`：文件上传组件。
    - `KBar`：键盘快捷键组件。
    - `Loading`：加载指示器组件。
    - `NavUser`：用户导航组件。
    - `Sidebar`：侧边栏组件。
    - `Theme`：主题切换组件。
    - `ui`：UI 基础组件。

#### hooks

- **用途**：存放自定义的 React Hooks。
- **内容**：各种自定义 Hook 函数。

#### lib

- **用途**：存放项目中使用的辅助函数和工具库。
- **内容**：通用工具函数和库。

#### mocks

- **用途**：存放模拟数据，用于开发和测试。
- **内容**：
    - `user`：用户相关的模拟数据。

#### pages

- **用途**：存放页面级别的组件。
- **内容**：
    - `apps`：应用相关页面。
    - `auth`：认证页面（登录、注册等）。
        - `ForgotPassword`：忘记密码页面及其子组件。
        - `Otp`：一次性密码页面及其子组件。
        - `SignIn`：登录页面及其子组件。
        - `SignIn2`：备用登录页面。
        - `SignUp`：注册页面及其子组件。
    - `dashboard`：仪表盘页面。
        - `Customers`：客户管理页面及其子组件。
        - `Monitor`：监控页面。
        - `Overview`：概览页面及其子组件。
        - `Products`：产品管理页面及其子组件。
        - `Settings`：设置页面及其子组件。
    - `errors`：错误页面。
    - `examples`：示例页面。
        - `form`：表单示例页面。
            - `advanced`：高级表单示例。
            - `basic`：基础表单示例。
            - `simple`：简单表单示例。
        - `list`：列表示例页面。
    - `extra-components`：额外组件页面。
    - `login`：登录页面。
    - `settings`：设置页面。
        - `account`：账户设置。
        - `appearance`：外观设置。
        - `components`：设置页面组件。
        - `display`：显示设置。
        - `error-example`：错误示例页面。
        - `notifications`：通知设置。
        - `profile`：个人资料设置。
    - `system`：系统管理页面。
        - `permissions`：权限管理。
        - `protected-route`：受保护路由。
        - `roles`：角色管理。
        - `settings`：系统设置。
        - `user`：用户管理。
        - `users`：用户列表及其子组件。
    - `tasks`：任务管理页面。
        - `components`：任务页面组件。
        - `data`：任务数据。

#### routes

- **用途**：存放路由配置文件。
- **内容**：
    - `(Auth)`：认证相关路由。
    - `(Errors)`：错误页面路由。
    - `_authorization`：授权相关路由。
        - `apps`：应用路由。
        - `dashboard`：仪表盘路由。
        - `examples`：示例页面路由。
            - `form`：表单示例路由。
            - `list`：列表示例路由。
        - `system`：系统管理路由。
        - `tasks`：任务管理路由。

#### services

- **用途**：存放服务层代码，如 API 请求封装。
- **内容**：
    - `system`：系统服务。

#### styles

- **用途**：存放全局样式文件。
- **内容**：CSS/SCSS 文件，全局样式定义。

#### types

- **用途**：存放 TypeScript 类型定义文件。
- **内容**：
    - `system`：系统相关类型定义。

#### utils

- **用途**：存放通用工具函数和辅助函数。
- **内容**：各种工具函数和辅助方法。

