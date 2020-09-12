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
	

2. 神经网络梯度计算里，momentum 设计是为了解决什么问题？
>- https://mofanpy.com/tutorials/machine-learning/torch/intro-speed-up-learning/

3. GAN网络里，判别器很强，生成器很弱，会有什么后果？

4. 有Accuracy, 为什么还需要 precision, recall？ roc曲线？
>- https://www.zhihu.com/question/30643044

5. dropout 机制？
>- https://mofanpy.com/tutorials/machine-learning/torch/dropout/

6. LSTM网络，sequence长度是变长的情况，如何处理？

7. 正负样本不平衡时，如何处理？
>- https://mofanpy.com/tutorials/machine-learning/ML-intro/imbalanced-data/

8. 强化学习PPO的核心是在哪？

9. L1, L2 正则化的作用？区别？
>- https://mofanpy.com/tutorials/machine-learning/ML-intro/l1l2regularization/

10. Pooling作用？1x1卷机核有啥作用？

11. 传统MDP解法，Qlearning， DQN 的不同？
        

### 同学讨论问题：
1. 单向链表里，如果以时间复杂度O(N), 空间复杂度O(1)的代价，判断链表有环？如何求环的入口点？
> 解题：快慢指针，快指针一次走2步，慢指针一次走1步
> 进一步：为什么快指针是2步？3，4，5步不行？
> 题解：https://zhuanlan.zhihu.com/p/60736361

### 推荐面试用书
* 百面机器学习 算法工程师带你去面试
    
