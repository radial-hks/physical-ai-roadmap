# Physical AI Learning Roadmap

基于 NVIDIA 官方 Physical AI 学习中心（https://docs.nvidia.com/learning/physical-ai/）的系统性学习路线图与实践计划。

## 定位

- 目标：进入 Physical AI 方向——自主机器人、数字孪生、sim-to-real 机器人系统。
- 学习主线：以 NVIDIA 官方免费课程为核心参考。
- 实践环境：Windows 主力机执行与操作；本地算力不足的环节（GR00T 微调等）使用云 GPU（Brev 等）兜底。
- 计划管理：路线图与进度全部落在本仓库，随学习推进持续调整，文档用中文，commit 用英文。

## 仓库结构

```
physical-ai-roadmap/
├── README.md                     # 项目说明与课程入口汇总
├── docs/
│   ├── roadmap.md                # 总路线图：阶段划分、实践任务、验收标准、决策点
│   ├── environment-windows.md    # Windows 环境准备清单与已知限制
│   └── progress.md               # 进度记录（勾选追踪）
```

## 课程入口汇总（来自 NVIDIA 官网）

| 课程 | 链接 | 难度 | 时长 |
|---|---|---|---|
| Building Your First Robot in Isaac Sim | https://docs.nvidia.com/learning/physical-ai/getting-started-with-isaac-sim/latest/index.html | 入门 | — |
| Physical AI Agent Bootcamp | https://docs.nvidia.com/learning/physical-ai/physical-ai-agent-bootcamp/latest/index.html | 初级 | 自定节奏 |
| Assembling Digital Twins | https://docs.nvidia.com/learning/physical-ai/assembling-digital-twins/latest/index.html | 中级 | 3-4h |
| Getting Started With Isaac Lab | https://docs.nvidia.com/learning/physical-ai/getting-started-with-isaac-lab/latest/index.html | 中级 | 3-4h |
| Getting Started With Isaac for Healthcare | https://docs.nvidia.com/learning/physical-ai/getting-started-with-isaac-for-healthcare/latest/index.html | 中级 | 3-4h |
| GR00T E2E Workflow | https://docs.nvidia.com/learning/physical-ai/gr00t-e2e-workflow/latest/index.html | 中级 | 4-12h |
| Sim-to-Real SO-101 | https://docs.nvidia.com/learning/physical-ai/sim-to-real-so-101/latest/index.html | 中级 | 6-10h |
| Seeed reBot 实战（Seeed 官网） | https://www.seeedstudio.com/sim-to-real-with-seeed-rebot-and-nvidia-isaac | 中级 | 20+h |
| Learn OpenUSD | https://docs.nvidia.com/learn-openusd/latest/index.html | 初→高级 | 开源自学 |

补充入口：

- Physical AI 概述：https://www.nvidia.com/en-us/glossary/generative-physical-ai/
- OpenUSD 认证：https://www.nvidia.com/en-us/learn/certification/openusd-development-professional/
- Brev（云 GPU 开发环境）：https://brev.nvidia.com/

## 技术栈覆盖

OpenUSD 数据工作流 → Omniverse 数字孪生 → Isaac Sim 仿真 → Isaac Lab 策略训练 → Isaac ROS / Jetson 部署 → sim-to-real 机器人。
