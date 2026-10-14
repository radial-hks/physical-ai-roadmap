# Physical AI Learning Roadmap

面向已有 UE / 数字孪生、Python 与 AI Agent 工程经验的 Physical AI 学习仓库。以 [NVIDIA Physical AI Learning](https://docs.nvidia.com/learning/physical-ai/) 为主线，从课程清单走向“能力 → 实践 → 证据 → 复盘”。

## 从这里开始

1. 阅读 [学习体系](docs/learning-system.md)：明确要具备的能力、基础补齐方式与推进节奏。
2. 查看 [六阶段路线图](docs/roadmap.md)：每个阶段都有前提、实践与验收标准。
3. 打开 [进度与近期队列](docs/progress.md)：从 Windows 环境盘点开始，只推进一个当前任务。
4. 实践时参考 [项目说明](docs/projects.md)，复制 [实验模板](templates/experiment.md) 留下可复现证据。

## 学习主线

```text
0 环境与基础门禁
  → 1 Isaac Sim：物理场景、控制与传感器
  → 2 OpenUSD / 数字孪生方法：模块化场景与数据
  → 3 Isaac Lab：有基线的 RL 训练与评估
  → 4 模仿学习 / VLA：小型 BC 实验、GR00T 接口与迁移边界
  → 5 成果内化：复现包、失败分析与分享
```

贯穿项目是**桌面机器人仿真与学习实验**：RL 核心可从 Cartpole 等官方简单任务起步，桌面 reach 是后续迁移方向。官方示例用于先建立基线；阶段间是否真正集成必须单独验证，不把几段独立演示称为全链路。

| 范围 | 内容 |
|---|---|
| 核心必修 | 基础概念、可复现场景、USD 资产组织、小型传感器数据、RL 闭环、小型行为克隆、VLA/部署边界分析、成果总结 |
| 条件实践 | Agent Bootcamp、ROS 2 桥接、GR00T/SO-101 仿真评估、VLA 微调；先验证平台、数据、算力与预算 |
| 拓展选修 | Healthcare、Newton、Cosmos、高级 USD、认证、GTC 资料 |
| 范围外 | 机械臂与 Jetson 等硬件采购、实体机器人部署/真实 sim-to-real 验证、公司战略或职业转型计划 |

## 执行约定

- 以 Windows 主力机作为实践入口；**未完成实测前，不承诺本机能跑任何指定训练规模**。
- Linux、Brev 等只是候选路径。云资源需单独确认预算、GPU 能力与停止机制；免费课程不代表免费算力。
- 以验收证据而非课时打卡判断完成；不设硬性日历截止日期。
- 中文文档、英文 commit；保持私有仓库，跨仓库分享和对外发布另行决定。
- 本轮完善的是学习体系与规划，**不是实验执行报告**；实际状态见进度页。

## 文档导航

| 文档 | 职责 |
|---|---|
| [学习体系](docs/learning-system.md) | 能力地图、按需补基础、学习循环、状态与裁剪规则 |
| [路线图](docs/roadmap.md) | 六阶段内容、依赖、验收、投入估算和决策点 |
| [实践项目](docs/projects.md) | P0–P5 产物、接口约定、评价协议与项目回退 |
| [Windows 环境](docs/environment-windows.md) | 官方约束与本机实测分离、版本候选、环境/算力门禁 |
| [资源与证据](docs/resources.md) | 课程入口、阅读优先级、官方课时与版本风险 |
| [进度记录](docs/progress.md) | 当前状态的唯一记录、近期动作、自评与历史日志 |
| [实验模板](templates/experiment.md) / [缺口模板](templates/gap.md) | 复现、基线对照、失败与未验证边界 |
| [结果归档规则](results/README.md) | 证据目录、大文件外置、许可与敏感信息管理 |

课程与平台信息核对基准：2026-10-14。`latest` 页面可能变化，真正安装或运行前须重新核对并记录版本。
