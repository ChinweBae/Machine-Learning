# Machine-Learning

### 一、什么是机器学习
利用大量的数据样本，使得计算机通过不断的学习获得一个模型，用来对新的未知数据做预测。

+ 有监督学习（分类、回归）

    同时将数据样本和标签输入给模型，模型学习到数据和标签的映射关系，从而对新数据进行预测。

    + 分类问题（监督学习）

      根据数据样本上抽出的特征，判断其属于有限个类别中的哪一个。

      + 垃圾邮件识别（结果类别：1、垃圾邮件 2、正常邮件）
      + 文本情感褒贬分析（结果类别：1、褒义 2、贬义）
      + 图像内容识别（结果类别：1、喵星人 2、汪星人 3、人类 4、草泥马 5、都不是）

    + 回归问题（监督问题）

      根据数据样本上抽出的特征，预测连续值结果。

      + 《芳华》票房值
      + 魔都房价具体值
      + 刘德华和吴彦祖具体颜值得分


+ 无监督学习（聚类）

    只有数据，没有标签，模型通过总结规律，从数据中挖掘出信息。

    + 聚类问题（无监督学习）

      根据数据样本上抽取出的特征，挖掘数据的关联模式

      + 相似用户挖掘/社区发现
      + 新闻聚类

    + 强化问题

      研究如何给予环境而行动，以取得最大化的预期利益

      + 游戏（"吃鸡"）最高得分
      + 机器人完成任务

+ 强化学习

    强化学习会在任何没有标签的情况下，通过先尝试作出一些行为得到一个结果，通过这个结果是对是错的反馈，调整之前的行为，就这样不断的调整，算法能够学习到，在什么样的情况下选择什么样的行为可以得到最好的结果。

    就好比你有一只还没有训练好的小狗，每当他把屋子弄乱后，就减少美味食物的数量（惩罚），每次表现不错时，就加倍美味食物的数量（奖励），那么小狗最终回学到一个知识，就是把客厅弄乱是不好的行为。

### 二、 线性回归

利用大量的样本，通过有监督的学习，学习到由x到y的映射，利用该映射关系对未知数据进行预估，因为y为连续值，所以是回归问题。

+ 单变量情况

  y=ax+b

+ 多变量情况

  二维空间的直线，转化为高位空间的平面

#### 2.1 线性回归的表达式

机器学习是数据驱动的算法，数据驱动=数据+模型，模型就是输入到输出的映射关系。

模型=假设函数（不同的学习方式）+ 优化

1. 假设函数

   线性回归假设函数（$\theta_{0}$ 表示截距项，$x_{0}=1$ ，方便矩阵表达）

   $$f(x)=\theta_{0}x_{0}+\theta_{1}x_{1}+\theta_{2}x_{2}...+\theta_{n}x_{n}$$ 

   向量形式（$\theta,x$都是列向量）

   $$ f(x)=\theta^Tx$$ 

2. 优化方法

   监督学习的优化方法=损失函数+对损失函数的优化

3. 损失函数

   如何衡量以后的参数$\theta$	的好坏？

   利用损失函数来衡量，损失函数度量预测值和标准答案的偏差，不同的参数有不同的偏差，所以要通过最小化损失函数，也就是最小化偏差来得到最好的参数。

   映射函数：$h_{\theta}$ 

   损失函数：$J(\theta_{1},\theta_{2},...,\theta_{n})=\frac{1}{2m}\sum_{i=1}^m(h_{\theta}(x^{(i)}-y^{(i)})^2$ 

   解释：因为有m个样本，所以要平均，分母的2是为了求导方便

   损失函数：凸函数

4. 损失函数的优化

   损失函数是一个凸函数，我们的目标是到达最低点，也就是是的损失函数最小。

   多元情况下容易出现局部极值。

   求极值的数学思想，对公式求导=0即可得到极值，但是工业上计算量很大，公式很复杂，所以从计算机的角度来讲，求极值是利用梯度下降法。

   + 梯度下降
     + 逐步最小化损失函数的过程
     + 如同下山，找准方向（斜率），每次迈进一小步，直至山底。
       + 初始位置选取很重要
       + 复梯度方向更新，二维情况下，函数变换最快的方向是斜率方向，多维情况下就称为梯度，梯度表示函数值增大的最快方向，所以要在负梯度方向上进行迭代
       + $$\theta_{1}:=\theta_{1}-\alpha\frac{d}{d\theta_{1}}J(\theta_{1})$$ 
