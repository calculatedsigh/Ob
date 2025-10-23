
问题点在于，我们验证一个函数是否是解的时候，需要做两件事：
1.  验证它是否满足**微分方程 (differential equation)** 本身，即 $x'(t) = 2\sqrt{|x(t)|}$。
2.  验证它是否满足**初始条件 (initial condition)**，即 $x(0) = 0$。

你的困惑主要出在第二点，我们先来解决它。

### 1. 验证初始条件 (Verifying the Initial Condition)

你问：“我把x=0代入t-a那个和t-b那个都得不到0啊？”

这里的关键在于，我们应该代入的是**自变量 (independent variable)** $t=0$，然后看**函数值 (function value)** $x(0)$ 是不是等于0。

我们来看这个分段函数 (piecewise function) 的定义：
$x(t) = \begin{cases} -(t-a)^2 & \text{if } t < a \\ 0 & \text{if } a \le t \le b \\ (t-b)^2 & \text{if } t > b \end{cases}$

题目给定的条件是 $a \le 0 \le b$。
==现在，我们要计算 $x(0)$，也就是当 $t=0$ 时的函数值。根据条件 $a \le 0 \le b$，自变量 $t=0$ 正好落在了中间那个区间 $[a, b]$ 里。==

所以，我们应该使用中间那条规则来计算 $x(0)$：
当 $a \le t \le b$ 时，$x(t) = 0$。
因此，当 $t=0$ 时，我们得到 $x(0) = 0$。

==这就证明了，这个函数是满足初始条件的。你不需要把 $t=0$ 代入第一条或第三条规则，因为 $t=0$ 并不在它们的定义域里（$0$ 不小于 $a$，也不大于 $b$）。==

---

### 2. 验证微分方程 (Verifying the Differential Equation)

为了完整性，我们再来验证这个函数确实满足微分方程 $x'(t) = 2\sqrt{|x(t)|}$。我们需要对每一段分别求导。

**情况一：当 $t < a$ 时**
*   $x(t) = -(t-a)^2$
*   左边 (LHS): $x'(t) = \frac{d}{dt}[-(t-a)^2] = -2(t-a) = 2(a-t)$
*   右边 (RHS): $2\sqrt{|x(t)|} = 2\sqrt{|-(t-a)^2|} = 2\sqrt{(t-a)^2} = 2|t-a|$
*   因为 $t < a$，所以 $t-a$ 是负数，因此 $|t-a| = -(t-a) = a-t$。
*   所以，右边 (RHS) $= 2(a-t)$。
*   LHS = RHS，方程成立。

**情况二：当 $a < t < b$ 时**
*   $x(t) = 0$
*   左边 (LHS): $x'(t) = \frac{d}{dt}(0) = 0$
*   右边 (RHS): $2\sqrt{|x(t)|} = 2\sqrt{|0|} = 0$
*   LHS = RHS，方程成立。

**情况三：当 $t > b$ 时**
*   $x(t) = (t-b)^2$
*   左边 (LHS): $x'(t) = \frac{d}{dt}[(t-b)^2] = 2(t-b)$
*   右边 (RHS): $2\sqrt{|x(t)|} = 2\sqrt{|(t-b)^2|} = 2\sqrt{(t-b)^2} = 2|t-b|$
*   因为 $t > b$，所以 $t-b$ 是正数，因此 $|t-b| = t-b$。
*   所以，右边 (RHS) $= 2(t-b)$。
*   LHS = RHS，方程成立。

**关键点：连接处的导数**
==我们还需要检查在连接点 $t=a$ 和 $t=b$ 处，导数是否平滑过渡。==
*   在 $t=a$ 处：
    *   左导数 (from case 1): $\lim_{t \to a^-} x'(t) = \lim_{t \to a^-} 2(a-t) = 0$
    *   右导数 (from case 2): $\lim_{t \to a^+} x'(t) = \lim_{t \to a^+} 0 = 0$
    *   左右导数相等，所以 $x'(a)=0$。方程 $x'(a) = 2\sqrt{|x(a)|}$ 变为 $0 = 2\sqrt{|0|}$，成立。
*   在 $t=b$ 处：
    *   左导数 (from case 2): $\lim_{t \to b^-} x'(t) = \lim_{t \to b^-} 0 = 0$
    *   右导数 (from case 3): $\lim_{t \to b^+} x'(t) = \lim_{t \to b^+} 2(t-b) = 0$
    *   左右导数相等，所以 $x'(b)=0$。方程 $x'(b) = 2\sqrt{|x(b)|}$ 变为 $0 = 2\sqrt{|0|}$，成立。

综上所述，这个分段函数在整个定义域上都满足微分方程。

### 为什么解不唯一？(Why is the solution not unique?)

### 根本原因：不满足利普希茨条件 (Root Cause: Not Lipschitz Continuous)

正如讲义中提到的，函数 $f(x) = 2\sqrt{|x|}$ 在 $x=0$ 附近不满足**利普希茨条件 (Lipschitz condition)**。

==利普希茨条件要求存在一个常数 $L$，使得 $|f(x_1) - f(x_2)| \le L|x_1 - x_2|$。==
==我们来检验一下，令 $x_2 = 0, x_1 > 0$：==
==$|2\sqrt{x_1} - 2\sqrt{0}| \le L|x_1 - 0|$==
==$2\sqrt{x_1} \le L x_1$==
==$L \ge \frac{2\sqrt{x_1}}{x_1} = \frac{2}{\sqrt{x_1}}$==

==当 $x_1 \to 0^+$ 时，$\frac{2}{\sqrt{x_1}} \to \infty$。这意味着我们无法找到一个**有限的 (finite)** 常数 $L$ 在包含0的区间上满足这个条件。==

正是因为在初始点 $x(0)=0$ 处不满足利普希茨条件，我们之前学习的**皮卡-林德洛夫存在唯一性定理 (Picard-Lindelöf existence and uniqueness theorem)** 的唯一性部分的前提就不成立了，从而导致了解的不唯一。

