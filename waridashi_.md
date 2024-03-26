---
ebook:
    authors: 秦野克彦
    title: 割り出し計算
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
  
-   [割り出し](#割り出し )
    -   [線分での割り出し](#線分での割り出し )
    -   [単曲線での割り出し](#単曲線での割り出し )
    -   [クロソイド曲線での割り出し](#クロソイド曲線での割り出し )
        -   [<img src="https://latex.codecogs.com/gif.latex?KA-KE"/>クロソイド<img src="https://latex.codecogs.com/gif.latex?(R%20&gt;%200)"/>](#ka-keクロソイドr-0 )
        -   [<img src="https://latex.codecogs.com/gif.latex?KA-KE"/>クロソイド<img src="https://latex.codecogs.com/gif.latex?(R%20&lt;%200)"/>](#ka-keクロソイドr-0-1 )
        -   [<img src="https://latex.codecogs.com/gif.latex?KA-KE"/>クロソイド](#ka-keクロソイド )
        -   [<img src="https://latex.codecogs.com/gif.latex?KE-KA"/>クロソイド<img src="https://latex.codecogs.com/gif.latex?（R&gt;0）"/>](#ke-kaクロソイドr0 )
        -   [<img src="https://latex.codecogs.com/gif.latex?KE-KA"/>クロソイド<img src="https://latex.codecogs.com/gif.latex?（R&lt;0）"/>](#ke-kaクロソイドr0-1 )
        -   [<img src="https://latex.codecogs.com/gif.latex?KE-KA"/>クロソイド](#ke-ka-クロソイド )
        -   [卵形クロソイド<img src="https://latex.codecogs.com/gif.latex?(KAE-KEE)"/>](#卵形クロソイドkae-kee )
        -   [卵形クロソイド<img src="https://latex.codecogs.com/gif.latex?(KEE-KAE)"/>](#卵形クロソイドkee-kae )
        -   [クロソイド割り出し式一覧表](#クロソイド割り出し式一覧表 )
    -   [補足](#補足 )
        -   [回転行列; 線形代数](#回転行列-線形代数 )
        -   [座標系の変換; 線形代数](#座標系の変換-線形代数 )
        -   [射影ベクトル; 数 II](#射影ベクトル-数-ii )
        -   [余弦定理](#余弦定理 )
        -   [<img src="https://latex.codecogs.com/gif.latex?sign"/>関数](#sign関数 )
        -   [方向角<img src="https://latex.codecogs.com/gif.latex?&#x5C;theta"/>](#方向角theta )
-   [路線における割り出し計算](#路線における割り出し計算 )
    -   [複数の線形に一致する割り出し](#複数の線形に一致する割り出し )
  
<!-- /code_chunk_output -->
</div>
  
<div style="page-break-before:always"></div>
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;gdef&#x5C;vectwo#1#2{&#x5C;begin{pmatrix}%20#1%20&#x5C;&#x5C;%20#2%20&#x5C;end{pmatrix}}&#x5C;gdef&#x5C;R#1{&#x5C;begin{pmatrix}%20&#x5C;cos#1%20&amp;%20-&#x5C;sin#1%20&#x5C;&#x5C;%20&#x5C;sin#1%20&amp;%20&#x5C;cos#1%20&#x5C;end{pmatrix}}&#x5C;gdef&#x5C;Rinv#1{&#x5C;begin{pmatrix}%20&#x5C;cos#1%20&amp;%20&#x5C;sin#1%20&#x5C;&#x5C;%20-&#x5C;sin#1%20&amp;%20&#x5C;cos#1%20&#x5C;end{pmatrix}}&#x5C;gdef&#x5C;Rinvthree#1#2#3{&#x5C;begin{pmatrix}%20(#2)&#x5C;cos#1%20+%20(#3)&#x5C;sin#1%20&#x5C;&#x5C;%20-(#2)&#x5C;sin#1%20+%20(#3)&#x5C;cos#1%20&#x5C;end{pmatrix}}&#x5C;gdef&#x5C;clothox#1{&#x5C;dfrac{A}{&#x5C;sqrt2}%20&#x5C;displaystyle&#x5C;int^{#1}_0%20&#x5C;dfrac{&#x5C;cos&#x5C;tau}{&#x5C;sqrt{&#x5C;tau}}%20d&#x5C;tau}&#x5C;gdef&#x5C;clothoy#1{&#x5C;dfrac{A}{&#x5C;sqrt2}%20&#x5C;displaystyle&#x5C;int^{#1}_0%20&#x5C;dfrac{&#x5C;sin&#x5C;tau}{&#x5C;sqrt{&#x5C;tau}}%20d&#x5C;tau}"/></p>  
  
  
#  割り出し
  
  
割り出しとは、平面直角座標系上の点 <img src="https://latex.codecogs.com/gif.latex?P(x,%20y)"/>を路線座標系の点<img src="https://latex.codecogs.com/gif.latex?(l,%20w)"/>に変換する計算のことである。3 つの線形(線分、単曲線、クロソイド曲線)から構成される曲線である「路線」は、路線距離<img src="https://latex.codecogs.com/gif.latex?l"/>の点<img src="https://latex.codecogs.com/gif.latex?Q"/>で直線<img src="https://latex.codecogs.com/gif.latex?QP"/>と直交する。この時の直線<img src="https://latex.codecogs.com/gif.latex?QP"/>との位置を幅<img src="https://latex.codecogs.com/gif.latex?w"/>で表現すると、点<img src="https://latex.codecogs.com/gif.latex?(l,%20w)"/>は路線に沿って湾曲した座標系を構成する。
  
##  線分での割り出し
  
  
曲線長<img src="https://latex.codecogs.com/gif.latex?L"/>の線分<img src="https://latex.codecogs.com/gif.latex?AB"/>に対して、平面直角座標系上の点 <img src="https://latex.codecogs.com/gif.latex?P(x,%20y)"/>から路線座標系上の点 <img src="https://latex.codecogs.com/gif.latex?P(l,%20w)"/>への変換を考える。具体的には、軸<img src="https://latex.codecogs.com/gif.latex?X"/>と線分<img src="https://latex.codecogs.com/gif.latex?AB"/> のなす角を<img src="https://latex.codecogs.com/gif.latex?&#x5C;theta"/>と置く。線分での割り出しを次の図で示す。
  
<img src="figure/segment.png" width="300"></img>
  
点<img src="https://latex.codecogs.com/gif.latex?P(l,%20w)"/>の座標系として、線分<img src="https://latex.codecogs.com/gif.latex?AB"/>の始点<img src="https://latex.codecogs.com/gif.latex?A(x_0,%20y_0)"/>を原点とし、線分<img src="https://latex.codecogs.com/gif.latex?AB"/>方向を軸<img src="https://latex.codecogs.com/gif.latex?L"/>、始点<img src="https://latex.codecogs.com/gif.latex?A"/>を通って点<img src="https://latex.codecogs.com/gif.latex?P"/>の軸 <img src="https://latex.codecogs.com/gif.latex?L"/> に直交する軸<img src="https://latex.codecogs.com/gif.latex?W"/> を考える。これは元の座標系を始点 <img src="https://latex.codecogs.com/gif.latex?A"/> を原点として、方向角<img src="https://latex.codecogs.com/gif.latex?&#x5C;theta"/>だけ回転させたものと一致する。したがって、逆回転行列を<img src="https://latex.codecogs.com/gif.latex?R^{-1}(&#x5C;theta)"/>とすると 点 <img src="https://latex.codecogs.com/gif.latex?P(l,%20w)"/>には次の式が成り立つ。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;vectwo{l}{w}%20=%20R^{-1}(&#x5C;theta)%20&#x5C;vectwo{x-x_0}{y%20-%20y_0}%20=%20&#x5C;Rinv{&#x5C;theta}&#x5C;vectwo{x-x_0}{y%20-y_0}"/></p>  
  
  
この時、点<img src="https://latex.codecogs.com/gif.latex?P"/>の軸 <img src="https://latex.codecogs.com/gif.latex?L"/> についての垂線は、線分 <img src="https://latex.codecogs.com/gif.latex?AB"/> 上で交わるとは限らない。交点が存在する条件は　<img src="https://latex.codecogs.com/gif.latex?0%20&#x5C;le%20l%20&#x5C;lt%20L%20=%20|&#x5C;vec{AB}|"/> である。
  
以上により、線分<img src="https://latex.codecogs.com/gif.latex?AB"/>に対する割り出しは次の通りである。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;vectwo{l}{w}%20=%20&#x5C;Rinvthree{&#x5C;theta}{x%20-%20x_0}{y%20-%20y_0}%20&#x5C;quad%20(0%20&#x5C;le%20l%20&#x5C;lt%20L)"/></p>  
  
  
交点 <img src="https://latex.codecogs.com/gif.latex?Q"/> は次の通りである。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{array}{cl}&#x5C;vec{OQ}%20&amp;%20=%20&#x5C;vec{OA}%20+%20&#x5C;vec{AQ}%20=%20&#x5C;vec{OA}%20+%20l&#x5C;vec{e_L}%20=&#x5C;vectwo{x_0}{y_0}+l&#x5C;vectwo{&#x5C;cos&#x5C;theta}{&#x5C;sin&#x5C;theta}&#x5C;&#x5C;%20&amp;%20=%20&#x5C;vectwo{x_0%20+%20((x%20-%20x_0)&#x5C;cos&#x5C;theta+(y%20-%20y_0)&#x5C;sin&#x5C;theta)&#x5C;cos&#x5C;theta}{y_0%20+%20((x%20-%20x_0)&#x5C;cos&#x5C;theta+(y%20-%20y_0)&#x5C;sin&#x5C;theta)&#x5C;sin&#x5C;theta}&#x5C;end{array}"/></p>  
  
  
##  単曲線での割り出し
  
  
線分の場合と同様に曲線長<img src="https://latex.codecogs.com/gif.latex?L"/>である単曲線<img src="https://latex.codecogs.com/gif.latex?AB"/>に対して、平面直角座標系上の点 <img src="https://latex.codecogs.com/gif.latex?P(x,%20y)"/>から路線座標系上の点 <img src="https://latex.codecogs.com/gif.latex?P(l,%20w)"/>への変換を考える。具体的には、単曲線<img src="https://latex.codecogs.com/gif.latex?AB"/>は中心点<img src="https://latex.codecogs.com/gif.latex?C(x_c,y_c)"/>で、半径 <img src="https://latex.codecogs.com/gif.latex?R"/>、単曲線の始点 <img src="https://latex.codecogs.com/gif.latex?A(x_a,%20y_a)"/> に対する接線方向角を <img src="https://latex.codecogs.com/gif.latex?&#x5C;tau"/>、<img src="https://latex.codecogs.com/gif.latex?&#x5C;vec{CA}"/>と<img src="https://latex.codecogs.com/gif.latex?&#x5C;vec{CP}"/>との**符号付き角度を<img src="https://latex.codecogs.com/gif.latex?&#x5C;phi"/>と置く**。ここで、単曲線の場合の割り出し計算を次の図に示す。単曲線の場合、反時計回りと時計回りの 2 つの場合を考える必要がある。反時計回りの場合は、<img src="https://latex.codecogs.com/gif.latex?R&gt;0,%20&#x5C;theta&gt;0"/> であり、時計回りの場合は、<img src="https://latex.codecogs.com/gif.latex?R&lt;0,%20&#x5C;theta%20&lt;%200"/>となる
  
<img src="figure/arc.png" width="600"></img>
  
曲線距離<img src="https://latex.codecogs.com/gif.latex?l"/>について、円弧<img src="https://latex.codecogs.com/gif.latex?AQ"/>は半径<img src="https://latex.codecogs.com/gif.latex?R"/>で角度<img src="https://latex.codecogs.com/gif.latex?&#x5C;phi"/>の円弧である。したがって、<img src="https://latex.codecogs.com/gif.latex?l=R&#x5C;phi"/>である。反時計回りの場合も、時計回りの場合も、<img src="https://latex.codecogs.com/gif.latex?l"/>は正の値を取るので同じ式となる。ここで、一般的に 2 点を与えられた時の角度<img src="https://latex.codecogs.com/gif.latex?&#x5C;theta_{CA}"/>の定義式を示す。式中の分子の<img src="https://latex.codecogs.com/gif.latex?&#x5C;times"/>は外積演算、分母の<img src="https://latex.codecogs.com/gif.latex?&#x5C;cdot"/>は内積演算である。また、<img src="https://latex.codecogs.com/gif.latex?&#x5C;vec{e_X}"/>は軸 <img src="https://latex.codecogs.com/gif.latex?X"/> の方向ベクトルであるので、<img src="https://latex.codecogs.com/gif.latex?&#x5C;vec{e_X}%20=%20(1,%200)"/>である。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;tan&#x5C;theta_{CA}%20=%20&#x5C;dfrac{|&#x5C;vec{e_X}|&#x5C;cdot|&#x5C;vec{CA}|&#x5C;sin&#x5C;theta_{CA}}{|&#x5C;vec{e_X}|&#x5C;cdot|&#x5C;vec{CA}|&#x5C;cos&#x5C;theta_{CA}}%20=%20&#x5C;dfrac{&#x5C;vec{e_X}%20&#x5C;times%20&#x5C;vec{CA}}{%20&#x5C;vec{e_X}&#x5C;cdot%20&#x5C;vec{CA}}%20=%20&#x5C;dfrac{1&#x5C;cdot(y_a-y_c)%20-%200&#x5C;cdot(x_a-x_c)}{1&#x5C;cdot(x_a-x_c)+0&#x5C;cdot(y_a-y_c)}%20=&#x5C;dfrac{y_a-y_c}{x_a-x_c}&#x5C;&#x5C;&#x5C;&#x5C;&#x5C;therefore%20&#x5C;theta_{CA}%20=%20&#x5C;arctan{&#x5C;dfrac{y_a-y_c}{x_a-x_c}}"/></p>  
  
  
これにより、符号付き角度<img src="https://latex.codecogs.com/gif.latex?&#x5C;phi"/>は、次のようになる。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;phi%20=%20&#x5C;theta_{CP}%20-%20&#x5C;theta_{CA}%20=%20&#x5C;arctan{&#x5C;dfrac{y-y_c}{x-x_c}}%20-%20&#x5C;arctan{&#x5C;dfrac{y_a-y_c}{x_a-x_c}}"/></p>  
  
  
さらなる条件として、直線<img src="https://latex.codecogs.com/gif.latex?CP"/>は、単曲線<img src="https://latex.codecogs.com/gif.latex?AB"/>と交わるとは限らない。交点<img src="https://latex.codecogs.com/gif.latex?Q"/>が存在する条件は<img src="https://latex.codecogs.com/gif.latex?0%20&#x5C;le%20|&#x5C;phi|%20&#x5C;lt%20L&#x2F;|R|"/>である。
  
次に、幅<img src="https://latex.codecogs.com/gif.latex?w"/>について、単曲線<img src="https://latex.codecogs.com/gif.latex?AB"/>と直線<img src="https://latex.codecogs.com/gif.latex?CP"/>の交点<img src="https://latex.codecogs.com/gif.latex?Q"/>を原点とし、点<img src="https://latex.codecogs.com/gif.latex?Q"/>の接線方向を軸<img src="https://latex.codecogs.com/gif.latex?U"/>、軸 <img src="https://latex.codecogs.com/gif.latex?U"/> と直交する軸 <img src="https://latex.codecogs.com/gif.latex?W"/> を取る座標系を考える。軸<img src="https://latex.codecogs.com/gif.latex?W"/>は交点<img src="https://latex.codecogs.com/gif.latex?Q"/>の接線方向に対し左が正になるので、正負の向きに注意すると幅<img src="https://latex.codecogs.com/gif.latex?w"/>は次の通りである。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?w%20=%20&#x5C;begin{cases}R%20%20-%20|&#x5C;vec{CP}|%20%20&amp;%20&#x5C;text{if}%20&amp;%20R%20&#x5C;ge%200%20&#x5C;&#x5C;R%20%20+%20|&#x5C;vec{CP}|%20%20&amp;%20&#x5C;text{if}%20&amp;%20R%20&lt;%200&#x5C;end{cases}"/></p>  
  
  
以上により、単曲線の場合の割り出し計算式は次の通りである。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{array}{cll}&#x5C;vectwo{l}{w}%20&amp;%20=%20&#x5C;vectwo{R&#x5C;phi}{R%20-%20sign(R)&#x5C;sqrt{(x-x_c)^2+(y-y_c)^2}}&#x5C;&#x5C;&#x5C;&#x5C;%20&amp;%20&#x5C;phi%20=%20&#x5C;arctan{&#x5C;dfrac{y-y_c}{x-x_c}}%20-%20&#x5C;arctan{&#x5C;dfrac{y_a-y_c}{x_a-x_c}}%20&#x5C;qquad%20%20(0%20&#x5C;le%20|&#x5C;phi|%20&#x5C;lt%20L&#x2F;|R|)&#x5C;end{array}"/></p>  
  
  
この場合、単曲線<img src="https://latex.codecogs.com/gif.latex?AB"/>と直線<img src="https://latex.codecogs.com/gif.latex?CP"/>の交点<img src="https://latex.codecogs.com/gif.latex?Q(x_q,y_q)"/>の座標は、線分<img src="https://latex.codecogs.com/gif.latex?CA"/>を点<img src="https://latex.codecogs.com/gif.latex?C"/>を中心に角度<img src="https://latex.codecogs.com/gif.latex?&#x5C;phi"/>回転させた点となる。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{array}{cl}&#x5C;begin{pmatrix}x_q%20&#x5C;&#x5C;y_q&#x5C;end{pmatrix}%20&amp;%20=　R(&#x5C;phi)&#x5C;vectwo{x_a%20-%20x_c}{y_a%20-%20y_c}+&#x5C;vectwo{x_c}{y_c}&#x5C;&#x5C;&#x5C;&#x5C;&amp;%20=&#x5C;begin{pmatrix}(x_a%20-%20x_c)&#x5C;cos&#x5C;phi%20-%20%20(y_a%20-%20y_c)&#x5C;sin&#x5C;phi%20+%20x_c&#x5C;&#x5C;(x_a%20-%20x_c)&#x5C;sin&#x5C;phi%20+%20%20(y_a%20-%20y_c)&#x5C;cos&#x5C;phi%20+%20y_c&#x5C;end{pmatrix}&#x5C;end{array}"/></p>  
  
  
##  クロソイド曲線での割り出し
  
  
これまで同様に曲線長<img src="https://latex.codecogs.com/gif.latex?L"/>であるクロソイド曲線に対して、平面直角座標系上の点 <img src="https://latex.codecogs.com/gif.latex?P(x,%20y)"/>から路線座標系上の点 <img src="https://latex.codecogs.com/gif.latex?P(l,%20w)"/>への変換を考える。具体的にクロソイド曲線は、始点 <img src="https://latex.codecogs.com/gif.latex?KA(x_{KA},y_{KA})"/>で接線方向角<img src="https://latex.codecogs.com/gif.latex?&#x5C;theta"/>、終端 <img src="https://latex.codecogs.com/gif.latex?KE"/> での半径 <img src="https://latex.codecogs.com/gif.latex?R"/>、クロソイドパラメータは <img src="https://latex.codecogs.com/gif.latex?A"/> とする。ここで、求める点 <img src="https://latex.codecogs.com/gif.latex?P"/> のクロソイド曲線に対する垂線との交点 <img src="https://latex.codecogs.com/gif.latex?K"/> を求めるために、<img src="https://latex.codecogs.com/gif.latex?KA"/> を原点としクロソイド曲線の接線方向角を軸 <img src="https://latex.codecogs.com/gif.latex?U"/>、軸 <img src="https://latex.codecogs.com/gif.latex?U"/> と直交する軸 <img src="https://latex.codecogs.com/gif.latex?V"/> を設定する。これらを説明する図を次に示す。なお、反時計回りの場合は、<img src="https://latex.codecogs.com/gif.latex?R&gt;0,%20&#x5C;theta&gt;0"/> であり、時計回りの場合は、<img src="https://latex.codecogs.com/gif.latex?R&lt;0,%20&#x5C;theta%20&lt;%200"/>である。
  
###  <img src="https://latex.codecogs.com/gif.latex?KA-KE"/>クロソイド<img src="https://latex.codecogs.com/gif.latex?(R%20&gt;%200)"/>
  
  
まず、原座標系を下左図で、変換後の小座標系を下右図に示す。下右図は、<img src="https://latex.codecogs.com/gif.latex?KA"/> を原点としクロソイド曲線の接線方向角を軸 <img src="https://latex.codecogs.com/gif.latex?U"/>、軸 <img src="https://latex.codecogs.com/gif.latex?U"/> と直交する軸 <img src="https://latex.codecogs.com/gif.latex?V"/> とする座標系である。
  
<img src="figure/clothoidKAKE_Rp.png" width="800"></img>
  
この小座標系への変換は次の通りである。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{pmatrix}u%20&#x5C;&#x5C;v&#x5C;end{pmatrix}%20=R^{-1}(&#x5C;theta)%20&#x5C;begin{pmatrix}x%20-%20x_{KA}%20&#x5C;&#x5C;y%20-%20y_{KA}&#x5C;end{pmatrix}%20=&#x5C;begin{pmatrix}&#x5C;cos&#x5C;theta%20&amp;%20&#x5C;sin&#x5C;theta%20&#x5C;&#x5C;-&#x5C;sin&#x5C;theta%20&amp;%20&#x5C;cos&#x5C;theta&#x5C;end{pmatrix}&#x5C;begin{pmatrix}x%20-%20x_{KA}%20&#x5C;&#x5C;y%20-%20y_{KA}&#x5C;end{pmatrix}"/></p>  
  
  
以降は全てこの小座標系で議論する。
  
求める点 <img src="https://latex.codecogs.com/gif.latex?P(l,%20w)"/> に対するクロソイド上の点 <img src="https://latex.codecogs.com/gif.latex?Q"/> が接線方向角<img src="https://latex.codecogs.com/gif.latex?&#x5C;phi"/>を持つ時、点 <img src="https://latex.codecogs.com/gif.latex?Q"/>を原点として接線方向を軸とする座標変換を考える。まず、クロソイド曲線の始点 <img src="https://latex.codecogs.com/gif.latex?KA"/> を <img src="https://latex.codecogs.com/gif.latex?Q_0(u_0,%20v_0)"/>とする。ここで、<img src="https://latex.codecogs.com/gif.latex?u_0%20=%20v_0%20=%200"/> であり、接線方向角 <img src="https://latex.codecogs.com/gif.latex?&#x5C;phi_0%20=%200"/>、クロソイド長 <img src="https://latex.codecogs.com/gif.latex?l_0=0"/> である。この座標系で求める点 <img src="https://latex.codecogs.com/gif.latex?P(l_0,%20w_0)"/>は次の通りになる。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{pmatrix}l_0%20&#x5C;&#x5C;w_0&#x5C;end{pmatrix}%20=R^{-1}(&#x5C;phi_0)%20&#x5C;begin{pmatrix}u%20-%20u_0%20&#x5C;&#x5C;v%20-%20v_0&#x5C;end{pmatrix}%20=&#x5C;begin{pmatrix}&#x5C;cos&#x5C;phi_0%20&amp;%20&#x5C;sin&#x5C;phi_0%20&#x5C;&#x5C;-&#x5C;sin&#x5C;phi_0%20&amp;%20&#x5C;cos&#x5C;phi_0&#x5C;end{pmatrix}&#x5C;begin{pmatrix}u%20-%20u_0%20&#x5C;&#x5C;v%20-%20v_0&#x5C;end{pmatrix}"/></p>  
  
  
次に、この <img src="https://latex.codecogs.com/gif.latex?l_0"/> をクロソイド長とする点<img src="https://latex.codecogs.com/gif.latex?Q_1(u_1,%20v_1)"/>を考える。<img src="https://latex.codecogs.com/gif.latex?&#x5C;phi_1%20=%20&#x5C;dfrac{l_0}{2R}"/>、<img src="https://latex.codecogs.com/gif.latex?u_1%20=%20&#x5C;clothox{&#x5C;phi_1}"/>、<img src="https://latex.codecogs.com/gif.latex?v_1%20=%20&#x5C;clothoy{&#x5C;phi_1}"/> である。この点<img src="https://latex.codecogs.com/gif.latex?Q_1"/> を原点とする座標系で求める点 <img src="https://latex.codecogs.com/gif.latex?P(l_1,%20w_1)"/>は次の通りになる。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{pmatrix}l_1%20&#x5C;&#x5C;w_1&#x5C;end{pmatrix}%20=&#x5C;begin{pmatrix}&#x5C;cos&#x5C;phi_1%20&amp;%20&#x5C;sin&#x5C;phi_1%20&#x5C;&#x5C;-&#x5C;sin&#x5C;phi_1%20&amp;%20&#x5C;cos&#x5C;phi_1&#x5C;end{pmatrix}&#x5C;begin{pmatrix}u%20-%20u_1%20&#x5C;&#x5C;v%20-%20v_1&#x5C;end{pmatrix}"/></p>  
  
  
次に<img src="https://latex.codecogs.com/gif.latex?l_0%20+%20l_1"/>をクロソイド長とする点<img src="https://latex.codecogs.com/gif.latex?Q_2(u_2,%20v_2)"/>を考える。<img src="https://latex.codecogs.com/gif.latex?&#x5C;phi_2%20=%20&#x5C;dfrac{l_0+l_1}{2R}"/>、<img src="https://latex.codecogs.com/gif.latex?u_2%20=%20&#x5C;clothox{&#x5C;phi_2}"/>、<img src="https://latex.codecogs.com/gif.latex?v_2%20=%20&#x5C;clothoy{&#x5C;phi_2}"/> である。
  
これを続けていくと<img src="https://latex.codecogs.com/gif.latex?&#x5C;displaystyle&#x5C;lim_{n&#x5C;to&#x5C;infty}l_n%20=%200"/>となり、点<img src="https://latex.codecogs.com/gif.latex?Q_n"/>は求める点<img src="https://latex.codecogs.com/gif.latex?Q"/>に収束する。計算上、十分 <img src="https://latex.codecogs.com/gif.latex?0"/> に近い値となるのが<img src="https://latex.codecogs.com/gif.latex?l_k"/>である時、求める点 <img src="https://latex.codecogs.com/gif.latex?P(l,%20w)"/>が次のように定まる。ここで、この点<img src="https://latex.codecogs.com/gif.latex?Q"/>がクロソイド曲線上に存在するためには、<img src="https://latex.codecogs.com/gif.latex?0%20&#x5C;le%20l%20&#x5C;lt%20L"/> でなければならない。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{array}{cll}&#x5C;begin{pmatrix}l%20&#x5C;&#x5C;w&#x5C;end{pmatrix}%20%20&amp;%20=&#x5C;begin{pmatrix}l_0%20+%20l_1%20+%20&#x5C;cdots%20+%20l_k%20&#x5C;&#x5C;w_k&#x5C;end{pmatrix}　%20(0%20&#x5C;le%20l%20&lt;%20L)&#x5C;&#x5C;&#x5C;&#x5C;&#x5C;begin{pmatrix}l_n%20&#x5C;&#x5C;w_n&#x5C;end{pmatrix}%20&amp;%20=&#x5C;begin{pmatrix}&#x5C;cos&#x5C;phi_n%20&amp;%20&#x5C;sin&#x5C;phi_n%20&#x5C;&#x5C;-&#x5C;sin&#x5C;phi_n%20&amp;%20&#x5C;cos&#x5C;phi_n&#x5C;end{pmatrix}&#x5C;begin{pmatrix}u%20-%20u_n%20&#x5C;&#x5C;v%20-%20v_n&#x5C;end{pmatrix}&#x5C;&#x5C;&#x5C;&#x5C;%20&amp;%20&#x5C;phi_k%20=%20&#x5C;dfrac{&#x5C;sum^k_{n=0}l_n}{2R},%20&#x5C;quad%20u_k%20=%20&#x5C;clothox{&#x5C;phi_k},%20&#x5C;quad%20v_n%20=%20&#x5C;clothoy{&#x5C;phi_k}%20&#x5C;&#x5C;%20&#x5C;&#x5C;%20&#x5C;vectwo{x_q}{y_q}%20&amp;%20=%20&#x5C;R{&#x5C;theta}&#x5C;vectwo{u_k}{v_k}+&#x5C;vectwo{x_{KA}}{y_{KA}}&#x5C;end{array}"/></p>  
  
  
###  <img src="https://latex.codecogs.com/gif.latex?KA-KE"/>クロソイド<img src="https://latex.codecogs.com/gif.latex?(R%20&lt;%200)"/>
  
  
まず、原座標系を下左図で、変換後の小座標系を下右図に示す。下右図は、<img src="https://latex.codecogs.com/gif.latex?KA"/> を原点としクロソイド曲線の接線方向角を軸 <img src="https://latex.codecogs.com/gif.latex?U"/>、軸 <img src="https://latex.codecogs.com/gif.latex?U"/> と直交する軸 <img src="https://latex.codecogs.com/gif.latex?V"/> とする座標系である。
  
<img src="figure/clothoidKAKE_Rn.png" width="800"></img>
  
この小座標系への変換は次の通りである。これは、<img src="https://latex.codecogs.com/gif.latex?R&gt;0"/>の場合と同じである。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{pmatrix}u%20&#x5C;&#x5C;v&#x5C;end{pmatrix}%20=R^{-1}(&#x5C;theta)%20&#x5C;begin{pmatrix}x%20-%20x_{KA}%20&#x5C;&#x5C;y%20-%20y_{KA}&#x5C;end{pmatrix}%20=&#x5C;begin{pmatrix}&#x5C;cos&#x5C;theta%20&amp;%20&#x5C;sin&#x5C;theta%20&#x5C;&#x5C;-&#x5C;sin&#x5C;theta%20&amp;%20&#x5C;cos&#x5C;theta&#x5C;end{pmatrix}&#x5C;begin{pmatrix}x%20-%20x_{KA}%20&#x5C;&#x5C;y%20-%20y_{KA}&#x5C;end{pmatrix}&#x5C;&#x5C;&#x5C;&#x5C;&#x5C;therefore&#x5C;begin{pmatrix}u%20&#x5C;&#x5C;v&#x5C;end{pmatrix}%20=&#x5C;begin{pmatrix}(x%20-%20x_{KA})&#x5C;cos&#x5C;theta%20+(y%20-%20y_{KA})&#x5C;sin&#x5C;theta%20&#x5C;&#x5C;-(x%20-%20x_{KA})&#x5C;sin&#x5C;theta%20+(y%20-%20y_{KA})&#x5C;cos&#x5C;theta&#x5C;end{pmatrix}"/></p>  
  
  
以降は全てこの小座標系で議論する。
  
求める点 <img src="https://latex.codecogs.com/gif.latex?P(l,%20w)"/> に対するクロソイド上の点 <img src="https://latex.codecogs.com/gif.latex?Q"/> が接線方向角<img src="https://latex.codecogs.com/gif.latex?&#x5C;phi"/>を持つ時、点 <img src="https://latex.codecogs.com/gif.latex?Q"/>を原点として接線方向を軸とする座標変換を考える。まず、クロソイド曲線の始点 <img src="https://latex.codecogs.com/gif.latex?KA"/> を <img src="https://latex.codecogs.com/gif.latex?Q_0(u_0,%20v_0)"/>とする。ここで、<img src="https://latex.codecogs.com/gif.latex?u_0%20=%20v_0%20=%200"/> であり、接線方向角 <img src="https://latex.codecogs.com/gif.latex?&#x5C;phi_0%20=%200"/>、クロソイド長 <img src="https://latex.codecogs.com/gif.latex?l_0=0"/> である。この座標系で求める点 <img src="https://latex.codecogs.com/gif.latex?P(l_0,%20w_0)"/>は次の通りになる。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{pmatrix}l_0%20&#x5C;&#x5C;w_0&#x5C;end{pmatrix}%20=R^{-1}(&#x5C;phi_0)%20&#x5C;begin{pmatrix}u%20-%20u_0%20&#x5C;&#x5C;v%20-%20v_0&#x5C;end{pmatrix}%20=&#x5C;begin{pmatrix}&#x5C;cos&#x5C;phi_0%20&amp;%20&#x5C;sin&#x5C;phi_0%20&#x5C;&#x5C;-&#x5C;sin&#x5C;phi_0%20&amp;%20&#x5C;cos&#x5C;phi_0&#x5C;end{pmatrix}&#x5C;begin{pmatrix}u%20-%20u_0%20&#x5C;&#x5C;v%20-%20v_0&#x5C;end{pmatrix}"/></p>  
  
  
次に、この <img src="https://latex.codecogs.com/gif.latex?l_0"/> をクロソイド長とする点<img src="https://latex.codecogs.com/gif.latex?Q_1(u_1,%20v_1)"/>を考える。<img src="https://latex.codecogs.com/gif.latex?&#x5C;phi_1%20=%20&#x5C;dfrac{l_0}{2R}"/>、<img src="https://latex.codecogs.com/gif.latex?u_1%20=%20&#x5C;clothox{|&#x5C;phi_1|}"/>、<img src="https://latex.codecogs.com/gif.latex?&#x5C;boxed{v_1%20=%20-&#x5C;clothoy{|&#x5C;phi_1|}}"/> である。この点<img src="https://latex.codecogs.com/gif.latex?K_1"/> を原点とする座標系で求める点 <img src="https://latex.codecogs.com/gif.latex?P(l_1,%20w_1)"/>は次の通りになる。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;vectwo{l_1}{w_1}%20=&#x5C;Rinv{&#x5C;phi_1}&#x5C;vectwo{u-u_1}{v-v_1}"/></p>  
  
  
次に<img src="https://latex.codecogs.com/gif.latex?l_0%20+%20l_1"/>をクロソイド長とする点<img src="https://latex.codecogs.com/gif.latex?Q_2(u_2,%20v_2)"/>を考える。<img src="https://latex.codecogs.com/gif.latex?&#x5C;phi_2%20=%20&#x5C;dfrac{l_0+l_1}{2R}"/>、<img src="https://latex.codecogs.com/gif.latex?u_2%20=%20&#x5C;clothox{|&#x5C;phi_2|}"/>、<img src="https://latex.codecogs.com/gif.latex?&#x5C;boxed{v_2%20=%20-&#x5C;clothoy{|&#x5C;phi_2|}}"/> である。
  
これを続けていくと<img src="https://latex.codecogs.com/gif.latex?&#x5C;displaystyle&#x5C;lim_{n&#x5C;to&#x5C;infty}l_n%20=%200"/>となり、点<img src="https://latex.codecogs.com/gif.latex?Q_n"/>は求める点<img src="https://latex.codecogs.com/gif.latex?Q"/>に収束する。計算上、十分 <img src="https://latex.codecogs.com/gif.latex?0"/> に近い値となるのが<img src="https://latex.codecogs.com/gif.latex?l_k"/>である時、求める点 <img src="https://latex.codecogs.com/gif.latex?P(l,%20w)"/>が次のように定まる。ここで、この点<img src="https://latex.codecogs.com/gif.latex?Q"/>がクロソイド曲線上に存在するためには、<img src="https://latex.codecogs.com/gif.latex?0%20&#x5C;le%20l%20&#x5C;lt%20L"/> でなければならない。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{array}{cll}&#x5C;begin{pmatrix}l%20&#x5C;&#x5C;w&#x5C;end{pmatrix}%20&amp;%20=&#x5C;begin{pmatrix}l_0%20+%20l_1%20+%20&#x5C;cdots%20+%20l_k%20&#x5C;&#x5C;w_k&#x5C;end{pmatrix}　%20&#x5C;quad%20(0%20&#x5C;le%20l%20&lt;%20L)&#x5C;&#x5C;&#x5C;&#x5C;&#x5C;begin{pmatrix}l_n%20&#x5C;&#x5C;w_n&#x5C;end{pmatrix}%20&amp;%20=&#x5C;begin{pmatrix}&#x5C;cos&#x5C;phi_n%20&amp;%20&#x5C;sin&#x5C;phi_n%20&#x5C;&#x5C;-&#x5C;sin&#x5C;phi_n%20&amp;%20&#x5C;cos&#x5C;phi_n&#x5C;end{pmatrix}&#x5C;begin{pmatrix}u%20-%20u_n%20&#x5C;&#x5C;v%20-%20v_n&#x5C;end{pmatrix}&#x5C;&#x5C;&#x5C;&#x5C;&amp;%20&#x5C;phi_k%20%20=%20&#x5C;dfrac{&#x5C;sum^k_{n=0}l_n}{2R},%20&#x5C;quad%20u_k%20=%20&#x5C;clothox{|&#x5C;phi_k|},%20&#x5C;quad%20v_k%20=%20-%20&#x5C;clothoy{|&#x5C;phi_k|}&#x5C;&#x5C;&#x5C;&#x5C;%20&#x5C;vectwo{x_q}{y_q}%20&amp;%20=%20&#x5C;R{&#x5C;theta}&#x5C;vectwo{u_k}{v_k}+&#x5C;vectwo{x_{KA}}{y_{KA}}&#x5C;end{array}"/></p>  
  
  
###  <img src="https://latex.codecogs.com/gif.latex?KA-KE"/>クロソイド
  
  
以上、<img src="https://latex.codecogs.com/gif.latex?KA-KE"/> クロソイドの割り出し計算式は以下の通りまとめることができる。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{array}{cll}&#x5C;begin{pmatrix}u%20&#x5C;&#x5C;v&#x5C;end{pmatrix}%20&amp;%20=&#x5C;begin{pmatrix}(x%20-%20x_{KA})&#x5C;cos&#x5C;theta%20+(y%20-%20y_{KA})&#x5C;sin&#x5C;theta%20&#x5C;&#x5C;-(x%20-%20x_{KA})&#x5C;sin&#x5C;theta%20+(y%20-%20y_{KA})&#x5C;cos&#x5C;theta&#x5C;end{pmatrix}&#x5C;&#x5C;&#x5C;&#x5C;&#x5C;begin{pmatrix}l%20&#x5C;&#x5C;w&#x5C;end{pmatrix}%20&amp;%20=&#x5C;begin{pmatrix}l_0%20+%20l_1%20+%20&#x5C;cdots%20+%20l_k%20&#x5C;&#x5C;w_k&#x5C;end{pmatrix}　%20&#x5C;quad%20(0%20&#x5C;le%20l%20&lt;%20L)&#x5C;&#x5C;&#x5C;&#x5C;&#x5C;begin{pmatrix}l_n%20&#x5C;&#x5C;w_n&#x5C;end{pmatrix}%20&amp;%20=&#x5C;begin{pmatrix}&#x5C;cos&#x5C;phi_n%20&amp;%20&#x5C;sin&#x5C;phi_n%20&#x5C;&#x5C;-&#x5C;sin&#x5C;phi_n%20&amp;%20&#x5C;cos&#x5C;phi_n&#x5C;end{pmatrix}&#x5C;begin{pmatrix}u%20-%20u_n%20&#x5C;&#x5C;v%20-%20v_n&#x5C;end{pmatrix}&#x5C;&#x5C;&#x5C;&#x5C;&amp;%20&#x5C;phi_k%20%20=%20&#x5C;dfrac{&#x5C;sum^k_{n=0}l_n}{2R},%20&#x5C;quad%20u_k%20=%20&#x5C;clothox{|&#x5C;phi_k|},%20&#x5C;quad%20v_k%20=%20sign(R)&#x5C;clothoy{|&#x5C;phi_k|}&#x5C;&#x5C;&#x5C;&#x5C;%20&#x5C;vectwo{x_q}{y_q}%20&amp;%20=%20&#x5C;R{&#x5C;theta}&#x5C;vectwo{u_k}{v_k}+&#x5C;vectwo{x_{KA}}{y_{KA}}&#x5C;end{array}"/></p>  
  
  
###  <img src="https://latex.codecogs.com/gif.latex?KE-KA"/>クロソイド<img src="https://latex.codecogs.com/gif.latex?（R&gt;0）"/>
  
  
<img src="https://latex.codecogs.com/gif.latex?KE-KA"/> クロソイドの場合も同様に、<img src="https://latex.codecogs.com/gif.latex?KA"/> を原点としクロソイド曲線の接線方向角と逆向きを軸 <img src="https://latex.codecogs.com/gif.latex?U"/>、軸 <img src="https://latex.codecogs.com/gif.latex?U"/> と直交する軸 <img src="https://latex.codecogs.com/gif.latex?V"/> とする座標系を取る。この小座標系への変換は次の通りである。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{pmatrix}u%20&#x5C;&#x5C;v&#x5C;end{pmatrix}%20=R^{-1}(&#x5C;theta+&#x5C;tau)%20&#x5C;begin{pmatrix}x%20-%20x_{KA}%20&#x5C;&#x5C;y%20-%20y_{KA}&#x5C;end{pmatrix}"/></p>  
  
  
ここで、点<img src="https://latex.codecogs.com/gif.latex?KA"/> は次の方程式を満たす。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{array}{c}R^{-1}(&#x5C;theta+&#x5C;tau)%20&#x5C;begin{pmatrix}x_{KA}%20-%20x_{KE}%20&#x5C;&#x5C;y_{KA}%20-%20y_{KE}&#x5C;end{pmatrix}%20=&#x5C;begin{pmatrix}x_&#x5C;tau%20&#x5C;&#x5C;-y_&#x5C;tau&#x5C;end{pmatrix}&#x5C;&#x5C;&#x5C;&#x5C;&#x5C;therefore%20&#x5C;vectwo{x_{KA}}{y_{KA}}%20=%20R(&#x5C;theta+&#x5C;tau)&#x5C;vectwo{x_&#x5C;tau}{-y_&#x5C;tau}+%20&#x5C;vectwo{x_{KE}}{y_{KE}}&#x5C;&#x5C;&#x5C;&#x5C;&#x5C;tau%20=%20&#x5C;dfrac{L}{2R},%20&#x5C;quad%20x_&#x5C;tau%20=%20&#x5C;clothox{&#x5C;tau},%20&#x5C;quad%20y_&#x5C;tau%20=%20&#x5C;clothoy{&#x5C;tau}&#x5C;end{array}"/></p>  
  
  
<img src="https://latex.codecogs.com/gif.latex?KE-KA"/> クロソイド は点<img src="https://latex.codecogs.com/gif.latex?KE"/>が始点であるから、点<img src="https://latex.codecogs.com/gif.latex?KA"/>の式を代入して点<img src="https://latex.codecogs.com/gif.latex?KE"/>の式にする。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{pmatrix}u%20&#x5C;&#x5C;v&#x5C;end{pmatrix}%20=R^{-1}(&#x5C;theta+&#x5C;tau)%20&#x5C;begin{pmatrix}x%20-%20x_{KE}%20&#x5C;&#x5C;y%20-%20y_{KE}&#x5C;end{pmatrix}%20-%20&#x5C;vectwo{x_&#x5C;tau}{-y_&#x5C;tau}"/></p>  
  
  
以降はこの小座標系<img src="https://latex.codecogs.com/gif.latex?(u,v)"/>で議論する。この小座標系は、<img src="https://latex.codecogs.com/gif.latex?KA-KE"/>クロソイドの<img src="https://latex.codecogs.com/gif.latex?R&lt;0"/>の形状を原点を中心に 180 度回転させものと一致する。したがって、求める点 <img src="https://latex.codecogs.com/gif.latex?P(l,%20w)"/> に対するクロソイド上の点 <img src="https://latex.codecogs.com/gif.latex?Q"/> に至るまで、次の同じ式が成り立つ。ここで、<img src="https://latex.codecogs.com/gif.latex?u_0%20=%20v_0%20=%200"/> であり、接線方向角 <img src="https://latex.codecogs.com/gif.latex?&#x5C;phi_0%20=%200"/>、クロソイド長 <img src="https://latex.codecogs.com/gif.latex?l_0=0"/> である。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{array}{cl}&#x5C;vectwo{l_n}{w_n}%20&amp;%20=%20&#x5C;Rinv{&#x5C;phi_n}&#x5C;vectwo{u-u_n}{v-v_n}&#x5C;&#x5C;&#x5C;&#x5C;&amp;%20&#x5C;phi_n%20=%20&#x5C;dfrac{&#x5C;sum^n_{k=0}l_k}{2R},%20&#x5C;quad%20u_n%20=%20-%20&#x5C;clothox{|&#x5C;phi_n|},%20&#x5C;quad%20v_n%20=%20&#x5C;clothoy{|&#x5C;phi_n|}&#x5C;end{array}"/></p>  
  
  
点<img src="https://latex.codecogs.com/gif.latex?Q_n(u_n,v_n)"/>は求める点<img src="https://latex.codecogs.com/gif.latex?Q"/>に収束する。計算上、十分 <img src="https://latex.codecogs.com/gif.latex?0"/> に近い値となるのが<img src="https://latex.codecogs.com/gif.latex?l_k"/>である時、求める点 <img src="https://latex.codecogs.com/gif.latex?P(l,%20w)"/>が次のように定まる。<img src="https://latex.codecogs.com/gif.latex?l"/>は、点<img src="https://latex.codecogs.com/gif.latex?KE"/>からの曲線長なので、曲線長 <img src="https://latex.codecogs.com/gif.latex?L"/>に累積曲線長<img src="https://latex.codecogs.com/gif.latex?&#x5C;sum^k_{n=0}l_n"/> を加えることになる。ここで、この点<img src="https://latex.codecogs.com/gif.latex?K"/>がクロソイド曲線上に存在するためには、<img src="https://latex.codecogs.com/gif.latex?0%20&#x5C;le%20l%20&#x5C;lt%20L"/> でなければならない。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{array}{cll}&#x5C;begin{pmatrix}l%20&#x5C;&#x5C;w&#x5C;end{pmatrix}%20%20&amp;%20=&#x5C;begin{pmatrix}L%20＋%20(l_0%20+%20l_1%20+%20&#x5C;cdots%20+%20l_k)%20&#x5C;&#x5C;w_k&#x5C;end{pmatrix}　%20(0%20&#x5C;le%20l%20&lt;%20L)&#x5C;&#x5C;&#x5C;&#x5C;&#x5C;begin{pmatrix}l_n%20&#x5C;&#x5C;w_n&#x5C;end{pmatrix}%20&amp;%20=&#x5C;begin{pmatrix}&#x5C;cos&#x5C;phi_n%20&amp;%20&#x5C;sin&#x5C;phi_n%20&#x5C;&#x5C;-&#x5C;sin&#x5C;phi_n%20&amp;%20&#x5C;cos&#x5C;phi_n&#x5C;end{pmatrix}&#x5C;begin{pmatrix}u%20-%20u_n%20&#x5C;&#x5C;v%20-%20v_n&#x5C;end{pmatrix}&#x5C;&#x5C;&#x5C;&#x5C;&#x5C;phi_k%20&amp;%20=%20&#x5C;dfrac{&#x5C;sum^k_{n=0}l_n}{2R},%20&#x5C;quad%20u_k%20=%20-&#x5C;clothox{|&#x5C;phi_k|},%20&#x5C;quad%20v_k%20=%20&#x5C;clothoy{|&#x5C;phi_k|}&#x5C;end{array}"/></p>  
  
  
###  <img src="https://latex.codecogs.com/gif.latex?KE-KA"/>クロソイド<img src="https://latex.codecogs.com/gif.latex?（R&lt;0）"/>
  
  
前節同同様に、点<img src="https://latex.codecogs.com/gif.latex?KA"/> を原点としクロソイド曲線の接線方向角を軸 <img src="https://latex.codecogs.com/gif.latex?U"/>、軸 <img src="https://latex.codecogs.com/gif.latex?U"/> と直交する軸 <img src="https://latex.codecogs.com/gif.latex?V"/> とする座標系であるぜこの小座標系への変換は次の通りである。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{pmatrix}u%20&#x5C;&#x5C;v&#x5C;end{pmatrix}%20=R^{-1}(&#x5C;theta-&#x5C;tau)%20&#x5C;begin{pmatrix}x%20-%20x_{KA}%20&#x5C;&#x5C;y%20-%20y_{KA}&#x5C;end{pmatrix}"/></p>  
  
  
ここで、点<img src="https://latex.codecogs.com/gif.latex?KA"/> は次の方程式を満たす。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{array}{c}R^{-1}(&#x5C;theta-&#x5C;tau)%20&#x5C;begin{pmatrix}x_{KA}%20-%20x_{KE}%20&#x5C;&#x5C;y_{KA}%20-%20y_{KE}&#x5C;end{pmatrix}%20=&#x5C;begin{pmatrix}x_&#x5C;tau%20&#x5C;&#x5C;y_&#x5C;tau&#x5C;end{pmatrix}&#x5C;&#x5C;&#x5C;&#x5C;&#x5C;therefore&#x5C;begin{pmatrix}x_{KA}%20&#x5C;&#x5C;y_{KA}&#x5C;end{pmatrix}%20=R(&#x5C;theta-&#x5C;tau)%20&#x5C;begin{pmatrix}x_&#x5C;tau%20&#x5C;&#x5C;y_&#x5C;tau&#x5C;end{pmatrix}%20+&#x5C;begin{pmatrix}x_{KE}%20&#x5C;&#x5C;y_{KE}&#x5C;end{pmatrix}&#x5C;&#x5C;&#x5C;&#x5C;&#x5C;tau%20=%20&#x5C;dfrac{L}{2|R|},%20&#x5C;quad%20x_&#x5C;tau%20=%20&#x5C;dfrac{A}{&#x5C;sqrt2}&#x5C;displaystyle&#x5C;int^{&#x5C;tau}_0%20&#x5C;dfrac{&#x5C;cos&#x5C;tau}{&#x5C;sqrt&#x5C;tau}%20d&#x5C;tau,%20&#x5C;quad%20y_&#x5C;tau%20=%20&#x5C;dfrac{A}{&#x5C;sqrt2}&#x5C;displaystyle&#x5C;int^{&#x5C;tau}_0%20&#x5C;dfrac{&#x5C;sin&#x5C;tau}{&#x5C;sqrt&#x5C;tau}%20d&#x5C;tau&#x5C;end{array}"/></p>  
  
  
<img src="https://latex.codecogs.com/gif.latex?KE-KA"/> クロソイド は点<img src="https://latex.codecogs.com/gif.latex?KE"/>が始点であるから、点<img src="https://latex.codecogs.com/gif.latex?KA"/>の式を代入して点<img src="https://latex.codecogs.com/gif.latex?KE"/>の式にする。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{pmatrix}u%20&#x5C;&#x5C;v&#x5C;end{pmatrix}%20=R^{-1}(&#x5C;theta-&#x5C;tau)%20&#x5C;begin{pmatrix}x%20-%20x_{KE}%20&#x5C;&#x5C;y%20-%20y_{KE}&#x5C;end{pmatrix}%20-%20&#x5C;vectwo{x_&#x5C;tau}{y_&#x5C;tau}"/></p>  
  
  
以降はこの小座標系<img src="https://latex.codecogs.com/gif.latex?(u,v)"/>で議論する。この小座標系は、<img src="https://latex.codecogs.com/gif.latex?KA-KE"/>クロソイドの<img src="https://latex.codecogs.com/gif.latex?R&gt;0"/>の形状と一致する。したがって、求める点 <img src="https://latex.codecogs.com/gif.latex?P(l,%20w)"/> に対するクロソイド上の点 <img src="https://latex.codecogs.com/gif.latex?Q"/> に至るまで、次の同じ式が成り立つ。ここで、<img src="https://latex.codecogs.com/gif.latex?u_0%20=%20v_0%20=%200"/> であり、接線方向角 <img src="https://latex.codecogs.com/gif.latex?&#x5C;phi_0%20=%200"/>、クロソイド長 <img src="https://latex.codecogs.com/gif.latex?l_0=0"/> である。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{array}{cl}&#x5C;vectwo{l_n}{w_n}%20&amp;%20=%20&#x5C;Rinv{&#x5C;phi_n}&#x5C;vectwo{u-u_n}{v-v_n}&#x5C;&#x5C;&#x5C;&#x5C;&amp;%20&#x5C;phi_n%20=%20&#x5C;dfrac{&#x5C;sum^n_{k=0}l_k}{2R},%20&#x5C;quad%20u_n%20=%20-&#x5C;clothox{&#x5C;phi_n},%20&#x5C;quad%20v_n%20=%20-%20&#x5C;clothoy{&#x5C;phi_n}&#x5C;end{array}"/></p>  
  
  
点<img src="https://latex.codecogs.com/gif.latex?Q_n(u_n,v_n)"/>は求める点<img src="https://latex.codecogs.com/gif.latex?Q"/>に収束する。計算上、十分 <img src="https://latex.codecogs.com/gif.latex?0"/> に近い値となるのが<img src="https://latex.codecogs.com/gif.latex?l_k"/>である時、求める点 <img src="https://latex.codecogs.com/gif.latex?P(l,%20w)"/>が次のように定まる。<img src="https://latex.codecogs.com/gif.latex?l"/>は、点<img src="https://latex.codecogs.com/gif.latex?KE"/>からの曲線長なので、曲線長 <img src="https://latex.codecogs.com/gif.latex?L"/>に累積曲線長<img src="https://latex.codecogs.com/gif.latex?&#x5C;sum^k_{n=0}l_n"/> を加えることになる。ここで、この点<img src="https://latex.codecogs.com/gif.latex?K"/>がクロソイド曲線上に存在するためには、<img src="https://latex.codecogs.com/gif.latex?0%20&#x5C;le%20l%20&#x5C;lt%20L"/> でなければならない。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{array}{cll}&#x5C;begin{pmatrix}l%20&#x5C;&#x5C;w&#x5C;end{pmatrix}%20%20&amp;%20=&#x5C;begin{pmatrix}L%20+%20(l_0%20+%20l_1%20+%20&#x5C;cdots%20+%20l_k)%20&#x5C;&#x5C;w_k&#x5C;end{pmatrix}　%20(0%20&#x5C;le%20l%20&lt;%20L)&#x5C;&#x5C;&#x5C;&#x5C;&#x5C;begin{pmatrix}l_n%20&#x5C;&#x5C;w_n&#x5C;end{pmatrix}%20&amp;%20=&#x5C;begin{pmatrix}&#x5C;cos&#x5C;phi_n%20&amp;%20&#x5C;sin&#x5C;phi_n%20&#x5C;&#x5C;-&#x5C;sin&#x5C;phi_n%20&amp;%20&#x5C;cos&#x5C;phi_n&#x5C;end{pmatrix}&#x5C;begin{pmatrix}u%20-%20u_n%20&#x5C;&#x5C;v%20-%20v_n&#x5C;end{pmatrix}&#x5C;&#x5C;&#x5C;&#x5C;&#x5C;phi_k%20&amp;%20=%20&#x5C;dfrac{&#x5C;sum^k_{n=0}l_n}{2R},%20&#x5C;quad%20u_k%20=%20-&#x5C;clothox{&#x5C;phi_k},%20&#x5C;quad%20v_k%20=%20%20-&#x5C;clothoy{&#x5C;phi_k}&#x5C;end{array}"/></p>  
  
  
###  <img src="https://latex.codecogs.com/gif.latex?KE-KA"/>クロソイド
  
  
以上、<img src="https://latex.codecogs.com/gif.latex?KE-KA"/> クロソイドの割り出し計算式は以下の通りまとめることができる。<img src="https://latex.codecogs.com/gif.latex?R&gt;0"/> の時、次の通りである。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{array}{cl}&#x5C;vectwo{u}{v}%20&amp;%20=R^{-1}(&#x5C;theta+&#x5C;tau)%20&#x5C;begin{pmatrix}x%20-%20x_{KE}%20&#x5C;&#x5C;y%20-%20y_{KE}&#x5C;end{pmatrix}%20-%20&#x5C;vectwo{x_&#x5C;tau}{-y_&#x5C;tau}%20&#x5C;&#x5C;&#x5C;&#x5C;&amp;%20&#x5C;tau%20=%20&#x5C;dfrac{L}{2R},%20&#x5C;quad%20x_&#x5C;tau%20=%20&#x5C;clothox{&#x5C;tau},%20&#x5C;quad%20y_&#x5C;tau%20=%20&#x5C;clothoy{&#x5C;tau}%20&#x5C;&#x5C;&#x5C;&#x5C;&#x5C;end{array}"/></p>  
  
  
<img src="https://latex.codecogs.com/gif.latex?R&lt;0"/> の時、次の通りである。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{array}{cl}&#x5C;vectwo{u}{v}%20&amp;%20=%20R^{-1}(&#x5C;theta-&#x5C;tau)&#x5C;begin{pmatrix}x%20-%20x_{KE}%20&#x5C;&#x5C;y%20-%20y_{KE}&#x5C;end{pmatrix}%20-%20&#x5C;vectwo{x_&#x5C;tau}{y_&#x5C;tau}%20&#x5C;&#x5C;&#x5C;&#x5C;&amp;%20&#x5C;tau%20=%20&#x5C;dfrac{L}{2|R|},%20&#x5C;quad%20x_&#x5C;tau%20=%20&#x5C;dfrac{A}{&#x5C;sqrt2}&#x5C;displaystyle&#x5C;int^{&#x5C;tau}_0%20&#x5C;dfrac{&#x5C;cos&#x5C;tau}{&#x5C;sqrt&#x5C;tau}%20d&#x5C;tau,%20&#x5C;quad%20y_&#x5C;tau%20=%20&#x5C;dfrac{A}{&#x5C;sqrt2}&#x5C;displaystyle&#x5C;int^{&#x5C;tau}_0%20&#x5C;dfrac{&#x5C;sin&#x5C;tau}{&#x5C;sqrt&#x5C;tau}%20d&#x5C;tau&#x5C;end{array}"/></p>  
  
  
まず、<img src="https://latex.codecogs.com/gif.latex?(u,%20v)"/>への変換の逆行列について、<img src="https://latex.codecogs.com/gif.latex?R%20&lt;%200"/> の時、<img src="https://latex.codecogs.com/gif.latex?|R|"/>の絶対値を外すと、<img src="https://latex.codecogs.com/gif.latex?&#x5C;tau%20=%20-%20&#x5C;dfrac{L}{2R}"/>であり、<img src="https://latex.codecogs.com/gif.latex?(u,%20v)"/>への変換式は <img src="https://latex.codecogs.com/gif.latex?R&gt;0"/>の場合と同じである。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{array}{cll}&#x5C;Rinv{(&#x5C;theta-&#x5C;tau)}%20&amp;%20=%20&#x5C;Rinv{(&#x5C;theta+&#x5C;frac{L}{2R})}%20&#x5C;quad%20(R%20&lt;%200)&#x5C;&#x5C;&#x5C;&#x5C;&#x5C;Rinv{(&#x5C;theta+&#x5C;tau)}%20&amp;%20=%20&#x5C;Rinv{(&#x5C;theta+&#x5C;frac{L}{2R})}%20&#x5C;quad%20(R%20&gt;%200)&#x5C;end{array}"/></p>  
  
  
次に、<img src="https://latex.codecogs.com/gif.latex?y_&#x5C;tau"/>の符号の違いを吸収するためには、<img src="https://latex.codecogs.com/gif.latex?x_&#x5C;tau%20=%20&#x5C;clothox{|&#x5C;tau|},%20&#x5C;quad%20y_&#x5C;tau%20=%20-%20sign(R)&#x5C;clothox{|&#x5C;tau|}"/>とすればよい。
  
まとめると、<img src="https://latex.codecogs.com/gif.latex?KE-KA"/> クロソイドの場合は、次の通りとなる。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{array}{cll}&#x5C;begin{pmatrix}u%20&#x5C;&#x5C;v&#x5C;end{pmatrix}%20&amp;%20=%20R^{-1}(&#x5C;theta+&#x5C;tau)&#x5C;begin{pmatrix}x%20-%20x_{KE}%20&#x5C;&#x5C;y%20-%20y_{KE}&#x5C;end{pmatrix}%20-&#x5C;begin{pmatrix}x_&#x5C;tau%20&#x5C;&#x5C;y_&#x5C;tau&#x5C;end{pmatrix}&#x5C;&#x5C;&#x5C;&#x5C;&amp;%20&#x5C;tau%20=%20&#x5C;dfrac{L}{2R},%20&#x5C;quad%20x_&#x5C;tau%20=%20&#x5C;dfrac{A}{&#x5C;sqrt2}&#x5C;displaystyle&#x5C;int^{|&#x5C;tau|}_0%20&#x5C;dfrac{&#x5C;cos&#x5C;tau}{&#x5C;sqrt&#x5C;tau}%20d&#x5C;tau,%20&#x5C;quad%20y_&#x5C;tau%20=%20-sign(R)&#x5C;dfrac{A}{&#x5C;sqrt2}&#x5C;displaystyle&#x5C;int^{|&#x5C;tau|}_0%20&#x5C;dfrac{&#x5C;sin&#x5C;tau}{&#x5C;sqrt&#x5C;tau}%20d&#x5C;tau&#x5C;&#x5C;&#x5C;&#x5C;&#x5C;begin{pmatrix}l%20&#x5C;&#x5C;w&#x5C;end{pmatrix}%20%20&amp;%20=&#x5C;begin{pmatrix}L%20+%20(l_0%20+%20l_1%20+%20&#x5C;cdots%20+%20l_k)%20&#x5C;&#x5C;w_k&#x5C;end{pmatrix}　%20(0%20&#x5C;le%20l%20&lt;%20L)&#x5C;&#x5C;&#x5C;&#x5C;&#x5C;begin{pmatrix}l_n%20&#x5C;&#x5C;w_n&#x5C;end{pmatrix}%20&amp;%20=&#x5C;begin{pmatrix}&#x5C;cos&#x5C;phi_n%20&amp;%20&#x5C;sin&#x5C;phi_n%20&#x5C;&#x5C;-&#x5C;sin&#x5C;phi_n%20&amp;%20&#x5C;cos&#x5C;phi_n&#x5C;end{pmatrix}&#x5C;begin{pmatrix}u%20-%20u_n%20&#x5C;&#x5C;v%20-%20v_n&#x5C;end{pmatrix}&#x5C;&#x5C;&#x5C;&#x5C;&amp;%20&#x5C;phi_k%20=%20&#x5C;dfrac{&#x5C;sum^k_{n=0}l_n}{2R},%20&#x5C;quad%20u_k%20=%20-&#x5C;clothox{|&#x5C;phi_k|},%20&#x5C;quad%20v_k%20=%20sign(R)&#x5C;clothoy{|&#x5C;phi_k|}&#x5C;end{array}"/></p>  
  
  
###  卵形クロソイド<img src="https://latex.codecogs.com/gif.latex?(KAE-KEE)"/>
  
  
クロソイドパラメータを <img src="https://latex.codecogs.com/gif.latex?A"/> とする卵形クロソイドは、基本クロソイド の<img src="https://latex.codecogs.com/gif.latex?KA-KE"/> の間に始点 <img src="https://latex.codecogs.com/gif.latex?KAE"/> を持ち、終端 <img src="https://latex.codecogs.com/gif.latex?KE"/> は終点<img src="https://latex.codecogs.com/gif.latex?KEE"/> と一致する。今、この点 <img src="https://latex.codecogs.com/gif.latex?KAE"/> での半径を <img src="https://latex.codecogs.com/gif.latex?R_1"/>、終点 <img src="https://latex.codecogs.com/gif.latex?KEE"/> での半径を <img src="https://latex.codecogs.com/gif.latex?R_2"/> として(<img src="https://latex.codecogs.com/gif.latex?R_1%20&gt;%20R_2"/>)、 点 <img src="https://latex.codecogs.com/gif.latex?KA"/> を求める。この点 <img src="https://latex.codecogs.com/gif.latex?KAE"/> または点 <img src="https://latex.codecogs.com/gif.latex?KEE"/> を所与の点として点 <img src="https://latex.codecogs.com/gif.latex?KA"/> が分かれば、前節までの基本クロソイドの式を全て再利用して割り出し計算を実施できる。ただし、交点 <img src="https://latex.codecogs.com/gif.latex?K"/> の存在する条件は、<img src="https://latex.codecogs.com/gif.latex?l&#x27;%20&#x5C;le%20l%20&lt;%20l&#x27;%20+%20L"/> である。ここで<img src="https://latex.codecogs.com/gif.latex?l&#x27;"/>は点<img src="https://latex.codecogs.com/gif.latex?KA-KAE"/>のクロソイド曲線長(<img src="https://latex.codecogs.com/gif.latex?=%20&#x5C;dfrac{A^2}{|R_1|}"/>)である。
  
<img src="https://latex.codecogs.com/gif.latex?R_1&gt;R_2&gt;0"/> である卵形クロソイドの点<img src="https://latex.codecogs.com/gif.latex?KAE(x_{KAE},y_{KAE})"/>での接線方向角を<img src="https://latex.codecogs.com/gif.latex?&#x5C;theta"/>、卵形クロソイドを包含する基本クロソイドとしての接線方向角<img src="https://latex.codecogs.com/gif.latex?&#x5C;tau"/>とする。この角度<img src="https://latex.codecogs.com/gif.latex?&#x5C;tau"/>での基本クロソイドとしての座標を<img src="https://latex.codecogs.com/gif.latex?(x_&#x5C;tau,%20y_&#x5C;tau)"/>とする。すると、原座標での点<img src="https://latex.codecogs.com/gif.latex?KA(x_{KA},y_{KA})"/>は次の方程式を満たす。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?R(-&#x5C;theta+&#x5C;tau)&#x5C;begin{pmatrix}x_{KA}%20-%20x_{KAE}%20&#x5C;&#x5C;y_{KA}%20-%20y_{KAE}&#x5C;end{pmatrix}%20+&#x5C;begin{pmatrix}x_&#x5C;tau%20&#x5C;&#x5C;y_&#x5C;tau&#x5C;end{pmatrix}%20=&#x5C;begin{pmatrix}0%20&#x5C;&#x5C;0&#x5C;end{pmatrix}"/></p>  
  
  
これを点<img src="https://latex.codecogs.com/gif.latex?KA(x_{KA},y_{KA})"/>について解くと、
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{pmatrix}x_{KA}&#x5C;&#x5C;y_{KA}&#x5C;end{pmatrix}%20=R^{-1}(-&#x5C;theta+&#x5C;tau)&#x5C;begin{pmatrix}0%20-%20x_{&#x5C;tau}%20&#x5C;&#x5C;0%20-%20y_{&#x5C;tau}&#x5C;end{pmatrix}%20+&#x5C;begin{pmatrix}x_{KAE}%20&#x5C;&#x5C;y_{KAE}&#x5C;end{pmatrix}%20=R(&#x5C;theta-&#x5C;tau)&#x5C;begin{pmatrix}%20-%20x_{&#x5C;tau}%20&#x5C;&#x5C;%20-%20y_{&#x5C;tau}&#x5C;end{pmatrix}%20+&#x5C;begin{pmatrix}x_{KAE}%20&#x5C;&#x5C;y_{KAE}&#x5C;end{pmatrix}"/></p>  
  
  
同様に、<img src="https://latex.codecogs.com/gif.latex?R_2%20&lt;%20R_1%20&lt;%200"/> の時、
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{pmatrix}x_{KA}&#x5C;&#x5C;y_{KA}&#x5C;end{pmatrix}%20=R(&#x5C;theta+&#x5C;tau)&#x5C;begin{pmatrix}%20-%20x_{&#x5C;tau}%20&#x5C;&#x5C;%20y_{&#x5C;tau}&#x5C;end{pmatrix}%20+&#x5C;begin{pmatrix}x_{KAE}%20&#x5C;&#x5C;y_{KAE}&#x5C;end{pmatrix}"/></p>  
  
  
となる。どちらも次の値を使う。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;tau%20=%20&#x5C;dfrac{l&#x27;}{2|R_1|},%20&#x5C;quad%20x_{&#x5C;tau}%20=%20&#x5C;dfrac{A}{&#x5C;sqrt2}&#x5C;int^{&#x5C;tau}_0%20&#x5C;dfrac{&#x5C;cos&#x5C;tau}{&#x5C;sqrt%20&#x5C;tau}d&#x5C;tau,%20&#x5C;quad%20y_{&#x5C;tau}%20=%20&#x5C;dfrac{A}{&#x5C;sqrt2}&#x5C;int^{&#x5C;tau}_0%20&#x5C;dfrac{&#x5C;sin&#x5C;tau}{&#x5C;sqrt%20&#x5C;tau}d&#x5C;tau"/></p>  
  
  
ここで、次の式に置き換えると式を共通化できる。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;tau%20=%20&#x5C;dfrac{l&#x27;}{2R_1},%20&#x5C;quad%20x_{&#x5C;tau}%20=%20&#x5C;dfrac{A}{&#x5C;sqrt2}&#x5C;int^{|&#x5C;tau|}_0%20&#x5C;dfrac{&#x5C;cos&#x5C;tau}{&#x5C;sqrt%20&#x5C;tau}d&#x5C;tau,%20&#x5C;quad%20y_{&#x5C;tau}%20=%20sign(R_1)&#x5C;dfrac{A}{&#x5C;sqrt2}&#x5C;int^{|&#x5C;tau|}_0%20&#x5C;dfrac{&#x5C;sin&#x5C;tau}{&#x5C;sqrt%20&#x5C;tau}d&#x5C;tau"/></p>  
  
  
さらに<img src="https://latex.codecogs.com/gif.latex?KAE-KEE"/> クロソイドは、点<img src="https://latex.codecogs.com/gif.latex?KAE"/>が始点であるから式をまとめると次の通りとなる。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{array}{cl}&#x5C;begin{pmatrix}u%20&#x5C;&#x5C;v&#x5C;end{pmatrix}%20&amp;%20=%20R^{-1}(&#x5C;theta)&#x5C;begin{pmatrix}x%20-%20x_{KA}%20&#x5C;&#x5C;y%20-%20y_{KA}&#x5C;end{pmatrix}%20=%20R^{-1}(&#x5C;theta)&#x5C;begin{pmatrix}x%20-%20x_{KAE}%20&#x5C;&#x5C;y%20-%20y_{KAE}&#x5C;end{pmatrix}%20-%20R^{-1}(&#x5C;theta)R(&#x5C;theta-&#x5C;tau)&#x5C;begin{pmatrix}%20-%20x_{&#x5C;tau}%20&#x5C;&#x5C;%20-%20y_{&#x5C;tau}&#x5C;end{pmatrix}&#x5C;&#x5C;&#x5C;&#x5C;&amp;%20=%20R^{-1}(&#x5C;theta)&#x5C;begin{pmatrix}x%20-%20x_{KAE}%20&#x5C;&#x5C;y%20-%20y_{KAE}&#x5C;end{pmatrix}%20+%20R^{-1}(&#x5C;tau)&#x5C;begin{pmatrix}%20x_{&#x5C;tau}%20&#x5C;&#x5C;%20y_{&#x5C;tau}&#x5C;end{pmatrix}&#x5C;end{array}"/></p>  
  
  
まとめると、<img src="https://latex.codecogs.com/gif.latex?KAE-KEE"/> 卵形クロソイドの場合次の式が成り立つ
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{array}{cl}&#x5C;begin{pmatrix}u%20&#x5C;&#x5C;v&#x5C;end{pmatrix}%20&amp;%20=%20R^{-1}(&#x5C;theta)&#x5C;begin{pmatrix}x%20-%20x_{KAE}%20&#x5C;&#x5C;y%20-%20y_{KAE}&#x5C;end{pmatrix}%20+%20R^{-1}(&#x5C;tau)&#x5C;begin{pmatrix}%20x_{&#x5C;tau}%20&#x5C;&#x5C;%20y_{&#x5C;tau}&#x5C;end{pmatrix}&#x5C;&#x5C;&#x5C;&#x5C;&#x5C;begin{pmatrix}l%20&#x5C;&#x5C;w&#x5C;end{pmatrix}%20&amp;%20=&#x5C;begin{pmatrix}l&#x27;%20+%20l_0%20+%20l_1%20+%20&#x5C;cdots%20+%20l_k%20&#x5C;&#x5C;w_k&#x5C;end{pmatrix}　(l&#x27;%20&#x5C;le%20l%20&lt;%20l&#x27;%20+%20L)&#x5C;&#x5C;&#x5C;&#x5C;&amp;%20l&#x27;%20%20=%20&#x5C;dfrac{A^2}{|R_1|},%20&#x5C;quad%20&#x5C;tau%20=%20&#x5C;dfrac{l&#x27;}{2R_1},%20&#x5C;quad%20x_&#x5C;tau%20=%20&#x5C;dfrac{A}{&#x5C;sqrt2}%20&#x5C;displaystyle&#x5C;int^{|&#x5C;tau|}_0%20&#x5C;dfrac{&#x5C;cos(&#x5C;tau)}{&#x5C;sqrt{&#x5C;tau}}%20d&#x5C;tau,%20&#x5C;quad%20y_&#x5C;tau%20=%20sign(R_1)&#x5C;dfrac{A}{&#x5C;sqrt2}%20&#x5C;displaystyle&#x5C;int^{|&#x5C;tau|}_0%20&#x5C;dfrac{&#x5C;sin(&#x5C;tau)}{&#x5C;sqrt{&#x5C;tau}}%20d&#x5C;tau%20&#x5C;&#x5C;&#x5C;&#x5C;%20&#x5C;begin{pmatrix}l_n%20&#x5C;&#x5C;w_n&#x5C;end{pmatrix}%20&amp;%20=&#x5C;begin{pmatrix}&#x5C;cos&#x5C;phi_n%20&amp;%20&#x5C;sin&#x5C;phi_n%20&#x5C;&#x5C;-&#x5C;sin&#x5C;phi_n%20&amp;%20&#x5C;cos&#x5C;phi_n&#x5C;end{pmatrix}&#x5C;begin{pmatrix}u%20-%20u_n%20&#x5C;&#x5C;v%20-%20v_n&#x5C;end{pmatrix}&#x5C;&#x5C;&#x5C;&#x5C;&amp;%20&#x5C;phi_k%20%20=%20&#x5C;dfrac{&#x5C;sum^k_{n=0}l_n}{2R_2},%20&#x5C;quad%20u_k%20=%20&#x5C;dfrac{A}{&#x5C;sqrt2}%20&#x5C;displaystyle&#x5C;int^{|&#x5C;phi_k|}_0%20&#x5C;dfrac{&#x5C;cos(&#x5C;tau)}{&#x5C;sqrt{&#x5C;tau}}%20d&#x5C;tau,%20&#x5C;quad%20v_k%20=%20sign(R_1)&#x5C;dfrac{A}{&#x5C;sqrt2}%20&#x5C;displaystyle&#x5C;int^{|&#x5C;phi_k|}_0%20&#x5C;dfrac{&#x5C;sin(&#x5C;tau)}{&#x5C;sqrt{&#x5C;tau}}%20d&#x5C;tau&#x5C;end{array}"/></p>  
  
  
###  卵形クロソイド<img src="https://latex.codecogs.com/gif.latex?(KEE-KAE)"/>
  
  
<img src="https://latex.codecogs.com/gif.latex?KE-KA"/>クロソイドの場合を原則そのまま利用できる。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{array}{cll}&#x5C;begin{pmatrix}u%20&#x5C;&#x5C;v&#x5C;end{pmatrix}%20&amp;%20=%20R^{-1}(&#x5C;theta+&#x5C;tau)&#x5C;begin{pmatrix}x%20-%20x_{KE}%20&#x5C;&#x5C;y%20-%20y_{KE}&#x5C;end{pmatrix}%20-&#x5C;begin{pmatrix}x_&#x5C;tau%20&#x5C;&#x5C;y_&#x5C;tau&#x5C;end{pmatrix}&#x5C;&#x5C;&#x5C;&#x5C;&amp;%20l&#x27;%20=%20&#x5C;dfrac{A^2}{|R_1|},%20&#x5C;quad%20&#x5C;tau%20=%20&#x5C;dfrac{l&#x27;%20+%20L}{2R_2},%20&#x5C;quad%20x_&#x5C;tau%20=%20-%20&#x5C;dfrac{A}{&#x5C;sqrt2}&#x5C;displaystyle&#x5C;int^{|&#x5C;tau|}_0%20&#x5C;dfrac{&#x5C;cos&#x5C;tau}{&#x5C;sqrt&#x5C;tau}%20d&#x5C;tau,%20&#x5C;quad%20y_&#x5C;tau%20=%20-%20sign(R_2)&#x5C;dfrac{A}{&#x5C;sqrt2}&#x5C;displaystyle&#x5C;int^{|&#x5C;tau|}_0%20&#x5C;dfrac{&#x5C;sin&#x5C;tau}{&#x5C;sqrt&#x5C;tau}%20d&#x5C;tau&#x5C;&#x5C;&#x5C;&#x5C;&#x5C;begin{pmatrix}l%20&#x5C;&#x5C;w&#x5C;end{pmatrix}%20%20&amp;%20=&#x5C;begin{pmatrix}l&#x27;%20+%20L%20+%20(l_0%20+%20l_1%20+%20&#x5C;cdots%20+%20l_k)%20&#x5C;&#x5C;w_k&#x5C;end{pmatrix}　%20(l&#x27;%20&#x5C;le%20l%20&lt;%20l&#x27;%20+%20L)&#x5C;&#x5C;&#x5C;&#x5C;&#x5C;begin{pmatrix}l_n%20&#x5C;&#x5C;w_n&#x5C;end{pmatrix}%20&amp;%20=&#x5C;begin{pmatrix}&#x5C;cos&#x5C;phi_n%20&amp;%20&#x5C;sin&#x5C;phi_n%20&#x5C;&#x5C;-&#x5C;sin&#x5C;phi_n%20&amp;%20&#x5C;cos&#x5C;phi_n&#x5C;end{pmatrix}&#x5C;begin{pmatrix}u%20-%20u_n%20&#x5C;&#x5C;v%20-%20v_n&#x5C;end{pmatrix}&#x5C;&#x5C;&#x5C;&#x5C;&amp;%20&#x5C;phi_k%20=%20&#x5C;dfrac{&#x5C;sum^k_{n=0}l_n}{2R_2},%20&#x5C;quad%20u_k%20=%20-%20&#x5C;dfrac{A}{&#x5C;sqrt2}%20&#x5C;displaystyle&#x5C;int^{|&#x5C;phi_k|}_0%20&#x5C;dfrac{&#x5C;cos&#x5C;tau}{&#x5C;sqrt{&#x5C;tau}}%20d&#x5C;tau,%20&#x5C;quad%20v_k%20=%20%20sign(R_2)&#x5C;dfrac{A}{&#x5C;sqrt2}%20&#x5C;displaystyle&#x5C;int^{|&#x5C;phi_k|}_0%20&#x5C;dfrac{&#x5C;sin&#x5C;tau}{&#x5C;sqrt{&#x5C;tau}}%20d&#x5C;tau&#x5C;end{array}"/></p>  
  
  
### 　　クロソイド割り出し式一覧表
  
  
|       式番号        |                     KA-KE                     |                                            KAE-KEE                                            |                                    KE-KA                                     |                                   KEE-KAE                                    |
| :-----------------: | :-------------------------------------------: | :-------------------------------------------------------------------------------------------: | :--------------------------------------------------------------------------: | :--------------------------------------------------------------------------: |
|   <img src="https://latex.codecogs.com/gif.latex?&#x5C;vectwo{u}{v}"/>   | <img src="https://latex.codecogs.com/gif.latex?R^{-1}(&#x5C;theta)&#x5C;vectwo{x%20-%20x_{KA}}{y-y_{KA}}"/> |     <img src="https://latex.codecogs.com/gif.latex?R^{-1}(&#x5C;theta)&#x5C;vectwo{x%20-%20x_{KAE}}{y-y_{KAE}}%20+%20R^{-1}(&#x5C;tau)&#x5C;vectwo{x_&#x5C;tau}{y_&#x5C;tau}"/>     | <img src="https://latex.codecogs.com/gif.latex?R^{-1}(&#x5C;theta+&#x5C;tau)&#x5C;vectwo{x%20-%20x_{KE}}{y-y_{KE}}%20-%20&#x5C;vectwo{x_&#x5C;tau}{y_&#x5C;tau}"/> | <img src="https://latex.codecogs.com/gif.latex?R^{-1}(&#x5C;theta+&#x5C;tau)&#x5C;vectwo{x%20-%20x_{KE}}{y-y_{KE}}%20-%20&#x5C;vectwo{x_&#x5C;tau}{y_&#x5C;tau}"/> |
|        <img src="https://latex.codecogs.com/gif.latex?l&#x27;"/>         |                       0                       |                                    <img src="https://latex.codecogs.com/gif.latex?&#x5C;dfrac{A^2}{&#x5C;|R_1&#x5C;|}"/>                                     |                                      0                                       |                         <img src="https://latex.codecogs.com/gif.latex?&#x5C;dfrac{A^2}{%20&#x5C;|%20R_1%20&#x5C;|%20}"/>                          |
|       <img src="https://latex.codecogs.com/gif.latex?&#x5C;tau"/>        |                       0                       |                                      <img src="https://latex.codecogs.com/gif.latex?&#x5C;dfrac{l&#x27;}{2R_1}"/>                                       |                               <img src="https://latex.codecogs.com/gif.latex?&#x5C;dfrac{L}{2R}"/>                               |                            <img src="https://latex.codecogs.com/gif.latex?&#x5C;dfrac{l&#x27;%20+%20L}{2R_2}"/>                            |
|      <img src="https://latex.codecogs.com/gif.latex?x_&#x5C;tau"/>       |                       0                       |                                     <img src="https://latex.codecogs.com/gif.latex?&#x5C;clothox{&#x5C;|&#x5C;tau&#x5C;|}"/>                                      |                             <img src="https://latex.codecogs.com/gif.latex?&#x5C;clothox{&#x5C;|&#x5C;tau&#x5C;|}"/>                             |                             <img src="https://latex.codecogs.com/gif.latex?&#x5C;clothox{&#x5C;|&#x5C;tau&#x5C;|}"/>                             |
|      <img src="https://latex.codecogs.com/gif.latex?y_&#x5C;tau"/>       |                       0                       |                                 <img src="https://latex.codecogs.com/gif.latex?sign(R_1)&#x5C;clothoy{&#x5C;|&#x5C;tau&#x5C;|}"/>                                 |                         <img src="https://latex.codecogs.com/gif.latex?-sign(R)&#x5C;clothoy{&#x5C;|&#x5C;tau&#x5C;|}"/>                         |                        <img src="https://latex.codecogs.com/gif.latex?-sign(R_2)&#x5C;clothoy{&#x5C;|&#x5C;tau&#x5C;|}"/>                        |
| <img src="https://latex.codecogs.com/gif.latex?&#x5C;vectwo{l_n}{w_n}"/> |                       >                       |                                               >                                               |                                      >                                       |                       <img src="https://latex.codecogs.com/gif.latex?&#x5C;Rinv{&#x5C;phi_n}&#x5C;vectwo{u_n}{v_n}"/>                       |
|      <img src="https://latex.codecogs.com/gif.latex?&#x5C;phi_n"/>       |                       >                       |                                               >                                               |                                      >                                       |                       <img src="https://latex.codecogs.com/gif.latex?&#x5C;dfrac{&#x5C;sum^n_{k=0}l_k}{2R_2}"/>                        |
|        <img src="https://latex.codecogs.com/gif.latex?u_k"/>        |            <img src="https://latex.codecogs.com/gif.latex?&#x5C;clothox{&#x5C;|&#x5C;phi_k&#x5C;|}"/>             |                                    <img src="https://latex.codecogs.com/gif.latex?&#x5C;clothox{&#x5C;|&#x5C;phi_k&#x5C;|}"/>                                     |                           <img src="https://latex.codecogs.com/gif.latex?-&#x5C;clothox{&#x5C;|&#x5C;phi_k&#x5C;|}"/>                            |                           <img src="https://latex.codecogs.com/gif.latex?-&#x5C;clothox{&#x5C;|&#x5C;phi_k&#x5C;|}"/>                            |
|        <img src="https://latex.codecogs.com/gif.latex?v_k"/>        |         <img src="https://latex.codecogs.com/gif.latex?sign(R)&#x5C;clothoy{&#x5C;|&#x5C;phi_k&#x5C;|}"/>         |                                <img src="https://latex.codecogs.com/gif.latex?sign(R_1)&#x5C;clothoy{&#x5C;|&#x5C;phi_k&#x5C;|}"/>                                |                        <img src="https://latex.codecogs.com/gif.latex?-sign(R)&#x5C;clothoy{&#x5C;|&#x5C;phi_k&#x5C;|}"/>                        |                       <img src="https://latex.codecogs.com/gif.latex?-sign(R_2)&#x5C;clothoy{&#x5C;|&#x5C;phi_k&#x5C;|}"/>                       |
|         <img src="https://latex.codecogs.com/gif.latex?l"/>         |               <img src="https://latex.codecogs.com/gif.latex?&#x5C;sum^k_{n=0}l_n"/>               |                                    <img src="https://latex.codecogs.com/gif.latex?l&#x27;%20+%20&#x5C;sum^k_{n=0}l_n"/>                                     |                             <img src="https://latex.codecogs.com/gif.latex?L+&#x5C;sum^k_{n=0}l_n"/>                              |                            <img src="https://latex.codecogs.com/gif.latex?l&#x27;+L+&#x5C;sum^k_{n=0}l_n"/>                            |
|         <img src="https://latex.codecogs.com/gif.latex?w"/>         |                       >                       |                                               >                                               |                                      >                                       |                                    <img src="https://latex.codecogs.com/gif.latex?w_k"/>                                     |
| <img src="https://latex.codecogs.com/gif.latex?&#x5C;vectwo{x_q}{y_q}"/> |                       >                       | <img src="https://latex.codecogs.com/gif.latex?R(&#x5C;theta)&#x5C;vectwo{u_k}{v_k}+R(&#x5C;theta-&#x5C;tau)&#x5C;vectwo{x_&#x5C;tau}{y_&#x5C;tau}+%20&#x5C;vectwo{x_{KAE}}{y_{KAE}}"/> |                                      >                                       |  <img src="https://latex.codecogs.com/gif.latex?R(&#x5C;theta+&#x5C;tau)&#x5C;vectwo{u_k+x_&#x5C;tau}{v_k+y_&#x5C;tau}+%20&#x5C;vectwo{x_{KEE}}{y_{KEE}}"/>  |
  
##  補足
  
  
###  回転行列; 線形代数
  
  
回転行列<img src="https://latex.codecogs.com/gif.latex?R(&#x5C;theta)"/>は、ある点を角度<img src="https://latex.codecogs.com/gif.latex?&#x5C;theta"/>回転させる特殊な行列である。回転行列の逆行列を逆回転行列と呼ぶ。回転行列<img src="https://latex.codecogs.com/gif.latex?R(&#x5C;theta)"/>と逆回転行列<img src="https://latex.codecogs.com/gif.latex?R^{-1}(&#x5C;tau)"/>は次の通りである。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?R(&#x5C;theta)%20=&#x5C;begin{pmatrix}&#x5C;cos&#x5C;theta%20&amp;%20-&#x5C;sin&#x5C;theta&#x5C;&#x5C;&#x5C;sin&#x5C;theta%20&amp;%20&#x5C;cos&#x5C;theta&#x5C;end{pmatrix}&#x5C;&#x5C;&#x5C;&#x5C;R^{-1}(&#x5C;tau)%20=&#x5C;begin{pmatrix}&#x5C;cos&#x5C;tau%20&amp;%20&#x5C;sin&#x5C;tau%20&#x5C;&#x5C;-&#x5C;sin&#x5C;tau%20&amp;%20&#x5C;cos&#x5C;tau&#x5C;end{pmatrix}&#x5C;&#x5C;&#x5C;&#x5C;"/></p>  
  
  
逆回転行列には<img src="https://latex.codecogs.com/gif.latex?R^{-1}(&#x5C;tau)=%20R(-&#x5C;tau)"/>という性質がある。<img src="https://latex.codecogs.com/gif.latex?&#x5C;theta"/>に<img src="https://latex.codecogs.com/gif.latex?-&#x5C;tau"/>を代入すると、逆回転行列となる。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?R(&#x5C;theta)|&#x5C;_{&#x5C;theta=-&#x5C;tau}%20=R(-&#x5C;tau)%20=&#x5C;begin{pmatrix}&#x5C;cos(-&#x5C;tau)%20&amp;%20-&#x5C;sin(-&#x5C;tau)&#x5C;&#x5C;&#x5C;sin(-&#x5C;tau)%20&amp;%20&#x5C;cos(-&#x5C;tau)&#x5C;end{pmatrix}%20=&#x5C;begin{pmatrix}&#x5C;cos&#x5C;tau%20&amp;%20&#x5C;sin&#x5C;tau&#x5C;&#x5C;-&#x5C;sin&#x5C;tau%20&amp;%20&#x5C;cos&#x5C;tau&#x5C;end{pmatrix}%20=R^{-1}(&#x5C;tau)"/></p>  
  
  
###  座標系の変換; 線形代数
  
  
ある座標系上の点<img src="https://latex.codecogs.com/gif.latex?(x,%20y)"/>が<img src="https://latex.codecogs.com/gif.latex?(x_0,y_0)"/>を原点として角度<img src="https://latex.codecogs.com/gif.latex?&#x5C;tau"/>回転させた新たな座標系上の点<img src="https://latex.codecogs.com/gif.latex?(u,%20v)"/>に一致する時、次の式が成り立つ。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{pmatrix}u%20&#x5C;&#x5C;v&#x5C;end{pmatrix}%20=R^{-1}(&#x5C;tau)&#x5C;begin{pmatrix}x%20-%20x_0&#x5C;&#x5C;y%20-%20y_0&#x5C;end{pmatrix}%20=&#x5C;begin{pmatrix}&#x5C;cos&#x5C;tau%20&amp;%20&#x5C;sin&#x5C;tau&#x5C;&#x5C;-&#x5C;sin&#x5C;tau%20&amp;%20&#x5C;cos&#x5C;tau&#x5C;end{pmatrix}&#x5C;begin{pmatrix}x%20-%20x_0&#x5C;&#x5C;y%20-%20y_0&#x5C;end{pmatrix}"/></p>  
  
  
-   **証明**
  
新たな座標系上の点を<img src="https://latex.codecogs.com/gif.latex?(u,%20v)"/>とすると、角度<img src="https://latex.codecogs.com/gif.latex?&#x5C;tau"/>回転させ、<img src="https://latex.codecogs.com/gif.latex?(x_0,%20y_0)"/>分、平行移動した先が元の座標<img src="https://latex.codecogs.com/gif.latex?(x,%20y)"/>であるから、次の式が成り立つ。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?R(&#x5C;tau)&#x5C;begin{pmatrix}u%20&#x5C;&#x5C;v&#x5C;end{pmatrix}%20+&#x5C;begin{pmatrix}x_0%20&#x5C;&#x5C;y_0&#x5C;end{pmatrix}%20=&#x5C;begin{pmatrix}x%20&#x5C;&#x5C;y&#x5C;end{pmatrix}&#x5C;&#x5C;&#x5C;&#x5C;"/></p>  
  
  
<img src="https://latex.codecogs.com/gif.latex?(x_0,%20y_0)"/>を移項して、逆回転行列を両辺にかける。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{array}{cl}(左辺)%20&amp;%20=%20R^{-1}(&#x5C;tau)R(&#x5C;tau)&#x5C;begin{pmatrix}u%20&#x5C;&#x5C;v&#x5C;end{pmatrix}%20=&#x5C;begin{pmatrix}1%20&amp;%200%20&#x5C;&#x5C;0%20&amp;%201&#x5C;end{pmatrix}&#x5C;begin{pmatrix}u%20&#x5C;&#x5C;v&#x5C;end{pmatrix}%20=&#x5C;begin{pmatrix}u%20&#x5C;&#x5C;v&#x5C;end{pmatrix}&#x5C;&#x5C;&#x5C;&#x5C;(右辺)%20&amp;%20=%20R^{-1}(&#x5C;tau)&#x5C;begin{pmatrix}x%20-%20x_0&#x5C;&#x5C;y%20-%20y_0&#x5C;end{pmatrix}%20=&#x5C;begin{pmatrix}&#x5C;cos&#x5C;tau%20&amp;%20&#x5C;sin&#x5C;tau&#x5C;&#x5C;-&#x5C;sin&#x5C;tau%20&amp;%20&#x5C;cos&#x5C;tau&#x5C;end{pmatrix}&#x5C;begin{pmatrix}x%20-%20x_0&#x5C;&#x5C;y%20-%20y_0&#x5C;end{pmatrix}&#x5C;&#x5C;&#x5C;&#x5C;&#x5C;therefore%20&#x5C;begin{pmatrix}u%20&#x5C;&#x5C;v&#x5C;end{pmatrix}&amp;%20=%20&#x5C;begin{pmatrix}(x%20-%20x_0)&#x5C;cos&#x5C;tau+(y%20-%20y_0)&#x5C;sin&#x5C;tau%20&#x5C;&#x5C;-(x%20-%20x_0)&#x5C;sin&#x5C;tau%20+(y%20-%20y_0)&#x5C;cos&#x5C;tau&#x5C;end{pmatrix}&#x5C;end{array}"/></p>  
  
  
###  射影ベクトル; 数 II
  
  
<img src="figure/segment.png" width="300"></img>
  
ベクトル<img src="https://latex.codecogs.com/gif.latex?&#x5C;vec{AP}%20=%20(x-x_0,%20y-y_0)"/> が、軸<img src="https://latex.codecogs.com/gif.latex?L"/>上に射影されたベクトルを<img src="https://latex.codecogs.com/gif.latex?&#x5C;vec{AQ}"/>、軸<img src="https://latex.codecogs.com/gif.latex?W"/>上に射影されたベクトルを<img src="https://latex.codecogs.com/gif.latex?&#x5C;vec{QP}"/>とする。軸<img src="https://latex.codecogs.com/gif.latex?L"/>の方向ベクトルは<img src="https://latex.codecogs.com/gif.latex?&#x5C;vec{e_L}=(&#x5C;cos&#x5C;tau,%20&#x5C;sin&#x5C;tau)"/>、軸<img src="https://latex.codecogs.com/gif.latex?W"/>の方向ベクトルは<img src="https://latex.codecogs.com/gif.latex?&#x5C;vec{e_W}=(-&#x5C;sin&#x5C;tau,%20&#x5C;cos&#x5C;tau)"/>である。これらは方向ベクトルなので、大きさは 1 である。<img src="https://latex.codecogs.com/gif.latex?|&#x5C;vec{e_L}|=|&#x5C;vec{e_W}|=1"/>。したがって、
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;vec{AQ}%20=%20&#x5C;dfrac{&#x5C;vec{AP}&#x5C;cdot&#x5C;vec{e_L}}{|&#x5C;vec{e_L}|^2}%20&#x5C;vec{e_L}%20=%20l&#x5C;vec{e_L}&#x5C;&#x5C;&#x5C;&#x5C;&#x5C;therefore%20l%20=%20&#x5C;frac{&#x5C;vec{AP}&#x5C;cdot&#x5C;vec{e_L}}{1^2}%20=%20(x-x_0)&#x5C;cos&#x5C;tau%20+%20(y%20-%20y_0)&#x5C;sin&#x5C;tau%20&#x5C;&#x5C;&#x5C;vec{QP}%20=%20&#x5C;dfrac{&#x5C;vec{AP}&#x5C;cdot&#x5C;vec{e_W}}{|&#x5C;vec{e_W}|^2}%20&#x5C;vec{e_W}%20=%20w&#x5C;vec{e_W}&#x5C;&#x5C;&#x5C;&#x5C;&#x5C;therefore%20w%20=%20&#x5C;frac{&#x5C;vec{AP}&#x5C;cdot&#x5C;vec{e_W}}{1^2}%20=%20-(x-x_0)&#x5C;sin&#x5C;tau%20+%20(y%20-%20y_0)&#x5C;cos&#x5C;tau"/></p>  
  
  
-   **証明**
  
点<img src="https://latex.codecogs.com/gif.latex?Q"/>は軸<img src="https://latex.codecogs.com/gif.latex?L"/>上の点なので比例定数<img src="https://latex.codecogs.com/gif.latex?l"/>とすると、<img src="https://latex.codecogs.com/gif.latex?&#x5C;vec{AQ}%20=%20l%20&#x5C;vec{e_L}"/>となる。<img src="https://latex.codecogs.com/gif.latex?&#x5C;vec{AQ}"/>と<img src="https://latex.codecogs.com/gif.latex?&#x5C;vec{QP}"/>は直交するので、<img src="https://latex.codecogs.com/gif.latex?&#x5C;vec{AQ}&#x5C;cdot&#x5C;vec{QP}%20=%200"/>となる。<img src="https://latex.codecogs.com/gif.latex?&#x5C;vec{QP}%20=%20&#x5C;vec{AP}%20-%20&#x5C;vec{AQ}"/> であるから、<img src="https://latex.codecogs.com/gif.latex?&#x5C;vec{QP}"/>を代入する。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{array}{cl}&amp;%20&#x5C;vec{AQ}&#x5C;cdot&#x5C;vec{QP}%20=%20&#x5C;vec{AQ}&#x5C;cdot(&#x5C;vec{AP}-&#x5C;vec{AQ})=%200&#x5C;&#x5C;&#x5C;implies%20&amp;%20l%20&#x5C;vec{e_L}%20&#x5C;cdot%20&#x5C;vec{AP}%20-%20l%20&#x5C;vec{e_L}%20&#x5C;cdot%20l%20&#x5C;vec{e_L}%20=%200&#x5C;&#x5C;&#x5C;implies%20&amp;%20l%20(&#x5C;vec{e_L}%20&#x5C;cdot%20&#x5C;vec{AP}%20-%20l%20|&#x5C;vec{e_L}|^2%20)%20=%200&#x5C;&#x5C;&amp;%20&#x5C;therefore%20l%20=%20&#x5C;dfrac{&#x5C;vec{AP}&#x5C;cdot%20&#x5C;vec{e_L}}{|&#x5C;vec{e_L}|^2}&#x5C;end{array}"/></p>  
  
  
軸<img src="https://latex.codecogs.com/gif.latex?W"/>でも同様の計算で、<img src="https://latex.codecogs.com/gif.latex?w%20=%20&#x5C;dfrac{&#x5C;vec{AP}&#x5C;cdot{&#x5C;vec{e_W}}}{|&#x5C;vec{e_W}|^2}"/>となる。
  
###  余弦定理
  
  
<img src="figure/segment.png" width="300"></img>
この図において、三角形<img src="https://latex.codecogs.com/gif.latex?PAB"/>の角度を<img src="https://latex.codecogs.com/gif.latex?&#x5C;theta"/>とすると、余弦定理から、<img src="https://latex.codecogs.com/gif.latex?|&#x5C;vec{PB}|^2%20=%20|&#x5C;vec{AP}|^2%20+%20|&#x5C;vec{AB}|^2%20-2%20|&#x5C;vec{AP}||&#x5C;vec{AB}|&#x5C;cos&#x5C;theta"/> が成り立つ。|<img src="https://latex.codecogs.com/gif.latex?&#x5C;vec{AP}|&#x5C;cos&#x5C;theta%20=%20l"/>であることに注意すると、次の式が成り立つ。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{cases}&#x5C;vec{PB}%20=%20(|&#x5C;vec{AB}|&#x5C;cos&#x5C;tau%20+%20x_0%20-%20x,%20|&#x5C;vec{AB}|&#x5C;sin&#x5C;tau%20+%20x_0%20-%20x)%20&#x5C;&#x5C;&#x5C;vec{AP}%20=%20(x%20-%20x_0,%20y%20-%20y_0)%20&#x5C;&#x5C;l%20=%20|&#x5C;vec{AP}|%20&#x5C;cos&#x5C;theta&#x5C;end{cases}"/></p>  
  
  
これらを余弦定理の式に代入する。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{array}{ll}(左辺)%20&amp;%20=%20(|&#x5C;vec{AB}|&#x5C;cos&#x5C;tau%20-(x%20-%20x_0))^2%20+%20(|&#x5C;vec{AB}|&#x5C;sin&#x5C;tau%20-%20(y%20-%20y_0))^2%20&#x5C;&#x5C;&amp;%20=%20&#x5C;cancel{|&#x5C;vec{AB}|^2}%20-2|&#x5C;vec{AB}|((x-x_0)&#x5C;cos&#x5C;tau%20+%20(y-y_0)&#x5C;sin&#x5C;tau)%20+%20&#x5C;cancel{(x-x_0)^2}%20+%20&#x5C;cancel{(y-y_0)^2}%20&#x5C;&#x5C;&#x5C;&#x5C;(右辺)%20&amp;%20=%20|&#x5C;vec{AP}|^2%20+%20|&#x5C;vec{AB}|^2%20-2%20|&#x5C;vec{AP}||&#x5C;vec{AB}|&#x5C;cos&#x5C;theta%20&#x5C;&#x5C;&amp;%20=%20&#x5C;cancel{(x-x_0)^2}%20+%20&#x5C;cancel{(y%20-%20y_0)^2}%20+%20&#x5C;cancel{|&#x5C;vec{AB}|^2}%20-2|&#x5C;vec{AB}|&#x5C;cdot%20l%20&#x5C;&#x5C;&#x5C;&#x5C;&#x5C;implies%20&amp;%202|&#x5C;vec{AB}|&#x5C;cdot%20l%20=%202|&#x5C;vec{AB}|((x-x_0)&#x5C;cos&#x5C;tau%20+%20(y-y_0)&#x5C;sin&#x5C;tau)%20&#x5C;&#x5C;&#x5C;end{array}"/></p>  
  
  
したがって、<img src="https://latex.codecogs.com/gif.latex?l%20=%20(x-x_0)&#x5C;cos&#x5C;tau%20+%20(y-y_0)&#x5C;sin&#x5C;tau"/>が成り立つ。
  
同様に、<img src="https://latex.codecogs.com/gif.latex?W"/>軸上の点<img src="https://latex.codecogs.com/gif.latex?Q_W"/>を考え、三角形<img src="https://latex.codecogs.com/gif.latex?PAQ_W"/>での余弦定理を考える。<img src="https://latex.codecogs.com/gif.latex?|&#x5C;vec{PQ_W}|^2%20=%20|&#x5C;vec{AP}|^2%20+%20|&#x5C;vec{AQ_W}|^2%20-2%20|&#x5C;vec{AP}||&#x5C;vec{AQ_W}|&#x5C;cos&#x5C;theta_w"/> である。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{array}{ll}(左辺)%20&amp;%20=%20(|&#x5C;vec{AQ_W}|&#x5C;cos(&#x5C;tau+&#x5C;pi&#x2F;2)%20-(x%20-%20x_0))^2%20+%20(|&#x5C;vec{AQ_W}|&#x5C;sin(&#x5C;tau+&#x5C;pi&#x2F;2)%20-%20(y%20-%20y_0))^2%20&#x5C;&#x5C;&amp;%20=%20&#x5C;cancel{|&#x5C;vec{AQ_W}|^2}%20-2|&#x5C;vec{AQ_W}|(-(x-x_0)&#x5C;sin&#x5C;tau%20+%20(y-y_0)&#x5C;cos&#x5C;tau)%20+%20&#x5C;cancel{(x-x_0)^2}%20+%20&#x5C;cancel{(y-y_0)^2}%20&#x5C;&#x5C;&#x5C;&#x5C;(右辺)%20&amp;%20=%20|&#x5C;vec{AP}|^2%20+%20|&#x5C;vec{AQ_W}|^2%20-2%20|&#x5C;vec{AP}||&#x5C;vec{AQ_W}|&#x5C;cos&#x5C;theta_w%20&#x5C;&#x5C;&amp;%20=%20&#x5C;cancel{(x-x_0)^2}%20+%20&#x5C;cancel{(y%20-%20y_0)^2}%20+%20&#x5C;cancel{|&#x5C;vec{AQ_W}|^2}%20-2|&#x5C;vec{AQ_W}|&#x5C;cdot%20w%20&#x5C;&#x5C;&#x5C;&#x5C;&#x5C;implies%20&amp;%202|&#x5C;vec{AQ_W}|&#x5C;cdot%20w%20=%202|&#x5C;vec{AQ_W}|(-(x-x_0)&#x5C;sin&#x5C;tau%20+%20(y-y_0)&#x5C;cos&#x5C;tau)&#x5C;end{array}"/></p>  
  
  
したがって、他の場合ど同様に、<img src="https://latex.codecogs.com/gif.latex?w=%20-(x-x_0)&#x5C;sin&#x5C;tau%20+%20(y-y_0)&#x5C;cos&#x5C;tau"/>が成り立つ。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;therefore%20&#x5C;begin{pmatrix}l%20&#x5C;&#x5C;w&#x5C;end{pmatrix}=%20&#x5C;begin{pmatrix}(x%20-%20x_0)&#x5C;cos&#x5C;tau+(y%20-%20y_0)&#x5C;sin&#x5C;tau%20&#x5C;&#x5C;-(x%20-%20x_0)&#x5C;sin&#x5C;tau%20+(y%20-%20y_0)&#x5C;cos&#x5C;tau&#x5C;end{pmatrix}"/></p>  
  
  
###  <img src="https://latex.codecogs.com/gif.latex?sign"/>関数
  
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?sign(x)%20=%20&#x5C;begin{cases}1%20&amp;%20&#x5C;text{if}%20&amp;%20x%20&gt;%200%20&#x5C;&#x5C;0%20&amp;%20&#x5C;text{if}%20&amp;%20x%20=%200%20&#x5C;&#x5C;-1%20&amp;%20&#x5C;text{if}%20&amp;%20x%20&lt;%200%20&#x5C;&#x5C;&#x5C;end{cases}"/></p>  
  
  
###  方向角<img src="https://latex.codecogs.com/gif.latex?&#x5C;theta"/>
  
  
任意の 2 点<img src="https://latex.codecogs.com/gif.latex?CA"/>を与えられた時の符号付き角度<img src="https://latex.codecogs.com/gif.latex?&#x5C;theta_{CA}"/>は次の式であった。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;theta&#x5C;_{CA}%20=%20&#x5C;arctan&#x5C;dfrac{y_a-y_c}{x_a-x_c}"/></p>  
  
  
ただし、<img src="https://latex.codecogs.com/gif.latex?arctan"/> 関数の値域は<img src="https://latex.codecogs.com/gif.latex?-&#x5C;pi%20&lt;%20&#x5C;theta_{CA}%20&#x5C;le%20&#x5C;pi"/> なので、軸<img src="https://latex.codecogs.com/gif.latex?X"/>を基準とした**方向角<img src="https://latex.codecogs.com/gif.latex?&#x5C;theta"/>は** <img src="https://latex.codecogs.com/gif.latex?0%20&#x5C;le%20&#x5C;theta%20&lt;%202&#x5C;pi"/> であるので、<img src="https://latex.codecogs.com/gif.latex?&#x5C;theta"/>を得るには <img src="https://latex.codecogs.com/gif.latex?&#x5C;theta_{CA}"/> が負の時だけ<img src="https://latex.codecogs.com/gif.latex?+2&#x5C;pi"/>分、この値を補正する必要がある。これは、sign 関数を使って次の通りとなる。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;theta%20=%20&#x5C;theta_{CA}%20+%20(1%20-%20sign(&#x5C;theta_{CA})%20|sign(&#x5C;theta_{CA})|&#x5C;pi"/></p>  
  
  
したがって、次の表により、方向角 <img src="https://latex.codecogs.com/gif.latex?&#x5C;theta"/>が成り立つことがわかる。
|条件|<img src="https://latex.codecogs.com/gif.latex?sign(&#x5C;theta_{CA})"/>|<img src="https://latex.codecogs.com/gif.latex?1-sign(&#x5C;theta_{CA})"/>|<img src="https://latex.codecogs.com/gif.latex?&#x5C;|sign(&#x5C;theta_{CA})&#x5C;|"/>| <img src="https://latex.codecogs.com/gif.latex?&#x5C;theta"/>|
|:-:|:-:|:-:|:-:|:-:|
|<img src="https://latex.codecogs.com/gif.latex?&#x5C;theta_{CA}&gt;0"/>|1|0|1| <img src="https://latex.codecogs.com/gif.latex?&#x5C;theta_{CA}"/>|
|<img src="https://latex.codecogs.com/gif.latex?&#x5C;theta_{CA}=0"/>|0|1|0| <img src="https://latex.codecogs.com/gif.latex?&#x5C;theta_{CA}"/>|
|<img src="https://latex.codecogs.com/gif.latex?&#x5C;theta_{CA}&lt;0"/>|-1|2|1| <img src="https://latex.codecogs.com/gif.latex?&#x5C;theta_{CA}%20+%202&#x5C;pi"/>|
  
#  路線における割り出し計算
  
  
##  複数の線形に一致する割り出し
  
  
路線は 3 種類の線形要素の組み合わせである。そこで、任意の点<img src="https://latex.codecogs.com/gif.latex?P(x,y)"/>が、路線中のどの線形要素上に対応するのか、探索する必要がある。素朴な線形探索では、路線の終端に近い領域ほど計時時間を必要とする実装になる。
  
一つのアイデアとして、各線形の始点と求めたい点<img src="https://latex.codecogs.com/gif.latex?P"/>との距離を計算しておき、最短距離となる始点を求める。始点は前後二つの線形の端点なので、その二つの線形に限って割り出し計算すると効率が良いはずである。この場合の計算量は <img src="https://latex.codecogs.com/gif.latex?O(n)"/>である。これより速くするなら**最近傍探索**用のデータ構造を導入する必要がある。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?"/></p>  
  
  