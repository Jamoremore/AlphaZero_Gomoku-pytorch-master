# AlphaZero_Gomoku-pytorch-master

算法改自 [junxiaosong/AlphaZero_Gomoku](https://github.com/junxiaosong/AlphaZero_Gomoku) ，做了以下调整：

* 通过pytorch对网络训练和决策部分的代码进行了重写
* 基于10 * 10的棋盘进行了约5000次的训练（可以10:0击败探索深度为5000的tcls算法）
* 增加了GUI
* 优化了算法，相比原文得到了5倍左右训练速度的提升
* data/logs.txt记录了我的训练情况，便于绘制迭代曲线、了解训练进度
* 调整了train.py，在外部输出进度，便于查看服务器训练情况

## 使用方法
与AI进行对弈

	$ python human_play.py
	
模型训练:

	$ python train.py

torch版本：1.13.0

### Example of Game

![Example](https://github.com/Jamoremore/AlphaZero_Gomoku-pytorch-master/example.gif)  
