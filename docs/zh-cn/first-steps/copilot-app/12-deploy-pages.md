---
title: "第 12 课 - 使用 GitHub Pages 部署网站"
description: "使用 GitHub Copilot app 配置 Pages 工作流，审查其拉取请求，并验证已发布的 Space Quiz。"
authors:
  - jamesmontemagno
lastUpdated: 2026-10-12
---

让 Space Quiz 有一个公开的家：使用 GitHub Pages 部署它。Copilot 可以准备工作流并引导部署，但你仍然需要负责审查变更并确认站点已上线。

在本课中，你将：

- 让 Copilot 配置 GitHub Pages 部署。
- 在合并前审查工作流和拉取请求。
- 跟踪部署并验证已发布的网站。

## 场景

Space Quiz 已经在 GitHub 仓库中，但人们仍然需要一种简单的方法来试用它。使用 GitHub Pages 发布这个单文件站点，可以在公共 URL 上访问，而无需额外的服务器或运行时依赖。

## 让 Copilot 准备部署

> [!WARNING]
> 创建拉取请求会提交并推送代码。在发送该提示前，请检查你的审批设置和目标仓库。使用 **Approve all** 时，不要指望会出现单独的确认提示。

在 `space-quiz` 的 Copilot app 会话中，发送此提示：

```plaintext
Prepare a GitHub Pages deployment for this repository. Create a GitHub Actions workflow that builds the website if needed and deploys it to GitHub Pages after changes reach the default branch. Add a README describing the app and how to run it locally if one does not already exist. Create a pull request with these changes and report its link and any required Pages settings or permissions. Do not merge, enable auto-merge, change Pages settings, or deploy. Stop and wait for my review.
```

## 审查工作流和拉取请求

1. 确认只有在仓库中原本没有 README 时才添加 README。
2. 审查拉取请求中的改动，包括工作流的构建和部署步骤、触发器和权限。
3. 确认工作流从默认分支部署，而不是从未合并的拉取请求部署。
4. 请求任何修正并重新审查更新后的差异。在授权合并前，等待所需的拉取请求检查通过。

## 授权合并和部署

> [!WARNING]
> 以下提示会授权代理合并已审查的拉取请求、修改仓库的 Pages 设置并发布网站。只有在你完成审查并确认仓库和拉取请求后，才发送此提示。审批设置可能允许这些操作无需第二次确认。

将 `<PR_NUMBER>` 替换为你审查过的拉取请求编号，然后发送单独的提示：

```plaintext
I have reviewed pull request <PR_NUMBER> in this repository and authorize its merge and deployment. Enable GitHub Pages using GitHub Actions, merge that pull request only after required checks pass, and monitor the deployment until it succeeds. Report the final URL of the live website. If you lack permission to enable Pages or merge, tell me exactly what I need to approve or do; do not report success until the site is live.
```

![三阶段示意图：已合并的 space-quiz 拉取请求；成功运行的 GitHub Actions Deploy website 工作流，其中包含 Build website、Upload artifact 和 Deploy to Pages 步骤；以及部署在 yourname.github.io/space-quiz/ 上的 Space Quiz。](../../../_images/first-steps-app-pages-deploy.svg)

## 验证部署

1. 跟随 GitHub Actions 部署运行，直至成功。
2. 打开上报的 URL，并确认 Space Quiz 能正常加载。

如果代理无法启用 Pages 或合并拉取请求，请遵循它提供的具体说明。只有在部署成功且实时站点成功加载后，才能将任务视为完成。

## 总结与后续步骤

你的 Space Quiz 现在已作为一个在线站点提供，并且你已经验证了部署，而不是仅仅依赖代理的报告。继续学习 [第 13 课：回顾和后续步骤][next-lesson]。

[next-lesson]: ../13-review/
