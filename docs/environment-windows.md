# Windows 环境、版本与算力门禁

> 实践入口：Windows 主力机（SSH 目标 `win`）。本轮仅核对官方资料，**未访问或配置目标机**；本机基线和性能均待实测。资料核对日：2026-10-14。

## 本机基线（等待 P0 填写）

| 项目 | 实测值 | 证据 / 结论 |
|---|---|---|
| Windows 版本与 build | 待填 | 不从设备昵称推断 |
| CPU / 系统 RAM | 待填 | — |
| GPU 型号 / 架构 / RT Core 支持 | 待填 | 硬件规格与官方支持矩阵双重核对 |
| 显存总量 / 空闲量 | 待填 | — |
| NVIDIA 驱动 | 待填 | — |
| 安装盘 / 空闲空间 / 缓存与数据位置 | 待填 | 安装、缓存、资产、checkpoint 分别预留 |
| 网络 / 下载 / 模型访问权限 | 待填 | 不把已有 HF 账号等同于获得所有 gated 模型授权 |
| WSL 版本与发行版（仅需 ROS 支线时） | 待填 | 不是 Sim/Lab 默认退路 |
| 所选 Sim / Lab / Python / 训练框架 | 待填 | 填精确版本、来源和安装方式 |
| Compatibility Checker / 最小仿真结果 | 待填 | 填 P0 实验路径 |

### 盘点命令（待在 Windows 执行，不代表本次已运行）

PowerShell 的只读采集示例：

```powershell
Get-CimInstance Win32_OperatingSystem | Select-Object Caption, Version, BuildNumber
Get-CimInstance Win32_ComputerSystem | Select-Object TotalPhysicalMemory
Get-CimInstance Win32_Processor | Select-Object Name
nvidia-smi --query-gpu=name,driver_version,memory.total,memory.free --format=csv
Get-PSDrive -PSProvider FileSystem | Select-Object Name, Used, Free
```

若 `nvidia-smi` 不存在或报错，记录原始错误，不能直接判定没有 GPU。必要时才补 `wsl --status` 和 `wsl --list --verbose`；不要为盘点顺便安装/升级系统或驱动。

## 按组件核对官方支持

| 组件 / 证据范围 | 官方信息 | 本计划处理 |
|---|---|---|
| [Isaac Sim 5.1.0 requirements](https://docs.isaacsim.omniverse.nvidia.com/5.1.0/installation/requirements.html) | x86_64 表列 Windows 10/11、Ubuntu 22.04/24.04；最低档位 RTX 4080 / 16GB VRAM / 32GB RAM / 50GB SSD；容器仅 Linux，无 RT Core 的 A100/H100 不支持 | 优先评估 Windows 11 原生；官方档位不是本机可用性的保证，复杂传感器/训练额外消耗另测 |
| [Isaac Lab v2.3.0 pip 安装](https://isaac-sim.github.io/IsaacLab/v2.3.0/source/setup/installation/pip_installation.html) | 有 Windows `isaaclab.bat` 流程；Sim 5.X 对应 Python 3.11；需注意 Windows 长路径；robomimic 在 Windows 不可用 | 不能笼统写 Windows 不支持 Lab，也不能承诺每个训练框架支持；只安装目标任务所需框架 |
| [Sim 5.1 ROS 2 安装](https://docs.isaacsim.omniverse.nvidia.com/5.1.0/installation/install_ros.html) | 提供原生 Windows Sim 与 WSL2 内 ROS 2 Humble 的通信路线；该 ROS Docker 工作流不支持 Windows/WSL2 | 区分 Sim 进程、ROS 节点和容器运行位置；不是 Sim/Lab 全栈 WSL2 受支持的证明 |
| [GR00T E2E 前提](https://docs.nvidia.com/learning/physical-ai/gr00t-e2e-workflow/latest/getting-started/prerequisites.html) | Linux/Docker；G1 课程 GR00T 1.7 后训练至少 48GB VRAM；自采演示有输入设备要求 | 单独建环境，推理与训练分别评估；可以选择已有数据/模型，不默认自采或微调 |
| [SO-101 课程代码与模型](https://docs.nvidia.com/learning/physical-ai/sim-to-real-so-101/latest/06-get-the-code.html) | Docker + Ada/Blackwell GPU；固定 Sim 5.1.0 / Lab 2.3.0 / LeRobot 0.4.3 / GR00T N1.6 | 保留课程版本，不用新版 N1.7 安装命令替换；该课程不等于原生 Windows 通用流程 |
| [LeRobot v0.4.3 安装](https://github.com/huggingface/lerobot/blob/v0.4.3/docs/source/installation.mdx) | 固定版本依赖和安装说明；当前 main 文档可能不同 | 数据/模型/视频后端按所选版本核验，不再笼统承诺“Windows 遥操作可跑” |
| [Isaac ROS release-4.6 平台表](https://nvidia-isaac-ros.github.io/v/release-4.6/getting_started/index.html) | 支持合格的 x86_64 Ubuntu 24.04 与 Jetson 等组合，ROS 2 Jazzy；该版支持表不含 WSL2 | Isaac ROS 不等于必须购买 Thor；桌面软件验证也不能替代板端或真实机器人验证 |

硬件、驱动与平台以所选版本的完整文档为准。版本表里的测试驱动不是永远适用的最低驱动；不把某教程的简化配置覆盖产品级要求。新硬件或上游不再支持旧版时，重新选完整兼容组合，而不是坚持旧锁。

## 版本锁：先候选，后实测确认

**阶段 0 的候选基线**：Isaac Sim **5.1.0** + Isaac Lab **v2.3.0** + Python **3.11**，依据上表固定 Lab 安装文档及 SO-101 课程。它是复现旧版教程的候选，**不是“当前最新版”，也未在本机验证**。可因课程变更或硬件支持重新选择。

| 环境 | 应锁定的信息 | 建立时机 |
|---|---|---|
| USD 基础 | OpenUSD 工具/`usd-core` 与 Python 版本；usdview 来源 | 阶段 0–2，独立环境 |
| Sim / Lab | Sim 发行版、Lab tag/commit、Python、PyTorch/CUDA wheel、训练框架、驱动、安装方式 | 阶段 0 选组合；阶段 3 前验证 Lab |
| 小型 BC | Python、PyTorch或所选轻量实现、数据 schema；是否只用 CPU | 阶段 4 核心实验 |
| LeRobot / GR00T | 对应课程版本、代码和模型 revision、数据版本、容器 tag/digest、授权 | 阶段 4 条件实践 |
| ROS / Isaac ROS | ROS 发行版、Python接口、Isaac ROS release、平台/驱动及通信拓扑 | 实际需要桥接或加速节点时 |

不能因 Python 相同就合并所有依赖；不要在能跑的学习环境上直接 `pip install -U` 全家桶。新组合用新环境，保留旧配置和回退说明。安装命令从**选定版本**官方页面获取，并在实际运行后收入实验记录，本文不提供未经验证的一键安装脚本。

### GR00T 显存数字为什么不统一

[固定源码快照的 N1.7 硬件指南](https://github.com/NVIDIA/Isaac-GR00T/blob/d2b7e75b937e3ec9aa5dbc798f08b89692c49734/getting_started/hardware_recommendation.md) 列出推理 16GB+、微调 40GB+、开启 LLM/视觉骨干微调建议 80GB+；G1 课程则要求后训练至少 48GB。这是不同运行配置和验收范围，**不能取较小数字来放行更重的教程**。运行 G1 课程按课程门槛；独立模型实验按锁定代码/模型配置再实测。

这些数字不证明目标 Windows 可原生运行 GR00T。官方模型路线的 OS、依赖与 RTX 仿真能力须分别核验；H100 能跑模型也不表示能跑 Isaac Sim RTX 仿真。

## 环境验收顺序

1. **E0 资料与硬件**：课程、版本候选、硬件与权限明确；冲突未解决前不下载大资产。
2. **E1 最小 Sim**：Compatibility Checker → 简单场景 → 正常退出 → 重新启动；记录日志/显存。
3. **E2 目标仿真**：物理与一个传感器输出正常，确认不是只有 viewport 能显示。
4. **E3 最小 Lab**：目标训练框架可用，小规模任务可 reset/step，完成短训练与回放。
5. **E4 规模与模型**：按实际需要测试并行度、数据规模、模型加载和单次推理；微调单独批准。

E1 是 G0 的运行部分；E2/E3/E4 随阶段推进，不要求阶段 0 一次完成全部。

## 算力摸底与云资源门禁

先跑小样本再递增任务规模；不把官方“数千机器人并行”作为本机目标。

| 工作负载 | 实测配置 / 指标 | 本地结论 | 云路径 / 批准记录 |
|---|---|---|---|
| RTX 仿真与传感器 | 待测：场景、分辨率、相机数、帧率、显存峰值 | 待评估 | 未批准 |
| RL | 待测：任务、环境数、steps/s、显存峰值、异常 | 待评估 | 未批准 |
| 小型 BC | 待测：数据规模、模型、CPU/GPU耗时 | 待评估 | 未批准 |
| GR00T 推理 | 待测：模型、精度、camera/action配置、延迟、显存 | 待评估 | 未批准 |
| GR00T 微调 | 待测：可训练参数、batch、显存、每步耗时 | 待评估 | 未批准 |

决定使用 Brev 等云服务前必须填：

- 具体工作负载、软件/镜像和 GPU 型号；同时运行仿真时确认 RT Core 与显存余量。
- 预计运行时长、实例/存储/流量费与费用上限，明确谁批准；不能因课程免费推定算力免费。
- 停止条件、停机/删除步骤、数据备份与 checkpoint 导出位置；区分停止实例和持续存储计费。
- 先做短任务验证，达到费用上限或失败阈值立即停止；未获批准不得创建实例。

原生 Windows 某组件受阻时，先查版本与组件限制、降低规模；有条件再评估受支持的原生 Linux。WSL2 按具体版本作为实验支线，不是通用回退。无资源时可继续读代码/分析数据，但执行项保留受阻，不能用概念笔记冒充训练成功。

## 网络、资产与工具链

- 按**执行机器**核验代理。`127.0.0.1:10808` 仅在该机确有服务时可用，不能从 Mac 直接复制到 Windows/WSL/容器；国内直连时清理全部代理变量，包括 `all_proxy`。
- HF gated 模型、NVIDIA 下载、资产许可分别确认；凭据不写进仓库、日志或命令截图。
- 复用 VS Code + Copilot custom agents + MCP；长任务继续用独立 worktree。外部课程代码/skills 先审阅再执行。
- 数据、模型与大型二进制资产外置；参见 [制品规则](../results/README.md)。
