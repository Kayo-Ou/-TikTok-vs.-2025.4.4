# **TikTok 项目**

## 研究TikTok内容类型（声明 vs. 观点）对流量与合规性的影响分析

- Tik Tok视频创作者按发布的内容可以分成两大类：发表“声明”和发表“观点”。

- 接下来将洞察数据集发表“声明”和发表“观点”的视频博主究竟哪一类型更受欢迎，哪类型的视频得到观众评论、转发、点赞更多。

- 为利益相关者创建可行性的建议。当在Tik Tok发布推广、广告等内容的时候。视频内容选择“声明”还是“观点”，会得到观众关注更多。说明视频合规的重要性，为什么发布视频前要进行合规性审查。

- 此项目将会使用工具Python分析数据集，使用工具：`pandas`、`numpy`、`matplotlib.pyplot`分析数据及创建可视化。



## 结论
  ### 数据集属性
- “声明”出现了9608次，“观点”出现了9476次,表明数据集收集的“声明”和“观点”视频数量差不多。


  ### 视频合规性分析
- 发布“声明”的作者被封禁次数为1603次。发布“观点”的作者被封禁次数为196次。
- 发布“声明”的作者更有机会被封禁，因为声明更可能出现违反平台规则导致被封禁的内容。
- 作者发布的封禁内容被转发的次数是14468次。而未封禁视频的转发次数只为437次。
- 视频声明和观点的占比大约是差不多，但是声明的视频更容易得到观众的点赞评论转发。同时声明被封禁的用户占了视频总数的7.42%，而观点被封禁的用户占了总视频的1.01%。结论是发表声明的用户被封禁的概率要比发表评论的用户高出6.41%。
- **作者发布的不当言论更有可能被大量的转发，造成群体的不适和其他的不良影响。这种账户有更大机会被迅速封禁**。


### “声明”和“观点”视频谁更受欢迎？
- “声明”视频被观看次数为平均值为501029.45次，中位数为501555.00次，“观点”视频被观看次数为平均值为4956.43次，中位数为4953.00次。
- “声明”视频和“观点”视频发布的数量接近，但是“声明”视频平均被观看次数要比“观点”视频多100倍左右。“声明”视频被点赞的机会和“观点”视频相比高出约10%。“声明”视频被评论的机会要比“观点”视频高出50%。“声明”视频被转发的机会要比“观点”视频高出20%。
-  **由此看出“声明”视频平均被观看次数大幅度领先“观点”视频。用户发表“声明”要比发表“观点”更受欢迎，获取更多的流量。**

### 当在Tik Tok发布推广、广告等内容的时候。发表“声明”要比发表“观点”更受欢迎，获取更多的流量。
### 但是注意“声明”的内容不要触犯平台的规则，发布前应进行平台合规性的审查，避免官方账号被封禁。






- 分页 -------------------------------------------------------------------------------------------------------------------

# **开始处理数据集：识别数据类型并汇总信息**

## **PLAN: 计划**

## 检查提供的数据并为其分析做好准备。

**调查并理解所提供的数据**

1. 熟悉数据
2. 汇总数据的摘要信息
3. 开始探索性数据分析（EDA）的过程，并揭示数据中包含的见解

**目标是：**当在Tik Tok发布推广、广告等内容的时候。视频内容选择声明还是观点，会得到观众关注更多，并向数据团队汇报我的发现。

*此项目分为三个部分：*

**第一部分：** 理解情况  
* 如何准备以理解 TikTok 信息？

**第二部分：** 理解数据  
* 创建一个 pandas 数据框，用于数据学习和未来的探索性数据分析（EDA）及统计活动  
* 汇总数据的摘要信息，以指导下一步行动

**第三部分：** 理解变量  
* 使用摘要数据的检查结果来指导对变量的深入调查

### **任务 1. 理解情况**

**如何最好地准备以理解和组织提供的信息？**

* 首先探索数据集，并考虑查看数据字典。

- 明确项目目标：为利益相关者创建可行性的建议。当在Tik Tok发布推广、广告等内容的时候。视频内容选择声明还是观点，会得到观众关注更多。
- 我的任务：导入数据并为团队进行审核，提供列数据类型、数据值非空数、相关列和无关列的摘要，以及其他我认为值得在笔记本中分享/展示的代码相关内容。我需要选择几个变量作为重点。包括它们的最小值和最大值。组合或修改给出的结构来创建有意义的变量。

## **PROCESS/ANALYTIC:处理/分析**

### **任务 2a. 导入和数据加载**

首先导入加载和探索数据集所需的包。使用以下导入语句：
*   `import pandas as pd`

*   `import numpy as np`

*   `import matplotlib.pyplot as plt`



```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```

接着，将数据集加载到数据框中。创建数据框将进行数据操作、探索性数据分析（EDA）和统计活动。


```python
data = pd.read_csv("tiktok_dataset.csv")
```

### **任务 2b. 理解数据 - 检查数据**

通过**编写以下代码**查看并检查数据框的摘要信息：

1. `data.head(10)`
2. `data.info()`
3. `data.describe()`

*思考以下问题：*

**问题 1：** 在查看数据框的前几行时，观察到了什么？每一行代表什么？

**问题 2：** 在查看 `data.info()` 的输出时，有哪些不同的变量？是否有空值？所有变量都是数值型的吗？还有什么其他值得注意的地方吗？

**问题 3：** 在查看 `data.describe()` 的输出时，查看每个变量的分布情况，是否有可疑的值？是否存在异常值？


















```python
data.head(10)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>#</th>
      <th>claim_status</th>
      <th>video_id</th>
      <th>video_duration_sec</th>
      <th>video_transcription_text</th>
      <th>verified_status</th>
      <th>author_ban_status</th>
      <th>video_view_count</th>
      <th>video_like_count</th>
      <th>video_share_count</th>
      <th>video_download_count</th>
      <th>video_comment_count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>claim</td>
      <td>7017666017</td>
      <td>59</td>
      <td>someone shared with me that drone deliveries a...</td>
      <td>not verified</td>
      <td>under review</td>
      <td>343296.0</td>
      <td>19425.0</td>
      <td>241.0</td>
      <td>1.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>claim</td>
      <td>4014381136</td>
      <td>32</td>
      <td>someone shared with me that there are more mic...</td>
      <td>not verified</td>
      <td>active</td>
      <td>140877.0</td>
      <td>77355.0</td>
      <td>19034.0</td>
      <td>1161.0</td>
      <td>684.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>claim</td>
      <td>9859838091</td>
      <td>31</td>
      <td>someone shared with me that american industria...</td>
      <td>not verified</td>
      <td>active</td>
      <td>902185.0</td>
      <td>97690.0</td>
      <td>2858.0</td>
      <td>833.0</td>
      <td>329.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>claim</td>
      <td>1866847991</td>
      <td>25</td>
      <td>someone shared with me that the metro of st. p...</td>
      <td>not verified</td>
      <td>active</td>
      <td>437506.0</td>
      <td>239954.0</td>
      <td>34812.0</td>
      <td>1234.0</td>
      <td>584.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>claim</td>
      <td>7105231098</td>
      <td>19</td>
      <td>someone shared with me that the number of busi...</td>
      <td>not verified</td>
      <td>active</td>
      <td>56167.0</td>
      <td>34987.0</td>
      <td>4110.0</td>
      <td>547.0</td>
      <td>152.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>6</td>
      <td>claim</td>
      <td>8972200955</td>
      <td>35</td>
      <td>someone shared with me that gross domestic pro...</td>
      <td>not verified</td>
      <td>under review</td>
      <td>336647.0</td>
      <td>175546.0</td>
      <td>62303.0</td>
      <td>4293.0</td>
      <td>1857.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>7</td>
      <td>claim</td>
      <td>4958886992</td>
      <td>16</td>
      <td>someone shared with me that elvis presley has ...</td>
      <td>not verified</td>
      <td>active</td>
      <td>750345.0</td>
      <td>486192.0</td>
      <td>193911.0</td>
      <td>8616.0</td>
      <td>5446.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>8</td>
      <td>claim</td>
      <td>2270982263</td>
      <td>41</td>
      <td>someone shared with me that the best selling s...</td>
      <td>not verified</td>
      <td>active</td>
      <td>547532.0</td>
      <td>1072.0</td>
      <td>50.0</td>
      <td>22.0</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>9</td>
      <td>claim</td>
      <td>5235769692</td>
      <td>50</td>
      <td>someone shared with me that about half of the ...</td>
      <td>not verified</td>
      <td>active</td>
      <td>24819.0</td>
      <td>10160.0</td>
      <td>1050.0</td>
      <td>53.0</td>
      <td>27.0</td>
    </tr>
    <tr>
      <th>9</th>
      <td>10</td>
      <td>claim</td>
      <td>4660861094</td>
      <td>45</td>
      <td>someone shared with me that it would take a 50...</td>
      <td>verified</td>
      <td>active</td>
      <td>931587.0</td>
      <td>171051.0</td>
      <td>67739.0</td>
      <td>4104.0</td>
      <td>2540.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
data.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 19382 entries, 0 to 19381
    Data columns (total 12 columns):
     #   Column                    Non-Null Count  Dtype  
    ---  ------                    --------------  -----  
     0   #                         19382 non-null  int64  
     1   claim_status              19084 non-null  object 
     2   video_id                  19382 non-null  int64  
     3   video_duration_sec        19382 non-null  int64  
     4   video_transcription_text  19084 non-null  object 
     5   verified_status           19382 non-null  object 
     6   author_ban_status         19382 non-null  object 
     7   video_view_count          19084 non-null  float64
     8   video_like_count          19084 non-null  float64
     9   video_share_count         19084 non-null  float64
     10  video_download_count      19084 non-null  float64
     11  video_comment_count       19084 non-null  float64
    dtypes: float64(5), int64(3), object(4)
    memory usage: 1.8+ MB



```python
data.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>#</th>
      <th>video_id</th>
      <th>video_duration_sec</th>
      <th>video_view_count</th>
      <th>video_like_count</th>
      <th>video_share_count</th>
      <th>video_download_count</th>
      <th>video_comment_count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>19382.000000</td>
      <td>1.938200e+04</td>
      <td>19382.000000</td>
      <td>19084.000000</td>
      <td>19084.000000</td>
      <td>19084.000000</td>
      <td>19084.000000</td>
      <td>19084.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>9691.500000</td>
      <td>5.627454e+09</td>
      <td>32.421732</td>
      <td>254708.558688</td>
      <td>84304.636030</td>
      <td>16735.248323</td>
      <td>1049.429627</td>
      <td>349.312146</td>
    </tr>
    <tr>
      <th>std</th>
      <td>5595.245794</td>
      <td>2.536440e+09</td>
      <td>16.229967</td>
      <td>322893.280814</td>
      <td>133420.546814</td>
      <td>32036.174350</td>
      <td>2004.299894</td>
      <td>799.638865</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000000</td>
      <td>1.234959e+09</td>
      <td>5.000000</td>
      <td>20.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>4846.250000</td>
      <td>3.430417e+09</td>
      <td>18.000000</td>
      <td>4942.500000</td>
      <td>810.750000</td>
      <td>115.000000</td>
      <td>7.000000</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>9691.500000</td>
      <td>5.618664e+09</td>
      <td>32.000000</td>
      <td>9954.500000</td>
      <td>3403.500000</td>
      <td>717.000000</td>
      <td>46.000000</td>
      <td>9.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>14536.750000</td>
      <td>7.843960e+09</td>
      <td>47.000000</td>
      <td>504327.000000</td>
      <td>125020.000000</td>
      <td>18222.000000</td>
      <td>1156.250000</td>
      <td>292.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>19382.000000</td>
      <td>9.999873e+09</td>
      <td>60.000000</td>
      <td>999817.000000</td>
      <td>657830.000000</td>
      <td>256130.000000</td>
      <td>14994.000000</td>
      <td>9599.000000</td>
    </tr>
  </tbody>
</table>
</div>



- 回答问题1：每一行都代表该用户对该视频发表的评论，并展示了视频可以被量化的参数。
- 回答问题2：有三种不同的数据类型：字符串、64位整数、64位浮点数。有部分列存在着空值。并不是所有变量都是数值型。数据集共有19382行和12列。
- 回答问题3：视频ID列类型错误，应为文本object字符串类型类型，将此列转换字符串类型。所有数值列可以只保留两位小数便于观察。

### **任务 2c. 理解数据 - 调查变量**

在此阶段，将开始更仔细地调查变量，以更好地理解数据。

从项目提案中可知，最终目标是视频内容选择“声明”和“观点”，会得到观众关注更多。因此，理解数据的第一步可能是检查 `claim_status` 变量。首先确定每个不同声明状态的视频数量。


```python
#  移除包含#N/A的行
data = data[~data.apply(lambda row: row.astype(str).str.contains('#N/A').any(), axis=1)]

#  将video_id列转换为字符串类型
data['video_id'] = data['video_id'].astype(str)

# 统计 claim_status 列中 claim 和 opinion 出现的次数
claim_opinion_counts = data['claim_status'].value_counts()

# 打印结果
print(claim_opinion_counts)

# 创建并显示可视化图表
plt.figure(figsize=(10, 6))
ax = claim_opinion_counts.plot(kind='bar', color=['#1f77b4', '#ff7f0e'], rot=0)
plt.title('Distribution of Claim Status', fontsize=14)
plt.xlabel('Status Type', fontsize=12)
plt.ylabel('Count', fontsize=12)

# 添加数值标签
for p in ax.patches:
    ax.annotate(f'{p.get_height():,.0f}', 
                (p.get_x() + p.get_width() / 2., p.get_height()), 
                ha='center', va='center', 
                xytext=(0, 9), 
                textcoords='offset points')

plt.grid(axis='y', linestyle='--', alpha=0.7)
plt.tight_layout()
plt.show()
```

    claim      9608
    opinion    9476
    Name: claim_status, dtype: int64



![png](output_18_1.png)


**问题：** 你注意到显示的数值有什么特点吗？

“声明”出现了9608次，“观点”出现了9476次,意思是数据集收集的“声明”和“观点”视频数量差不多。

接下来，检查与每个不同声明状态（claim_status）相关的互动趋势。

首先使用布尔掩码（Boolean masking）根据声明状态过滤数据，然后计算每个声明状态的平均（mean）和中位数（median）视频被观看次数（video_view_count）


```python
# 根据 claim_status 过滤数据
claim_data = data[data['claim_status'] == 'claim']
opinion_data = data[data['claim_status'] == 'opinion']

# 计算 claim 状态的平均和中位数观看次数，并保留两位小数
claim_mean_views = round(claim_data['video_view_count'].mean(), 2)
claim_median_views = round(claim_data['video_view_count'].median(), 2)

# 计算 opinion 状态的平均和中位数观看次数，并保留两位小数
opinion_mean_views = round(opinion_data['video_view_count'].mean(), 2)
opinion_median_views = round(opinion_data['video_view_count'].median(), 2)
```


```python
# 打印结果，保留两位小数
print("Claim Status - Mean Views:", "{:.2f}".format(claim_mean_views))
print("Claim Status - Median Views:", "{:.2f}".format(claim_median_views))
print("Opinion Status - Mean Views:", "{:.2f}".format(opinion_mean_views))
print("Opinion Status - Median Views:", "{:.2f}".format(opinion_median_views))

# 创建第一个图表 - Claim Status
plt.figure(figsize=(8, 6))

# 准备数据
categories = ['Mean Views', 'Median Views']
claim_values = [claim_mean_views, claim_median_views]
x = range(len(categories))

# 绘制柱状图
plt.bar(x, claim_values, width=0.5, color='#1f77b4')

# 添加图表元素
plt.title('Claim Status - Video Views Metrics', fontsize=14)
plt.xlabel('Metric', fontsize=12)
plt.ylabel('View Count', fontsize=12)
plt.xticks(x, categories)

# 添加数值标签
for i, v in enumerate(claim_values):
    plt.text(i, v + 1000, "{:,.2f}".format(v), ha='center')

# 调整布局和显示
plt.tight_layout()
plt.grid(axis='y', linestyle='--', alpha=0.7)
plt.show()

# 创建第二个图表 - Opinion Status
plt.figure(figsize=(8, 6))

# 准备数据
opinion_values = [opinion_mean_views, opinion_median_views]

# 绘制柱状图
plt.bar(x, opinion_values, width=0.5, color='#ff7f0e')

# 添加图表元素
plt.title('Opinion Status - Video Views Metrics', fontsize=14)
plt.xlabel('Metric', fontsize=12)
plt.ylabel('View Count', fontsize=12)
plt.xticks(x, categories)
plt.ylim(0, 20000)  # 设置Y轴最大值为20000

# 添加数值标签
for i, v in enumerate(opinion_values):
    plt.text(i, v + 500, "{:,.2f}".format(v), ha='center')  # 调整了标签位置

# 调整布局和显示
plt.tight_layout()
plt.grid(axis='y', linestyle='--', alpha=0.7)
plt.show()
```

    Claim Status - Mean Views: 501029.45
    Claim Status - Median Views: 501555.00
    Opinion Status - Mean Views: 4956.43
    Opinion Status - Median Views: 4953.00



![png](output_22_1.png)



![png](output_22_2.png)


**问题：** 每个“声明”和“观点”类别中的均值和中位数有什么特点吗？

- “声明”视频被观看次数为平均值为501029.45次，中位数为501555.00次，“观点”视频被观看次数为平均值为4956.43次，中位数为4953.00次。

-  由此看出“声明”视频被观看次数大幅度领先“观点”视频。

- “声明”和“观点”中位数和平均值相当接近，当中位数和平均值接近时，通常表明数据分布对称、没有极端值、集中趋势明显且分布均匀。

现在，检查与作者封禁状态相关的趋势。

使用 `groupby()` 计算每种声明状态和作者封禁状态组合的视频数量。


```python
# 使用 groupby 计算每种声明状态和作者封禁状态组合的视频数量
grouped_data = data.groupby(['claim_status', 'author_ban_status']).size().reset_index(name='video_count')

# 打印结果
print(grouped_data)
```

      claim_status author_ban_status  video_count
    0        claim            active         6566
    1        claim            banned         1439
    2        claim      under review         1603
    3      opinion            active         8817
    4      opinion            banned          196
    5      opinion      under review          463


**问题：** 你注意到被封禁作者的“声明”视频数量有什么特点吗？为什么会出现这种关系？

- 发布“声明”的作者被封禁次数为1603次。发布“观点”的作者被封禁次数为196次.

- 发布“声明”的作者更有机会被封禁，因为声明更可能出现违反平台规则导致被封禁的内容。

继续调查互动水平，现在重点关注 `author_ban_status`。

计算每个作者封禁状态的视频分享次数中位数。


```python
# 计算每个 author_ban_status 的视频分享次数中位数
median_shares_by_ban_status = data.groupby('author_ban_status')['video_share_count'].median().reset_index()
```


```python
# 打印结果
print(median_shares_by_ban_status)
```

      author_ban_status  video_share_count
    0            active              437.0
    1            banned            14468.0
    2      under review             9444.0


**问题：** 你注意到被封禁作者的分享次数与活跃作者的分享次数相比有什么特点吗？进一步探索这一点。

- 作者发布的封禁内容被转发的次数是14468次。而未封禁视频的转发次数只为437次。
- 作者发布的不当言论可能已经经过大量的转发，造成群体的不适和其他的不良影响。这种账户有更大机会被封禁。

使用 `groupby()` 按 `author_ban_status` 对数据进行分组，然后使用 `agg()` 获取以下各列的计数、均值和中位数：
* `video_view_count`（视频观看次数）
* `video_like_count`（视频点赞次数）
* `video_share_count`（视频分享次数）

记住，`agg()` 函数的参数是一个字典，其键是列名，每列的值是要执行的计算列表。


```python
# 按 author_ban_status 分组，并计算各列的计数、均值和中位数
engagement_stats = data.groupby('author_ban_status').agg({
    'video_view_count': ['count', lambda x: round(x.mean(), 2), lambda x: round(x.median(), 2)],
    'video_like_count': ['count', lambda x: round(x.mean(), 2), lambda x: round(x.median(), 2)],
    'video_share_count': ['count', lambda x: round(x.mean(), 2), lambda x: round(x.median(), 2)]
}).reset_index()

# 重命名列名，使其更清晰
engagement_stats.columns = [
    'author_ban_status',
    'view_count', 'view_mean', 'view_median',
    'like_count', 'like_mean', 'like_median',
    'share_count', 'share_mean', 'share_median'
]

# 打印结果
print(engagement_stats.to_string(index=False, float_format='%.2f'))

# 设置图表风格
plt.style.use('ggplot')

# 1. 创建计数图表（视频数量）
plt.figure(figsize=(10, 6))
bars = plt.bar(engagement_stats['author_ban_status'], engagement_stats['view_count'], 
               color=['#1f77b4', '#ff7f0e', '#2ca02c'])
plt.title('Video Count by Author Ban Status', fontsize=14)
plt.xlabel('Author Ban Status', fontsize=12)
plt.ylabel('Number of Videos', fontsize=12)

# 添加数值标签
for bar in bars:
    height = bar.get_height()
    plt.text(bar.get_x() + bar.get_width()/2., height,
             f'{int(height)}',
             ha='center', va='bottom')

plt.tight_layout()
plt.show()

# 2. 创建均值比较图表
metrics = ['view_mean', 'like_mean', 'share_mean']
labels = ['Views', 'Likes', 'Shares']
ban_statuses = engagement_stats['author_ban_status']

x = np.arange(len(ban_statuses))  # 分组位置
width = 0.25  # 柱状图宽度

plt.figure(figsize=(12, 6))
for i, metric in enumerate(metrics):
    plt.bar(x + i*width, engagement_stats[metric], width, label=labels[i])

plt.title('Average Engagement Metrics by Author Ban Status', fontsize=14)
plt.xlabel('Author Ban Status', fontsize=12)
plt.ylabel('Average Count', fontsize=12)
plt.xticks(x + width, ban_statuses)
plt.legend()
plt.tight_layout()
plt.show()

# 3. 创建中位数比较图表
metrics = ['view_median', 'like_median', 'share_median']

plt.figure(figsize=(12, 6))
for i, metric in enumerate(metrics):
    plt.bar(x + i*width, engagement_stats[metric], width, label=labels[i])

plt.title('Median Engagement Metrics by Author Ban Status', fontsize=14)
plt.xlabel('Author Ban Status', fontsize=12)
plt.ylabel('Median Count', fontsize=12)
plt.xticks(x + width, ban_statuses)
plt.legend()
plt.tight_layout()
plt.show()

# 4. 为每个ban status创建单独的图表
for status in engagement_stats['author_ban_status']:
    stats = engagement_stats[engagement_stats['author_ban_status'] == status].iloc[0]
    
    plt.figure(figsize=(8, 5))
    metrics = ['view_mean', 'like_mean', 'share_mean']
    values = [stats[metric] for metric in metrics]
    
    plt.bar(labels, values, color=['#1f77b4', '#ff7f0e', '#2ca02c'])
    plt.title(f'Average Engagement Metrics ({status})', fontsize=14)
    plt.ylabel('Average Count', fontsize=12)
    
    # 添加数值标签
    for i, v in enumerate(values):
        plt.text(i, v + max(values)*0.05, f"{v:.2f}", ha='center')
    
    plt.tight_layout()
    plt.show()
```

    author_ban_status  view_count  view_mean  view_median  like_count  like_mean  like_median  share_count  share_mean  share_median
               active       15383  215927.04      8616.00       15383   71036.53      2222.00        15383    14111.47        437.00
               banned        1635  445845.44    448201.00        1635  153017.24    105573.00         1635    29998.94      14468.00
         under review        2066  392204.84    365245.50        2066  128718.05     71204.50         2066    25774.70       9444.00



![png](output_29_1.png)



![png](output_29_2.png)



![png](output_29_3.png)



![png](output_29_4.png)



![png](output_29_5.png)



![png](output_29_6.png)


**问题：** 你注意到被封禁作者的观看次数、点赞次数和分享次数与活跃作者相比有什么特点吗？

- 被封禁作者的视频平均被观看的次数是215927.04次，未被封禁作者的视频平均被观看次数是215927.04次。被封禁作者的视频被观看的次数很多，形成大量点赞和转发。活跃作者视频被观看次数比较少，被观看的平均次数只占被封禁作者视频48%左右，被点赞的平均次数只占被封禁作者视频46%左右，被分享的次数的平均次数只占被封禁作者视频47%左右。

现在，创建三个新列以帮助更好地理解互动率：
* `likes_per_view`：表示每个视频的点赞次数除以观看次数
* `comments_per_view`：表示每个视频的评论次数除以观看次数
* `shares_per_view`：表示每个视频的分享次数除以观看次数


```python
# 创建新列 likes_per_view
data['likes_per_view'] = data['video_like_count'] / data['video_view_count']

# 创建新列 comments_per_view
data['comments_per_view'] = data['video_comment_count'] / data['video_view_count']

# 创建新列 shares_per_view
data['shares_per_view'] = data['video_share_count'] / data['video_view_count']

# 打印前几行数据以检查新列
print(data[['video_view_count', 'video_like_count', 'video_comment_count', 'video_share_count', 
            'likes_per_view', 'comments_per_view', 'shares_per_view']].head())
```

       video_view_count  video_like_count  video_comment_count  video_share_count  \
    0          343296.0           19425.0                  0.0              241.0   
    1          140877.0           77355.0                684.0            19034.0   
    2          902185.0           97690.0                329.0             2858.0   
    3          437506.0          239954.0                584.0            34812.0   
    4           56167.0           34987.0                152.0             4110.0   
    
       likes_per_view  comments_per_view  shares_per_view  
    0        0.056584           0.000000         0.000702  
    1        0.549096           0.004855         0.135111  
    2        0.108282           0.000365         0.003168  
    3        0.548459           0.001335         0.079569  
    4        0.622910           0.002706         0.073175  


使用 `groupby()` 按声明状态（`claim_status`）和作者封禁状态（`author_ban_status`）的组合对数据进行分组，然后使用 `agg()` 计算每组中以下三个新列的计数、均值和中位数：
* `likes_per_view`（点赞率）
* `comments_per_view`（评论率）
* `shares_per_view`（分享率）


```python
# 按 claim_status 和 author_ban_status 分组，并计算新列的计数、均值和中位数
engagement_rates = data.groupby(['claim_status', 'author_ban_status']).agg({
    'likes_per_view': ['count', 'mean', 'median'],
    'comments_per_view': ['count', 'mean', 'median'],
    'shares_per_view': ['count', 'mean', 'median']
}).reset_index()

# 打印结果
print(engagement_rates)
```

      claim_status author_ban_status likes_per_view                      \
                                              count      mean    median   
    0        claim            active           6566  0.329542  0.326538   
    1        claim            banned           1439  0.345071  0.358909   
    2        claim      under review           1603  0.327997  0.320867   
    3      opinion            active           8817  0.219744  0.218330   
    4      opinion            banned            196  0.206868  0.198483   
    5      opinion      under review            463  0.226394  0.228051   
    
      comments_per_view                     shares_per_view                      
                  count      mean    median           count      mean    median  
    0              6566  0.001393  0.000776            6566  0.065456  0.049279  
    1              1439  0.001377  0.000746            1439  0.067893  0.051606  
    2              1603  0.001367  0.000789            1603  0.065733  0.049967  
    3              8817  0.000517  0.000252            8817  0.043729  0.032405  
    4               196  0.000434  0.000193             196  0.040531  0.030728  
    5               463  0.000536  0.000293             463  0.044472  0.035027  


**问题：**

- “声明”视频（claim videos）和“观点”视频（opinion videos）的数据有何异同？从观看次数、评论次数、点赞次数和分享次数等方面进行分析。

- “声明”视频和“观点”视频发布的数量接近，但是“声明”视频被观看次数要比“观点”视频多100倍左右。“声明”视频被点赞的机会和“观点”视频相比高出约10%。“声明”视频被评论的机会要比“观点”视频高出50%。“声明”视频被转发的机会要比“观点”视频高出20%。

## **EXCUTIVE: 执行**

### **根据分析，能为 TikTok 数据团队总结什么？**

*   数据中有多少百分比是声明（claims），多少百分比是观点（opinions）？
*   哪些因素与视频的声明状态相关？
*   哪些因素与视频的互动水平相关？


```python
# 统计 claim_status 列中 claim 和 opinion 的出现次数
claim_opinion_counts = data['claim_status'].value_counts()

# 计算百分比
claim_percentage = (claim_opinion_counts['claim'] / len(data)) * 100
opinion_percentage = (claim_opinion_counts['opinion'] / len(data)) * 100

# 打印结果
print(f"声明（claims）的百分比: {claim_percentage:.2f}%")
print(f"观点（opinions）的百分比: {opinion_percentage:.2f}%")

# 创建饼图
plt.figure(figsize=(8, 6))
colors = ['#ff7f0e', '#1f77b4']  # 橙色和蓝色
labels = [f'Claims ({claim_percentage:.1f}%)', 
          f'Opinions ({opinion_percentage:.1f}%)']

plt.pie(claim_opinion_counts, 
        labels=labels,
        colors=colors,
        autopct='%1.1f%%',
        startangle=90,
        wedgeprops={'edgecolor': 'white', 'linewidth': 1},
        textprops={'fontsize': 12})

# 添加标题
plt.title('Distribution of Claim vs. Opinion Videos', 
          fontsize=14, pad=20)

# 显示为圆形
plt.axis('equal')

# 添加图例
plt.legend(title="Video Type:",
           loc="upper right",
           labels=[f'Claims - {claim_opinion_counts["claim"]} videos',
                   f'Opinions - {claim_opinion_counts["opinion"]} videos'])

plt.tight_layout()
plt.show()
```

    声明（claims）的百分比: 49.57%
    观点（opinions）的百分比: 48.89%



![png](output_37_1.png)



```python
# 统计 claim 被 banned 的次数
claim_banned_count = data[(data['claim_status'] == 'claim') & (data['author_ban_status'] == 'banned')].shape[0]

# 统计 opinion 被 banned 的次数
opinion_banned_count = data[(data['claim_status'] == 'opinion') & (data['author_ban_status'] == 'banned')].shape[0]

# 计算百分比
total_videos = len(data)
claim_banned_percentage = (claim_banned_count / total_videos) * 100
opinion_banned_percentage = (opinion_banned_count / total_videos) * 100

# 打印结果
print(f"claim 被 banned 的次数占视频总数的百分比: {claim_banned_percentage:.2f}%")
print(f"opinion 被 banned 的次数占视频总数的百分比: {opinion_banned_percentage:.2f}%")

# 创建条形图
plt.figure(figsize=(8, 6))
categories = ['Claims', 'Opinions']
percentages = [claim_banned_percentage, opinion_banned_percentage]
colors = ['#ff7f0e', '#1f77b4']  # 橙色和蓝色

bars = plt.bar(categories, percentages, color=colors, width=0.6)

# 添加标题和标签
plt.title('Percentage of Banned Videos by Claim Status', fontsize=14, pad=20)
plt.xlabel('Video Type', fontsize=12)
plt.ylabel('Percentage of Total Videos (%)', fontsize=12)
plt.ylim(0, max(percentages) * 1.2)  # 自动调整y轴上限

# 在每个条形上添加数值标签
for bar in bars:
    height = bar.get_height()
    plt.text(bar.get_x() + bar.get_width()/2., height,
             f'{height:.2f}%',
             ha='center', va='bottom',
             fontsize=12)

# 添加网格线
plt.grid(axis='y', linestyle='--', alpha=0.7)

# 显示绝对数量文本
plt.text(0.5, max(percentages) * 1.1, 
         f'Total Videos: {total_videos}\nBanned Claims: {claim_banned_count}\nBanned Opinions: {opinion_banned_count}',
         ha='center', va='center',
         bbox=dict(facecolor='white', alpha=0.8))

plt.tight_layout()
plt.show()
```

    claim 被 banned 的次数占视频总数的百分比: 7.42%
    opinion 被 banned 的次数占视频总数的百分比: 1.01%



![png](output_38_1.png)


- “声明”出现次数占总数的百分比: 49.57%
- “观点”出现次数占总数的百分比: 48.89%
- “声明”被封禁的次数占视频总数的百分比: 7.42%
- “观点”被封禁的次数占视频总数的百分比: 1.01%

- 我们可以观察得到，视频声明和观点的占比大约是差不多，但是声明的视频更容易得到观众的点赞评论转发。同时声明被封禁的用户占了视频总数的7.42%，而观点被封禁的用户占了总视频的1.01%。结论是发表声明的用户被封禁的概率要比发表评论的用户高出6.41%。

- 从点赞量、评论率、分享率这三个与视频的互动水平相关的参数来看，发表声明要比发表评论的用户更受青睐。

- 最终结论：当在Tik Tok发布推广、广告等内容的时候。发表“声明”要比发表“观点”更受欢迎，获取更多的流量。但是注意自己“声明”的内容不要触犯平台的规则，发布前应进行平台合规性的审查，避免官方账号被封禁。
