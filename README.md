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

## 安装 `testcase-markdown-to-xmind`

此 skill 依赖全局可用的 XMind CLI 及其官方 `xmind-file` skill。

### XMind CLI 官方安装流程

```bash
npm install -g @xmindltd/xmind-cli
npx skills add xmindltd/xmind-cli -y
```

### 验证 CLI 和认证状态

```bash
xmind --version
xmind auth status
```

如果需要登录：

```bash
xmind auth login
```

请在浏览器中完成授权，然后再次运行 `xmind auth status`。认证成功后，验证可用指导：

```bash
xmind skill list
```

不要要求用户手动运行安装命令；只有环境阻止自动执行时，才请用户协助完成。

### 安装本仓库 skill

```bash
npx skills add https://github.com/zhshbcn/skills --skill testcase-markdown-to-xmind -y
```

`npx skills add` 负责安装 skill，不会安装 XMind CLI；CLI 必须先通过 `npm install -g @xmindltd/xmind-cli` 全局安装。

## 使用说明

在 Codex 对话中可通过 `$<skill 名称>` 显式调用 skill；满足 skill 描述的任务也可被自动匹配。

新建或更新自定义 skill 后，提交并推送变更即可同步本仓库的版本记录。
