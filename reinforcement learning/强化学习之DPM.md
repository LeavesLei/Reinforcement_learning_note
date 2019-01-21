### MDP的动态规划解法（dynamic programming methods）
---
- 贝尔曼方程

![贝尔曼方程](https://images0.cnblogs.com/blog/489049/201401/201019351882.png)

- 优化目标

![优化目标](https://images0.cnblogs.com/blog/489049/201401/201019355785.png)

- 对于最优策略π*

状态值函数为V*(s) 行为值函数为Q*(s,a)  

**V\*与Q\*存在如下关系**：  
&emsp;![relation](https://images0.cnblogs.com/blog/489049/201401/201019377660.png)  

- 贝尔曼最优性方程（Bellman optimality equation）  

![BOE1](https://images0.cnblogs.com/blog/489049/201401/201019379691.png)

![BOE2](https://images0.cnblogs.com/blog/489049/201401/201019398446.png)

---
- 策略估计：对于任意策略，如何计算其状态值函数

---
- 强化学习的分类：

1. 基于模型的动态规划方法  


    (S,A,P,R,γ)均已知

2. 无模型的强化学习方法


    (S,A,P?,R?,γ?)

- 值函数的计算

![值函数计算过程](C:/Users/Leaves/Desktop/ACACACAC/强化学习/强化学习/值函数计算.png)

![值函数计算过程](C:/Users/Leaves/Desktop/ACACACAC/强化学习/强化学习/值函数计算过程.png)

- 求解值函数：自举算法（bootstrapping）

策略评估算法：

    值函数全部置零，开始起震。迭代到值函数不发生变化时停止

贪婪策略计算

- 策略迭代算法 = 策略评估算法 + 策略改进算法
- 值函数迭代算法
两者不同：一个是迭代π 一个是迭代V函数（不发生变化时迭代完成）


- **迭代π与迭代v的优劣讨论**

    <font color=purple>迭代π时每次都要根据v函数的更新来更新策略，比较耗时，但是步数少</font>  
    <font color=blue>迭代v时v函数收敛需要的步数较多，但是很有可能v函数没有收敛时，策略π就已经收敛，这样做了无用功</font>  
    <font color=red>个人想法：每次迭代k次v函数后对策略π进行更新，当π不变时停止v函数的迭代</font>

    


### V函数与Q函数的区别
---
- policy iteration使用bellman方程来更新value，最后收敛的value 即v_\pi是当前policy下的value值（所以叫做对policy进行评估），目的是为了后面的policy improvement得到新的policy。
- value iteration是使用bellman 最优方程来更新value，最后收敛得到的value即v_*就是当前state状态下的最优的value值。因此，只要最后收敛，那么最优的policy也就得到的。因此这个方法是基于更新value的，所以叫value iteration。