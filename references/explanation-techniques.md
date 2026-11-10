# 讲解与记号示例

## 1. 保留 α 的参数依赖

对应原则：稳定简记；说明固定量；沿用时间积分变量。

已知 Fourier 变换后的时间方程为

\[
\widehat u_t(\lambda,t)+(a^2\lambda^2-ib\lambda-c)\widehat u(\lambda,t)=\widehat f(\lambda,t),
\qquad \widehat u(\lambda,0)=\widehat g(\lambda).
\]

当前研究一阶 ODE 的求解结构，将已经明确的系数记为

\[
\alpha(\lambda)=a^2\lambda^2-ib\lambda-c.
\]

对每个固定的 λ，α(λ) 关于 t 为常量。利用积分因子得到

\[
\widehat u(\lambda,t)=e^{-\alpha(\lambda)t}\widehat g(\lambda)
+\int_0^t e^{-\alpha(\lambda)(t-\tau)}\widehat f(\lambda,\tau)\,\mathrm d\tau.
\]

继续讨论卷积结构时可保留 α，需要具体计算高斯核时再展开。若对 λ 求导，则应使用

\[
\frac{\partial}{\partial\lambda}e^{-\alpha(\lambda)t}
=-t\alpha'(\lambda)e^{-\alpha(\lambda)t}.
\]

## 2. K 的构造写完整，最终卷积保留 K

对应原则：沿用定义；关键计算充分展开；最终表达符合请求范围。

使用 1/√(2π) 的 Fourier 归一化。若用户已经定义

\[
\widehat K(\lambda,t)=e^{-\alpha(\lambda)t},\qquad t>0,
\]

则保持

\[
K(x,t)=\frac1{\sqrt{2\pi}}\int_{\mathbb R}
e^{-\alpha(\lambda)t+i\lambda x}\,\mathrm d\lambda.
\]

相应的卷积表达带有 1/√(2π)。这使用户的定义、推导和最终结果保持一致。

例如 α(λ)=λ²+2iλ，由 [高斯变换](calculation-methods.md) 和伸缩性质，逐步写出

\[
\mathcal F[e^{-x^2/(4t)}](\lambda)
=2\sqrt t\,\frac1{\sqrt2}e^{-(2\sqrt t\lambda)^2/4}
=\sqrt{2t}\,e^{-t\lambda^2}.
\]

因此

\[
\mathcal F^{-1}[e^{-t\lambda^2}](x)
=\frac1{\sqrt{2t}}e^{-x^2/(4t)}.
\]

再使用平移性质，得到

\[
K(x,t)=\mathcal F^{-1}[e^{-2it\lambda}e^{-t\lambda^2}](x)
=\frac1{\sqrt{2t}}\exp\left[-\frac{(x-2t)^2}{4t}\right].
\]

若 g(x)=e^{-(x-1)²} 且右端项为零，按用户要求将最终答案保留为

\[
u(x,t)=\frac1{\sqrt{2\pi}}\int_{\mathbb R}
K(x-\xi,t)e^{-(\xi-1)^2}\,\mathrm d\xi.
\]

用户只要求补全 K 的计算并用 K 表示结果时，在这里结束。若用户从一开始把 1/√(2π) 合并进 K 的定义，则卷积外的系数相应取消；先读取当前定义再继续。

一般右端项 f(x,t) 还会产生

\[
\frac1{\sqrt{2\pi}}\int_0^t\int_{\mathbb R}
K(x-\xi,t-\tau)f(\xi,\tau)\,\mathrm d\xi\,\mathrm d\tau.
\]

用户问一重、二重积分的来源时，分别联系初值和持续作用的右端项，并说明 f=0 时第二项为零。保留相关项的语义，无需重复展开核。

## 3. 保留已求出的时间系数

对应原则：稳定简记；保留空间与时间的组成关系。

若已知 a>0、λ_n>0，并已求得

\[
T_n(t)=A_n\cos(a\sqrt{\lambda_n}t)
+\frac{B_n}{a\sqrt{\lambda_n}}\sin(a\sqrt{\lambda_n}t),
\]

在说明空间特征函数与时间系数如何组成解时，使用

\[
u(x,t)=\sum_{n=1}^{\infty}X_n(x)T_n(t).
\]

需要验证具体时间方程或计算数值时，再使用 T_n(t) 的表达式；级数的求导与收敛条件由具体问题另行验证。若题目含零特征值，先单独求出对应的时间系数，再写入解，避免在含 1/√λ_n 的公式中直接代入零。
