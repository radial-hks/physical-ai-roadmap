# Physical AI 学习路线图

> 参考来源：NVIDIA Physical AI Learning Center（https://docs.nvidia.com/learning/physical-ai/）。
> 约定：只写学习内容与时长估算，不设硬性日历日期；每个阶段以验收标准收口。决策点单独列出，调整时更新本文件并在 progress.md 记录。

## 总览

```
阶段 0  环境准备（Windows 基线确认 + Isaac Sim 安装）
阶段 1  入门：Isaac Sim 基础 + Physical AI Agent Bootcamp
阶段 2  OpenUSD 与数字孪生
阶段 3  Isaac Lab 强化学习
阶段 4  Sim-to-Real 与 VLA（GR00T）
阶段 5  垂直领域与生态（Healthcare / GTC / 内化分享）
```

各阶段课程时长合计约 40-50 小时（不含环境折腾与自主实践），按每周 5-8 小时节奏估算，整体为 2-3 个月量级，弹性推进。

---

## 阶段 0：环境准备

**目标**：在 Windows 主力机上建立可运行的 Isaac Sim / Isaac Lab / LeRobot 基线环境，摸清本机算力边界。

### 任务

1. 基线确认：GPU 型号与显存、NVIDIA 驱动版本、磁盘空间（Isaac Sim 占用大）、WSL2 可用性。
2. 安装 Isaac Sim（pip 安装 `isaacsim` 包或 Omniverse 方式，以官方当前推荐为准），记录版本号。
3. 启动 Isaac Sim，确认 RTX 渲染 viewport 正常，截图留档。
4. 安装 Isaac Lab，验证 Windows 支持状态（见 environment-windows.md 已知限制）；受阻则改走 WSL2 或 Brev 云环境。
5. 准备 LeRobot（Hugging Face）Python 环境（阶段 4 遥操作要用）。
6. AI coding agent 工具链复用：现有 VS Code + Copilot custom agents + MCP 流水线直接接入本方向，无需另建。

### 验收标准

- [ ] Isaac Sim 可启动并完成 RTX 渲染截图
- [ ] Isaac Lab 或替代路径（WSL2 / Brev）确认可用
- [ ] 本机算力边界结论写入 environment-windows.md（哪些环节本地跑、哪些走云）

---

## 阶段 1：入门 — Isaac Sim 基础 + Agent Bootcamp

**目标**：掌握 Isaac Sim 界面与仿真基础；用 AI agent 工作流完成第一批 OpenUSD / 仿真实践。

### 课程

- **Building Your First Robot in Isaac Sim**（入门，零基础）：界面、从零搭机器人、物理属性配置、加传感器、跑首次仿真。
- **Physical AI Agent Bootcamp**（初级，自定节奏）：Patterned Prompt Method，用 AI coding agent 直接驱动 NVIDIA SDK / Omniverse Kit 库，渲染 OpenUSD 场景、验证 SimReady 资产、跑实时物理仿真。

### 实践任务

1. 完成两个课程全部 hands-on 环节（Windows 本机）。
2. Agent Bootcamp 的 prompt 工作流与现有 Copilot custom agent 方法对比，沉淀一篇笔记（方法论同构性：patterned prompt vs custom agent 指令集）。
3. 产出物入库：`results/` 目录存放渲染场景截图与 USD 资产验证记录。

### 验收标准

- [ ] 自建机器人场景完成一次含传感器配置的仿真
- [ ] 至少 3 个 OpenUSD 场景通过 agent 工作流渲染并留档
- [ ] Agent 工作流方法笔记一篇

---

## 阶段 2：OpenUSD 与数字孪生

**目标**：系统掌握 OpenUSD——数字孪生与工业自动化方向的基础标准。

### 课程

- **Learn OpenUSD**（开源自学，初→高级）：USD 基础、资产结构、组合弧（composition arcs）、模块化、管线开发。
- **Assembling Digital Twins**（中级，3-4h）：OpenUSD 场景组装、资产组织、管线开发。

### 实践任务

1. 按课程完成组合弧与资产模块化练习。
2. 组装一个场景级数字孪生（题材自选，建议与 GIS/数字孪生兴趣结合，如小型场景孪生）。
3. 评估是否参加 OpenUSD Development Professional 认证（决策点 D3）。

### 验收标准

- [ ] Learn OpenUSD 核心章节完成并留笔记
- [ ] 一个完整数字孪生场景（USD 组合结构清晰、可复用资产模块化）
- [ ] 认证去留有明确结论

---

## 阶段 3：Isaac Lab 强化学习

**目标**：掌握 GPU 加速的并行策略训练——Isaac Lab 数千机器人并行、数小时收敛。

### 课程

- **Getting Started With Isaac Lab**（中级，3-4h）：强化学习、GPU 加速、并行策略训练。

### 实践任务

1. 完成课程 hands-on：训练一个 RL 策略并在仿真中回放。
2. 摸底本地 GPU 并行训练吞吐（环境数量上限），决定后续训练规模走本地还是云（决策点 D2）。
3. 进阶选做：Newton 物理引擎、Franka 机械臂逆运动学、可变形缆线操作（Isaac for Healthcare 课程内容，提前摸一角）。

### 验收标准

- [ ] 一个 RL 策略完成训练 + 仿真回放
- [ ] 本地训练吞吐摸底结论写入 environment-windows.md

---

## 阶段 4：Sim-to-Real 与 VLA（GR00T）

**目标**：打通「遥操作 → 数据增强 → VLA 微调 → sim-to-real 部署」完整链路。

### 课程

- **GR00T E2E Workflow**（中级，4-12h）：Isaac GR00T、Isaac Lab-Arena、Isaac Teleop、Isaac ROS、Jetson Thor、Unitree G1。
- **Sim-to-Real SO-101**（中级，6-10h）：LeRobot 遥操作、Isaac Sim 数字孪生仿真、Cosmos Transfer 场景增强、GR00T VLA 微调、sim-to-real 迁移原则。
- **Seeed reBot 实战**（中级，20+h）：~~可选完整版~~ **D1 落地后不在本计划范围**（依赖物理机械臂与 Jetson 硬件），仅作概念参考。

### 实践任务

1. LeRobot 遥操作环节（Windows 可跑；决策点 D1 已落地——**不购置物理机械臂**，涉及实体机械臂的操作环节以缺口文档化收口，仿真侧链路照常走通）。
2. Isaac Sim 中构建对应数字孪生并做仿真验证。
3. Cosmos Transfer 场景增强实验。
4. GR00T VLA 微调：本地 GPU 基本不可行，走 Brev / 云 GPU（决策点 D2 落地）。
5. 边缘部署（Jetson Thor / Isaac ROS）：无硬件则用文档化缺口收口，重点掌握 Isaac ROS 工作流概念。

### 验收标准

- [ ] 遥操作 → 数字孪生 → 场景增强链路走通
- [ ] 一次 GR00T 微调实验完成（本地或云）并记录配置与结果
- [ ] sim-to-real 迁移笔记；Jetson 部署部分缺口文档化（如无硬件）

---

## 阶段 5：垂直领域与生态

**目标**：垂直领域拓展 + 生态跟进 + 学习成果内化。

### 内容

- **Isaac for Healthcare**（中级，3-4h）：医疗机器人、安全协议、领域适配；Newton 物理引擎深度实践。
- **GTC Berlin 2026**（2026-10-20 至 10-22）：关注 RL 策略训练竞赛（CoreWeave 基础设施 + W&B）的会后资料与回放，竞赛形式本身值得研究。
- 成果内化：将本方向学习整理为教程/分享，可并入 ai-tools-tutorial（radial-hks）系列。

### 验收标准

- [ ] Isaac for Healthcare 完成
- [ ] GTC 会后关键资料收集并归档
- [ ] 一篇可分享的教程/总结产出

---

## 决策点（随推进逐个落地）

| # | 决策 | 触发时机 | 当前倾向 |
|---|---|---|---|
| D1 | ~~是否购置物理机械臂~~ **已落地（2026-10-14）：不购置** | — | 个人学习为基础；硬件投入属个人职业规划与公司战略规划层面的动作，不在本计划范围内。物理遥操作环节以缺口文档化收口，其余全链路（仿真侧）照常 |
| D2 | 训练算力走本地还是云（Brev 等） | 阶段 0 摸底 + 阶段 3 吞吐结论 | 学习中依次跟进 |
| D3 | 是否参加 OpenUSD 认证 | 阶段 2 结束 | 学习中依次跟进 |
| D4 | 是否跟进 Jetson 硬件（Thor） | 阶段 4 边缘部署环节 | 学习中依次跟进 |

## 调整约定

- 每个阶段完成后：勾选验收项、在 progress.md 记录结论、需要时修订本文件。
- 范围裁剪遵循既有偏好：弃低价值环节时文档化说明即收口，不无限补齐。
- Windows 执行细节与已知限制统一见 `environment-windows.md`。
