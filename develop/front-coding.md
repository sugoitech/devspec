# 前端 TypeScript 编码规范 (front-coding.md)

## 目的

定义前端项目中 TypeScript 的编码规范，确保代码风格一致，提高代码的可读性和可维护性。这些规范适用于所有使用 TypeScript
的前端开发人员。

---

## 1. **命名规范**

### 1.1 变量名

- **驼峰命名法**：采用小驼峰命名法（camelCase），首字母小写。
- **常量名**：全部大写，单词之间用下划线分隔（SCREAMING_SNAKE_CASE）。

```typescript
let userName = "Alice";
const MAX_RETRIES = 5;
```

### 1.2 函数名

- **驼峰命名法**：采用小驼峰命名法，首字母小写。
- **构造函数**：采用大驼峰命名法（PascalCase），首字母大写。

```typescript
function getUser() {
  // ...
}

class User {
}
```

### 1.3 类名和接口名

- **大驼峰命名法**：采用大驼峰命名法，首字母大写。

```typescript
class UserProfile {
}

interface User {
  id: number;
  name: string;
}
```

### 1.4 文件名

- **小写字母和下划线**：文件名使用小写字母和下划线分隔单词（snake_case）。

```typescript
// user_profile.ts
```

---

## 2. **注释规范**

### 2.1 包/模块注释

- 每个模块或包都应该有一个简要的描述，介绍其功能和用途。

```typescript
/**
 * utils.ts: 该模块包含了项目共用的一些工具函数。
 */
```

### 2.2 函数注释

- 每个函数都应该有简要说明，包括参数和返回值的解释。

```typescript
/**
 * 创建一个新的用户对象。
 *
 * @param name - 用户名
 * @returns 用户对象指针
 */
function createUser(name: string): User {
  return {id: 1, name};
}
```

### 2.3 关键逻辑注释

- 对于复杂的逻辑或算法，应在代码块前添加详细的注释。

```typescript
// 计算斐波那契数列的第 n 项
// 使用递归方式实现，适用于较小的 n 值
function fibonacci(n: number): number {
  if (n <= 1) {
    return n;
  }
  return fibonacci(n - 1) + fibonacci(n - 2);
}
```

### 2.4 TODO 注释

- 使用 `TODO` 标记未来需要处理的任务或潜在问题。格式为：`TODO(username): description`。

```typescript
// TODO(hanru): 改进性能，优化查询逻辑
```

---

## 3. **代码风格**

### 3.1 缩进和折行

- 使用编辑器自带的格式化工具（如 Prettier、ESLint）自动格式化代码，保持一致的缩进和折行规则。
- 缩进使用 2 个空格。

```typescript
if (a > 0) {
  // ...
}
```

### 3.2 空行和空白

- 在逻辑独立的代码块之间添加空行，提高可读性。
- 所有的运算符和操作数之间要留空格。

```typescript
// 正确的代码风格
if (a > 0) {
  // ...
}

// 错误的代码风格
if (a > 0) { // 不正确
  // ...
}
```

### 3.3 最大行宽

- 一行代码不超过 120 个字符，超过的请使用换行展示。

```typescript
// 超过 120 字符时换行
const longString = `This is a very long string that needs to be wrapped for better readability.`;
```

---

## 4. **类型声明**

### 4.1 显式类型声明

- 尽可能显式声明变量和函数的类型，避免隐式 `any` 类型。

```typescript
let count: number = 0;

function add(a: number, b: number): number {
  return a + b;
}
```

### 4.2 接口与类型别名

- 使用接口（Interface）定义对象形状，使用类型别名（Type Alias）定义联合类型或映射类型。

```typescript
interface User {
  id: number;
  name: string;
}

type Role = 'admin' | 'user';
```

### 4.3 泛型

- 使用泛型提高代码的复用性和灵活性。

```typescript
function identity<T>(arg: T): T {
  return arg;
}
```

---

## 5. **错误处理**

### 5.1 不要忽略错误

- 所有可能抛出异常的操作都必须处理，不能简单地忽略。

```typescript
try {
  const result = await fetchData();
} catch (error) {
  console.error('Failed to fetch data:', error);
}
```

### 5.2 自定义错误类型

- 对于特定业务逻辑的错误，建议定义自定义错误类型。

```typescript
class ValidationError extends Error {
  constructor(message: string) {
    super(message);
    this.name = 'ValidationError';
  }
}
```

---

## 6. **依赖管理**

### 6.1 版本锁定

- 使用包管理工具（如 npm、yarn）进行依赖管理，确保依赖版本可控。

```bash
# 使用 npm 锁定依赖版本
npm install --save-dev package-name

# 使用 yarn 锁定依赖版本
yarn add package-name
```

### 6.2 私有仓库依赖

- 如果项目依赖私有仓库，确保在配置文件中正确配置路径。

```json
{
  "dependencies": {
    "private-package": "file:../path/to/private/package"
  }
}
```

---

## 7. **并发编程**

### 7.1 异步任务

- 使用 `async/await` 实现异步任务，确保资源正确释放，避免内存泄漏。

```typescript
async function fetchData() {
  try {
    const response = await fetch('/api/data');
    const data = await response.json();
    return data;
  } catch (error) {
    console.error('Error fetching data:', error);
  }
}
```

### 7.2 上下文管理

- 使用上下文管理器（如 React 的 `useEffect` 和 `useContext`）管理资源的生命周期。

```typescript
import React, {useEffect, useContext} from 'react';

function MyComponent() {
  useEffect(() => {
    // 组件挂载时执行
    return () => {
      // 组件卸载时清理资源
    };
  }, []);

  return <div>Hello
  World < /div>;
}
```

---

## 8. **日志和监控**

### 8.1 日志记录

- 使用标准库或第三方库（如 `console.log` 或 `winston`）进行日志记录，确保日志级别合理。

```typescript
console.log('Starting server');
```

### 8.2 监控和报警

- 集成监控工具（如 Prometheus、Grafana）进行系统监控，设置合理的报警阈值。

```typescript
// 示例：集成 Prometheus 客户端库
import {register, Counter} from 'prom-client';

const httpRequestCounter = new Counter({
  name: 'http_requests_total',
  help: 'Total number of HTTP requests',
});

app.get('/', (req, res) => {
  httpRequestCounter.inc();
  res.send('Hello World');
});
```

---

## 9. **测试**

### 9.1 单元测试

- 为每个重要的函数编写单元测试，确保其行为符合预期。

```typescript
import {test, expect} from '@jest/globals';

test('add function', () => {
  expect(add(1, 2)).toBe(3);
});
```

### 9.2 集成测试

- 编写集成测试，验证不同模块之间的交互是否正常。

```typescript
import request from 'supertest';
import app from '../src/app';

test('GET /api/users should return status 200', async () => {
  const response = await request(app).get('/api/users');
  expect(response.statusCode).toBe(200);
});
```

### 9.3 端到端测试

- 编写端到端测试，模拟真实用户操作，确保整个系统的稳定性。

```typescript
import {test, expect} from '@playwright/test';

test('User can login and navigate to dashboard', async ({page}) => {
  await page.goto('/login');
  await page.fill('#username', 'alice');
  await page.fill('#password', 'password');
  await page.click('button[type="submit"]');
  await expect(page).toHaveURL('/dashboard');
});
```

---

## 10. **代码审查**

### 10.1 定期审查

- 定期进行代码审查，确保代码质量符合团队标准。

### 10.2 建设性反馈

- 提出的问题和建议应具体且具有建设性，避免模糊或负面的评论。

---

## 11. **持续集成与部署**

### 11.1 CI/CD 工具

- 使用 CI/CD 工具（如 Jenkins、Travis CI、CircleCI）自动化构建、测试和部署流程。

```yaml
# CI 配置示例 (GitHub Actions)
name: CI

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Set up Node.js
        uses: actions/setup-node@v2
        with:
          node-version: '14'
      - name: Install dependencies
        run: npm install
      - name: Run tests
        run: npm test
```

通过以上规范，团队成员可以在开发过程中保持一致的标准，确保代码质量和项目的长期稳定性。希望这些指南能帮助大家更高效地进行开发，共同提升项目的整体水平。

---