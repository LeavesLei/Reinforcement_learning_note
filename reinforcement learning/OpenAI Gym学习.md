### CartPole 代码

```python
import gym
#初始化环境名称
env = gym.make('CartPole-v0')
#每次学习前都要重置环境，让环境恢复到一个随机状态
observation = env.reset

#多次循环，选择动作执行
for t in range(100):
    #随机选择一个动作
    action = env.action_space.sample()
    #执行动作，获取环境反馈
    observation,reward,done,info = env.step(action)
    #如果玩死了就退出
    if done：
        break
    env.render()
```

### 编写Gym环境
- states，返回环境的状态空间
- actons，返回环境的动作空间
- reset，重置环境
- step，针对环境执行动作，使环境进入下一个状态
