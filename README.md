# AlphaZero_Gomoku-pytorch-master

基于alphazero的可视化五子棋程序

算法改自 [junxiaosong/AlphaZero_Gomoku](https://github.com/junxiaosong/AlphaZero_Gomoku) ，做了以下调整：

* 通过pytorch对网络训练和决策部分的代码进行了重写
* 基于10 * 10的棋盘进行了约5000次的训练（可以10:0击败探索深度为5000的tcls算法）
* 增加了GUI
* 优化了算法，相比原文得到了5倍左右训练速度的提升
* data/logs.txt记录了我的训练情况，便于绘制迭代曲线、了解训练进度
* 调整了train.py，在外部输出进度，便于查看服务器训练情况

每隔1000次循环，与mcls进行一次对弈。胜率达到10:0，则将mcls搜索深度增加1000.mcls初始搜索深度1000，最大为5000.

## 使用方法
与AI进行对弈

	$ python human_play.py
	
模型训练:

	$ python train.py

torch版本：1.13.0

### 运行示例

![Example](https://github.com/Jamoremore/AlphaZero_Gomoku-pytorch-master/blob/main/example.gif)  
