# 学习资源与官方证据

> 核对日期：2026-10-14。以第一方课程、文档和源码为依据；课程入口的 `latest` 会变化。下表标注的是**阅读优先级与计划范围**，不是已完成状态。课时是官方门户标注，不是个人完成预算。

## 核心与条件课程

[官方总入口：Physical AI Learning](https://docs.nvidia.com/learning/physical-ai/)。核心资源不用一次全部学完，围绕当前项目选章节。

| 资源 | 使用阶段 / 范围 | 官方标注课时 | 本计划阅读到哪里 |
|---|---|---|---|
| [Building Your First Robot in Isaac Sim](https://docs.nvidia.com/learning/physical-ai/getting-started-with-isaac-sim/latest/building-your-first-robot-in-isaac-sim/index.html) | 1 / 核心 | 入门路径 2–3h | 构建、物理、控制、传感器；ROS 桥接后置，HIL 排除 |
| [Physical AI Agent Bootcamp](https://docs.nvidia.com/learning/physical-ai/physical-ai-agent-bootcamp/latest/index.html) | 1–2 / 条件 | 自定节奏 | RTX viewer → SimReady physics；先确认环境，不要求未发布模块 |
| [Learn OpenUSD](https://docs.nvidia.com/learn-openusd/latest/index.html) | 0–2 / 核心章节 | 自定节奏 | stage/prim、坐标、layer、组合、资产结构；高级章节按需 |
| [Assembling Digital Twins](https://docs.nvidia.com/learning/physical-ai/assembling-digital-twins/latest/index.html) | 2 / 核心 | 3–4h | 资产组织、场景组合、验证；不扩成真实工厂集成 |
| [Train Your First Robot in Isaac Lab](https://docs.nvidia.com/learning/physical-ai/getting-started-with-isaac-lab/latest/train-your-first-robot-with-isaac-lab/index.html) | 3 / 核心 | 入门路径 3–4h | Cartpole 配置、训练、评估、修改；先小规模 |
| [GR00T E2E Workflow](https://docs.nvidia.com/learning/physical-ai/gr00t-e2e-workflow/latest/index.html) | 4 / 核心概念、条件运行 | 门户 4–12h | 数据/动作接口为阅读重点；仿真分支与实机分支区分 |
| [Sim-to-Real SO-101](https://docs.nvidia.com/learning/physical-ai/sim-to-real-so-101/latest/index.html) | 4 / 与 G1 条件运行择一 | 6–10h | 已有数据/模型与仿真评估；真实遥操作与部署排除 |

## 基础补齐与小实验

| 资源 | 用途 | 停止边界 |
|---|---|---|
| [Modern Robotics — Chapter 3: Rigid-Body Motions](https://modernrobotics.northwestern.edu/chapters/chapter3/) | C1：坐标系、旋转、齐次变换 | 能解释并验证一次坐标变换；不要求先修完整本书 |
| [OpenUSD — Installing usdview and Setting Up Python](https://docs.nvidia.com/learn-openusd/latest/usdview-install-instructions.html) | C2/C4：轻量 USD 工具与 API | 独立环境；USD 基础不必等待 Isaac Sim 可用 |
| [OpenUSD — Creating Composition Arcs](https://docs.nvidia.com/learn-openusd/latest/creating-composition-arcs/index.html) | C4：组合弧与前置章节清单 | 先学基础再进入，不把 UE 资产经验视为已掌握 USD |
| [Isaac Sim 5.1 — Replicator Getting Started Scripts](https://docs.isaacsim.omniverse.nvidia.com/5.1.0/replicator_tutorials/tutorial_replicator_getting_started.html) | C5：小型数据采集/随机化 | 少量样本 + manifest + 抽检；不先做大数据集 |
| [Hugging Face — Introduction to Deep Reinforcement Learning](https://huggingface.co/learn/deep-rl-course/unit1/introduction) | C6：RL 基础概念 | 按需补概念，不强制另修全部课程或上传模型 |
| [imitation — Train an Agent using Behavior Cloning](https://imitation.readthedocs.io/en/latest/tutorials/1_train_bc.html) | C7：小型 BC 的数据/训练/评价方法 | 作为方法参考，先核对其包依赖；不要求把该库装进 Sim 环境 |

BC 项目允许使用兼容的轻量实现与小型任务；验收契约由 [P4](projects.md) 定义，不照抄教程示例指标。分类动作报告准确率/交叉熵，连续动作报告 MAE/MSE；两者不可直接比较。

## 选择性拓展

| 资源 | 官方门户课时 | 选择条件 |
|---|---|---|
| [Getting Started With Isaac for Healthcare](https://docs.nvidia.com/learning/physical-ai/getting-started-with-isaac-for-healthcare/latest/index.html) | 3–4h | Agentic Workflows 与 Robotic Ultrasound 是独立分支，选一条；另查 OS/许可/算力 |
| [Accelerating Robot Learning With Isaac Lab and Newton](https://docs.nvidia.com/learning/physical-ai/getting-started-with-newton/latest/index.html) | 2h | 需要探索物理引擎、Franka IK、可变形物体时再学 |
| [Getting Started With Isaac ROS](https://docs.nvidia.com/learning/physical-ai/getting-started-with-isaac-ros/latest/index.html) | 2–3h | 有明确 ROS 2 加速工作负载；不是采购 Jetson 的理由 |
| [OpenUSD Development Professional 认证](https://www.nvidia.com/en-us/learn/certification/openusd-development-professional/) | 不作为学习时数 | D3 单独决定，核心学习不以取得证书为终点 |
| [Seeed reBot 合作课程](https://www.seeedstudio.com/sim-to-real-with-seeed-rebot-and-nvidia-isaac) | 门户标 20+h | 仅概念参考；实体课程已排除，来源是合作方而非 NVIDIA 自编课程 |

GTC 与生态动态只为解决当前问题而查阅，不设“全部收集”或“跟完会议”门槛。Cosmos 数据生成/增强作为条件扩展，不能仅因课程提到它就新增大型训练任务。

## 会影响学习顺序的核查结论

| 主题 | 实际证据 | 对规划的影响 |
|---|---|---|
| Bootcamp 前后依赖 | [SimReady physics 详细课程](https://docs.nvidia.com/learning/physical-ai/physical-ai-agent-bootcamp/latest/lab-2-simready-physics/index.html) 明确延续第一课 Attic Portal，并要求运行时物理证据 | 第二课不按独立新环境启动；用资产报告与 drop test 验收 |
| Bootcamp 发布/环境状态 | [课程首页](https://docs.nvidia.com/learning/physical-ai/physical-ai-agent-bootcamp/latest/index.html) 核对时部分课程为 Coming soon，本地设置说明仍有待发布项 | 不承诺“完成全部 hands-on”；再次执行时重查可用内容 |
| Digital Twins 资产/应用 | [Accessing the Course Assets](https://docs.nvidia.com/learning/physical-ai/assembling-digital-twins/latest/getting-started/course-application-access.html) 提供课程应用和平台步骤 | 使用对应 Kit 应用/资产，不能认为装过 Isaac Sim 就自动满足课程环境 |
| Isaac Lab 课程漂移 | [Get Started In Isaac Lab](https://docs.nvidia.com/learning/physical-ai/getting-started-with-isaac-lab/latest/train-your-first-robot-with-isaac-lab/05-create-and-install-a-new-external-project.html) 提示 Launchable 的 Lab 3.0 可能与课程不兼容 | 先锁版本，不把云预装镜像当作课程一致性保证 |
| G1 课程算力与输入设备 | [Prerequisites](https://docs.nvidia.com/learning/physical-ai/gr00t-e2e-workflow/latest/getting-started/prerequisites.html)：Linux/Docker、GR00T 1.7 后训练至少 48GB、自采需要支持的遥操作输入 | 无实体机器人可利用已有数据/模型；无输入设备不保证自行收集仿真演示 |
| SO-101 版本 | [Get the Code and Models](https://docs.nvidia.com/learning/physical-ai/sim-to-real-so-101/latest/06-get-the-code.html)：Sim 5.1.0、Lab 2.3.0、LeRobot 0.4.3、GR00T N1.6 | 与 G1/N1.7 分开，不合并依赖 |
| SO-101 仿真仍可能需要硬件 | [Domain Randomization / Teleop](https://docs.nvidia.com/learning/physical-ai/sim-to-real-so-101/latest/09-strategy1-dr-teleop.html) 要求遥操作臂；[Sim Evaluation](https://docs.nvidia.com/learning/physical-ai/sim-to-real-so-101/latest/11-sim-evaluation.html) 使用已有模型 | 无机械臂走现成数据/模型评价支线，不能承诺完整遥操作链路 |
| Cosmos 不是强制生成实验 | [Augmenting Datasets With Cosmos](https://docs.nvidia.com/learning/physical-ai/sim-to-real-so-101/latest/14-strategy3-cosmos.html) 提供预增强数据/策略用于比较 | 阅读和分析预生成数据不代表运行过 Cosmos；真实对比仍超出无硬件范围 |
| Healthcare 与 Newton | Healthcare 入口区分两个独立分支；Newton 另有独立课程入口（见上表） | 修正原路线课程归属，均不强制作为毕业条件 |

这些结论是页面核查，不是本机安装或算法实验结论。平台支持、GPU/显存数字差异与版本锁完整说明集中在 [环境文档](environment-windows.md)，不在此复制另一张配置真相表。

## 资料维护规则

- 当前阶段只保留少量主资源；先官方文档、代码和示例，二手教程用来解释而不是覆盖官方约束。
- 实践记录必须填课程 URL、访问日期、所用软件/模型 revision；`latest` 链接本身不是版本锁。
- 遇到冲突，区分“产品文档”“固定教程”“开发分支”“具体模型配置”，保留范围和来源后再决策。
- 重新进入某阶段或更换版本时核对该阶段来源；不要为了追新版反复重装已可用环境。
- 不把免费课程、官方演示性能或网页时长改写为免费云资源、本机性能保证或个人交付期限。
