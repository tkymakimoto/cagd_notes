![](https://raw.githubusercontent.com/tkymakimoto/cagd_notes/master/IMG_20140601_001010.jpg "Test image")

# 曲線表現

曲線を表現する方法は無数にあり、用途によってさまざまに発展してきた。一般的に曲線表現法は、多数の点（点群、離散点）を結ぶ方法の違いによってその特徴が現れる。

## 陽的表現（Explicit representation）

\begin{eqnarray}
y & = & f(x) \\
z & = & g(x)
\end{eqnarray}

## 陰的表現（Implicit representation）

\begin{eqnarray}
f(x, y, z) = 0
\end{eqnarray}

## パラメトリック表現（Parametric representation）

\begin{eqnarray}
\mathbf{r} & = & \mathbf{r}(t) \\
\mathbf{r}(t) & = & \left[ \begin{array}{ccc} x(t) & y(t) & z(t)\end{array} \right]
\end{eqnarray}

## スプライン

* 離散点（点群）
* 区分多項式
* 滑らか

## ポリライン

点群から作成される曲線で最も単純な表現方法は、各2点間を線分（線形）に結ぶ方法である。

## ラグランジュ曲線

点群を一つの$(\mbox{点数}-1)$次の多項式で表現する方法。

\begin{eqnarray}
x(t) & = & \sum_{j=0}^{n-1} a_jt^{j} \nonumber \\
y(t) & = & \sum_{j=0}^{n-1} b_jt^{j} \\
z(t) & = & \sum_{j=0}^{n-1} c_jt^{j}  \nonumber \\
\end{eqnarray}

ここで、$t$：パラメータ、$a_j \: b_j \: c_j$：$x(t), \: y(t), \: z(t)$における$j$次の係数、$n$：点数である。

\begin{eqnarray}
\mathbf{r}(t) = \sum_{j=0}^{n} a_jt^{j} 
\end{eqnarray}

## Cubic spline
## PARSEC 

PARSECは、航空機の翼型設計でよく用いられている曲線である。上下面それぞれ下記の式で定義する。

$$
z(x) = \sum_{j=0}^{p-1}a_j x^{j+\frac{1}{2}}
$$

## Bézier曲線

\eqref{eq:1}

\begin{equation}
z = x + y
\label{eq:1}
\end{equation}

\begin{eqnarray}
\mathbf{r}(t)  = \sum_{j=0}^{n-1}B_{j,n-1}(t)\mathbf{Q}_j \label{eq:bezier} && \\
n &:& 制御点数 \nonumber \\
B_{j,n-1}(t)&：&バーンスタイン関数 \nonumber \\
\mathbf{Q}_j&：&j番目の制御点 \nonumber \\
\end{eqnarray}

\eqref{eq:bezier}式からも分かるように、$(\mbox{曲線の次数}+1) = \mbox{制御点数}$、または、$\mbox{曲線の階数} = \mbox{制御点数}$となる。

## B-spline

\begin{eqnarray}
\mathbf{r}(t)  =  \sum_{j=0}^{n-1}N_{j,p}(t)\mathbf{Q}_j \\
n & : & 制御点数 \nonumber \\
p &: & 次数 \nonumber \\
N_{j,p}(t) & : & 基底関数　\nonumber \\
\mathbf{Q}_j & : & 制御点 \nonumber
\end{eqnarray}

基底関数は以下のとおりである。

\begin{eqnarray}
N_{j,0}(t) & = & \left \{ \begin{array}{ll} 1 & (t_j \le t \lt t_{j+1}) \\ 0 & \mbox{otherwise} \end{array}  \right . \nonumber \\
\\
N_{j,p}(t) & = & \frac{t - t_{j}}{t_{j+p} - t_j}N_{j,p-1}(t) + \frac{t_{j+p+1} - t}{t_{j+p+1} - t_{j+1}}N_{j+1,p-1}(t) \nonumber \\
\end{eqnarray}

$t_j \: (j = \begin{array}{cccc}0, & 1, & \cdots & p+n \end{array})$は、ノットベクトル$\mathbf{T}$

\begin{eqnarray*}
\mathbf{T} = \left[ \begin{array}{cccc} t_0 & t_1 & \cdots & t_{p+n}\end{array} \right] \\
\end{eqnarray*}




The NURBS Book p.9 1.3 Bézier Curves

> The power basis form has the following disadvantages.

> - it is unnatural for interactive shape design; the coefficients ${a_i}$ convey very little geometric insight about the shape of the curve. Furthermore, a designer typically wants to specify end conditions at both ends of the curve, not just at the starting point;

> -  algorithms for processing power basis polynomials have an algebraic rather than a geometric flavor (e.g., Horner's method);

> - numerically, it is a rather poor form; e.g., Horner's method is prone to round-off error if the coefficients vary greatly in magnitude.

日本語訳
> 累乗型は、次のような欠点がある。

> - 会話的デザインで不自然。曲線の形状における係数$a_i$の寄与（影響度）はとても小さい。さらに、デザイナーは一般的に始点だけでなく曲線の両端をいじりたい。

> - 累乗型多項式を計算するアルゴリズムは、幾何学的特性よりも代数（数学）的特性が強い。

> - 数値的にとても不安定である。例えば、Horner式は、各係数が大きく異なる際に丸め誤差が起こり易い。

　
> Written with [StackEdit](https://stackedit.io/).