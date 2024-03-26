---
puppeteer:
    displayHeaderFooter: true
    headerTemplate: '<div style="font-size: 9px; margin-left: 1cm;"><span class=''title''></span></div>'
    footerTemplate: '<div style="font-size: 9px; margin: 0 auto; "> <span class=''pageNumber''></span>/<span class=''totalPages''></span></div>'
---

<style>
  hr {
    opacity: 0;
    break-after: page;
  }
</style>

# クロソイド曲線

## クロソイド曲線の基本式

| 式番号 | 式                                                                                                                                                                              | 説明                                                                                                              |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
|  (1)   | $RL=A^2$                                                                                                                                                                        | 曲率半径$R$と曲線長$L$の積が定数(一定)                                                                            |
|  (2)   | $\dfrac{d\tau}{dL}=\dfrac{1}{R}$                                                                                                                                                | 曲率の定義式: 曲線の曲がり具合を表す                                                                              |
|  (3)   | $\tau = \dfrac{L^2}{2A^2} = \dfrac{L}{2R} $                                                                                                                                     | 接線角$\tau$はクロソイドパラメータ A と曲線長 L で決まる<br>分母の$A^2$に(1)式を再代入                            |
|  (4)   | $L=A\sqrt{2\tau}$                                                                                                                                                               | (3)式を$L$について解く                                                                                            |
|  (5)   | $R=\dfrac{A^2}{L}=\dfrac{A}{\sqrt{2\tau}}$                                                                                                                                      | (1)式に(4)式を代入                                                                                                |
|  (6)   | $dx = dL \cos\tau$ <br> $dy = dL \sin\tau$                                                                                                                                      | 曲線の微小変化$dx,dy$は、曲線長の微小増分$dL$と接線角$\tau$を成す                                                 |
|  (7)   | $x = \dfrac{A}{\sqrt{2}}\displaystyle\int^\tau_0 \dfrac{\cos\tau}{\sqrt{\tau}}d\tau$　<br> $y = \dfrac{A}{\sqrt{2}}\displaystyle\int^\tau_0 \dfrac{\sin\tau}{\sqrt{\tau}}d\tau$ | クロソイド曲線$(x,y)$は、<br>クロソイドパラメータ$A$と接線角$\tau$で決まる<br>ここで、接線角$\tau$は(3)式で定まる |

## 接線角$\tau$の導出

(1)式を$R$の式にした$R=\dfrac{A^2}{L}$を(2)式の右辺に代入すると、微分方程式$\dfrac{d\tau}{dL}=\dfrac{L}{A^2}$が得られる。これを$\tau$について解く[^1]。

$$
\tau = \int^L_0{\frac{d\tau}{dL}dL} = \int^L_0{\frac{L}{A^2}}dL = \frac{1}{A^2}\int^L_0{L}dL=\frac{1}{A^2}\cdot\frac{1}{2}L^2 = \frac{L^2}{2A^2}
$$

---

## クロソイド曲線$(x,y)$の導出

(6)式から(7)式を導く。まず、(6)式に(4)式を代入して$\tau$で式をまとめる[^2]。

$$
    dx = dL\cos\tau= d(A\sqrt{2\tau})\cos\tau = A\cdot \dfrac{1}{2}(2\tau)^{\frac{1}{2}-1}\cdot d(2\tau)\cos\tau d\tau = \dfrac{Ad\tau}{\sqrt{2\tau}}\cos{\tau}
$$

$$
    dy = dL\sin\tau= d(A\sqrt{2\tau})\sin\tau = A\cdot \dfrac{1}{2}(2\tau)^{\frac{1}{2}-1}\cdot d(2\tau)\sin\tau d\tau = \dfrac{Ad\tau}{\sqrt{2\tau}}\sin{\tau}
$$

したがって、(6)式は二つの微分方程式になる。

$$
    \frac{dx}{d\tau} = \dfrac{A}{\sqrt{2\tau}}\cos{\tau}, \hspace{0.5cm} \frac{dy}{d\tau} = \dfrac{A}{\sqrt{2\tau}}\sin{\tau}
$$

これらの微分方程式を各々解く。

$$
　
    x = \int^\tau_0 \frac{dx}{d\tau}d\tau=\int^\tau_0\dfrac{A}{\sqrt{2\tau}}\cos\tau d\tau = \dfrac{A}{\sqrt{2}}\int^\tau_0\frac{\cos\tau}{\sqrt{\tau}}d\tau
$$

$$
    y = \int^\tau_0 \frac{dy}{d\tau}d\tau=\int^\tau_0\dfrac{A}{\sqrt{2\tau}}\sin\tau d\tau = \dfrac{A}{\sqrt{2}}\int^\tau_0\frac{\sin\tau}{\sqrt{\tau}}d\tau
$$

(7)式がこれで導出された。(7)式はフレネル積分を含む式である。

## クロソイド曲線$(x,y)$の計算

クロソイド曲線上の任意の点 P$(x,y)$は、クロソイドパラメータ$A$と接線角$\tau$で表されているが、(7)式のままでは具体的に値を計算できない。いったん被積分関数を無限級数にした後に積分する。無限級数の形にすることによってコンピュータ上で正確に値を計算可能になる。

$$
\begin{array}{cl}
      x & = \dfrac{A}{\sqrt2} \displaystyle\int^\tau_0 \dfrac{\cos\tau}{\sqrt{\tau}}d\tau = \dfrac{A}{\sqrt2{}} \int^\tau_0 \tau^{ -1/2 } (1 - \dfrac{\tau^2}{2!} + \dfrac{\tau^4}{4!} - \dfrac{\tau^6}{6!} \dots) d\tau;  \hspace{0.5cm} //\cos\tau\text{を展開}
      \\
      \\
      & = \dfrac{A}{\sqrt2{}} \displaystyle\int^\tau_0 (\tau^{-1/2} - \frac{\tau^{3/2}}{2!} +  \frac{\tau^{7/2}}{4!} -  \frac{\tau^{11/2}}{6!} \dots )d\tau; \hspace{1cm} //因子\tau^{-1/2}を掛ける
      \\
      \\
      & = \dfrac{A}{\sqrt2{}} \left(2\tau^{1/2} - \dfrac{2\tau^{5/2}}{5\cdot2!} +  \dfrac{2\tau^{9/2}}{9\cdot4!} -  \dfrac{2\tau^{13/2}}{13\cdot6!} + \dots +\dfrac{(-1)^{n-1} 2\tau^{(4n-3)/2}}{(4n-3)\cdot(2n-2)!}+ \dots\right); //積分
      \\
      \\
      & = A\sqrt{2\tau}\left(1 - \dfrac{\tau^2}{5\cdot 2!} +  \dfrac{\tau^4}{9\cdot4!} -  \dfrac{\tau^6}{13\cdot6!} + \dots +\dfrac{(-1)^{n-1} \tau^{2(n-1)}}{(4n-3)\cdot(2n-2)!}+ \dots\right); // 2\tau^{1/2}を抽出
      \\
      \\
      & = A\sqrt{2\tau}\left(\displaystyle\sum^{\infty}_{n=1}\dfrac{(-1)^{n-1} \tau^{2(n-1)}}{(4n-3)\cdot(2n-2)!}\right)
      \\
      \\
\end{array}
$$

$$
\begin{array}{cl}
    y & = \dfrac{A}{\sqrt{2}} \displaystyle\int^\tau_0 \dfrac{\sin\tau}{\sqrt{\tau}}d\tau = \dfrac{A}{\sqrt2{}} \int^\tau_0 \tau^{ -1/2 } (\tau - \dfrac{\tau^3}{3!} + \dfrac{\tau^5} {5!} - \dfrac{\tau^7}{7!} \dots) d\tau;  \hspace{0.5cm} //\sin\tau\text{を展開}
    \\
    \\
      & = \dfrac{A}{\sqrt2{}} \displaystyle\int^\tau_0 (\tau^{1/2} - \frac{\tau^{5/2}}{3!} +  \frac{\tau^{9/2}}{5!} -  \frac{\tau^{13/2}}{7!} \dots )d\tau; \hspace{1cm} //因子\tau^{-1/2}を掛ける
    \\
    \\
      &  = \dfrac{A}{\sqrt2{}} \left(\dfrac{2}{3}\tau^{3/2} - \dfrac{2\tau^{7/2}}{7\cdot3!} +  \dfrac{2\tau^{11/2}}{11\cdot5!} -  \dfrac{2\tau^{15/2}}{15\cdot7!} + \dots +\dfrac{(-1)^{n-1} 2\tau^{(4n-1)/2}}{(4n-1)(2n-1)!}+ \dots\right); //積分
    \\
    \\
      & = A\sqrt{2\tau}\left(\dfrac{\tau}{3} - \dfrac{\tau^3}{7\cdot 3!} +  \dfrac{\tau^5}{11\cdot5!} -  \dfrac{\tau^7}{15\cdot7!} + \dots +\dfrac{(-1)^{n-1} \tau^{2n-1}}{(4n-1)(2n-1)!}+ \dots\right); // 2\tau^{1/2}を抽出
    \\
    \\
      & = A\sqrt{2\tau}\left(\displaystyle\sum^{\infty}_{n=1}\dfrac{(-1)^{n-1} \tau^{2n-1}}{(4n-1)\cdot(2n-1)!}\right)
\end{array}
$$

これで、$x, y$どちらも無限級数で表せたのでコンピュータで計算可能になった。

また、これらに$(3)式\tau=\dfrac{L}{2R}と(4)式L=\sqrt2\tau$式を代入すると、クロソイド曲線ではお馴染みの計算式であることがわかる。

$$
    x = L\left(1 - \dfrac{L^2}{40R^2} +  \dfrac{L^4}{3456R^4} -  \dfrac{L^6}{599040R^6} +\dots\right),
    y  = \dfrac{L^2}{6R}\left(1 - \dfrac{L^2}{56R^2} +  \dfrac{L^4}{7040R^4} -  \dfrac{L^6}{1612800R^6} + \dots \right)
$$

## 数値計算上の工夫

一般に無限級数で表現される一般項をそのままコンピュータで計算する際には次の課題がある。

-   6 乗 7 乗など高次の項は整数値がコンピュータ上で扱える最大値を超えてしまい誤った数値になる
-   級数は小さい順や大きい順に計算しないと誤差が大きくなる
-   級数を有限項で打ち切る場合は、精度評価しておく必要がある

したがって、こうした無限級数の計算では、一般項そのものを計算するのではなく、隣接二項間漸化式を利用して各項を逐次計算する。各項は十分小さな値になったところで計算を終了すれば良い。この方針でクロソイド曲線を求めるアルゴリズムを以下に示す。

## 級数における係数数列の一般項

クロソイド曲線$(x,y)$の共通項の各項を要素とする数列をそれぞれ$x_n, y_n$とすると、$x, y$の式は次のようになる。

$$
\begin{array}{cll}
    x  = & A\sqrt{2\tau}(x_1+ x_2 + x_3 + \cdots), &
      x_n = \left\{ 1, -\dfrac{\tau^2}{5\cdot2!}, \dfrac{\tau^4}{9\cdot4!},
                      -\dfrac{\tau^6}{13\cdot6!}, \cdots \right\} \\
    \\
    y  = & A\sqrt{2\tau}(y_1+ y_2 + y_3 + \cdots), &
      y_n = \left\{ \dfrac{\tau}{3},
                 -\dfrac{\tau^3}{7\cdot3!}, \dfrac{\tau^5}{11\cdot5!},
                 -\dfrac{\tau^7}{15\cdot7!}, \cdots \right\}
\end{array}
$$

さらに偶数項を$x_n$奇数項目を$y_n$とする新しい数列$c_n$を考えると、$x, y$は次のようになる。

$$
\begin{array}{c}
    x  =  A\sqrt{2\tau}(x_1+ x_2 + x_3 + \cdots) = A\sqrt{2\tau}(c_0 + c_2 + c_4 + \cdots) \\
    \\
    y  =  A\sqrt{2\tau}(y_1+ y_2 + y_3 + \cdots) = A\sqrt{2\tau}(c_1 + c_3 + c_5 + \cdots) \\
    \\
    c_n = \left\{ 1, \dfrac{\tau}{3}, -\dfrac{\tau^2}{5\cdot2!},
        -\dfrac{\tau^3}{7\cdot3!}, \dfrac{\tau^4}{9\cdot4!},
        \dfrac{\tau^5}{11\cdot5!}, -\dfrac{\tau^6}{13\cdot6!},
        -\dfrac{\tau^7}{15\cdot7!}, \cdots
    \right\}
\end{array}
$$

この新しい数列$c_n$の隣接二項漸化式を求めるために$c_{n+1}とc_n$の商である数列$\dfrac{c_{n+1}}{c_n}$を考える。

$$
    \frac{c_{n+1}}{c_n} = \left\{
      \frac{\tau}{3\cdot1},
      -\frac{3\tau}{5\cdot2},
      \frac{5\tau}{7\cdot3},
      -\frac{7\tau}{9\cdot4},
      \frac{9\tau}{11\cdot5},
      -\frac{11\tau}{13\cdot6},
      \frac{13\tau}{15\cdot7}, \dots
    \right\} = \frac{(-1)^n(2n+1)\tau}{(2n+3)(n+1)}
$$

したがって数列$c_n$は、隣接二項間漸化式として$ c\_{n+1} = \dfrac{(-1)^n(2n+1)\tau}{(2n+3)(n+1)}c_n $ であることがわかった。

この漸化式を用いると初項$c_0=1$を与えるだけで数列$c_n$ の各項が求められ、計算過程において、数列$c_n$の元になった数列$x_n,y_n$を交互に計算していることがわかる。

$$
\begin{array}{cccl}
  c_0 =& 1 &=& 1 && &=& x_1\\
         & \\
  c_1 =& (-1)^0 \dfrac{\tau}{3\cdot1}c_0　&=& \dfrac{\tau}{3}\cdot1 &=&  \dfrac{\tau}{3} & = & y_1\\
         & \\
  c_2 =& (-1)^1 \dfrac{3\tau}{5\cdot2}c_1 &=& -\dfrac{3\tau}{5\cdot2!}\cdot \dfrac{\tau}{3} &=& -\dfrac{\tau^2}{5\cdot2!} &=& x_2\\
         & \\
  c_3 =& (-1)^2 \dfrac{5\tau}{7\cdot3}c_2 &=& \dfrac{5\tau}{7\cdot3} \cdot -\dfrac{\tau^2}{5\cdot2!}&=& - \dfrac{\tau^3}{7\cdot3!} &=& y_2\\
         & \\
  c_4 =& (-1)^3 \dfrac{7\tau}{9\cdot4}c_3 &=& -\dfrac{7\tau}{9\cdot4} \cdot  - \dfrac{\tau^3}{7\cdot3!}&=& \dfrac{\tau^4}{9\cdot4!} &=& x_3 \\
\dots
\end{array}
$$

数列$c_n$の漸化式から$x_1\rightarrow y_1 \rightarrow x_2 \rightarrow \dots$と順番に計算できる。これらを$x, y$に交互に足し合わせることで目的の$(x,y)$の理論式である(7)式に一致する。この時、$y_n$が十分小さくなるまで繰り返せば良い。

$$
\begin{array}{cl}
    x & = A\sqrt{2\tau}(c_0 + c_2 + c_4 + \cdots) = A\sqrt{2\tau}(x_1 + x_2 + x_3 + \cdots) \\
      & \\
      & = A\sqrt{2\tau}\left(1 - \dfrac{\tau^2}{5\cdot 2!} +  \dfrac{\tau^4}{9\cdot4!} -  \dfrac{\tau^6}{13\cdot6!} + \dots +\dfrac{(-1)^{n-1} \tau^{2(n-1)}}{(4n-3)(2n-2)!}+ \dots\right) \\
      & \\
    y & = A\sqrt{2\tau}(c_1 + c_3 + c_5 + \cdots) = A\sqrt{2\tau}(y_1 + y_2 + y_3 + \cdots)  \\
      & \\
      & = A\sqrt{2\tau}\left(\dfrac{\tau}{3} - \dfrac{\tau^3}{7\cdot 3!} +  \dfrac{\tau^5}{11\cdot5!} -  \dfrac{\tau^7}{15\cdot7!} + \dots +\dfrac{(-1)^{n-1} \tau^{2n-1}}{(4n-1)(2n-1)!}+ \dots\right)  \\
\end{array}
$$

---

## 丁張マンの中でのクロソイド曲線の計算コード

本稿で考察した内容そのもので実装がなされている。

```vba　.numberLines
T = Tau(A, R)
X = 1
Y = T/3
g = -Y
h = 1
I = 0
Do Until Abs(g) <= 0.00000000001
    g = (2 * h + 1) * T * g / (2 * h + 3)/ (h + 1)
    If I = 0 Then
        X = X + g
        I = 1
    Else
        Y = Y + g
        I = 0
        g = -g
    EndIf
    h = h + 1
Loop
j = Sqr(2 * Abs(T))
X = X * A * j
Y = Y * A * j
```

### 解説

-   1: $\tau$を計算
-   2: $x_1$を初期設定
-   3: $y_1$を初期設定
-   4: 一般項の係数$(-1)^n$部分
-   5: 一般項の添字$n$と同様
-   6: $x, y$を交互に計算するためのフラグ変数
-   7: 一般項の収束条件
-   8: 一般項そのもの
-   9-18: $x、y$に順次計算して足し合わせている
-   19-21: 係数調整

### 係数数列$c_n$の存在理由

係数数列$x_n, y_n$両方含む数列$c_n$を考えることにより、収束判定ループを一つにできるからである。

[^1]:
    微分方程式の解法
    ある関数$f(t)$の積分である$x(t)=\displaystyle\int f(t)dt$となる関数$x(t)$において、$x(t)$の微分は $\dfrac{dx}{dt}=\dfrac{d}{dt}\displaystyle\int f(t)dt = f(t)$となる。これにより、$f(t) = \dfrac{dx}{dt}$ を $x(t)$ の定義に代入すると $x(t) = \displaystyle\int \frac{dx}{dt}dt$となる。導関数を積分すれば元の関数に戻るこの性質[^3]を利用して微分方程式を解く。

[^2]:
    合成関数の微分 $dL= \frac{dL}{dt}\cdot \frac{dt}{d\tau}$
    $L=A\sqrt{t}, t = 2\tau$ の時、$ \frac{dL}{dt} = A\dfrac{1}{2}t^{\frac{1}{2}-1} = \frac{A}{2\sqrt{t}}$ であり、$\frac{dt}{d\tau}=2d\tau$。したがって、$dL=\dfrac{Ad\tau}{\sqrt{2\tau}}$

[^3]:
    微分積分学の基本定理
    積分した関数を微分すると元に戻り、微分した関数を積分しても元に戻る。微分と積分がお互いに逆演算であること。
