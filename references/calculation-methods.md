# 计算方法示例

## 1. 高斯 Fourier 变换：配方与直接积分

对应原则：优先常用方法及其变式；保留方法成立的依据。

采用定义

\[
\widehat h(\lambda)=\frac1{\sqrt{2\pi}}\int_{\mathbb R}h(x)e^{-i\lambda x}\,\mathrm dx,
\qquad \lambda\in\mathbb R.
\]

求 h(x)=e^{-x²} 的 Fourier 变换。指数是二次多项式，先配方，使积分与已知高斯积分联系起来：

\[
-x^2-i\lambda x
=-\left(x+\frac{i\lambda}{2}\right)^2-\frac{\lambda^2}{4}.
\]

因此

\[
\widehat h(\lambda)
=\frac{e^{-\lambda^2/4}}{\sqrt{2\pi}}
\int_{\mathbb R}e^{-(x+i\lambda/2)^2}\,\mathrm dx.
\]

令 z=x+iλ/2 后，积分路径为 ℝ+iλ/2。使用高斯积分的路径平移性质：

\[
\int_{\mathbb R+i\lambda/2}e^{-z^2}\,\mathrm dz
=\int_{\mathbb R}e^{-x^2}\,\mathrm dx=\sqrt\pi.
\]

得到

\[
\boxed{\widehat h(\lambda)=\frac1{\sqrt2}e^{-\lambda^2/4}.}
\]

### 路径平移的依据与讲解范围

若课程已给出这一性质，说明使用了该性质即可。需要补充依据时，固定实数 λ，考虑连接两条水平路径的矩形。e^{-z²} 在复平面上解析，由 Cauchy 定理，闭合路径积分为零。竖直边上 z=±R+iy，且 |y|≤|λ|/2，因此

\[
|e^{-z^2}|=e^{-R^2+y^2}\le e^{-R^2+\lambda^2/4}.
\]

竖直边长度固定，故其积分在 R→∞ 时趋于零，从而得到两条水平路径的积分相等。这也适用于 λ<0 的向下平移。

用户要求直接积分时，将配方、提出常数和高斯积分连接完整。复数平移的理由必须准确，不应默认改写为对 λ 求导后建立 ODE。用户限定只能使用实分析且没有可用的复平移结论时，说明适用条件，再选择课程内能够完成的推导。

## 2. 已知变换的变式：使用 Fourier 性质

对应原则：复用已知结果；按结构选择方法；减少额外记忆。

已经求出 h(x)=e^{-x²} 的变换，再求 xh(x) 或 h(x-d)，直接使用已有性质：

\[
\mathcal F[xh(x)](\lambda)
=i\widehat h'(\lambda)
=-\frac{i\lambda}{2\sqrt2}e^{-\lambda^2/4},
\]

\[
\mathcal F[h(x-d)](\lambda)
=e^{-id\lambda}\widehat h(\lambda),\qquad d\in\mathbb R.
\]

这里的频率求导直接作用于已经求出的表达式，是课程内常用性质。方法选择原则允许这种简单、可复用的计算，也允许用户明确请求的参数求导法。

## 3. 双曲型方程：根据计算结构选择特征变量

对应原则：独立判断当前题目的计算量；熟悉程度与结构共同决定方法。

考虑

\[
u_{tt}+2u_{xt}-3u_{xx}+2u_t+6u_x=0.
\]

系数矩阵的特征值为 -1±√5。若题目允许自行选择变换，观察二阶主部的因式分解

\[
\partial_t^2+2\partial_x\partial_t-3\partial_x^2
=(\partial_t-\partial_x)(\partial_t+3\partial_x),
\]

即可选择特征变量 ξ=x+t、η=x-3t。记 u(x,t)=U(ξ,η)，完整方程变为

\[
-16U_{\xi\eta}+8U_\xi=0,
\qquad U_{\xi\eta}-\frac12U_\xi=0.
\]

这一选择使变换系数和后续运算简单。讲解时说明选择依据，不必同时展开矩阵对角化的全部计算。用户要求比较两种方法或题目指定特征向量法时，再按所问范围处理。特征变量的代换系数与矩阵特征值各有定义，不能混用。

## 4. 非齐次边界：先利用已有的齐次化方法

对应原则：识别题型；需求先于构造；利用已学通法。

考虑半直线上的问题

\[
u_{tt}-u_{xx}=0,\quad u(x,0)=x^2,\quad u_t(x,0)=0,
\quad u_x(0,t)=t^2.
\]

为了使空间导数在边界为零，选择一个关于 x 的导数为 t² 的函数 xt²，令

\[
v(x,t)=u(x,t)-xt^2.
\]

逐项得到

\[
v_{tt}-v_{xx}=-2x,\quad v(x,0)=x^2,\quad v_t(x,0)=0,
\quad v_x(0,t)=0.
\]

齐次 Neumann 边界对应偶延拓，初位移延拓为 x²，右端项延拓为 -2|x|，随后使用非齐次 D'Alembert 公式。解释到这里时，读者已经知道每次构造要消去什么，以及产生的新条件应如何处理。完整解题仍应完成积分并恢复 u。
