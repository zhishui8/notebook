# 1 绪论

+ 黑箱到白箱

+ 现代控制理论：系统辨识，状态估计，控制理论

+ 80%的PID没有达到最优（缺乏系统辨识）

辨识参数 分为 **运动学参数** **动力学参数**

**运动学参数** ： 减速比 DH参数（通常其精度够用了，不需要辨识）

<img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241805378.png" alt="image-20220426103155841" style="zoom:50%;" />

动力学参数： 最小惯性参数集
$$
\tau = Y_r p_r
$$
参数辨识方法：

<img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241805379.png" alt="image-20220426103618538" style="zoom:50%;" />

# 2 系统辨识基础

## 2.1 整体流程

$\tau = Y_r p_r$ 

<img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241805380.png" alt="image-20220426104134347" style="zoom:50%;" />

最小二乘具有很强的收敛性

## 2.2 相关细节

### 2.2.1 最小二乘

<img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241805381.png" alt="image-20220426104726865" style="zoom:50%;" />

前提是高斯白噪声，才能确保是无偏估计

![image-20220426110216912](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241805382.png)

### 2.2.2 递推最小二乘，在线辨识减少运算量

<img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241805383.png" alt="image-20220426110424570" style="zoom:67%;" />

### 2.2.3 噪声影响

<img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241805384.png" alt="image-20220426111614155" style="zoom:50%;" />

速度可以通过直接差分获取，加速度需要滤波处理

控制过程中避免角加速度的反馈

### 2.2.4 滤波器

低通滤波器

<img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241805385.png" alt="image-20220426112251984" style="zoom:50%;" /> 

电路就是模拟滤波器（改起来麻烦）

离散系统实现

<img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241805386.png" alt="image-20220426112451942" style="zoom:50%;" />



Tips: 滤波会必然引入延时，导致数据串掉，没法对其位移，速度，加速度的数据

### 2.2.5 离线滤波与在线并行滤波

<img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241805387.png" alt="image-20220426112844884" style="zoom:50%;" />

两种都是好方法，一般都是采集完所有数据在进行滤波进行辨识，所以可以用filtfilt函数进行辨识，消灭延时

或者在线辨识的话需要对等式两边同时滤波，这样也可以变相消除延时影响（decimate）

#### 在线并行滤波



![image-20220426114709457](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241805388.png)

**力矩信号获取**

![image-20220426114936962](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241805389.png)



### 2.2.6 连续系统和离散系统

采样过程发生时：A/D 信号转化需要时间，信号在该时间段保持不变

<img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241805390.png" alt="image-20220426120043098" style="zoom:33%;" />

离散信号采样相较于连续信号（原始信号）会有ts/2的延迟，所以得使用奈奎斯特采样定理（2*fs）

eg: <img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241805391.png" alt="image-20220426120521530" style="zoom:50%;" />

### 2.2.7 连续系统和离散系统的系统辨识

![image-20220426120852248](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241805392.png)

Tips：离散系统不需要速度，加速度量，只是需要位置参数，通过离散化，但是要注意dt其实包含在系数里

连续系统则是需要角速度和角加速度(推荐走连续)

 

### 2.2.8 最优激励轨迹

当解集x对A和b的系数高度敏感，那么这样的方程组就是病态的

eg:<img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241805393.png" alt="image-20220426122021463" style="zoom:50%;" />.

评价指标: matlab conda

最优激励轨迹就是设计轨迹使得 $Y_r$ conda 最小

转化为优化问题，通过若干阶傅里叶级数生成轨迹，降低conda值

<img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241805394.png" alt="image-20220426122353985" style="zoom:50%;" />

<img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241805395.png" alt="image-20220426122448761" style="zoom:50%;" />

tips: 低速，避免激发关节柔性



其他理论系统辨识方法

先仿真后实践，慎重滤波，时刻提防摩擦力

# 3 实例 

单自由度连续系统辨识

![image-20220426133201531](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241805396.png)



设置激励轨迹

<img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241805397.png" alt="image-20220426133323625" style="zoom:50%;" />

噪声影响（当某项所占比越小，该值估计越不稳定）

![image-20220426133420459" style="zoom:50%;"](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241805398.png)

转速影响：会引起尖峰

8

单自由度离散系统辨识

<img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241805399.png" alt="image-20220426134008430" style="zoom:50%;" />