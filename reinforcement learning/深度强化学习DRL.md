- 利用RL对图像进行预处理，然后在投入CNN
- 图像的状态与动作？

### DQN(Deep Q-learning)
问题的提出：  
&emsp;但state和action的空间(size)是高维连续时，此时使用Q-table存储每个状态对应的Q函数变得不现实。

解决:  
&emsp;通常做法是把Q-table的更新问题变成一个函数拟合问题，相近的状态输出相近的输出动作，通过更新θ参数来是Q函数逼近最优Q值

DRL是将深度学习（DL）与强化学习（RL）结合，直接从高维原始数据学习控制策略。而DQN是DRL的其中一种算法，它要做的就是将卷积神经网络（CNN）和Q-Learning结合起来，CNN的输入是原始图像数据（作为状态State），输出则是每个动作Action对应的价值评估Value Function（Q值）。

- Crafting a Toolchain for Image Restoration by DRL(具有复杂混合失真的图像复原问题) [图像复原](https://github.com/yuke93/RL-Restore)
- Reinforcement Learning in Images for object detection
- [自动给图片添加说明：Deep Reinforcement Learning-based Image Captioning with Embedding Reward](http://openaccess.thecvf.com/content_cvpr_2017/papers/Ren_Deep_Reinforcement_Learning-Based_CVPR_2017_paper.pdf)


### Deep Q-learning(DQN)
---
off-policy
对于普遍的RL问题，Q-table(size_q-table = size_state * size_action)

- 价值函数近似(Value Function Approximation)  

用一个函数表示Q(s,a),即f(s,a) = Q(s,a) = w1*s+w2*s+b