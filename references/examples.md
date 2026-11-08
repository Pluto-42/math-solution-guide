# 证明讲解示例

## 1. 圆周平均恒等式：让积分区域变化有明确用途

设 u 是二维波动方程的 C² 解，定义

\[
I(\mathbf x,r,t)=\frac1{2\pi}\int_{\lVert\mathbf y\rVert=1}u(\mathbf x+r\mathbf y,t)\,dS_{\mathbf y}.
\]

要证明

\[
I_{tt}=a^2\left(I_{rr}+\frac1r I_r\right),\qquad r>0.
\]

**Step 1：从已知方程明确剩余目标。**

由 u 的波动方程，I 的时间二阶导数等于 a² 乘以 Laplace 算子的圆周平均。因此只需证明

\[
\frac1{2\pi}\int_{\lVert\mathbf y\rVert=1}\Delta_{\mathbf x}u(\mathbf x+r\mathbf y,t)\,dS_{\mathbf y}
=I_{rr}+\frac1r I_r.
\]

**Step 2：目标中的结构提示研究 rI_r。**

乘积求导给出

\[
I_{rr}+\frac1r I_r=\frac1r\partial_r(rI_r).
\]

从定义求导，I_r 的被积函数是梯度与径向单位向量的内积。它是法向导数；再乘 r，线元就转化为半径 r 的圆周线元。令 \(\mathbf z=r\mathbf y\)，得到

\[
rI_r=\frac1{2\pi}\int_{\lVert\mathbf z\rVert=r}
\nabla_{\mathbf z}u(\mathbf x+\mathbf z,t)\cdot\frac{\mathbf z}{r}\,dS_{\mathbf z}.
\]

**Step 3：目标需要 Laplace 算子，Gauss 公式提供它。**

梯度的散度正是 Laplace 算子，故

\[
rI_r=\frac1{2\pi}\int_{\lVert\mathbf z\rVert<r}\Delta_{\mathbf z}u(\mathbf x+\mathbf z,t)\,d\mathbf z.
\]

圆盘积分在这一需求下出现。为了对 r 求导，将积分写成极坐标形式：

\[
rI_r=\frac1{2\pi}\int_0^r s\int_{\lVert\mathbf y\rVert=1}
\Delta_{\mathbf x}u(\mathbf x+s\mathbf y,t)\,dS_{\mathbf y}\,ds.
\]

**Step 4：完成先前需要的半径求导。**

由变上限积分求导，

\[
\partial_r(rI_r)=\frac r{2\pi}\int_{\lVert\mathbf y\rVert=1}
\Delta_{\mathbf x}u(\mathbf x+r\mathbf y,t)\,dS_{\mathbf y}.
\]

除以 r 后得到 Step 1 所需恒等式，代回时间导数即得目标。C² 正则性和局部紧致积分区域保证这里的求导与 Gauss 公式适用。

## 2. 极限证明：由目标决定参数

证明 \(\lim_{x\to2}x^2=4\)。

**Step 1：展开目标。** 给定任意 \(\varepsilon>0\)，需要选取 \(\delta>0\)，使得 \(0<|x-2|<\delta\) 蕴含 \(|x^2-4|<\varepsilon\)。

**Step 2：寻找足够的控制条件。** 因为 \(|x^2-4|=|x-2||x+2|\)，若能给第二个因子一个固定上界，就可以用第一个因子控制乘积。选择邻域 \(|x-2|<1\)，便有 \(|x+2|<5\)。于是再要求 \(|x-2|<\varepsilon/5\) 就足够。

**Step 3：构造并验证。** 取

\[
\delta=\min\{1,\varepsilon/5\}.
\]

当 \(0<|x-2|<\delta\) 时，上述两个条件同时成立，故

\[
|x^2-4|=|x-2||x+2|<5|x-2|<5\delta\le\varepsilon.
\]

邻域 1 提供方便的充分条件；其他能产生统一上界的邻域也可以使用。无需让读者相信这个数值是唯一选择。

## 3. 能量法：由消去项的需求决定辅助量

设两个经典解满足一维波动方程，在区间 \([0,L]\) 上有相同的齐次 Dirichlet 边界条件和相同初值，证明它们相等。

**Step 1：把目标转化为零解问题。** 令 \(w(x,t)=u(x,t)-v(x,t)\)，则 w 满足同一波动方程、零初值和齐次边界条件。目标为 w 恒为零。

**Step 2：从零解目标寻找可用量。** 若能找到由 \(w_t,w_x\) 构成的非负积分量，证明其初值为零且保持为零，就能得到 \(w_x=0\)，再由边界条件得到 w=0。

**Step 3：由方程匹配导数。** 方程连接 \(w_{tt}\) 和 \(a^2w_{xx}\)。乘以 \(w_t\) 后，时间侧出现 \(\partial_t(w_t^2/2)\)；空间侧积分分部后出现 \(-a^2w_xw_{xt}=-\partial_t(a^2w_x^2/2)\)。这提示定义

\[
E(t)=\frac12\int_0^L\left[w_t(x,t)^2+a^2w_x(x,t)^2\right]dx.
\]

**Step 4：核对并完成。**

\[
E'(t)=a^2[w_t(x,t)w_x(x,t)]_{x=0}^{x=L}=0.
\]

经典解的固定齐次边界给出端点处 \(w_t=0\)。零初值给出 \(E(0)=0\)，于是 E 恒为零。连续性和非负性给出 \(w_x=0\)，故每个时刻 w 关于 x 为常数；端点零值使该常数为零。
