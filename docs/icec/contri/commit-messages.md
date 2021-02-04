为了创建一套清晰的提交历史，我们对 **commit messages** 做出如下规定。

基本格式：

```text
<emoji> <描述>

[可选的正文]
```

这里，我们采用 emoji[^1] 表情向仓库维护者简要地表明当前提交的类型，`<emoji>` 的选择包括：

| emoji 表情及其对应的 Markdown 代码，可直接在 message 中使用 | 类型                       |
| ----------------------------------------------------------- | -------------------------- |
| :pencil: `:pencil:`​                                             | 新建页面                   |
| :pencil2: `:pencil2:`​                                       | 修改页面内容、错字以及排版 |
| :bug: `:bug:`                                               | 修复除内容以外的错误       |
| :sparkles: `:sparkles:`​                                     | 新增功能、特性             |
| :fire: `:fire:`                                             | 删除文件                   |
| :lipstick: `:lipstick:`                                     | 修改 Wiki 外观             |
| :construction: `:construction:`                             | 工作进行中，尚未完成       |
| :construction_worker: `:construction_worker:`               | 添加或更新 CI 配置         |
| :wrench: `:wrench:`​                                         | 修改配置文件               |
| :see_no_evil: `:see_no_evil:`​                               | 修改 `.gitignore` 文件     |

在 `<描述>` 中，需清晰地描述出修改了什么内容以及文件或页面，例如：

- :sparkles: 添加脚注功能
- :see_no_evil: ​将 yarn.lock 添加至 .gitignore
- :pencil2: ​修复了 README.md 的排版问题

## 参考链接

[^1]: [gitmoji | An emoji guide for your commit messages](https://gitmoji.dev/)
