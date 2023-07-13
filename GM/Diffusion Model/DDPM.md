[Denoising Diffusion Probabilistic Models](https://arxiv.org/abs/2006.11239)
![[DDPM.jpg]]
## Introduction
DDPM简称为Diffusion model，是一个使用variational inference训练的参数化马尔科夫链。并且，扩散模型的某些参数化揭示了训练期间多个噪声水平上的去噪声分数匹配以及采样期间的退火的Langevin动力学的等价性。并且他们发现他们模型的大部分无损码长都被用来描述难以察觉的图像细节。他们表明扩散模型的采样过程是一种 progressive decoding，类似于autoregressive decoding.
## Background
DM是$p_\theta(x_0) := \int p_\theta(x_{0:T})dx_{1:T}$的一个[[Latent Variable Models]][[Explain of the definition]]。联合分布$p_\theta(x_{0:T})$被称为逆过程，它被定义为一个马尔科夫链，从$p(x_T) = \mathcal{N}(x_T;0,I)$开始学习[[Gaussian transitions]]([[DDPM数据生成过程概率分布]]):
$$
\begin{align}
& p_\theta(x_{0:T}) := p(x_T)\prod^{T}_{t=1}p_\theta(x_{t-1}|x_t),   \\
& p_\theta(x_{t-1}|x_t) := \mathcal{N}(x_{t-1};\mu_\theta(x_t,t),\sum_\theta(x_t,t))
\end{align}\tag{1}$$
DM与其他的LVM之间区别在于，近似后验$q(x_{1:T}|x_0)$（也就是前向过程或扩散过程）被固定到马尔科夫链，该马尔科夫链根据一个方差表$\beta_1...\beta_T$逐渐向数据添加高斯噪声。
$$
\begin{align}
& q(x_{1:T}|x_0) := \prod^{T}_{t=1}q(x_t|x_{t-1}),   \\
& q(x_t|x_{t-1}) := \mathcal{N}(x_t;\sqrt{1-\beta_t}x_{t-1},\beta_tI)
\end{align}\tag{2}$$
训练过程时通过优化负对数似然的常见变分界限来执行的:
$$
\begin{align}
\mathbb{E}[-\log p_\theta(x_0)]\le\mathbb{E}_q[-\log \frac{p_\theta(x_{0:T})}{q(x_{1:T}|x_0)}]=\mathbb{E}_q[-\log p(x_T)-\sum_{t\ge1}\log \frac{p_\theta(x_{t-1}|x_t)}{q(x_t|x_{t-1})}] =: L
\end{align}\tag{3}$$