# 机器学习基础day02

### 回顾与反馈



### 今日目标

* matplotlib的使用
  * matplotlib实现绘制城市温度变换案例
  * 绘图辅助功能
    * 自定义坐标
    * 自定义标题
  * 一个坐标系下绘制多个图像
  * 绘制多个图像
  * 常见的其他绘图
* numpy
  * 基本操作
  * 数组间的运算
* pandas
  * 基本使用



### 实现基础绘图-莫城市温度变换图

* 导入 matplotlib.pylab

* 定义数据

  * 定义x坐标
  * 定义y坐标

* 创建画布

  * plt.figure(figsize=(20, 8), dpi=80)

* 绘制图像

  * plt.figure(figsize=(20, 8), dpi=80)

* 显示图像 

  * plt.show()

    

#### 绘制辅助功能（自定义x坐标，y坐标）

* 在plot后增加 x，y坐标数据

  * plt.xticks(x[::5], x_ticks_label)
  * plt.yticks(y_ticks[::5])

* 修改中文问题

  * 1、安装字体
  * 2、动态增加

* 添加网格

  * plt.grid(True, linestyle='--', alpha=0.5)

* 添加描述信息

  * plt.xlabel("时间")
    plt.ylabel("温度")
    plt.title("中午11点0分到12点之间的温度变化图示", fontsize=20)

* 图像保存

  * plt.savefig("test.png")

  * plt.show()会释放figure资源，如果在显示图像之后保存图片将只能保存空图片

    

### 在一个坐标系下绘制多个图像

* 多次plot绘制
* 绘制图例 在plot中增加label属性
* 显示图例
  * plt.legend(loc="best")    loc代表位置

### 在多个坐标系下绘制多个图像

* matplotlib.pyplot.subplots(nrows=1, ncols=1, **fig_kw) 创建一个带有多个axes(坐标系/绘图区)的图

* ```
  Parameters:    
  
  nrows, ncols : 设置有几行几列坐标系
      int, optional, default: 1, Number of rows/columns of the subplot grid.
  
  Returns:    
  fig : 图对象
  axes : 返回相应数量的坐标系
  
  设置标题等方法不同：
      set_xticks
      set_yticks
      set_xlabel
      set_ylabel
  ```

**plt.函数名()**相当于面向过程的画图方法，**axes.set_方法名()**相当于面向对象的画图方法。

### 常见的图形绘制

* **折线图**

  * plt.plot(x, y)

* **散点图**

  * api：plt.scatter(x, y)

* **柱状图**

  * plt.bar(x, width, align='center', **kwargs)

  * ```
    Parameters:    
    x : 需要传递的数据
    
    width : 柱状图的宽度
    
    align : 每个柱状图的位置对齐方式
        {‘center’, ‘edge’}, optional, default: ‘center’
    
    **kwargs :
    color:选择柱状图的颜色
    ```

* **直方图**

  * matplotlib.pyplot.hist(x, bins=None)

  * ```
    Parameters:    
    x : 需要传递的数据
    bins : 组距
    ```

* **饼图**

  * plt.pie(x, labels=,autopct=,colors)

  * ```
    Parameters:  
    x:数量，自动算百分比
    labels:每部分名称
    autopct:占比显示指定%1.2f%%
    colors:每部分颜色
    ```



### numpy介绍

Numpy（Numerical Python）是一个开源的Python科学计算库，**用于快速处理任意维度的数组**。

Numpy**支持常见的数组和矩阵操作**。对于同样的数值计算任务，使用Numpy比直接使用Python要简洁的多。

Numpy**使用ndarray对象来处理多维数组**，该对象是一个快速而灵活的大数据容器。

### ndarray介绍

NumPy提供了一个**N维数组类型ndarray**，它描述了**相同类型**的“items”的集合。

* 属性

* |     属性名字     |          属性解释          |
  | :--------------: | :------------------------: |
  |  ndarray.shape   |       数组维度的元组       |
  |   ndarray.ndim   |          数组维数          |
  |   ndarray.size   |      数组中的元素数量      |
  | ndarray.itemsize | 一个数组元素的长度（字节） |
  |  ndarray.dtype   |       数组元素的类型       |

* 形状

  * 一维数组
  * 二维数组
  * 三维数组

* 类型  dtype指定类型

* |     名称      |                       描述                        | 简写  |
  | :-----------: | :-----------------------------------------------: | :---: |
  |    np.bool    |      用一个字节存储的布尔类型（True或False）      |  'b'  |
  |    np.int8    |             一个字节大小，-128 至 127             |  'i'  |
  |   np.int16    |               整数，-32768 至 32767               | 'i2'  |
  |   np.int32    |              整数，-2^31 至 2^32 -1               | 'i4'  |
  |   np.int64    |              整数，-2^63 至 2^63 - 1              | 'i8'  |
  |   np.uint8    |               无符号整数，0 至 255                |  'u'  |
  |   np.uint16   |              无符号整数，0 至 65535               | 'u2'  |
  |   np.uint32   |             无符号整数，0 至 2^32 - 1             | 'u4'  |
  |   np.uint64   |             无符号整数，0 至 2^64 - 1             | 'u8'  |
  |  np.float16   | 半精度浮点数：16位，正负号1位，指数5位，精度10位  | 'f2'  |
  |  np.float32   | 单精度浮点数：32位，正负号1位，指数8位，精度23位  | 'f4'  |
  |  np.float64   | 双精度浮点数：64位，正负号1位，指数11位，精度52位 | 'f8'  |
  | np.complex64  |     复数，分别用两个32位浮点数表示实部和虚部      | 'c8'  |
  | np.complex128 |     复数，分别用两个64位浮点数表示实部和虚部      | 'c16' |
  |  np.object_   |                    python对象                     |  'O'  |
  |  np.string_   |                      字符串                       |  'S'  |
  |  np.unicode_  |                    unicode类型                    |  'U'  |

### 使用Numpy如何创建符合某种规律的数组

* 生成都是1的数组

```python
ones = np.ones([4,8])
```

* 生成都是0的数组

  ```python
  np.zeros_like(ones)
  ones = np.zeros([4,8])
  ```

* 从现有的数组生成

  * array

  * ```python
    a = np.array([[1,2,3],[4,5,6]])
    # 从现有的数组当中创建
    a1 = np.array(a)
    ```

  * asarray

  * ```python
    # 相当于索引的形式，并没有真正的创建一个新的
    a2 = np.asarray(a)
    ```

  * 区别
    * 深拷贝、浅拷贝

* 生成固定范围的数据

  * #### np.linspace (start, stop, num, endpoint)

    * 创建等差数组 — 指定数量
    * 参数:
      - start:序列的起始值
      - stop:序列的终止值
      - num:要生成的等间隔样例数量，默认为50
      - endpoint:序列中是否包含stop值，默认为ture

  * #### np.arange(start,stop, step, dtype)

    * 创建等差数组 — 指定步长
    * 参数
      - step:步长,默认值为1

  * #### np.logspace(start,stop, num)

    * 创建等比数列
    * 参数:
      - num:要生成的等比数列数量，默认为50

  

### 创建随机数组

* 正态分布方式

  * np.random.randn(*d0, d1, …, dn*)

    功能：从标准正态分布中返回一个或多个样本值 

  * **np.random.normal(\*loc=0.0\*, \*scale=1.0\*, \*size=None\*)**

    loc：float 

     此概率分布的均值（对应着整个分布的中心centre）

    scale：float

     此概率分布的标准差（对应于分布的宽度，scale越大越矮胖，scale越小，越瘦高） 

    size：int or tuple of ints 

     输出的shape，默认为None，只输出一个值

  * np.random.standard_normal(*size=None*)

    返回指定形状的标准正态分布的数组。

* 均匀分布

  * np.random.rand(d0,d1,...,dn)
    - 返回**[0.0，1.0)**内的一组均匀分布的数。
  * np.random.uniform(*low=0.0*, *high=1.0*, *size=None*)
    - 功能：从一个均匀分布[low,high)中随机采样，注意定义域是左闭右开，即包含low，不包含high. 
    - 参数介绍:
      - low: 采样下界，float类型，默认值为0；
      - high: 采样上界，float类型，默认值为1；
      - size: 输出样本数目，为int或元组(tuple)类型，例如，size=(m,n,k), 则输出m*n*k个样本，缺省时输出1个值。 
    - 返回值：ndarray类型，其形状和参数size中描述一致。
  * np.random.randint(low, high=None, size=None, dtype='l')
    - 从一个均匀分布中随机采样，生成一个整数或N维整数数组，
    - 取数范围：若high不为None时，取[low,high)之间随机整数，否则取值[0,low)之间随机整数。



### 数组的基本操作

* 索引和切片

  * 一维、二维、三维的数组如何索引？
    - 直接进行索引,切片
    - 对象[:, :] -- 先行后列

* 形状修改

  * ### ndarray.reshape(shape, order)

    * 返回一个具有相同数据域，但shape不一样的**视图**
    * 行、列不进行互换

  * ### ndarray.resize(new_shape)

    * 修改数组本身的形状（需要保持元素个数前后相同）
    * 行、列不进行互换

  * ### ndarray.T

    * 数组的转置
    * 将数组的行、列进行互换

* 类型修改

  * ### ndarray.astype(type)

    * 返回修改了类型之后的数组

  * ### ndarray.tostring([order])或者ndarray.tobytes([order])

    * 构造包含数组中原始数据字节的Python字节

* 数组的去重

  * ### np.unique()



### ndarray的运算

* 逻辑运算

  * 直接进行比较
  * 满足要求赋值

* 通用判断

  * all
    * 判断所有是否符合
  * any
    * 只有一个符合

* 三维运算

  * where
  * np.logical_and和np.logical_or

* 统计计算

  * a代表要求的数组  axis代表是行还是列
  * min(a, axis)  最小值
    - Return the minimum of an array or minimum along an axis.
  * max(a, axis]) 最大值
    - Return the maximum of an array or maximum along an axis.
  * median(a, axis) 中位数
    - Compute the median along the specified axis.
  * mean(a, axis, dtype) 平均值
    - Compute the arithmetic mean along the specified axis.
  * std(a, axis, dtype) 标准差
    - Compute the standard deviation along the specified axis.
  * var(a, axis, dtype) 方差
    - Compute the variance along the specified axis.

  * np.argmax  行最大
  * np.argmax  行最小

  

### 数组间的运算

* 数组与数
  * 减价乘除  对每一个值的运算
* 数组与数组
  * 广播机制
    * 1.数组的某一维度等长。 
    * 2.其中一个数组的某一维度为1 



### 矩阵复习

- np.matmul
  - 不支持矩阵和标量的运算
- np.dot
- 二者都是矩阵乘法。 np.matmul中禁止矩阵与标量的乘法。 在矢量乘矢量的內积运算中，np.matmul与np.dot没有区别。



### pandas介绍

- 增强图表可读性
- 便捷的数据处理能力
- 读取文件方便
- 封装了Matplotlib、Numpy的画图和计算



### pandas数组结构-series

* 创建

* ```python
  import pandas as pd
  pd.Series(data=None, index=None, dtype=None)
  ```

  * 参数：
    data：传入的数据，可以是ndarray、list等
    index：索引，必须是唯一的，且与数据的长度相等。如果没有传入索引参数，则默认会自动创建一个从0-N的整数索引。
    dtype：数据的类型
  * 直接创建
  * index创建
  * 字典创建

* 属性
  * index
  * values
  * 也可以使用索引来获取数据



### pandas数据结构-DataFrame1

DataFrame是一个类似于二维数组或表格(如excel)的对象，既有行索引，又有列索引

* 创建

  * ```python
    import pandas as pd
    
    pd.DataFrame(data=None, index=None, columns=None)
    ```



### pandas数据结构-DataFrame2

* 修改索引
  * 必须整体全部修改



### pandas数据结构-multiindex和panel

* multiindex

  * 多级索引

* ### Panel

  * *class* `pandas.Panel`(*data=None*, *items=None*, *major_axis=None*, *minor_axis=None*)
    - 作用：存储3维数组的Panel结构
    - 参数：
      - **data** : ndarray或者dataframe
      - **items** : 索引或类似数组的对象，axis=0
      - **major_axis** : 索引或类似数组的对象，axis=1
      - **minor_axis** : 索引或类似数组的对象，axis=2









