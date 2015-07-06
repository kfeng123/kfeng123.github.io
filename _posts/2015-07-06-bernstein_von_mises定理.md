---
layout: post
title: "bernstein-von mises theorem证明报告"
date: 2015-07-06 16:27:00
categories: math
---


**准备:**
Contiguity:
测度序列$Q_n$关于$P_n$ contiguous：如果集合序列$A_n$使得$P_n(A_n)\to 0$，那么$Q_n(A_n)\to 0$，记做$Q_n\triangleleft P_n$ 。如果$P_n$与$Q_n$相互contiguous，记为$Q_n\triangleleft \triangleright P_n$

均方可微：
$P_\theta (\theta \in \Theta )$在$\theta$处均方可微：存在$\dot l_\theta$，使得
$$\int [\sqrt {p_{\theta+h}}-\sqrt {p_{\theta}}-\frac{1}{2}h^T\dot{l_\theta}\sqrt{p_\theta}]^2\, d\mu=o(||h||^2)$$<

定理7.2：设$\Theta$是$R^k$的一个开子集，模型($P_\theta :\theta \in \Theta$)在$\theta$处均方可微。那么$P_\theta \dot{l}_\theta =0$，并且Fisher信息阵存在$I_\theta=P_\theta \dot{l}_\theta\dot{l}_\theta^T$ 。并且对于$h_n\to h$，有：
$$\log \prod_{i=1}^n\frac{p_{\theta+h_n/\sqrt n}}{p_\theta}(X_i)=\frac{1}{\sqrt n}\sum_{i=1}^n h^T\dot{l}_\theta(X_i)-\frac{1}{2}h^TI_\theta h+o_{P_\theta}(1)$$

推论：$P_{\theta+h_n/\sqrt n}\triangleleft \triangleright P_{\theta}$

--------------
> **条件**

> 1. $P_\theta (\theta \in \Theta )$在$\theta_0$处均方可微
> 2. Fisher信息阵$I_{\theta_0}$非奇异
> 3. 对任意的$\epsilon >0$，存在一个检验序列$\phi_n$使得:
$$P_{\theta_0}^n \phi_n \to 0,\sup_{||\theta-\theta_0||\ge \epsilon}P^n_\theta (1-\phi_n)\to 0$$
> 4. $\pi(\theta)$在$\theta_0$附近连续并且具有正密度

**记号**
设$h=\sqrt{n} (\theta-\theta_0)$，$\Pi_n$是相应于h的先验分布$\Pi_n(B)=\Pi (\theta_0 +B/\sqrt{n}$) 。对于给定的集合C，设$\Pi_n^C$是把$\Pi_n$限制在C上并标准化得到的概率测度，对应的密度为：
$$\pi_n^C=\frac{\pi_n(h)1_{\{C\}}(h)}{\int_C \pi_n(h)\,dh}$$
记$P_{n,h}$是$\vec{X_n}=(X_1,...,X_n)$在参数$\theta_0 + h/\sqrt{n}$下的分布
设$P_{n,C}=\int P_{n,h}\, d\Pi_n^C(h)$
设$\vec {H}_n=\sqrt n (\vec{\Theta}_n -\theta_0)$,设$\Pi_n$和$\Pi_n^C$对应的后验分布为$P_{\vec H_n|\vec X_n}$和$P_{\vec H_n|\vec X_n}^C$
设$\Delta_{n,\theta_0}=\frac{1}{\sqrt n}\sum^n_{i=1}I^{-1}_{\theta_0}\dot l_{\theta_0}(X_i)$

----------
证明分两部：首先证明对应于$\Pi_n$和$\Pi_n^{C_n}$的后验分布的差异趋于0，其中$C_n$是半径为$M_n$的球，$M_n\to \infty$ 。然后再证明$\Pi_n^{C_n}$对应的后验分布与$N(\Delta_{n,\theta_0},I^{-1}_{\theta_0})$的差异趋于0 。

设U是一个以0为原点，半径固定的一个球。我们有$P_{n,U}\triangleleft \triangleright P_{n,0}$，这是因为由定理7.2，对于每个有界的序列$h_n$,$P_{n,h_n}\triangleleft \triangleright P_{n,0}$ 。因此，当我们证明依概率趋于0时，我们总是可以把$P_{n,0}$和$P_{n,U}$换着用的。

设$C_n$是半径为$M_n$的球。我们有:
$$
\begin{align}
P_{\vec{H}_n|\vec{X}_n}(B)-P^{C_n}_{\vec{H}_n|\vec{X}_n}(B) 
&=\frac{\int_B p_{n,h} \pi_n(h)\,dh}{\int p_{n,h} \pi_n(h)\,dh}-\frac{\int_{B\cap C_n} p_{n,h} \pi_n(h)\,dh}{\int_{C_n} p_{n,h} \pi_n(h)\,dh} \\
&=\frac{\int_{B\cap C_n^C}}{\int}+\frac{\int_{B\cap C_n}}{\int}-\frac{\int_{B\cap C_n}}{\int_{C_n}}   \\
&=\frac{\int_{B\cap C_n^C}}{\int}+\int_{B\cap C_n}(\frac{1}{\int}-\frac{1}{\int_{C_n}})  \\
&=\frac{\int_{B\cap C_n^C}}{\int}-\int_{B\cap C_n}\frac{\int_{C_n^c}}{\int_{C_n}\int}  \\
&=P_{\vec{H}_n|\vec{X}_n}(C_n^c\cap B)-P_{\vec{H}_n|\vec{X}_n}(C_n^c)P^{C_n}_{\vec{H}_n|\vec{X}_n}(B) 
\end{align}
$$


所以有：
$$||P_{\vec{H}_n|\vec{X}_n}-P^{C_n}_{\vec{H}_n|\vec{X}_n} ||\leq 2P_{\vec{H}_n|\vec{X}_n}(C^c_n)$$

下面证明上式右边在$P_{n,U}$下$L^1$收敛到0，其中U是一个以0为圆心，半径固定的球。首先由条件3以及$P_{n,U}\triangleleft P_{n,0}$，我们有
$$P_{n,U}P_{\vec{H}_n|\vec{X}_n}(C^c_n)=P_{n,U}[P_{\vec{H}_n|\vec{X}_n}(C^c_n)(1-\phi_n)]+o(1)$$
可以对上式右边第一项进行如下操作：
$$
\begin{align}
P_{n,U}[P_{\vec{H}_n|\vec{X}_n}(C^c_n)(1-\phi_n)]&=\int P_{\vec{H}_n|\vec{X}_n}(C^c_n)(1-\phi_n)\int p_{n,h}\pi^U_n\,dh\,dx   \\
&=\int P_{\vec{H}_n|\vec{X}_n}(C^c_n)(1-\phi_n)\int p_{n,h}\pi^U_n\,dh\,dx   \\
&=\int \frac{\int_{C_n^c} p_{n,h}\pi_n\,dh}{\int p_{n,h}\pi_n\,dh}(1-\phi_n)\frac{\int_U p_{n,h}\pi_n\,dh}{\int_U \pi_n\,dh}\,dx   \\
&=\int \frac{\int_{U} p_{n,h}\pi_n\,dh}{\int p_{n,h}\pi_n\,dh}(1-\phi_n)\frac{\int_{C_n^c} p_{n,h}\pi_n\,dh}{\int_U \pi_n\,dh}\,dx   \\
&=\frac{\int_{C_n^c} \pi_n\,dh}{\int_U \pi_n\,dh}\int \frac{\int_{U} p_{n,h}\pi_n\,dh}{\int p_{n,h}\pi_n\,dh}(1-\phi_n)\frac{\int_{C_n^c} p_{n,h}\pi_n\,dh}{\int_{C_n^c} \pi_n\,dh}\,dx   \\
&=\frac{\Pi_n(C_n^c)}{\Pi_n(U)}P_{n,C_n^c}P_{\vec H_n |\vec X_n}(U)(1-\phi_n)  \\
&\leq \frac{\Pi_n(C_n^c)}{\Pi_n(U)}P_{n,C_n^c}(1-\phi_n)  \\
&=\frac{1}{\Pi_n(U)}\int_{C^c_n}P_{n,h}(1-\phi_n)\,d\Pi_n(h)\\
\end{align}
$$

 被积函数逐点趋于0，但是这是不够的。由引理10.3，自动存在一个以指数速度收敛的$\phi_n$ 。
**引理 10.3**
在定理10.1的条件下，对于任意的$M_n\to\infty$，存在一个检验序列$\phi_n$和一个常数$c>0$使得：对每个充分大的n和$||\theta-\theta_0||\ge M_n/\sqrt n$,有：
$$
P^n_{\theta_0}\phi_n \to 0,P^n_{\theta}(1-\phi_n)\leq e^{-cn(||\theta-\theta_0||^2\wedge 1)} 
$$
使用这样的检验，上边的式子的上界变成：
$$
\frac{1}{\Pi_n(U)}\int_{||h||\ge M_n}e^{-c(||h||^2\wedge n)}\,d\Pi_n(h)
$$

由条件4，这里$\Pi_n(U)=\Pi (\theta_0+U/\sqrt n)$的下界是一个常数乘以$1/\sqrt n^k$。把积分区域分成$M_n\leq ||h||\leq D\sqrt n$和$||h||\geq D\sqrt n$，其中$D\leq 1$充分小使得$\pi (\theta)$在$||\theta-\theta_0||\leq D$内有界。上面的表达式的上界是常数乘以
$$
\int_{||h||\ge M_n} e^{-c||h||^2}\,dh+\sqrt n^k e^{-cD^2n}
$$
收敛到0
















