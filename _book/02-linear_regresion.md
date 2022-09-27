# Linear regression

## Ejercicio 4 {-}

*I collect a set of data (n = 100 observations) containing a single predictor and a quantitative response. I then fit a linear regression model to the data, as well as a separate cubic regression, i.e. $Y = \beta_{0} + \beta_{1}X + \beta_{2}X^{2} + \beta_{3}X^{3} + \varepsilon$.*

- **(a) Suppose that the true relationship between X and Y is linear, i.e. $Y = \beta_{0} + \beta_{1}X + \varepsilon$. Consider the training residual sum of squares ($RSS$) for the linear regression, and also the training $RSS$ for the cubic regression. Would we expect one to be lower than the other, would we expect them to be the same, or is there not enough information to tell? Justify your answer.**

    Al que estamos bajo el supuesto que la relación entre la variable respuesta es exactamente lineal y que el la esperanza del RSS lo podemos descomponer en : 

    \begin{equation*}
        E(RSS) = E\left[\left(Y - \hat{Y}\right)^{2}\right] = E\left[f(X) + \varepsilon - \hat{f}(X)\right]^{2} = \underbrace{\left[f(X) - \hat{f}(X)\right]^{2}}_{\longrightarrow 0} + Var(\varepsilon)
    \end{equation*}

    El primer sumando tiende a cero, ya que la relación es exactamente lineal y en el caso que nuestra $\hat{f}(X)$ considere una forma cúbica el sesgo por la especificación sería mayor que en este caso.

- **(b) Answer (a) using test rather than training $RSS$.**
    
    Como se comento anteriormente, se esperaría que el $RSS$ de training del modelo de regresión lineal sea mas bajo que el del modelo cúbico, debido a que la verdadera relación es lineal.
    El modelo cúbico al intentar ajustar con una especificación incorrecta es mas sensible a cambios en la muestra, por lo tanto esperaría una mayor varianza en el término de error.

- **(c) Suppose that the true relationship between X and Y is not linear, but we don’t know how far it is from linear. Consider the training $RSS$ for the linear regression, and also the training $RSS$ for the cubic regression. Would we expect one to be lower than the other, would we expect them to be the same, or is there not enough information to tell? Justify your answer.**

    En este caso, el modelo cúbico tendría un menor $RSS$ de training debido a que es un modelo mas flexible ya que seguira mas de cerca los puntos.

- **(d) Answer (c) using test rather than training $RSS$.**

    Si bien sabemos que la relación no es lineal, no sabemos que órden tiene la función polinomial que generan estos datos, modelos no lineales tendrían un menor sesgo por su flexibilidad aunque este puede crecer de forma considerable
    en el término de la varianza del ruido si el órden no es el correcto por más que sea un error sumamente saturado.
