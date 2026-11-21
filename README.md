# 强化学习与智能决策的跨学科理论及方法

**Interdisciplinary Theories and Methods for Reinforcement Learning and Intelligent Decision-Making**

本项目汇集博弈论、数学优化、控制理论、概率统计、统计物理和信息几何中的理论与方法，探索它们如何用于强化学习（Reinforcement Learning, RL）。


## 主题目录

1. [博弈论与策略交互](#1-博弈论与策略交互)
2. [平均场理论与群体动力学](#2-平均场理论与群体动力学)
3. [策略优化与学习动力学](#3-策略优化与学习动力学)
4. [均衡计算与博弈学习](#4-均衡计算与博弈学习)
5. [数学优化与问题分解](#5-数学优化与问题分解)
6. [约束、层次与多目标优化](#6-约束层次与多目标优化)
7. [规划、控制与动态规划](#7-规划控制与动态规划)
8. [概率建模与结构化推断](#8-概率建模与结构化推断)
9. [能量建模与统计物理](#9-能量建模与统计物理)
10. [不确定性、风险与鲁棒决策](#10-不确定性风险与鲁棒决策)
11. [信息几何、最优传输与分布优化](#11-信息几何最优传输与分布优化)

## 专题与案例

- [最优性与帕累托权衡](docs/theory/optimality-and-pareto.md) · [多目标 RL 与交通信号控制](docs/research/multi-objective-traffic-signal.md)
- [平均场方法](docs/theory/mean-field-methods.md) · [平均场 RL 与出行路线选择](docs/research/mean-field-route-choice.md)

[查看全部专题与标签](docs/index.md)

## 1. 博弈论与策略交互

*Game Theory and Strategic Interaction*

当每个主体的结果都取决于其他主体的选择时，用博弈模型描述收益、信息结构和行动次序。

**与强化学习的联系**　多智能体强化学习、协作与竞争、交通资源分配。 [相关均衡与计算方法](#4-均衡计算与博弈学习)

建模时先明确各方能看到什么、何时行动、收益如何耦合。以车辆合流为例，可用同时行动博弈描述双方各自选择让行或加速，用斯塔克尔伯格模型描述一方先承诺动作的情形，再用马尔可夫博弈纳入车速和距离随时间的变化。

### 交互模型

- **零和与一般和博弈（Zero-sum and General-sum Games）** — 零和博弈中各方收益之和为零，一般和博弈允许竞争、共同利益与协调需求同时存在。 [MIT · 博弈与基本解概念](https://ocw.mit.edu/courses/14.126-game-theory-spring-2024/mit14_126_s24_lecture_1_solution-concepts.pdf)
- **斯塔克尔伯格博弈（Stackelberg Game）** — 领导者先承诺策略，并在选择策略时预判跟随者的最优响应。 [Economics of Organizations · 斯塔克尔伯格产量竞争](https://colleen.quarto.pub/economics-of-organizations/stackelberg.html)
- **势博弈（Potential Game）** — 用一个共享势函数刻画各参与者单边改变行动时的收益变化或改进方向。 [Roughgarden · 势函数与纯策略均衡](https://theory.stanford.edu/~tim/f13/l/f13.pdf)
- **拥堵博弈（Congestion Game）** — 将参与者的成本写成所选资源的拥堵成本之和，经典模型中每项资源的拥堵成本由使用人数决定。 [Heller · 拥堵博弈与势函数实例](https://r-heller.github.io/equilibria/tutorials/network-games/congestion-games-potential/)
- **贝叶斯博弈（Bayesian Game）** — 用类型刻画参与者的私有信息，使最优响应取决于对其他主体类型的信念。 [Yıldız · 博弈论讲义中的不完全信息博弈](https://ocw.mit.edu/courses/14.126-game-theory-spring-2024/mit14_126_s24_yildiz-lecture-notes.pdf)
- **重复博弈（Repeated Game）** — 多次进行同一个阶段博弈，使当前行动可以依赖过去的交互历史。 [Yıldız · 博弈论讲义中的重复博弈](https://ocw.mit.edu/courses/14.126-game-theory-spring-2024/mit14_126_s24_yildiz-lecture-notes.pdf)
- **马尔可夫博弈（Markov Game）** — 多个主体的联合行动共同决定即时收益和状态转移，从而把策略交互扩展到序贯决策。 [Littman · 从 MDP 到马尔可夫博弈](https://aima.eecs.berkeley.edu/~russell/classes/cs294/f21/papers/Littman_ICML94_Markov_Games.pdf)

### 均衡、合作与激励

- **纳什均衡（Nash Equilibrium）** — 给定其他主体的策略，每个主体都无法通过单独改变自己的策略来提高期望收益。 [MIT · 最优响应与纳什均衡](https://ocw.mit.edu/courses/14.126-game-theory-spring-2024/mit14_126_s24_lecture_1_solution-concepts.pdf)
- **合作博弈（Cooperative Game Theory）** — 研究联盟可以实现的收益及其在成员之间的分配。 [MIT · 联盟、核与 Shapley 值](https://ocw.mit.edu/courses/14-126-game-theory-spring-2016/a4d0a3949ab29c2a2f55442a9723d205_MIT14_126S16_noncoop.pdf)
- **联盟形成（Coalition Formation）** — 研究主体为何结成特定联盟，以及成员退出或重组的激励如何影响联盟稳定性。 [Bogomolnaia 与 Jackson · 偏好与联盟稳定性](https://doi.org/10.1006/game.2001.0877)
- **机制设计（Mechanism Design）** — 从期望实现的结果反推交互规则，使参与者基于自身利益作出的选择能够实现目标。 [Roughgarden · 机制设计基础与拍卖](https://theory.stanford.edu/~tim/f13/l/l2.pdf)

## 2. 平均场理论与群体动力学

*Mean-field Theory and Population Dynamics*

用群体分布或宏观统计量描述大量主体的集体效应，并研究个体决策与群体演化如何相互影响。

**与强化学习的联系**　大规模多智能体学习、交通流与车群控制、分布式资源分配。 [均值场变分近似](#后验推断与计算) · [统计物理中的平均场](#宏观近似与计算)

同样是用群体分布描述交通流，平均场博弈可以研究驾驶者各自作最优响应时形成的流量，平均场控制可以研究以全网延误为目标的协调策略。两者的区别体现在优化目标和群体分布进入方程的方式。

[平均场方法对照](docs/theory/mean-field-methods.md) · [出行路线选择案例](docs/research/mean-field-route-choice.md)

### 大规模主体建模

- **平均场近似（Mean-field Approximation）** — 在适当的大群体与交互假设下，用群体分布或其统计量近似其他主体对单个主体的总体影响。 [Yang 等 · 用邻域平均行动近似个体交互](https://proceedings.mlr.press/v80/yang18d.html)
- **平均场博弈（Mean-field Game, MFG）** — 求一个群体分布，使代表性主体对它的最优响应共同生成同一个分布。 [Carmona 等 · 平均场博弈建模与数值方法](https://arxiv.org/abs/2107.04568)
- **平均场控制（Mean-field Control, MFC）** — 把群体分布纳入系统动态，选择控制规则来优化整体目标。 [Carmona 等 · 平均场控制与平均场博弈对比](https://pmc.ncbi.nlm.nih.gov/articles/PMC7197015/)
- **平均场强化学习（Mean-field Reinforcement Learning）** — 在动力学或收益未知时，利用群体统计量来学习大规模交互系统中的策略或价值。 [Yang 等 · 平均场 Q 学习与 Actor–Critic](https://proceedings.mlr.press/v80/yang18d.html)
- **异质群体模型（Heterogeneous Population Models）** — 为具有不同目标、动力学或信息条件的主体设置类型，并用分类分布描述群体交互。 [Cui 与 Koeppl · 用图极限描述异质交互](https://arxiv.org/abs/2112.01280)

### 群体状态与演化

- **群体博弈（Population Games）** — 用群体中的策略占比表示交互状态，并让各策略的收益依赖这些占比。 [Sandholm · 群体博弈的状态与收益](https://users.ssc.wisc.edu/~whs/research/ded.pdf)
- **群体动力学（Population Dynamics）** — 建立随时间演化的方程，描述群体的规模、状态分布或策略比例如何变化。 [Sandholm · 群体策略修正规则与确定性动力学](https://users.ssc.wisc.edu/~whs/research/ded.pdf)
- **复制者动力学（Replicator Dynamics）** — 高于群体平均收益的策略占比增长，低于平均收益的策略占比下降。 [Sandholm · 复制者方程的定义与性质](https://users.ssc.wisc.edu/~whs/research/ded.pdf)
- **演化稳定策略（Evolutionarily Stable Strategy, ESS）** — 当少量主体改用其他策略时，原有策略仍能保持适应度优势。 [Sandholm · 演化稳定性与局部稳定性](https://users.ssc.wisc.edu/~whs/research/ded.pdf)
- **福克–普朗克方程（Fokker–Planck Equation）** — 通过漂移与扩散项描述随机动力系统的状态概率密度如何随时间演化。 [Pavliotis · 从随机微分方程到概率密度演化](https://www.ma.imperial.ac.uk/~pavl/PavliotisBook.pdf)

## 3. 策略优化与学习动力学

*Policy Optimization and Learning Dynamics*

研究策略更新所依据的梯度、几何、正则化与反馈，以及这些选择如何影响学习过程。

**与强化学习的联系**　理解 TRPO 的信赖域与 PPO 的近端更新设计，比较不同更新规则的稳定性和样本效率。 [分布几何工具](#11-信息几何最优传输与分布优化)

比较策略更新时，可以分别问更新要提高什么目标、用什么量衡量策略变化、如何控制每一步的幅度。自然梯度着重于局部度量，信赖域直接限制更新范围，熵正则则改变所优化的目标。

### 梯度、几何与更新幅度

- **策略梯度方法（Policy Gradient Methods）** — 估计期望回报对策略参数的梯度，并用它构造梯度上升更新。 [Spinning Up · 策略梯度推导](https://spinningup.openai.com/en/latest/spinningup/rl_intro3.html) · [《动手学强化学习》中文实例 · 策略梯度与 REINFORCE](https://hrl.boyuai.com/chapter/2/%E7%AD%96%E7%95%A5%E6%A2%AF%E5%BA%A6%E7%AE%97%E6%B3%95/)
- **自然梯度（Natural Gradient）** — 用 [Fisher 信息度量](#度量散度与参数几何)调整梯度，使局部更新反映策略分布的变化幅度。 [Kakade · 自然策略梯度](https://proceedings.neurips.cc/paper/2001/hash/4b86abe48d358ecf194c56c69108433e-Abstract.html)
- **镜像下降（Mirror Descent）** — 用由镜像势函数诱导的 Bregman 散度定义更新代价，使迭代适应变量的几何结构。 [Bubeck · 镜像下降与非欧几里得优化](https://arxiv.org/abs/1405.4980)
- **镜像策略优化（Mirror Policy Optimization）** — 在策略空间中结合回报或优势的局部估计与散度惩罚，求出下一步策略。 [Tomar 等 · 镜像下降在策略空间中的实现](https://arxiv.org/abs/2005.09814)
- **信赖域方法（Trust Region Methods）** — 将更新限制在局部近似可信的区域内，例如用 KL 散度限制策略变化。 [Spinning Up · TRPO 的目标与 KL 约束](https://spinningup.openai.com/en/latest/algorithms/trpo.html)
- **近端优化（Proximal Optimization）** — 通过[近端子问题](#对偶分解与迭代)平衡策略目标的改进与相对当前策略的变化幅度。 [Parikh 与 Boyd · 近端算子与算法](https://web.stanford.edu/~boyd/papers/prox_algs.html)

### 在线反馈与演化式更新

- **在线凸优化（Online Convex Optimization, OCO）** — 每轮先选决策再获得凸损失反馈，并用累计遗憾衡量表现。 [Hazan · 在线凸优化教材](https://arxiv.org/abs/1909.05207)
- **正则化的跟随领导者（Follow-the-Regularized-Leader, FTRL）** — 每轮根据已观察到的累计损失与正则项选择新决策。 [McMahan · FTRL 与镜像下降](https://jmlr.org/papers/v18/14-428.html)
- **熵正则化优化（Entropy-Regularized Optimization）** — 在回报目标中加入策略熵奖励，以提高随机性并平滑策略选择。 [Spinning Up · SAC 与最大熵目标](https://spinningup.openai.com/en/latest/algorithms/sac.html)
- **基于复制者动力学的策略更新（Replicator-based Policy Updates）** — 根据动作相对当前策略平均收益的优势调整其概率质量。 [Hennes 等 · Neural Replicator Dynamics](https://arxiv.org/abs/1906.00190)
- **演化优化（Evolutionary Optimization）** — 通过选择、变异或重组逐步改进一组候选解，可用于无需显式梯度的策略搜索。 [OpenAI 技术博客 · 用演化策略搜索 RL 策略](https://openai.com/index/evolution-strategies/)

## 4. 均衡计算与博弈学习

*Equilibrium Computation and Learning in Games*

先确定能够检验的均衡概念，再研究交互规则或数值算法在什么条件下能逼近均衡。

**与强化学习的联系**　多智能体学习的均衡分析、鞍点求解与均衡间隙评估。 [纳什均衡与博弈模型](#1-博弈论与策略交互)

阅读收敛结果时要区分最后一次策略与历史行动的经验分布。在有限重复博弈中，各方平均外部遗憾趋零给出经验分布逼近粗相关均衡的条件，相关均衡还要检验根据推荐动作进行的偏离。

### 均衡概念与学习动态

- **相关均衡（Correlated Equilibrium, CE）** — 在给定私人行动建议后，每个主体都没有通过依建议单边改选而获益的动机。 [Hart 与 Mas-Colell · 相关均衡的激励约束](https://math.huji.ac.il/~hart/papers/adapt.pdf)
- **粗相关均衡（Coarse Correlated Equilibrium, CCE）** — 在收到建议之前，每个主体都没有预先改用某个固定行动来提高期望收益的动机。 [Roughgarden · 外部遗憾与粗相关均衡](https://theory.stanford.edu/~tim/f13/l/l17.pdf)
- **最佳响应动力学（Best Response Dynamics）** — 主体反复根据其他主体的当前策略作出最佳响应，使联合策略随更新规则演化。 [Sandholm · 最佳响应动力学](https://users.ssc.wisc.edu/~whs/research/ded.pdf)
- **虚拟博弈（Fictitious Play）** — 主体用对手历史行动的经验频率估计其策略，并对该估计作最佳响应。 [Heller · 虚拟博弈及其收敛示例](https://r-heller.github.io/equilibria/tutorials/ml-and-gt/fictitious-play-convergence/index.html)
- **遗憾匹配（Regret Matching）** — 将改选其他行动的概率与相应的正遗憾挂钩，在适用的重复博弈中可使经验联合分布趋近相关均衡集合。 [Hart 与 Mas-Colell · 遗憾匹配更新与收敛定理](https://math.huji.ac.il/~hart/papers/adapt.pdf)
- **无悔学习（No-regret Learning）** — 设定一类允许事后比较的替代决策，并让相对于这些决策的平均遗憾随轮次趋于零。 [Roughgarden · 无悔动态课程讲义](https://theory.stanford.edu/~tim/f13/l/l17.pdf)

### 数值刻画与求解工具

- **变分不等式（Variational Inequalities, VI）** — 用算子与所有可行比较方向的内积不等式统一刻画一类最优点、鞍点与均衡。 [Nemirovski · 单调变分不等式的建模与求解](https://www2.isye.gatech.edu/~nemirovs/SIOPT_MP_2004.pdf)
- **单调算子理论（Monotone Operator Theory）** — 用算子差与输入差的内积非负性刻画其结构，为分析求解过程提供条件。 [Ryu 与 Boyd · 单调算子教程](https://web.stanford.edu/~boyd/papers/monotone_primer.html)
- **外梯度方法（Extragradient Methods）** — 先用当前位置的算子值预测一步，再用预测点的算子值校正从原位置出发的更新。 [Nemirovski · 外梯度及其近端推广](https://www2.isye.gatech.edu/~nemirovs/SIOPT_MP_2004.pdf)
- **镜像近端算法（Mirror-Prox Algorithm）** — 用 Bregman 几何执行预测和校正两次近端更新，以求解一类单调变分不等式。 [Nemirovski · Mirror-Prox 论文与收敛分析](https://www2.isye.gatech.edu/~nemirovs/SIOPT_MP_2004.pdf)
- **不动点方法（Fixed-point Methods）** — 将目标解写成在某个映射下保持不变的点，并在适用条件下通过迭代逼近它。 [Ryu 与 Boyd · 不动点迭代与算子分裂](https://web.stanford.edu/~boyd/papers/monotone_primer.html)

## 5. 数学优化与问题分解

*Mathematical Optimization and Decomposition*

根据目标函数、可行域和变量耦合方式，选择合适的建模形式与求解算法。

**与强化学习的联系**　占用测度求解、分布式策略学习、调度与资源分配。 [约束处理与层次结构](#6-约束层次与多目标优化)

问题结构决定求解器的选择。例如，多路口各自拥有信号配时变量，而相邻路口通过车流约束耦合，可以先检查能否按路口分块，再考虑用对偶分解或 ADMM 协调。

### 问题结构

- **凸优化（Convex Optimization）** — 在凸可行域上最小化凸函数，使局部最优解同时也是全局最优解。 [Boyd 与 Vandenberghe · 凸优化教材第 4 章](https://web.stanford.edu/~boyd/cvxbook/bv_cvxbook.pdf)
- **非凸优化（Non-convex Optimization）** — 针对目标或可行域不满足凸性的情形，借助问题结构研究驻点、局部解或全局解。 [Jin 等 · 非凸优化中逃离鞍点的一个结果](https://proceedings.mlr.press/v70/jin17a.html)
- **线性规划（Linear Programming, LP）** — 以线性目标和线性等式或不等式描述连续决策，可用于表示适用条件下的占用测度优化。 [Boyd 与 Vandenberghe · 线性规划 §4.3](https://web.stanford.edu/~boyd/cvxbook/bv_cvxbook.pdf)
- **二次规划（Quadratic Programming, QP）** — 在通常为线性的约束下优化二次目标，可用来表达跟踪误差和控制代价。 [Boyd 与 Vandenberghe · 二次规划 §4.4](https://web.stanford.edu/~boyd/cvxbook/bv_cvxbook.pdf)
- **整数规划（Integer Programming, IP）** — 要求决策变量取整数值，以刻画选择、指派和调度等离散结构。 [MIT · 整数规划与组合优化讲义](https://ocw.mit.edu/courses/15-083j-integer-programming-and-combinatorial-optimization-fall-2009/pages/lecture-notes/)
- **混合整数规划（Mixed-Integer Programming, MIP）** — 将连续变量和整数变量放在同一模型中，联合描述数量分配、开关或组合选择。 [MOSEK 建模手册 · 混合整数建模与实例](https://docs.mosek.com/modeling-cookbook/mio.html)
- **次模优化（Submodular Optimization）** — 利用集合函数的边际收益递减性质，分析选址、覆盖等离散优化问题。 [Bach · 次模函数与凸优化教程](https://arxiv.org/abs/1111.6453)

### 最优性判定

- **局部最优与全局最优（Local and Global Optima）** — 局部最优只在邻域内成立，而全局最优需要与整个可行域比较。 [专题 · 最优性与帕累托权衡](docs/theory/optimality-and-pareto.md#单目标如何判定最优)
- **一阶与二阶最优性条件（First- and Second-Order Optimality Conditions）** — 对二阶可微的无约束问题，可以用梯度和 Hessian 判断候选点能否成为局部极小值。 [Boyd 与 Vandenberghe · 无约束最小化第 9 章](https://web.stanford.edu/~boyd/cvxbook/bv_cvxbook.pdf)

### 对偶、分解与迭代

- **拉格朗日对偶（Lagrangian Duality）** — 为约束引入乘子并构造对偶问题，以界定原问题的最优值并利用可分结构。 [Boyd 与 Vandenberghe · 对偶性第 5 章](https://web.stanford.edu/~boyd/cvxbook/bv_cvxbook.pdf)
- **近端方法（Proximal Methods）** — 通过求解带距离惩罚的局部子问题，处理非光滑项、正则项或约束。 [Parikh 与 Boyd · 常用近端算子和实例](https://web.stanford.edu/~boyd/papers/prox_algs.html)
- **交替方向乘子法（Alternating Direction Method of Multipliers, ADMM）** — 交替求解变量分块的子问题，并更新乘子以协调耦合约束。 [Boyd 等 · ADMM 教程与分布式应用](https://web.stanford.edu/~boyd/papers/admm_distr_stats.html)
- **对偶分解（Dual Decomposition）** — 用共享乘子为耦合约束定价，使各子问题可以独立求解后再协调。 [Stanford · 分解方法讲义](https://web.stanford.edu/class/ee364b/lectures.html)
- **坐标下降（Coordinate Descent）** — 固定其余变量，逐次更新一个坐标或一组坐标。 [Wright · 坐标下降算法综述](https://arxiv.org/abs/1502.04759)
- **Frank–Wolfe 算法（Frank–Wolfe Algorithm）** — 在可行域上求解目标的一阶线性近似，再朝该线性子问题的解移动。 [Jaggi · 无投影优化与对偶间隙](https://proceedings.mlr.press/v28/jaggi13.html)

## 6. 约束、层次与多目标优化

*Constrained, Hierarchical, and Multi-objective Optimization*

区分必须满足的约束、不同目标间的权衡，以及上下层决策之间的响应关系。

**与强化学习的联系**　安全与资源约束策略学习、层次决策、多目标策略评估。

目标、约束和层级对应不同的决策结构。例如，平均延误可以作为优化目标，超出队列上限的概率可以作为约束，下层驾驶者对上层收费规则的响应可以形成双层问题。

### 约束建模与处理

- **约束马尔可夫决策过程（Constrained Markov Decision Process, CMDP）** — 在序贯回报优化中加入期望累计成本等约束，以表达预算或资源上限。 [Achiam 等 · CMDP 定义与约束策略优化](https://proceedings.mlr.press/v70/achiam17a.html)
- **拉格朗日松弛（Lagrangian Relaxation）** — 将选定约束通过乘子移入目标函数，使原问题转化为更容易处理的松弛子问题。 [Stanford · 对偶与松弛讲义](https://web.stanford.edu/class/ee364a/lectures.html)
- **原始–对偶优化（Primal–Dual Optimization）** — 联合更新决策变量和约束乘子，使收益改进与约束满足相互协调。 [Tessler 等 · 约束 RL 中的策略与乘子更新](https://arxiv.org/abs/1805.11074)
- **KKT 条件（Karush–Kuhn–Tucker Conditions）** — 用驻点、原始可行性、对偶可行性和互补松弛刻画带约束问题的候选最优解。 [Boyd 与 Vandenberghe · 最优性条件 §5.5](https://web.stanford.edu/~boyd/cvxbook/bv_cvxbook.pdf)
- **惩罚函数方法（Penalty Methods）** — 将违反约束的程度计入目标，并通过惩罚权重控制可行性与原目标之间的权衡。 [Bertsekas · 非线性规划课程第 16 讲](https://ocw.mit.edu/courses/6-252j-nonlinear-programming-spring-2003/resources/6252_slides16/)
- **障碍函数方法（Barrier Methods）** — 在目标中加入靠近可行域边界时增大的代价，使迭代从内部逼近受约束最优解。 [Boyd 与 Vandenberghe · 内点法第 11 章](https://web.stanford.edu/~boyd/cvxbook/bv_cvxbook.pdf)
- **机会约束优化（Chance-Constrained Optimization）** — 要求不确定条件下的约束以至少指定概率成立。 [Nemirovski 与 Shapiro · 机会约束与凸近似](https://www2.isye.gatech.edu/~nemirovs/ChanceConstr-Nov14.pdf)

[最优性与帕累托权衡](docs/theory/optimality-and-pareto.md#多目标如何选解) · [交通信号控制案例](docs/research/multi-objective-traffic-signal.md)

### 决策层级与目标权衡

- **双层优化（Bilevel Optimization）** — 将下层优化问题的最优解纳入上层的目标或约束，使上层决策显式依赖下层响应。 [Colson 等 · 双层优化形式与应用](https://www.iro.umontreal.ca/~marcotte/ARTIPS/AOR2007.pdf)
- **层次优化（Hierarchical Optimization）** — 按决策层级或优先级组织多个优化问题，并明确各层如何传递约束、目标或解。 [Gurobi · 按优先级优化多个目标的实例](https://docs.gurobi.com/projects/optimizer/en/current/features/multiobjective.html)
- **多目标优化（Multi-objective Optimization）** — 同时处理多个目标，并用帕累托最优等概念描述可行的权衡。 [Boyd 与 Vandenberghe · 向量优化与帕累托解 §4.7](https://web.stanford.edu/~boyd/cvxbook/bv_cvxbook.pdf)
- **帕累托最优与前沿（Pareto Optimality and Frontier）** — 找出无法在保持其他目标表现的同时改进任一目标的可行解，再用其目标向量描述可达到的权衡。 [专题 · 帕累托支配与偏好](docs/theory/optimality-and-pareto.md#多目标如何选解)
- **标量化与 ε-约束（Scalarization and ε-Constraint）** — 用权重把多个目标合成一个标量，或保留主目标并将其余指标写为预算，两种做法可能选择不同的策略。 [案例 · 四种信号策略的比较](docs/research/multi-objective-traffic-signal.md#用四个候选策略说明选择过程)
- **分布鲁棒优化（Distributionally Robust Optimization, DRO）** — [在候选概率分布集合上优化最坏情形表现](#10-不确定性风险与鲁棒决策)，可用于分布存在估计误差时的约束设计。 [Kuhn 等 · 分布集合与最坏期望](https://arxiv.org/abs/1908.08729)

## 7. 规划、控制与动态规划

*Planning, Control, and Dynamic Programming*

利用系统模型与状态反馈，研究怎样协调当前行动、未来收益和系统约束。

**与强化学习的联系**　基于模型的 RL、滚动规划、轨迹生成与闭环安全。

可以沿着 MDP、贝尔曼方程、动态规划的顺序阅读离散时间模型，再看连续时间的 HJB 方程。实际控制若需要根据新观测在线修正，可从 MPC 的滚动求解开始。

### 序贯建模与最优性

- **马尔可夫决策过程（Markov Decision Process, MDP）** — 用状态、动作、转移和奖励描述序贯决策，其中给定当前状态和动作即可确定下一步的条件分布。 [UC Berkeley CS188 · MDP 定义与示例](https://inst.eecs.berkeley.edu/~cs188/textbook/mdp/markov-decision-processes.html) · [《动手学强化学习》中文实例 · MDP 与价值函数](https://hrl.boyuai.com/chapter/1/%E9%A9%AC%E5%B0%94%E5%8F%AF%E5%A4%AB%E5%86%B3%E7%AD%96%E8%BF%87%E7%A8%8B/)
- **部分可观测马尔可夫决策过程（Partially Observable Markov Decision Process, POMDP）** — 当真实状态不可直接观测时，用观测历史更新对隐藏状态的信念并据此决策。 [Kaelbling 等 · 信念状态与 POMDP 规划](https://people.smp.uq.edu.au/YoniNazarathy/Control4406_2014/resources/KaelblingLittmanCassandra1998.pdf)
- **占用测度（Occupancy Measure）** — 统计策略在各状态–动作对上的访问量，有限折扣 MDP 中可将期望回报和累计成本写成占用测度的线性函数。 [EPFL · 线性规划视角下的强化学习](https://www.epfl.ch/labs/lions/wp-content/uploads/2024/08/Lecture-3_-RL-via-Linear-Programming.pdf)
- **动态规划（Dynamic Programming, DP）** — 把跨时间的优化分解为按状态或阶段递推的子问题。 [Tedrake · 动态规划与控制实例](https://underactuated.mit.edu/dp.html)
- **贝尔曼方程（Bellman Equation）** — 通过即时收益与下一步价值的关系刻画策略价值，或通过对行动取最优来刻画最优价值。 [UC Berkeley CS188 · 贝尔曼递推与价值迭代](https://inst.eecs.berkeley.edu/~cs188/textbook/mdp/value-iteration.html)
- **最优控制（Optimal Control）** — 在满足系统动力学和约束的条件下选择控制输入，以优化给定的性能指标。 [Liberzon · 最优控制公开教材](https://liberzon.csl.illinois.edu/teaching/cvoc/)
- **随机最优控制（Stochastic Optimal Control）** — 在随机扰动下选择随信息更新的控制策略，以优化期望或风险敏感的累积目标。 [Bertsekas · 动态规划与随机控制课程](https://ocw.mit.edu/courses/6-231-dynamic-programming-and-stochastic-control-fall-2015/)
- **哈密顿–雅可比–贝尔曼方程（Hamilton–Jacobi–Bellman Equation, HJB）** — 将连续时间的动态规划原理写成刻画价值函数的偏微分方程。 [Liberzon · 动态规划与 HJB 章节](https://liberzon.csl.illinois.edu/teaching/cvoc/node91.html)
- **庞特里亚金极大值原理（Pontryagin Maximum Principle, PMP）** — 通过状态、伴随变量和哈密顿量给出最优轨迹与控制必须满足的条件。 [Liberzon · 极大值原理的推导与例题](https://liberzon.csl.illinois.edu/teaching/cvoc/node61.html)

### 规划、稳定性与安全

- **模型预测控制（Model Predictive Control, MPC）** — 每一步求解有限时域控制问题，执行首个动作后用新观测重新规划。 [Tedrake · 轨迹优化讲义中的 MPC](https://underactuated.mit.edu/trajopt.html) · [《动手学强化学习》中文实例 · 模型预测控制](https://hrl.boyuai.com/chapter/3/%E6%A8%A1%E5%9E%8B%E9%A2%84%E6%B5%8B%E6%8E%A7%E5%88%B6/)
- **轨迹优化（Trajectory Optimization）** — 直接搜索满足动力学和任务约束的状态与控制序列，使轨迹成本最小。 [Tedrake · 射击法、直接转录与配点](https://underactuated.mit.edu/trajopt.html)
- **控制障碍函数（Control Barrier Functions, CBF）** — 约束控制输入使安全集合保持前向不变，从而在相应条件下维持系统安全。 [Ames 等 · 安全集合不变性与 CBF-QP](https://arxiv.org/abs/1903.11199)
- **李雅普诺夫稳定性理论（Lyapunov Stability Theory）** — 借助沿系统轨迹的标量函数变化，判断平衡点的稳定性及在更强条件下的收敛。 [Tedrake · Lyapunov 稳定性与吸引域](https://underactuated.mit.edu/lyapunov.html)
- **鲁棒控制（Robust Control）** — 针对给定的模型误差或扰动范围设计控制器，以保持稳定性或性能保证。 [Tedrake · 不确定性建模与鲁棒控制](https://underactuated.mit.edu/robust.html)
- **可达性分析（Reachability Analysis）** — 计算系统在给定动力学、时间范围及允许输入下可能到达的状态集合。 [Bansal 等 · Hamilton–Jacobi 可达性教程](https://arxiv.org/abs/1709.07523)

## 8. 概率建模与结构化推断

*Probabilistic Modeling and Structured Inference*

用概率分布和变量依赖结构表达未知状态，并在获得观测后更新信念。

**与强化学习的联系**　隐状态估计、信念状态规划、基于概率模型的决策。

建模时先明确隐藏变量和依赖结构，再选择推断方法。以交通状态估计为例，HMM 可以描述不可直接观测的拥堵状态，获得新传感器数据后可用滤波更新其后验分布。

### 变量依赖与概率表示

- **概率图模型（Probabilistic Graphical Models, PGM）** — 利用图表达条件独立性和分解结构，使联合分布的建模与推断可以利用局部关系。 [Stanford CS228 · 图模型表示与推断](https://kuleshov.github.io/cs228-notes/)
- **贝叶斯网络（Bayesian Networks）** — 用有向无环图将联合分布分解为每个变量在其父节点条件下的概率。 [UC Berkeley CS188 · 贝叶斯网络的结构与分解](https://inst.eecs.berkeley.edu/~cs188/textbook/bayes-nets/)
- **马尔可夫随机场（Markov Random Fields, MRF）** — 用无向图描述局部条件依赖，并用相互作用势函数表达联合分布。 [MIT · 概率图模型教材中的无向模型](https://visionbook.mit.edu/graphical_models.html)
- **条件随机场（Conditional Random Fields, CRF）** — 给定观测后，用带图结构的条件分布刻画相互依赖的输出变量。 [Lafferty 等 · 线性链 CRF 与序列标注](https://home.cs.colorado.edu/~mozer/Teaching/syllabi/6622/papers/LaffertyMcCallumPereira2001.pdf)
- **因子图（Factor Graphs）** — 用变量节点和因子节点组成的二分图明确表示分布如何分解为局部因子的乘积。 [Kschischang 等 · 因子图与和积算法](https://www.isiweb.ee.ethz.ch/papers/arch/aloe-2001-1.pdf)
- **隐马尔可夫模型（Hidden Markov Models, HMM）** — 用一条不可直接观察的马尔可夫状态链解释观测序列的生成过程。 [UC Berkeley CS188 · HMM、滤波和预测](https://inst.eecs.berkeley.edu/~cs188/textbook/hmms/)

### 后验推断与计算

- **贝叶斯推断（Bayesian Inference）** — 用似然将先验更新为后验，在获得观测后重新量化对未知量的信念。 [Bayes Rules! · 贝叶斯法则与后验分布](https://www.bayesrulesbook.com/chapter-2)
- **置信传播（Belief Propagation）** — 在图上交换局部消息以计算边缘分布，可在树结构上得到精确结果。 [Kschischang 等 · 树上的和积消息传递](https://www.isiweb.ee.ethz.ch/papers/arch/aloe-2001-1.pdf)
- **变分推断（Variational Inference）** — 将后验近似转化为在选定分布族内优化散度或证据下界的问题。 [Blei 等 · ELBO 与变分推断教程](https://arxiv.org/abs/1601.00670)
- **均值场变分近似（Mean-field Variational Approximation）** — 将变分分布限制为独立因子的乘积，以降低后验近似的计算成本。 [Blei 等 · 因子化近似与坐标更新](https://www.cs.columbia.edu/~blei/papers/BleiKucukelbirMcAuliffe2017.pdf)
- **马尔可夫链蒙特卡洛（Markov Chain Monte Carlo, MCMC）** — 构造以目标分布为平稳分布的马尔可夫链，并在相应遍历条件下用样本估计分布性质。 [Betancourt · MCMC 原理与 HMC 的构造](https://arxiv.org/abs/1701.02434)

## 9. 能量建模与统计物理

*Energy-based Modeling and Statistical Physics*

从能量、熵和局部相互作用出发，解释系统分布、集体行为和搜索过程。

**与强化学习的联系**　能量策略、最大熵建模、组合决策搜索与群体涌现分析。

玻尔兹曼分布把能量变成概率，温度控制分布的集中程度。能量模型可用于表示对候选动作的偏好，模拟退火则用温度调度控制搜索配置的过程。

### 用能量表示结构与分布

- **能量模型（Energy-based Models, EBM）** — 给状态或配置赋予标量能量，以较低能量表示模型更偏好的配置。 [LeCun 等 · 能量建模与学习教程](https://cs.nyu.edu/~yann/talks/lecun-tutorial-nips-2006.pdf)
- **玻尔兹曼分布（Boltzmann Distribution）** — 令概率与 exp(−能量 / 温度尺度) 成正比，使温度控制概率在低能状态上的集中程度。 [Tong · 正则系综与玻尔兹曼权重](https://www.damtp.cam.ac.uk/user/tong/statphys/statmechhtml/S1.html)
- **玻尔兹曼机（Boltzmann Machines）** — 用随机二值单元之间的相互作用定义能量与联合分布，从而学习变量间的依赖。 [Hinton · 玻尔兹曼机及其训练](https://www.cs.utoronto.ca/~hinton/csc321/readings/boltz321.pdf)
- **伊辛模型（Ising Model）** — 用二态自旋、局部耦合和外场描述大量简单双态变量的集体行为。 [Tong · 伊辛模型与相变](https://davidtong.org/teaching/statistical-physics/statmechhtml/S5)
- **波茨模型（Potts Model）** — 将二态自旋扩展为多态变量，用相邻变量取相同状态时的耦合刻画局部相互作用。 [Beaudin 等 · 从图结构推导 Potts 模型及配分函数](https://arxiv.org/abs/0804.2468)

### 宏观近似与计算

- **自由能（Free Energy）** — 亥姆霍兹自由能将内部能量和熵组合为温度相关的势，用来刻画恒温条件下的平衡。 [Tong · 配分函数、熵与亥姆霍兹自由能](https://www.damtp.cam.ac.uk/user/tong/statphys/statmechhtml/S1.html)
- **最大熵原理（Maximum Entropy Principle）** — 在满足已知统计约束的所有分布中，选取熵最大的分布。 [Jaynes · 最大熵与统计力学原论文](https://wwwusers.ts.infn.it/~milotti/Didattica/Bayes/pdfs/Jaynes_1957a.pdf)
- **统计物理中的平均场理论（Mean-field Theory）** — 用自洽的有效场代替复杂的局部相互作用，把多体问题化为较易分析的近似模型。 [Tong · 伊辛模型的平均场推导](https://davidtong.org/teaching/statistical-physics/statmechhtml/S5)
- **能量景观（Energy Landscape）** — 用能量函数刻画配置空间中的低能区域和势垒，以分析亚稳态及搜索难度。 [Ballard 等 · 能量景观与机器学习](https://arxiv.org/abs/1703.07915)
- **模拟退火（Simulated Annealing）** — 通过逐步降低温度，从有概率接受较差解的广域搜索过渡到偏向低能解的搜索。 [Kirkpatrick 等 · 模拟退火原论文](https://www2.stat.duke.edu/~scs/Courses/Stat376/Papers/TemperAnneal/KirkpatrickAnnealScience1983.pdf)
- **相变（Phase Transitions）** — 研究宏观性质如何在控制参数跨过临界条件时发生定性变化。 [Tong · 序参量、相变与临界行为](https://davidtong.org/teaching/statistical-physics/statmechhtml/S5)
- **重整化群（Renormalization Group）** — 反复粗粒化并重缩放系统，追踪模型参数随观察尺度变化的规律。 [Tong · 粗粒化与重整化群讲义](https://www.damtp.cam.ac.uk/user/tong/sft/sfthtml/S3.html)

## 10. 不确定性、风险与鲁棒决策

*Uncertainty, Risk, and Robust Decision-Making*

分别描述对模型认知不足、结果随机性与环境偏移，并据此明确策略要承担的风险和需要防范的情形。

**与强化学习的联系**　鲁棒 RL、安全探索、风险敏感策略与分布偏移下的评估。

两条策略即使平均延误相同，极端拥堵程度也可能相差很大。VaR 给出损失的分位点，CVaR 汇总最坏一段损失的平均水平，DRO 则描述对真实损失分布缺乏把握时的决策问题。

### 判断不确定性与选择目标

- **贝叶斯决策理论（Bayesian Decision Theory）** — 用后验分布描述未知量，并选择使后验期望损失最小的行动。 [CMU 统计学讲义 · 损失函数与贝叶斯决策](https://www.stat.cmu.edu/~siva/teaching/700/lec11.pdf)
- **不确定性量化（Uncertainty Quantification, UQ）** — 估计并传播数据、参数或模型中的不确定性，以评估预测和决策结果的可信程度。 [Ralph C. Smith · 不确定性量化教材资源](https://rsmith.math.ncsu.edu/UQ_TIA/)
- **贝叶斯优化（Bayesian Optimization）** — 用概率代理模型与采集函数选择下一次昂贵的目标评估，在试验收益与信息获取之间权衡。 [Frazier · 高斯过程代理与采集函数](https://arxiv.org/abs/1807.02811)
- **遗憾最小化（Regret Minimization）** — 缩小所作决策的累计损失与事后选定的基准策略之间的差距。 [Hazan · 在线决策中的遗憾与基准](https://arxiv.org/abs/1909.05207)
- **风险敏感优化（Risk-sensitive Optimization）** — 将方差、尾部损失或效用等纳入目标，使结果分布影响最优决策。 [Chow 等 · CVaR 风险敏感序贯决策](https://arxiv.org/abs/1506.02188)
- **风险价值（Value at Risk, VaR）** — 用指定置信水平下的损失分位数给出损失阈值。 [Rockafellar 与 Uryasev · 一般损失分布下的 VaR](https://sites.math.washington.edu/~rtr/papers/rtr187-CVaR2.pdf)
- **条件风险价值（Conditional Value at Risk, CVaR）** — 用损失分布最坏一段的平均值衡量尾部严重程度，分位点处的概率质量按尾部所需比例计入。 [Rockafellar 与 Uryasev · CVaR 定义、离散情形与优化](https://sites.math.washington.edu/~rtr/papers/rtr187-CVaR2.pdf)
- **分布强化学习（Distributional Reinforcement Learning）** — 学习给定状态或状态–动作对的随机累积回报分布，为分析分位数和尾部提供信息。 [Bellemare 等 · 回报分布与分布贝尔曼方程](https://proceedings.mlr.press/v70/bellemare17a.html)

### 不确定条件下的保证

- **鲁棒优化（Robust Optimization）** — 对不确定集合中的参数考虑最坏情形，按该情形保证约束或优化目标。 [Bertsimas 等 · 不确定集合与鲁棒优化教程](https://arxiv.org/abs/1010.5445)
- **分布鲁棒优化（Distributionally Robust Optimization, DRO）** — 将不确定对象设为概率分布，并针对集合中使期望目标最不利的分布优化决策。 [Kuhn 等 · 分布集合与最坏期望](https://arxiv.org/abs/1908.08729)
- **机会约束（Chance Constraints）** — [给违约概率设定容许上限](#6-约束层次与多目标优化)，用允许的事件概率表述可靠性要求。 [Nemirovski 与 Shapiro · 违约概率约束及其近似](https://www2.isye.gatech.edu/~nemirovs/ChanceConstr-Nov14.pdf)

## 11. 信息几何、最优传输与分布优化

*Information Geometry, Optimal Transport, and Distribution Optimization*

用几何度量、散度和传输成本描述概率分布或表示空间的结构。

**与强化学习的联系**　策略分布优化、状态表示、占用测度对齐与跨环境迁移。

使用分布几何前，先确定比较的是策略分布、状态访问频率还是回报分布。KL 散度常用于约束局部策略更新，最优传输则可把状态或动作之间的距离纳入分布比较。

### 度量、散度与参数几何

- **信息几何（Information Geometry）** — 将参数化概率分布族视为带有几何结构的空间，以研究分布变化与统计推断。 [Nielsen · 统计流形与信息几何入门](https://arxiv.org/abs/1808.08271)
- **Fisher 信息矩阵（Fisher Information Matrix, FIM）** — 用对数似然梯度的二阶矩刻画分布对参数变化的局部敏感性。 [Nielsen · Fisher–Rao 度量及推导](https://pmc.ncbi.nlm.nih.gov/articles/PMC7650632/)
- **自然梯度（Natural Gradient）** — 以 Fisher 度量定义最陡上升方向，对应[策略更新](#3-策略优化与学习动力学)中的局部分布几何。 [Amari 与 Douglas · 学习中的自然梯度原理](https://proceedings.neurips.cc/paper/1996/file/39e4973ba3321b80f37d9b55f63ed8b8-Paper.pdf)
- **黎曼优化（Riemannian Optimization）** — 在流形的切空间中计算更新方向，再通过指数映射或回缩返回流形。 [Boumal · 流形梯度、回缩与优化算法](https://www.nicolasboumal.net/book/)
- **KL 散度（Kullback–Leibler Divergence）** — 在第一个分布下取对数概率比的期望，以度量它偏离第二个分布的程度。 [Nielsen · KL 散度与统计模型](https://pmc.ncbi.nlm.nih.gov/articles/PMC7650632/)
- **Bregman 散度（Bregman Divergence）** — 用凸函数与其在参考点的线性近似之间的差值衡量偏离程度。 [Nielsen · Bregman 散度与对偶几何](https://pmc.ncbi.nlm.nih.gov/articles/PMC7650632/)

### 分布传输与表示结构

- **最优传输（Optimal Transport, OT）** — 在所有满足边缘分布的耦合中，寻找使平均质量搬运成本最小的方案。 [Peyré 与 Cuturi · 计算最优传输第 2 章](https://optimaltransport.github.io/book/)
- **Wasserstein 距离（Wasserstein Distance）** — 用基于底层空间距离的最优传输成本衡量两个概率分布之间的几何差异。 [Peyré 与 Cuturi · Wasserstein 距离及实例](https://arxiv.org/abs/1803.00567)
- **Sinkhorn 算法（Sinkhorn Algorithm）** — 通过交替缩放非负矩阵的行和列，使其满足两边的边缘约束，可用于求解熵正则化最优传输。 [Cuturi · 熵正则化最优传输与 Sinkhorn 迭代](https://arxiv.org/abs/1306.0895)
- **Wasserstein 梯度流（Wasserstein Gradient Flow）** — 在 Wasserstein 几何下沿能量最陡下降的方向演化概率分布。 [Ambrosio 与 Savaré · 概率分布的梯度流讲义](https://web.math.ucsb.edu/~kcraig/math/AmbrosioSavareLectureNotes.pdf)
- **流形学习（Manifold Learning）** — 试图从高维观测中恢复低维结构，以保留对表示或决策重要的几何关系。 [Tenenbaum 等 · Isomap 与非线性降维](https://redwood.berkeley.edu/wp-content/uploads/2018/08/tenenbaum-manifold.pdf)
- **拓扑数据分析（Topological Data Analysis, TDA）** — 用连通分支、环等跨尺度拓扑特征概括数据的形状。 [Ghrist · 条形码与持久同调入门](https://graphics.stanford.edu/courses/cs164-09-spring/Handouts/paper_barcodes.pdf)
