# 第一章 绪论

## 单量子比特

### 表示方式
$$
\ket{\psi} = \alpha \ket{0} + \beta \ket{1} = e^{\imath \gamma}(cos\frac{\theta}{2}\ket{0}+e^{\imath \phi}sin\frac{\theta}{2}\ket{1})
$$

整体相因子$e^{\imath \gamma}$可以略去，因此可以将单量子比特在一个球面上表示(Bloch球面)

$$
\ket{\psi}\bra{\psi}=\frac{1}{2}I+\frac{1}{2}sin\theta cos\phi\text{ }\sigma_x+\frac{1}{2}sin\theta sin\phi\text{ }\sigma_y+\frac{1}{2}cos\theta\text{ }\sigma_z
$$

### 泡利矩阵
$$
\sigma_x=\sigma_1=X=\begin{pmatrix} 0 & 1 \\ 1 & 0\end{pmatrix} \quad
\sigma_y=\sigma_2=Y=\begin{pmatrix} 0 & -i \\ -i & 0\end{pmatrix} \quad
\sigma_z=\sigma_3=Z=\begin{pmatrix} 1 & 0 \\ 0 & -1 \end{pmatrix}
$$

## 多量子比特

### 表示方式
两个量子位，相应的有4个计算基矢态
$$
\ket{00},\ket{01},\ket{10},\ket{11} (这里\ket{ij}=\ket{i}_1 \otimes \ket{j}_2)
$$

双量子位的任意状态可以写成计算基矢态的叠加，并且系数满足归一化条件

### 纠缠态
多粒子态不能写成每一个粒子波函数的乘积态称为纠缠态，比如Bell态：
$$
\frac{\ket{00} \pm \ket{11}}{\sqrt{2}} \qquad \frac{\ket{01} \pm \ket{10}}{\sqrt{2}}
$$
否则称为分离态

### 更多的量子比特
对于n个量子比特，计算基态为$\ket{x_1 x_2 \cdots x_n}$，$2^n$个几率辐

# 第二章 线性代数

## 线性算子
线性算子：矢量空间V和W之间的一个线性算子$A$被定义为任意的函数$A:V \to W$，它对输入是线性的。

特别地，$A:V \to V$是定义在向量空间V上的线性算子。

设$A:V \to W$为矢量空间V与W之间的一个线性算子，设$\ket{v_1},\cdots,\ket{v_m}$为V的一个基，$\ket{w_1},\cdots,\ket{w_n}$为W的一个基，则对每个$\ket{v_j},(j=1,\cdots,m)$，存在复数$A_{1j}~A_{nj}$，使得：$A\ket{v_j}=\sum_{i}A_{ij}\ket{w_i}$。此矩阵$[A_{ij}]$就叫算子A的矩阵表示。

## 内积
在量子信息学中常出现的有限维复矢量空间中，Hilbert空间与内积空间是一样的，这两词可互换。 

### Gram-Schmidt方法 
设$\ket{w_1},\cdots,\ket{w_d}$是内积空间V的一组基，则可以用Gram-Schmidt方法产生一个V的标准正交基$\ket{v_1},\cdots,\ket{v_d}$，其中：
$$
\ket{v_1} \equiv \frac{\ket{w_1}}{\left\lVert \ket{w_1} \right\rVert} \\
\ket{v_{k+1}} \equiv \frac{\ket{w_{k+1}}-\sum^{k}_{i=1} \braket{v_i|w_{k+1}} \ket{v_i}}{\left\lVert \ket{w_{k+1}}-\sum^{k}_{i=1} \braket{v_i|w_{k+1}} \ket{v_i} \right\rVert}(1 \leq k \leq d-1)
$$

## 外积
设$\ket{v}$为内积空间V上的矢量，$\ket{w}$为内积空间W上的矢量，则外积$\ket{w}\bra{v}$为从V到W的线性算子，其作用为：$(\ket{w}\bra{v})(\ket{v'})\equiv\ket{w}\braket{v|v'}$

可以用矩阵表示为：
$$
\ket{w}\bra{v}=\begin{pmatrix} w_1 \\ \vdots \\ w_n\end{pmatrix} \begin{pmatrix} v_1^*,\cdots,v_n^*\end{pmatrix}=\begin{pmatrix} w_1v_1^* & \cdots & w_1v_m^* \\ \cdots & \cdots & \cdots \\ w_nv_1^* & \cdots & w_nv_m^*\end{pmatrix}
$$
### 完备性关系
设$\ket{i}$为矢量空间中一组标准正交基，则$\sum\ket{i}\bra{i}=I$

### 外积表示
$A=I_W A I_V=\sum_{ij}\ket{w_j}\bra{w_j}A\ket{v_i}\bra{v_i}=\sum_{ij}\bra{w_j}A\ket{v_i}\ket{w_j}\bra{v_i}$
相对于输入基$\ket{v_i}$和输出基$\ket{w_j}$，A的第i列第j行元素是$\bra{w_j}A\ket{v_i}$

## 本征向量与本征值(eigenvectors and eigenvalues)
矢量空间V上算子A的一个对角表示如下，其中矢量$\ket{i}$形成A的一个正交本征矢量集：$A=\sum_i\lambda_i\ket{i}\bra{i}$

厄米共轭/伴随(adjoints)算子：$A^{\dagger}=(A^*)^T$，即共轭转置。

### 厄米(Hermitian)算符
其伴随即自身，$A^{\dagger} \equiv A$

性质：
1. 厄米算符的平均值为实数
2. 厄米算符的本征波函数具有正交性
3. 厄米算符的本征函数是完备的
4. 两个厄米算符有共同本征波函数完备集的充分必要条件是：二者对易

### 几类重要算子

* 投影算子：设W为d维矢量空间V的k维子空间，可构造V的正交基 $\ket{1},\cdots,\ket{d}$ ，使得W的正交基为 $\ket{1},\cdots,\ket{k}$ 。定义 $P\equiv\sum^k_{i=1}\ket{i}\bra{i}$ 为子空间W上的投影子(projector)。

- 正规(normal)算子A满足关系：$AA^{\dagger}=A^{\dagger}A$

- 半正定算子

- 酉(Unitary)矩阵或酉算子：$U^{\dagger}U=UU^{\dagger}=I$

    - 酉矩阵是正规矩阵，具有谱分解
    - 具有保内积运算
    - 如果 $\ket{v_i}$ 是一个标准正交基，那么 $U\ket{v_i}$ 也是标准正交基

## 正规算子的谱分解定理
矢量空间V上的任何正规算子M对于V的某个正交归一基是对角化的。反之, 任何可对角化的算子也是正规的。

即正规算子可以表示成：
$$M=\sum_i \lambda_i\ket{i}\bra{i}$$
$\lambda_i$ 是M的本征值，$\ket{i}$是V的正交归一基，每个$\ket{i}$是M的具有本征值$\lambda_i$的本征矢量。

## 张量积
设V和W分别为m, n维的矢量空间，则$V \otimes W$为mn维矢量空间，其元素是V中元素和W中元素的张量积$\ket{v}\otimes\ket{w}$的线性组合，记为$\ket{v}\otimes\ket{w}=\ket{v}\ket{w}=\ket{vw}$

自身的k次张量积$\ket{\phi}^{\otimes k}=\ket{\phi}\otimes\cdots\otimes\cdots\otimes\ket{\phi}$

## 迹
$$
tr(A\ket{\psi}\bra{\psi})=\bra{\psi}A\ket{\psi}
$$

## 对易子与反对易子 
* 对易子：$[A,B]\equiv AB-BA$

    若$[A,B]=0$，则称$A,B$对易

* 反对易子：${A,B}\equiv AB+BA$
    若${A,B}=0$，则称$A,B$反对易

同时对角化定理：两个算子对易是其能同时对角化的充要条件。

设A和B为Hermitian算子，当且仅当存在一个正交归一基，使得A和B在此基下是同时对角化的，则$[A,B] = 0$。此时，称A和B为可同时对角化。

# 第三章 量子力学引论I

## 量子力学的四个假设

### 假定1
任意孤立的物理系统都有一个与其相联的具有内积的复矢量空间(即Hilbert空间)，称之为状态空间。系统完全由状态矢量完备地表征，态矢量是系统的状态空间中的单位矢量。

### 假定2
一个封闭(closed)量子系统的演化由一个酉变换来描述。即$t_1$时刻的状态$\ket{\psi}$与$t_2$时刻的状态$\ket{\psi'}$由一个酉算子$U$(它只依赖于时间$t_1$和$t_2$)联系起来：
$$\ket{\psi'}=U\ket{\psi}$$

假定2'：一个封闭量子系统的状态的时间演化由Schrodinger方程描述：
$$
i\hbar\frac{d\ket{\psi}}{dt}=H\ket{\psi}
$$
其中$H$为系统的Hamiltonian，是一个厄米算子，所以有谱分解：$H=\sum E\ket{E}\bra{E}$

### 假定3 
量子测量由一组测量算子$\{M_m\}$来描述。这些算子作用于被测系统的状态空间上。m指系统可能发生的测量结果。如果测量前系统的态为$\ket{\psi}$，则测量后结果m发生的概率为
$$
p(m)=\bra{\psi}M_m^{\dagger}M_m\ket{\psi}
$$
测量后的系统状态为：$\frac{M_m\ket{\psi}}{\sqrt{\bra{\psi}M_m^{\dagger}M_m\ket{\psi}}}$，
此测量算子满足完备性方程：$\sum M_m^{\dagger}M_m=I$
    
#### 投影测量：
假定3描述的通用测量的一个重要特例(满足完备性&正交性)
- 投影测量由被观测系统状态空间上的可观测量厄米算子$M$描述，此观测量具有谱分解$M=\sum mP_m$ (此处，$P_m$是投影到算子$M$的本征值为m的本征空间的投影算子)
- 测量状态$\ket{\psi}$得到结果m的概率是$p(m)=\bra{\psi}P_m\ket{\psi}$。如果得到结果m，测量后系统状态变成$\frac{P_m\ket{\psi}}{\sqrt{p(m)}}$。
- 在$\ket{m}$基上的测量，就是意味着做一投影测量，而投影算子为$P_m=\ket{m}\bra{m}$

#### POVM(Positive Operator-Valued Measurement)测量
定义$E_m\equiv M_m^{\dagger}M_m$，其满足下列条件：
- 每个算子$E_m$是半正定的(厄米算子)
- $E_m$满足完备性关系：$\sum E_m=I$

得到结果m的概率为$p(m)=\bra{\psi}E_m\ket{\psi}$

投影测量是POVM算子

### 假定4
复合系统的状态空间是分物理系统态空间的张量积。若有n个子系统, 第i个系统处于状态$\ket{\psi_i}$，则总系统的状态为
$$
\ket{\psi_1}\otimes\ket{\psi_2}\cdots\otimes\ket{\psi_n}
$$
基为$\{\ket{\psi^{(1)}_i}\}\otimes\{\ket{\psi^{(2)}_j}\}\cdots\otimes\{\ket{\psi^{(n)}_k}\}$

#### 纠缠态(entanglement)
当一个复合系统的状态不能写成其子系统状态的张量积时，称此态为纠缠态，如$\ket{\psi}=\frac{\ket{00}+\ket{11}}{\sqrt{2}}$

##### Bell态
$$
\ket{\beta_{00}}=\frac{\ket{00}+\ket{11}}{\sqrt{2}}\quad\ket{\beta_{01}}=\frac{\ket{01}+\ket{10}}{\sqrt{2}}\quad\ket{\beta_{10}}=\frac{\ket{00}-\ket{11}}{\sqrt{2}}\quad\ket{\beta_{11}}=\frac{\ket{01}-\ket{10}}{\sqrt{2}}
$$

# 第四章 密度算子
设量子系统以概率$p_i$处在一组状态$\ket{\psi_i}$的某一个，则称$\{p_i,\ket{\psi_i}\}$为一个纯态系综，定义系统的密度算子(密度矩阵)为：$\rho\equiv\sum p_i\ket{\psi_i}\bra{\psi_i}$

## 密度算子的演化
假设封闭系统的演化由酉算子$U$来描述。如果系统有$p_i$的概率处于初态$\ket{\psi_i}$，则经过酉演化$U$后，系统有$p_i$的概率处于$U\ket{\psi_i}$，那么密度算子的演化过程为：
$$
\rho=\sum_ip_i\ket{\psi_i}\bra{\psi_i}\overset{\text{U}}{\rightarrow}\sum_ip_iU\ket{\psi_i}\bra{\psi_i}U^{\dagger}=U\rho U^{\dagger}
$$

## 量子测量
$$
\begin{align*}
p(m)&= \sum_i p(m|i)p_i=\sum_i p_i tr(M_m^{\dagger} M_m \ket{\psi_i} \bra{\psi_i}) \\
&=\sum_i tr(M_m^{\dagger}M_m p_i \ket{\psi_i}\bra{\psi_i}) =tr(M_m^{\dagger}M_m \rho)
\end{align*}
$$
测量得到m后系统的状态为$\ket{\psi^m_i}=\frac{M_m\ket{\psi_i}}{\sqrt{\bra{\psi_i}M_m^{\dagger}M_m\ket{\psi_i}}}$

经过一个得到结果m的测量，得到状态$\ket{\psi^m_i}$对应概率为$p(i|m)$的系综。相应的密度算子是
$$
\begin{align*}
\rho_m &= \sum_i p(i|m)\ket{\psi^m_i}\bra{\psi^m_i} = \sum_i p(i|m) \frac{M_m \ket{\psi_i}\bra{\psi_i}M_m^{\dagger}}{\bra{\psi_i}M_m^{\dagger}M_m \ket{\psi_i}} \\
&=\frac{M_m(\sum\limits_{i}p_i\ket{\psi_i}\bra{\psi_i})M_m^{\dagger}}{tr(M_m^{\dagger}M_m\rho)}=\frac{M_m\rho M_m^{\dagger}}{tr(M_m^{\dagger}M_m\rho)} 
\end{align*}
$$
$$
(tr(M_m^{\dagger}M_m\ket{\psi_i}\bra{\psi_i}))=\bra{\psi_i}M_m^{\dagger}M_m \ket{\psi_i}
$$

## 纯态与混合态
- 纯态：一个量子系统其状态精确知道，就叫做处于纯态(pure state)。此时密度算子就是$\rho=\ket{\psi}\bra{\psi}$

- 混合态：如果一个量子系统的状态不精确知道，就处于一个混合态，它就叫做一个系综的不同纯态的混合体(mixture)。

    纯态满足$tr(\rho^2)=1$，混合态满足$tr(\rho^2)<1$

- 混合态密度算子：设一个量子系统制备在$\rho_i$的概率为$p_i$，则系统的密度矩阵为$\rho=\sum p_i \rho_i$。则称$\rho$是具有概率$p_i$的状态$\rho_i$的混合体(mixture)。

## 密度算子的一般性质
一个算子$\rho$是与某个系综$\{p_i,\ket{\psi_i}\}$相联系的密度算子，当且仅当：
1. 其迹为1
2. 算子为正定的

## 四个假定的密度算子描述
1. 与任何孤立物理系统相联系的是一个具有内积的复矢量空间(即Hilbert空间)， 称为系统的状态空间。系统由其密度算子完备描述, 此密度算子为正定的且迹为1，作用于系统的状态空间上。如果一个量子系统以概率$p_i$处于状态$\rho_i$，则系统的密度算子为：$\sum p_i \rho_i$
2. 一个封闭量子系统的演化是由一个酉变换来描述的。即系统在时刻$t_1$的状态$\rho$与系统在时刻$t_2$的状态$\rho'$是由只依赖
于时刻$t_1$和$t_2$的酉算子$U$来描述的：$\rho'=U\rho U^{\dagger}$
3. 量子测量由一组测量算子的集合$\{M_m\}$来描述。这些是作用在被测系统的状态空间上的算子。索引$m$指的是实验中可能发生的测量结果。   
    如果测试前系统的状态为$\rho$，则测得结果$m$的概率为$p(m)=tr(M^{\dagger}_mM_m\rho)$ 且测量后系统的状态为$\frac{M_m\rho M_m^{\dagger}}{tr(M^{\dagger}_mM_m\rho)}$。测量算子满足完备性方程$\sum M^{\dagger}_mM_m=I$
4. 一个复合物理系统的状态空间是组元物理系统的状态空间的张量积。进一步地, 拥有编号从$1$到$n$的系统，且第$i$号系统被制备到状态$\rho_i$，则全系统的联合状态(joint state)是$\rho_1\otimes\rho_2\otimes\cdots\rho_n$

## 集合生成算子
设由未归一化集合$\ket{\tilde{\psi_i}}$生成算子$\rho\equiv\sum\ket{\tilde{\psi_i}}\bra{\tilde{\psi_i}}$，与普通密度算子系综的关系由$\ket{\tilde{\psi_i}}=\sqrt{p_i}\ket{\psi_i}$

定理：(密度矩阵系综中的酉矩阵自由度)两个集合$\ket{\tilde{\psi_i}}$和$\ket{\tilde{\phi_i}}$生成相同的密度矩阵，当且仅当$\ket{\tilde{\psi_i}}=\sum_j u_{ij}\ket{\tilde{\phi_i}}$。其中$u_{ij}$是具有复数元素的酉矩阵，具有索引$i$和$j$，并且我们对于矢量集合$\ket{\tilde{\psi_i}}$和$\ket{\tilde{\phi_i}}$中小的那个附加另外的矢量0，使得这两个集合具有相同数目的元素。

## 约化密度算子
假设由系统$A$和$B$组成了复合系统，它的密度算子是$\rho^{AB}$，则系统$A$的约化密度算子算子就定义为$\rho_A\equiv tr_B(\rho^{AB})$

$tr_B$是一算子映射，称为系统$B$上的偏迹(partial trace)
$$
tr_B(\ket{a_1}\bra{a_2}\otimes\ket{b_1}\bra{b_2})\equiv\ket{a_1}\bra{a_2}tr(\ket{b_1}\bra{b_2})=\ket{a_1}\bra{a_2}\braket{b_2|b_1}
$$
其中$\ket{a_1}$和$\ket{a_2}$为$A$状态空间的两个矢量，其中$\ket{b_1}$和$\ket{b_2}$为$B$状态空间的两个矢量
### 一个等式
$\ket{a_1}$和$\ket{a_2}$为$A$状态空间的两个矢量，其中$\ket{b_1}$和$\ket{b_2}$为$B$状态空间的两个矢量
$$
\ket{a_1b_1}\bra{a_2b_2}=\ket{a_1}\bra{a_2}\otimes\ket{b_1}\bra{b_2}
$$

## Schmidt分解
设$\ket{\psi}$是一个复合系统$AB$的纯态。则对于系统$A$存在正交归一态$\ket{i_A}$，对于系统$B$存在正交归一态$\ket{i_B}$，使得：$\ket{\psi}=\sum_i\lambda_i\ket{i_A}\ket{i_B}$，其中$\lambda_i$为非负实数，满足$\sum_i\lambda_i^2=1$，称之为Schmidt系数。

- 基$\ket{i_A}$和$\ket{i_B}$分别称为$A$和$B$的Schmidt基。
- 非零值$\lambda_i$的个数称为Schmidt数。只有当Schmidt数为1时，复合系统才是乘积态。

## 纯化 (purification)
给定一个量子系统$A$的状态$\rho^A$，可以引入另一个系统$R$，且定义一个纯态$\ket{AR}$，对联合系统$AR$使得$\rho^A=tr_R(\ket{AR}\bra{AR})$

### 纯化的方法
1. 设$\rho^A$具有一个正交归一解$\sum_ip_i\ket{i^A}\bra{i^A}$
2. 引入系统$R$，它具有与系统$A$相同的状态空间，具有正交归一基$\ket{i^R}$，且对联合系统定义一个纯态$\ket{AR}\equiv\sum_i\sqrt{p_i}\ket{i^A}\ket{i^R}$

即
1. 定义一个纯态
2. 该纯态对于系统$A$的Schmidt基恰好将混合态对角化
3. 该纯态的Schmidt系数是被纯化的密度算子本征值的平方根 

# 第五章 量子线路
## 量子计算的基本要求
1. Scalable qubits
2. Universal quantum gate
    - single-bit gate and two-qubit gate
3. Initialization
    - preparation of $\ket{0}$ state
4. Readout
    - $a\ket{0}+b\ket{1}\Rightarrow$ 0 with probability $|a|^2$, 1 with probability $|b|^2$
5. Long decoherence time
    - much longer than gate operation time

## 单量子门
任意$2\times2$的酉矩阵都是单量子比特逻辑门，每一个酉矩阵都定义一个有效的逻辑门。(注意这些门是定义在某一组基矢下)

### Pauli矩阵
$$
X\equiv\begin{bmatrix} 0&1 \\ 1&0 \end{bmatrix} \quad Y\equiv\begin{bmatrix} 0 &-i \\ i&0 \end{bmatrix} \quad Z\equiv\begin{bmatrix} 1&0 \\ 0&-1 \end{bmatrix}
$$
### 其他常用酉矩阵
1. Hadamard门
$$
H\equiv\frac{1}{\sqrt{2}}\begin{bmatrix} 1&1 \\ 1&-1 \end{bmatrix}
$$
2. 位相门(Phase门)
$$
S\equiv\begin{bmatrix} 1&0 \\ 0&i \end{bmatrix}
$$
3. $\pi/8$门
$$
T\equiv\begin{bmatrix} 1&0 \\ 0&e^{\frac{i\pi}{4}}\end{bmatrix}=e^{\frac{i\pi}{8}}\begin{bmatrix} e^{\frac{-i\pi}{8}}&0 \\ 0&e^{\frac{i\pi}{8}} \end{bmatrix}
$$

## 量子线路的注意事项
1. 连线必须是单线，这种连线不一定是物理上的连线，可能对应于一段时间或空间从一处移动到另一处 
2. 线路读法（信息处理从左到右），逻辑门对应从右到左，越左越后作用在态上
3. 不允许有回路出现，即从一部分到另一部分的反馈 
4. 不允许有连线汇合（不可逆）
5. 不允许有分支（量子不可克隆定理）

## Bloch球面
$$
\ket{\psi}=exp(i\gamma)[cos\frac{\theta}{2}\ket{0}+e^{i\phi}sin\frac{\theta}{2}\ket{1}]
$$
$$
\begin{align*}
\rho &=\ket{\psi}\bra{\psi}=\frac{1}{2}I+\frac{1}{2}sin\theta cos\phi \sigma_x+\frac{1}{2}sin\theta sin\phi \sigma_y+\frac{1}{2}cos\theta \sigma_z \\
&=\frac{1}{2}(I+\rho_xX+\rho_yY+\rho_zZ)
\end{align*}
$$
Bloch矢量：
$$
\bm{\rho}=(sin\theta cos\phi,sin\theta sin\phi,cos\theta)=(\bm{\rho_x},\bm{\rho_y},\bm{\rho_z})
$$
### 旋转算子
1. 绕x轴旋转：
$$
R_x(\theta)\equiv e^{-i\theta X/2}=cos\frac{\theta}{2}I-i sin\frac{\theta}{2}X=\begin{bmatrix} cos\frac{\theta}{2}&-isin\frac{\theta}{2} \\ -isin\frac{\theta}{2}&cos\frac{\theta}{2} \end{bmatrix}
$$
2. 绕y轴旋转
$$
R_y(\theta)\equiv e^{-i\theta Y/2}=cos\frac{\theta}{2}I-i sin\frac{\theta}{2}Y=\begin{bmatrix} cos\frac{\theta}{2}&-isin\frac{\theta}{2} \\ isin\frac{\theta}{2}&cos\frac{\theta}{2} \end{bmatrix}
$$
3. 绕z轴旋转
$$
R_z(\theta)\equiv e^{-i\theta Z/2}=cos\frac{\theta}{2}I-i sin\frac{\theta}{2}Z=\begin{bmatrix} e^{-i\theta/2}&0 \\ 0&e^{i\theta/2} \end{bmatrix}
$$
推广：若$\hat{n}=(n_x,n_y,n_z)$为3维实单位矢量，则绕$\hat{n}$轴旋转$\theta$角的算子为
$$
R_{\hat{n}}(\theta)=exp(-i\theta\hat{n}\cdot\vec{\sigma/2})=cos\frac{\theta}{2}I-isin\frac{\theta}{2}(n_xX+n_yY+n_zZ)
$$

## 单量子位的Z-Y分解
设$U$是对单量子位的酉操作，则存在实数$\alpha$，$\beta$，$\gamma$，$\delta$，使得
$$
U=e^{i\alpha}R_z(\beta)R_y(\gamma)R_z(\delta)
$$
### 推论
设$U$是一个单量子位上的酉门。则存在单量子位上的酉算子$A$，$B$，$C$, 使得$ABC=I$且
$$
U=e^{i\alpha}AXBXC
$$

## 受控操作

### 两比特受控-U(Controlled-U)操作
运算规则：U是单量子比特上的任意酉运算，是双量子比特的运算。如果控制比特置位(是$\ket{1}$)，则$U$作用到目标比特。否则目标比特不变。

操作：
$$
\ket{ct}=\ket{c}\ket{t}\overset{\text{受控U}}{\rightarrow}=\ket{c}U^c\ket{t}
$$

CNOT门：$U=X$ or $CNOT=(I\otimes H)CZ(I\otimes H)$

### 对单量子位门实现C-U操作
$$
U=exp(i\alpha)AXBXC, ABC=I
$$

### 表示$C^n(U)$操作的线路
$C^n(U)$表示当n个控制位都为1时，对k位实施U操作
$$
C^n(U)\ket{x_1,\cdots,x_n}\ket{x_{n+1},\cdots,x_{n+k}}=\ket{x_1,\cdots,x_n}U^{x_1\cdots x_n}\ket{x_{n+1},\cdots,x_{n+k}}
$$

### Toffoli门
真值表：
|Input a|Input b|Input c|Output a'|Output b'|Output c'|
|:-:|:-:|:-:|:-:|:-:|:-:|
|0|0|0|0|0|0|
|0|0|1|0|0|1|
|0|1|0|0|1|0|
|0|1|1|0|1|1|
|1|0|0|1|0|0|
|1|0|1|1|0|1|
|1|1|0|1|1|1|
|1|1|1|1|1|0|

## 测量
### 推迟测量原理(Principle of deferred measurement)
总能够把测量从量子线路的中间阶段移到结尾；如果在线路的某部分用到了测量结果，则经典的条件操作可由带条件的量子操作(即量子受控操作)来代替。

当被测量子比特是一个量子门的控制比特时，则测量和量子门可以交换.

### 隐含测量原则(Principle of implicit measurement)
不失一般性，在量子线路结尾的未终止的量子线(即未测量的量子比特)都可假定为已被测量。

## 普适量子门
对于量子线路，如果任意的酉操作都可用一个集合中的门构成的线路来近似，且可达到任意精度，则称此集合中的门对于量子计算是普适的。

可以证明用H、CNOT、S、T门以任意精度近似任意酉操作。

## Gray code
设我们有两个不同的二进制数，s和t。则我们可以找到一系列二进制数，从s开始，到t结束，列表中相邻的两个数只有一位数字不同，这就是Gray码。因此Gray码是一组二进制的数，每一组数称为码元。

## 能量与计算
### 可逆逻辑门
给定输出可唯一确定输入，即为可逆逻辑门，否则为不可逆逻辑门。非门和Toffoli门等都是可逆的。

### Landauer原理
1. 设一个计算机擦除一位的信息，则耗散到环境中的能量至少为$k_BT\times ln2$。其中$k_B$为Boltzman常数，T为计算机的环境温度。
2. 设一个计算机擦除一位信息，则环境的熵至少增加$k_B\times ln2$

## 量子计算线路模型总结
1. 经典资源
    
    量子计算包括经典部分和量子部分
2. 一个合适的状态空间

    $2^n$维的复Hilbert空间，积形式$\ket{x_1,x_2,x_3,\cdots,x_n}$的状态称为计算机的计算基态，其中$x_i=0,1$，每一个基矢态简写为$\ket{x}$且x是二进制表示为$x_1x_2\cdots x_n$的数。
3. 制备处于计算基矢态的能力

    任何计算基矢态$\ket{x_1,x_2,x_3,\cdots,x_n}$，可在n步内制备。
4. 执行量子门运算的能力

    可以对量子比特的任意子集施加逻辑门。存在普适量子门集。
5. 在计算基矢上进行测量的能力

# 第六章 量子算法
## 量子并行性
1. 采用Toffoli门实现与非门：
    上面两位表示与非门的输入，第3位制备成标准态1(也称为辅助态ancilla state)，输出放在第3位。
2. 采用Toffoli门的扇出(fanout)
    第二位是到fanout的输入，其他两位为标准辅助位($\ket{1}\ket{0}$)，输出在第二位和第三位。

有了用Toffoli门表示的与非门与FANOUT，就可以模拟经典线路中所有其他元件。因而一个任意的经典线路都能用一个等效的可逆线路来模拟。

### 量子不可克隆原理
由于量子力学的态叠加原理，量子系统的任意未知量子态，不可能在不遭破坏的前提下，以确定成功的概率被克隆到另一个体系。

### 多量子位Hadamard变换
- 所有量子位的初始态都为$\ket{0}$，即初态为$\ket{000\cdots0}$
$$
H^{\otimes n}\ket{0}^{\otimes n}=\frac{1}{\sqrt{2^n}}\sum_x\ket{x}
$$
- 求和是对所有可能的x值

对具有n个量子位的输入，$f(x)$具有n位输入，需制备$n+1$为位量子比特$\ket{000\cdots0}$，前n位用Hadamard门并对$n+1$位实现$U_f$变换结果。即为
$$
\frac{1}{\sqrt{2^n}}(\sum_x\ket{x})\ket{0}=\frac{1}{\sqrt{2^n}}(\sum_x\ket{x}\ket{0})\overset{U_f}{\rightarrow}\frac{1}{\sqrt{2^n}}(\sum_x\ket{x}\ket{f(x)})
$$
仅有量子并行性并不能提高运算速度。每次测量只能得到一个结果，而且所的结果的机率是一样的。 

## Deutsch算法
1. 输入态
$$
\ket{\psi_0}=\ket{01}
$$
2. 对初始态做Hadamard变换
$$
\ket{\psi_1}=\left[\frac{\ket{0}+\ket{1}}{\sqrt{2}}\right]\left[\frac{\ket{0}-\ket{1}}{\sqrt{2}}\right]
$$
3. 施加$U_f$
$$
\ket{\psi}=\ket{x}\left[\frac{\ket{0}-\ket{1}}{\sqrt{2}}\right]\overset{U_f}\rightarrow\ket{x}(-1)^{f(x)}\frac{\ket{0}-\ket{1}}{\sqrt{2}}
$$
$$
\begin{align*}
\ket{\psi_2}&=\frac{1}{\sqrt{2}}\left[\ket{0}(-1)^{f(0)}\frac{\ket{0}-\ket{1}}{\sqrt{2}}+\ket{1}(-1)^{f(1)}\frac{\ket{0}-\ket{1}}{\sqrt{2}}\right] \\
&=\left[\frac{\ket{0}(-1)^{f(0)}+\ket{1}(-1)^{f(1)}}{\sqrt{2}}\right]\left[\frac{\ket{0}-\ket{1}}{\sqrt{2}}\right] \\
&=
\begin{cases}
\pm \left[\frac{\ket{0}+\ket{1}}{\sqrt{2}}\right]\left[\frac{\ket{0}-\ket{1}}{\sqrt{2}}\right], &\text{if: }f(0)=f(1) \\
\pm \left[\frac{\ket{0}-\ket{1}}{\sqrt{2}}\right]\left[\frac{\ket{0}-\ket{1}}{\sqrt{2}}\right], &\text{if: }f(0)\neq f(1)
\end{cases}
\end{align*}
$$
4. 第一个量子比特经过最后的Hadamard门
$$
\begin{align*}
\ket{\psi_3}&=
\begin{cases}
\pm \ket{0}\left[\frac{\ket{0}-\ket{1}}{\sqrt{2}}\right], &\text{if: }f(0)=f(1) \\
\pm \ket{1}\left[\frac{\ket{0}-\ket{1}}{\sqrt{2}}\right], &\text{if: }f(0)\neq f(1)
\end{cases} \\
&=
\pm \ket{f(0)\oplus f(1)}\left[\frac{\ket{0}-\ket{1}}{\sqrt{2}}\right]
\end{align*}
$$
- 只对第一位测量一次，即可得知f(x)的一个整体特性$f(0)\oplus f(1)$
- 量子线路使我们能确定函数的一个整体特性，而只计算一次f(x)

## Deutsch-Jozsa算法
- Alice，$0~2^n-1$间选数x，送给Bob计算f(x)，f(x)只能是0或1
    - Bob只能选择两种函数之一：constant or balanced
    - Constant即对所有x，f(x)值相同
    - Balanced即对一半的x，f(x)=0，另一半等于1
- Bob把计算的数据发给Alice
- Alice猜Bob所选择的f(x)种类

量子算法只需要1次就能猜对

条件：
1. Alice和Bob交换的是量子比特
2. Bob同意用酉变换$U_f$来计算f(x)

步骤：
1. Alice 用n量子比特的寄存器存储她的查询输入，用一个单量子比特寄存器给Bob存储答案
2. 开始把查询和答案寄存器置于一个叠加态
3. Bob用量子并行计算f(x)，把结果放在答案寄存器中 
4. Alice用Hadamard变换干涉查询寄存器的状态并做测量

## 量子傅里叶变换
设有一组正交归一基$\ket{0},\cdots,\ket{N-1}$，则量子Fourier变换式：
$$
F\ket{j}=\frac{1}{\sqrt{N}}\sum^{N-1}_{k=0}e^{\frac{2\pi ijk}{N}}\ket{k}
$$
令$\ket{\psi}=\sum x_j\ket{j}$，则
$$
F\ket{\psi}=\sum_{k=0}^{N-1}y_k\ket{k} \text{ ,其中}y_k=\frac{1}{\sqrt{N}}\sum^{N-1}_{k=0}x_je^{\frac{2\pi ijk}{N}}
$$

此外，还可以表示为：
$$
F\ket{j_1,\cdots,j_n}=\frac{(\ket{0}+e^{2\pi i0.j_n\ket{1}})(\ket{0}+e^{2\pi i0.j_{n-1}j_n})\cdots(\ket{0}+e^{2\pi i0.j_1j_2\cdots j_n})}{2^{n/2}}
$$

用到矩阵：
$$
R_k=\begin{bmatrix}1&0 \\ 0&e^{\frac{2\pi i}{2^k}}\end{bmatrix} \quad
R_1=Z \quad R_2=S \quad R_3=T
$$