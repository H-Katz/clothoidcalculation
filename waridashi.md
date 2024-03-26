---
ebook:
    authors: '秦野克彦'
    title: '割り出し計算'

puppeteer:
    displayHeaderFooter: true
    headerTemplate: '<div style="font-size: 9px; margin-left: 1cm;"><span class=''title''></span>, <span class=''date''></span></div>'
    footerTemplate: '<div style="font-size: 9px; margin: 0 auto; "> <span class=''pageNumber''></span>/<span class=''totalPages''></span></div>'
---

<style>
  hr {
    opacity: 0;
    break-after: page;
  }
</style>

<div class="TOC">

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [割り出し](#割り出し)
  - [線分での割り出し](#線分での割り出し)
  - [単曲線での割り出し](#単曲線での割り出し)
  - [クロソイド曲線での割り出し](#クロソイド曲線での割り出し)
    - [$KA-KE$クロソイド$(R > 0)$](#ka-keクロソイドr--0)
    - [$KA-KE$クロソイド$(R < 0)$](#ka-keクロソイドr--0-1)
    - [$KA-KE$クロソイド](#ka-keクロソイド)
    - [$KE-KA$クロソイド$（R>0）$](#ke-kaクロソイドr0)
    - [$KE-KA$クロソイド$（R<0）$](#ke-kaクロソイドr0-1)
    - [$ KE-KA $クロソイド](#-ke-ka-クロソイド)
    - [卵形クロソイド$(KAE-KEE)$](#卵形クロソイドkae-kee)
    - [卵形クロソイド$(KEE-KAE)$](#卵形クロソイドkee-kae)
  - [補足](#補足)
    - [回転行列; 線形代数](#回転行列-線形代数)
    - [座標系の変換; 線形代数](#座標系の変換-線形代数)
    - [射影ベクトル; 数 II](#射影ベクトル-数-ii)
    - [余弦定理](#余弦定理)
    - [$sign$関数](#sign関数)
    - [方向角$\theta$](#方向角theta)
- [路線における割り出し計算](#路線における割り出し計算)
  - [複数の線形に一致する割り出し](#複数の線形に一致する割り出し)

<!-- /code_chunk_output -->
</div>

<div style="page-break-before:always"></div>

$$
\gdef\vectwo#1#2{\begin{pmatrix} #1 \\ #2 \end{pmatrix}}
\gdef\R#1{\begin{pmatrix} \cos#1 & -\sin#1 \\ \sin#1 & \cos#1 \end{pmatrix}}
\gdef\Rinv#1{\begin{pmatrix} \cos#1 & \sin#1 \\ -\sin#1 & \cos#1 \end{pmatrix}}
\gdef\Rinvthree#1#2#3{\begin{pmatrix} (#2)\cos#1 + (#3)\sin#1 \\ -(#2)\sin#1 + (#3)\cos#1 \end{pmatrix}}
\gdef\clothox#1{\dfrac{A}{\sqrt2} \displaystyle\int^{#1}_0 \dfrac{\cos\tau}{\sqrt{\tau}} d\tau}
\gdef\clothoy#1{\dfrac{A}{\sqrt2} \displaystyle\int^{#1}_0 \dfrac{\sin\tau}{\sqrt{\tau}} d\tau}
$$

# 割り出し

割り出しとは、平面直角座標系上の点 $P(x, y)$を路線座標系の点$(l, w)$に変換する計算のことである。3 つの線形(線分、単曲線、クロソイド曲線)から構成される曲線である「路線」は、路線距離$l$の点$Q$で直線$QP$と直交する。この時の直線$QP$との位置を幅$w$で表現すると、点$(l, w)$は路線に沿って湾曲した座標系を構成する。

## 線分での割り出し

曲線長$L$の線分$AB$に対して、平面直角座標系上の点 $P(x, y)$から路線座標系上の点 $P(l, w)$への変換を考える。具体的には、軸$X$と線分$AB$ のなす角を$\theta$と置く。線分での割り出しを次の図で示す。

<img src="figure/segment.png" width="300"></img>

点$P(l, w)$の座標系として、線分$AB$の始点$A(x_0, y_0)$を原点とし、線分$AB$方向を軸$L$、始点$A$を通って点$P$の軸 $L$ に直交する軸$W$ を考える。これは元の座標系を始点 $A$ を原点として、方向角$\theta$だけ回転させたものと一致する。したがって、逆回転行列を$R^{-1}(\theta)$とすると 点 $P(l, w)$には次の式が成り立つ。

$$
\vectwo{l}{w} = R^{-1}(\theta) \vectwo{x-x_0}{y - y_0} = \Rinv{\theta}\vectwo{x-x_0}{y -y_0}
$$

この時、点$P$の軸 $L$ についての垂線は、線分 $AB$ 上で交わるとは限らない。交点が存在する条件は　$ 0 \le l \lt L = |\vec{AB}|$ である。

以上により、線分$AB$に対する割り出しは次の通りである。

$$
\vectwo{l}{w} = \Rinvthree{\theta}{x - x_0}{y - y_0} \quad (0 \le l \lt L)
$$

交点 $Q$ は次の通りである。

$$
\begin{array}{cl}
\vec{OQ} & = \vec{OA} + \vec{AQ} = \vec{OA} + l\vec{e_L} =
\vectwo{x_0}{y_0}+l\vectwo{\cos\theta}{\sin\theta}\\
 & = \vectwo{x_0 + ((x - x_0)\cos\theta+(y - y_0)\sin\theta)\cos\theta}{y_0 + ((x - x_0)\cos\theta+(y - y_0)\sin\theta)\sin\theta}
\end{array}
$$

## 単曲線での割り出し

線分の場合と同様に曲線長$L$である単曲線$AB$に対して、平面直角座標系上の点 $P(x, y)$から路線座標系上の点 $P(l, w)$への変換を考える。具体的には、単曲線$AB$は中心点$C(x_c,y_c)$で、半径 $ R $、単曲線の始点 $ A(x_a, y_a) $ に対する接線方向角を $\tau$、$\vec{CA}$と$\vec{CP}$との**符号付き角度を$\phi$と置く**。ここで、単曲線の場合の割り出し計算を次の図に示す。単曲線の場合、反時計回りと時計回りの 2 つの場合を考える必要がある。反時計回りの場合は、$R>0, \theta>0$ であり、時計回りの場合は、$　R<0, \theta < 0$となる

<img src="figure/arc.png" width="600"></img>

曲線距離$l$について、円弧$AQ$は半径$R$で角度$\phi$の円弧である。したがって、$l=R\phi$である。反時計回りの場合も、時計回りの場合も、$l$は正の値を取るので同じ式となる。ここで、一般的に 2 点を与えられた時の角度$\theta_{CA}$の定義式を示す。式中の分子の$\times$は外積演算、分母の$\cdot$は内積演算である。また、$\vec{e_X}$は軸 $X$ の方向ベクトルであるので、$\vec{e_X} = (1, 0)$である。

$$
 \tan\theta_{CA} = \dfrac{|\vec{e_X}|\cdot|\vec{CA}|\sin\theta_{CA}}{|\vec{e_X}|\cdot|\vec{CA}|\cos\theta_{CA}} = \dfrac{\vec{e_X} \times \vec{CA}}{ \vec{e_X}\cdot \vec{CA}} =
 \dfrac{1\cdot(y_a-y_c) - 0\cdot(x_a-x_c)}{1\cdot(x_a-x_c)+0\cdot(y_a-y_c)} =
\dfrac{y_a-y_c}{x_a-x_c}
\\\\
\therefore \theta_{CA} = \arctan{\dfrac{y_a-y_c}{x_a-x_c}}
$$

これにより、符号付き角度$\phi$は、次のようになる。

$$
\phi = \theta_{CP} - \theta_{CA} = \arctan{\dfrac{y-y_c}{x-x_c}} - \arctan{\dfrac{y_a-y_c}{x_a-x_c}}
$$

さらなる条件として、直線$CP$は、単曲線$AB$と交わるとは限らない。交点$Q$が存在する条件は$0 \le |\phi| \lt L/|R|$である。

次に、幅$w$について、単曲線$AB$と直線$CP$の交点$Q$を原点とし、点$Q$の接線方向を軸$U$、軸 $U$ と直交する軸 $W$ を取る座標系を考える。軸$W$は交点$Q$の接線方向に対し左が正になるので、正負の向きに注意すると幅$w$は次の通りである。

$$
w = \begin{cases}
R  - |\vec{CP}|  & \text{if} & R \ge 0 \\
R  + |\vec{CP}|  & \text{if} & R < 0
\end{cases}
$$

以上により、単曲線の場合の割り出し計算式は次の通りである。

$$
\begin{array}{cll}
\vectwo{l}{w} & = \vectwo{R\phi}{R - sign(R)\sqrt{(x-x_c)^2+(y-y_c)^2}}
\\
\\
 & \phi = \arctan{\dfrac{y-y_c}{x-x_c}} - \arctan{\dfrac{y_a-y_c}{x_a-x_c}} \qquad  (0 \le |\phi| \lt L/|R|)
\end{array}
$$

この場合、単曲線$AB$と直線$CP$の交点$Q(x_q,y_q)$の座標は、線分$CA$を点$C$を中心に角度$\phi$回転させた点となる。

$$
\begin{array}{cl}
\begin{pmatrix}
x_q \\
y_q
\end{pmatrix} & =　R(\phi)\vectwo{x_a - x_c}{y_a - y_c}+\vectwo{x_c}{y_c}
\\\\
& =\begin{pmatrix}
(x_a - x_c)\cos\phi -  (y_a - y_c)\sin\phi + x_c\\
(x_a - x_c)\sin\phi +  (y_a - y_c)\cos\phi + y_c
\end{pmatrix}
\end{array}
$$

## クロソイド曲線での割り出し

これまで同様に曲線長$L$であるクロソイド曲線に対して、平面直角座標系上の点 $P(x, y)$から路線座標系上の点 $P(l, w)$への変換を考える。具体的にクロソイド曲線は、始点 $KA(x_{KA},y_{KA})$で接線方向角$\theta$、終端 $KE$ での半径 $R$、クロソイドパラメータは $A$ とする。ここで、求める点 $P$ のクロソイド曲線に対する垂線との交点 $K$ を求めるために、$KA$ を原点としクロソイド曲線の接線方向角を軸 $U$、軸 $U$ と直交する軸 $V$ を設定する。これらを説明する図を次に示す。なお、反時計回りの場合は、$R>0, \theta>0$ であり、時計回りの場合は、$　R<0, \theta < 0$である。

### $KA-KE$クロソイド$(R > 0)$

まず、原座標系を下左図で、変換後の小座標系を下右図に示す。下右図は、$KA$ を原点としクロソイド曲線の接線方向角を軸 $U$、軸 $U$ と直交する軸 $V$ とする座標系である。

<img src="figure/clothoidKAKE_Rp.png" width="800"></img>

この小座標系への変換は次の通りである。

$$
\begin{pmatrix}
u \\
v
\end{pmatrix} =
R^{-1}(\theta) \begin{pmatrix}
x - x_{KA} \\
y - y_{KA}
\end{pmatrix} =
\begin{pmatrix}
\cos\theta & \sin\theta \\
-\sin\theta & \cos\theta
\end{pmatrix}
\begin{pmatrix}
x - x_{KA} \\
y - y_{KA}
\end{pmatrix}
$$

以降は全てこの小座標系で議論する。

求める点 $P(l, w)$ に対するクロソイド上の点 $Q$ が接線方向角$\phi$を持つ時、点 $Q$を原点として接線方向を軸とする座標変換を考える。まず、クロソイド曲線の始点 $KA$ を $Q_0(u_0, v_0)$とする。ここで、$u_0 = v_0 = 0$ であり、接線方向角 $\phi_0 = 0$、クロソイド長 $l_0=0$ である。この座標系で求める点 $P(l_0, w_0)$は次の通りになる。

$$
\begin{pmatrix}
l_0 \\
w_0
\end{pmatrix} =
R^{-1}(\phi_0) \begin{pmatrix}
u - u_0 \\
v - v_0
\end{pmatrix} =
\begin{pmatrix}
\cos\phi_0 & \sin\phi_0 \\
-\sin\phi_0 & \cos\phi_0
\end{pmatrix}
\begin{pmatrix}
u - u_0 \\
v - v_0
\end{pmatrix}
$$

次に、この $l_0$ をクロソイド長とする点$Q_1(u_1, v_1)$を考える。$\phi_1 = \dfrac{l_0}{2R}$、$u_1 = \clothox{\phi_1}$、$v_1 = \clothoy{\phi_1}$ である。この点$Q_1$ を原点とする座標系で求める点 $P(l_1, w_1)$は次の通りになる。

$$
\begin{pmatrix}
l_1 \\
w_1
\end{pmatrix} =
\begin{pmatrix}
\cos\phi_1 & \sin\phi_1 \\
-\sin\phi_1 & \cos\phi_1
\end{pmatrix}
\begin{pmatrix}
u - u_1 \\
v - v_1
\end{pmatrix}
$$

次に$l_0 + l_1$をクロソイド長とする点$Q_2(u_2, v_2)$を考える。$\phi_2 = \dfrac{l_0+l_1}{2R}$、$u_2 = \clothox{\phi_2}$、$v_2 = \clothoy{\phi_2}$ である。

これを続けていくと$\displaystyle\lim_{n\to\infty}l_n = 0$となり、点$Q_n$は求める点$Q$に収束する。計算上、十分 $0$ に近い値となるのが$l_k$である時、求める点 $P(l, w)$が次のように定まる。ここで、この点$Q$がクロソイド曲線上に存在するためには、$0 \le l \lt L$ でなければならない。

$$
\begin{array}{cll}
\begin{pmatrix}
l \\
w
\end{pmatrix}  & =
\begin{pmatrix}
l_0 + l_1 + \cdots + l_k \\
w_k
\end{pmatrix}　 (0 \le l < L)
\\
\\
\begin{pmatrix}
l_n \\
w_n
\end{pmatrix} & =
\begin{pmatrix}
\cos\phi_n & \sin\phi_n \\
-\sin\phi_n & \cos\phi_n
\end{pmatrix}
\begin{pmatrix}
u - u_n \\
v - v_n
\end{pmatrix}
\\
\\
 & \phi_k = \dfrac{\sum^k_{n=0}l_n}{2R}, \quad u_k = \clothox{\phi_k}, \quad v_n = \clothoy{\phi_k}
 \\
 \\
 \vectwo{x_q}{y_q} & = \R{\theta}\vectwo{u_k}{v_k}+\vectwo{x_{KA}}{y_{KA}}
\end{array}
$$

### $KA-KE$クロソイド$(R < 0)$

まず、原座標系を下左図で、変換後の小座標系を下右図に示す。下右図は、$KA$ を原点としクロソイド曲線の接線方向角を軸 $U$、軸 $U$ と直交する軸 $V$ とする座標系である。

<img src="figure/clothoidKAKE_Rn.png" width="800"></img>

この小座標系への変換は次の通りである。これは、$R>0$の場合と同じである。

$$
\begin{pmatrix}
u \\
v
\end{pmatrix} =
R^{-1}(\theta) \begin{pmatrix}
x - x_{KA} \\
y - y_{KA}
\end{pmatrix} =
\begin{pmatrix}
\cos\theta & \sin\theta \\
-\sin\theta & \cos\theta
\end{pmatrix}
\begin{pmatrix}
x - x_{KA} \\
y - y_{KA}
\end{pmatrix}
\\
\\
\therefore\begin{pmatrix}
u \\
v
\end{pmatrix} =
\begin{pmatrix}
(x - x_{KA})\cos\theta +(y - y_{KA})\sin\theta \\
-(x - x_{KA})\sin\theta +(y - y_{KA})\cos\theta
\end{pmatrix}
$$

以降は全てこの小座標系で議論する。

求める点 $P(l, w)$ に対するクロソイド上の点 $Q$ が接線方向角$\phi$を持つ時、点 $Q$を原点として接線方向を軸とする座標変換を考える。まず、クロソイド曲線の始点 $KA$ を $Q_0(u_0, v_0)$とする。ここで、$u_0 = v_0 = 0$ であり、接線方向角 $\phi_0 = 0$、クロソイド長 $l_0=0$ である。この座標系で求める点 $P(l_0, w_0)$は次の通りになる。

$$
\begin{pmatrix}
l_0 \\
w_0
\end{pmatrix} =
R^{-1}(\phi_0) \begin{pmatrix}
u - u_0 \\
v - v_0
\end{pmatrix} =
\begin{pmatrix}
\cos\phi_0 & \sin\phi_0 \\
-\sin\phi_0 & \cos\phi_0
\end{pmatrix}
\begin{pmatrix}
u - u_0 \\
v - v_0
\end{pmatrix}
$$

次に、この $l_0$ をクロソイド長とする点$Q_1(u_1, v_1)$を考える。$\phi_1 = \dfrac{l_0}{2R}$、$u_1 = \clothox{|\phi_1|}$、$\boxed{v_1 = -\clothoy{|\phi_1|}}$ である。この点$K_1$ を原点とする座標系で求める点 $P(l_1, w_1)$は次の通りになる。

$$ \vectwo{l_1}{w_1} =\Rinv{\phi_1}\vectwo{u-u_1}{v-v_1}$$

次に$l_0 + l_1$をクロソイド長とする点$Q_2(u_2, v_2)$を考える。$\phi_2 = \dfrac{l_0+l_1}{2R}$、$u_2 = \clothox{|\phi_2|}$、$\boxed{v_2 = -\clothoy{|\phi_2|}}$ である。

これを続けていくと$\displaystyle\lim_{n\to\infty}l_n = 0$となり、点$Q_n$は求める点$Q$に収束する。計算上、十分 $0$ に近い値となるのが$l_k$である時、求める点 $P(l, w)$が次のように定まる。ここで、この点$Q$がクロソイド曲線上に存在するためには、$0 \le l \lt L$ でなければならない。

$$
\begin{array}{cll}
\begin{pmatrix}
l \\
w
\end{pmatrix} & =
\begin{pmatrix}
l_0 + l_1 + \cdots + l_k \\
w_k
\end{pmatrix}　 \quad (0 \le l < L)
\\
\\
\begin{pmatrix}
l_n \\
w_n
\end{pmatrix} & =
\begin{pmatrix}
\cos\phi_n & \sin\phi_n \\
-\sin\phi_n & \cos\phi_n
\end{pmatrix}
\begin{pmatrix}
u - u_n \\
v - v_n
\end{pmatrix}
\\
\\
& \phi_k  = \dfrac{\sum^k_{n=0}l_n}{2R}, \quad u_k = \clothox{|\phi_k|}, \quad v_k = - \clothoy{|\phi_k|}
\\
\\
 \vectwo{x_q}{y_q} & = \R{\theta}\vectwo{u_k}{v_k}+\vectwo{x_{KA}}{y_{KA}}
\end{array}
$$

### $KA-KE$クロソイド

以上、$KA-KE$ クロソイドの割り出し計算式は以下の通りまとめることができる。

$$
\begin{array}{cll}
\begin{pmatrix}
u \\
v
\end{pmatrix} & =
\begin{pmatrix}
(x - x_{KA})\cos\theta +(y - y_{KA})\sin\theta \\
-(x - x_{KA})\sin\theta +(y - y_{KA})\cos\theta
\end{pmatrix}
\\
\\
\begin{pmatrix}
l \\
w
\end{pmatrix} & =
\begin{pmatrix}
l_0 + l_1 + \cdots + l_k \\
w_k
\end{pmatrix}　 \quad (0 \le l < L)
\\
\\
\begin{pmatrix}
l_n \\
w_n
\end{pmatrix} & =
\begin{pmatrix}
\cos\phi_n & \sin\phi_n \\
-\sin\phi_n & \cos\phi_n
\end{pmatrix}
\begin{pmatrix}
u - u_n \\
v - v_n
\end{pmatrix}
\\
\\
& \phi_k  = \dfrac{\sum^k_{n=0}l_n}{2R}, \quad u_k = \clothox{|\phi_k|}, \quad v_k = sign(R)\clothoy{|\phi_k|}
\\
\\
 \vectwo{x_q}{y_q} & = \R{\theta}\vectwo{u_k}{v_k}+\vectwo{x_{KA}}{y_{KA}}
\end{array}
$$

### $KE-KA$クロソイド$（R>0）$

$KE-KA$ クロソイドの場合も同様に、$KA$ を原点としクロソイド曲線の接線方向角と逆向きを軸 $U$、軸 $U$ と直交する軸 $V$ とする座標系を取る。この小座標系への変換は次の通りである。

$$
\begin{pmatrix}
u \\
v
\end{pmatrix} =
R^{-1}(\theta+\tau) \begin{pmatrix}
x - x_{KA} \\
y - y_{KA}
\end{pmatrix}
$$

ここで、点$KA$ は次の方程式を満たす。

$$
\begin{array}{c}
R^{-1}(\theta+\tau) \begin{pmatrix}
x_{KA} - x_{KE} \\
y_{KA} - y_{KE}
\end{pmatrix} =
\begin{pmatrix}
x_\tau \\
-y_\tau
\end{pmatrix}
\\
\\
\therefore \vectwo{x_{KA}}{y_{KA}} = R(\theta+\tau)\vectwo{x_\tau}{-y_\tau}+ \vectwo{x_{KE}}{y_{KE}}
\\
\\
\tau = \dfrac{L}{2R}, \quad x_\tau = \clothox{\tau}, \quad y_\tau = \clothoy{\tau}
\end{array}
$$

$KE-KA　$ クロソイド は点$KE$が始点であるから、点$KA$の式を代入して点$KE$の式にする。

$$
\begin{pmatrix}
u \\
v
\end{pmatrix} =
R^{-1}(\theta+\tau) \begin{pmatrix}
x - x_{KE} \\
y - y_{KE}
\end{pmatrix} - \vectwo{x_\tau}{-y_\tau}
$$

以降はこの小座標系$(u,v)$で議論する。この小座標系は、$KA-KE$クロソイドの$R<0$の形状を原点を中心に 180 度回転させものと一致する。したがって、求める点 $P(l, w)$ に対するクロソイド上の点 $Q$ に至るまで、次の同じ式が成り立つ。ここで、$u_0 = v_0 = 0$ であり、接線方向角 $\phi_0 = 0$、クロソイド長 $l_0=0$ である。

$$
\begin{array}{cl}
\vectwo{l_n}{w_n} & = \Rinv{\phi_n}\vectwo{u-u_n}{v-v_n}
\\
\\
& \phi_n = \dfrac{\sum^n_{k=0}l_k}{2R}, \quad u_n = - \clothox{|\phi_n|}, \quad v_n = \clothoy{|\phi_n|}
\end{array}
$$

点$Q_n(u_n,v_n)$は求める点$Q$に収束する。計算上、十分 $0$ に近い値となるのが$l_k$である時、求める点 $P(l, w)$が次のように定まる。$l$は、点$KE$からの曲線長なので、曲線長 $L$に累積曲線長$\sum^k_{n=0}l_n$ を加えることになる。ここで、この点$K$がクロソイド曲線上に存在するためには、$0 \le l \lt L$ でなければならない。

$$
\begin{array}{cll}
\begin{pmatrix}
l \\
w
\end{pmatrix}  & =
\begin{pmatrix}
L ＋ (l_0 + l_1 + \cdots + l_k) \\
w_k
\end{pmatrix}　 (0 \le l < L)
\\
\\
\begin{pmatrix}
l_n \\
w_n
\end{pmatrix} & =
\begin{pmatrix}
\cos\phi_n & \sin\phi_n \\
-\sin\phi_n & \cos\phi_n
\end{pmatrix}
\begin{pmatrix}
u - u_n \\
v - v_n
\end{pmatrix}
\\
\\
\phi_k & = \dfrac{\sum^k_{n=0}l_n}{2R}, \quad u_k = -\clothox{|\phi_k|}, \quad v_k = \clothoy{|\phi_k|}
\end{array}
$$

### $KE-KA$クロソイド$（R<0）$

前節同同様に、点$KA$ を原点としクロソイド曲線の接線方向角を軸 $U$、軸 $U$ と直交する軸 $V$ とする座標系であるぜこの小座標系への変換は次の通りである。

$$
\begin{pmatrix}
u \\
v
\end{pmatrix} =
R^{-1}(\theta-\tau) \begin{pmatrix}
x - x_{KA} \\
y - y_{KA}
\end{pmatrix}
$$

ここで、点$KA$ は次の方程式を満たす。

$$
\begin{array}{c}
R^{-1}(\theta-\tau) \begin{pmatrix}
x_{KA} - x_{KE} \\
y_{KA} - y_{KE}
\end{pmatrix} =
\begin{pmatrix}
x_\tau \\
y_\tau
\end{pmatrix}
\\
\\
\therefore
\begin{pmatrix}
x_{KA} \\
y_{KA}
\end{pmatrix} =
R(\theta-\tau) \begin{pmatrix}
x_\tau \\
y_\tau
\end{pmatrix} +
\begin{pmatrix}
x_{KE} \\
y_{KE}
\end{pmatrix}
\\
\\
\tau = \dfrac{L}{2|R|}, \quad x_\tau = \dfrac{A}{\sqrt2}\displaystyle\int^{\tau}_0 \dfrac{\cos\tau}{\sqrt\tau} d\tau, \quad y_\tau = \dfrac{A}{\sqrt2}\displaystyle\int^{\tau}_0 \dfrac{\sin\tau}{\sqrt\tau} d\tau
\end{array}
$$

$KE-KA　$ クロソイド は点$KE$が始点であるから、点$KA$の式を代入して点$KE$の式にする。

$$
\begin{pmatrix}
u \\
v
\end{pmatrix} =
R^{-1}(\theta-\tau) \begin{pmatrix}
x - x_{KE} \\
y - y_{KE}
\end{pmatrix} - \vectwo{x_\tau}{y_\tau}
$$

以降はこの小座標系$(u,v)$で議論する。この小座標系は、$KA-KE$クロソイドの$R>0$の形状と一致する。したがって、求める点 $P(l, w)$ に対するクロソイド上の点 $Q$ に至るまで、次の同じ式が成り立つ。ここで、$u_0 = v_0 = 0$ であり、接線方向角 $\phi_0 = 0$、クロソイド長 $l_0=0$ である。

$$
\begin{array}{cl}
\vectwo{l_n}{w_n} & = \Rinv{\phi_n}\vectwo{u-u_n}{v-v_n}
\\
\\
& \phi_n = \dfrac{\sum^n_{k=0}l_k}{2R}, \quad u_n = -\clothox{\phi_n}, \quad v_n = - \clothoy{\phi_n}
\end{array}
$$

点$Q_n(u_n,v_n)$は求める点$Q$に収束する。計算上、十分 $0$ に近い値となるのが$l_k$である時、求める点 $P(l, w)$が次のように定まる。$l$は、点$KE$からの曲線長なので、曲線長 $L$に累積曲線長$\sum^k_{n=0}l_n$ を加えることになる。ここで、この点$K$がクロソイド曲線上に存在するためには、$0 \le l \lt L$ でなければならない。

$$
\begin{array}{cll}
\begin{pmatrix}
l \\
w
\end{pmatrix}  & =
\begin{pmatrix}
L + (l_0 + l_1 + \cdots + l_k) \\
w_k
\end{pmatrix}　 (0 \le l < L)
\\
\\
\begin{pmatrix}
l_n \\
w_n
\end{pmatrix} & =
\begin{pmatrix}
\cos\phi_n & \sin\phi_n \\
-\sin\phi_n & \cos\phi_n
\end{pmatrix}
\begin{pmatrix}
u - u_n \\
v - v_n
\end{pmatrix}
\\
\\
\phi_k & = \dfrac{\sum^k_{n=0}l_n}{2R}, \quad u_k = -\clothox{\phi_k}, \quad v_k =  -\clothoy{\phi_k}
\end{array}
$$

### $ KE-KA $クロソイド

以上、$KE-KA$ クロソイドの割り出し計算式は以下の通りまとめることができる。$R>0 $ の時、次の通りである。

$$
\begin{array}{cl}
\vectwo{u}{v} & =
R^{-1}(\theta+\tau) \begin{pmatrix}
x - x_{KE} \\
y - y_{KE}
\end{pmatrix} - \vectwo{x_\tau}{-y_\tau} \\\\
& \tau = \dfrac{L}{2R}, \quad x_\tau = \clothox{\tau}, \quad y_\tau = \clothoy{\tau} \\\\
\end{array}
$$

$R<0 $ の時、次の通りである。

$$
\begin{array}{cl}
\vectwo{u}{v} & = R^{-1}(\theta-\tau)
\begin{pmatrix}
x - x_{KE} \\
y - y_{KE}
\end{pmatrix} - \vectwo{x_\tau}{y_\tau} \\\\
& \tau = \dfrac{L}{2|R|}, \quad x_\tau = \dfrac{A}{\sqrt2}\displaystyle\int^{\tau}_0 \dfrac{\cos\tau}{\sqrt\tau} d\tau, \quad y_\tau = \dfrac{A}{\sqrt2}\displaystyle\int^{\tau}_0 \dfrac{\sin\tau}{\sqrt\tau} d\tau
\end{array}
$$

まず、$(u, v)$への変換の逆行列について、$R < 0$ の時、$|R|$の絶対値を外すと、$\tau = - \dfrac{L}{2R}$であり、$(u, v)$への変換式は $R>0$の場合と同じである。

$$
\begin{array}{cll}
\Rinv{(\theta-\tau)} & = \Rinv{(\theta+\frac{L}{2R})} \quad (R < 0)
\\
\\
\Rinv{(\theta+\tau)} & = \Rinv{(\theta+\frac{L}{2R})} \quad (R > 0)
\end{array}
$$

次に、$y_\tau$の符号の違いを吸収するためには、$x_\tau = \clothox{|\tau|}, \quad y_\tau = - sign(R)\clothox{|\tau|}$とすればよい。

まとめると、$KE-KA$ クロソイドの場合は、次の通りとなる。

$$
\begin{array}{cll}
\begin{pmatrix}
u \\
v
\end{pmatrix} & = R^{-1}(\theta+\tau)
\begin{pmatrix}
x - x_{KE} \\
y - y_{KE}
\end{pmatrix} -
\begin{pmatrix}
x_\tau \\
y_\tau
\end{pmatrix}
\\
\\
& \tau = \dfrac{L}{2R}, \quad x_\tau = \dfrac{A}{\sqrt2}\displaystyle\int^{|\tau|}_0 \dfrac{\cos\tau}{\sqrt\tau} d\tau, \quad y_\tau = -sign(R)\dfrac{A}{\sqrt2}\displaystyle\int^{|\tau|}_0 \dfrac{\sin\tau}{\sqrt\tau} d\tau
\\
\\
\begin{pmatrix}
l \\
w
\end{pmatrix}  & =
\begin{pmatrix}
L + (l_0 + l_1 + \cdots + l_k) \\
w_k
\end{pmatrix}　 (0 \le l < L)
\\
\\
\begin{pmatrix}
l_n \\
w_n
\end{pmatrix} & =
\begin{pmatrix}
\cos\phi_n & \sin\phi_n \\
-\sin\phi_n & \cos\phi_n
\end{pmatrix}
\begin{pmatrix}
u - u_n \\
v - v_n
\end{pmatrix}
\\
\\
& \phi_k = \dfrac{\sum^k_{n=0}l_n}{2R}, \quad u_k = -\clothox{|\phi_k|}, \quad v_k = sign(R)\clothoy{|\phi_k|}
\end{array}
$$

### 卵形クロソイド$(KAE-KEE)$

クロソイドパラメータを $A$ とする卵形クロソイドは、基本クロソイド の$KA-KE$ の間に始点 $KAE$ を持ち、終端 $KE$ は終点$KEE$ と一致する。今、この点 $KAE$ での半径を $R_1$、終点 $KEE$ での半径を $R_2$ として($R_1 > R_2$)、 点 $KA$ を求める。この点 $KAE$ または点 $KEE$ を所与の点として点 $KA$ が分かれば、前節までの基本クロソイドの式を全て再利用して割り出し計算を実施できる。ただし、交点 $K$ の存在する条件は、$l' \le l < l' + L $ である。ここで$l'$は点$KA-KAE$のクロソイド曲線長($= \dfrac{A^2}{|R_1|}$)である。

$R_1>R_2>0$ である卵形クロソイドの点$KAE(x_{KAE},y_{KAE})$での接線方向角を$\theta$、卵形クロソイドを包含する基本クロソイドとしての接線方向角$\tau$とする。この角度$\tau$での基本クロソイドとしての座標を$(x_\tau, y_\tau)$とする。すると、原座標での点$KA(x_{KA},y_{KA})$は次の方程式を満たす。

$$
R(-\theta+\tau)\begin{pmatrix}
x_{KA} - x_{KAE} \\
y_{KA} - y_{KAE}
\end{pmatrix} +
\begin{pmatrix}
x_\tau \\
y_\tau
\end{pmatrix} =
\begin{pmatrix}
0 \\
0
\end{pmatrix}
$$

これを点$KA(x_{KA},y_{KA})$について解くと、

$$
\begin{pmatrix}
x_{KA}\\
y_{KA}
\end{pmatrix} =
R^{-1}(-\theta+\tau)\begin{pmatrix}
0 - x_{\tau} \\
0 - y_{\tau}
\end{pmatrix} +
\begin{pmatrix}
x_{KAE} \\
y_{KAE}
\end{pmatrix} =
R(\theta-\tau)
\begin{pmatrix} - x_{\tau} \\ - y_{\tau}
\end{pmatrix} +
\begin{pmatrix}
x_{KAE} \\
y_{KAE}
\end{pmatrix}
$$

同様に、$R_2 < R_1 < 0$ の時、

$$
\begin{pmatrix}
x_{KA}\\
y_{KA}
\end{pmatrix} =
R(\theta+\tau)\begin{pmatrix} - x_{\tau} \\ y_{\tau}
\end{pmatrix} +
\begin{pmatrix}
x_{KAE} \\
y_{KAE}
\end{pmatrix}
$$

となる。どちらも次の値を使う。

$$
\tau = \dfrac{l'}{2|R_1|}, \quad x_{\tau} = \dfrac{A}{\sqrt2}\int^{\tau}_0 \dfrac{\cos\tau}{\sqrt \tau}d\tau, \quad y_{\tau} = \dfrac{A}{\sqrt2}\int^{\tau}_0 \dfrac{\sin\tau}{\sqrt \tau}d\tau
$$

ここで、次の式に置き換えると式を共通化できる。

$$
\tau = \dfrac{l'}{2R_1}, \quad x_{\tau} = \dfrac{A}{\sqrt2}\int^{|\tau|}_0 \dfrac{\cos\tau}{\sqrt \tau}d\tau, \quad y_{\tau} = sign(R_1)\dfrac{A}{\sqrt2}\int^{|\tau|}_0 \dfrac{\sin\tau}{\sqrt \tau}d\tau
$$

さらに$KAE-KEE$ クロソイドは、点$KAE$が始点であるから式をまとめると次の通りとなる。

$$
\begin{array}{cl}
\begin{pmatrix}
u \\
v
\end{pmatrix} & = R^{-1}(\theta)
\begin{pmatrix}
x - x_{KA} \\
y - y_{KA}
\end{pmatrix} = R^{-1}(\theta)
\begin{pmatrix}
x - x_{KAE} \\
y - y_{KAE}
\end{pmatrix} - R^{-1}(\theta)R(\theta-\tau)
\begin{pmatrix} - x_{\tau} \\ - y_{\tau}\end{pmatrix}
\\\\
& = R^{-1}(\theta)
\begin{pmatrix}
x - x_{KAE} \\
y - y_{KAE}
\end{pmatrix} + R^{-1}(\tau)\begin{pmatrix} x_{\tau} \\ y_{\tau}\end{pmatrix}
\end{array}
$$

まとめると、$KAE-KEE$ 卵形クロソイドの場合次の式が成り立つ

$$
\begin{array}{cl}
\begin{pmatrix}
u \\
v
\end{pmatrix} & = R^{-1}(\theta)
\begin{pmatrix}
x - x_{KAE} \\
y - y_{KAE}
\end{pmatrix} + R^{-1}(\tau)\begin{pmatrix} x_{\tau} \\ y_{\tau}\end{pmatrix}
\\\\
\begin{pmatrix}
l \\
w
\end{pmatrix} & =
\begin{pmatrix}
l' + l_0 + l_1 + \cdots + l_k \\
w_k
\end{pmatrix}　(l' \le l < l' + L)
\\
\\
& l'  = \dfrac{A^2}{|R_1|}, \quad \tau = \dfrac{l'}{2R_1}, \quad x_\tau = \dfrac{A}{\sqrt2} \displaystyle\int^{|\tau|}_0 \dfrac{\cos(\tau)}{\sqrt{\tau}} d\tau, \quad y_\tau = sign(R_1)\dfrac{A}{\sqrt2} \displaystyle\int^{|\tau|}_0 \dfrac{\sin(\tau)}{\sqrt{\tau}} d\tau \\\\
 \begin{pmatrix}
l_n \\
w_n
\end{pmatrix} & =
\begin{pmatrix}
\cos\phi_n & \sin\phi_n \\
-\sin\phi_n & \cos\phi_n
\end{pmatrix}
\begin{pmatrix}
u - u_n \\
v - v_n
\end{pmatrix}
\\
\\
& \phi_k  = \dfrac{\sum^k_{n=0}l_n}{2R_2}, \quad u_k = \dfrac{A}{\sqrt2} \displaystyle\int^{|\phi_k|}_0 \dfrac{\cos(\tau)}{\sqrt{\tau}} d\tau, \quad v_k = sign(R_1)\dfrac{A}{\sqrt2} \displaystyle\int^{|\phi_k|}_0 \dfrac{\sin(\tau)}{\sqrt{\tau}} d\tau
\end{array}
$$

### 卵形クロソイド$(KEE-KAE)$

$KE-KA$クロソイドの場合を原則そのまま利用できる。

$$
\begin{array}{cll}
\begin{pmatrix}
u \\
v
\end{pmatrix} & = R^{-1}(\theta+\tau)
\begin{pmatrix}
x - x_{KE} \\
y - y_{KE}
\end{pmatrix} -
\begin{pmatrix}
x_\tau \\
y_\tau
\end{pmatrix}
\\
\\
& l' = \dfrac{A^2}{|R_1|}, \quad \tau = \dfrac{l' + L}{2R_2}, \quad x_\tau = - \dfrac{A}{\sqrt2}\displaystyle\int^{|\tau|}_0 \dfrac{\cos\tau}{\sqrt\tau} d\tau, \quad y_\tau = - sign(R_2)\dfrac{A}{\sqrt2}\displaystyle\int^{|\tau|}_0 \dfrac{\sin\tau}{\sqrt\tau} d\tau
\\
\\
\begin{pmatrix}
l \\
w
\end{pmatrix}  & =
\begin{pmatrix}
l' + L + (l_0 + l_1 + \cdots + l_k) \\
w_k
\end{pmatrix}　 (l' \le l < l' + L)
\\
\\
\begin{pmatrix}
l_n \\
w_n
\end{pmatrix} & =
\begin{pmatrix}
\cos\phi_n & \sin\phi_n \\
-\sin\phi_n & \cos\phi_n
\end{pmatrix}
\begin{pmatrix}
u - u_n \\
v - v_n
\end{pmatrix}
\\
\\
& \phi_k = \dfrac{\sum^k_{n=0}l_n}{2R_2}, \quad u_k = - \dfrac{A}{\sqrt2} \displaystyle\int^{|\phi_k|}_0 \dfrac{\cos\tau}{\sqrt{\tau}} d\tau, \quad v_k =  sign(R_2)\dfrac{A}{\sqrt2} \displaystyle\int^{|\phi_k|}_0 \dfrac{\sin\tau}{\sqrt{\tau}} d\tau
\end{array}
$$

###　　クロソイド割り出し式一覧表

|       式番号        |                     KA-KE                     |                                            KAE-KEE                                            |                                    KE-KA                                     |                                   KEE-KAE                                    |
| :-----------------: | :-------------------------------------------: | :-------------------------------------------------------------------------------------------: | :--------------------------------------------------------------------------: | :--------------------------------------------------------------------------: |
|   $\vectwo{u}{v}$   | $R^{-1}(\theta)\vectwo{x - x_{KA}}{y-y_{KA}}$ |     $R^{-1}(\theta)\vectwo{x - x_{KAE}}{y-y_{KAE}} + R^{-1}(\tau)\vectwo{x_\tau}{y_\tau}$     | $R^{-1}(\theta+\tau)\vectwo{x - x_{KE}}{y-y_{KE}} - \vectwo{x_\tau}{y_\tau}$ | $R^{-1}(\theta+\tau)\vectwo{x - x_{KE}}{y-y_{KE}} - \vectwo{x_\tau}{y_\tau}$ |
|        $l'$         |                       0                       |                                    $\dfrac{A^2}{\|R_1\|}$                                     |                                      0                                       |                         $\dfrac{A^2}{ \| R_1 \| } $                          |
|       $\tau$        |                       0                       |                                      $\dfrac{l'}{2R_1}$                                       |                               $\dfrac{L}{2R} $                               |                            $\dfrac{l' + L}{2R_2}$                            |
|      $x_\tau$       |                       0                       |                                     $\clothox{\|\tau\|}$                                      |                             $\clothox{\|\tau\|}$                             |                             $\clothox{\|\tau\|}$                             |
|      $y_\tau$       |                       0                       |                                 $sign(R_1)\clothoy{\|\tau\|}$                                 |                         $-sign(R)\clothoy{\|\tau\|}$                         |                        $-sign(R_2)\clothoy{\|\tau\|}$                        |
| $\vectwo{l_n}{w_n}$ |                       >                       |                                               >                                               |                                      >                                       |                       $\Rinv{\phi_n}\vectwo{u_n}{v_n}$                       |
|      $\phi_n$       |                       >                       |                                               >                                               |                                      >                                       |                       $\dfrac{\sum^n_{k=0}l_k}{2R_2}$                        |
|        $u_k$        |            $\clothox{\|\phi_k\|}$             |                                    $\clothox{\|\phi_k\|}$                                     |                           $-\clothox{\|\phi_k\|}$                            |                           $-\clothox{\|\phi_k\|}$                            |
|        $v_k$        |         $sign(R)\clothoy{\|\phi_k\|}$         |                                $sign(R_1)\clothoy{\|\phi_k\|}$                                |                        $-sign(R)\clothoy{\|\phi_k\|}$                        |                       $-sign(R_2)\clothoy{\|\phi_k\|}$                       |
|         $l$         |               $\sum^k_{n=0}l_n$               |                                    $l' + \sum^k_{n=0}l_n$                                     |                             $L+\sum^k_{n=0}l_n$                              |                            $l'+L+\sum^k_{n=0}l_n$                            |
|         $w$         |                       >                       |                                               >                                               |                                      >                                       |                                    $w_k$                                     |
| $\vectwo{x_q}{y_q}$ |                       >                       | $R(\theta)\vectwo{u_k}{v_k}+R(\theta-\tau)\vectwo{x_\tau}{y_\tau}+ \vectwo{x_{KAE}}{y_{KAE}}$ |                                      >                                       |  $R(\theta+\tau)\vectwo{u_k+x_\tau}{v_k+y_\tau}+ \vectwo{x_{KEE}}{y_{KEE}}$  |

## 補足

### 回転行列; 線形代数

回転行列$R(\theta)$は、ある点を角度$\theta$回転させる特殊な行列である。回転行列の逆行列を逆回転行列と呼ぶ。回転行列$R(\theta)$と逆回転行列$R^{-1}(\tau)$は次の通りである。

$$
R(\theta) =
\begin{pmatrix}
\cos\theta & -\sin\theta\\
\sin\theta & \cos\theta
\end{pmatrix}
\\
\\
R^{-1}(\tau) =
\begin{pmatrix}
\cos\tau & \sin\tau \\
-\sin\tau & \cos\tau
\end{pmatrix}
\\
\\
$$

逆回転行列には$R^{-1}(\tau)= R(-\tau)$という性質がある。$\theta$に$-\tau$を代入すると、逆回転行列となる。

$$
R(\theta)|\_{\theta=-\tau} =
R(-\tau) =
\begin{pmatrix}
\cos(-\tau) & -\sin(-\tau)\\
\sin(-\tau) & \cos(-\tau)
\end{pmatrix} =
\begin{pmatrix}
\cos\tau & \sin\tau\\
-\sin\tau & \cos\tau
\end{pmatrix} =
R^{-1}(\tau)
$$

### 座標系の変換; 線形代数

ある座標系上の点$(x, y)$が$(x_0,y_0)$を原点として角度$\tau$回転させた新たな座標系上の点$(u, v)$に一致する時、次の式が成り立つ。

$$
\begin{pmatrix}
u \\
v
\end{pmatrix} =
R^{-1}(\tau)
\begin{pmatrix}
x - x_0\\
y - y_0
\end{pmatrix} =
\begin{pmatrix}
\cos\tau & \sin\tau\\
-\sin\tau & \cos\tau
\end{pmatrix}
\begin{pmatrix}
x - x_0\\
y - y_0
\end{pmatrix}
$$

-   **証明**

新たな座標系上の点を$(u, v)$とすると、角度$\tau$回転させ、$(x_0, y_0)$分、平行移動した先が元の座標$(x, y)$であるから、次の式が成り立つ。

$$
R(\tau)\begin{pmatrix}
u \\
v
\end{pmatrix} +
\begin{pmatrix}
x_0 \\
y_0
\end{pmatrix} =
\begin{pmatrix}
x \\
y
\end{pmatrix}
\\
\\
$$

$(x_0, y_0)$を移項して、逆回転行列を両辺にかける。

$$
\begin{array}{cl}
(左辺) & = R^{-1}(\tau)R(\tau)\begin{pmatrix}
u \\
v
\end{pmatrix} =
\begin{pmatrix}
1 & 0 \\
0 & 1
\end{pmatrix}
\begin{pmatrix}
u \\
v
\end{pmatrix} =
\begin{pmatrix}
u \\
v
\end{pmatrix}
\\\\
(右辺) & = R^{-1}(\tau)
\begin{pmatrix}
x - x_0\\
y - y_0
\end{pmatrix} =
\begin{pmatrix}
\cos\tau & \sin\tau\\
-\sin\tau & \cos\tau
\end{pmatrix}
\begin{pmatrix}
x - x_0\\
y - y_0
\end{pmatrix}
\\\\
\therefore \begin{pmatrix}
u \\
v
\end{pmatrix}
& = \begin{pmatrix}
(x - x_0)\cos\tau+(y - y_0)\sin\tau \\
-(x - x_0)\sin\tau +(y - y_0)\cos\tau
\end{pmatrix}
\end{array}
$$

### 射影ベクトル; 数 II

<img src="figure/segment.png" width="300"></img>

ベクトル$\vec{AP} = (x-x_0, y-y_0)$ が、軸$L$上に射影されたベクトルを$\vec{AQ}$、軸$W$上に射影されたベクトルを$\vec{QP}$とする。軸$L$の方向ベクトルは$\vec{e_L}=(\cos\tau, \sin\tau)$、軸$W$の方向ベクトルは$\vec{e_W}=(-\sin\tau, \cos\tau)$である。これらは方向ベクトルなので、大きさは 1 である。$|\vec{e_L}|=|\vec{e_W}|=1$。したがって、

$$
\vec{AQ} = \dfrac{\vec{AP}\cdot\vec{e_L}}{|\vec{e_L}|^2} \vec{e_L} = l\vec{e_L}
\\
\\
\therefore l = \frac{\vec{AP}\cdot\vec{e_L}}{1^2} = (x-x_0)\cos\tau + (y - y_0)\sin\tau \\
\vec{QP} = \dfrac{\vec{AP}\cdot\vec{e_W}}{|\vec{e_W}|^2} \vec{e_W} = w\vec{e_W}
\\
\\
\therefore w = \frac{\vec{AP}\cdot\vec{e_W}}{1^2} = -(x-x_0)\sin\tau + (y - y_0)\cos\tau
$$

-   **証明**

点$Q$は軸$L$上の点なので比例定数$l$とすると、$\vec{AQ} = l \vec{e_L}$となる。$\vec{AQ}$と$\vec{QP}$は直交するので、$\vec{AQ}\cdot\vec{QP} = 0$となる。$\vec{QP} = \vec{AP} - \vec{AQ}$ であるから、$\vec{QP}$を代入する。

$$
\begin{array}{cl}
& \vec{AQ}\cdot\vec{QP} = \vec{AQ}\cdot(\vec{AP}-\vec{AQ})= 0
\\
\implies & l \vec{e_L} \cdot \vec{AP} - l \vec{e_L} \cdot l \vec{e_L} = 0\\
\implies & l (\vec{e_L} \cdot \vec{AP} - l |\vec{e_L}|^2 ) = 0\\
& \therefore l = \dfrac{\vec{AP}\cdot \vec{e_L}}{|\vec{e_L}|^2}
\end{array}
$$

軸$W$でも同様の計算で、$ w = \dfrac{\vec{AP}\cdot{\vec{e_W}}}{|\vec{e_W}|^2} $となる。

### 余弦定理

<img src="figure/segment.png" width="300"></img>
この図において、三角形$PAB$の角度を$\theta$とすると、余弦定理から、$|\vec{PB}|^2 = |\vec{AP}|^2 + |\vec{AB}|^2 -2 |\vec{AP}||\vec{AB}|\cos\theta$ が成り立つ。|$\vec{AP}|\cos\theta = l$であることに注意すると、次の式が成り立つ。

$$
\begin{cases}
\vec{PB} = (|\vec{AB}|\cos\tau + x_0 - x, |\vec{AB}|\sin\tau + x_0 - x) \\
\vec{AP} = (x - x_0, y - y_0) \\
l = |\vec{AP}| \cos\theta
\end{cases}
$$

これらを余弦定理の式に代入する。

$$
\begin{array}{ll}
(左辺) & = (|\vec{AB}|\cos\tau -(x - x_0))^2 + (|\vec{AB}|\sin\tau - (y - y_0))^2 \\
& = \cancel{|\vec{AB}|^2} -2|\vec{AB}|((x-x_0)\cos\tau + (y-y_0)\sin\tau) + \cancel{(x-x_0)^2} + \cancel{(y-y_0)^2} \\
\\
(右辺) & = |\vec{AP}|^2 + |\vec{AB}|^2 -2 |\vec{AP}||\vec{AB}|\cos\theta \\
& = \cancel{(x-x_0)^2} + \cancel{(y - y_0)^2} + \cancel{|\vec{AB}|^2} -2|\vec{AB}|\cdot l \\
\\
\implies & 2|\vec{AB}|\cdot l = 2|\vec{AB}|((x-x_0)\cos\tau + (y-y_0)\sin\tau) \\
\end{array}
$$

したがって、$l = (x-x_0)\cos\tau + (y-y_0)\sin\tau$が成り立つ。

同様に、$W$軸上の点$Q_W$を考え、三角形$PAQ_W$での余弦定理を考える。$|\vec{PQ_W}|^2 = |\vec{AP}|^2 + |\vec{AQ_W}|^2 -2 |\vec{AP}||\vec{AQ_W}|\cos\theta_w$ である。

$$
\begin{array}{ll}
(左辺) & = (|\vec{AQ_W}|\cos(\tau+\pi/2) -(x - x_0))^2 + (|\vec{AQ_W}|\sin(\tau+\pi/2) - (y - y_0))^2 \\
& = \cancel{|\vec{AQ_W}|^2} -2|\vec{AQ_W}|(-(x-x_0)\sin\tau + (y-y_0)\cos\tau) + \cancel{(x-x_0)^2} + \cancel{(y-y_0)^2} \\
\\
(右辺) & = |\vec{AP}|^2 + |\vec{AQ_W}|^2 -2 |\vec{AP}||\vec{AQ_W}|\cos\theta_w \\
& = \cancel{(x-x_0)^2} + \cancel{(y - y_0)^2} + \cancel{|\vec{AQ_W}|^2} -2|\vec{AQ_W}|\cdot w \\
\\
\implies & 2|\vec{AQ_W}|\cdot w = 2|\vec{AQ_W}|(-(x-x_0)\sin\tau + (y-y_0)\cos\tau)
\end{array}
$$

したがって、他の場合ど同様に、$ w= -(x-x_0)\sin\tau + (y-y_0)\cos\tau$が成り立つ。

$$
\therefore \begin{pmatrix}
l \\
w
\end{pmatrix}
= \begin{pmatrix}
(x - x_0)\cos\tau+(y - y_0)\sin\tau \\
-(x - x_0)\sin\tau +(y - y_0)\cos\tau
\end{pmatrix}
$$

### $sign$関数

$$
sign(x) = \begin{cases}
1 & \text{if} & x > 0 \\
0 & \text{if} & x = 0 \\
-1 & \text{if} & x < 0 \\
\end{cases}
$$

### 方向角$\theta$

任意の 2 点$CA$を与えられた時の符号付き角度$\theta_{CA}$は次の式であった。

$$
\theta\_{CA} = \arctan\dfrac{y_a-y_c}{x_a-x_c}
$$

ただし、$arctan$ 関数の値域は$-\pi < \theta_{CA} \le \pi $ なので、軸$X$を基準とした**方向角$\theta$は** $ 0 \le \theta < 2\pi $ であるので、$\theta$を得るには $\theta_{CA}$ が負の時だけ$+2\pi$分、この値を補正する必要がある。これは、sign 関数を使って次の通りとなる。

$$
\theta = \theta_{CA} + (1 - sign(\theta_{CA}) |sign(\theta_{CA})|\pi
$$

したがって、次の表により、方向角 $\theta$が成り立つことがわかる。
|条件|$sign(\theta_{CA})$|$1-sign(\theta_{CA})$|$\|sign(\theta_{CA})\|$| $\theta$|
|:-:|:-:|:-:|:-:|:-:|
|$\theta_{CA}>0$|1|0|1| $\theta_{CA}$|
|$\theta_{CA}=0$|0|1|0| $\theta_{CA}$|
|$\theta_{CA}<0$|-1|2|1| $\theta_{CA} + 2\pi$|

# 路線における割り出し計算

## 複数の線形に一致する割り出し

路線は 3 種類の線形要素の組み合わせである。そこで、任意の点$P(x,y)$が、路線中のどの線形要素上に対応するのか、探索する必要がある。素朴な線形探索では、路線の終端に近い領域ほど計時時間を必要とする実装になる。

一つのアイデアとして、各線形の始点と求めたい点$P$との距離を計算しておき、最短距離となる始点を求める。始点は前後二つの線形の端点なので、その二つの線形に限って割り出し計算すると効率が良いはずである。この場合の計算量は $O(n)$である。これより速くするなら**最近傍探索**用のデータ構造を導入する必要がある。

$$
$$
