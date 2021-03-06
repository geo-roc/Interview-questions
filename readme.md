## 求职问题整理

### 阿里面试问题：
1. 2个鸡蛋，100层楼，测试鸡蛋从几楼掉下来会碎？ 在最坏情况下摔鸡蛋的次数最少，鸡蛋掉下来没碎，可以继续用。进一步，m个鸡蛋，n层楼，如果解？
> 解题：动态规划
>- https://www.jianshu.com/p/bef8997e7e90

### 腾讯机器学习面试：
1. 神经网络loss 为None，如何调试，如何排查问题？
> 一般来说，出现NaN有以下几种情况：
> 1. 如果在迭代的100轮以内，出现NaN，一般情况下的原因是因为你的学习率过高，需要降低学习率。可以不断降低学习率直至不出现NaN为止，一般来说低于现有学习率1-10倍即可。**
> 2. 如果当前的网络是类似于RNN的循环神经网络的话，出现NaN可能是因为梯度爆炸的原因，一个有效的方式是增加“gradient clipping”（梯度截断来解决）
> 3. 可能用0作为了除数;
> 4. 可能0或者负数作为自然对数
> 5. 需要计算loss的数组越界（尤其是自己，自定义了一个新的网络，可能出现这种情况）
> 6.在某些涉及指数计算，可能最后算得值为INF（无穷）（比如不做其他处理的softmax中分子分母需要计算exp（x），值过大，最后可能为INF/INF，得到NaN，此时你要确认你使用的softmax中在计算exp（x）做了相关处理（比如减去最大值等等）
>- https://zhuanlan.zhihu.com/p/89588946
>- https://blog.csdn.net/u012910595/article/details/78843031
>- https://jishuin.proginn.com/p/763bfbd29dce
	

2. 神经网络梯度计算里，momentum 设计是为了解决什么问题？
> 山谷和鞍点两类地形,山谷顾名思义就是狭长的山间小道，左右两边是峭壁；
> 鞍点的形状像是一个马鞍 ， 一个方向上两头翘，另一个方向上两头垂，而中心区域是一片近乎水平的平地。
> 为什么随机梯度下降法 最害怕遇上这两类地形呢？在山谷中，准确的梯度方向是沿山道向下， 稍有偏离就会撞向山壁，而粗糙的梯度估计使得它在两山壁间来回反弹,震荡,不能沿山道方向迅速下降，
> 导致收敛不稳定和收敛速度憬。在鞍点处,随机楠度下降法会走入－片平坦之地（此时离最低点还很远，故也称 plateau）。
> 想象一下蒙着双眼只凭借脚底感觉坡度,如果坡度很明显，那么基本能估计出下山的大致方向，如果坡度不明显,则很可能走锚方向。
> 同样，在梯度近乎为零的区域，随机梯度下降法无法准确察 觉出梯度的微小变化,结果就停滞下来。

>- 百面机器学习 第七章 06
>- https://mofanpy.com/tutorials/machine-learning/torch/intro-speed-up-learning/

3. GAN网络里，判别器很强，生成器很弱，会有什么后果？
> 在实际训练中，旱期阶段生成器G很差，生成的模拟样本很容易被判别器D识别，使得D回传给G的梯度极真小，达不到训练目的，这个现象称为优化饱合。

>- 百面机器学习 第十三章

4. 有Accuracy, 为什么还需要 precision, recall？ ROC曲线？AUC?
>- 百面机器学习 第二章
>- https://www.zhihu.com/question/30643044

5. dropout 机制？
>- https://mofanpy.com/tutorials/machine-learning/torch/dropout/

6. LSTM网络，由哪些门构成？其作用是？sequence长度是变长的情况，如何处理？
>- 百面机器学习 第十章 04

7. 正负样本不平衡时，如何处理？
>- 百面机器学习 第八章 07
>- https://mofanpy.com/tutorials/machine-learning/ML-intro/imbalanced-data/

8. 强化学习PPO的核心是在哪？
> 根据 OpenAI 的官方博客, PPO 已经成为他们在强化学习上的默认算法. 如果一句话概括 PPO: OpenAI 提出的一种解决 Policy Gradient 不好确定 Learning rate (或者 Step size) 的问题. 因为如果 step size 过大, 学出来的 Policy 会一直乱动, 不会收敛, 但如果 Step Size 太小, 对于完成训练, 我们会等到绝望. PPO 利用 New Policy 和 Old Policy 的比例, 限制了 New Policy 的更新幅度, 让 Policy Gradient 对稍微大点的 Step size 不那么敏感.
>- https://mofanpy.com/tutorials/machine-learning/reinforcement-learning/DPPO/

9. L1, L2 正则化的作用？区别？
>- 百面机器学习 第七章 07
>- https://mofanpy.com/tutorials/machine-learning/ML-intro/l1l2regularization/

10. Pooling作用？1x1卷机核有啥作用？
>由于 1×1 并不会改变 height 和 width，改变通道的第一个最直观的结果，就是可以将原本的数据量进行增加或者减少。这里看其他文章或者博客中都称之为升维、降维。但我觉得维度并没有改变，改变的只是 height × width × channels 中的 channels 这一个维度的大小而已。
>- https://zhuanlan.zhihu.com/p/40050371
>- https://zhuanlan.zhihu.com/p/29119239

11. 传统MDP解法，Qlearning， DQN 的不同？
>- 百面机器学习 第11章 

12. 生成式模型vs判别式模型?
> 判别式模型，就是只有一个模型，你把测试用例往里面一丢，label就出来了，如SVM。生成式模型，有多个模型(一般有多少类就有多少个)，你得把测试用例分别丢到各个模型里面，最后比较其结果，选择最优的作为label，如朴素贝叶斯。本文将从生成式模型与判别式模型的概念，适用环境以及具体模型三个方面分析比较这两个模型，并在最后对列出模型范例，进行范例比较。
>- https://blog.csdn.net/u013630349/article/details/47146425
>- https://www.jianshu.com/p/12edc0e4cf2c

### 同学讨论问题：
1. 单向链表里，如果以时间复杂度O(N), 空间复杂度O(1)的代价，判断链表有环？如何求环的入口点？
> 解题：快慢指针，快指针一次走2步，慢指针一次走1步
> 进一步：为什么快指针是2步？3，4，5步不行？
> 题解：https://zhuanlan.zhihu.com/p/60736361

### 推荐面试用书
* 百面机器学习 算法工程师带你去面试
    
