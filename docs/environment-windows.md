# Windows 环境准备与已知限制

> 执行机器：Windows 主力机（SSH 目标 `win`）。本文件记录环境基线、版本、已知限制与算力边界结论，随阶段 0 及后续推进持续更新。

## 基线确认清单（阶段 0）

- [ ] GPU 型号 / 显存：（待填）
- [ ] NVIDIA 驱动版本：（待填）
- [ ] 磁盘剩余空间（Isaac Sim + 缓存占用较大，建议预留 100GB+ 级别）：（待填）
- [ ] WSL2 可用性（Isaac Lab 受阻时的备选路径）：（待填）
- [ ] Isaac Sim 版本与安装方式：（待填）
- [ ] Isaac Lab 版本与安装状态：（待填）
- [ ] LeRobot 环境版本：（待填）

## 已知限制（以官方文档为准，逐项验证后更新）

1. **Isaac Sim**：官方支持 Windows，本机执行仿真、RTX 渲染、OpenUSD 场景组装应无障碍。
2. **Isaac Lab**：以 Linux 为一等公民，Windows 支持可能有限制（待阶段 0 验证）；受阻则走 WSL2 或 Brev 云环境。
3. **GR00T 微调 / 训练**：算力需求高，Windows 本地基本不可行，直接走云 GPU（Brev 等）。
4. **LeRobot 遥操作**：Windows 可跑；物理机械臂环节依赖硬件（见 roadmap.md 决策点 D1）。
5. **Jetson 部署**：需要 Jetson Thor 硬件；无硬件时以 Isaac ROS 工作流学习收口。

## 算力边界结论（阶段 3 摸底后填写）

- RL 并行训练环境数量上限：（待填）
- 结论：哪些环节本地跑、哪些走云：（待填）

## 网络与代理

- 外网访问（NVIDIA、HuggingFace、pip）需要走代理 `127.0.0.1:10808`；国内源直连时清空全部代理变量（含 `all_proxy`）。
- HuggingFace token 已有（gated 模型仓库访问用）。

## 工具链复用

- VS Code + Copilot custom agents + MCP 流水线：直接接入本方向（Agent Bootcamp 的 agent 工作流实践）。
- 多会话/长任务沿用既有偏好：长任务用 git worktree 隔离。
