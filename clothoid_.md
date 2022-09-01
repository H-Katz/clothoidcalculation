#  クロソイド曲線の数値計算
  
  
  
線分の長さ<img src="https://latex.codecogs.com/gif.latex?L"/>と曲率半径<img src="https://latex.codecogs.com/gif.latex?R"/>の積が定数(一定)となることが前提: <img src="https://latex.codecogs.com/gif.latex?RL=A^2"/>
  
カーブ中の任意の点について接線微小長さ<img src="https://latex.codecogs.com/gif.latex?dL"/>の微小角度<img src="https://latex.codecogs.com/gif.latex?d&#x5C;tau"/>とすると、<img src="https://latex.codecogs.com/gif.latex?dL=Rd&#x5C;tau"/>
  
よって、<img src="https://latex.codecogs.com/gif.latex?dL=&#x5C;frac{A^2}{L}d&#x5C;tau%20%20&#x5C;therefore%20LdL=A^2d&#x5C;tau"/>
  
この微分方程式を初期条件<img src="https://latex.codecogs.com/gif.latex?&#x5C;tau%20=%200でL=0"/>について解くと、
  
<img src="https://latex.codecogs.com/gif.latex?&#x5C;dfrac{L^2}{2}=A^2&#x5C;tau,%20&#x5C;tau%20=%20&#x5C;dfrac{L^2}{2A^2}=&#x5C;dfrac{L}{2R},L=A&#x5C;sqrt{2&#x5C;tau},%20%20R=&#x5C;dfrac{A^2}{L}=&#x5C;dfrac{A}{&#x5C;sqrt{2&#x5C;tau}}"/>
  
<img src="https://latex.codecogs.com/gif.latex?x,%20y"/>方向の微小長さは(マクローリン展開を利用して)
  
<img src="https://latex.codecogs.com/gif.latex?dx=dL&#x5C;cos&#x5C;tau=%20&#x5C;dfrac{A}{&#x5C;sqrt{2&#x5C;tau}}&#x5C;cos&#x5C;tau%20d&#x5C;tau%20=%20&#x5C;dfrac{A}{&#x5C;sqrt{2&#x5C;tau}}(1%20-%20&#x5C;dfrac{&#x5C;tau^2}{2!}%20+%20&#x5C;dfrac{&#x5C;tau^4}{4!}%20-%20&#x5C;dfrac{&#x5C;tau^6}{6!}%20...)%20d&#x5C;tau"/>
  
<img src="https://latex.codecogs.com/gif.latex?dy=dL&#x5C;sin&#x5C;tau=%20&#x5C;dfrac{A}{&#x5C;sqrt{2&#x5C;tau}}&#x5C;sin&#x5C;tau%20d&#x5C;tau%20=%20&#x5C;dfrac{A}{&#x5C;sqrt{2&#x5C;tau}}(&#x5C;tau%20-%20&#x5C;dfrac{&#x5C;tau^3}{3!}%20+%20&#x5C;dfrac{&#x5C;tau^5}{5!}%20-%20&#x5C;dfrac{&#x5C;tau^7}{7!}%20...)%20d&#x5C;tau"/>
  
よって積分すると
  
<img src="https://latex.codecogs.com/gif.latex?x=%20&#x5C;dfrac{A}{&#x5C;sqrt{2}}%20&#x5C;displaystyle&#x5C;int^&#x5C;tau_0%20&#x5C;dfrac{&#x5C;cos&#x5C;tau}{&#x5C;sqrt{&#x5C;tau}}%20=%20&#x5C;dfrac{A}{&#x5C;sqrt2{}}%20&#x5C;int^&#x5C;tau_0%20&#x5C;tau^{%20-1&#x2F;2%20}%20(1%20-%20&#x5C;dfrac{&#x5C;tau^2}{2!}%20+%20&#x5C;dfrac{&#x5C;tau^4}{4!}%20-%20&#x5C;dfrac{&#x5C;tau^6}{6!}%20&#x5C;dots)%20d&#x5C;tau"/>
  
<img src="https://latex.codecogs.com/gif.latex?=%20&#x5C;dfrac{A}{&#x5C;sqrt2{}}%20&#x5C;displaystyle&#x5C;int^&#x5C;tau_0%20(&#x5C;tau^{-1&#x2F;2}%20-%20&#x5C;frac{&#x5C;tau^{3&#x2F;2}}{2!}%20+%20%20&#x5C;frac{&#x5C;tau^{7&#x2F;2}}{4!}%20-%20%20&#x5C;frac{&#x5C;tau^{11&#x2F;2}}{6!}%20&#x5C;dots%20)d&#x5C;tau"/>
  
<img src="https://latex.codecogs.com/gif.latex?=%20&#x5C;dfrac{A}{&#x5C;sqrt2{}}%20&#x5C;left(2&#x5C;tau^{1&#x2F;2}%20-%20&#x5C;dfrac{2&#x5C;tau^{5&#x2F;2}}{5&#x5C;cdot2!}%20+%20%20&#x5C;dfrac{2&#x5C;tau^{9&#x2F;2}}{9&#x5C;cdot4!}%20-%20%20&#x5C;dfrac{2&#x5C;tau^{13&#x2F;2}}{13&#x5C;cdot6!}%20+%20&#x5C;dots%20+&#x5C;dfrac{(-1)^{n-1}%20&#x5C;tau^{(4n-3)&#x2F;2}}{(4n-3)(2n-2)!}+%20&#x5C;dots&#x5C;right)"/>
  
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?=%20A&#x5C;sqrt{2&#x5C;tau}&#x5C;left(1%20-%20&#x5C;dfrac{&#x5C;tau^2}{5&#x5C;cdot%202!}%20+%20%20&#x5C;dfrac{&#x5C;tau^4}{9&#x5C;cdot4!}%20-%20%20&#x5C;dfrac{&#x5C;tau^6}{13&#x5C;cdot6!}%20+%20&#x5C;dots%20+&#x5C;dfrac{(-1)^{n-1}%20&#x5C;tau^{2(n-1)}}{(4n-3)(2n-2)!}+%20&#x5C;dots&#x5C;right)%20&#x5C;tag{1}"/></p>  
  
  
<img src="https://latex.codecogs.com/gif.latex?=%20L&#x5C;left(1%20-%20&#x5C;dfrac{L^2}{40R^2}%20+%20%20&#x5C;dfrac{L^4}{3456R^4}%20-%20%20&#x5C;dfrac{L^6}{599040R^6}%20+&#x5C;dots&#x5C;right)"/>
  
/* コメント　*/
  
<img src="https://latex.codecogs.com/gif.latex?y=%20&#x5C;dfrac{A}{&#x5C;sqrt{2}}%20&#x5C;displaystyle&#x5C;int^&#x5C;tau_0%20&#x5C;dfrac{&#x5C;sin&#x5C;tau}{&#x5C;sqrt{&#x5C;tau}}%20=%20&#x5C;dfrac{A}{&#x5C;sqrt2{}}%20&#x5C;int^&#x5C;tau_0%20&#x5C;tau^{%20-1&#x2F;2%20}%20(&#x5C;tau%20-%20&#x5C;dfrac{&#x5C;tau^3}{3!}%20+%20&#x5C;dfrac{&#x5C;tau^5}{5!}%20-%20&#x5C;dfrac{&#x5C;tau^7}{7!}%20&#x5C;dots)%20d&#x5C;tau"/>
  
<img src="https://latex.codecogs.com/gif.latex?=%20&#x5C;dfrac{A}{&#x5C;sqrt2{}}%20&#x5C;displaystyle&#x5C;int^&#x5C;tau_0%20(&#x5C;tau^{1&#x2F;2}%20-%20&#x5C;frac{&#x5C;tau^{5&#x2F;2}}{3!}%20+%20%20&#x5C;frac{&#x5C;tau^{9&#x2F;2}}{5!}%20-%20%20&#x5C;frac{&#x5C;tau^{13&#x2F;2}}{7!}%20&#x5C;dots%20)d&#x5C;tau"/>
  
<img src="https://latex.codecogs.com/gif.latex?=%20&#x5C;dfrac{A}{&#x5C;sqrt2{}}%20&#x5C;left(&#x5C;dfrac{2}{3}&#x5C;tau^{3&#x2F;2}%20-%20&#x5C;dfrac{2&#x5C;tau^{7&#x2F;2}}{7&#x5C;cdot3!}%20+%20%20&#x5C;dfrac{2&#x5C;tau^{11&#x2F;2}}{11&#x5C;cdot5!}%20-%20%20&#x5C;dfrac{2&#x5C;tau^{15&#x2F;2}}{15&#x5C;cdot7!}%20+%20&#x5C;dots%20+&#x5C;dfrac{(-1)^{n-1}%20&#x5C;tau^{(4n-1)&#x2F;2}}{(4n-1)(2n-1)!}+%20&#x5C;dots&#x5C;right)"/>
  
<p align="center"><img src="https://latex.codecogs.com/gif.latex?=%20A&#x5C;sqrt{2&#x5C;tau}&#x5C;left(&#x5C;dfrac{&#x5C;tau}{3}%20-%20&#x5C;dfrac{&#x5C;tau^3}{7&#x5C;cdot%203!}%20+%20%20&#x5C;dfrac{&#x5C;tau^5}{11&#x5C;cdot5!}%20-%20%20&#x5C;dfrac{&#x5C;tau^7}{15&#x5C;cdot7!}%20+%20&#x5C;dots%20+&#x5C;dfrac{(-1)^{n-1}%20&#x5C;tau^{2n-1}}{(4n-1)(2n-1)!}+%20&#x5C;dots&#x5C;right)%20&#x5C;tag{2}"/></p>  
  
  
<img src="https://latex.codecogs.com/gif.latex?=%20&#x5C;dfrac{L^2}{6R}&#x5C;left(1%20-%20&#x5C;dfrac{L^2}{56R^2}%20+%20%20&#x5C;dfrac{L^4}{7040R^4}%20-%20%20&#x5C;dfrac{L^6}{1612800R^6}%20+%20&#x5C;dots%20&#x5C;right)"/>
  