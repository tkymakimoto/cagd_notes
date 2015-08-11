# 曲線表現


- 累乗型
- ブレンディング関数型


```cpp
#include <cstdlib>

int main(int argc, char** argv){
	double y;
	std::vector<double> v;
	return EXIT_SUCCESS;
}
```

    
##累乗型曲線

\\[
\mathbf{r}(t) = \sum_{j=0}^{n} a_jt^{j} 
\\]

### Cubic spline
### PARSEC 

$$
z(x) = \sum_{j=0}^{p-1}a_j x^{j+\frac{1}{2}}
$$


##ブレンディング関数型曲線
### Bézier曲線

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

\eqref{eq:bezier}式からも分かるように、$\mbox{曲線の次数}+1(階数) = \mbox{制御点数}$となる。このBe一般的に一つのセグメントで表現しようとする。

### B-spline

\begin{eqnarray}
\mathbf{r}(t) & = & \sum_{j=0}^{n-1}N_{j,p}(t)\mathbf{Q}_j \\
x & = & y
\end{eqnarray}

\begin{array}{cc}
  a & b \\
  c & c
\end{array}


The NURBS ⧸⧸Book⧸⧸book⧸⧸ p.9 1.3 Bézier Curves

> The power basis form has the following disadvantages.

> - it is unnatural for interactive shape design; the coefficients ${a_i}$ convey very little geometric insight about the shape of the curve. Furthermore, a designer typically wants to specify end conditions at both ends of the curve, not just at the ⧸⧸starting⧸⧸strting⧸⧸ point;

> -  algorithms for processing power basis polynomials have an algebraic rather than a geometric flavor (e.g., Horner's method);

> - numerically, it is a rather poor form; e.g., Horner's method is prone to round-off error if the coefficients vary greatly in magnitude.

日本語訳
> 累乗型は、次の面で不利がある。

> - 会話的デザインで不自然。曲線の形状における係数$a_i$の寄与（影響度）はとても小さい。さらに、デザイナーは一般的に始点だけでなく曲線の両端をいじりたい。

> - 累乗型多項式を計算するアルゴリズムは、幾何学的特性よりも代数（数学）的特性が強い。

> - 数値的にとても不安定である。例えば、Horner式は、各係数が大きく異なる際に丸め誤差が起こり易い。

　
> Written with [StackEdit](https://stackedit.io/).