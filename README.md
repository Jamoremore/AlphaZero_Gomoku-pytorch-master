# AlphaZero_Gomoku-pytorch-master

基于alphazero的可视化五子棋程序

算法改自 [junxiaosong/AlphaZero_Gomoku](https://github.com/junxiaosong/AlphaZero_Gomoku) ，做了以下调整：

* 通过pytorch对网络训练和决策部分的代码进行了重写
* 基于10 * 10的棋盘进行了约5000次的训练（可以10:0击败探索深度为5000的tcls算法）
* 增加了GUI
* 优化了算法，相比原文得到了5倍左右训练速度的提升
* data/logs.txt记录了我的训练情况，便于绘制迭代曲线、了解训练进度
* 调整了train.py，在外部输出进度，便于查看服务器训练情况

## 局面描述
对于10x10的棋盘，采用4个10x10的二值特征平面。
其中前两个平面分别表示当前player的棋子位置和对手player的棋子位置，有棋子的位置是1，没棋子的位置是0. 第三个平面表示对手player最近一步的落子位置，也就是整个平面只有一个位置是1，其余全部是0. 第四个平面，表示的是当前player是不是先手player，如果是先手player则整个平面全部为1，否则全部为0.

## 网络结构
最开始是公共的3层全卷积网络，分别使用32、64和128个3x3的filter，使用ReLu激活函数。然后再分成policy和value两个输出，在policy这一端，先使用4个1x1的filter进行降维，再接一个全连接层，使用softmax非线性函数直接输出棋盘上每个位置的落子概率；在value这一端，先使用2个1x1的filter进行降维，再接一个64个神经元的全连接层，最后再接一个全连接层，使用tanh非线性函数直接输出[-1,1]之间的局面评分。

## 评估方式
每隔1000次循环，与随机rollout的pure mcls AI进行十次对局。若胜率达到10:0，则将mcls搜索深度增加1000。pure mcls AI初始搜索深度1000，最大为5000

## 使用方法
与AI进行对弈

	$ python human_play.py
	
模型训练:

	$ python train.py

torch版本：1.13.0

### 运行示例

![Example](https://github.com/Jamoremore/AlphaZero_Gomoku-pytorch-master/blob/main/example.gif)  
