同学，你问到了一个非常经典且深刻的问题！这个问题完美地揭示了实变函数 (real-valued functions) 和复变函数 (complex-valued functions) 之间一个令人惊讶的巨大差异。

我们从中学到大学微积分，脑海里根深蒂固的印象就是 $\sin(x)$ 和 $\cos(x)$ 是有界函数 (bounded functions) 的典范，它们的值域永远被限制在 $[-1, 1]$ 这个“盒子”里。

然而，一旦我们把定义域从实轴 $\mathbb{R}$ 扩展到整个复平面 $\mathbb{C}$，这个“盒子”就被彻底打破了。

---

### **核心思路：从定义出发，寻找“失控”的来源 (The Core Strategy: Find the Source of Unboundedness in the Definition)**

要证明一个函数 $f(z)$ 是**无界的 (unbounded)**，我们的目标是证明它的**模 (modulus)** $|f(z)|$ 可以变得任意大。也就是说，无论你给我一个多大的正数 $M$（比如 $10^{100}$），我总能找到一个复数 $z$，使得 $|f(z)| > M$。

那么，我们怎么找到这个 $z$ 呢？关键在于复变三角函数的定义。它们不是通过几何定义的，而是通过**欧拉公式 (Euler's formula)** 和指数函数来定义的。

有两个等价的定义非常有用：

1.  **指数定义 (Exponential Definition):**
    $\sin(z) = \frac{e^{iz} - e^{-iz}}{2i}$
    $\cos(z) = \frac{e^{iz} + e^{-iz}}{2}$

2.  **双曲函数定义 (Hyperbolic Function Definition):**
    当 $z = x+iy$ 时，利用和角公式可以展开：
    $\sin(z) = \sin(x+iy) = \sin(x)\cosh(y) + i\cos(x)\sinh(y)$
    $\cos(z) = \cos(x+iy) = \cos(x)\cosh(y) - i\sin(x)\sinh(y)$

    其中，$\cosh(y) = \frac{e^y + e^{-y}}{2}$ 和 $\sinh(y) = \frac{e^y - e^{-y}}{2}$ 是双曲余弦和双曲正弦函数。

**突破口就在这里！**
我们知道 $\sin(x)$ 和 $\cos(x)$ 是有界的。但是，双曲函数 $\cosh(y)$ 和 $\sinh(y)$ 随着 $|y|$ 的增大是**指数级增长**的！当 $y \to \infty$ 时，它们都趋向于 $\infty$。这就是我们要利用的“失控”的来源。

我们的策略就是：**固定实部 $x$ 来控制 $\sin(x)$ 和 $\cos(x)$ 的值，然后让虚部 $y$ 趋向无穷大，来引爆双曲函数。**

---

### **详细证明 (Detailed Proof)**

我们以 $\sin(z)$ 为例进行详细证明。

**第一步：计算 $|\sin(z)|$ 的表达式**

我们使用双曲函数定义来计算 $\sin(z)$ 的模的平方：
$|\sin(z)|^2 = |\sin(x)\cosh(y) + i\cos(x)\sinh(y)|^2$

根据复数模的定义 $|a+ib|^2 = a^2 + b^2$：
$|\sin(z)|^2 = (\sin(x)\cosh(y))^2 + (\cos(x)\sinh(y))^2$
$|\sin(z)|^2 = \sin^2(x)\cosh^2(y) + \cos^2(x)\sinh^2(y)$

为了简化这个表达式，我们使用恒等式 $\cosh^2(y) = 1 + \sinh^2(y)$ 和 $\sin^2(x) + \cos^2(x) = 1$。
$|\sin(z)|^2 = \sin^2(x)(1 + \sinh^2(y)) + \cos^2(x)\sinh^2(y)$
$= \sin^2(x) + \sin^2(x)\sinh^2(y) + \cos^2(x)\sinh^2(y)$
$= \sin^2(x) + (\sin^2(x) + \cos^2(x))\sinh^2(y)$
$= \sin^2(x) + \sinh^2(y)$

这是一个非常优美且关键的结果！$|\sin(z)|^2 = \sin^2(x) + \sinh^2(y)$。

**第二步：构造一个路径使 $|\sin(z)|$ 趋向无穷**

现在我们有了这个简化的表达式，事情就变得很简单了。
*   $\sin^2(x)$ 这一项总是在 $$ 之间，是有界的。
* $\sinh^2(y)$ 这一项，当 $y \to \infty$ 或 $y \to -\infty$ 时，它会趋向于 $\infty$。

所以，我们可以选择一条特定的路径，例如，沿着一条垂直线移动。
我们固定实部 $x$，比如取 $x = \frac{\pi}{2}$。这样做的好处是 $\sin^2(\frac{\pi}{2}) = 1^2 = 1$，可以简化计算。
我们考虑一系列点 $z_n$ 的形式为 $z_n = \frac{\pi}{2} + in$，其中 $n$ 是一个趋向于无穷大的正实数。

对于这些点，我们有：
$|\sin(z_n)|^2 = \sin^2(\frac{\pi}{2}) + \sinh^2(n) = 1 + \sinh^2(n)$

当 $n \to \infty$ 时，$\sinh(n) = \frac{e^n - e^{-n}}{2}$ 显然趋向于 $\infty$。
因此，$\sinh^2(n) \to \infty$，从而 $|\sin(z_n)|^2 \to \infty$，这意味着 $|\sin(z_n)| \to \infty$。

**结论：**
因为我们可以找到一系列点（沿着虚轴方向），使得 $|\sin(z)|$ 的值可以任意大，所以函数 $\sin(z)$ 在 $\mathbb{C}$ 上是无界的。

---

### **对于 $\cos(z)$ 的证明**

证明 $\cos(z)$：

我们知道 $\sin(z)$ 和 $\cos(z)$ 之间有一个简单的平移关系：
$\cos(z) = \sin(z + \frac{\pi}{2})$
这意味着 $\cos(z)$ 的值域 (the set of all possible output values) 和 $\sin(z)$ 的值域是完全相同的。因为我们已经证明了 $\sin(z)$ 的值域是无界的，所以 $\cos(z)$ 的值域也必然是无界的。

---

### **更深层次的联系：刘维尔定理 (Deeper Connection: Liouville's Theorem)**

这个问题其实和一个复变分析中非常深刻的定理——**刘维尔定理 (Liouville's Theorem)**——紧密相关。
该定理指出：**任何一个在整个复平面上都有定义的、有界的解析函数（称为整函数, entire function），必然是一个常数函数。**

$\sin(z)$ 和 $\cos(z)$ 都是整函数（它们在整个 $\mathbb{C}$ 上都解析）。同时，它们显然不是常数函数。
因此，根据刘维尔定理的逆否命题，**它们必然是无界的**。

虽然这个定理不能作为这道题的直接证明（因为题目要求你“show that”），但它为你提供了一个强大的理论背景，让你在看到这个问题时就能立刻知道答案和其背后的深刻原因。

当然可以！你提供的这个提示和解题思路非常棒，这正是最直接、最根本的证明方法，完全不需要双曲函数的知识。

这个方法的核心思想是：**利用复指数函数的性质，找到一条能让函数值“失控”的路径。**

让我们把这个过程补充完整，并把每一步的道理都讲清楚。

---

### **第一部分：解释Hint背后的逻辑 (Explaining the Logic Behind the Hint)**

**1. Hint是什么？**
Hint给出了复数余弦的定义：
$\cos(z) = \frac{e^{iz} + e^{-iz}}{2}$

**2. 我们的目标是什么？**
我们要证明 $\cos(z)$ 是**无界的 (unbounded)**。这意味着我们要证明 $|\cos(z)|$ 的值可以变得任意大。

**3. 如何利用这个Hint？**
观察这个公式，它的行为完全由指数函数 $e^{w}$ 决定。我们来分析一下指数函数的特性：
*   如果指数 $w$ 是一个**纯虚数**，比如 $w=i\theta$（$\theta$是实数），那么 $e^{i\theta}$ 的模长 $|e^{i\theta}|$ 永远是1。它只是在单位圆上旋转，是**有界的**。
*   如果指数 $w$ 是一个**实数**，比如 $w=y$（$y$是实数），那么 $e^y$ 会随着 $y$ 的增大而**指数级增长**，是**无界的**。

**这里的突破口就来了！**
我们能不能通过巧妙地选择 $z$，使得公式中的指数 $iz$ 和 $-iz$ 变成**实数**？
当然可以！如果我们选择的 $z$ 是一个**纯虚数**，那么 $i$ 乘以一个纯虚数就会得到一个实数。
这就是你图片中“Along the imaginary axis, z = yi”这一步的根本原因。这是一个非常有洞察力的策略！

---

### **第二部分：补充完整的证明 (The Complete Proof)**

#### **证明 $\cos(z)$ 是无界的**

1.  **从定义出发 (Start with the definition):**
    我们使用指数定义式：
    $\cos(z) = \frac{e^{iz} + e^{-iz}}{2}$

2.  **选择一条路径 (Choose a path):**
    我们选择沿着虚轴 (imaginary axis) 移动。令 $z = iy$，其中 $y$ 是一个可以任意变化的实数。

3.  **代入并化简 (Substitute and simplify):**
    将 $z=iy$ 代入定义式中：
    $\cos(iy) = \frac{e^{i(iy)} + e^{-i(iy)}}{2}$
    因为 $i \cdot i = i^2 = -1$，所以指数部分变为：
    $\cos(iy) = \frac{e^{-y} + e^{y}}{2}$

4.  **分析结果 (Analyze the result):**
    现在我们得到的表达式 $\frac{e^y + e^{-y}}{2}$ 是一个关于实变量 $y$ 的实数函数（这其实就是 $\cosh(y)$，但我们不需要知道这个名字）。
    我们来考察当 $y$ 变得非常大时，这个函数值的行为：
    *   当 $y \to \infty$ 时， $e^y$ 会变得无限大 ($e^y \to \infty$)。
    *   同时，$e^{-y} = \frac{1}{e^y}$ 会趋向于0 ($e^{-y} \to 0$)。
    所以，整个表达式的行为主要由 $e^y$ 决定：
    $\lim_{y\to\infty} \frac{e^{-y} + e^{y}}{2} = \frac{0 + \infty}{2} = \infty$

5.  **得出结论 (Draw the conclusion):**
    我们已经证明，通过让 $z$ 沿着虚轴向上移动（即让 $z=iy$ 中的 $y \to \infty$），$\cos(z)$ 的值可以变得任意大。因此，函数 $\cos(z)$ 在复平面 $\mathbb{C}$ 上是无界的。

#### **证明 $\sin(z)$ 是无界的 (同理)**

现在我们用完全相同的思路来证明 $\sin(z)$ 也是无界的。

1.  **从定义出发 (Start with the definition):**
    $\sin(z)$ 的指数定义是：
    $\sin(z) = \frac{e^{iz} - e^{-iz}}{2i}$

2.  **选择同一条路径 (Choose the same path):**
    我们同样选择 $z = iy$。

3.  **代入并化简 (Substitute and simplify):**
    $\sin(iy) = \frac{e^{i(iy)} - e^{-i(iy)}}{2i} = \frac{e^{-y} - e^{y}}{2i}$

4.  **分析结果的模 (Analyze the modulus of the result):**
    这次的结果是一个纯虚数。要证明函数无界，我们要看它的**模 (modulus)** 是否可以任意大。
    $|\sin(iy)| = \left| \frac{e^{-y} - e^{y}}{2i} \right| = \frac{|e^{-y} - e^{y}|}{|2i|}$
    我们知道 $|2i| = 2$。
    对于分子，当 $y \to \infty$ 时，$e^y$ 远大于 $e^{-y}$，所以 $e^{-y} - e^{y}$ 是一个大的负数。它的绝对值是 $e^y - e^{-y}$。
    所以，$|\sin(iy)| = \frac{e^y - e^{-y}}{2}$

5.  **得出结论 (Draw the conclusion):**
    同样地，当 $y \to \infty$ 时：
    $\lim_{y\to\infty} \frac{e^y - e^{-y}}{2} = \frac{\infty - 0}{2} = \infty$
    我们证明了，通过让 $z$ 沿着虚轴移动，$|\sin(z)|$ 的值可以变得任意大。因此，函数 $\sin(z)$ 在复平面 $\mathbb{C}$ 上也是无界的。

这个证明非常漂亮，因为它只用了最基本的定义，并且清晰地揭示了复变三角函数与实变三角函数的根本不同之处——虚数分量的存在，通过指数函数，将振荡行为转化为了增长行为。