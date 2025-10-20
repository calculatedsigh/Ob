
---

### **证明目标 (Goal of the Proof)**

我们要从复指数函数最根本的**幂级数定义 (power series definition)** 出发，严格证明对于任意复数 $z$ 和 $w$，都满足以下性质：
$e^{z+w} = e^z \cdot e^w$

### **证明过程 (The Proof)**

**第一步：写出定义，准备相乘**

我们从等式的右边 $e^z \cdot e^w$ 开始。根据定义，我们有：
$e^z = \sum_{n=0}^{\infty} \frac{z^n}{n!} = \frac{z^0}{0!} + \frac{z^1}{1!} + \frac{z^2}{2!} + \dots$
$e^w = \sum_{m=0}^{\infty} \frac{w^m}{m!} = \frac{w^0}{0!} + \frac{w^1}{1!} + \frac{w^2}{2!} + \dots$

所以，我们要计算的是这两个无穷级数的乘积：
$e^z \cdot e^w = \left( \sum_{n=0}^{\infty} \frac{z^n}{n!} \right) \cdot \left( \sum_{m=0}^{\infty} \frac{w^m}{m!} \right)$

**第二步：应用柯西乘积 (Apply the Cauchy Product)**

柯西乘积告诉我们如何将两个幂级数相乘。它的核心思想是模仿多项式乘法：将所有乘积项中，总次数相同的项归类合并。

如果我们将 $e^z \cdot e^w$ 的结果写成一个新的幂级数 $\sum_{k=0}^{\infty} c_k$，那么第 $k$ 项的系数 $c_k$ 是由所有 $z^n \cdot w^m$ (其中 $n+m=k$) 的项合并而来的。

根据柯西乘积的公式，新级数的通项 $c_k$ 是：
$c_k = \sum_{i=0}^{k} (\text{第一个级数中第 } i \text{ 项}) \cdot (\text{第二个级数中第 } k-i \text{ 项})$

应用到我们这里：
*   第一个级数的第 $i$ 项是 $\frac{z^i}{i!}$
*   第二个级数的第 $k-i$ 项是 $\frac{w^{k-i}}{(k-i)!}$

==所以，我们得到：==
$e^z \cdot e^w = \sum_{k=0}^{\infty} \left( \sum_{i=0}^{k} \frac{z^i}{i!} \cdot \frac{w^{k-i}}{(k-i)!} \right)$

这一步是整个证明的框架，也是你之前提示中的第一行。现在，我们的任务就是化简括号里的那个内部求和。

**第三步：化简内部求和 (The Key Step: Simplify the Inner Sum)**

让我们把内部求和单独拿出来分析：
$\sum_{i=0}^{k} \frac{z^i}{i!} \cdot \frac{w^{k-i}}{(k-i)!}$

这个形式看起来是不是有点眼熟？它非常像**二项式定理 (Binomial Theorem)** 的展开式。我们回忆一下二项式定理：
$(z+w)^k = \sum_{i=0}^{k} \binom{k}{i} z^i w^{k-i}$
其中，二项式系数 (binomial coefficient) $\binom{k}{i} = \frac{k!}{i!(k-i)!}$。

比较一下，我们发现我们的表达式里分母是 $i!(k-i)!$，正好是二项式系数的一部分，但是**缺少了一个分子 $k!$**。

为了凑出这个二项式系数，我们可以做一个非常巧妙的代数变形：**在求和符号的内外同时乘以和除以 $k!$**。因为对于内部求和（变量是 $i$），$k$ 是一个常数，所以这个操作是合法的。

$\sum_{i=0}^{k} \frac{z^i}{i!} \frac{w^{k-i}}{(k-i)!} = \frac{1}{k!} \left( \sum_{i=0}^{k} \frac{k!}{i!(k-i)!} z^i w^{k-i} \right)$

现在，括号里的 $\frac{k!}{i!(k-i)!}$ 正是二项式系数 $\binom{k}{i}$！我们把它替换掉：
$= \frac{1}{k!} \left( \sum_{i=0}^{k} \binom{k}{i} z^i w^{k-i} \right)$

太棒了！括号里的求和现在**完完全全**就是 $(z+w)^k$ 的二项式展开式。所以我们可以把它整个替换掉：
$= \frac{1}{k!} (z+w)^k = \frac{(z+w)^k}{k!}$

**第四步：代回原式，完成证明**

我们已经成功地证明了，在 $e^z \cdot e^w$ 的级数展开中，那个复杂的内部求和其实就等于 $\frac{(z+w)^k}{k!}$。

现在我们把它代回到第二步的框架中：
$e^z \cdot e^w = \sum_{k=0}^{\infty} \left( \frac{(z+w)^k}{k!} \right)$

我们再来看看等式左边的 $e^{z+w}$。根据指数函数的定义，把变量 $z$ 换成 $(z+w)$，我们得到：
$e^{z+w} = \sum_{k=0}^{\infty} \frac{(z+w)^k}{k!}$

两者完全相等！

因此，我们从 $e^z$ 和 $e^w$ 的定义出发，通过柯西乘积和二项式定理，最终推导出了 $e^{z+w}$ 的定义。证明完毕。

---
### **逻辑总结**

$e^z \cdot e^w \xrightarrow{\text{定义}} \left(\sum \frac{z^n}{n!}\right)\left(\sum \frac{w^m}{m!}\right) \xrightarrow{\text{柯西乘积}} \sum_{k=0}^{\infty} \left(\sum_{i=0}^{k} \frac{z^i w^{k-i}}{i!(k-i)!}\right) \xrightarrow{\text{凑二项式}} \sum_{k=0}^{\infty} \frac{1}{k!}\left(\sum_{i=0}^{k} \binom{k}{i} z^i w^{k-i}\right) \xrightarrow{\text{二项式定理}} \sum_{k=0}^{\infty} \frac{(z+w)^k}{k!} \xrightarrow{\text{定义}} e^{z+w}$好的，我们再来完整地走一遍这个证明。这是一个非常经典的证明，它完美地展示了柯西乘积 (Cauchy Product) 的威力。

我会把每一步都分解开，并解释清楚我们为什么要这么做，尤其是你之前看到的提示中省略的那个关键步骤。

---

### **证明目标 (Goal of the Proof)**

我们要从复指数函数最根本的**幂级数定义 (power series definition)** 出发，严格证明对于任意复数 $z$ 和 $w$，都满足以下性质：
$e^{z+w} = e^z \cdot e^w$

### **证明过程 (The Proof)**

**第一步：写出定义，准备相乘**

我们从等式的右边 $e^z \cdot e^w$ 开始。根据定义，我们有：
$e^z = \sum_{n=0}^{\infty} \frac{z^n}{n!} = \frac{z^0}{0!} + \frac{z^1}{1!} + \frac{z^2}{2!} + \dots$
$e^w = \sum_{m=0}^{\infty} \frac{w^m}{m!} = \frac{w^0}{0!} + \frac{w^1}{1!} + \frac{w^2}{2!} + \dots$

所以，我们要计算的是这两个无穷级数的乘积：
$e^z \cdot e^w = \left( \sum_{n=0}^{\infty} \frac{z^n}{n!} \right) \cdot \left( \sum_{m=0}^{\infty} \frac{w^m}{m!} \right)$

**第二步：应用柯西乘积 (Apply the Cauchy Product)**

柯西乘积告诉我们如何将两个幂级数相乘。它的核心思想是模仿多项式乘法：将所有乘积项中，总次数相同的项归类合并。

如果我们将 $e^z \cdot e^w$ 的结果写成一个新的幂级数 $\sum_{k=0}^{\infty} c_k$，那么第 $k$ 项的系数 $c_k$ 是由所有 $z^n \cdot w^m$ (其中 $n+m=k$) 的项合并而来的。

根据柯西乘积的公式，新级数的通项 $c_k$ 是：
$c_k = \sum_{i=0}^{k} (\text{第一个级数中第 } i \text{ 项}) \cdot (\text{第二个级数中第 } k-i \text{ 项})$

应用到我们这里：
*   第一个级数的第 $i$ 项是 $\frac{z^i}{i!}$
*   第二个级数的第 $k-i$ 项是 $\frac{w^{k-i}}{(k-i)!}$

所以，我们得到：
$e^z \cdot e^w = \sum_{k=0}^{\infty} \left( \sum_{i=0}^{k} \frac{z^i}{i!} \cdot \frac{w^{k-i}}{(k-i)!} \right)$

这一步是整个证明的框架，也是你之前提示中的第一行。现在，我们的任务就是化简括号里的那个内部求和。

**第三步：化简内部求和 (The Key Step: Simplify the Inner Sum)**

让我们把内部求和单独拿出来分析：
$\sum_{i=0}^{k} \frac{z^i}{i!} \cdot \frac{w^{k-i}}{(k-i)!}$

这个形式看起来是不是有点眼熟？它非常像**二项式定理 (Binomial Theorem)** 的展开式。我们回忆一下二项式定理：
$(z+w)^k = \sum_{i=0}^{k} \binom{k}{i} z^i w^{k-i}$
其中，二项式系数 (binomial coefficient) $\binom{k}{i} = \frac{k!}{i!(k-i)!}$。

比较一下，我们发现我们的表达式里分母是 $i!(k-i)!$，正好是二项式系数的一部分，但是**缺少了一个分子 $k!$**。

为了凑出这个二项式系数，我们可以做一个非常巧妙的代数变形：**在求和符号的内外同时乘以和除以 $k!$**。因为对于内部求和（变量是 $i$），$k$ 是一个常数，所以这个操作是合法的。

$\sum_{i=0}^{k} \frac{z^i}{i!} \frac{w^{k-i}}{(k-i)!} = \frac{1}{k!} \left( \sum_{i=0}^{k} \frac{k!}{i!(k-i)!} z^i w^{k-i} \right)$

现在，括号里的 $\frac{k!}{i!(k-i)!}$ 正是二项式系数 $\binom{k}{i}$！我们把它替换掉：
$= \frac{1}{k!} \left( \sum_{i=0}^{k} \binom{k}{i} z^i w^{k-i} \right)$

太棒了！括号里的求和现在**完完全全**就是 $(z+w)^k$ 的二项式展开式。所以我们可以把它整个替换掉：
$= \frac{1}{k!} (z+w)^k = \frac{(z+w)^k}{k!}$

**第四步：代回原式，完成证明**

我们已经成功地证明了，在 $e^z \cdot e^w$ 的级数展开中，那个复杂的内部求和其实就等于 $\frac{(z+w)^k}{k!}$。

现在我们把它代回到第二步的框架中：
$e^z \cdot e^w = \sum_{k=0}^{\infty} \left( \frac{(z+w)^k}{k!} \right)$

我们再来看看等式左边的 $e^{z+w}$。根据指数函数的定义，把变量 $z$ 换成 $(z+w)$，我们得到：
$e^{z+w} = \sum_{k=0}^{\infty} \frac{(z+w)^k}{k!}$

两者完全相等！

因此，我们从 $e^z$ 和 $e^w$ 的定义出发，通过柯西乘积和二项式定理，最终推导出了 $e^{z+w}$ 的定义。证明完毕。

---
### **逻辑总结**

$e^z \cdot e^w \xrightarrow{\text{定义}} \left(\sum \frac{z^n}{n!}\right)\left(\sum \frac{w^m}{m!}\right) \xrightarrow{\text{柯西乘积}} \sum_{k=0}^{\infty} \left(\sum_{i=0}^{k} \frac{z^i w^{k-i}}{i!(k-i)!}\right) \xrightarrow{\text{凑二项式}} \sum_{k=0}^{\infty} \frac{1}{k!}\left(\sum_{i=0}^{k} \binom{k}{i} z^i w^{k-i}\right) \xrightarrow{\text{二项式定理}} \sum_{k=0}^{\infty} \frac{(z+w)^k}{k!} \xrightarrow{\text{定义}} e^{z+w}$