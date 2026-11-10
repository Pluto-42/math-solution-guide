# math-solution-guide

**解题方法选择与讲解**：面向数学学习的 AI 技能，用于计算求解、证明分析和已有推导检查。优先采用常用方法及其变式，解释关键操作和辅助构造的依据，让学习者能够理解并再次使用解法。

方法选择同时考虑题目结构、课程范围、计算量和额外记忆负担。当前示例主要来自微积分、Fourier 变换和偏微分方程；讲解原则可以用于其他数学课程。

## 适用场景

- **完整解题**：选择合适的方法，按步骤完成计算或证明，验证题目要求。
- **方法选择**：解释为什么采用某种变换、公式或辅助函数，结合实际计算量作出判断。
- **局部讲解**：解释某个换元、积分、参数选择或逻辑跳转，衔接相邻步骤。
- **推导检查**：检查已有解答的条件、符号、系数和逻辑，保留可以继续使用的部分。
- **复习整理**：沿用笔记中的符号和已学方法，使同类题目的解法可以复用。

## 三类内容

### 1. 解题方法选择

先检查定义、直接积分、配方、换元、因式分解、常用公式和已有性质。选择方法时同时考虑计算量、适用条件、增加的知识和记忆负担。

例如，求高斯函数的 Fourier 变换时，优先通过配方与直接积分完成；随后求乘以自变量或平移后的函数时，复用已有变换性质。涉及复数平移时，保留积分路径变化的依据。题目或用户明确指定方法时，遵守该要求。

详细示例：[计算方法](references/calculation-methods.md)，包括高斯积分、Fourier 性质、特征变量和非齐次边界处理。

### 2. 通用讲解技巧

在关键操作之前，说明当前目标以及该操作的用途。先展示需要替换的整体，再进行换元；保留已经形成的乘积导数、配方和因式分解结构。

已经定义的 `α(λ)`、`K(x,t)`、`T_n(t)` 可以继续作为简记。需要计算其内部结构时完整展开，最终结果按照问题要求保留紧凑表示。函数变量、积分变量和归一化系数应当始终一致。

详细示例：[讲解与记号](references/explanation-techniques.md)，包括参数依赖、核函数的构造、卷积表达和空间与时间系数的组合。

### 3. 证明题原则

从待证结论寻找足够的中间条件，再连接已知条件的正向推导。引入辅助量之前解释其用途，检查充分条件、等价变形、定理适用条件和必要分支，最后完成原题要求。

详细示例：[证明方法](references/proof-methods.md)，包括圆周平均恒等式、极限中的参数选择和波动方程的能量构造。

## 获取与使用

下载仓库，或使用 Git 克隆：

```bash
git clone https://github.com/Pluto-42/math-solution-guide.git
```

本仓库根目录就是完整的技能目录，入口为 [SKILL.md](SKILL.md)。在支持 `SKILL.md` 的工具中，将整个 `math-solution-guide` 目录加入该工具的技能加载位置，保留 `references`、`agents` 和 `evals` 的相对路径。具体加载位置以所用工具的配置为准。

加载后，可以这样调用：

> 请使用 $math-solution-guide 讲解这道题，优先使用常用方法或变式，说明关键变换的依据，再按 Step 完成解答。

只解释一个步骤时，可以明确范围：

> 请使用 $math-solution-guide，把这里构造 K 的过程写完整，最终答案继续用 K 表示。

分析证明思路时，可以说明理解障碍：

> 请使用 $math-solution-guide，从待证结论解释为什么需要这个辅助函数，再连接已知条件完成证明。

也可以直接向支持读取文件的助手提供 `SKILL.md` 的路径，请它读取并遵循相关部分。提供题目、课程范围、已经学过的方法或当前推导，有助于选择合适的讲解深度。

## 文件说明

| 文件 | 内容 |
| --- | --- |
| [SKILL.md](SKILL.md) | 技能入口、适用范围、方法选择与讲解原则 |
| [agents/openai.yaml](agents/openai.yaml) | 显示名称、简短介绍和默认调用提示 |
| [references/calculation-methods.md](references/calculation-methods.md) | 计算方法及其变式的示例 |
| [references/explanation-techniques.md](references/explanation-techniques.md) | 关键步骤、变量依赖与简记的讲解示例 |
| [references/proof-methods.md](references/proof-methods.md) | 目标反推、辅助构造与完整证明示例 |
| [evals/cases.md](evals/cases.md) | 16 个验收用例、通过条件和评分标准 |

## 验收与维护

修改技能后，使用 [验收用例](evals/cases.md) 检查实际解答：方法是否合适、计算和证明是否正确、关键步骤的来源是否清楚、篇幅是否符合请求。

结构检查、数学内容核验和独立模型评估分别记录。结构检查通过不能代替解题质量评估。新增示例按三类内容归档，并更新对应验收用例，保持入口文件简洁。

## 证明讲解的理论来源

- George Pólya, *Mathematical Discovery*, 第 8 章：从目标寻找条件的 working backwards，以及分析与综合的关系。[书籍](https://www.tlu.ee/~tonu/modesimu/George_Polya_Mathematical_discovery.pdf)
- Rebecca Lea Morris, *Motivated proofs: What they are, why they matter and how to write them*, 2020：解释证明步骤的任务和合理来源。[论文](https://arxiv.org/abs/2001.02657)

证明题部分将这些思想组织成面向学习者的讲解要求；计算方法和通用讲解部分通过具体示例与验收用例检查。
