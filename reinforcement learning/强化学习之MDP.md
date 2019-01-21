### 强化学习（reinforcement learning）
---
- 两种基本元素:状态与动作
- 状态看做属性，动作看做标记
- 强化学习没有监督学习那样的标记信息  
    通常都是在尝试动作后才能获得结果

&emsp;强化学习基本图示模型
```
sequenceDiagram
A->>B: 动作a
B->>A: 状态x，奖赏r
```

#### 为什么使用强化学习
eg：构建一个比象棋大师还厉害的机器下棋的机器

#### 强化学习的特点
- 强化学习是试错学习（Trail-and-error），没有直接的指导信息，比如supervised learning中的label
- 延迟回报，强化学习的指导信息很少，而且往往是在事后给出的。

#### 强化学习与监督学习的区别与联系
- 强化学习是评估式反馈，比如做完一套试卷告诉你最终得分
- 监督学习是教导式反馈，在你做题前把答案给你，告诉你什么答案是正确的，什么答案是错误的

---

 null| 不考虑动作 | 考虑动作
---|---|---
状态可见 | 马尔科夫链（MC） | 马尔科夫决策过程（MDP）
状态不完全可见 |隐马尔科夫模型（HMM）|不完全观察马尔科夫决策过程（POMDP）
---
#### 隐马尔科夫链（HMM）
---
- 马尔科夫链的状态变量是隐藏的，不可观测的  
- 通过可观测变量来预测其状态变量


#### 马尔科夫决策过程（Markov Decision Process）
---
- 由一个四元组M = （S，A，Psa，R）构成
- S：状态集states
- A：动作集actions，ai表示第i步动作
- Psa：状态转移概率
- R：回报函数reward function

![状态转移示意图1](https://images0.cnblogs.com/blog/489049/201401/131433102201.jpg)

![状态转移示意图2](https://images0.cnblogs.com/blog/489049/201401/132312526273.jpg)

---
- 行为策略  

&emsp;强化学习学到的是一个从环境状态到动作的映射（即行为策略），记为策略n：S —> A  
&emsp;策略（policy）π 决定了 在状态x下要执行的动作a = π(x)

<font color=blue>*策略分为两种*</font>
1. 确定性策略π：X -> A，此时在状态x处采取动作a = π(x)
2. 随机性策略π：X × A -> R，此时π(x,a)表示在状态x下采取动作a的概率，这里必须有Σπ(x,a) = 1

<font color=purple>**策略的好坏取决于长期执行这一策略后得到的奖赏**</font>

---
- 状态值函数（state value function）

**设置值函数的原因**  
    增强学习往往具有延迟回报的特点: 如果在第n步输掉了棋，那么只有状态sn和动作an获得了立即回报r(sn,an)=-1，前面的所有状态立即回报均为0。所以对于之前的任意状态s和动作a，立即回报函数r(s,a)无法说明策略的好坏。因而需要定义值函数(value function，又叫效用函数)来表明当前状态下策略π的长期影响  
---
**常见值函数**

*用Vπ(s)表示策略π下，状态s的值函数。ri表示未来第i步的立即回报，常见的值函数有以下三种：*

- **a):**![value function 1](https://images0.cnblogs.com/blog/489049/201401/171629098615.png)  

- **b):**![value function 2](https://images0.cnblogs.com/blog/489049/201401/171629100809.png)

- **c):**![value function 3](https://images0.cnblogs.com/blog/489049/201401/171629102528.png)

---
- Q函数迭代推导：

![Q函数迭代推导](C:/Users/Leaves/Desktop/ACACACAC/强化学习/强化学习/value_function.png)  

    R代表当前状态的奖赏/回报/reward,r代表某一步的立即回报？（个人感觉） 
&emsp;Q函数实质上等于无穷次reward的数学期望

---

- 动作值函数（action value function） 

&emsp;**常见动作值函数**

![action value function](https://images0.cnblogs.com/blog/489049/201401/171629108773.png)

---
- **值函数与Q函数的计算过程**
---
*立即回报reward图*  
![reward](https://images0.cnblogs.com/blog/489049/201401/132323587361.jpg)
---
*策略n*  
![n](https://images0.cnblogs.com/blog/489049/201401/161254079863.png)
---
*值函数Vn(S)*  
![value function graph](https://images0.cnblogs.com/blog/489049/201401/132324064863.jpg)
  
计算过程：  
Vπ(s12) = r(s12,ar) = r(s13|s12,ar) = 100

 Vπ(s11)= r(s11,ar)+γ*Vπ(s12) = 0+0.9*100 = 90

Vπ(s23) = r(s23,au) = 100

 Vπ(s22)= r(s22,ar)+γ*Vπ(s23) = 90

 Vπ(s21)= r(s21,ar)+γ*Vπ(s22) = 81  
 
 ---
 *Q函数计算*  
 ![Q function graph](https://images0.cnblogs.com/blog/489049/201401/132345002982.png)
 
---

 #####  **难点：V函数与Q函数的区别**  
 - V函数是根据某一套策略n计算出来的，动作a是定死的
 - **V(S)函数表示从状态S出发，使用策略π所带来的累积奖赏的平均值**
 - **Q(S,a)函数表示从状态x出发，执行动作a后再使用策略π所带来的累积奖赏的平均值**
 - **某个策略π下状态S的值函数表示为Vπ(S),它是从状态S之后的期望回报**
 - **Qπ(s,a)表示在状态s采取动作a的价值**
 - <font color=blue>V函数以状态为前提，仅仅描述这个状态成功的希望有多大，从这一个状态出去之后可能有多个行为，每个行为选定后又可能有多个状态。</font>
 - <font color=purple>Q函数限定了s下的动作a之后能到达状态的累积回报，也就是说在这个状态下这步a走的怎么样，在这个局面走的这步棋究竟是步好棋还是坏棋</font>
 - V衡量状态好坏，Q衡量动作的好坏
 ---

- **最优值函数V***  

&emsp;一个策略π比另外一个策略π'好 <==> Vπ(s) >= Vπ'(s) 对状态空间S中的任意状态均成立。最优策略对应的状态值函数叫做最优状态函数，表示为V*，定义为

&emsp;&emsp;![Q函数迭代推导](C:/Users/Leaves/Desktop/ACACACAC/强化学习/强化学习/最优值函数.png)  
---
- **最优值行为函数Q***

&emsp;&emsp;![Q函数迭代推导](C:/Users/Leaves/Desktop/ACACACAC/强化学习/强化学习/最优值行为函数.png) 
---
- 最优行为值函数和最优状态值函数的关系

&emsp;&emsp;![Q函数迭代推导](C:/Users/Leaves/Desktop/ACACACAC/强化学习/强化学习/vq_relation.png) 

    原因：最优策略下的状态值必须等于从该状态开始的最优的期望动作获得的回报

&emsp;
- **强化学习的目的**  



在任意初始条件下，是Vn值最大的策略n*
 
 

