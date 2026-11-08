# goal-driven-proof

目标反推式证明讲解：先说明待证结论产生了什么需求，再引入满足需求的构造，将它与已知条件连接起来。

适用于“每一步都能看懂，却想不到为什么这样做”的证明学习问题。

## 使用

本仓库根目录就是完整的技能目录，入口为 [SKILL.md](SKILL.md)。支持加载技能目录的工具可以使用本目录；通过对话也可以指定读取 SKILL.md 并采用其中的讲解方法。

调用示例：

> 请使用 $goal-driven-proof 重新讲解这道证明。先说明要证明什么、只需证明什么，再解释辅助函数为什么选择这个形式。

## 讲解要求

- 构造出现之前，读者已经知道它的任务。
- 从当前目标说明选择依据，避免让中间结论突然出现。
- 明确充分条件与等价变形的区别。
- 按照问题需要结合反向分析和正向推导。
- 保留定理适用条件和完整验证。

具体材料见 [示例](references/examples.md) 和 [验收用例](evals/cases.md)。

## 理论来源

- George Pólya, *Mathematical Discovery*, 第 8 章：从目标寻找条件的 working backwards，以及分析与综合的关系。[书籍](https://www.tlu.ee/~tonu/modesimu/George_Polya_Mathematical_discovery.pdf)
- Rebecca Lea Morris, *Motivated proofs: What they are, why they matter and how to write them*, 2020：解释证明步骤的任务和合理来源。[论文](https://arxiv.org/abs/2001.02657)

本技能将这些思想组织成面向学习者的讲解要求。示例与用例用于检验证明质量，教学效果尚待实际使用评价。
