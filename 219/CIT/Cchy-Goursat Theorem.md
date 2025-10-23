**面对一个复杂的围线积分，不要急着动手去计算，首先要检查函数和路 径是否满足柯西积分定理的条件。如果满足，答案可能直接就是零！**

---

### 1. 围线 C 的分析 (Analysis of the Contour C)

*   **描述 (Description):** $C$ 是**单位正方形 (unit square)** 的边界。这个正方形的四个顶点分别是 $0, 1, 1+i, i$。
*   **性质 (Properties):** 这条路径 $C$ 是一条**简单闭合围线 (simple closed contour)**。
    *   **简单 (Simple):** 它自身没有交叉。
    *   **闭合 (Closed):** 它从起点 $0$ 出发，最终回到了起点 $0$。
    *   **围线 (Contour):** 它是由四条光滑的直线段（分段光滑, piecewise smooth）组成的。
*   **参数化 (Parameterization):** 例子中给出了构成 $C$ 的四条路径 $\gamma_1, \gamma_2, \gamma_3, \gamma_4$ 的参数化方程，我们来验证一下：
    *   $\gamma_1(t) = t$, for $t \in$: 当 $t$ 从 $0$ 变到 $1$ 时, $z$ 从 $0$ 变到 $1$。这是从 $0$ 到 $1$ 的底边。
    *   $\gamma_2(t) = 1 + ti$, for $t \in$: 当 $t$ 从 $0$ 变到 $1$ 时, $z$ 从 $1$ 变到 $1+i$。这是从 $1$ 到 $1+i$ 的右边。
    *   $\gamma_3(t) = (1-t) + i$, for $t \in$: 当 $t$ 从 $0$ 变到 $1$ 时, $z$ 从 $1+i$ 变到 $i$。这是从 $1+i$ 到 $i$ 的顶边（注意方向是向左）。
    *   $\gamma_4(t) = (1-t)i$, for $t \in$: 当 $t$ 从 $0$ 变到 $1$ 时, $z$ 从 $i$ 变到 $0$。这是从 $i$ 到 $0$ 的左边（注意方向是向下）。

这四条路径合在一起，==构成了沿**逆时针方向 (counter-clockwise)** 遍历的单位正方形边界。在复分析中，逆时针方向通常被定义为**正方向 (positive orientation)**。==

---

### 2. 函数 f(z) 的分析 (Analysis of the Function f(z))

*   **函数 (Function):** $f(z) = \sin(z^2)$。
*   **关键问题：这个函数在哪里是解析的 (analytic)？**
    *   我们知道函数 $g(z) = z^2$ 是一个多项式，它在整个复平面 $\mathbb{C}$ 上都是解析的。
    *   我们还知道函数 $h(w) = \sin(w)$ 在整个复平面 $\mathbb{C}$ 上也是解析的。
    *   **解析函数的复合仍然是解析函数**。因此，$f(z) = h(g(z)) = \sin(z^2)$ 在整个复平面 $\mathbb{C}$ 上都是解析的。
*   **专业术语：** 一个在整个复平面上都解析的函数被称为**整函数 (entire function)**。所以，$f(z) = \sin(z^2)$ 是一个整函数。

---

### 3. 柯西-古尔萨定理 (Cauchy-Goursat Theorem)

*   **柯西积分定理 (Cauchy's Integral Theorem) - 初始版本**
    *   **条件**: 函数 $f(z)$ 在一个单连通区域 $D$ 内是全纯的 (holomorphic)，**并且其导数 $f'(z)$ 在 $D$ 内是连续的**。
    *   **结论**: 对于 $D$ 内的任何简单闭合曲线 $\gamma$，有 $\oint_{\gamma} f(z)dz = 0$。
    *   **证明方法**: 正是你图片中展示的方法。这个证明依赖于**格林公式 (Green's Theorem)**。而格林公式本身要求被积函数的偏导数是连续的，这正好对应了 "$f'(z)$ 连续" 这个条件。

*   **柯西-古尔萨定理 (Cauchy-Goursat Theorem) - 加强版/现代版**
    *   **条件**: 函数 $f(z)$ 在一个单连通区域 $D$ 内是全纯的 (holomorphic)。 **(没有对 $f'(z)$ 的额外要求)**
    *   **结论**: 对于 $D$ 内的任何简单闭合曲线 $\gamma$，有 $\oint_{\gamma} f(z)dz = 0$。
    *   **证明方法**: 这个证明要复杂得多，由数学家古尔萨 (Goursat) 提出。它不使用格林公式，而是通过将区域不断细分成无限小的矩形或三角形来直接证明，从而**避免了使用 "$f'(z)$ 连续" 这个条件**。

---


### **总结一下：**

| 特性 (Feature) | 柯西积分定理 (CIT)                      | 柯西-古尔萨定理 (CGT)                |
| :----------- | :-------------------------------- | :---------------------------- |
| **提出者**      | 柯西 (Cauchy)                       | 柯西 (Cauchy)，由古尔萨 (Goursat) 完善 |
| **核心条件**     | $f(z)$ 全纯 **且 $f'(z)$ 连续**        | $f(z)$ 全纯                     |
| **典型证明**     | 使用格林公式                            | 古尔萨的证明 (不依赖格林公式)              |
| **现代观点**     | 是CGT的一个特例，但由于“全纯必导致导数连续”，两者实际上等价。 | **现代标准版本**，是复分析的基石。           |

---


### 4. 将定理应用于本例 (Applying the Theorem to the Example)

现在，我们把所有部分组合起来：

1.  **路径 C：** 是一个简单闭合围线。 (满足条件)
2.  **函数 f(z) = sin(z²):** 是一个整函数，意味着它在**整个复平面**上都是解析的。
3.  **检查条件：** 因为 $f(z)$ 在整个复平面上都解析，所以它必然在单位正方形的边界 $C$ 上以及其内部区域 $D$ 的每一点都是解析的。 (满足条件)

**结论 (Conclusion):**
因为函数 $f(z)$ 和路径 $C$ 完全满足柯西-古尔萨定理的所有条件，我们可以**直接得出结论**：

$\oint_C \sin(z^2) dz = 0$


### 5.证明步骤详解 (Step-by-Step Breakdown of the Proof)

我们来逐行解读图片中的推导：

#### 1. **初始设定 (Initial Setup)**

   首先设定积分路径 $\gamma$ 的方向。==在复分析中，我们通常默认闭合路径是**正向的 (positively oriented)**，也就是逆时针方向。当你沿着曲线走的时候，曲线所包围的区域 $D$ 总是在你的左手边。这是一个应用格林公式 (Green's Theorem) 的标准约定。==

*   **`Write f(z) = u(x, y) + iv(x, y), γ(t) = x(t) + iy(t).`**
    *   这是证明的标准准备工作。我们将复数的所有部分都用其实部 (real part) 和虚部 (imaginary part) 来表示。
    *   复变函数 $f(z)$ 被写成 $u(x, y) + iv(x, y)$，其中 $u$ 和 $v$ 都是关于 $x$ 和 $y$ 的实值函数。
    *   路径 $\gamma$ 被参数化 (parameterized) 为 $\gamma(t) = x(t) + iy(t)$，其中 $t$ 是一个实数参数，从 $a$ 变化到 $b$。

#### 2. **展开围线积分 (Expanding the Contour Integral)**

*   **`Then ∫γ f(z)dz = ∫a^b f(γ(t))γ'(t)dt`**
    *   这是复数围线积分的定义。我们将关于 $z$ 的积分转换为了关于实数参数 $t$ 的定积分。其中 $\gamma'(t) = \frac{d\gamma}{dt} = x'(t) + iy'(t)$。

*   **`= ∫a^b [ (ux' - vy') + i(uy' + vx') ] dt`**
    *   这一步是把上一行的表达式完全展开。我们来演算一下：
        *   $f(\gamma(t)) = u(x(t), y(t)) + iv(x(t), y(t))$
        *   $\gamma'(t) = x'(t) + iy'(t)$
        *   两者相乘：$f(\gamma(t))\gamma'(t) = (u + iv)(x' + iy') = (ux' + iuy' + ivx' + i^2vy') = (ux' - vy') + i(uy' + vx')$。
    *   推导完全正确，这一步只是简单的复数乘法。

#### 3. **转换为实数线积分 (Rewriting in Terms of Real Line Integrals)**

*   **`Rewrite in terms of line integrals → = ∫γ udx - vdy + i∫γ udy + vdx`**
    *   这一步非常关键，它将一个复数积分分成了两个实数的线积分 (line integrals)。
    *   ==我们知道在线积分中，$dx = x'(t)dt$ 且 $dy = y'(t)dt$。==
    *   ==我们看上一行的实部：==$\int_a^b (ux' - vy')dt = \int_a^b (u \cdot x'(t)dt - v \cdot y'(t)dt) = \int_{\gamma} udx - vdy$。
    *   再看虚部：$\int_a^b (uy' + vx')dt = \int_a^b (u \cdot y'(t)dt + v \cdot x'(t)dt) = \int_{\gamma} udy + vdx$。
    *   所以，原积分被成功地分成了两个我们在线性代数或多元微积分中熟悉的线积分。

#### 4. **应用格林公式 (Applying Green's Formula)**

*   **` = ∬D (-vx - uy) dxdy + i∬D (ux - vy) dxdy`**
    *   这是整个证明的核心步骤。这里用到了**格林公式 (Green's Theorem)**，我们来回顾一下：
        > 对于一个正向的简单闭合曲线 $C$ 和它所包围的区域 $D$，==如果有函数 $P(x,y)$ 和 $Q(x,y)$ 在 $D$ 上有一阶连续偏导数==，那么：
        > $$ \oint_C Pdx + Qdy = \iint_D (\frac{\partial Q}{\partial x} - \frac{\partial P}{\partial y}) dxdy $$

    *   现在我们把格林公式应用到上一步的两个线积分上：
        1.  对于第一个积分 $\int_{\gamma} udx - vdy$：这里 $P=u$，$Q=-v$。
            *   应用格林公式：$\iint_D (\frac{\partial(-v)}{\partial x} - \frac{\partial u}{\partial y}) dxdy = \iint_D (-v_x - u_y) dxdy$。（这里 $v_x$ 代表 $\frac{\partial v}{\partial x}$）
        2.  对于第二个积分 $\int_{\gamma} vdx + udy$：这里 $P=v$，$Q=u$。
            *   应用格林公式：$\iint_D (\frac{\partial u}{\partial x} - \frac{\partial v}{\partial y}) dxdy = \iint_D (u_x - v_y) dxdy$。
    *   将这两个结果带回，就得到了图片中的这一行，推导无误。

#### 5. **使用柯西-黎曼方程 (Using Cauchy-Riemann Equations)**

*   **`C-R equitions → = 0. Q.E.D.`**
    *   这是临门一脚！定理的前提条件是函数 $f(z)$ 是**全纯的 (holomorphic)**。一个函数全纯，意味着它必须满足**柯西-黎曼方程 (Cauchy-Riemann Equations, C-R equations)**：
        > $$ \frac{\partial u}{\partial x} = \frac{\partial v}{\partial y} \quad (u_x = v_y) $$
        > $$ \frac{\partial u}{\partial y} = -\frac{\partial v}{\partial x} \quad (u_y = -v_x) $$
    *   现在我们将 C-R 方程代入到上一步得到的两个二重积分 (double integrals) 中：
        1.  第一个积分的被积函数是 $(-v_x - u_y)$。根据 C-R 方程，我们有 $u_y = -v_x$，所以 $-v_x - u_y = -v_x - (-v_x) = 0$。
        2.  第二个积分的被积函数是 $(u_x - v_y)$。根据 C-R 方程，我们有 $u_x = v_y$，所以 $u_x - v_y = u_x - u_x = 0$。
    *   既然两个二重积分的被积函数都恒等于零，那么这两个积分的结果自然就是 0。
    *   因此，总的结果是 $0 + i \cdot 0 = 0$。