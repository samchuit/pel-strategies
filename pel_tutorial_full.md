# 金字塔PEL量化编程完全教程

> 作者: 贾维斯 | 学习日期: 2026-03-10

---

## 目录

1. [基础行情函数](#1-基础行情函数)
2. [数据引用函数](#2-数据引用函数)
3. [逻辑与条件函数](#3-逻辑与条件函数)
4. [数学函数](#4-数学函数)
5. [统计函数](#5-统计函数)
6. [时间函数](#6-时间函数)
7. [字符串函数](#7-字符串函数)
8. [图表函数(交易)](#8-图表函数交易)
9. [后台函数(实盘)](#9-后台函数实盘)
10. [动态行情函数](#10-动态行情函数)
11. [账户函数](#11-账户函数)
12. [交易控制](#12-交易控制)
13. [财务函数](#13-财务函数)
14. [指标函数](#14-指标函数)
15. [画线函数](#15-画线函数)
16. [股票池函数](#16-股票池函数)
17. [自定义数据](#17-自定义数据)
18. [除权函数](#18-除权函数)
19. [全局变量](#19-全局变量)
20. [消息日志](#20-消息日志)
21. [周权函数(期权)](#21-周权函数期权)
22. [线性代数函数](#22-线性代数函数)
23. [共同特性/其他](#23-共同特性其他)

---

## 1. 基础行情函数

| 函数 | 说明 | 简写 |
|-----|------|-----|
| OPEN / O | 开盘价 | |
| HIGH / H | 最高价 | |
| LOW / L | 最低价 | |
| CLOSE / C | 收盘价 | |
| VOL / V | 成交量 | |
| AMOUNT | 成交额 | |
| OPENINT | 持仓量(期货) | |

**原始价(未复权)：**
- OOPEN, OHIGH, OLOW, OCLOSE, OAMOUNT, OVOL

**指数函数：**
- INDEXO/H/L/C/V/A - 对应大盘指数
- INDEXDAV/DEC - 市场涨跌家数
- ADVANCE/DECLINE/EQUAL - 沪深涨跌平盘家数

---

## 2. 数据引用函数

### 引用函数
| 函数 | 说明 |
|-----|------|
| REF(X,N) | 向前引用N周期 |
| REFX(X,N) | 向后引用(未来函数) |
| REFDATE(X,DATE) | 引用指定日期 |
| VALUEWHEN(COND, X) | 条件跟随 |
| RET(X,N) | 按自然日向前引用 |

### 统计函数
| 函数 | 说明 |
|-----|------|
| COUNT(X,N) | 满足条件周期数 |
| SUM(X,N) | 求和 |
| MA(X,N) | 简单移动平均 |
| EMA(X,N) | 指数平滑平均 |
| SMA(X,N,M) | 移动平均 |
| DMA(X,A) | 动态移动平均 |
| WMA(X,N) | 加权移动平均 |
| TMA(X,N,M) | 递归移动平均 |
| TRMA(X,N) | 三角移动平均 |

### 极值函数
| 函数 | 说明 |
|-----|------|
| HHV(X,N) | 最高值 |
| LLV(X,N) | 最低值 |
| HHVBARS(X,N) | 上一高点位置 |
| LLVBARS(X,N) | 上一低点位置 |
| NEWHBARS(X,N) | 创新高跨度 |
| TOPRANGE(X) | 周期内最大值排名 |
| LOWRANGE(X) | 周期内最小值排名 |

### 位置函数
| 函数 | 说明 |
|-----|------|
| BARPOS | K线顺序位置 |
| CURRBARSCOUNT | K线逆序位置 |
| BARSLAST(X) | 上次条件成立位置 |
| BARSSINCE(X) | 首次条件成立位置 |
| BARSCOUNT(X) | 有效周期数 |
| BARSLASTCOUNT(X) | 连续满足条件次数 |
| FILTER(X,N) | 信号过滤 |
| CONDBARS(A,B) | 条件A到B的周期数 |

### 其他数据函数
| 函数 | 说明 |
|-----|------|
| CROSS(A,B) | 交叉(A上穿B) |
| TR | 真实波幅 |
| WINNER(X) | 获利盘比例 |
| LWINNER(N,X) | 近期获利盘比例 |
| DRAWNULL | 无效数 |
| CATEGORY/STKTYPE | 证券类型 |
| BARSTATUS | 数据位置状态(1首/2尾/0中) |
| DATACOUNT | K线数量 |

---

## 3. 逻辑与条件函数

| 函数 | 说明 |
|-----|------|
| IF(X,A,B) | 条件选择 |
| IFELSE(X,A,B) | 条件选择 |
| CROSS(A,B) | 上穿交叉 |
| LONGCROSS(A,B,N) | 持续N周期后交叉 |
| ALL(X,N) | 是否全部满足 |
| ANY(X,N) | 是否存在满足 |
| EVERY(X,N) | 是否连续满足 |
| EXIST(X,N) | 是否存在满足 |
| BETWEEN(A,B,C) | 是否在区间 |
| RANGE(A,B,C) | 范围(A在B-C之间) |
| ISLASTBAR | 是否最后周期 |
| ISUP | 是否收阳 |
| ISDOWN | 是否收阴 |
| ISEQUAL | 是否平盘 |
| NOT(X) | 逻辑非 |
| TRUE | 真(1) |
| FALSE | 假(0) |
| VALID(X) | 是否有效数据 |
| LAST(X,A,B) | 连续A到B周期满足 |

---

## 4. 数学函数

| 函数 | 说明 |
|-----|------|
| ABS(X) | 绝对值 |
| MAX(A,B) | 最大值 |
| MIN(A,B) | 最小值 |
| SQRT(X) | 平方根 |
| POW(A,B) | 幂运算 |
| EXP(X) | E的X次方 |
| LN(X) | 自然对数 |
| LOG(X) | 10为底对数 |
| SIN(X) | 正弦 |
| COS(X) | 余弦 |
| TAN(X) | 正切 |
| ASIN(X) | 反正弦 |
| ACOS(X) | 反余弦 |
| ATAN(X) | 反正切 |
| CEILING(A) | 向上取整 |
| FLOOR(A) | 向下取整 |
| ROUND(X) | 四舍五入 |
| ROUNDS(A,B) | 指定位数四舍五入 |
| MOD(A,B) | 取模 |
| SGN(X) | 符号函数 |
| RAND(N) | 随机数 |
| REVERSE(X) | 相反数 |
| INTPART(A) | 取整数部分 |
| FRACPART(X) | 取小数部分 |
| VAR(X,N) | 方差 |
| STD(X,N) | 标准差 |
| STDP(X,N) | 总体标准差 |

---

## 5. 统计函数

| 函数 | 说明 |
|-----|------|
| SUM(X,N) | 求和 |
| AVG(X,N) | 平均值 |
| MA(X,N) | 简单移动平均 |
| EMA(X,N) | 指数移动平均 |
| STD(X,N) | 标准差 |
| VAR(X,N) | 方差 |
| MAX(X,N) | 最大值 |
| MIN(X,N) | 最小值 |

---

## 6. 时间函数

| 函数 | 说明 |
|-----|------|
| DATE | 日期(YYYYMMDD) |
| TIME | 时间(HHMMSS) |
| YEAR | 年 |
| MONTH | 月 |
| DAY | 日 |
| HOUR | 小时 |
| MINUTE | 分钟 |
| SECOND | 秒 |
| WEEKDAY | 星期几(0-6) |
| DAYOFWEEK | 星期几 |
| ISWEEKEND | 是否周末 |
| ISMONTHEND | 是否月末 |
| CURRENTDATE | 当前日期 |
| CURRENTTIME | 当前时间 |
| DATEDIFF(D1,D2) | 日期间差 |
| TRADINGDATEDIFF(D1,D2) | 交易日期差 |
| OPENMINUTES(TIME) | 开市分钟数 |
| OPENTIME(N) | 开市时间 |
| CLOSETIME(N) | 闭市时间 |
| TRADINGNODES(N) | 交易节点 |

---

## 7. 字符串函数

| 函数 | 说明 |
|-----|------|
| NUMTOSTR(N,M) | 数字转字符串 |
| STRTONUM(STR) | 字符串转数字 |
| STRLEN(STR) | 字符串长度 |
| STRCAT(DES,STR) | 字符串连接 |
| STRLEFT(STR,N) | 取左边N个字符 |
| STRRIGHT(STR,N) | 取右边N个字符 |
| STRMID(STR,N,M) | 取中间字符 |
| STRFIND(STR,S1,N) | 查找字符串位置 |
| STRCMP(STR1,STR2) | 字符串比较 |
| STRICMP(STR1,STR2) | 不区分大小写比较 |
| UPPERSTR(STR) | 转大写 |
| LOWERSTR(STR) | 转小写 |
| LTRIM(STR) | 去除左边空格 |
| RTRIM(STR) | 去除右边空格 |
| STRINSERT(STR,I,S1) | 插入字符串 |
| STRREMOVE(STR,I,C) | 删除字符串 |
| STRREPLACE(STR,OLD,NEW) | 替换字符串 |

---

## 8. 图表函数(交易)

> 用于回测/模拟交易

### 交易函数
| 函数 | 说明 |
|-----|------|
| BUY(COND, V, Type, P) | 开多 |
| BUYSHORT(COND, V, Type, P) | 开空 |
| SELL(COND, V, Type, P) | 平多 |
| SELLSHORT(COND, V, Type, P) | 平空 |

### 报单控制符
**本周(当根K执行):**
- LIMITR / PFAKR / PFOKR / MARKETR / THISCLOSE / PDBESTR / PWBESTR

**次周(下一根K执行):**
- LIMIT / PFAK / PFOK / MARKET / NEXTOPEN / PDBEST / PWBEST / STOP

### 状态查询
| 函数 | 说明 |
|-----|------|
| HOLDING | 持仓量(多正空负) |
| DAYHOLDING | 今持仓量 |
| ENTERBARS | 开仓以来周期数 |
| EXITBARS | 平仓以来周期数 |
| ENTERPRICE | 上次开仓价 |
| EXITPRICE | 上次平仓价 |
| OPENPROFIT | 浮动盈亏 |
| OPENPROFITPER | 浮动盈亏比例 |
| AVGENTERPRICE | 持仓均价 |

### 统计函数
| 函数 | 说明 |
|-----|------|
| TOTALTRADE | 总交易次数 |
| NUMWINTRADE | 盈利次数 |
| NUMLOSSTRADE | 亏损次数 |
| PERCENTWIN | 胜率 |
| AVGWIN | 平均盈利 |
| AVGLOSS | 平均亏损 |
| PayoffRate | 盈亏比 |
| MaxDrawDown | 最大回撤 |

---

## 9. 后台函数(实盘)

> 用于实盘交易

### 交易函数
| 函数 | 说明 |
|-----|------|
| TBUY(COND, V, Type, P1, P2, AC, STOCK) | 开多 |
| TBUYSHORT(COND, V, Type, P1, P2, AC, STOCK) | 开空 |
| TSELL(COND, V, Type, P1, P2, AC, STOCK) | 平多 |
| TSELLSHORT(COND, V, Type, P1, P2, AC, STOCK) | 平空 |

### 下单指令类型
- LMT: 限价
- MKT: 市价
- FOK: 全部成交或撤单
- FAK: 部分成交剩余撤单
- STP: 止损
- STPLMT: 限价止损
- DBEST: 对手方最优价
- WBEST: 本方最优价

### 账户状态
| 函数 | 说明 |
|-----|------|
| TASSET | 当前资产 |
| TCASH | 可用资金 |
| THOLDING | 可用持仓量 |
| TBUYHOLDING | 多头持仓 |
| TSELLHOLDING | 空头持仓 |
| TAVGENTERPRICE | 持仓均价 |
| TOPENPROFIT | 浮动盈亏 |
| TACCOUNT(N) | 账户信息 |

### 委托管理
| 函数 | 说明 |
|-----|------|
| TISREMAIN(N) | 是否有未成交 |
| TCANCEL(COND, N) | 撤单 |
| TSUBMIT(N) | 委托单历时 |

---

## 10. 动态行情函数

> DYNAINFO(N) - 实时盘面数据

| N | 说明 |
|---|------|
| 3 | 昨收 |
| 4 | 今开 |
| 5 | 最高 |
| 6 | 最低 |
| 7 | 最新价 |
| 8 | 总手 |
| 9 | 现手 |
| 10 | 总额(万) |
| 11 | 均价 |
| 12 | 涨跌 |
| 13 | 振幅 |
| 14 | 涨幅 |
| 15 | 委比 |
| 17 | 量比 |
| 22 | 内盘 |
| 23 | 外盘 |
| 37 | 换手率 |
| 40 | 成交方向 |
| 45 | 持仓量 |
| 54 | 涨停价 |
| 55 | 跌停价 |

**五档报价:**
- 买一~五价: 28-30, 42, 48, 49
- 买一~五量: 25-27, 41, 43, 50, 51
- 卖一~五价: 31-33, 44, 50
- 卖一~五量: 34-36, 45, 51

---

## 11. 账户函数

> TACCOUNT(N) - 账户资金信息

| N | 说明 |
|---|------|
| 1 | 账户ID |
| 2 | 账户类型 |
| 3 | 现金余额 |
| 4 | 浮动盈亏 |
| 5 | 盯市盈亏 |
| 6 | 动态权益 |
| 19 | 可用资金 |
| 20 | 流动资产 |
| 28 | 占用保证金 |
| 29 | 可取资金 |
| 30 | 平仓盈亏 |
| 31 | 手续费 |
| 41 | 多头保证金率 |
| 42 | 空头保证金率 |
| 53 | 账户是否有效 |

---

## 12. 交易控制

| 控制符 | 说明 |
|-------|------|
| PERTRADER | 资金百分比交易 |
| ORDERQUEUE | 顺序下单 |
| ALLOWREPEAT | 允许重复信号 |
| NOATTACK | 不追单 |
| FINANCING | 融资标志 |
| HEDGE | 保值标志 |
| GENERAL | 普通交易 |
| SETTRADESIGN(F) | 允许/禁止交易 |
| SLEEP(D) | 延时(毫秒) |
| RUNMODE:X | 运行模式(0逐K线/1序列) |
| ODDLOTSMODE:X | 零股交易方式 |
| TSETSTOPORDER | 动态设置止损 |

---

## 13. 财务函数

### 基础财务 FINANCE(N)
| N | 说明 |
|---|------|
| 1 | 总股本 |
| 2 | 流通股本 |
| 3 | 主营业务收入 |
| 4 | 主营业务利润 |
| 5 | 利润总额 |
| 6 | 净利润 |
| 7 | 未分配利润 |
| 8 | 资本公积金 |
| ... | (更多见文档) |

### 深度财务
| 函数 | 说明 |
|-----|------|
| FINBALANCESTD | 资产负债表 |
| FINPROFITSTD | 利润表 |
| FINCASHFLOWSTD | 现金流量表 |
| FININDICATOR | 财务指标 |
| FINCOMHOLDER | 股东人数 |
| FINHOLDERTOP10 | 十大股东 |

---

## 14. 指标函数

| 函数 | 说明 |
|-----|------|
| ZIG(K,N) | 之字转向 |
| ZIGA(X,N) | 变化率之字转向 |
| PEAK(K,N,M) | 前M个波峰值 |
| TROUGH(K,N,M) | 前M个波谷值 |
| PEAKBARS(K,N,M) | 波峰位置 |
| TROUGHBARS(K,N,M) | 波谷位置 |
| SAR(N,S,M) | 抛物转向 |

---

## 15. 画线函数

| 函数 | 说明 |
|-----|------|
| DRAWICON(COND,P,TYPE) | 绘制图标 |
| DRAWLINE(C1,P1,C2,P2,E) | 绘制直线 |
| STICKLINE(COND,P1,P2,W,E) | 绘制柱线 |
| DRAWTEXT(COND,P,TEXT) | 显示文字 |
| DRAWNUMBER(COND,P,N) | 显示数字 |
| KLINE(O,H,L,C) | 绘制K线 |
| FILLRGN(COND,P1,P2) | 区域填充 |
| POLYLINE(COND,P) | 折线 |
| PARTLINE(COND,P) | 分段线 |

---

## 16. 股票池函数

| 函数 | 说明 |
|-----|------|
| INBLOCK(S) | 是否在板块 |
| DYBLOCK | 动态板块 |
| GNBLOCK | 概念板块 |
| HYBLOCK | 行业板块 |
| STKCOUNT(BLK股票) | 板块数量 |
| BLKNAME | 板块名称 |
| ADDTOBLOCK(STK, BLK) | 添加到板块 |
| DELETEFROMBLOCK(STK, BLK) | 从板块删除 |

---

## 17. 自定义数据

| 函数 | 说明 |
|-----|------|
| SELFDATA(X) | 自定义数据 |
| SELFDATAN(N) | 序列自定义数据 |
| SELFDATAS(S) | 字符串自定义数据 |
| SELFDATALABEL(X, CODE) | 指定品种自定义数据 |

---

## 18. 除权函数

| 函数 | 说明 |
|-----|------|
| SPLIT(N) | 送转股信息 |
| DIVIDEND(N) | 分红信息 |
| SPLITBARS(N) | 送转股位置 |
| DIVIDBARS(N) | 分红位置 |
| SPLITP | 股价权息 |
| SPLITV | 成交量权息 |

---

## 19. 全局变量

### 变量类型
| 类型 | 作用域 |
|-----|-------|
| 普通变量 | 单根K线 |
| VARIABLE | 首根到最后K线 |
| GLOBALVARIABLE | 加载到停止运行 |
| EXTGBDATA | 金字塔软件范围 |
| SETREGVAL | 注册表(永久) |
| WRITEINIFILE | INI文件(永久) |

### 函数
| 函数 | 说明 |
|-----|------|
| EXTGBDATA('name') | 读取全局变量 |
| EXTGBDATASET('name', v) | 设置全局变量 |
| GETINIFILE(PATH, APP, KEY) | 读INI |
| WRITEINIFILE(PATH, APP, KEY, V) | 写INI |
| GETREGVAL(KEY, NAME, DEF) | 读注册表 |
| SETREGVAL(KEY, NAME, DATA) | 写注册表 |

---

## 20. 消息日志

### 调试输出
| 函数 | 说明 |
|-----|------|
| DEBUGFILE(PATH, STR, N) | 输出到文件(仅最后BAR) |
| DEBUGFILE2(PATH, STR, N, T) | 输出到文件(所有BAR) |
| DEBUGOUT(STR, N) | 输出到监控界面 |
| MSGOUT(COND, S) | 输出到消息栏 |

### 通知功能
| 函数 | 说明 |
|-----|------|
| SPEAK(COND, STR) | 语音播报 |
| PLAYSOUND(COND, PATH) | 播放声音 |
| SENDPHONEMSG(MSG, N) | 发送微信 |
| SENDMAIL(COND, TO, SUB, CON) | 发送邮件 |
| SENDMSG(COND, MSG, USER) | 发送消息 |

---

## 21. 周权函数(期权)

| 函数 | 说明 |
|-----|------|
| IMPLIEDVOLATILITY(N,R) | 隐含波动率 |
| OPTIONPRICE(N,R) | 期权定价 |
| OPTIONGREEKVALUE(N,r,K) | 期权希腊值 |
| OPTIONSIZE(CODE,MONTH,TYPE) | 期权合约数量 |
| OPTIONLABEL(N) | 期权合约代码 |
| TSTATE | 账户状态 |
| TSTRIKE | 期权下单 |

---

## 22. 线性代数函数

基于OpenBLAS的矩阵运算:

| 函数 | 说明 |
|-----|------|
| MFADD | 矩阵加法 |
| MFSUB | 矩阵减法 |
| MFMUL | 矩阵乘法 |
| MFDOT | 向量点积 |
| MFSUM | 矩阵元素和 |
| MFAMAX | 最大值位置 |
| MFAMIN | 最小值位置 |
| MFNORM2 | 向量范数 |

---

## 23. 共同特性/其他

### 市场信息
| 函数 | 说明 |
|-----|------|
| MARKETLABEL | 市场代码(SH/SZ) |
| MARKETNAME | 市场名称 |
| STKLABEL | 股票代码 |
| STKNAME | 股票名称 |
| STKINDI | 引用指标 |
| MINDIFF | 最小变动价位 |
| MULTIPLIER | 合约乘数 |

### 共同特性
| 函数 | 说明 |
|-----|------|
| FORMULANAME | 公式名称 |
| STKFROMBLK | 取板块内股票 |
| TINSORT | 板块内排序 |

---

## 附录: 常用代码示例

### 均线交叉策略
```
MA5 := MA(CLOSE, 5);
MA20 := MA(CLOSE, 20);

开多条件 := CROSS(MA5, MA20);
平多条件 := CROSS(MA20, MA5);

BUY(开多条件, 1, LIMITR, CLOSE);
SELL(平多条件, 1, LIMITR, CLOSE);
```

### 资金百分比开仓
```
TBUY(CROSS(MA5,MA20), 50%, MKT), PERTRADER;
```

### 账户全平
```
HC := THOLDCOUNT('');
FOR I := 1 TO HC DO
BEGIN
    HLABEL := THOLDINDEXLABEL(I, '');
    THC := TBUYHOLDINGEX('', HLABEL, 1);
    TSELL(THC>0, THC, MKT, 0, 0, '', HLABEL),ALLOWREPEAT;
END
```

### 调试输出
```
IF ISLASTBAR THEN
    DEBUGFILE('D:\log.txt', '资产:%.2f', ASSET);
```

---

*教程整理: 贾维斯*
*日期: 2026-03-10*
