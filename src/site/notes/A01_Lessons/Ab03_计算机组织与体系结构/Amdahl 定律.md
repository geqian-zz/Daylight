---
{"dg-publish":true,"aliases":["阿姆达尔定律"],"tags":["1_AtomNote"],"number headings":"auto, first-level 1, max 6, A.1.","Created-Date":"2024-02-28 11:28:54","Modified-Date":"2024-04-18 11:53:23","permalink":"/A01_Lessons/Ab03_计算机组织与体系结构/Amdahl 定律/","dgPassFrontmatter":true}
---



# A. Amdahl 定律的基本内容

计算机系统中某一部件由于采用某种更快的执行方式后，整个系统性能的提高与这种执行方式的使用频率或占总执行时间的比例有关。


![Pasted image 20240228113050.png](/img/user/Z02_ObFiles/Attachments/Pasted%20image%2020240228113050.png)



- 可改进比例 $f_e$
- 部件加速比 $r_e$

![Pasted image 20240228115639.png|400](/img/user/Z02_ObFiles/Attachments/Pasted%20image%2020240228115639.png)

$$
T_n=T_o\left(1-f_e+\frac{f_e}{r_e}\right)
$$


	