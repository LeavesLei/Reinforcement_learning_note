![DP](C:/Users/Leaves/Desktop/ACACACAC/强化学习/强化学习/DP实例模型.png)

### MDP四元组
- 状态集合S：图中除去黑色阴影的小格，其他11个格子分别代表一个状态，(2,4)和(3,4)代表终止状态。 
- 决策集合A：A=[‘north’, ‘east’, ‘west’, ‘south’]表示四个移动方向。 
- 状态转移分布P=(ps,a(s′)ps,a(s′)): 在某个状态s ∈∈ S, 若采取行动方向a，则s以0.8的概率按照a方向移动到s′s′, 以0.1的概率按照a的左侧方向移动，以0.1的概率按照a的右侧方向移动；如果移动方向没有S中的状态，则停留在原地；如果s是终止状态，则始终停留在原地。 
- 奖励函数R: 如图，对于每个状态s∈Ss∈S, 都对应一个奖励值（图中格子上的数值）；若某次行动移动到该状态，则得到对应的奖励值。
--------------------- 
[详细信息](https://blog.csdn.net/newbieMath/article/details/78665622)

### 代码
- 优点：q函数以及v函数计算那块比较清晰，贪婪策略不错。