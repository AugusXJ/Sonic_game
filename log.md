## content
[version1](#version1)
[version2](#version2)

<span id = "version1"></span>
## version1
**(2018.5.21)**： 使用随机策略作为版本1提交，得到分数1300左右。
<span id = "version2"></span>
## version2
**(2018.5.21)**： 使用双层DQN读取特征，初步提交失败，没有结果。
**(2018.5.22)**： 
`12:00`  本地测试可运行，但是速度缓慢，大概1小时2个eposide。查阅文档知docker需要pull下tensorflow，pull之后重新提交。
`3:00` 报错，state=env.reset()错误。怀疑是不能进行两次reset？难道比赛是让我们在本地训练好数据再提交？将state=env.reset()改成state = np.array(env.reset())再试一次。
`6:00` 再次提交结果仍然是错误的，并且返回来的输出结果可以看出，提交的eooside是最终的运行结果，所以我们需要在本地训练好之后再提交，目前主要有两个困难：1.本地训练速度慢 2. 训练好之后如何直接提交agent
