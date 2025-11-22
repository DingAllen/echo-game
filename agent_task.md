# 🤖 智能体自主科研任务书：基于声望博弈的回音室效应研究

**项目代号：** PROJECT_ECHO_GAME

**执行角色：** Principal Investigator Agent (PI-Agent)

**最终交付物：** 一篇符合物理/复杂系统期刊（如 *Physical Review E* 或 *JASSS*）标准的学术论文 (PDF)。

## 🎯 核心目标 (Mission Objective)

构建一个基于**“信号传递博弈” (Signaling Game)** 的多智能体演化模型，探索“追求社会声望”（而非追求真理）如何导致社交网络中谣言的固化。必须定位到系统的**相变点 (Phase Transition)**，即人群从“理性共识”突变到“极端极化”的临界参数区域。

## ⚙️ 第一阶段：仿真内核构建 (Simulation Core)

**指令：** 编写 Python 模拟脚本。
**约束条件：** 必须使用 `numpy` 和 `networkx` 进行轻量级计算。

1. **网络拓扑：** 初始化一个 Watts-Strogatz 小世界网络 ($N=1000$, $k=10$, $p=0.1$)。
2. **Agent 属性：**
    - `opinion` (观点): 连续变量 $[-1, 1]$。
    - `reputation` (声望): 累积得分，初始为 0。
    - `strategy` (策略): 到底是“诚实表达”还是“迎合邻居”。
3. **博弈机制 (关键创新)：**
    - 在每一轮 $t$，Agent $i$ 决定传播什么观点 $O_i$。
    - **收益函数 (Utility Function)：**$$U_i = \alpha \cdot (\text{Local Conformity}) - \beta \cdot (\text{Global Truth Deviation})$$
        - $\alpha$ 项：如果 $O_i$ 与邻居的主流观点一致，获得声望（点赞）。
        - $\beta$ 项：如果 $O_i$ 与客观事实（设为 0）偏离太远，且被外部“Fact Checker”揭穿，扣除声望。
4. **演化规则：** Agent 会根据历史收益，用梯度下降法调整自己的 $\alpha$（对合群的渴望程度）。

## 🔄 第二阶段：自适应实验与评估循环 (Adaptive Experiment Loop)

**⚠️ 核心指令：** Agent 不得在运行一次后就停止。必须执行以下 `While` 循环，直到通过“学术发表标准检查”。

### 循环逻辑：

1. **参数扫描 (Parameter Sweep)：** 遍历 $\alpha \in [0, 1]$ 和 $\beta \in [0, 1]$。
2. **数据收集：** 记录每一组参数下的**极化指数 (Polarization Index)** 和 **收敛时间**。
3. **自动评估 (Auto-Critic)：**
    - **检查点 1 (非平凡性)：** 结果是否是一条直线？如果是，判定为**失败**（模型太简单）。
        - *Action:* 增加网络结构的异质性或引入“顽固分子”。
    - **检查点 2 (相变存在性)：** 是否观察到 $\alpha$ 超过某阈值 $\alpha_c$ 时，系统状态发生突变（Order Parameter 出现 Jump）？
        - *Action:* 如果相变不明显，精细化扫描步长，或调整收益函数的非线性程度。
    - **检查点 3 (鲁棒性)：** 重复运行 10 次，标准差是否过大？
        - *Action:* 增加蒙特卡洛模拟次数。

**✅ 通过标准：** 成功绘制出清晰的**相图 (Phase Diagram)**，且相变边界清晰可见。

## 📊 第三阶段：可视化与证据生成 (Visualization)

**指令：** 生成以下高清图表（保存为 `.png` 或 `.pdf`）：

1. **Fig 1 - 相图：** X轴为 $\alpha$（合群欲望），Y轴为 $\beta$（羞耻感），颜色代表最终的极化程度。需要展示出清晰的“相分离”边界。
2. **Fig 2 - 时间演化：** 展示在临界点附近，观点分布如何从“单峰（共识）”分裂为“双峰（对立）”。
3. **Fig 3 - 网络结构图：** 对节点进行着色，直观展示“回音室”的聚类情况。

## 📝 第四阶段：论文撰写与编译 (Paper Production)

**指令：** 只有当第三阶段通过后，才能启动 LaTeX 引擎。

1. **模板选择：** 使用标准的 `article` class 或 `revtex4-2`（如果环境支持）。
2. **LaTeX 结构要求：**
    - **Abstract:** 强调我们引入了“博弈论”机制，不仅仅是简单的传染模型。
    - **Model:** 清晰写出上述收益公式 $U_i$。
    - **Results:** 插入生成的 Fig 1, 2, 3。重点描述“相变点”的发现。
    - **Discussion:** 讨论这意味着什么（例如：只要社会对“合群”的奖励 $\alpha$ 高于对“真相”的坚持 $\beta$，回音室不可避免）。
3. **编译指令：**
    
    ```
    pdflatex main.tex
    bibtex main
    pdflatex main.tex
    pdflatex main.tex
    
    ```
    
4. **最终检查：** 确保 PDF 无乱码，图表引用正确。

## 📂 交付清单 (Deliverables)

1. `simulation.py`: 包含自动迭代逻辑的完整代码。
2. `data/`: 原始实验数据 (CSV)。
3. `figures/`: 3张关键图表。
4. `paper/main.tex`: LaTeX 源码。
5. `paper/main.pdf`: 最终学术论文。

**致 Agent：**
不要为了完成任务而完成任务。你的目标是**发现知识**。如果没有发现有趣的规律，请修改假设，直到发现为止。开始行动。
