# Codex Skills

此仓库用于版本管理本机 Codex 的全局 skill 目录。

## 目录说明

- 自定义 skill 位于仓库根目录，可按需维护和扩展。
- `.gitignore` 已排除 Python 缓存等运行时文件。

## 自定义 Skill

| Skill | 用途 |
| --- | --- |
| [`testcase-design-markdown`](./testcase-design-markdown/) | 根据需求设计固定层级的测试用例，并输出可评审、可导入 XMind 的 Markdown 文件。 |
| [`testcase-markdown-to-xmind`](./testcase-markdown-to-xmind/) | 将符合约定层级的测试用例 Markdown 转换为本地 `.xmind` 文件。 |

## 使用说明

在 Codex 对话中可通过 `$<skill 名称>` 显式调用 skill；满足 skill 描述的任务也可被自动匹配。

新建或更新自定义 skill 后，提交并推送变更即可同步本仓库的版本记录。
