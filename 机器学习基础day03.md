# 机器学习基础day03

### 回顾与反馈



### 今日目标

* pandas的使用
* 数据分析案例



### pandas中的索引

* read_csv
  * 读取csv文件
* drop
  * 删除索引对应的数据
* data['索引'] 
  * 直接使用行列索引名字的方式（先列后行）
  * 获取当前索引的值
* 结合loc 和 iloc使用索引 （先列后行）
  * 使用loc:只能指定行列索引的名字
    data.loc['2018-02-27':'2018-02-22', 'open']
  * 这里使用的是 【】
  * 使用iloc可以通过索引下表获取
* ix 
  * 既可以使用索引小标，又可以使用索引
  * 即将淘汰



```python
# 推荐使用loc和iloc来获取的方式
data.loc[data.index[0:4], ['open', 'close', 'high', 'low']]
data.iloc[0:4, data.columns.get_indexer(['open', 'close', 'high', 'low'])]
```



#### 赋值和排序

* 赋值

* ```python
  # 直接修改原来的值
  data['close'] = 1
  # 或者
  data.close = 1
  ```

* 排序

  * dataFrame排序
    * 排序有两种形式，一种对于索引进行排序，一种对于内容进行排序
    * 值排序
      * 使用df.sort_values(by=, ascending=)
        - 单个键或者多个键进行排序,  多个值排序传入列表即可
        - 参数：
          - by：指定排序参考的键
          - ascending:默认升序
            - ascending=False:降序
            - ascending=True:升序
    * 索引排序
      * 使用df.sort_index给索引进行排序
  * series排序
    * 值排序
      * 使用series.sort_values(ascending=True)进行排序
        * series排序时，只有一列，不需要参数
    * 索引排序
      * 使用series.sort_index()进行排序



### pandas中的算术运算和逻辑运算

* 算术运算
  * add(other)  加
  * sub(other) 减
  * div              商
  * 也可以直接进行加减运算符使用
* 逻辑运算
  * 使用运算符号即可
  *  "> < = = & |"
* query(expr)
  * expr:查询字符串
  * 查询一个范围
* isin(values)
  * values:查询值是否在里面
  * 查询是否在我当前的列表里



### pandas中的统计函数

* describe

  * 能够直接得出很多统计结果,`count`, `mean`, `std`, `min`, `max` 等

    * | `count`  | Number of non-NA observations                              |
      | -------- | ---------------------------------------------------------- |
      | `sum`    | **Sum of values          求和**                            |
      | `mean`   | **Mean of values       平均值**                            |
      | `median` | Arithmetic median of values   中位数                       |
      | `min`    | **Minimum                 最小值**                         |
      | `max`    | **Maximum               最大值**                           |
      | `mode`   | Mode                        众数                           |
      | `abs`    | Absolute Value        绝对值                               |
      | `prod`   | Product of values    乘积                                  |
      | `std`    | **Bessel-corrected sample standard deviation   标准差**    |
      | `var`    | ** Unbiased variance           方差**                      |
      | `idxmax` | compute the index labels with the maximum      最大值索引  |
      | `idxmin` | compute the index labels with the minimum       最小值索引 |



**对于单个函数去进行统计的时候，坐标轴还是按照默认列“columns” (axis=0, default)，如果要对行“index” 需要指定(axis=1)**

value_counts  统计出现的次数



### pandas中的累计统计函数和自定义函数

| 函数      | 作用                        |
| --------- | --------------------------- |
| `cumsum`  | **计算前1/2/3/…/n个数的和** |
| `cummax`  | 计算前1/2/3/…/n个数的最大值 |
| `cummin`  | 计算前1/2/3/…/n个数的最小值 |
| `cumprod` | 计算前1/2/3/…/n个数的积     |

* 自定义运算
  * apply(func, axis=0)
    - func:自定义函数
    - axis=0:默认是列，axis=1为行进行运算



### pandas中绘图方式介绍

- `DataFrame.plot`(*kind='line'*)     kind : str，需要绘制图形的种类
  - **‘line’ : line plot (default)  折线图**
  - ‘bar’ : vertical bar plot       柱状图
  - ‘barh’ : horizontal bar plot  横向柱状图
    - 关于“barh”的解释：
    - http://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.plot.barh.html
  - ‘hist’ : histogram        直方图
  - ‘pie’ : pie plot              饼图
  - ‘scatter’ : scatter plot  散点图



### pandas中文件的读取和存储

* csv
  * pandas.read_csv(filepath_or_buffer, sep =',', usecols )
    - filepath_or_buffer:文件路径
    - sep :分隔符，默认用","隔开
    - usecols:指定读取的列名，列表形式
  * DataFrame.to_csv(path_or_buf=None, sep=', ’, columns=None, header=True, index=True, mode='w', encoding=None)
    - path_or_buf :文件路径
    - sep :分隔符，默认用","隔开
    - columns :选择需要的列索引
    - header :boolean or list of string, default True,是否写进列索引值
    - index:是否写入索引
    - mode:'w'：重写, 'a' 追加

* HDF

  * **HDF5文件的读取和存储需要指定一个键，值为要存储的DataFrame**

    - pandas.read_hdf(path_or_buf，key =None，** kwargs)

      从h5文件当中读取数据

      - path_or_buffer:文件路径
      - key:读取的键
      - return:Theselected object

    - DataFrame.to_hdf(path_or_buf, *key*, **\*kwargs*)

* JSON

  * pandas.read_json(path_or_buf=None, orient=None, typ='frame', lines=False)
    - 将JSON格式准换成默认的Pandas DataFrame格式
    - orient : string,Indication of expected JSON string format.
      - 'split' : dict like {index -> [index], columns -> [columns], data -> [values]}
        - split 将索引总结到索引，列名到列名，数据到数据。将三部分都分开了
      - 'records' : list like [{column -> value}, ... , {column -> value}]
        - records 以`columns：values`的形式输出
      - 'index' : dict like {index -> {column -> value}}
        - index 以`index：{columns：values}...`的形式输出
      - 'columns' : dict like {column -> {index -> value}},默认该格式
        - colums 以`columns:{index:values}`的形式输出
      - 'values' : just the values array
        - values 直接输出值
    - lines : boolean, default False
      - 按照每行读取json对象
    - typ : default ‘frame’， 指定转换成的对象类型series或者dataframe
  * DataFrame.to_json(path_or_buf=None, orient=None, lines=False)
    - 将Pandas 对象存储为json格式
    - *path_or_buf=None*：文件地址
    - orient:存储的json形式，{‘split’,’records’,’index’,’columns’,’values’}
    - lines:一个对象存储为一行



### 缺失值的处理

- 获取缺失值的标记方式(NaN或者其他标记方式)
- 如果缺失值的标记方式是NaN
  - 判断数据中是否包含NaN：
    - pd.isnull(df)
    - pd.notnull(df)
  - 存在缺失值nan:
    - 1、删除存在缺失值的:dropna(axis='rows')
      - 注：不会修改原数据，需要接受返回值
    - 2、替换缺失值:fillna(value, inplace=True)
      - value:替换成的值
      - inplace:True:会修改原数据，False:不替换修改原数据，生成新的对象
- 如果缺失值没有使用NaN标记，比如使用"？"
  - 先替换‘?’为np.nan，然后继续处理  
  - 使用replace替换



### 数据离散化

* 应用cut、qcut实现数据的区间分组
  * pd.qcut(data, q)：
    - 对数据进行分组将数据分组，一般会与value_counts搭配使用，统计每组的个数
    - series.value_counts()：统计分组次数
  * pd.cut
    * 自定义区间分组
* 应用get_dummies实现数据的one-hot编码
  * 把每个类别生成一个布尔列，这些列中只有一列可以为这个样本取值为1.其又被称为热编码。
  * data:array-like, Series, or DataFrame
  * prefix:分组名字



### 数据表的合并

* pd.concat([data1, data2], axis=1)
  - 按照行或列进行合并,axis=0为列索引，axis=1为行索引
* pd.merge(left, right, how='inner', on=None)
  - 可以指定按照两组数据的共同键值对合并或者左右各自
  - `left`: DataFrame
  - `right`: 另一个DataFrame
  - `on`: 指定的共同键
  - how:按照什么方式连接



### 交叉表和透视表的介绍

- 交叉表：

  交叉表用于计算一列数据对于另外一列数据的分组个数(用于统计分组频率的特殊透视表)

  - pd.crosstab(value1, value2)

- 透视表：指定某一列对另一列的关系百分占比

  透视表是将原有的DataFrame的列分别作为行索引和列索引，然后对指定的列应用聚集函数

  - data.pivot_table(）

- - DataFrame.pivot_table([], index=[])



### 数组聚合介绍

- DataFrame.groupby(key, as_index=False)
  - key:分组的列数据，可以多个



### 星巴克案例实现

* 从文件中读取星巴克店铺数据

* ```python
  starbucks = pd.read_csv("./data/starbucks/directory.csv")
  ```

* 按照国家分组，求出每个国家的星巴克零售店数量

* ```python
  count = starbucks.groupby(['Country']).count()
  ```

* 画图显示结果

* ```python
  count['Brand'].plot(kind='bar', figsize=(20, 8))
  plt.show()
  ```



### 电影案例分析1



### 电影案例分析2

* 统计电影分类(genre)的情况



