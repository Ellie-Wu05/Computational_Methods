# Project 2

### Kaiyue Wu

## 1. Bivariate-Normal

Input : a

<span style = 'color:blue'>Output: -0.163864</span>

```python
The simulated correlation rho is: -0.1638640937610348
```

## 2. Evaluate the following expected values by using Monte Carlo simulation:

  Input: 𝜌 = 0.6 

<span style = 'color:blue'> Output: 1.5372813821388835</span>

```python
The Expected Value with 0.6 correlation is: 1.5372813821388835
```

## 3. 

### (a) The estimated value by simulation:

<img src="/Users/elliewu/Library/Application Support/typora-user-images/image-20220411110206770.png" alt="image-20220411110206770" style="zoom:50%;" />

### (b)

<p style="color:blue">The B(t) values of t=1,3,5 are related that they are all around 1 and the reason is the equation is a maritingale. </p>

----



For the equation : $e^{\frac{t}{2}}cos(W_t)$ , if we apply Ito's lemma         $f(t,B_t) = \frac{\partial f}{\partial t}d_t + \frac{\partial f}{\partial x}dB_t + \frac{1}{2}\frac{\partial^2 f}{\partial x^2}(dB_t)^2$

Let $Y(t,B_t) = e^{\frac{t}{2}}cos(W_t)$ , we have

$dy_t = \frac{1}{2}e^{\frac{1}{2}}cos(W_t) dt + e^{\frac{1}{2}}(-sin(W_t))dW_t + \frac{1}						{2}e^{\frac{1}{2}}(-cos(W_t))(dW_t)^2$ 

= $\frac{1}{2}e^{\frac{1}{2}}cos(W_t) dt + e^{\frac{1}{2}}(-sin(W_t))dW_t - \frac{1}{2}e^{\frac{1}{2}}cos(W_t)d_t$

= $e^{\frac{1}{2}}(-sin(W_t))dW_t$ = $-e^{\frac{1}{2}}sin(W_t)dW_t$

$Y_T - Y_0 = \int _{0}^{T}-e^{\frac{1}{2}}sin(W_t)dW_t$, 	thus: $Y_T= Y_0- \int _{0}^{T}e^{\frac{1}{2}}sin(W_t)dW_t$

$Y_0 = e^0cos(0) = 1$

$Y_T = 1 - \int _{0}^{T}e^{\frac{1}{2}}sin(W_t)dW_t$, which is a martingale.

Finally, if we take the expectation of $Y_T$, we see the expectation is always 1.

$E[Y_T] = E[1 - \int _{0}^{T}e^{\frac{1}{2}}sin(W_t)dW_t] = 1-0 = 1$

### (c) Expected value after variance control:

Here I apply the Antithetic Variates Reduction Method. 
		As we can see for A, the variance changes from 57.130 to 55.678, which does improve a little bit, but it cannot be considered truly effective. However, the variance of B5 decreases a lot, from 77.199 to 55.666, which can be seen as a big improvement. 

<img src="/Users/elliewu/Library/Application Support/typora-user-images/image-20220411110241195.png" alt="image-20220411110241195" style="zoom:50%;" />

## 4 .

### (a) The call price estimate call price by Monte Carlo simulation is 17.981594283190127.

```python
The estimate the price of this European Call option is: 17.981594283190127
```

### (b) The call price calculated by Black-Scholes is 18.28376570485581.

```python
The Black-Scholes price of this European Call option is: 18.28376570485581
```

### (c) The  call option price after using the Antithetic Variates reduction technique is 18.213360.

- The standard deviation before variance control is <span style="color:blue">34.29</span>
-  The standard deviation after variance control is <span style="color:blue">21.78</span>
-  We can see that we reduce the variance significantly. At the same time, this method improves the accuracy of simulation, it approaches the value calculated by Black-Scholes 18.284

```python
The price of this European Call option is with variance control is: 18.213359908553063
```

<img src="/Users/elliewu/Library/Application Support/typora-user-images/image-20220411110356129.png" alt="image-20220411110356129" style="zoom:50%;" />

## 5. 

### (a) Plot of $E(S_n)$

<img src="/Users/elliewu/Library/Application Support/typora-user-images/image-20220411110413588.png" alt="image-20220411110413588" style="zoom:50%;" />

### (b)(c) Plot of 6 paths and $E(Sn)$

<img src="/Users/elliewu/Library/Application Support/typora-user-images/image-20220411110558974.png" alt="image-20220411110558974" style="zoom:40%;" />

### (d) Plot of 6 paths and $E(Sn)$ If we change $\sigma$  from 18% to 35%.

- As we change the volatility from 18% to 35%, the expected value theoretically would not change, but the graph shows it actually becomes more fluctuated
- The variance of simulated 6 paths are way more than smaller volatility ones. 



<img src="/Users/elliewu/Library/Application Support/typora-user-images/image-20220411231454444.png" alt="image-20220411231454444" style="zoom:50%;" />                              <img src="/Users/elliewu/Library/Application Support/typora-user-images/image-20220411111040149.png" alt="image-20220411111040149" style="zoom:40%;" />

## 6. 

### (a)**Euler Discretization**

$\frac{dy}{dx} = f(y,t), and y(0) = y_0$, we can divide $[0,T]$ to $N$ equal parts so that $\tau = \frac{T}{N}$ as step.

For this equation, we have :  $ 4[\int_{0}^{1} \sqrt{1-x^2} \,dx] $ and for simplicity we let y = $4\sqrt{1-x^2}$


According to the formula $y_t = y_o \ + [ \int_{t_0}^{t} \ f(y_{\tau},\tau)d_\tau]$, we can know 

$y_{t_1} = y_o \ + [ \int_{t_0}^{t_1} \ f(y_{\tau},\tau)d_\tau]$

$y_{t_1} \approx y_1 = y_0 + f(y_0,t_0)\tau$

$y_{n+1} = y_n + f(y_n,t_n)\tau , \ n=0,1,2 ···· N-1$



We now implement this idea to get the estimated value: <span style="color:blue">3.14355</span>

```python
Estimate value by using the Euler’s discretization scheme is: 3.143555466911028.
```

### (b)  **Estimate the integral by Monte Carlo simulation.**

The estimated value by Monte Carlo simulation is : <span style="color:blue">3.13555</span>

```python
Estimate value by using the Monte Carlo simulation is: 3.1355512852508935.
```

### (c)  **Importance Sampling Method**

$\theta = 4 [ \int_{0}^{1} \sqrt{1-x^2} \,dx ] = \pi $

$= E\left[4\sqrt{1-u^2}\right]$

Let $x = U$, $ \ g(x) = 4\sqrt{1-x^2}$

$t(·) = \left\{
    \begin{array}\\
        \frac{1-ax^2}{1-\frac{a}{3}} & \mbox{for } \ [0,1] \\
        0 & \ else
    \end{array}
\right.$ 

$E_{t(·)}\left[ \frac{4\sqrt{1-y^2}}{t(y)}\right] \approx \frac{1}{N}\sum_{i=1}^{N} \frac{4\sqrt{1-y^2}}{t(y)}$



1. First, I try to get the alpha value by finding the minimum variance, and the result is 0.76, slightly different form the true optimal value of 0.74, therefore, I apply 0.74 in the following calculation.

2. Second, I use the acceptance - rejection method to simulate random variable with uniform distribution with t(·) 

3. Third, I reestimate with the sampling random variable generated from step 2.

4. Finally, I compare the expected value and variance, with and without variance control.

   ```python
   Estimate value by with importance sampling is: 3.149794491445853.
   ```

   The estimated value by with importance sampling is : <span style="color:blue">3.149794491445853</span>. 

   - The variance before importance sampling is <span style="color:blue">0.856790</span>
   - The variance after importance sampling is <span style="color:blue">0.191652</span>
   - We can observe that the variance has decreased significantly with variance control. However, in practice, the accuracy after importance sampling seems not appealing. If we keep generating different samples with accept-reject method, we might get values like 3.16, 3.15, even though the variance still remain small.

![image-20220411232746379](/Users/elliewu/Library/Application Support/typora-user-images/image-20220411232746379.png)
