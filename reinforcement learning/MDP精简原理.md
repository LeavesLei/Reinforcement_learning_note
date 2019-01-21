### MDP
---
- 转移概率P


- 策略π：在状态S时执行动作a的概率  


- 回报函数R：从状态s1转移到s2会得到reward


- 累积回报G：γ折扣累积奖赏


- 在策略π下，可以计算累积回报G


- <font color=red>因为π是执行动作的概率，因此G可能有多个可能值</font>


- 因此使用value function通过计算累积回报G的期望来描述某个状态s接近成功的程度


- 状态值函数与状态-行为函数成为Bellman方程


- <font color=purple>Q函数实际上为具体制定某一个动作a后的V函数</font>

- RL中需要学习的东西：<font color=red>值函数</font>




    
