# 实践产物与证据

当前仅有归档规则，**尚未提交学习实验结果**。按需创建目录，不用空截图或示例指标填充进度。

## 目录约定

```text
results/
  p0-environment/<run-id>/README.md
  p1-simulation/<run-id>/README.md
  p2-usd-data/<run-id>/README.md
  p3-rl/<run-id>/README.md
  p4-imitation/<run-id>/README.md
  p5-summary/<run-id>/README.md
```

只在实际开展实验时建相应目录。`run-id` 使用实际日期与语义清晰的主题；复现说明来自 [实验模板](../templates/experiment.md)。缺口记录可放在对应项目目录，使用 [缺口模板](../templates/gap.md)。

## 提交与外部存储

- 提交：中文实验笔记、配置、脚本、小型 `.usda` 资产、必要的少量截图、汇总指标和许可说明。
- 不提交：完整数据集、模型权重/checkpoint、训练缓存、大型 USD 二进制资产、长视频、SDK 安装包、API token、私钥。
- 大文件存放 NAS 或经批准的对象存储；在实验记录填写稳定 URI/路径、访问条件、大小、真实计算的校验和和对应软件版本。引用地址不含临时访问 token。
- 本地未提交制品统一放项目根目录 `artifacts/` 或 `data/`，已列入 `.gitignore`。`.gitignore` 不是安全扫描，提交前仍需检查新增文件。
- 出现敏感信息时先清理再提交；公开数据仍需检查许可，不因仓库 private 就默认可再分发。

## 证据索引

每个项目目录的 README 链接其实际运行记录。阶段状态与验收证据入口只在 [progress.md](../docs/progress.md) 维护，不另造一套总进度。
