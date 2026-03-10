// =====================================================
// 螺纹钢/铁矿石 均线交叉策略
// 适用品种: 螺纹钢(RB), 铁矿石(I)
// 周期: 15分钟/30分钟/1小时
// =====================================================

// ---------- 策略参数 ----------
N1 := 5;        // 短期均线周期
N2 := 20;       // 长期均线周期
止损P := 2;      // 止损百分比(%)
止盈P := 4;      // 止盈百分比(%)
手数 := 1;       // 开仓手数

// ---------- 计算均线 ----------
MA1 := MA(CLOSE, N1);   // 短期均线
MA2 := MA(CLOSE, N2);   // 长期均线

// ---------- 交易条件 ----------
金叉 := CROSS(MA1, MA2);    // 短期上穿长期 -> 买入信号
死叉 := CROSS(MA2, MA1);    // 短期下穿长期 -> 卖出信号

// ---------- 过滤信号(避免频繁交易) ----------
// 过滤: 连续5根K线内不重复信号
金叉过滤 := FILTER(金叉, 5);
死叉过滤 := FILTER(死叉, 5);

// ---------- 止损止盈条件 ----------
多头止损 := (CLOSE - ENTERPRICE) / ENTERPRICE * 100 < -止损P AND HOLDING > 0;
多头止盈 := (CLOSE - ENTERPRICE) / ENTERPRICE * 100 > 止盈P AND HOLDING > 0;
空头止损 := (ENTERPRICE - CLOSE) / ENTERPRICE * 100 < -止损P AND HOLDING < 0;
空头止盈 := (ENTERPRICE - CLOSE) / ENTERPRICE * 100 > 止盈P AND HOLDING < 0;

// ---------- 交易执行 ----------
// 先平仓后开仓(顺序下单)
SELL(死叉过滤 OR 多头止损 OR 多头止盈, 1, LIMITR, CLOSE);
BUY(金叉过滤 AND HOLDING = 0, 手数, LIMITR, CLOSE);

BUYSHORT(死叉过滤 AND HOLDING = 0, 手数, LIMITR, CLOSE);
SELLSHORT(死叉过滤 OR 空头止损 OR 空头止盈, 1, LIMITR, CLOSE);

// ---------- 输出显示 ----------
DRAWTEXT(ISLASTBAR, LOW, 'MA5:' + NUMTOSTR(MA1, 2)), COLORYELLOW;
DRAWTEXT(ISLASTBAR, LOW*0.98, 'MA20:' + NUMTOSTR(MA2, 2)), COLORYELLOW;

当前持仓:HOLDING, COLORGRAY, LINETHICK0;
持仓均价:AVGENTERPRICE, COLORGRAY, LINETHICK0;
浮动盈亏:OPENPROFIT, COLORGRAY, LINETHICK0;
浮动盈亏%:OPENPROFITPER, COLORGRAY, LINETHICK0;

// 绘制均线
MA(CLOSE, N1), COLORRED;
MA(CLOSE, N2), COLORBLUE;

// =====================================================
// 策略说明:
// 1. 金叉(MA5上穿MA20) -> 做多
// 2. 死叉(MA5下穿MA20) -> 做空
// 3. 止损: 亏损2%自动止损
// 4. 止盈: 盈利4%自动止盈
// 5. FILTER函数避免5根K线内重复信号
// =====================================================
