### Lecture 1
**最小化分类错误或总体风险**，前提是假设我们知道（或近似）数据的真实分布
#### Bayes error（贝叶斯错误率）
* 定义：给予真实分布$p(x,y)$所能达到的最小错误率
* 特点：
  * 由真实分布决定$\rightarrow$我们一般不知道（因为真实分布未知）
  * 理论极限$\rightarrow$所有分类器的性能上界
  * 计算涉及高维积分$\rightarrow$即使分布已知，也可能很复杂
---
#### Conditional risk
* 定义：$R(\alpha_i|x)=\sum_j \lambda(\alpha_i|\omega_j)P(\omega_j|x)$
    当你在样本$x$上选择动作（分类决策）$\alpha_i$ 时，根据它可能属于不同类别$\omega_j$的概率，加权计算决策带来的损失
* 损失函数$\lambda$：定义错分，代价不同的场景
---
#### Total risk
* 定义： $R=\int R(\alpha(x)|x)p(x)dx$
* 对所有样本的conditional risk求期望，得到整体性能
---
#### Minimum total risk
* 策略：对每个$x$, 选择使$ R(\alpha_i|x) $ 最小的$\alpha_i$
* 特殊情况：0-1损失下，等价于选择后验概率最大的类（MAP rule）
* 与Bayes error的关系：在0-1损失下，最小总体风险就是Bayes error
---
#### 高斯判别分析（Quadratic/Linear Classifier）
* **Quadratic classifier**：covariance matrix不同    $\rightarrow$决策边界是二次型
* **Linear classifier**: covariance matrix相同$\rightarrow$决策边界是线形的