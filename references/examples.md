# 证明讲解示例

<a id="circle-average"></a>

## 1. 圆周平均恒等式：直接使用定理，显露整体后换元

对应原则：目标与证明组织；构造与理解顺序；符号代换第 1、2 项。

设 a>0，u 是二维波动方程的 C² 解，定义

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

从定义求导得到

\[
rI_r=\frac r{2\pi}\int_{\lVert\mathbf y\rVert=1}
\nabla_{\mathbf x}u(\mathbf x+r\mathbf y,t)\cdot\mathbf y\,dS_{\mathbf y}.
\]

**Step 3：目标需要 Laplace 算子，Gauss 公式提供它。**

单位圆周的外单位法向量正是 \(\mathbf y\)。固定 \(\mathbf x,r,t\)，直接对关于 \(\mathbf y\) 的向量场 \(\nabla_{\mathbf x}u(\mathbf x+r\mathbf y,t)\) 应用 Gauss 公式：

\[
rI_r=\frac r{2\pi}\int_{\lVert\mathbf y\rVert<1}
\operatorname{div}_{\mathbf y}\left[\nabla_{\mathbf x}u(\mathbf x+r\mathbf y,t)\right]\,d\mathbf y.
\]

这里的散度对 \(\mathbf y\) 求导。链式法则给出

\[
\operatorname{div}_{\mathbf y}\left[\nabla_{\mathbf x}u(\mathbf x+r\mathbf y,t)\right]
=r\Delta_{\mathbf x}u(\mathbf x+r\mathbf y,t),
\]

所以

\[
rI_r=\frac{r^2}{2\pi}\int_{\lVert\mathbf y\rVert<1}
\Delta_{\mathbf x}u(\mathbf x+r\mathbf y,t)\,d\mathbf y.
\]

**Step 4：将半径依赖转到积分上限。**

目标需要对 r 求导。为了把这一步化为变上限积分求导，先将圆盘按半径分层，再把被积函数中的尺度整体作为新变量。令

\[
\mathbf y=\rho\boldsymbol\omega(\theta),\qquad
\boldsymbol\omega(\theta)=(\cos\theta,\sin\theta),\qquad
0\le\rho\le1,\quad 0\le\theta\le2\pi.
\]

由极坐标面积元，

\[
rI_r=\frac{r^2}{2\pi}\int_0^1\rho\int_0^{2\pi}
\Delta_{\mathbf x}u(\mathbf x+r\rho\boldsymbol\omega(\theta),t)\,d\theta\,d\rho.
\]

将外面的两个 r 分别分配给权重和微分：

\[
rI_r=\frac1{2\pi}\int_0^1(r\rho)\int_0^{2\pi}
\Delta_{\mathbf x}u(\mathbf x+(r\rho)\boldsymbol\omega(\theta),t)\,d\theta\,(r\,d\rho).
\]

现在权重和函数自变量中都出现整体 \(r\rho\)。固定 r 时有 \(r\,d\rho=d(r\rho)\)，因此将这个整体记为 s，积分范围相应从 \([0,1]\) 变为 \([0,r]\)：

\[
rI_r=\frac1{2\pi}\int_0^r s\int_0^{2\pi}
\Delta_{\mathbf x}u(\mathbf x+s\boldsymbol\omega(\theta),t)\,d\theta\,ds.
\]

此时 r 只出现在积分上限，故

\[
\partial_r(rI_r)=\frac r{2\pi}\int_0^{2\pi}
\Delta_{\mathbf x}u(\mathbf x+r\boldsymbol\omega(\theta),t)\,d\theta.
\]

除以 r 后得到 Step 1 所需恒等式：

\[
I_{rr}+\frac1r I_r
=\frac1{2\pi}\int_{\lVert\mathbf y\rVert=1}
\Delta_{\mathbf x}u(\mathbf x+r\mathbf y,t)\,dS_{\mathbf y}
=\frac1{a^2}I_{tt}.
\]

代回即得目标。C² 正则性和局部紧致积分区域保证求导与 Gauss 公式适用。

## 2. 极限证明：由目标决定参数

对应原则：目标与证明组织；构造与理解顺序；逻辑与数学含义。

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

对应原则：构造与理解顺序；逻辑与数学含义。

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

<a id="compact-notation"></a>

## 4. 稳定简记：保留已经明确的对象

对应原则：符号代换第 3 项；表达与信息安排。

### 4.1 保留 α 的参数依赖

已知 Fourier 变换后的时间方程为

\[
\widehat u_t(\lambda,t)+(a^2\lambda^2-ib\lambda-c)\widehat u(\lambda,t)=\widehat f(\lambda,t),
\qquad \widehat u(\lambda,0)=\widehat\varphi(\lambda).
\]

当前需要研究一阶 ODE 的求解结构，因此把已经明确的系数记为

\[
\alpha(\lambda)=a^2\lambda^2-ib\lambda-c.
\]

对每个固定的 λ，α(λ) 关于 t 为常量。利用积分因子得到

\[
\widehat u(\lambda,t)=e^{-\alpha(\lambda)t}\widehat\varphi(\lambda)
+\int_0^t e^{-\alpha(\lambda)(t-\tau)}\widehat f(\lambda,\tau)\,d\tau.
\]

这个形式清楚呈现初值项和源项。继续讨论卷积结构时可保留 α；需要具体计算 Gaussian 核时再展开。若对 λ 求导，则应使用

\[
\frac{\partial}{\partial\lambda}e^{-\alpha(\lambda)t}
=-t\alpha'(\lambda)e^{-\alpha(\lambda)t}.
\]

### 4.2 保留已求出的时间系数

若已知 \(a>0\)、\(\lambda_n>0\)，并已求得

\[
T_n(t)=A_n\cos(a\sqrt{\lambda_n}t)
+\frac{B_n}{a\sqrt{\lambda_n}}\sin(a\sqrt{\lambda_n}t),
\]

在说明空间模态与时间系数如何组成解时，使用

\[
u(x,t)=\sum_{n=1}^{\infty}X_n(x)T_n(t).
\]

它保留了空间、时间的组成关系。需要验证具体时间方程或计算数值时，再使用 T_n(t) 的表达式；级数的求导与收敛条件由具体问题另行验证。
