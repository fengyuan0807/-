# 机器学习day01

### 今日目标

机器学习介绍

基础环境安装以及基本使用



### 机器学习科学计算库简介

* 机器学习概述
* 机器学习环境安装
* Matplotlib
* Numpy
* Pandas
* 拓展



### 人工智能概述

* 应用
* 发展三要素
  * 数据
  * 算法
  * 计算力
* 人工智能、机器学习、深度学习关系
  * 机器学习是人工智能实现的途径
  * 深度学习是人工智能的方法发展而来（神经网络）
* 知识扩展
  * cpu和gpu区别
    * https://blog.csdn.net/cyj2014go/article/details/80283007
    * http://www.sohu.com/a/201309334_468740
  * Google TPU 介绍：（需要翻墙）
    * https://buzzorange.com/techorange/2017/09/27/what-intel-google-nvidia-microsoft-do-for-ai-chips/



### 3.人工智能的发展

* 图灵测试

  * 图灵测试与第一次AI热潮

    2016年是计算机科学领域的最高奖项——图灵奖设立50周年。1966年，美国计算机协会(ACM)以开创计算机科学和人 工智能基本理论的科学巨匠——艾伦·图灵的名字设立了这项“计算机界的诺贝尔奖”。

    艾伦·图灵的人生本身就是一个传奇。他利用自己卓越的数学、密码学和计算理论知识，在第二次世界大战期间，帮助英国军方成功破译了德军使用的著名密码系统——恩尼格玛(Enigma)密码机。他早在20世纪30年代就提出了指导所有现代计算 机(那个时候，通用电子计算机还没有诞生)的计算原理设计的图灵机理论。他还是个擅长马拉松的运动健将，却因为性取向 问题受到英国政府的迫害，最终服毒身亡。有关图灵的传奇故事，2014年的电影《模仿游戏》很值得推荐，该片曾于2015年7 月在中国大陆公映。

    艾伦·图灵是人工智能的开拓者，他所提出的图灵测试，直到今天仍然是我们判定一部机器是否具有人类智慧的重要手 段。那么，到底什么是图灵测试呢?

* 达特茅斯会议  



### 4.人工智能主要分支

* 计算机视觉
* 语音识别
* 文本挖掘
* 机器翻译
* 机器人



### 机器学习定义工作流程概述

* 计算机从数据中自动分析获取模型，并利用模型对未知的数据进行预测
* **获取数据->数据基本处理->特征工程->机器学习（模型训练）->模型评估**



### 6.机器学习工作流程各步骤解释

* 获取数据
  * 数据简介
    * 样本
      * 一行数据我们称为一个**样本**
    * 特征
      * 一列数据我们成为一个**特征**
    * 目标值
      * 我们期望得到的结果
  * 数据类型
    * 数据类型一：特征值+目标值（目标值是连续的和离散的）
    * 数据类型二：只有特征值，没有目标值
  * 数据分割
    * 训练集
    * 测试集
* 数据预处理（广义）
  * 即对数据进行缺失值、去除异常值等处理
* 特征工程（非常重要，耗时、费力、对结果影响大）
  * 特征工程是使用**专业背景知识和技巧处理数据**，**使得特征能在机器学习算法上发挥更好的作用的过程**。
  * 我的理解：是最大限度地从原始数据中提取特征以供算法和模型使用
* 算法模型训练
* 模型评估



### 7.机器学习算法分类介绍

* 机器学习的分类
  * 监督学习（有目标值）
    * 目标值连续：回归
    * 目标值离散：分类
  * 无监督学习（无目标值）
    * 无目标值，根据样本的特征进行聚类
  * 半监督学习
    * 只有部分样本有目标值
  * 强化学习
    * 输入动态的数据，决策+回报函数
    * 目的是得到更多的奖励的一系列决策过程



### 8.模型评估

* 分类模型评估

  1）准确率：预测正确的样本占样本总数的比例。

  

  2）精确率：正确预测为正例的样本占全部预测为正例的比例。

  

  3）召回率：正确预测为正例的样本占全部为正例的样本的比例。

  

  4）F1-score：主要用于评估模型的稳健性。

  

  5）AUC指标：主要用于二分类场景中样本不均衡情况下的模型评估。

  

* 回归模型评估

  * https://www.jianshu.com/p/9ee85fdad150

  * ##### 均方根误差（Root Mean Squared Error，RMSE）

    * ![image-20191211100657985](/Users/rookieyu/Library/Application Support/typora-user-images/image-20191211100657985.png)

  * ##### 相对平方误差（Relative Squared Error，RSE）

    * ![image-20191211100708799](/Users/rookieyu/Library/Application Support/typora-user-images/image-20191211100708799.png)

  * ##### 平均绝对误差（Mean Absolute Error，MAE)

    * ![image-20191211100721228](/Users/rookieyu/Library/Application Support/typora-user-images/image-20191211100721228.png)

  * ##### 相对绝对误差（Relative Absolute Error，RAE)

    * ![image-20191211100729193](/Users/rookieyu/Library/Application Support/typora-user-images/image-20191211100729193.png)

* 拟合  

  * 欠拟合：模型学习到的特征较少，导致模型对未知数据的预测能力过低。

  * 过拟合：模型学习到的特征较多（异常数据，噪声），导致模型对未知数据

    的预测能力同样过低。

    

### 9.Azure机器学习平台实验演示1

1）获取数据

2）数据的预处理

3）特征工程

4）算法模型训练

5）算法模型评估



## 10.Azure机器学习平台实验演示2



### 11.深度学习简介

* 神经网络

* 卷积神经网络

* 节点（神经元）、深度

  

### 12.基础环境安装

* 创建虚拟环境
* 安装扩展包
  * 注意安装包版本，最新版本不稳定
  * 资料中  pip3 install -r requirements.txt
* windows中安装虚拟环境
  * https://blog.csdn.net/zhushixia1989/article/details/93366838

### 13.jupyter notebook的基本使用1

* ipython的网页加强版
* 启动
  * jupyter notebook
* 基本使用
  * 编辑模式
  * 命令模式
* 默认地址
  * http://localhost:8888



### 14.jupyter notebook的基本使用2

* makedown模式的使用

* 其他功能添加

  * ```shell
    python -m pip install jupyter_contrib_nbextensions
    jupyter contrib nbextension install --user --skip-running-check
    ```



### 15.matplotlib的基本使用

* 画2D图像

* 1）准备数据

  ~~~
  import matplotlib.pyplot as plt
  X = ? Y = ?
  ~~~

* 2）创建画布

  ~~~
  plt.figure(figsize=(20, 8), dpi=80)   
  ~~~

* 3）绘制图像

* ~~~
  plt.plot(X, Y)
  ~~~

* 4）显示图像

* ~~~
  plt.show()
  # show 为显示 在交互模式下可以直接显示出来
  # show一次显示后第二次show缓存区没有数据显示不出来
  ~~~

  

* 有的电脑在使用pycharm的时候 出现错误提示

Python is not installed as a framework. The Mac OS X backend will not be able to function correctly if Python is not installed as a framework. See the Python documentation for more information on installing Python as a framework on Mac OS X. Please either reinstall Python as a framework, or try one of the other backends. If you are using (Ana)Conda please install python.app and replace the use of 'python' with 'pythonw'. See 'Working with Matplotlib on OSX' in the Matplotlib FAQ for more information.

```
import matplotlib
matplotlib.use('TkAgg')
```

