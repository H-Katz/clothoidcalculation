---
title: 位置出し計算
author: 秦野克彦
rights: '© 2022 合同会社Kiah'
language: ja-JP
output:
    custom_document: {path: ./ichidashi.epub}
ebook:
    authors: 秦野克彦
    title: 位置出し計算
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
  
- [位置出し](#位置出し )
  - [GPS 機器での位置出し](#gps-機器での位置出し )
  - [光波での位置出し](#光波での位置出し )
  
<!-- /code_chunk_output -->
  
</div>
  
<div style="page-break-before:always"></div>
  
  
  
  
#  位置出し
  
  
位置出しとは、路線座標上の点<img src="https://latex.codecogs.com/gif.latex?P(x,y)"/>が与えられた時、目的座標<img src="https://latex.codecogs.com/gif.latex?(x_t,%20y_t)"/>に対して、前後左右どれくらい移動すれば良いか誘導するための業務である。ここでは求める前後・左右の計算結果を<img src="https://latex.codecogs.com/gif.latex?(&#x5C;Delta%20d,&#x5C;Delta%20w)"/>とする。
  
##  GPS 機器での位置出し
  
  
下の図の通り、目的座標を点<img src="https://latex.codecogs.com/gif.latex?T(x_t,%20y_t)"/>、自己位置を点<img src="https://latex.codecogs.com/gif.latex?P(x,%20y)"/>とし、GPS 機器による計測結果として、自己位置<img src="https://latex.codecogs.com/gif.latex?(x,%20y)"/>、方向角<img src="https://latex.codecogs.com/gif.latex?&#x5C;theta"/>がわかるものとする。すると誘導のために必要な<img src="https://latex.codecogs.com/gif.latex?(&#x5C;Delta%20d,&#x5C;Delta%20w)"/>は、自己位置<img src="https://latex.codecogs.com/gif.latex?(x,%20y)"/>を原点とする方向角<img src="https://latex.codecogs.com/gif.latex?&#x5C;theta"/>の座標系に変換すれば良い。
  
<img src="figure/ichidashi_GPS.png" width="800"></img>
  
したがって、求める式は次の通りである。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;vectwo{&#x5C;Delta%20d}{&#x5C;Delta%20w}%20=%20&#x5C;Rinv{&#x5C;theta}&#x5C;vectwo{x_t%20-%20x}{y_t%20-%20y}%20=%20&#x5C;Rinvthree{&#x5C;theta}{x_t%20-%20x}{y_t%20-%20y}"/></p>  
  
  
  
  
  
##  光波での位置出し
  
  
下の図の通り、目的座標を点<img src="https://latex.codecogs.com/gif.latex?T(x_t,%20y_t)"/>、自己位置を点<img src="https://latex.codecogs.com/gif.latex?P(x,%20y)"/>とし、光波による計測結果として、夾角<img src="https://latex.codecogs.com/gif.latex?&#x5C;phi"/>、距離<img src="https://latex.codecogs.com/gif.latex?d"/>がわかるものとする。すると誘導のために必要な<img src="https://latex.codecogs.com/gif.latex?(&#x5C;Delta%20d,&#x5C;Delta%20w)"/>は、自己位置<img src="https://latex.codecogs.com/gif.latex?(x,%20y)"/>を原点とする自己位置<img src="https://latex.codecogs.com/gif.latex?P"/>から器械点<img src="https://latex.codecogs.com/gif.latex?K"/>への方向角<img src="https://latex.codecogs.com/gif.latex?&#x5C;theta_k"/>の座標系に変換すれば良い。
  
<img src="figure/ichidashi_opticmeasure.png" width="800"></img>
  
光波の場合、光波の据付位置を示す器械点<img src="https://latex.codecogs.com/gif.latex?K(x_k,%20y_k)"/>は与えられている。夾角の基準になる後視点<img src="https://latex.codecogs.com/gif.latex?B"/>はどこでも良いが、ここでは仮に目的座標<img src="https://latex.codecogs.com/gif.latex?T"/>からの垂線が交わる中心線の座標<img src="https://latex.codecogs.com/gif.latex?(x_b,%20y_b)"/>とする。これは路線計算で求めることができるのでここでは与えられているものとみなす。
  
まず、自己位置<img src="https://latex.codecogs.com/gif.latex?P(x,%20y)"/>を求めるために、直線 <img src="https://latex.codecogs.com/gif.latex?KP"/> の方向角<img src="https://latex.codecogs.com/gif.latex?&#x5C;theta_p"/>を求める。二点<img src="https://latex.codecogs.com/gif.latex?K,P"/>が与えられた時の方向角は 直線 <img src="https://latex.codecogs.com/gif.latex?KB"/> が基準であるから、計測した夾角と合わせて次の通りとなる。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;theta_p%20=%20&#x5C;phi%20+%20tan^{-1}&#x5C;frac{y_b%20-%20y_k}{x_b%20-%20x_k}"/></p>  
  
  
計測された距離は<img src="https://latex.codecogs.com/gif.latex?d"/>で、方向角がこの<img src="https://latex.codecogs.com/gif.latex?&#x5C;theta_p"/>となるから、求める自己位置<img src="https://latex.codecogs.com/gif.latex?P(x,%20y)"/>は次の通りである。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;vectwo{x}{y}%20=%20&#x5C;R{&#x5C;theta_p}&#x5C;vectwo{d}{0}%20+%20&#x5C;vectwo{x_k}{y_k}=%20&#x5C;vectwo{d&#x5C;cos&#x5C;theta_p%20+%20x_k}{d&#x5C;sin&#x5C;theta_p%20+%20y_k}"/></p>  
  
  
次に求めたい<img src="https://latex.codecogs.com/gif.latex?(&#x5C;Delta%20d,&#x5C;Delta%20w)"/>を計算するには、自己位置<img src="https://latex.codecogs.com/gif.latex?P"/>からみた器械点<img src="https://latex.codecogs.com/gif.latex?K"/>の方向角<img src="https://latex.codecogs.com/gif.latex?&#x5C;theta_k"/>が必要である。これは<img src="https://latex.codecogs.com/gif.latex?&#x5C;theta_p"/>とちょうど向きが逆になるので、<img src="https://latex.codecogs.com/gif.latex?&#x5C;theta_k%20=%20&#x5C;theta_p%20+%20&#x5C;pi"/>となる。
  
以上により、自己位置<img src="https://latex.codecogs.com/gif.latex?(x,%20y)"/>とその点の方向角<img src="https://latex.codecogs.com/gif.latex?&#x5C;theta_k"/>がわかったので、<img src="https://latex.codecogs.com/gif.latex?(&#x5C;Delta%20d,&#x5C;Delta%20w)"/>は次の通りである。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;vectwo{&#x5C;Delta%20d}{&#x5C;Delta%20w}%20=%20&#x5C;Rinv{&#x5C;theta_k}&#x5C;vectwo{x_t%20-%20x}{y_t%20-%20y}%20=%20&#x5C;Rinvthree{&#x5C;theta_k}{x_t%20-%20x}{y_t%20-%20y}"/></p>  
  
  
まとめると、光波による位置出しは、次の式で計算すればよい。
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?&#x5C;begin{aligned}%20&#x5C;theta_p%20&amp;%20=%20&#x5C;phi%20+%20tan^{-1}&#x5C;frac{y_b%20-%20y_k}{x_b%20-%20x_k}%20&#x5C;&#x5C;&#x5C;&#x5C;&#x5C;vectwo{x}{y}%20&amp;%20=%20&#x5C;vectwo{d&#x5C;cos&#x5C;theta_p%20+%20x_k}{d&#x5C;sin&#x5C;theta_p%20+%20y_k}　&#x5C;&#x5C;&#x5C;&#x5C;&#x5C;theta_k%20&amp;%20=%20&#x5C;theta_p%20+%20&#x5C;pi%20&#x5C;&#x5C;&#x5C;&#x5C;&#x5C;vectwo{&#x5C;Delta%20d}{&#x5C;Delta%20w}%20&amp;%20=%20%20&#x5C;Rinvthree{&#x5C;theta_k}{x_t%20-%20x}{y_t%20-%20y}&#x5C;end{aligned}"/></p>  
  
  