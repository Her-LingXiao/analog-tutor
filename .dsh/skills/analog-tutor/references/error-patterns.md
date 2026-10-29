# 模电高频错误模式

每条按“错误现象 → 归因标签 → 修正动作”组织。标签只用六个：concept、sop、formula、circuit、state、calculation。

| 错误现象 | 归因标签 | 修正动作 |
|---|---|---|
| 电容在交流通路中未短路 | circuit | 重画交流通路，逐电容判断 |
| r_be 中 I_EQ 用 μA 代入 | formula | 统一换算为 mA 再代入 |
| 共射 A_u 丢负号 | formula | 显式写出负号，并与相位或仿真核对 |
| 运放题默认虚短虚断，实际处于非线性区 | state | 先判负反馈是否存在，再决定用虚短还是比较器 |
| 反馈极性判断跳步 | sop | 强制走“瞬时极性法”三步：设正、逐级标、回输入端 |
| 分压偏置不验算 I_1 ≫ I_BQ 就套 U_BQ 公式 | concept | 先估 I_BQ，确认旁路电流足够大 |
| 共集 R_o 直接写成 R_e | formula | 补上 (r_be+R_b∥R_s)/(1+β) 的并联 |
| 共基 R_i 写成 R_e∥r_be | formula | 除以 (1+β) 后再并联 |
| 长尾差分 I_0 不除以 2 | formula | I_CQ1 = I_CQ2 = I_0/2 |
| 双端输出带载用 R_L 而非 R_L/2 | circuit | 画差模半边电路，确认负载折半 |
| CMRR 把倍数当 dB | calculation | 用 20lg 换算并标明单位 |
| OCL 与 OTL 的 U_om 混用 | formula | 先确认单/双电源，再选 V_CC 或 V_CC/2 |
| 功率管耗按总功耗算 | formula | 单管 P_T = (P_V−P_o)/2 |
| 效率计算忽略 U_CES 却不声明 | concept | 写明“忽略 U_CES”的近似条件 |
| 振荡器只验幅度不验相位 | sop | 逐级算 A、F 相移，确认 2nπ |
| 文氏桥起振条件漏掉 F=1/3 | formula | 起振要求 A > 3，即 R_f/R_1 > 2 |
| 稳压电源 U_2 用峰值代入 | concept | 用副边有效值，峰值另算 |
| 桥式整流二极管电流按 I_L 选 | circuit | 每管导通半周，I_D = I_L/2 |
| 输出已触轨仍按线性公式给结果 | state | 先与 ±U_om 比较，触轨则改按非线性处理 |
| 单位混用（kΩ 与 Ω、mA 与 A） | calculation | 统一到 SI 或统一到 mA/V/kΩ 后再回代 |
| 直流通路里把旁路电容当短路 | circuit | 直流分析时所有电容开路 |
| 共射 R_i 漏掉偏置电阻 | formula | R_i = R_b∥r_be，R_b = R_b1∥R_b2 |
| 单端输出差分增益漏掉 1/2 | formula | A_ud1 = −β(R_c∥R_L)/(2r_be) |
| 三点式振荡器判据用错 | concept | 按“射同基反”核对两个电抗元件的性质 |
| 题目只给端口数据，却硬套内部 Q 点 SOP | sop | 先盘点已知信息；黑箱题改列端口叠加方程，不凑内部参数 |
| 多级放大直接套单级增益公式 | sop | 拆成单级，级间用前级 R_o 与后级 R_i 衔接 |
