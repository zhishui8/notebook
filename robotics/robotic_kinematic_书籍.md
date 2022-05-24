



# Robotic kinematic

## 1. 刚体位置与指向的确定

刚体姿态描述： **位置** 与 **姿态** 

### 1.1 刚体位置的确定

<img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746169.png" alt="image-20220329115150555" style="zoom:50%;" />  			刚体的位置可用刚体坐标系原点的矢径来刻画

Q 在参考系$OXYZ$ 中的矢径 为$p+r$ 



### 1.2 刚体指向的确定

刚体的指向可由刚体坐标系与参考坐标系之间的相对位置来刻画

方法：记刚体坐标系$O_1\xi\eta\zeta$ 坐标轴上的三个单位矢量 **n,o,a** 在参考坐标系$OXYZ$（简称系0）中的坐标表达式

![image-20220329122155545](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746171.png) 

则可以用3×3矩阵进行表达

![image-20220329122226586](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746172.png) 

来表示**刚体**相对于**参考坐标系**的指向

对于旋转矩阵$^{0}R_1$几点注意：

+ 若记$X,Y,Z$ 轴上的单位矢量为$x,y,z$ 则

![image-20220329122710837](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746173.png)

故矩阵 $^{0}R_1$ 又称为系1(即坐标系$O_1\xi\eta\zeta$) 相较于系0($OXYZ$) 的方向余弦矩阵

+ 9个元素 但是只有三个自由度，存在六个约束方程

  即：$||n|| = ||o|| = ||a||=1$                 **n×o=a**  

+ **向量b ** 在系1 和系0之间的关系是 **$^{0}b=^{0}R_1{^{1}b}$**   

证明如下

![image-20220329123642138](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746174.png) 

![image-20220329123716625](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746175.png) 

![image-20220329123728675](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746176.png) 

+ $^{0}R_1$ 是正交矩阵，即有$(^{0}R_1)^{-1}$ = $(^{0}R_1)^{T}$ , 亦即 $^{0}R_1 = (^{1}R_0)^T$

### 1.3 旋转变换

#### 1.3.1 欧拉公式

新的坐标系1，可以看作是坐标系0绕着过系0原点的一轴转动一个角度后得到的。其表示方法如下

![image-20220329124714844](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746177.png)  

其中单位矢量$k$在系0中的表达为$^{0}k=[k_x,k_y,k_Z]^T$ ,$\theta$ 是旋转角度 ，$S(^0k)$ 定义如下，其称之为$^{0}k$所对应的叉乘矩阵$S(^0k)^0b=^0k×^0b$ 

![image-20220329124936600](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746178.png)

#### 1.3.2 旋转矩阵

$^0R_1$ 除了称之为**系1(即坐标系$O_1\xi\eta\zeta$) 相较于系0($OXYZ$) 的方向余弦矩阵**； 也可看做是**系0到系1的旋转矩阵** 

引申出一个常见问题，矢量b 在系0中绕着某一轴进行旋转，得到的b\' 在系0 的表达

**理解思路** ：建立坐标系1与矢量b固连，且初始时与系0重合，并随着b相同转动。当转动完成时从系0到系1的转动可用旋转矩阵$^0R_1$进行表示。进而表示如下。这个公式也同时说明了它是矢量旋转前后的坐标表达式间的变化矩阵

![image-20220329130214737](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746179.png)

#### 1.3.3 基本旋转矩阵

绕坐标轴转动称之为基本转动

![image-20220329130753675](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746180.png)

#### 1.3.4 连续相对转动的合成

即每次转动都是相对前一坐标系，记$^0R_1$ 为系0 到系1的旋转矩阵，$^1R_2$ 为系1到系2的旋转矩阵

![image-20220329131100558](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746181.png) 

**结论** ：连续相对转动的旋转矩阵可以按照相对转动的次序**连续右乘**各次转动的旋转矩阵来得到（类似于机械臂）

#### 1.3.5 欧拉角

任何一个指定指向均可由三个连续的绕坐标轴旋的相对转动得到，即任何一个方向余弦矩阵等于三个基本旋转矩阵的乘积，这三个基本旋转矩阵称之为欧拉角

![image-20220329141520094](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746182.png)



![image-20220329141540012](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746183.png)

三次转动的轴的选取和顺序至关重要

#### 1.3.6齐次变化矩阵

（1）点在不同坐标系下的坐标变化

![image-20220329142132227](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746184.png) 

![image-20220329142154918](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746185.png)



（2） 齐次变化矩阵

<img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746186.png" alt="image-20220329142318334" style="zoom:67%;" />

记点Q在系0，系1和系2中的坐标分别为$^0r,^1r和^2r$ ,则由

$^0r = ^{0}p+^0R_1{^1r}$             $^1r = ^{1}p_2+^1R_2{^2r}$  

知

$^0r = ^{0}p+^0R_1({^{1}p_2+^1R_2{^2r}}) =^{0}p +^0R_1{^{1}p_2}+^0R_1{^1R_2{^2r}} $                                       **(1-5)**

<img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746187.png" alt="image-20220329143010407" style="zoom:67%;" />

简记为 **$^0r=^0A_1{^1R}$**             $^0A_1$  4×4矩阵即为从系0到系1的齐次变化矩阵

几点说明

+ 齐次坐标定义:若以空间中的一已知点O作为参考点，则任一点Q可由下式表达

  $\alpha r = a_0 \                    \              r= OQ^{\rightarrow} = \frac{1}{\alpha} a_0$   

  其中 $\alpha$ 为为距离，a0为方向

  数学中的齐次意味着任何一个非零常数乘此向量，坐标表示的实体不变

+ 齐次坐标变换矩阵$^0A_1$ 由方向余弦矩阵$^0R_1$和$^0p$ 共同组成，包括坐标间的相对指向和位置信息

+ 齐次变换矩阵的意义

  + $^0A_1$ 表示了系1相对系0的位置指向
  + $^0A_1$ 把点在系1中的齐次坐标变为系0中的齐次坐标变化矩阵
  + $^0A_1$表示系1可以由系0经过移动和转动后得到

+ 连续相对运动的齐次变化矩阵可按照相对运动次序连续右乘得到

  <img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746188.png" alt="image-20220329145639038" style="zoom:67%;" />

+ 齐次变化矩阵的逆

  <img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746189.png" alt="image-20220329145754880" style="zoom:67%;" />



## 2 机器人杆件坐标系的建立

### 2.1机器人杆件与关节编号

基座定义为杆0，杆1，2，3，，n ,关节i连接杆i与杆i-1

### 2.2 建立杆件坐标系的DH法

#### 2.2.1 建立杆件坐标系的方法

对于n自由度机器人，可用以下步骤建立与各杆件i(i=0,1,2,.....,n)固连的坐标系$O_iX_iY_iZ_i$ 并简称为系i 坐标系个数比自由度多一 ，末端坐标系

+ 确定各坐标系Z轴，基本原则是 沿关节i+1的轴向，方向任选，一般各平行z轴同向（没有全局坐标系）
  + 若为关节i+1为移动关节，选取zi轴与zi+1轴相交
  + 机器人杆n的远端没有关节n+1，则选取zn轴与zn-1重合
+ 确定原点 选取的原点Oi在Zi-1和Zi轴的公法线上
  + 若Zi-1与zi平行 时，若重合Oi=Oi-1,若平行不重合过Oi-1做二轴的公法线，与Zi轴相交即为Oi
  + 无法确定O0, 若Z0和Z1相交时，取O0=O1
+ 确定 各坐标系的X轴，基本原则时选取的Xi轴沿Zi-1轴和Zi轴的公法线
  + 相交不重合时Xi = Zi-1×Zi
+ 确定y轴 ，右手坐标系Z

#### 2.2.2 D-H参数

+ 杆件长度$a_i$ 定义为$Z_{i-1}轴到Z_i$的距离， 沿着$X_i$的指向为正
+ 杆件长度$\alpha_i$ 定义为$X$的转动， 沿着$X_i$的X正向转动为正，且规定$-\pi<\alpha_i<\pi$  
+ 关节距离$d_i$ 定义为$X_{i-1}轴到X_i$的距离， 沿着$Z_{i-1}$的指向为正
+ 关节转角$\theta_i$ 定义为$X_{i-1}轴到X_i$的转动， 沿着$Z_{i-1}$的X正向转动为正，且规定$-\pi<\alpha_i<\pi$  

<img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746190.png" alt="image-20220329154302824" style="zoom:50%;" /> 

#### 2.2.3 用DH参数确定坐标系间的齐次变换矩阵

沿着$z_{i-1}$ 轴移动 $d_i$ ,绕着$z_{i-1}$ 转动$\theta_i$ ,沿着$x_i$轴移动$a_i$ ,绕着 $x_i$转动$\alpha_i$ 

![image-20220329155359249](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746191.png)





### 2.3 修改的DH 参数建立驱动轴坐标系

主要克服树形结构或者含有闭链的机器人，会造成杆件多一个传动轴，使用传动DH会造成歧义

**一般传统就够使用了**

**齐次变化矩阵和其逆变化矩阵本质上都只是变量$q_i的函数$ ** 





## 3 运动学问题

### 3.1 相关定义

运动学问题就是研究关节变量$q = [q_1,...,q_n]^T$ 与其末端夹持器位置和指向之间的关系，研究$q与^0A_n$ 之间的关系

正运动学：已知q,求相应的$^0A_n$      逆运动学：已知$^0A_n$ 求q

### 3.2 正运动学解法

<img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746192.png" alt="image-20220329162135639" style="zoom:67%;" />

**$q_i$是关节i角度的变化,对应的是$z_{i-1}$轴的角度变化，所以是$^{i-1}A_i$  **  



### 3.3 逆运动学解法

#### 3.3.1 Stanford臂 的逆运动学问题

**eg Stanford臂 解法**

<img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746193.png" alt="image-20220329162526545" style="zoom:50%;" /><img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746194.png" alt="image-20220329162637632" style="zoom:50%;" /> 

![image-20220329162653693](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746195.png) 



**详解见书** 其思想主要将最后三轴最后考虑，首先确定位置，在|O1O3|的值 求出q3,在反带求q1与q2



#### 3.3.2 关于逆运动学的进一步研究

+ 解的存在性和唯一性问题
  + 所以当n小于6时并不是对于任意给定$^0A_n$ 都有解  **自由度不够，正常的空间位置确定 需要六个自由度**
  + 当n=6时在数学意义上是有解的（只有在工作空间），解的个数取决于事先给定的常数项$^0A_6$ 可能有限组，也有可能无限组解
  + 当n>6, 称之为冗余度的机器人
+ 存在性问题
  + 解析解能增加运算速率，数值解计算量比较大。
  + 六自由度解细解存在的充分条件，6自由度后3个关节的轴线始终交与一点，则此机器人的逆运动学必有解细节



## 4 速度问题

### 4.1预备知识

#### 4.1.1 **齐次变换矩阵**速度表示

$ ^0A_n = \left[ \matrix{  ^0R_n & p_n\\  0 & 1} \right]$

系n的速度可用$^0A_n$ 的导数表示$\dot{^0A_n}$ 表示；其中$\dot{p_n}= v_n$ ,是系n原点On的速度，是三维矢量的坐标表达式，反映了系n随其原点移动的速度，而$\dot{^0R_n}$ 是系n相对On(相对系0)的旋转速度

$\dot{ ^0A_n}= \left[\matrix{\dot{^0R_n} & \dot{p_n}\\ 0&1}\right]$ 

#### 4.1.2 **三维矢量法**

**背景** 之前学习过 还可以通过单位矢量 **k**= $[k_x,k_y,k_z]$ 和$\theta$ 表示角位置，以及 **欧拉角**$[\varphi,\theta,\psi]^T$ 表示，但是由欧拉公式等可证其并不满足矢量的交换律 即$R_l({\varphi})*R_k({\theta}) \neq R_k({\theta}) *R_l({\varphi})$ 即 $\theta k+ \varphi l\neq \varphi l+\theta k$， 即 **有限转动不能用矢量表示**

但是转动的角速度可以用矢量表示

<img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746196.png" alt="image-20220329224657357" style="zoom:50%;" /> <img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746197.png" alt="image-20220329224713045" style="zoom:50%;" />



由叉乘矩阵与三维矢量一一对应可知，此转动的时间变化率可用矢量$\dot{\theta}k$ 表示，记为$\omega$ ,其满足矢量的交换律![image-20220329225225945](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746198.png)



#### 4.1.3 **齐次变换矩阵表示法与三维矢量法之间的关系** 

$\dot{^0R_n} = \frac{d}{dt}R_k(\theta) = [\frac{\partial}{\partial\theta}R_k(\theta)]\frac{d\theta}{dt}=\dot{\theta}\frac{\partial}{\partial\theta}R_k(\theta)$ 

由欧拉公式得

$\frac{\partial}{\partial\theta}R_k(\theta) = S(k)R_k(\theta) = S(k)^nR_0$

所以

$\dot{^0R_n} = S(\dot{\theta}k)^0R_n = S(\omega){^0R_n}$

 

### 4.2 正速度问题的解法

#### 4.2.1 齐次变换矩阵表示正速度的关系：

​	问题**已知$q和\dot q$,求解$\dot{^0A_n}$** 



**递推公式及框图**

 由 $^0A_n =^0A_n(q_1,q_2,....,q_n) $ 知

$\dot{^ 0A_n} =\sum_{i=1}^{n}{[\frac{\partial}{\partial q_i}^0A_n]\dot q_i} $   **齐次变化矩阵是关于q的函数，所以需要先进行偏导**

又由$^0A_n = ^0A_1(q_1)^1A_2(q_2)....^{n-1}A_n(q_n)$ 

得到$\frac{\partial}{\partial q_i}^0A_n = ^0A_{i-1}[\frac{d}{dq_i}^{i-1}A_i]^iA_n$ **因为只有$^{i-1}A_i$与$q_i$有关  **

由于转动副或者移动副的原因

$\frac{d}{dq_i}^{i-1}A_i = \hat{\sigma}\frac{d}{d\theta}^{i-1}A_i(\theta_i) + \sigma\frac{d}{d\theta}^{i-1}A_i(d_i)$

其中

<img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746199.png" alt="image-20220330110825567" style="zoom:50%;" />



所以![image-20220330110916885](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746200.png)

$\frac{d}{dq_i}^{i-1}A_i = Q_i$



代入上式得到

$\frac{d}{dq_i}^{i-1}A_i(q_i) = Q_i  {^{i-1}A_i}$

 $\frac{\partial}{\partial q_i}^0A_n = ^0A_{i-1}Q_i ^{i-1}A_n$

所以

$\dot{^ 0A_n} =\sum_{i=1}^{n}{^0A_{i-1}}{Q_i}^{i-1}A_n\dot q_i $   



**递推公式**

<img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746201.png" alt="image-20220330112142110" style="zoom:80%;" />



#### 4.2.2 用三维矢量表示正速度关系

+ 问题提法

当杆n的角速度用$\omega_n$ 表示时，已知$q,\dot q$ 求解系n的角速度$\omega _n$及其原点$O_n$ 的速度$v$

+  有两种方法可以求解

  + 通过三维矢量发与齐次变换矩阵之间的关系求解

  + 直接利用矢量力学公式求解

    <img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746202.png" alt="image-20220330114721200" style="zoom:80%;" />

    **对于任意旋转矩阵R和矢量a,均有$RS(a)R^T = S(Ra)$ ,再考虑到$Z_{i-1}$ 轴上的单位矢量$z_{i-1}$ 在系0中的坐标$z_{i-1} = ^0R_1z$**

    

    <img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746203.png" alt="image-20220330114744475" style="zoom:80%;" />

    ![image-20220330130630521](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746204.png)

    ![image-20220330130939349](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746205.png)

    ![image-20220330130955605](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746206.png)

    

**ps:三维矢量表达更为简单，其将与各杆有关的矢量用其在各自杆坐标系中的坐标表达式来表示，减少了计算量**



#### 4.2.3 机器人的雅可比矩阵

![image-20220330132448353](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746207.png)

![image-20220330132504681](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746208.png)

![image-20220330132546960](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746209.png)





![image-20220330132637755](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746210.png)

**ps**：由式1-59知，雅可比矩阵的第i列$J_i由z_{i-1},p_{i-1}和p_n$ 共同组成，而$z_{i-1}$是$^{0}A_{i-1}$中第三列的前三行，$p_{n-1} 和 p_{n}$ 分别时$^0A_{n-1} 和^0A_{n}$第四列的前三行



#### 4.2.4逆速度问题的解法

**问题的提法：**已知$q及\omega_n,v_n$,求对应的关节角速度$\dot q$

说明：逆速度问题时，一般不研究齐次变换矩阵表示的逆速度问题（已知$q及\dot{^0A_n}$,求$\dot q$） ,原因是$\dot p_n = v_n$，以及

![image-20220330140828156](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746211.png)

立即可由$\dot{^0A_n}$确定出$\omega_n,v_n$

**逆速度的解**

雅可比矩阵知：

$\left[\matrix{v_n\\\omega_n}\right] = J(q)\dot q$

其中$J\in R^{6*n}$ ,由线性方程组值逆速度问题对给定任意$w_n,v_n$,都有解的必要条件是

<img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746212.png" alt="image-20220330142024644" style="zoom:80%;" />

**这表明：对任给的$w_n$和 $v_n$，逆速度均有解的前提是机器人自由度大于 n≥6**

因为$J= J(q)$,**所以rank K** 随 **q** 变化，通常称是J(q)不满秩的q称之为奇异点，此位置机器人末端在某些方向不能移动，且逆速度求解存在较大麻烦



具体求解情况如下

+ 机器人自由度个数 **n=6**

​		这时由J满秩则J可逆，故速度问题有唯一解
$$
\dot q = J^{-1}\dot x
$$
不必直接求逆，**有相关递推公式** **p41**

+ **n>6**

  此时因为J满秩，且方程个数小于为实数个数，故有无穷多个解，但是需要的是最小范数解（即使$||q||$最小）；或者更为一般的需要加权最小范数解

  求$\dot q$ 在满足$\dot x = J\dot q$且使得$L =\frac{1}{2}\dot q^TD\dot q$ 最小。实际上是求性能指标 L在约束条件下$\dot x = J\dot q$ 的极值，可以用 Lagrang乘子法进行求解。

  

  ![image-20220330144646269](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746213.png)

   

+ **n<6**

  

  $J满秩$ 且方程组个数大于未知数个数，可能是无解的，最小误差解

  

  <img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746214.png" alt="image-20220330145754697" style="zoom:80%;" />

  ![image-20220330145811108](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746215.png)

#### 4.2.5 机器人奇异位置及特点

##### 奇异位置的特点

+ q为奇异点时，逆速度问题不存在唯一解，可能无解\无穷多解
+ 系n有限的速度对应于 无穷大的关节速度
+ 在奇异点位置时，机器人可能在某些方向不能移动，常对应于机器人工作空间的边界点

##### 解耦

![image-20220330151450667](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746216.png)

![image-20220330151509124](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746217.png)

![image-20220330151521560](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746218.png)

**例子**

![image-20220330151546420](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746219.png)

![image-20220330151600301](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746220.png)

![image-20220330151617246](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746221.png)

![image-20220330151626525](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746222.png)

## 5 加速度问题

已知机器人关节位置$q和\dot q$的前提下，研究关节加速度$\ddot q$与杆n加速度的关系

### 5.1正加速度的解法

#### 5.1.1齐次变换矩阵 

​	**已知$q,\dot q,\ddot  q$ ,求对应的$\ddot {^0A_n}$** 

![image-20220330153547485](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746223.png)

对上式进行二次求导

![image-20220330153611833](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746224.png)。

这样第四节中求出的$\dot {^0A_i}与{^0A_i}$ 的递推公式与1-67共同构成 了用齐次变化矩阵构成表示的正加速度公式





#### 5.1.2三维矢量法

​	**已知$q,\dot q,\ddot  q$ ,求对应的角加速度$\dot\omega_n和 \dot v_n$**   

<img src="https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746225.png" alt="image-20220330154219946" style="zoom:67%;" />

对1-51二次求导得

![image-20220330154728756](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746226.png)

![image-20220330154825336](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746227.png)

![image-20220330155125612](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746228.png)

![image-20220330155155594](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746229.png) 



 为啥等于0   **$z_{i-1}×p_i^*$ ** 

### 5.2逆加速度解法

#### 5.2.1问题描述

已知$q,\dot q, a_n,\epsilon_n$ ,求对应得关节加速度

#### 5.2.2逆加速度解法

![image-20220330160308814](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746230.png)

![image-20220330160319346](https://cdn.jsdelivr.net/gh/zhishui8/figure/img/202205241746231.png)

