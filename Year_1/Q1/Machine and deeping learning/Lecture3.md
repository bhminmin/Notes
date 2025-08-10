### Lecture 3
#### Revise 
* **Bayes Error**: 理论分类误差下界，取决于真实数据分布（不可直接获得）
* **Risk & Minimum Risk**: 统计决策论框架，引出conditional risk and total risk
* **LDA/QDA**: generative方法，通过建模$P(x|y)$和$P(y)$得到分类边界（假设高斯分布）
* **Fisher LDA**:discriminative方法，不建模分布，直接找最大化between-class variance/within-class variance的投影方向
* **Least Squares Classification**: 用回归的思路做分类，拟合标签，某些条件下与LDA等价
---
#### Linear classifier的不同视角
* LDA(Linear Discriminant Analysis):
  * 基于概率建模(generative method),假设各类样本服从Gaussian Distribution且covariance matrix相同
  * 得到的分类边界:Linear
* QDA(Quadratic Discriminant Analysis)
  * 同样假设Gaussian distribution，但允许不同类别有不同的covariance matrix
  * decision boundary 是二次曲线
  * 需要covariance matrix is inverted
---
#### Fisher Linear Discriminant(Fisher LDA)
* 不直接建模概率分布，而是通过优化投影方向$\theta$
* 目标是**最大化between-class variance/within-class variance**,投影后的两类样本尽量分开
* 本质上是一种discriminant方法，但在Gaussian+等协方差假设下等价于LDA
---
#### Least Squares Classification
* 把分类问题转化为回归问题
* 给类别打标签（例如+1，-1），用最小二乘法拟合一个线形模型
* 计算简单，但对异常值敏感
---
#### 贯穿的主线
* 从贝叶斯最优分类器的理论极限出发->用统计决策论刻画风险->从生成式方法(LDA/QDA)到判别式方法(Fisher LDA)->再到回归化分类
* 体现了方法论的转变：从建模数据分布，到直接优化判别能力，再到借助回归工具做分类

   
