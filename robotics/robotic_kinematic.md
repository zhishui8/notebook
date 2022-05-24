





# 运动学



## 1 旋转运动学



![](.\figure\4a0cbd2a056f2244a040f0ccc6d8dc0.png)



### 1.1 绕全局直角坐标系旋转

**局部坐标系**$O_{xyz}$                **全局坐标系**$G_{xyz}$ 

如果刚体B绕全局坐标系的Z 轴旋转α 角，在局部坐标系和全局坐标系中刚体上任何点P 的坐标通过下面方程相互联系为
$$
^{G}r = Q_{Z,\alpha}{^{B}r}
$$
![image-20220323210059991](../../../AppData/Roaming/Typora/typora-user-images/image-20220323210059991.png)



类似的还有
$$
^{G}r = Q_{Y,\beta}{^{B}r}
\\
^{G}r = Q_{Z,\gamma}{^{B}r}
$$

**证明**

![image-20220323212010908](../../../AppData/Roaming/Typora/typora-user-images/image-20220323212010908.png)









## $\textcolor{red}{思考}$

某点在局部坐标系下的可用$xyz$ 数值 表示 单位矢量为$ijk$  那么该点在全局坐标系下的表示可以由$XYZ$ 数值表示 单位矢量为$IJK$

$X$ 的具体数值 可以看作是局部坐标系下三个轴分量$xyz$ 分别在全局坐标系$X$ 轴下的投影之和

**按照矩阵的思想** 就是同一矢量在不同基坐标下的表达

需要将原始基的三个轴分别投影至新基的某个轴 上 再与原始基的相应坐标相乘得到新基下该轴的坐标值





## 1.2 绕全局坐标系连续旋转

矩阵相乘不能交换顺序，注意旋转顺序。**且旋转矩阵是正交的**  即 **$Q^T = Q^-1$** 



## 1.3 全局翻滚角、俯仰角、偏航角度

绕**全局坐标系X 轴**的旋转被称为**翻滚（roll）**，绕**全局坐标系Y 轴**的旋转被称为**俯仰（pitch）**，绕**全局坐标系Z 轴**的旋转被称为**偏航（yaw）**。全局翻滚-俯仰-偏航矩阵

$^{G}Q{_B} = Q_{Z, \gamma} Q_{Y, \beta} Q_{X, \alpha}$ 

![image-20220323233626227](../../../AppData/Roaming/Typora/typora-user-images/image-20220323233626227.png)



### **$\textcolor{red}{思考}$**

上述旋转矩阵是固定的**先X，接着Y，最后Z旋转**的顺序进行，且上述矩阵都是按照**全局坐标系**进行

若给定上述旋转矩阵则

**翻滚角 $\alpha = arctan(\frac{r_{32}}{r_{33}})$**  **俯仰角 $\beta = - arcsin(r_{31})$**  **偏航角 $\gamma = arctan(\frac{r_{21}}{r_{11}})$**

所以思路一般是求出他的旋转变化矩阵在去求他的各个变化角度

如果是 IMU  则应该先解算姿态，再根据旋转变化矩阵求出 他的 各个角度



## 1.4 绕局部直角坐标轴旋转

局部坐标系的相乘顺序相反

先旋转

$\textcolor{red}{根据这本书，貌似绕全局和局部坐标轴旋转并没有太大差异}$

不不 ，还是有较大差异的

若是绕着局部直角坐标系进行旋转时，其旋转矩阵是绕全局坐标系的逆

以绕z轴旋转为例 局部坐标系 $A_{Z,\alpha}$  全局坐标系 $Q_{Z,\alpha}$ 二者互为转置且 相乘为 $I$ 1.5



## 1.5 绕局部坐标系连续旋转



## 1.6 欧拉角

欧拉角意味着绕着局部坐标系进行旋转





### 插入林沛群运动学相关描述

#### 1. 旋转矩阵的作用

**$^{A}_{B}R$ 描述B相对于A的姿态**

![](../../../AppData/Roaming/Typora/typora-user-images/image-20220324165811273.png)

![image-20220324165918839](../../../AppData/Roaming/Typora/typora-user-images/image-20220324165918839.png)

![image-20220324170038777](../../../AppData/Roaming/Typora/typora-user-images/image-20220324170038777.png)

​							**每一列相当于从B坐标系的某个轴在A坐标系下每个轴的投影 **

​							**每一行相当于B坐标系的三个轴对A坐标系下某个轴的投影** 

**eg** 

![image-20220324170711908](../../../AppData/Roaming/Typora/typora-user-images/image-20220324170711908.png)  新的坐标系的每个轴在旧的坐标轴三个轴上的投影



****





$^{A}_{B}R = ^{B}_{A}R^T$



#### Rotation Matrix 除了描述${B}$ 相当于${A}$的姿态，也可以用来表示转化向量在不同坐标下的表示



![image-20220324171743214](../../../AppData/Roaming/Typora/typora-user-images/image-20220324171743214.png)

### 描述物体转动的状态

即若物体随着局部坐标系一起旋转，刚体上的向量旋转后在全局坐标系下的表示可以转化为局部向量在全局下的坐标问题

描述向量绕着某一个轴进行旋转，可以理解成该向量与参考坐标系固连，向量绕着某个轴旋转即是参考坐标系的旋转



### 总结（旋转矩阵的三种用法）

+ **描述参考坐标系相较于另外一个坐标系的姿态**

+ **将空间中的一点由某一个坐标系的表达转化到另一个与此坐标系仅有相对转动的坐标系下的表达**

+ **描述向量在同一个坐标系下转动后的坐标**

  ![image-20220324213759636](../../../AppData/Roaming/Typora/typora-user-images/image-20220324213759636.png)

  #### 2.矩阵的旋转

  ##### 2.1固定轴的旋转

  先绕着X轴旋转γ，接着Y轴旋转β，最后Z轴α

  $^{A}_{B}R_{xyz}{(\gamma,\beta,\alpha)}*v$  = $R_z{(\alpha)} R_y{(\beta)} R_x{(\gamma)}*v$ 

  **思考** 以操作的考虑进行，向量$v$ 首先与参考坐标系下固连， 参考坐标系绕着X 轴进行旋转带动向量一起旋转， 那么此时$R_x{\gamma}*v$ 即是参考向量在绕着固定坐标系X轴后旋转后在固定坐标系下的表达  $\rightarrow$  同理再绕着固定坐标系Y轴进行 旋转得到上述向量在固定坐标系下的表达 $\rightarrow$ 最后绕着Z轴旋转 

  所以上述公式可以满足直接相乘，因为从右往左乘的过程中，都是该向量在全局坐标系下的表达，接着 在以全局坐标系的轴进行旋转

  旋转轴的顺序对于旋转矩阵有着影响，**所以需要注意旋转的顺序**  

+ 根据旋转矩阵反推转动的角度

  ![image-20220324221704988](../../../AppData/Roaming/Typora/typora-user-images/image-20220324221704988.png)

  ##### 2.2 绕 局部坐标系进行旋转

  先Z轴旋转$\alpha$ , 在Y轴旋转$\beta$ , 在X轴旋转$\gamma$ 

  $^{A}_{B}R_{z^{'}y{'}x{'}}{(\gamma,\beta,\alpha)}*v$  =  $R_{z^{'}}{(\alpha)} R_{y^{'}}{(\beta)} R_{x{'}}{(\gamma)}*v$ 

​	  **思考** 其思路将翻转后的向量逐步回倒，返回到第一个固定坐标系下的感觉

向量表达是该向量在最后旋转坐标系下的表达，其过程类似于 **追溯** ；$ R_{x{'}}{(\gamma)}*v$ 首先 $ R_{x{'}}{(\gamma)}$ 是第二坐标系绕着X轴旋转后的坐标轴表达， *$v$ 意味着 原本在第三坐标系下表达的向量 转化为 第二坐标系 下表达 ； 以此类推得到旋转后的向量在固定坐标系下的表达。**典型特征** 向量在每个坐标系下的表达不变 

最后也是得到按照局部坐标系旋转后，该坐标在全局下的表达

+ 根据旋转矩阵反推旋转角度

  下述只是zyz旋转方法，同一向量可以由不同旋转方式得到，只要最后得到下面旋转矩阵可以通过ZYZ旋转得到

  ![image-20220324230847163](../../../AppData/Roaming/Typora/typora-user-images/image-20220324230847163.png) 

#####   $$\textcolor{red}{绕着固定轴旋转，先旋转的与向量最近，其逻辑是每次相乘都是重新转化为全局坐标系下，所以是绕着固定轴进行旋转；}$$ 

**$$\textcolor{red}{绕着局部旋转，后旋转的与向量最近，其逻辑是每次相乘都是重新转化为上一个坐标系下的表达，所以是绕着上一个坐标系进行旋转；}$$**



## 2 刚体状态的整体表达

#### 2.1即将旋转矩阵与空间位置结合 构建**齐次变换矩阵（homogeneous transformation matrix）**

上图均是**B相对A**的**转动**以及相对于A的**空间位置**

![image-20220325111746185](../../../AppData/Roaming/Typora/typora-user-images/image-20220325111746185.png)

**理解成 两个坐标系首先是固连在一起的，参考坐标系B带着P点旋转，旋转后的P点在固连坐标系的表达 $^{A}_{B}R*^{B}P$** **,随后P点和参考坐标系B相对A进行平移 所以 加上 $^{A}P_{B Org}$** **（即B原点相较于A的平移位置）**

**映射(mapping)**: 即同一向量在不同坐标系下的表达 

除了mapping 之外也可以看作是operator,operator需要注意就是**先转动后移动**与**先移动后转动**并不相同

#### 2.2连续运算

![image-20220325120947148](../../../AppData/Roaming/Typora/typora-user-images/image-20220325120947148.png) 

$^{C}P$ 在坐标系A下的表达其本质还是向量相加，向量的数值表达加减只有在同一基坐标系下才有效

$^{A}_{B}R*^{B}_{C}R*^CP$ 即是向量$^{C}P$ 在无平移的情况下在A坐标系下的表达 + C原点在A坐标系下的表达即 



**$^{A}_{B}T * ^{B}_{A}T =^{A}_{B}T * ^{A}_{B}T^{-1} = I$ **   

齐次变化矩阵同样可以由operator 和 mapping 来理解

operator 意味着 绕固定坐标系旋转 先旋转的放后面 这样才能满足绕固定坐标系旋转顺序的要求

mapping 意味着绕局部坐标系旋转 先旋转的放前面  这样往左乘时顺序才对



## 3 机械手臂 的正向动力学

**kinematic** **只考虑运动本身暂时不考虑力**

+ **编号方式** Link_0，不动的杆件通常是与地面连接; Link_1和link_0连接是第一个可以动的杆件

+ 每两杆之间可以用$\alpha，a$ 来定义之间关系 其中$a$ 是两杆之间的长度 $\alpha$ 为两杆之间的扭转角度

+ 多杆串联 需要$d_i,\theta_i$ 描述$a_i,a_{i-1}$ 之间的相对关系 

  <img src="../../../AppData/Roaming/Typora/typora-user-images/image-20220325143115596.png" alt="image-20220325143115596" style="zoom:50%;" />  

+ 分析第一个杆件和最后一个杆件的特殊处理方式

  + **link_0**   **与 参考坐标系 1 重合**  $\alpha _0 = 0 , a_0 = 0$ 即一般 $z_0与z_1$ 两个轴重合，这样的话 没有相对扭转 故 $\alpha_0$ = 0,公法线也没有相对距离所以$a_0$ =0
    + 如果是旋转幅，则 $\theta_1$ 就是link_1相对于link_0绕$z_0$ 轴的旋转角度，$d_1$ =0因为 $x_0 与 x_1$ 轴之间的公法线之间的距离为0 
    + 如果是平移副，则 $\theta_1 = 0$，因为link_1相对于link_0绕$z_0$ 轴没有旋转，$d_1$ 就是link_1相较于Link_0之间平移的距离
  + **link_n** **取和$x_{n-1}$同方向**   $\alpha _0 = 0 , a_0 = L $ 即一般 $z_0与z_1$ 两个轴方向相同，这样的话 没有相对扭转 故 $\alpha_0$ = 0,公法线即z轴相对距离为**L**， 即Link_n-1的长度
    + 如果是旋转副， 则$\theta_n$ 就是 link_n与link_n-1之间的绕$z_{n-1}$的旋转角度 , $d_n$ = 0，因为$x_{n-1}与x_n$ 同方向
    + 如果是平移副，则 $\theta_1 = 0$，因为link_1相对于link_0绕$z_0$ 轴没有旋转，$d_1$ 就是link_1相较于Link_0之间平移的距离

+ $\alpha_{n-1},a_{n-1},\theta_{n},d_n$的具体含义

  + $\alpha_{n-1}$ : $z_{n-1} 与 z_n$ 之间的相对扭转，沿着$x_{n-1}$ 观察$z_{n-1} 与 z_n$ 之间的相对夹角(**PS :大拇指指向X轴正方向 ，四指弯曲即正方向*，均是上一个坐标系的轴相较于此时大拇指这个轴的旋转方向。所有的方向都是上一个坐标系到这一个坐标系)

  + $a_{n-1}$ : $z_{n-1} 与 z_n$ 之间的相对距离，沿着$x_{n-1}$ 观察$z_{n-1} 与 z_n$ 之间的相对距离

  + $\theta_n$ :   $x_{n-1} 与 x_n$ 之间的相对扭转，沿着$z_{n}$ 观察$x_{n-1} 与 x_n$ 之间的相对夹角

  + $d_n$：$x_{n-1} 与 x_n$ 之间的相对距离，沿着$z_{n}$ 观察$x_{n-1} 与 x_n$ 之间的相对距离

    **mapping 以第n个坐标系表达， 逐步回溯到以第n-1个坐标系下表达**

<img src="../../../AppData/Roaming/Typora/typora-user-images/image-20220325154039149.png" alt="image-20220325154039149" style="zoom:50%;" />



**eg**

<img src="../../../AppData/Roaming/Typora/typora-user-images/image-20220325154409684.png" alt="image-20220325154409684" style="zoom:50%;" />   

|      | $\alpha_{n-1}$ | $a_{n-1}$ | $\theta_n$ | $d_n$ |
| ---- | -------------- | --------- | ---------- | ----- |
| L_1  | 0              | 0         | $\theta_1$ | 0     |
| L_2  | 0              | L1        | $\theta_2$ | 0     |
| L_3  | 0              | L2        | $\theta_3$ | 0     |

<img src="../../../AppData/Roaming/Typora/typora-user-images/image-20220325155609702.png" alt="image-20220325155609702" style="zoom:50%;" /> 

|      | $\alpha_{n-1}$ | $a_{n-1}$ | $\theta_n$ | $d_n$ |
| ---- | -------------- | --------- | ---------- | ----- |
| L_1  | 0              | 0         | $\theta_1$ | 0     |
| L_2  | 0              | a2        | 0          | d     |
| L_3  | 0              | 0         | $\theta_3$ | L2    |

revolute joint **坐标系在转子上** 



## 4 执行器，关节，笛卡尔坐标系

joint space $\rightarrow$ Cartesian space 正向运动学 ，反之则是逆向动力学
