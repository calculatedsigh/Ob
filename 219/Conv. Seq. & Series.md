
---

### **第一部分：建立宏观概念 (The Big Picture)**

首先，最重要的事情是区分**序列的收敛 (Convergence of a Sequence)** 和 **级数的收敛 (Convergence of a Series)**。

1.  **序列 (Sequence):** $\lim_{n\to\infty} z_n$
    *   **问的是什么？** 当 $n$ 变得无限大时，序列中的项 $z_n$ 是不是无限**接近某一个特定的值** $L$？
    *   **直观想象:** 想象你在复平面上画出一连串的点 $z_1, z_2, z_3, \dots$。如果这些点最终都挤向同一个目标点 $L$，那么序列就收敛到 $L$。如果这些点到处乱跑、或者在几个点之间来回跳跃、或者跑向无穷远，那么序列就发散。
    *   **你的问题中的例子:** (1) 和 (2) 是序列。

2.  **级数 (Series):** $\sum_{n=1}^{\infty} a_n$
    *   **问的是什么？** 把序列中的所有项 $a_1, a_2, a_3, \dots$ **全部加起来**，这个总和会不会是一个**有限的数**？
    *   **直观想象:** 这不是看每一项的最终去向，而是看“累加”这个动作的最终结果。级数收敛意味着，虽然你不停地在加新的项，但这个总和最终会稳定在某个数值上，不会无限增大或无限振荡。
    *   **你的问题中的例子:** (3) 和 (4) 是级数。

---

### **第二部分：判断收敛的“工具箱” (The Convergence Toolkit)**

现在，我们来看看解决这两类问题的具体方法。

#### **A. 序列收敛的判断方法 (For Sequences: $\lim_{n\to\infty} z_n$)**

对于复数序列 $z_n = x_n + iy_n$，我们有两条主要的路可以走：

*   **规则1：拆分法 (Splitting into Real and Imaginary Parts)**
    复数序列 $z_n$ 收敛到 $L = a+ib$ 的**充要条件**是：它的实部 $x_n$ 收敛到 $a$，并且它的虚部 $y_n$ 收敛到 $b$。
    > $\lim_{n\to\infty} z_n = L \iff (\lim_{n\to\infty} x_n = a \text{ and } \lim_{n\to\infty} y_n = b)$
    *   **套路:** 把一个复数极限问题，变成两个你更熟悉的实数极限问题。

*   **规则2：模长法/夹逼定理 (Modulus/Squeeze Theorem)**
    如果一个序列的模长（绝对值）趋向于0，那么这个序列本身也一定趋向于0。
    > $\lim_{n\to\infty} |z_n| = 0 \iff \lim_{n\to\infty} z_n = 0$
    *   **套路:** 这是判断极限是否为0的超级利器。通过三角不等式 $|z+w| \le |z|+|w|$ 放缩，然后用夹逼定理。

*   **规则3：观察法 (Observation for Divergence)**
    如果序列的项在多个值之间来回跳动（振荡, oscillating），或者模长趋向于无穷大，那么它就是发散的。

#### **B. 级数收敛的判断方法 (For Series: $\sum a_n$)**

对于复数级数，我们有一个黄金法则：**先看绝对值 (Check the absolute value first)**。

*   **规则1：发散检验 (The Divergence Test) - 必须最先检查！**
    如果级数的通项 $a_n$ **不趋向于0** (i.e., $\lim_{n\to\infty} a_n \neq 0$)，那么这个级数**必定发散**。
    *   **注意:** 如果 $\lim_{n\to\infty} a_n = 0$，这个检验无法给出任何结论，你需要用其他方法继续判断。

*   **规则2：绝对收敛检验 (Absolute Convergence Test)**
    如果各项的**模长**组成的级数 $\sum_{n=1}^{\infty} |a_n|$ 收敛，那么原级数 $\sum_{n=1}^{\infty} a_n$ **必定收敛**。这种情况我们称之为**绝对收敛 (absolutely convergent)**。
    *   **套路:** 这是处理复数级数最强大的方法！因为它把一个复数级数问题，转化成了一个各项为**正实数**的级数问题。然后你就可以使用所有你在微积分中学过的判别法了。

*   **规则3：用于判断 $\sum |a_n|$ 的实数级数判别法 (Tests for Real Series)**
    一旦你通过取模长得到了一个正项级数 $\sum |a_n|$，你就可以用：
    *   **p-级数检验 (p-Series Test):** 级数 $\sum_{n=1}^{\infty} \frac{1}{n^p}$ 在 $p>1$ 时收敛，在 $p \le 1$ 时发散。这是你的“标尺”。
    *   **比较判别法 (Comparison Test):** 将你的级数与一个已知的收敛或发散的级数（如p-级数）进行比较。
    *   **比值判别法 (Ratio Test) / 根值判别法 (Root Test):** 对于包含阶乘或n次方的项特别有效。

---

### **核心理论：子序列与收敛 (The Core Principle: Subsequences and Convergence)**

这个判别法的理论基础非常直观和强大：

**一个序列 $\{z_n\}$ 收敛到极限 $L$ 的一个必要条件是，它的任何一个子序列 $\{z_{n_k}\}$ 也必须收敛到同一个极限 $L$。**
(A necessary condition for a sequence $\{z_n\}$ to converge to a limit $L$ is that every subsequence $\{z_{n_k}\}$ must also converge to the same limit $L$.)

反过来说，这就给了我们一个非常有力的证明**发散**的工具：

**子序列判别法 (Subsequence Test for Divergence):**
如果我们可以从原序列 $\{z_n\}$ 中找到**两个**子序列，它们收敛到**不同**的极限，那么原序列 $\{z_n\}$ **必定发散**。
(If we can find two subsequences of $\{z_n\}$ that converge to different limits, then the original sequence $\{z_n\}$ must diverge.)

---

### **应用到你的问题：$\lim_{n\to\infty} e^{n\pi i/2}$**

现在我们用这个正式的方法来证明第2题发散。

我们的序列是 $z_n = e^{n\pi i/2}$。
我们通过“瞪眼法”已经知道，这个序列的值在 $i, -1, -i, 1$ 这四个值之间循环。我们的目标就是从这个序列里“挑”出两组“小分队”（子序列），让它们各自奔向不同的目标（极限）。

**第一步：选择第一个子序列 (Choose the first subsequence)**

让我们挑选所有 $n$ 是4的倍数的项。我们可以令 $n_k = 4k$，其中 $k=1, 2, 3, \dots$。这样我们得到一个子序列 $\{z_{n_k}\} = \{z_{4k}\}$。

我们来计算这个子序列的极限：
$z_{4k} = e^{(4k)\pi i/2} = e^{2k\pi i}$
根据欧拉公式，$e^{2\pi i} = \cos(2\pi) + i\sin(2\pi) = 1$。
所以，$z_{4k} = (e^{2\pi i})^k = 1^k = 1$。
这个子序列是 $1, 1, 1, \dots$，它显然收敛到1。
$\lim_{k\to\infty} z_{4k} = 1$

**第二步：选择第二个子序列 (Choose the second subsequence)**

现在我们再挑另一组。比如说，我们挑选所有 $n$ 的形式是 $4k+2$ 的项。我们令 $n'_k = 4k+2$，其中 $k=0, 1, 2, \dots$ (这里从k=0开始更方便，得到n=2, 6, 10...)。这样我们得到子序列 $\{z_{n'_k}\} = \{z_{4k+2}\}$。

我们来计算这个子序列的极限：
$z_{4k+2} = e^{(4k+2)\pi i/2} = e^{(2k\pi + \pi)i} = e^{2k\pi i} \cdot e^{\pi i}$
我们已经知道 $e^{2k\pi i} = 1$，并且 $e^{\pi i} = \cos(\pi) + i\sin(\pi) = -1$。
所以，$z_{4k+2} = 1 \cdot (-1) = -1$。
这个子序列是 $-1, -1, -1, \dots$，它显然收敛到-1。
$\lim_{k\to\infty} z_{4k+2} = -1$

**第三步：得出结论 (Draw the conclusion)**

我们成功地找到了两个子序列：
1.  子序列 $\{z_{4k}\}$ 收敛到 **1**。
2.  子序列 $\{z_{4k+2}\}$ 收敛到 **-1**。

因为 $1 \neq -1$，我们找到了两个收敛到不同极限的子序列。因此，根据子序列判别法，原序列 $\{z_n\} = \{e^{n\pi i/2}\}$ **发散**。

---
