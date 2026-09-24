---
name: testcase-markdown-to-xmind
description: 将符合固定测试用例层级的 Markdown 文件转换为本地 `.xmind` 文件。当用户提供或指定测试用例 Markdown 并要求生成 XMind 文件时使用。
---

# 测试用例 Markdown 转 XMind

将已有的测试用例 Markdown 直接转换为 `.xmind`。此技能只负责读取、检查和转换现有 Markdown；不设计或改写用例内容。

## 输入要求

输入文件必须使用以下标题层级：

`# 需求：` → `## 模块：` → `### 测试点：` → `#### 用例：…#0～#3` → `##### 前置条件：/步骤：` → `###### 预期：`

前置条件必须在所有步骤之前；最后一个步骤必须有至少一条预期。输入不满足这些要求时，报告具体问题并请用户先使用 `testcase-design-markdown` 修正；不要擅自改写源文件。

## XMind 依赖

使用全局安装的 XMind CLI 和其内置的 `xmind-file` 技能，并遵循当前的认证和交付要求。该 skill 不负责安装自身或安装 CLI。开始转换前先确认：

```bash
xmind --version
xmind auth status
xmind skill list
```

如果全局 `xmind` 命令不可用，请先参考仓库 README 的安装顺序完成全局安装，不要在此处改用局部依赖。若认证状态显示未登录，运行 `xmind auth login cn` 或 `xmind auth login global`，让用户在浏览器中完成授权后再继续。

## 转换流程

1. 读取 Markdown，检查输入要求、标题层级和目标输出路径；不覆盖已有文件。
2. 固定使用 `recipe/quick-map` 和逻辑图画布创建 XMind：

   ```bash
   xmind create --from-markdown <功能>_测试用例.md --skeleton LogicChart-1 --color Dawn-#ffffff-MULTI_LINE_COLORS --skill recipe-quick-map -o <功能>_测试用例.xmind
   xmind validate <功能>_测试用例.xmind --quiet
   ```

3. 报告 `.xmind` 的绝对路径和 `xmind validate` 结果。若 XMind 文件已在桌面端打开，提醒用户关闭并重新打开以刷新内容。

## 边界

- 仅使用 `recipe/quick-map` 生成测试用例 XMind。
- 只通过全局 XMind CLI 创建和校验 `.xmind`；不要伪造或手写 XMind 压缩包。
