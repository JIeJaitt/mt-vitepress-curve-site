---
title: 欢迎使用vitepress
tags: [vitepress, vue]
categories: [日常随笔]
date: 2024-03-01 15:11:14
description: ReferenceError: require is not defined in ES module scope, you can use import instead
articleGPT: ReferenceError: require is not defined in ES module scope, you can use import instead
---

```bash
➜  mt-vitepress-curve-site git:(master) ✗ node push.js
file:///Users/jiejaitt/Desktop/mt-vitepress-curve-site/push.js:1
const { exec } = require('child_process');
                 ^

ReferenceError: require is not defined in ES module scope, you can use import instead
This file is being treated as an ES module because it has a '.js' file extension and '/Users/jiejaitt/Desktop/mt-vitepress-curve-site/package.json' contains "type": "module". To treat it as a CommonJS script, rename it to use the '.cjs' file extension.
    at file:///Users/jiejaitt/Desktop/mt-vitepress-curve-site/push.js:1:18
    at ModuleJob.run (node:internal/modules/esm/module_job:195:25)
    at async ModuleLoader.import (node:internal/modules/esm/loader:337:24)
    at async loadESM (node:internal/process/esm_loader:34:7)
    at async handleMainPromise (node:internal/modules/run_main:106:12)

Node.js v18.20.1
```

从错误信息来看，你遇到了一个 Node.js 模块系统的问题。错误提示 `ReferenceError: require is not defined in ES module scope` 表示 `require` 函数在 ES 模块作用域中没有被定义。这是因为你的项目被识别为 ES 模块，而 `require` 是 CommonJS 模块的语法。

你的 `package.json` 文件中包含了 `"type": "module"`，这意味着 Node.js 默认将 `.js` 文件作为 ES 模块来处理。如果你想要使用 CommonJS 模块的 `require` 语法，你可以将文件扩展名改为 `.cjs`，或者在 `package.json` 中删除 `"type": "module"` 这一行。

如果你想要继续使用 ES 模块，你可以使用 `import` 语法来代替 `require`。例如，如果你的 `push.js` 文件需要执行一个子进程，你可以这样修改：

```javascript
import { exec } from 'child_process';

// 你的其他代码
```

如果你的项目需要同时支持 CommonJS 和 ES 模块，你可以保留 `"type": "module"` 并使用 `import` 语法，或者为 CommonJS 模块创建 `.cjs` 文件。

根据你的需求，你可以选择以下解决方案之一：

1. **修改 `package.json`：** 删除 `"type": "module"` 来让 Node.js 按照 CommonJS 模块处理 `.js` 文件。
2. **重命名文件：** 将 `push.js` 改为 `push.cjs` 来明确告诉 Node.js 这是一个 CommonJS 模块。
3. **使用 ES 模块语法：** 修改你的代码以使用 `import` 语法。

选择哪种方法取决于你的项目需求和个人偏好。如果你的项目是混合模块类型，可能需要更复杂的配置来同时支持两种模块系统。