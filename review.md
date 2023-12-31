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
因此增益 $A_v = g_{m1} \frac{1}{g_{m2} + g_{mb2}} = - \sqrt{\frac{(W/L)_1}{(W/L)_2}} \frac{1}{1 + \eta}$ <br>
可以看到在忽略 $\eta$ 的变化的情况下，增益只与宽长比的比值有关，即线性度提高了。 <br>
采用PMOS可以避免体效应，因此增益中不会有 $\eta$ 有关项，但是牺牲了电压余度，输出最大值为 $V_{DD} - \left| V_{GS2} \right|$ （用NMOS不会有这个问题，因为NMOS从漏到源的大信号导通压降接近0） <br>

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



# 英语词组

## CH2
源 source
漏 drain
有效沟道长度 effective channel length
三极管区 triode region
栅电容 gate capacitance
体区 bulk
CMOS complementary MOS
衬底 substrate
过驱电压 overdrive voltage
宽长比 aspect ratio
饱和 saturation
跨导 transconductance
背栅效应 back-gate effect
沟道长度调制系数 channel-length modulation coefficient
耗尽区 depletion
重叠 overlap
边缘电场 fringing electric fields
内建电势 built-in potential
侧壁 sidewall
外围 perimeter
反型层 inversion layer
屏蔽 shield
积累 accumulation

monotonically


## CH3
电源电压 supply voltage
电压摆幅 voltage swings
阻抗 impedance
导数 derivative
亚阈区导电 subthreshold conduction
代价 penalty
电压余度 voltage headroom
负反馈 degeneration
推导 derive
直观的 intuitive
消除 eliminate
迁移率 mobility
耦合 couple
级联 cascade
拓扑 topology
套筒式共源共栅 telescopic cascode
折中 trade-off
限制 constraint
劣质的共源共栅 poor man's cascode
折叠式共源共栅 folded cascode






























