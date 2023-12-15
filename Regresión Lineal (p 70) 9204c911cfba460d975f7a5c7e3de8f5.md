# Regresión Lineal (p.70)

---

<aside>
🎯 *Según James et al. (2013), en el libro "An Introduction to Statistical Learning", la regresión lineal es un método estadístico que se utiliza para modelar la relación entre una variable dependiente y una o más variables independientes. La variable dependiente es la variable que se está tratando de predecir, y las variables independientes son las variables que se utilizan para hacer la predicción. [AN INTRODUCTION TO STATISCTICAL LEARNING: with Applications with R](https://www.notion.so/AN-INTRODUCTION-TO-STATISCTICAL-LEARNING-with-Applications-with-R-b6f1d10032844592b50c82b4aadaadc0?pvs=21)*

</aside>

### 3.1 Regresión lineal simple

---

La regresión lineal se basa en la suposición de que la relación entre la variable dependiente$\ Y$ y las variables independientes $\ X$ es **lineal**. Esto significa que la relación entre las dos variables se puede modelar mediante la ecuación de una [línea recta](https://www.notion.so/l-nea-recta-81091b9995254cb5aac1c0f8eb0d2d55?pvs=21):

$$
\begin{equation} Y\approx \beta_0+\beta_1X \end{equation}

$$

Donde $\approx$ deberá interpretarse como **“es modelado aproximadamente…”** También, comúnmente, es bien dicho que: $Y$ **es regresado en** $X$.

$\beta_0$ y $\beta_1$ son constantes desconocidas que representan la **“intersección”** y la “**pendiente**” de una recta. Ambas serán conocidas como **parámetros del modelo**. Así entonces tenemos que:

$$
\begin{equation} \hat y\approx \hat\beta_0+\hat\beta_1x\end{equation}

$$

será nuestro **“modelo de parámetros”** donde una vez que usamos nuestros datos de entrenamiento para producir estimaciones para $\hat\beta_0$ y $\hat\beta_1$ podemos entonces hacer predicciones para cualquier valor de $\hat y=Y$ con base en $X=x$.

### 3.1.1 Estimación de parámetros o coeficientes

---

Para poder hacer predicciones podemos usar nuestros datos para poder hacer estimaciones de nuestros coeficientes. Ahora, si:

$$
\ (x_1,y_1), (x_2,y_2)\dots (x_n,y_n)

$$

representan $n$ pares ordenados de observaciones y cada uno representa un valor o medición de $Y$ a partir de $X$. En el dataset $“Advertising”$, cada uno de los datos representa el presupuesto designado para propaganda en la $TV$, $Radio$ y $Periódico$; y la cantidad de productos vendidos en 200 tiendas diferentes $(sales)$.

Nuestro objetivo entonces es estimar los coeficientes $\beta_0$ y $\beta_1$ que se ajusten mejor al modelo lineal $\hat y\approx \hat\beta_0+\hat\beta_1x$. En otras palabras necesitamos encontrar una recta de regresión ($least\ squares\ line$)$**\ ^1**$, ****la mejor, que se ajusta a los 200 datos de $TV \sim sales$ disponibles para este caso.

Para ajustar **un modelo de regresión lineal** a un conjunto de datos, uno de los métodos comúnmente utilizado es el de mínimos cuadrados. El método de mínimos cuadrados minimiza la suma de los cuadrados de las diferencias entre los valores observados de la variable dependiente y los valores predichos por el modelo.

Sabemos que $Y$ puede predecirse con $(2)$. Pero, si compramos el valor de la predicción con el valor de $X$ tendremos un error en los datos, un error residual$**\ ^2**$ $(RSS)$ que es igual a  $e=y_i-\hat y_i$. El $RSS$ total será igual a: 

$$
RSS= e_1^2+e_2^2+\dots +e_n^2
$$

Si sustituimos a  $\hat y_i$ por $\hat\beta_0+\hat\beta_1x_1$ por $e$ tenemos una expresión equivalente:

$$
RSS=(y_1-\hat\beta_0-\hat\beta_1x_1)^2+\dots+(y_n-\hat\beta_0-\hat\beta_1x_n)^2
$$

El [método de los mínimos cuadrados](https://www.notion.so/m-todo-de-los-m-nimos-cuadrados-3441aded2a684a97a5e7a6db43608a38?pvs=21) calcula a $\hat\beta_0$ y  $\hat\beta_1$ a partir de:

$$
\begin{split} & \hat\beta_1=\frac{\sum_{i=1}^{n}(x_i-\bar x)-(y_i-\bar y)}{\sum_{i=1}^{n}(x_i-\bar x)^2} \\\\ &\hat\beta_0=\bar y-\hat\beta\bar x \end{split}

$$

para $\bar y \equiv\frac {1}{n}\sum_{i=1}^{n} y_i$ y $\bar x \equiv\frac {1}{n}\sum_{i=1}^{n} x_i$ que en otras palabras son los promedios.

### 3.1.3 Evaluación de la exactitud de los coeficientes

---

La relación entre $X$ y $Y$ puede tomar la forma $Y=\ f(X)+\epsilon$ , para cualquier función $f$ desconocida, y donde $\epsilon$ es la variación en los datos que no se puede explicar por el modelo y que parte de una [distribución normal con promedio igual a cero](https://www.notion.so/distribuci-n-normal-con-promedio-igual-a-cero-3a7861e89ce842e1bcd249089fda7e68?pvs=21). En otras palabras, el error $\epsilon$ es lo que hace al modelo interesante.

$$
\begin{equation} Y=2+3X+\epsilon \end{equation}
$$

En la vida real nunca vamos a poder acceder a todos los datos que forman parte de nuestro modelo. Siempre estaremos acotados a un conjunto de datos (datos de observación) y de ahí tendremos que realizar nuestras predicciones.

La ecuación número ($3$)$**\ “least\ squares\ line”**$ es la ecuación de uno de los modelos, a partir de los coeficientes calculados $\hat \beta_0\$ y $\hat \beta_1$, que puede trata de imitar el verdadero comportamiento de$\ Y=2+3X$ la cual es nombrada$**\ “population\ regression\ line”$** y que generalmente es desconocida. Entonces, si, siempre tenemos acceso a diferentes conjuntos de datos de observación, con los cuales pueden calcular diferentes rectas$\ “least\ squares\ lines”$, dichas rectas van a ser parecidas, pero la que nunca cambiará es la recta$\ “population\ regression\ line”$ porque es la recta que representa a la ecuación.

Supongamos que estamos tratando de estimar el $\mu$ de una población para unos datos aleatorios de $Y$. Desafortunadamente, $\mu$ siempre será desconocida pero tenemos acceso a $n$ cantidad de datos de observación de $Y$, $y_1\dots \ y_n$ con los cuales podemos **“estimar”** $\mu$. Podemos decir entonces que $\hat\mu = \bar{y}$ donde $\bar{y}=\frac {1}{n}\sum_{i=1}^{n} y_i$ o sea el promedio de la muestra. El promedio de la población y de la muestra siempre van a ser diferentes, pero el promedio de la muestra puede ser una buena estimación del de la población.

Podemos decir que el problema de tratar de estimar a $\mu$ y el tratar de encontrar una línea de regresión a partir de los coeficientes $\hat \beta_0,\ \hat \beta_1$ es el mismo, pero existe un **sesgo**. Es decir que; esperaríamos que $\hat\mu$ fuera igual que $\mu$ para no existir ningún sesgo, pero esto nunca pasa. Siempre existe una estimación y una sobre estimación de  $\hat\mu$ sobre  $\mu$. Esta estimación puede ser inexacta debido a la aleatoriedad de los datos de observación. En otras palabras eso es lo que representa el sesgo. Sin embargo, si pudiéramos promediar a varios $\hat\mu$  de diferentes conjuntos de datos podemos estar seguros que ese promedio sería igual que $\mu$. Por lo tanto, con este ejemplo, podemos decir que los parámetros $\hat \beta_0\ y\ \hat \beta_1$, para diferentes conjuntos de datos, no serán siempre los mismos, pero siempre se acercarán a los valores reales de  $\beta_0\ , \beta_1$. ¿Qué tanto?, podemos estimarlo a partir del $[“standard\ error”](https://www.notion.so/varianza-y-error-est-ndar-SE-c23bd9a072134549bb476b092621cdfd?pvs=21)$ $SE$($\hat\mu$).

$$
\begin{equation} Var(\hat\mu)=SE(\hat\mu)^2= \frac{\sigma^2}{n}\end{equation}

$$

Donde $\sigma^2$ es la [desviación estándar](https://www.notion.so/varianza-y-desviaci-n-est-ndar-sigma-ae141a6773474e3a8d9522907ae129ea?pvs=21) para cada una de las entradas  $y_1$de $Y$. El error estándar lo que quiere decirnos es: ***“en qué proporción la estimación para $\hat\mu$ difiere del verdadero valor de $\mu$*”.** Esta diferencia también está acotada a la cantidad de datos observados, mientras más datos se tenga estaremos más cercanos al verdadero valor de $\mu$.

Del mismo modo podemos preguntarnos qué tan cercano es nuestro valor $\hat\beta_0$  y $\hat\beta_1$ del verdadero valor de $\beta_0$ y $\beta_1$. Para poder calcular el$“standard\ error”$ asociado a $\hat\beta_0$ y $\hat\beta_1$ tenemos que:

$$
\begin{equation} \begin{split}
& SE(\hat\beta_0)^2=\sigma^2\bigg[\frac{1}{n}+\frac{\bar x^2}{\sum_{x=1}^n(x_i-\bar x)^2}\bigg] \\\\ & SE(\hat\beta_1)^2=\frac{\sigma^2}{\sum_{x=i}^n(x_i-\bar x^2)} \end{split} \end{equation}
$$

Donde $[\sigma^2=Var(\epsilon)](https://www.notion.so/variancia-de-una-variable-aleatoria-epsilon-9ad349ab0cc04b88bcb67dbbb4e84f2f?pvs=21)$, en otras palabras es la variancia de una variable aleatoria $\epsilon_i$ y donde se considera que es más deseable que los errores tengan una varianza en común y que no estén correlacionados. El error estándar del estimador de la pendiente, $SE(\hatβ_1)$, es menor cuando los $x_i$ están más dispersos. Esto significa que la estimación de la pendiente será más precisa cuando los $x_i$ estén más dispersos. También se puede ver que el $SE(\hatβ_0)$ del intercepto es igual a la media $\bar y$ si el valor de $\bar x$ fuera igual a cero. En general, es importante tener en cuenta que la varianza del error [es un parámetro desconocido](https://www.notion.so/varianza-del-error-como-par-metro-desconocido-87d1a450f2e84ec59b341caa7f330e19?pvs=21) que no podemos observar directamente. Sin embargo, podemos estimar la varianza del error a partir de los datos utilizando un estimador, como la varianza muestral. Este estimador para \sigma es conocido como $“residual\ standard\ error”$ y está dado por $RSE=\sqrt{RSS/(n-2)}$. Estrictamente hablando; cuando $\sigma²$ es calculado desde los datos es importante tener en cuenta que el error estándar del estimador de la pendiente se debe escribir como $\widehat{SE}(\hat\beta_1)$.

Los errores estándar pueden ser utilizados como intervalos de confianza. El intervalo de confianza se define como un rango de valores tal que con un intervalo del $95\%$ de probabilidad, el rango contendrá el verdadero valor desconocido del parámetro. El rango es definido en términos del límite superior e inferior de la muestra de los datos. Un intervalo de confianza de $95\%$ tiene la siguiente propiedad: si tomamos varias muestras y construimos sus intervalos de confianza para cada una de ellas, el $95\%$ de los intervalos de confianza contendrán el verdadero valor del parámetro desconocido. Para una regresión lineal, el intervalo de confianza de un $95\%$ toma la siguiente forma:

$$
\begin{equation} \hat\beta_1 \pm2\cdot SE(\hat\beta_1)\end{equation}
$$

Hay un 95% de probabilidad de que en el intervalo:

$$
\begin{equation} \bigg[\hat\beta_1-2\cdot SE(\hat\beta_1),\hat\beta_1+2\cdot SE(\hat\beta_1)\bigg] \end{equation}
$$

contenga el verdadero valor de $\beta_1$. De manera similar, el intervalo de confianza para $\beta_0$ aproximadamente toma la forma:

$$
\begin{equation} \hat\beta_0 \pm2\cdot SE(\hat\beta_0)\end{equation}
$$

Para el caso de $“Advertising”$, el intervalo$**\ ^3**$ con un $95\%$ de confianza construido para $\beta_0$ fue de $[6.130,7.935]$, y para $\beta_1$ fue de $[0.042,0.053]$. Por lo tanto, podemos concluir que; sin ningún presupuesto asignado a la publicidad de televisión, en promedio, el número de artículos vendidos rondarán entre $6, 130$ y $7, 935$ unidades. Del mismo modo, por cada $\$ 1,000$  asignados a la publicidad de televisión en promedio las ventas serán entre 42 y 43 unidades. 

El $“standard\ error”$ también se puede utilizar para plantear las pruebas de hipótesis de los coeficientes. La más común de todas es la de la hipótesis nula

Regresión lineal de $sales \approx \beta_0+\beta_1*TV$

```r
# cargamos los datos en una variable llamada "df"

attach(df)
plot(TV,sales, pch=16)
lm.fit=lm(sales ~ TV,df)
abline(lwd=2,col="red",lm.fit)
```

![$**\ ^1**$ *Advertising scatter plot sales ~ TV*](Regresio%CC%81n%20Lineal%20(p%2070)%209204c911cfba460d975f7a5c7e3de8f5/Untitled.png)

$**\ ^1**$ *Advertising scatter plot sales ~ TV*

```r
plot(TV,sales, pch=20, col="red")
abline(lwd=2,col="blue",lm.fit)
# obtenemos las predicciónes del modelo
predictions = predict(lm.fit)
segments(TV, sales, TV, predictions, lwd=0.3)
```

![$**\ ^2**$ *Cada segmento de línea de color gris representa un residuo.*](Regresio%CC%81n%20Lineal%20(p%2070)%209204c911cfba460d975f7a5c7e3de8f5/Untitled%201.png)

$**\ ^2**$ *Cada segmento de línea de color gris representa un residuo.*

```r
View(lm.fit)
```

![*resumen del modelo*](Regresio%CC%81n%20Lineal%20(p%2070)%209204c911cfba460d975f7a5c7e3de8f5/Untitled%202.png)

*resumen del modelo*

```r
coef(lm.fit)
```

```
(Intercept)          TV  
7.03259355  0.04753664
```

---

```r
confint(lm.fit)
```

```
						2.5 %     97.5 %
(Intercept) 6.12971927 7.93546783
TV          0.04223072 0.05284256
```

**Aspectos importantes**

- a
- b
- c

---

Definiciones a partir del autor.

<aside>
🎯 Un sistema de $m$ ecuaciones lineales en $n$ variables es un conjunto de $m$ ecuaciones, cada una de las cuales es lineal en las mismas $n$ variables. [FUNDAMENTOS DE ÁLGEBRA LINEAL](https://www.notion.so/FUNDAMENTOS-DE-LGEBRA-LINEAL-555414b9943345aab4fd1ca90077b50f?pvs=21)

</aside>

$\begin{alignedat}{2}&
a_{11}x_1+ a_{12}x_2+a_{13}x_3+\dotsc+a_{1n}x_n=\ b_1\\&a_{21}x_1+ a_{22}x_2+a_{23}x_3+\dotsc+a_{2n}x_n=\ b_2\\&a_{31}x_1+ a_{32}x_2+a_{33}x_3+\dotsc+a_{3n}x_n=\ b_3\\\vdots\\&a_{m1}x_1+ a_{m2}x_2+a_{m3}x_3+\dotsc+a_{mn}x_n=\ b_m\end{alignedat}$

**NOTA: un sistema de ecuaciones puede tener:**

- exactamente una solución.
- un número infinito de soluciones (p.ej.) cuando se obtienen soluciones como $\ 0=0$ entre las ecuaciones de algún sistema.
- no tiene solución (p.ej.) cuando se obtienen soluciones como $\ 0=2$ entre las ecuaciones de algún sistema.

[Recursos](Regresio%CC%81n%20Lineal%20(p%2070)%209204c911cfba460d975f7a5c7e3de8f5/Recursos%20ad88798d634d41c3817749b36b7472ad.csv)

**Aspectos importantes**

- a
- b
- c

---

Definiciones a partir del autor.

<aside>
🎯 Un sistema de $m$ ecuaciones lineales en $n$ variables es un conjunto de $m$ ecuaciones, cada una de las cuales es lineal en las mismas $n$ variables. [FUNDAMENTOS DE ÁLGEBRA LINEAL](https://www.notion.so/FUNDAMENTOS-DE-LGEBRA-LINEAL-555414b9943345aab4fd1ca90077b50f?pvs=21)

</aside>

$\begin{alignedat}{2}&
a_{11}x_1+ a_{12}x_2+a_{13}x_3+\dotsc+a_{1n}x_n=\ b_1\\&a_{21}x_1+ a_{22}x_2+a_{23}x_3+\dotsc+a_{2n}x_n=\ b_2\\&a_{31}x_1+ a_{32}x_2+a_{33}x_3+\dotsc+a_{3n}x_n=\ b_3\\\vdots\\&a_{m1}x_1+ a_{m2}x_2+a_{m3}x_3+\dotsc+a_{mn}x_n=\ b_m\end{alignedat}$

**NOTA: un sistema de ecuaciones puede tener:**

- exactamente una solución.
- un número infinito de soluciones (p.ej.) cuando se obtienen soluciones como $\ 0=0$ entre las ecuaciones de algún sistema.
- no tiene solución (p.ej.) cuando se obtienen soluciones como $\ 0=2$ entre las ecuaciones de algún sistema.