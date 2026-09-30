# 项目交付与追踪流程

仓库：`aiStackcoding/aiStack`。GitHub Issue 保存任务的目标、范围、验收与证据；[跨项目研发总看板](https://github.com/users/fxxkrlab/projects/6) 汇总跨仓库工作；[Linear 跨项目研发总览](https://linear.app/fxxkrlab/project/跨项目研发总览-cf51cdb72517) 关联规划与依赖。

## 开始一项工作

1. 核对真实 Git 根目录、远端归属、当前分支、未提交改动及适用 AGENTS；保护现有工作区。
2. 在本仓库按目标和源链接查重，然后复用或新建 Issue。写明范围、验收条件、依赖、预期验证环境和下一步。普通问答与只读排查无需人为创建工程工单。
3. 将 Issue 加入总看板，填写项目、优先级、工作类型；未知状态使用“待整理 / 待核验”。
4. 关联 Linear 工作区 fxxkrlab、团队 FXX、本项目。当前 GitHub App 未连接 aiStackcoding 组织，采用有 GitHub 源 Issue 链接的手动 Linear 关联。尚未配置原生自动同步；补接 App 后先按源链接去重，不扩大代码访问权限。
5. 从核验的基线创建独立分支/worktree。使用 `codex/fxx-<数字>-gh-<Issue数字>-<简短描述>`；同步尚未提供编号时先用 `codex/gh-<Issue数字>-<简短描述>`，获得 Linear 编号后记录准确链接。

## 提交与 PR

提交引用 `Refs aiStackcoding/aiStack#N`。默认创建 Draft PR；正文填写真实 Linear Issue URL、分支、当前完整 head SHA、目标、验收条件、验证证据、风险/回滚和剩余交付步骤。使用 `Related to <Linear URL>` 保留任务关联，需要部署或真实用户验收的任务避免自动关闭关键词。

将 PR 加入总看板，并更新 Issue 与 Linear 的明确链接。跨仓库工作建立协调 Issue 和双方实施 Issue，实际阻塞关系写明解除所需证据；不能仅凭相似标题关联。

仓库的 `Portfolio traceability / traceability` 检查验证分支中的 GitHub/Linear 编号、同仓库的开放 Issue、实际 head SHA 及 PR 说明。它只读取事件和当前 GitHub PR/Issue API，使用只读 GITHUB_TOKEN，无 checkout、部署或业务操作。读取当前 PR 正文避免提交和正文先后更新引发旧事件误报；并发取消过期作业，已被新 head 替代的事件不验证当前交付。旧 PR 后续触发检查时也需补齐流程；在迁移前保留旧分支和已有证据，通过独立任务决定迁移方式。

该检查验证 Linear/总看板链接格式与正文信息；它没有跨产品凭据，**不能证明 Linear 任务存在、关联正确、总看板成员关系或验收证据真实**。这些内容由执行者回读核验并由审查人确认；GitHub App 未获权限时记录缺口。不能用一条绿色元数据检查代替原有产品 CI。

## 状态与完成

总看板：待整理 → 待开发 → 开发中 → 待审核 → 待合并 → 待部署 → 待验收 → 完成；按实际任务跳过不适用阶段，阻塞时填写原因、解除证据和下一步。

证据分别记录本地/静态、指定服务器 CI/数据库、合并、部署、启用与真实用户/客户端验收。未知、未执行和环境失败不标记通过。仅本 Issue 的全部验收条件满足后关闭 Issue 并完成 Linear 任务；文档整理验收不能计为产品发布。

原生 GitHub–Linear 集成不负责 GitHub Projects 自定义状态。原生同步 Issue 的标题/描述/开放关闭变化可能双向传播；将状态更新视为真实变更，只在相应验收满足后关闭，不用 PR 合并替代交付完成。

合并、发布、部署、生产启用和外部资金/通知动作仍需明确操作授权及指定负责人。默认分支保护和 required check 只有平台实际允许、配置成功且回读核验后才能记为生效；当前套餐限制不能通过公开私有仓库绕过。PR 检查本身不阻止直接推送。

## 后续新增项目

首次实施前复用真实仓库并完成相同核对、去重 Issue、总看板、Linear、独立分支和 Draft PR 接入。没有远端时先确认 owner、名称和可见性。用专门初始化 Issue/PR 添加这些模板与规则，保留既有 AGENTS、模板和 CI，核验新仓库的 App 权限与关联方式。全局 Codex 规则指导本机未来项目；团队成员和其他设备通过仓库 AGENTS/模板继承。

## 本次初始化

- GitHub：https://github.com/aiStackcoding/aiStack/issues/2
- Linear：https://linear.app/fxxkrlab/issue/FXX-27/流程初始化-aistack接入-issue总看板linear独立分支与-draft-pr
- 关联方式：`manual-source-link`
- 合并后核验默认分支模板和工作流；本初始化不会关闭产品交付任务。

技术参考：[GitHub GITHUB_TOKEN 权限](https://docs.github.com/en/actions/tutorials/authenticate-with-github_token)、[Issues API](https://docs.github.com/en/rest/issues/issues)、[Linear GitHub 集成](https://linear.app/docs/github)。
