理解：就是一个数学模型，通过大量的输入，然后正向加上反向的修正，最终达到某个目的

1、CNN convolutional neural network 卷积神经网络
常用于图片分析等


2、 RNN recurrent neural network 循环神经网络
分析序列化数据


3、LSTM（long short-term memory 长短期记忆） RNN
相对于普通RNN，增加了输入，忘记，输出的控制

4、autoencoder 自编码
类似压缩，提取精髓，本质的操作，来降低数据量

5、生成对抗网络GAN （generative adversarial nets）
generator random output，discriminator tell，generator learn，recurrent，final produce

6、迁移学习
将一种理解代表特征的能力保留，然后套上另一层专职的神经网络，从而得到宁一种结果，所谓之迁移，但有时候也不一定会好用，看情况？

8、数据标准化
为什么？就是为了让不同影响力的参数，在训练是得到更加高效的结果。
特征标准化的途径有两种, 一种叫做 min max normalization, 他会将所有特征数据按比例缩放到0-1的这个取值区间. 有时也可以是-1到1的区间. 还有一种叫做 standard deviation normalization, 他会将所有特征数据缩放成 平均值为0, 方差为1

9、激励函数 activation function
有时候关系不是线性的，就需要掰弯，而这就是激励函数，像有relu，tanh的，啥的


10、过拟合（overfitting）
避免：增大数据量
正规化，什么L1,L2，dropout，啥的避免过于依赖训练数据

11、经验损失最小化
一个可以最大限度减少损失的模型寻找过程

12、损失
预测值和实际值的偏差

13、损失函数
一种可以以有意义的方式汇总各个损失，常见的有平方损失（L2），均方误差 (MSE) 指的是每个样本的平均平方损失

14、降低损失（reducing loss）
一般有梯度下降法（gradient descend），即在损失函数上，通过计算某个点的偏导数，得到负梯度（具体怎么算我也不知道），然后靠近损失函数更小的点移动。有随机梯度下降（SGD，只拿一个样本）和小批量的随机梯度下降（拿10-1000个样本计算梯度），和全批量。学习速率是往损失函数最小点靠近的步长问题。