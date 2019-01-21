### 算法重点阐述
- 采用Q-learning的目标值函数来构造DL的标签，从而构造DL的loss function
- 采用**记忆回放(experience replay mechanism)**来解决数据关联性问题
- 使用一个CNN(Main Net)来产生当前Q值，使用另外一个CNN(Target)来产生Target Q值（在2015年DeepMind的论文Human-level Control Through Deep Reinforcement Learning新版DQN中采用）

[Loss function构造，详解DQN](https://blog.csdn.net/LagrangeSK/article/details/80321265)

**为什么需要记忆回放？**

&emsp;为了让 RL 的数据 （关联性不独立分布的数据） 更接近DL所需要的数据（独立同分布数据），在学习过程中建立一个“记忆库”，将一段时间内的state、action、state_ (下一时刻状态）以及reward存储在记忆库里，每次训练神经网络时，从记忆库里随机抽取一个batch的记忆数据， 这样就打乱了原始数据的顺序，将数据的关联性减弱。

**为什么使用两个CNN？**

为了使得算法性能更稳定，建立两个结构一样的神经网络：一直在更新神经网络参数的网络（MainNet)和用于更新Q值（TargetNet)。
- 初始时刻将MainNet的参数赋值给TargetNet，
- 然后MainNet继续更新神经网络参数，而TargetNet的参数固定不动。
- 再过一段时间将MainNet的参数赋给TargetNet，如此循环往复。
  
这样使得一段时间内的目标Q值是稳定不变的，从而使得算法更新更加稳定。

### 算法流程
![2015版DQN](https://img-blog.csdn.net/20180515143710839?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0xhZ3JhbmdlU0s=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

CSDN图片不能显示，佛了！辣鸡CSDN！你收你马的费呢？