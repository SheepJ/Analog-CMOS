## 
模拟信号：时间上连续并且具有无限范围的值
模拟IC：产生或放大模拟信号
数字信号：离散的

## 模拟IC的应用
控制；数据转换；功率调节；通信；仪器仪表和物理世界接口；计算；

## 模拟IC设计要求
关注功耗和处理速度；它们一般矛盾。

## 如何设计
1. 设计规范
1. 子电路设计、物理布局和仿真

## 汽车芯片的五大功能
计算、感知、执行、通信、存储


## 汽车芯片九大类
1. 控制
1. 计算
1. 功率
1. 通信
1. 存储
1. 电源/模拟
1. 驱动
1. 传感
1. 安全





# CH2 CMOS器件基础

## KCL和KVL
 简单

## 戴维南和诺顿定理
戴维南： 含独立电源的线性电阻单口网络N，就端口特性而言，可以等效为一个电压源和电阻串联的单口网络。电压源的电压等于单口网络在负载开路时的电压；电阻Ro是单口网络内全部独立电源为零值时所得单口网络No的等效电阻。 <br>
诺顿定理：含独立源的线性电阻单口网络N，就端口特性而言，可以等效为一个电流源和电阻的并联。电流源的电流等于单口网络从外部短路时的端口电流；电阻Ro是单口网络内全部独立源为零时所得网络 No的等效电阻

戴维南和诺顿等效的电阻是一样的吗？ <br>

## 叠加定理
叠加定理陈述为：由全部独立电源在线性电阻电路中产生的任一电压或电流，等于每一个独立电源单独作用所产生的相应电压或电流的代数和。
在计算某一独立电源单独作用所产生的电压或电流时，应将电路中其它独立电压源用短路代替，而其它独立电流源用开路代替。



## MOSFET 结构
1. 源提供载流子，漏端收集载流子<br>
1. 源漏掺杂会向栅极下方扩散，有效沟道长度应该为沟道长度（即栅的长度）减去两倍扩散长度 $L_{eff} = L_{drawn} - 2L_D$ <br>
1. 栅宽W越大导电能力越强，栅电容越大。 <br>


NMOS体区连最低电位；PMOS体区连最高电位。 <br>

### 符号表示
分数字和模拟

## I-V特性
### 阈值电压
发生强反型时的电压，在半导体中的MIS结构学过。 <br>

### I-V关系
NMOS： <br>
线性区 $I_D = \mu_n C_{ox} \frac{W}{L} [(V_{GS} - V_{TH})V_{DS} - \frac{1}{2}V_{DS}^2]$ <br>
饱和区 $I_D = \frac{1}{2} \mu_n C_{ox} \frac{W}{L} (V_{GS} - V_{TH})^2$ <br>

PMOS： <br>
线性区 $I_D = - \mu_p C_{ox} \frac{W}{L} [(V_{GS} - V_{TH})V_{DS} - \frac{1}{2}V_{DS}^2]$ <br>
饱和区 $I_D = - \frac{1}{2} \mu_p C_{ox} \frac{W}{L} (V_{GS} - V_{TH})^2$ <br>

### 跨导
跨导等于电流对电压求导。 <br>
NMOS： <br>
饱和区 $g_m = \mu_n C_{ox} \frac{W}{L} (V_{GS} - V_{TH}) = \frac{2 I_D}{V_{GS} - V_{TH}} = \sqrt{2 \mu_n C_{ox} \frac{W}{L} I_D}$ <br>
饱和区 $g_m$ 为线性区导通电阻的倒数。 <br>

期望MOS工作于饱和区，因为线性区的 $g_m$ 较小，并且还随 $V_{DS}$ 变化。 <br>

### 二级效应
#### 体效应
也叫衬底偏置效应，或者背栅效应，是由于体区和漏极存在电位差而导致阈值电压的变化。 <br>
在设计工艺中PMOS一般不会有体效应的问题，因为PMOS做在n-well上，每个n-well都可以独立的接一个电位，只要将源极与n-well相连就能避免体效应。 <br>
而NMOS做在一个大p型衬底上，p型衬底必须接地，因此源极电位就可能不等于地。 <br>

#### 沟道长度调制效应
实际沟道长度与 $V_{DS}$ 相关。 $\lambda$ 为沟道长度调制系数。<br>
考虑沟道长度调制效应后，饱和区电流 <br>
$I_D = \frac{1}{2} \mu_n C_{ox}\frac{W}{L}(V_{GS} - V_{TH})^2(1 + \lambda V_{DS})$ <br>
饱和区跨导<br>
$g_m = \mu_n C_{ox} \frac{W}{L} (V_{GS} - V_{TH})(1 + \lambda V_{DS}) = \frac{2 I_D}{V_{GS} - V_{TH}} = \sqrt{2 \mu_n C_{ox} \frac{W}{L} I_D (1 + \lambda V_{DS})}$ <br>

沟道长度调制效应会使得 $I_D$ 随 $V_{DS}$ 增大而增大，即饱和区的 $g_m$ 不是一个定值。 <br>
增大沟道长度可以减小这种效应，但是会降低器件速度。 <br>

#### 亚阈值导电
在 $V_{GS} < V_{TH}$ 时沟道不会完全关断，沟道处于若反型， $I_D$ 与 $V_{GS}$ 成指数关系。 <br>

## 电容模型
电路模型和CMOS模型 <br>
具体表达式要不要记? <br>


## 小信号模型
1. 直流电压源看作大电容，视为短路，直流电流源看作大电感，视为开路。 <br>
1. 交流源保留
1. 受控源保留
1. 体效应带来一个附加受控源与 $g_m V_{GS}$ 并联，  $g_{mb} V_{BS}$ ， 其中 $g_{mb} = g_m \frac{\gamma}{2 \sqrt{2 \Phi_F + V_{SB}}} = \eta g_m$ <br>
1. 沟道长度调制效应会带来一个附加电阻 $r_o$ 与受控源并联。 $r_o =\frac{1}{\lambda I_D}$ <br>




# CH3 单级放大器
## 一. 八边形法则
噪声： 低 <br>
线性度：期望有高的线性度<br>
增益：期望高增益<br>
电源电压<br>
电压摆幅： 期望大的摆幅<br>
速度： 要快<br>
输入/输出阻抗：视不同情况选择<br>
功耗： 低功耗<br>

## 二. 有用的结论
在分析各类单级放大电路前，先认识一些结论。 <br>


## 三. 共源级

### 1. 电阻负载
$V_{in}$ 从0开始增大，会经历截止、饱和导通、进入线性区和深线性区 <br>
忽略沟道调制效应，大信号增益 $A_v = -g_m R_D$ <br>
可以列出输出电压和输入电压的关系后求导得到 <br>
考虑沟道调制效应后
$A_v = -g_m R_D \parallel r_o$ <br>
可以看做负载电阻变成了 $R_D$ 与从漏端看MOS的等效电阻 $r_o$ 的并联。 <br>

### 2. 二极管连接型
二极管连接型器件一直工作在饱和区 <br>
若用NMOS作为负载，考虑负载MOS的体效应，其源端看入等效电阻为 $\frac{1}{g_{m2} + g_{mb2}}$ <br>
因此增益 $A_v = \frac{g_{m1}}{g_{m2} + g_{mb2}} = -\sqrt{\frac{(W/L)_1}{(W/L)_2}} \frac{1}{1 + \eta}$ <br>
可以看到在忽略  $\eta$ 的变化的情况下，增益只与宽长比的比值有关，即线性度提高了。 <br>
采用PMOS可以避免体效应，因此增益中不会有   $\eta$    有关项，但是牺牲了电压余度，输出最大值为   $V_{DD} - \left| V_{GS2} \right|$   （用NMOS不会有这个问题，因为NMOS从漏到源的大信号导通压降接近0） <br>

### 3. 电流源负载
电流源不是线性电阻元件，可以提高一个很高的负载电阻同时有低的电压降，从而减小输出摆幅的损失。 <br>
用PMOS做电流源负载，从漏端看等效电阻为 $r_{op}$ ，所有负载电阻为 $r_{on} \parallel r_{op}$ <br>
增益 $A_v = - g_m r_{on} \parallel r_{op}$ <br>

### 4. 三极管区负载
处于三极管区的MOS负载作为负载，实际等效为一个电阻。实际工艺中很少用到。 <br>
导通电阻等于MOS管饱和区跨导的倒数。 <br>

### 5. 源极负反馈
1. 增益等于漏极电阻除以源极通路上所有电阻的和。 <br>
因此 $A_v =  - \frac{R_D}{1/g_m + R_s} = - \frac{g_m R_D}{1 + g_m R_s}$ <br>
1. 考虑体效应和沟道长度调制效应后：
$A_v = -G_m R_{out} = \frac{-g_m r_o R_D}{R_D + r_o + R_s + r_o R_s(g_m + g_{mb})}$ <br>

讨论： <br>
1. 其中的 $r_o + R_s + r_o R_s(g_m + g_{mb})$ 是从漏端看的等效电阻，可以看做漏端等效电阻被放大了 $1 + R_s[1 + r_o(g_m + g_{mb})]$ 倍 <br>
1. 负反馈电阻增大了输出电阻，但是获得了更好的线性度，因为引入源极电阻后，源极电位跟随栅极电位，使得 $V_{gs}$ 相对不变。 <br>



## 二. 源极跟随器
源极电压跟随栅极电压，输入阻抗高，输出阻抗低，可以用作缓冲级或电压平移。 <br>
$A_v = \frac{g_m R_s}{1 + (g_m  + g_{mb})R_s}$ <br>
当 $R_s$ 很大，可以认为 $A_v = \frac{g_m}{g_m + g_{mb}} = \frac{1}{1 + \eta}$ <br>
即使 $R_s$ 很大，增益也不能达到1，因为从工艺上一般 $\eta > 0.2$  <br>

输入与输出之间具有非线性，为了将源极电阻增大，减少从栅到源的压降，采用电流源为负载。<br>
输出阻抗 $R_{out} = \frac{1}{g_m + g_{mb}}$ 因此<br>
$A_v = g_m R_{out} = \frac{g_m}{g_m + g_{mb}}$ <br>


源极跟随器会消耗电压余度，即从栅到源有 $V_{GS}$ 的压降 <br>
源级跟随器并不是一个好的输出驱动级，更多用作电平位移 <br>


## 三. 共栅级
不考虑沟道长度调制 <br>
$A_v = g_m (1 + \eta) R_D$ <br>

考虑沟道效应后 <br>
从源端看的电阻：
$R_{in} = \frac{R_D + r_o}{1 + (g_m + g_{mb})r_o}$ <br>
相当于增大了源极看进去的电阻 <br>
等效跨导
$G_m = \frac{1 + (g_m + g_{mb})r_o}{r_o + R_s + r_o R_s(g_m  + g_{mb})}$ <br>
输出电阻
$R_{out} = R_D \parallel [r_o + R_s + r_oR_s(g_m + g_{mb})]$ <br>
增益
$A_v = \frac{1 + (g_m + g_{mb})r_o}{R_D + r_o + R_s + r_oR_s(g_m + g_{mb})} R_D$ <br>


## 四. 共源共栅级
输入电压转化为电流信号，电流信号作为共栅极的输入信号。 <br>
1. 定性分析，M2的栅极偏置变化并不会影响Vout，因为M1看做恒流源电流没变
1. 要满足电流不变，M1和M2需要工作在饱和区 <br>
分析思路：饱和即分别要求 $V_{DS} > V_{GS} - V_{TH}$ <br>
求得 $V_b > V_{in} - V_{TH1} + V_{GS2}$ <br>
输出电压Vout要大于等于两个管的过驱电压之和。可见输出电压摆幅降低了。

至于增益，漏端输入电阻可以直接看出来，等效跨导需要画小信号求出。得到： <br>
$G_m = \frac{g_{m1} r_{o1} [1+ r_{o2}(g_{m2} + g_{mb2})]}{r_{o1} + r_{o2} + r_{o1} r_{o2} (g_{m2} + g_{mb2})}$ <br>
$R_L = R_D \parallel [r_{o1} + r_{o2} + r_{o1} r_{o2}(g_{m2}+g_{mb2})]$ <br>

若将 $R_D$ 换做一个电流源，则 $R_D$ 无穷大，增益 <br>
$A_v = g_{m1} r_{o1} [1+ r_{o2}(g_{m2} + g_{mb2})]$ <br>

优点：高的输出阻抗，可以做电流源 <br>
缺点：牺牲了电压余度 <br>

屏蔽特性： <br>
共源共栅级可以屏蔽输出对输入的影响。当MOS进入三极管区屏蔽特性会减弱 <br>


## 五. 优缺点比较
|    |共源级 |源极跟随器 |共栅级 |共源共栅级|
|---|---|---|---|---|
|输入电阻|大|大|小|大|
|输出电阻|小|小|大|很大|
|增益|大|约等于1|比共源极略大|大|
|应用|第一级|中间级，电压平移|做电流源|做电流源并且能够屏蔽输出影响|



# CH4 差动放大器
优点：<br>
1. 对环境噪声和电源噪声抗干扰能力强
1. 电源抑制比和信噪比好
1. 增大了输出摆幅
1. 偏置简单，高线性度
1. 消除了偶次谐波？


缺点： <br>
1. 电路面积增加
1. 

## 基本差动对
小信号分析，半边电路法分析得到增益 
$A_v = -g_m R_D$ <br>

增加源极负反馈电阻可以提高线性度。 <br>


## 共模响应
共模增益来源 <br>
1. 尾电流源不理想，具有一个有限的阻抗
1. 负载失配，负载电阻不完全相等
1. MOS管失配

#### 1. 尾电流源不理想
假设MOS和负载电阻都完全对称，则可以将它们并联，求得 <br>
$A_{v,CM} = -\frac{\frac{1}{2}R_D}{1/(2 g_m) + R_{ss}}$ <br>
并不会影响差分增益

#### 2. 负载失配
负载电阻有 $\Delta R$ 的差异，利用上面的公式分别求输出电压，再求增益 <br>
$A_{CM-DM} = - \frac{\frac{1}{2}\Delta R}{1/(2 g_m) + R_{ss}}$ <br>

#### 3. MOS失配
MOS管的 $g_{m1}$ 和 $g_{m2}$ 不一样。 <br>
$A_{CM-DM} = - \frac{\Delta g_m R_D}{1+ (g_{m1}+g_{m2})R_{ss}}$ <br>

#### 影响
在高频时失配导致的影响会更大，因为尾电流源有寄生电容，频率越高，从电容的分流越大，尾电流会增大。 <br>

#### 共模抑制比CMRR
$CMRR = \left| \frac{A_{DM}}{A_{CM-DM}} \right|$ <br>
共模抑制比越大越好。

## MOS负载


# CH5 电流镜

## 基本电流镜
电阻偏置，受温度影响 <br>

电流复制，只与宽长比有关（忽略沟道效应）<br>
采取相同宽敞比的器件，通过并联串联得到复制不同的电流值<br>

## 共源共栅电流镜
考虑沟道效应，电流值与 $V_{DS}$ 有关，需要保证 $V_{DS}$ 相同。通过合理的偏置实现<br>

低功耗连接方法<br>

## 有源电流镜


五管运放的增益推导方法：分别求Gm和 Rout ，要掌握带源反馈电阻的共源极从源端看到的电阻 $R_{eq} = \frac{R_s + R_D}{1 + g_m R_s}$<br>

五管运放的大信号特性<br>

小信号特性：$A_v = g_m (r_{o2} r_{o4})$<br>

共模抑制比：与 $(g_m r_o)^2$ 成正比<br>

缺点： <br>
1. 即使没有失配CMRR也是有限的<br>
2. 电源抑制能力较差，因此改进，将M3的电流用电流镜来偏置<br>



# CH6 频率响应

## 密勒定理
适用于多通路；频率越高越不使用 <br>
密勒近似消除了零点，并预计了两个极点。 <br>
## 极点与节点关系


## 共源级
用密勒近似： <br>
输入极点直接看出 <br>
输出极点要考虑 $C_{GD}$ 和 电源内阻的阻抗大小关系 <br>
1. 当电源阻抗很小时认为短路，Vout通过 $C_{GD}$ 对输入的影响比较小，可以认为 $C_{GD}$ 开路，不会影响输入 <br>
$w_{out} = \frac{1}{R_D (C_{DB}+C_{GD})}$
1. 当电源阻抗很大时，认为开路， Vout 会通过 $C_{GD}$ 对输入有影响，附加了一个阻抗。 <br>
$w_{out} = \frac{1}{[R_D \parallel (\frac{C_{GD}+C_{GS}}{C_{GD}}\frac{1}{g_m})](C_{eq} + C_{DB})}$ <br>
$C_{eq} = \frac{1}{\frac{1}{sC_{GS}} + \frac{1}{sC_{GD}}}$ <br>

用密勒近似少了一个零点 <br>
零点分析技巧：让输出电位为0，即接地；没有电流从输出流出，通过 $C_{GD}$ 的电流与通过MOS的电流等值反向，从而求出零点。 <br>

当 $C_{DB}$ 很大时，密勒效应消失，因为从栅到漏的增益降低。

## 源级跟随器
$C_{GS}$ 没有密勒效应，因为理想源跟随器增益为1，g和s电位相同，没有电流流过 $C_{GS}$ <br>
输入阻抗包含一个负电阻，负电阻可能引起不稳定。 <br>
输出阻抗在低频时为 $\frac{1}{g_m}$ ，高频时为 $R_s$ <br>
输出阻抗随频率变化，表现出电感特性，可以用源跟随器做电感元件。 <br>

## 共栅级
共栅级没有电容密勒乘积项，可以达到高带宽。应用与要求低输入阻抗的放大器和共源共栅。<br>

## 共源共栅
没有零点

## 差动对
要增大CMRR就要减小 $C_{P}$ ，就要减小W；
但是要降低M3消耗的电压余度就要把W增大。需要折中

## 增益带宽折中
增益带宽积 $GBW=A_0 w_p$ <br>
注意这个 $w_p$ 是频率，求出的极点是角频率，需要除 $2 \pi$ 换算成频率。 <br>
同一个增益带宽积一般不变，要增大增益就必须减小带宽。 <br>

# CH7 噪声
噪声平均功率
功率谱密度
概率密度函数
相关噪声和非相关噪声
信噪比SNR，定义信号平均功率比噪声平均功率，越大越好
（放大器并不能提高信噪比，只能减少SNR的降低）

## 噪声类型
器件电子噪声和环境噪声。电子噪声分为热噪声和闪烁噪声
### 热噪声
#### 1. 电阻热噪声 <br>
来源：导体中电子的随机运动使平均电流为0，但是会引起导体两端电压波动 <br>

$S_v(f) = \overline{V_n^2} = 4kTR$ <br>
电阻热噪声为白噪声 <br>
注意： <br>
1. 电容电感并不贡献噪声 <br>
1. 增大电容可以降低噪声 <br>
1. 温度升高噪声增大 <br>

噪声模型：可以用一个无噪声电阻和一个噪声电压源串联表示，也可以用一个无噪声电阻和噪声电流源并联表示 $\overline{I_n^2} = \overline{V_n^2}/R^2$ <br>

#### 2. MOS管热噪声
来源： 沟道 <br>
$\overline{I_n^2} = 4kT \gamma g_m$ <br>
对于长沟道器件 $\gamma = \frac{2}{3}$ <br>
噪声模型：噪声电流与MOS并联，并且通过电阻可以转化为输出端的噪声电压。 <br>


### 闪烁噪声
来源：硅和二氧化硅界面的悬挂键对载流子俘获和释放，放出能量，就像在“闪烁”一样 <br>
$\overline{V_n^2} = \frac{K}{C_{ox}WLf}$ <br>
闪烁噪声不容易预测。低频下闪烁噪声更大。增加面积可以减小闪烁噪声

埋沟输运器件（如PMOS）可以减小输入噪声。因为吸硼吐磷现象让PMOS导电沟道在距离界面一定距离的地方，避免了界面态的影响。 <br>

## 输入参考噪声
输入参考噪声电压等于输出噪声电压除以增益 <br>

输入参考噪声电压并不足以表示输入参考噪声，因为这与输入阻抗和信号源内阻的大小关系有关。 <br>
当电压源的内阻相对输入阻抗很小时，输入参考噪声电压足以表示 <br>
当电压源内阻相对输入阻抗很大时，需要用输入参考噪声电流来表示 <br>
总的输入参考噪声是它们共同作用。 <br>

输入参考噪声电流求解方法： <br>
1. 将输入短路求出输入参考噪声电压
1. 将输入开路，用输入参考电流噪声用阻抗转换成加在栅上的电压后，在通过放大转换成输出噪声，输出噪声可以直接求出
1. 通过输出噪声求输入参考电流噪声 

## 折中
降低热噪声可以通过增大 $g_m$ 即增加漏电流或栅宽，或增大Rd；但是输出电压摆幅减小，功耗增加，速度降低 <br>
降低闪烁噪声可以增加栅面积同时保持W/L不变，但是减低速度，增加功耗 <br>

## 其他
共栅级的负载产生的噪声电流会反映到输入。 <br>
源跟随器将噪声叠加到输入信号，低噪声放大器应避免使用源跟随器。<br>
差动对噪声是共源级共源级的两倍<br>

# CH8 反馈
反馈系统四个部分<br>
1. 前馈放大器
1. 检测输出的方式
1. 反馈网络
1. 产生反馈误差的方式

反馈电路特性 <br>
1. 降低增益灵敏度，但是会减小增益
1. 改变终端阻抗
1. 增大带宽，但是会减小增益，增益带宽乘积不变
1. 减小非线性
1. 反馈并不会减小噪声，还可能会增加噪声


## 闭环增益
$A_c = \frac{A}{1+\beta A}$ <br>
$\beta A$ 为环路增益，要会求 <br>

## 终端阻抗
视不同的反馈类型来定
输入电压：
$R_{in,closed} = R_{in,open} (1 + \beta A)$ <br>
输入电流：
$R_{in,closed} = R_{in,open} \frac{1}{1 + \beta A}$ <br>
输出电压：
$R_{out,closed} = R_{out,open} \frac{1}{1 + \beta A}$ <br>
输出电流：
$R_{out,closed} = R_{out,open} (1 + \beta A)$ <br>



## 带宽变化
增益变为原来 $\frac{1}{1 + \beta A}$ <br>
带宽变为原来 $1 + \beta A$ 倍 <br>
但是增益减小是小问题，可以通过两个放大器级联在一起增大增益；而带宽变宽带来的速度增加足以弥补缺陷 <br>


## 放大器种类
电压放大器、跨阻放大器、跨导放大器、电流放大器

## 检测机制
电压反馈：反馈信号和输入信号接不同位置 <br>
电流反馈：反馈信号和输入信号接同一节点 <br>

## 反馈分析的困难
1. 加载效应：反馈网络对前馈放大器的影响
1. 无法明确分解出前馈放大器和反馈网络
1. 一些电路不容易映射到四种规范结构，如带源极负反馈电阻的共源极
1. 有些电路包含双向电路，允许信号从输出向输入流动
1. 包含多重反馈机制的电路



# 英语词组

## CH2
源 source<br>
漏 drain<br>
有效沟道长度 effective channel length<br>
三极管区 triode region<br>
栅电容 gate capacitance<br>
体区 bulk<br>
CMOS complementary MOS<br>
衬底 substrate<br>
过驱电压 overdrive voltage<br>
**宽长比 aspect ratio**<br>
饱和 saturation<br>
跨导 transconductance<br>
背栅效应 back-gate effect<br>
沟道长度调制系数 channel-length modulation coefficient<br>
耗尽区 depletion<br>
重叠 overlap <br>
边缘电场 fringing electric fields<br>
内建电势 built-in potential<br>
侧壁 sidewall<br>
外围 perimeter<br>
反型层 inversion layer<br>
屏蔽 shield<br>
积累 accumulation<br>
单调地 monotonically<br>


## CH3
电源电压 supply voltage          <br>
电压摆幅 voltage swings          <br>
阻抗 impedance                 <br>
导数 derivative                <br>
亚阈区导电 subthreshold conduction<br>
代价 penalty                <br>
电压余度 voltage headroom     <br>
负反馈 degeneration          <br>
推导 derive                 <br>
直观的 intuitive             <br>
消除 eliminate              <br>
迁移率 mobility              <br>
耦合 couple                 <br>
级联 cascade                <br>
拓扑 topology               <br>
套筒式共源共栅 telescopic cascode<br>
折中 trade-off              <br>
限制 constraint             <br>
劣质的共源共栅 poor man's cascode<br>
折叠式共源共栅 folded cascode <br>

## CH4
差动对 differential pair                         <br>
共模电平 common-mode level                        <br>
峰峰值 peak-to-peak swing                        <br>
抗干扰 immunity                                  <br>
差动相位 differential phases                      <br>
共模抑制 common-mode rejection                    <br>
单端电路 single-ended counterpart                 <br>
电源噪声抑制 supply noise rejection                 <br>
失真 clip                                       <br>
平衡态 equilibrium                               <br>
半边电路 half-circuit                             <br>
阻性负反馈 resistive degeneration                  <br>
承担 substains                                  <br>
并联 parallel                                   <br>
失配 mismatch                                   <br>
共模到差模转换 common-mode to differential conversion<br>
高频 high frequency <br>
寄生 parasitic<br>
共模抑制比 common-mode rejection ratio<br>
器件尺寸 device dimension<br>


## CH5
电流镜 current mirrors   <br>
基准，参考 reference       <br>
精度 accuracy           <br>
误差 inaccuracy         <br>
阈值电压 threshold voltage<br>
有源的 active <br>
超过 exceed <br>

## CH6
氧化物 oxide<br>
沟道 channel<br>
传递函数 transfer function<br>
低通滤波器 low-pass filter<br>
截止频率 cutoff frequency<br>
极点 pole<br>
零点 zero<br>
密勒近似 miller's approximation<br>
原点 origin<br>
主极点近似 dominant pole approximation<br>
一阶低通电路 first-order low-pass circuit<br>
相应端口 corresponding terminal<br>
自举 bootstrap<br>
有源电感 active inductor<br>
抑制 suppress<br>
扰动 disturbance<br>
储能元件 storage element<br>
时间常数 time constant<br>

## CH7
统计特性 statistical characteristic<br>
随机过程 random process<br>
波形 waveform<br>
功率 power<br>
归一化 normalize<br>
频谱 spectrum<br>
功率谱密度 power spectral density<br>
概率密度函数 probability denesity function<br>
信噪比 signal-to-noise ratio        <br>
正弦波 sinusoid                     <br>
**热噪声 thermal noise**                <br>
串联 series                        <br>
**集总电阻 lumped resistance**           <br>
分布栅电阻 distributed gate resistance<br>
版图 layout                  <br>
悬挂键 dangling bonds         <br>
闪烁噪声 flicker noise         <br>
输入参考噪声 input-referred noise<br>
幅值 amplitude <br>


## CH8
反馈 feedback                     <br>
前馈 feedforward                  <br>
反馈误差 feedback error             <br>
开环 open-loop                    <br>
闭环 closed-loop                  <br>
虚地 virtual ground               <br>
增益灵敏度降低 gain desensitization    <br>
定量的 quantified                  <br>
电容分压器 capacitive voltage divider<br>
不同节点 distinct node<br>
同一节点 single node  <br>
环路增益 loop gain    <br>











