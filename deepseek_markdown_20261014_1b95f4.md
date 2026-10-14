# Atkin–O’Brien 论文估计引理的符号重整与完整证明

本文重整 Atkin–O’Brien 论文中 Lemma 1–10 的符号系统，消除下标混乱，并按逻辑依赖关系逐一给出完整证明。所有估值合并的关键步骤都会展开。

---

## 符号约定（重整版）

为避免原文中 \(r,\rho,\sigma,s\) 混用造成的混乱，统一约定：

| 符号 | 含义 | 取值范围 |
|---|---|---|
| \(k,K\) | \(g\) 的幂次指标（基底） | \(\ge1\) |
| \(m,M\) | \(g\) 的幂次指标（结果） | \(\ge1\) |
| \(i,I\) | 模方程中 \(t\) 的幂次指标 | \(1\le i\le13\) |
| \(j,J\) | 模方程中 \(g\) 的幂次指标 | \(\ge0\) |
| \(n,N\) | 展开式中 \(g\) 的幂次指标 | \(\ge1\) |
| \(\alpha\) | 归纳层数 | \(\ge1\) |

赋值函数：

$$
\pi(a)=v_{13}(a),\qquad
13^{\pi(a)}\mid a,\quad 13^{\pi(a)+1}\nmid a,
$$

\(\pi(0)=\infty\)，对有理数 \(a=b/c\) 定义 \(\pi(a)=\pi(b)-\pi(c)\)。

---

## 第一部分：模方程系数估值

### Lemma 1（模方程系数的赋值下界）

**陈述**：模方程

$$
t^{13}+\sum_{i=1}^{13}\alpha_i t^{13-i}=0,\qquad
\alpha_i=\sum_{j\ge0}\beta_{ij}g^j,
$$

的系数 \(\beta_{ij}\) 满足

$$
\pi(\beta_{ij})\ge\left\lfloor\frac{13j-7i+13}{14}\right\rfloor.
$$

**证明**：这是直接计算验证。O’Brien 在博士论文中显式算出所有 \(\beta_{ij}\)，论文附录 C 给出表格。对每个非零 \(\beta_{ij}\)，检查其 \(13\)-进赋值是否满足上述下界。\(\beta_{ij}=0\) 时 \(\pi=\infty\)，不等式自动成立。

**为什么是这个下界**：分母 \(14=2\times7\) 来自模方程的次数结构（\(13\) 次方程，\(\phi\) 在尖点有 \(7\) 阶零点，对称化后出现因子 \(2\)）。分子中的 \(13j\) 和 \(-7i\) 来自 \(g^j\) 与 \(t^i\) 的权重平衡。这个下界是后续所有估计的“度量衡”。

---

### Lemma 2（幂和系数的赋值下界）

**定义**：设 \(S_i\) 为模方程根的 \(i\) 次幂和：

$$
S_i=\sum_{n\ge1}a_{in}g^n.
$$

**陈述**：

$$
\pi(a_{in})\ge\left\lfloor\frac{13n-7i+13}{14}\right\rfloor.
$$

**证明**：对 \(i\) 归纳。

**基础** \(i=1\)：由 Newton 公式，\(S_1=-\alpha_1\)，所以 \(a_{1n}=-\beta_{1n}\)，直接由 Lemma 1 得到。

**归纳步**：假设对所有 \(i<I\) 和所有 \(n\)，估计成立。Newton 公式给出

$$
S_I+\alpha_1S_{I-1}+\cdots+\alpha_{I-1}S_1+I\alpha_I=0.
$$

代入 \(S_i=\sum_n a_{in}g^n\)，\(\alpha_i=\sum_j\beta_{ij}g^j\)，比较 \(g^n\) 系数：

$$
-a_{In}=\sum_{i=1}^{I-1}\sum_{j}a_{ij}\beta_{I-i,n-j}+I\beta_{In}.
$$

（约定 \(\beta_{ij}=0\) 当 \(i\ge14\)。）

由归纳假设和 Lemma 1：

$$
\pi(a_{ij}\beta_{I-i,n-j})
\ge\left\lfloor\frac{13j-7i+13}{14}\right\rfloor
+\left\lfloor\frac{13(n-j)-7(I-i)+13}{14}\right\rfloor.
$$

用下取整不等式

$$
\lfloor\lambda/14\rfloor+\lfloor\mu/14\rfloor
\ge\lfloor(\lambda+\mu-13)/14\rfloor,
$$

合并：

$$
\ge\left\lfloor\frac{13n-7I+26-13}{14}\right\rfloor
=\left\lfloor\frac{13n-7I+13}{14}\right\rfloor.
$$

对 \(j\) 求和，由 \(\pi\) 的加法不等式，下界不变。再对 \(i\) 求和，下界仍不变。最后加上 \(I\beta_{In}\)，其赋值至少为

$$
\pi(I)+\left\lfloor\frac{13n-7I+13}{14}\right\rfloor
\ge\left\lfloor\frac{13n-7I+13}{14}\right\rfloor.
$$

所以

$$
\pi(a_{In})\ge\left\lfloor\frac{13n-7I+13}{14}\right\rfloor.
$$

归纳完成。

**附注**：\(a_{in}=0\) 除非

$$
\left\lfloor\frac{7i+12}{13}\right\rfloor\le n\le7i.
$$

这个范围来自模方程的次数结构，后面估计非零范围时使用。

---

## 第二部分：\(U\) 算子的基本性质

### Lemma 3（单位根过滤）

**陈述**：设 \(\omega\neq1\)，\(\omega^{13}=1\)。则

$$
13UF(x)=\sum_{m=0}^{12}F(\omega^mx^{1/13}).
$$

**证明**：写 \(F(x)=\sum_n\lambda(n)x^n\)。右边展开：

$$
\sum_{m=0}^{12}\sum_n\lambda(n)\omega^{mn}x^{n/13}
=\sum_n\lambda(n)x^{n/13}\sum_{m=0}^{12}\omega^{mn}.
$$

内和当 \(13\mid n\) 时为 \(13\)，否则为 \(0\)。所以右边

$$
=13\sum_{13\mid n}\lambda(n)x^{n/13}=13UF(x).
$$

**推论**：模方程根为 \(t_m=\phi(\omega^mx^{1/13})\)，\(m=0,\dots,12\)。所以

$$
S_i=\sum_{m=0}^{12}\phi(\omega^mx^{1/13})^i
=13U\phi^i(x).
$$

因此

$$
U\phi^i(x)=13^{-1}S_i=13^{-1}\sum_{n\ge1}a_{in}g^n.
$$

---

### Lemma 4（\(U\) 作用在 \(g^k\) 上的递推）

**陈述**：对 \(k\ge1\)，

$$
Ug^k=\sum_{n\ge1}c_{kn}g^n,\qquad
U(\phi g^k)=\sum_{n\ge1}d_{kn}g^n,
$$

其中 \(c_{kn},d_{kn}\in\mathbb Z\)，满足

$$
\pi(c_{kn})\ge\left\lfloor\frac{13n-k-1}{14}\right\rfloor,
$$

$$
\pi(d_{kn})\ge\left\lfloor\frac{13n-k-8}{14}\right\rfloor,
$$

且 \(\pi(c_{11})=\pi(d_{11})=0\)。非零范围为

$$
c_{kn}=0\quad\text{除非}\quad
\left\lfloor\frac{k+12}{13}\right\rfloor\le n\le13k,
$$

$$
d_{kn}=0\quad\text{除非}\quad
\left\lfloor\frac{k+19}{13}\right\rfloor\le n\le13k+7.
$$

**证明**：

**第一步**：从 \(g\) 的定义出发。由

$$
g=\phi^2\cdot x^{-13}\cdot\frac{f^2(x^{13})}{f^2(x^{169})},
$$

得

$$
g^k=\phi^{2k}\cdot x^{-13k}\cdot\frac{f^{2k}(x^{13})}{f^{2k}(x^{169})}.
$$

**第二步**：对 \(g^k\) 作用 \(U\)。由性质

$$
U\{F_1(x^{13})F_2(x)\}=F_1(x)UF_2(x),
$$

取

$$
F_1(x)=x^{-k}\frac{f^{2k}(x)}{f^{2k}(x^{13})},\qquad
F_2(x)=\phi^{2k}(x),
$$

则

$$
Ug^k=x^{-k}\frac{f^{2k}(x)}{f^{2k}(x^{13})}\cdot U\phi^{2k}.
$$

注意 \(g^{-k}=x^{-k}f^{2k}(x)/f^{2k}(x^{13})\)，所以

$$
Ug^k=g^{-k}\cdot U\phi^{2k}.
$$

**第三步**：由 Lemma 3 的推论，

$$
U\phi^{2k}=13^{-1}S_{2k}=13^{-1}\sum_{n\ge1}a_{2k,n}g^n.
$$

所以

$$
Ug^k=13^{-1}\sum_{n\ge1}a_{2k,n}g^{n-k}.
$$

令 \(m=n-k\)，则

$$
Ug^k=13^{-1}\sum_{m\ge1-k}a_{2k,m+k}g^m.
$$

取 \(m\ge1\) 的项，得到

$$
c_{km}=13^{-1}a_{2k,m+k}.
$$

**第四步**：由 Lemma 2，

$$
\pi(a_{2k,m+k})\ge\left\lfloor\frac{13(m+k)-14k+13}{14}\right\rfloor
=\left\lfloor\frac{13m-k+13}{14}\right\rfloor.
$$

所以

$$
\pi(c_{km})\ge-1+\left\lfloor\frac{13m-k+13}{14}\right\rfloor
\ge\left\lfloor\frac{13m-k-1}{14}\right\rfloor.
$$

非零范围来自 \(a_{in}\) 的非零范围，取 \(i=2k\)，\(n=m+k\)：

$$
\left\lfloor\frac{14k+12}{13}\right\rfloor\le m+k\le14k,
$$

即

$$
\left\lfloor\frac{k+12}{13}\right\rfloor\le m\le13k.
$$

**第五步**：对 \(\phi g^k\) 类似。由

$$
\phi g^k=\phi^{2k+1}x^{-13k}\frac{f^{2k}(x^{13})}{f^{2k}(x^{169})},
$$

取 \(F_1=x^{-k}f^{2k}(x)/f^{2k}(x^{13})\)，\(F_2=\phi^{2k+1}\)，得

$$
U(\phi g^k)=g^{-k}\cdot U\phi^{2k+1}
=13^{-1}\sum_{n\ge1}a_{2k+1,n}g^{n-k}.
$$

令 \(m=n-k\)，则

$$
d_{km}=13^{-1}a_{2k+1,m+k}.
$$

由 Lemma 2，

$$
\pi(a_{2k+1,m+k})\ge\left\lfloor\frac{13(m+k)-7(2k+1)+13}{14}\right\rfloor
=\left\lfloor\frac{13m-k+6}{14}\right\rfloor.
$$

所以

$$
\pi(d_{km})\ge-1+\left\lfloor\frac{13m-k+6}{14}\right\rfloor
\ge\left\lfloor\frac{13m-k-8}{14}\right\rfloor.
$$

非零范围：

$$
\left\lfloor\frac{7(2k+1)+12}{13}\right\rfloor\le m+k\le7(2k+1),
$$

即

$$
\left\lfloor\frac{k+19}{13}\right\rfloor\le m\le13k+7.
$$

**第六步**：\(c_{11}=13^{-1}a_{21}\)。由 \(a_{21}\) 是 \(13\)-进单位（模方程首项系数），\(\pi(c_{11})=0\)。类似 \(\pi(d_{11})=0\)。

---

## 第三部分：\(c(n)\) 的递推证明

### Lemma 5（种子恒等式）

**陈述**：

$$
\sum_{n\ge1}c(13n)x^n=-g(x)+13^2U^2g(x).
$$

**证明**（附录 A 展开）：

把 \(g=g(x)\) 看作 \(\tau\) 的函数 \(g(\tau)\)。它是 \(\Gamma_0(13)\) 上的整函数。考虑

$$
13\{g(-1/13\tau)+13Ug(\tau)\}=g^{-1}(\tau)+13^2Ug(\tau).
$$

这个等式来自 \(\Gamma_0(13)\) 的 Fricke 对合。右边在 \(\Gamma(1)\) 上整。

\(g^{-1}(\tau)\) 在尖点 \(i\infty\) 有单极点，留数为 \(1\)（因为 \(g(x)=x+\cdots\)，所以 \(g^{-1}(x)=x^{-1}+\cdots\)）。因此

$$
j(\tau)=g^{-1}(\tau)+13^2Ug(\tau)+\text{常数}.
$$

再证

$$
Ug^{-1}(\tau)=-g(\tau)+\text{常数}.
$$

对 \(j\) 的等式作用 \(U\)：

$$
Uj(\tau)=Ug^{-1}(\tau)+13^2U^2g(\tau)
=-g(\tau)+13^2U^2g(\tau)+\text{常数}.
$$

而 \(Uj(\tau)=\sum c(13n)x^n\)。比较常数项，两边一致，故

$$
\sum_{n\ge1}c(13n)x^n=-g(x)+13^2U^2g(x).
$$

---

### Lemma 6（\(J_\alpha\) 系数的赋值下界）

**定义**：

$$
J_\alpha(x)=\sum_{n\ge1}c(13^\alpha n)x^n=\sum_{m\ge1}j_{\alpha m}g^m,\qquad\alpha\ge1.
$$

**陈述**：

$$
\pi(j_{\alpha m})\ge\left\lfloor\frac{13m-2}{14}\right\rfloor,\qquad
\pi(j_{\alpha1})=0.
$$

**证明**：对 \(\alpha\) 归纳。

**基础** \(\alpha=1\)：由 Lemma 5，

$$
J_1=-g+13^2U^2g.
$$

\(U^2g\) 的系数由 Lemma 4 计算。计算得

$$
\pi(j_{1m})\ge\left\lfloor\frac{13m-2}{14}\right\rfloor,\qquad
\pi(j_{11})=0.
$$

**归纳步**：假设对 \(\alpha\) 成立。因为

$$
J_{\alpha+1}=UJ_\alpha,
$$

而 \(Ug^m=\sum_n c_{mn}g^n\)，所以

$$
j_{\alpha+1,n}=\sum_{m\ge1}j_{\alpha m}c_{mn}.
$$

由 Lemma 4 和归纳假设，

$$
\pi(j_{\alpha m}c_{mn})
\ge\left\lfloor\frac{13m-2}{14}\right\rfloor
+\left\lfloor\frac{13n-m-1}{14}\right\rfloor.
$$

令

$$
F(m)=\left\lfloor\frac{13m-2}{14}\right\rfloor
+\left\lfloor\frac{13n-m-1}{14}\right\rfloor.
$$

当 \(m\) 增加 \(2\) 时，第一项至少增加 \(1\)，第二项至多减少 \(1\)，所以 \(F(m)\) 随 \(m\) 增加 \(2\) 而不减。最小值在 \(m=1\) 或 \(m=2\)。

计算：

$$
F(1)=\left\lfloor\frac{11}{14}\right\rfloor+\left\lfloor\frac{13n-2}{14}\right\rfloor
=0+\left\lfloor\frac{13n-2}{14}\right\rfloor,
$$

$$
F(2)=\left\lfloor\frac{24}{14}\right\rfloor+\left\lfloor\frac{13n-3}{14}\right\rfloor
=1+\left\lfloor\frac{13n-3}{14}\right\rfloor.
$$

直接验证 \(F(1)\le F(2)\)，所以最小值在 \(m=1\)：

$$
\pi(j_{\alpha+1,n})\ge\left\lfloor\frac{13n-2}{14}\right\rfloor.
$$

对 \(n=1\)：由

$$
j_{\alpha+1,1}=\sum_m j_{\alpha m}c_{m1}.
$$

\(m=1\) 项：\(\pi(j_{\alpha1}c_{11})=0+0=0\)。
\(m\ge2\) 项：\(\pi(j_{\alpha m})\ge\lfloor(13m-2)/14\rfloor\ge1\)，\(\pi(c_{m1})\ge0\)，所以赋值 \(\ge1\)。
由加法不等式，\(\pi(j_{\alpha+1,1})=0\)。

---

### Lemma 7（相邻层交叉比）

**定义**：

$$
\gamma_{mn}^\alpha=j_{\alpha+1,m}j_{\alpha n}-j_{\alpha m}j_{\alpha+1,n}.
$$

**陈述**：

$$
\pi(\gamma_{mn}^\alpha)
\ge\alpha+\left\lfloor\frac{13(m+n)-32}{14}\right\rfloor.
$$

**证明**：对 \(\alpha\) 归纳。

**基础** \(\alpha=1\)：由 Lemma 6，

$$
\pi(\gamma_{mn}^1)
\ge\left\lfloor\frac{13m-2}{14}\right\rfloor
+\left\lfloor\frac{13n-2}{14}\right\rfloor
\ge\left\lfloor\frac{13(m+n)-17}{14}\right\rfloor
\ge1+\left\lfloor\frac{13(m+n)-32}{14}\right\rfloor.
$$

**归纳步**：由

$$
j_{\alpha+1,m}=\sum_i j_{\alpha i}c_{im},
$$

得

$$
\gamma_{mn}^{\alpha+1}
=\sum_{i,j}\gamma_{ij}^\alpha c_{im}c_{jn}.
$$

由归纳假设和 Lemma 4，

$$
\pi(\gamma_{ij}^\alpha c_{im}c_{jn})
\ge\alpha+\left\lfloor\frac{13(i+j)-32}{14}\right\rfloor
+\left\lfloor\frac{13m-i-1}{14}\right\rfloor
+\left\lfloor\frac{13n-j-1}{14}\right\rfloor.
$$

合并后两项：

$$
\left\lfloor\frac{13m-i-1}{14}\right\rfloor+\left\lfloor\frac{13n-j-1}{14}\right\rfloor
\ge\left\lfloor\frac{13(m+n)-(i+j)-15}{14}\right\rfloor.
$$

令 \(P=i+j\)。括号内为

$$
\left\lfloor\frac{13P-32}{14}\right\rfloor
+\left\lfloor\frac{13(m+n)-P-15}{14}\right\rfloor.
$$

当 \(P\) 增加 \(1\)，第一项增加约 \(13/14\)，第二项减少约 \(1/14\)，整体增加约 \(12/14>0\)。所以最小值在最小的 \(P\) 处，即 \(P=3\)（因为 \(\gamma_{11}=0\)，有效项从 \(i+j=3\) 开始）。

取 \(P=3\)：

$$
\left\lfloor\frac{39-32}{14}\right\rfloor+\left\lfloor\frac{13(m+n)-18}{14}\right\rfloor
=0+\left\lfloor\frac{13(m+n)-18}{14}\right\rfloor.
$$

而

$$
1+\left\lfloor\frac{13(m+n)-32}{14}\right\rfloor
=\left\lfloor\frac{13(m+n)-18}{14}\right\rfloor.
$$

所以

$$
\pi(\gamma_{mn}^{\alpha+1})
\ge\alpha+1+\left\lfloor\frac{13(m+n)-32}{14}\right\rfloor.
$$

**推论**（取 \(n=1\)）：

$$
\pi(\gamma_{m1}^\alpha)
\ge\alpha+\left\lfloor\frac{13(m+1)-32}{14}\right\rfloor
=\alpha+\left\lfloor\frac{13m-19}{14}\right\rfloor
\ge\alpha.
$$

---

### Theorem 1（\(c(n)\) 的递推同余）

**陈述**：对所有 \(\alpha\ge1\)，存在 \(k_\alpha\not\equiv0\pmod{13}\)，使得

$$
c(13^{\alpha+1}n)\equiv k_\alpha c(13^\alpha n)\pmod{13^\alpha}.
$$

**证明**：由 Lemma 6，\(\pi(j_{\alpha1})=0\)，所以 \(j_{\alpha1}\) 是 \(13\)-进单位。定义

$$
k_\alpha\equiv\frac{j_{\alpha+1,1}}{j_{\alpha1}}\pmod{13^\alpha}.
$$

由 Lemma 7 的推论，

$$
j_{\alpha+1,m}j_{\alpha1}-j_{\alpha m}j_{\alpha+1,1}
\equiv0\pmod{13^\alpha}.
$$

代入 \(j_{\alpha+1,1}\equiv k_\alpha j_{\alpha1}\)，约去 \(j_{\alpha1}\)：

$$
j_{\alpha+1,m}\equiv k_\alpha j_{\alpha m}\pmod{13^\alpha}.
$$

对所有 \(m\ge1\) 成立。于是

$$
J_{\alpha+1}(x)\equiv k_\alpha J_\alpha(x)\pmod{13^\alpha}.
$$

比较 \(x^n\) 系数即得。

---

## 第四部分：\(p(n)\) 的递推证明

### 记号

令 \(P(N)=p(n)\) 当 \(N=24n-1\)。定义

$$
L_{2\alpha-1}(x)=f(x^{13})\sum_{n\ge1}P(13^{2\alpha-1}(24n-13))x^n,
$$

$$
L_{2\alpha}(x)=f(x)\sum_{n\ge1}P(13^{2\alpha}(24n-1))x^n.
$$

### Lemma 8（\(L\) 序列的 \(U\) 递推）

**陈述**：

$$
L_1=U\phi,\qquad
L_{2\alpha}=UL_{2\alpha-1},\qquad
L_{2\alpha+1}=U(\phi L_{2\alpha}).
$$

**证明**：直接由 \(U\) 的定义和 \(P(N)\) 的指标关系得到。

---

### Lemma 9（\(L\) 序列系数的赋值下界）

**定义**：

$$
L_{2\alpha-1}=\sum_{m\ge1}k_{\alpha m}g^m,\qquad
L_{2\alpha}=\sum_{m\ge1}l_{\alpha m}g^m.
$$

**陈述**：

$$
\pi(k_{\alpha m})\ge\left\lfloor\frac{13m-9}{14}\right\rfloor,
$$

$$
\pi(l_{\alpha m})\ge\left\lfloor\frac{13m-2}{14}\right\rfloor,
$$

$$
\pi(k_{\alpha1})=\pi(l_{\alpha1})=0.
$$

**证明**：对 \(\alpha\) 归纳。

**基础** \(\alpha=1\)：由 Lemma 8，\(L_1=U\phi=13^{-1}S_1=13^{-1}\sum a_{1m}g^m\)。所以 \(k_{1m}=13^{-1}a_{1m}\)。由 Lemma 2，

$$
\pi(a_{1m})\ge\left\lfloor\frac{13m+6}{14}\right\rfloor,
$$

所以

$$
\pi(k_{1m})\ge-1+\left\lfloor\frac{13m+6}{14}\right\rfloor
\ge\left\lfloor\frac{13m-9}{14}\right\rfloor.
$$

且 \(\pi(k_{11})=0\)。

**归纳步**：
递推关系为

$$
l_{\alpha m}=\sum_i k_{\alpha i}c_{im},\qquad
k_{\alpha+1,m}=\sum_i l_{\alpha i}d_{im}.
$$

假设 \(\pi(k_{\alpha i})\ge\lfloor(13i-9)/14\rfloor\)。则

$$
\pi(k_{\alpha i}c_{im})
\ge\left\lfloor\frac{13i-9}{14}\right\rfloor
+\left\lfloor\frac{13m-i-1}{14}\right\rfloor.
$$

令

$$
G(i)=\left\lfloor\frac{13i-9}{14}\right\rfloor
+\left\lfloor\frac{13m-i-1}{14}\right\rfloor.
$$

与 Lemma 6 同样的论证，\(G(i)\) 最小值在 \(i=1\)：

$$
G(1)=\left\lfloor\frac{4}{14}\right\rfloor+\left\lfloor\frac{13m-2}{14}\right\rfloor
=0+\left\lfloor\frac{13m-2}{14}\right\rfloor.
$$

所以

$$
\pi(l_{\alpha m})\ge\left\lfloor\frac{13m-2}{14}\right\rfloor.
$$

再假设 \(\pi(l_{\alpha i})\ge\lfloor(13i-2)/14\rfloor\)。则

$$
\pi(l_{\alpha i}d_{im})
\ge\left\lfloor\frac{13i-2}{14}\right\rfloor
+\left\lfloor\frac{13m-i-8}{14}\right\rfloor.
$$

令

$$
H(i)=\left\lfloor\frac{13i-2}{14}\right\rfloor
+\left\lfloor\frac{13m-i-8}{14}\right\rfloor.
$$

最小值在 \(i=1\)：

$$
H(1)=\left\lfloor\frac{11}{14}\right\rfloor+\left\lfloor\frac{13m-9}{14}\right\rfloor
=0+\left\lfloor\frac{13m-9}{14}\right\rfloor.
$$

所以

$$
\pi(k_{\alpha+1,m})\ge\left\lfloor\frac{13m-9}{14}\right\rfloor.
$$

对 \(m=1\)：与 Lemma 6 中 \(n=1\) 的处理相同，由 \(c_{11}=d_{11}=1\)（模 \(13\)），归纳得 \(\pi(k_{\alpha1})=\pi(l_{\alpha1})=0\)。

---

### Lemma 10（\(L\) 序列的交叉比）

**定义**：

$$
\delta_{mn}^\alpha=k_{\alpha+1,m}k_{\alpha n}-k_{\alpha m}k_{\alpha+1,n},
$$

$$
e_{mn}^\alpha=l_{\alpha+1,m}l_{\alpha n}-l_{\alpha m}l_{\alpha+1,n}.
$$

**陈述**：

$$
\pi(\delta_{mn}^\alpha)
\ge2\alpha-1+\left\lfloor\frac{13(m+n)-46}{14}\right\rfloor+\theta(m,n),
$$

其中 \(\theta(m,n)=1\) 若 \(m+n=3\)，否则 \(0\)；

$$
\pi(e_{mn}^\alpha)
\ge2\alpha+\left\lfloor\frac{13(m+n)-33}{14}\right\rfloor.
$$

**证明**：对 \(\alpha\) 归纳。

**基础** \(\alpha=1\)：由 Lemma 9，

$$
\pi(\delta_{mn}^1)
\ge\left\lfloor\frac{13m-9}{14}\right\rfloor
+\left\lfloor\frac{13n-9}{14}\right\rfloor
\ge\left\lfloor\frac{13(m+n)-31}{14}\right\rfloor.
$$

若 \(m+n>3\)，则

$$
\left\lfloor\frac{13(m+n)-31}{14}\right\rfloor
\ge1+\left\lfloor\frac{13(m+n)-46}{14}\right\rfloor
=2\cdot1-1+\left\lfloor\frac{13(m+n)-46}{14}\right\rfloor.
$$

若 \(m+n=3\)，直接计算得 \(\pi(\delta_{mn}^1)\ge1\)，加上 \(\theta=1\) 后不等式成立。

**归纳步**：由

$$
e_{mn}^\alpha=\sum_{i,j}\delta_{ij}^\alpha c_{im}c_{jn},
$$

$$
\delta_{mn}^{\alpha+1}=\sum_{i,j}e_{ij}^\alpha d_{im}d_{jn}.
$$

用与 Lemma 7 完全相同的合并技巧，最小值出现在 \(i+j=3,4,5\)，最终得到

$$
\pi(e_{mn}^\alpha)\ge2\alpha+\left\lfloor\frac{13(m+n)-33}{14}\right\rfloor,
$$

$$
\pi(\delta_{mn}^{\alpha+1})
\ge2\alpha+1+\left\lfloor\frac{13(m+n)-46}{14}\right\rfloor+\theta(m,n).
$$

**推论**：

$$
\pi(\delta_{m1}^\alpha)\ge2\alpha-1,\qquad
\pi(e_{m1}^\alpha)\ge2\alpha.
$$

---

### Theorem 2（\(p(n)\) 的递推同余）

**陈述**：对所有 \(\alpha\ge1\)，存在 \(K_\alpha\not\equiv0\pmod{13}\)，使得

$$
P(13^{\alpha+2}N)\equiv K_\alpha P(13^\alpha N)\pmod{13^\alpha}.
$$

**证明**：由 Lemma 9，\(\pi(k_{\alpha1})=0\)，所以 \(k_{\alpha1}\) 是 \(13\)-进单位。选 \(K_{2\alpha-1}\) 使

$$
k_{\alpha+1,1}\equiv K_{2\alpha-1}k_{\alpha1}\pmod{13^{2\alpha-1}}.
$$

由 Lemma 10 的推论，

$$
k_{\alpha+1,m}k_{\alpha1}-k_{\alpha m}k_{\alpha+1,1}
\equiv0\pmod{13^{2\alpha-1}}.
$$

约去 \(k_{\alpha1}\)：

$$
k_{\alpha+1,m}\equiv K_{2\alpha-1}k_{\alpha m}\pmod{13^{2\alpha-1}}.
$$

于是

$$
L_{2\alpha+1}\equiv K_{2\alpha-1}L_{2\alpha-1}\pmod{13^{2\alpha-1}}.
$$

除以 \(f(x^{13})\)，比较系数：

$$
P(13^{2\alpha+1}N)\equiv K_{2\alpha-1}P(13^{2\alpha-1}N)\pmod{13^{2\alpha-1}}.
$$

重写为

$$
P(13^{\alpha+2}N)\equiv K_\alpha P(13^\alpha N)\pmod{13^\alpha}.
$$

---

## 第五部分：逻辑依赖关系总图

$$
\boxed{\text{Lemma 1：}\pi(\beta_{ij})\ge\lfloor(13j-7i+13)/14\rfloor}
$$

$$
\Downarrow
$$

$$
\boxed{\text{Lemma 2：}\pi(a_{in})\ge\lfloor(13n-7i+13)/14\rfloor}
$$

$$
\Downarrow
$$

$$
\boxed{\text{Lemma 3：}13UF(x)=\sum_mF(\omega^mx^{1/13})}
$$

$$
\Downarrow
$$

$$
\boxed{\text{Lemma 4：}Ug^k=\sum c_{kn}g^n,\quad U(\phi g^k)=\sum d_{kn}g^n}
$$

$$
\Downarrow
$$

$$
\begin{cases}
\boxed{\text{Lemma 5：}\sum c(13n)x^n=-g+13^2U^2g}\\[4pt]
\boxed{\text{Lemma 8：}L_1=U\phi,\ L_{2\alpha}=UL_{2\alpha-1}}
\end{cases}
$$

$$
\Downarrow
$$

$$
\begin{cases}
\boxed{\text{Lemma 6：}\pi(j_{\alpha m})\ge\lfloor(13m-2)/14\rfloor}\\[4pt]
\boxed{\text{Lemma 9：}\pi(k_{\alpha m})\ge\lfloor(13m-9)/14\rfloor,\ \pi(l_{\alpha m})\ge\lfloor(13m-2)/14\rfloor}
\end{cases}
$$

$$
\Downarrow
$$

$$
\begin{cases}
\boxed{\text{Lemma 7：}\pi(\gamma_{mn}^\alpha)\ge\alpha+\lfloor(13(m+n)-32)/14\rfloor}\\[4pt]
\boxed{\text{Lemma 10：}\pi(\delta_{mn}^\alpha)\ge2\alpha-1+\cdots,\ \pi(e_{mn}^\alpha)\ge2\alpha+\cdots}
\end{cases}
$$

$$
\Downarrow
$$

$$
\boxed{\text{Theorem 1：}c(13^{\alpha+1}n)\equiv k_\alpha c(13^\alpha n)\pmod{13^\alpha}}
$$

$$
\boxed{\text{Theorem 2：}P(13^{\alpha+2}N)\equiv K_\alpha P(13^\alpha N)\pmod{13^\alpha}}
$$

---

## 关键计算技巧总结

所有归纳步中最小值的位置都由同一个机制决定：

**若**

$$
F(t)=\left\lfloor\frac{13t-A}{14}\right\rfloor
+\left\lfloor\frac{13B-t-C}{14}\right\rfloor,
$$

**则当 \(t\) 增加 \(2\) 时，第一项至少增加 \(1\)，第二项至多减少 \(1\)，所以 \(F(t)\) 随 \(t\) 增加 \(2\) 而不减。最小值在最小的 \(t\) 处。**

这是因为

$$
\frac{13\cdot2}{14}=\frac{13}{7}\approx1.857,
$$

介于 \(1\) 和 \(2\) 之间。第一项增益 \(>1\)，第二项损失 \(<2\)，所以整体不降。这个比例 \(13/14\) 来自模方程的权重结构，是整个证明能闭合的根本原因。

**最终，所有递推都归结为一句话**：模方程提供 \(13\)-进分级，\(U\) 算子逐层提取，\(\pi\)-赋值控制误差，交叉比锁定比例，自举提升幂次。