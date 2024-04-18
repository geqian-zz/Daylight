---
{"dg-publish":true,"aliases":[null],"tags":["1_AtomNote"],"number headings":"auto, first-level 1, max 6, A.1.","Created-Date":"2024-04-06 14:51:58","Modified-Date":"2024-04-18 11:53:18","permalink":"/A01_Lessons/Ac03_模电_模拟电子技术基础/PN结/","dgPassFrontmatter":true}
---



# A. PN 结

## A.1. PN 结的形成


![Pasted image 20240406152220.png](/img/user/Z02_ObFiles/Attachments/Pasted%20image%2020240406152220.png)

- **自建场的形成**
	- 多子的扩散
- **自建场的特点**
	- 无载流子
	- 阻碍多子的扩散
	- 促进少子的漂移
- **PN 结的形成**
	- 多子扩散和少子漂移的动态平衡




## A.2. PN 结的实质


$$PN结=空间电荷区=耗尽层=内电场=电阻$$



# B. PN 结的单向导电性



![Pasted image 20240406153316.png](/img/user/Z02_ObFiles/Attachments/Pasted%20image%2020240406153316.png)


- PN 结的单向导电性
	- 正向偏置 -> 削弱自建场 -> 低阻
	- 反向偏置 -> 增强自建场 -> 高阻


![Pasted image 20240406153912.png|300](/img/user/Z02_ObFiles/Attachments/Pasted%20image%2020240406153912.png)




# C. PN 结的伏安特性

![Pasted image 20240406155552.png|300](/img/user/Z02_ObFiles/Attachments/Pasted%20image%2020240406155552.png)



$$
I_D=I_S\left(e^\frac{u}{U_T}-1\right)
$$


- $I_D$ -> 流过 PN 结的电流
- $I_{\mathrm{S}}$ -> 反向饱和电流
- $u$ -> 结电压
- $U_{T}$ -> 温度的电压当量

$$
U_T=\frac{k T}{q}
$$

- $k$ -> 波耳次曼常数 $(1.381 * 10^{-3} \mathrm{~J} / \mathrm{k})$
- $T$ -> 为绝对工作温度
- $\mathrm{q}$ -> 为电子电荷量 $1.6*10^{-19}$ $\mathrm{C}$

$$
\begin{gathered}
T=300K\left(27^{\circ} \mathrm{C}\right)~~~->~~~
U_T=26 \mathrm{mV}
\end{gathered}
$$








## C.1. PN 结的反向击穿

- 电击穿
- 热击穿
- **雪崩击穿**
	- 条件：反向电压足够高
	- 过程：反向电场使电子加速，动能增大，撞击使自由电子数突增
- **齐纳击穿**
	- 条件：杂质浓度高
	- 过程：反向电场太强，将电子强行拉出共价键  **(击穿电压 < 6V)**





# D. PN 结的电容效应
势垒电容 $C_{\mathrm{T}}$ 和扩散电容 $C_{\mathrm{D}}$ 均是非线性电容。
$\mathrm{P} \mathrm{N}$ 结的结电容 $C_{\mathrm{j}}$ 包括两部分, 即:
$$
C_{\mathrm{j}}=C_{\mathrm{T}}+C_{\mathrm{D}}
$$
$\mathrm{PN}$ 结正偏时, 扩散电容起主要作用
$$
C_{\mathrm{j}} \approx C_{\mathrm{D}}
$$

当 $\mathrm{P} \mathrm{N}$ 结反偏时, 势垒电容起主要作用
$$
C_{\mathrm{j}} \approx C_{\mathrm{T}}
$$




