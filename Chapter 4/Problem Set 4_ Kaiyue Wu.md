# Problem Set 4_ Kaiyue Wu

## 1. Compare the convergence rates of the four methods below by doing the following:
__(a)__

$\mu = \frac{1}{d},~~~~~~~~~ d = c-\sqrt{c^2-1} ~~~~~~~~~c=\frac{1}{2}(e^{-r\Delta}+e^{(r+\sigma^2)\Delta}),~~~~~~~~p=\frac{e^{r\Delta}-d}{u-d}$

__(b)__

$\mu = e^{r\Delta}(1+\sqrt{e^{\sigma^2\Delta}-1}),~~~~~~~~~ d = e^{r\Delta}(1-\sqrt{e^{\sigma^2\Delta}-1}) ~~~~~~~~~~~~~~p=\frac{1}{2}$

__(c)__

$\mu = e^{(r-\frac{\sigma^2}{2})\Delta+\sigma\Delta} ~~~~~~ d = e^{(r-\frac{\sigma^2}{2})\Delta-\sigma\Delta}~~~~~~~p=\frac{1}{2}$

__(d)__

$\mu = e^{\sigma\sqrt{\Delta}} ~~~~~~ d =e^{-\sigma\sqrt\Delta}~~~~~~~ p= \frac{1}{2}+\frac{1}{2}(\frac{(r-\frac{\sigma^2}{2})\sqrt\Delta}{\sigma})$



Answer: 

![image-20220427225019265](/Users/elliewu/Library/Application Support/typora-user-images/image-20220427225019265.png)

![image-20220428200746316](/Users/elliewu/Library/Application Support/typora-user-images/image-20220428200746316.png)

## 2. 

```python
AMZN Jan 2023 call expire on:						  2023-01-20
The current price as of April 27 is		 		2787.820068359375
The current volatility as of April 27 is  0.3147985505575901
The strike price we choose is 						3050
Days until expire is 											269
```

```python
The etimated Amazon call price with binomial method is 207.12028952948447
```

__**I choose the market option price is 302.75 with strike price of 3050, in which the strike price is same to my strike price 3050.**__

__The market price of 302.75 is higher than the estimated value of 207.120, and it not far from it.， but it still implies the market expects more volatility of Amazon stock in the near future.__

```python
The volatility should be about 41.48% to make the estimated price equal to the market price.
```

__In order to find corresponding volatility with this price, I iteratively recalculate call price with difference volatility and the volatility should be about 41.48% to make the estimated price equal to the market price.__

```python
target  = 302.75

eps= 0.001
count = 0
max_iter = 1500
vol = amzn_std
i =0
while abs(amzn_estimated-target)>0.01:
    if (amzn_estimated>target):
        vol -= eps
    else:
        vol += eps
    
    amzn_estimated = binoAmer_fast(s0=current_price,k=strike_price,r=rf,N=N,T=T,sigma=vol,option_type='c',formula='a')
    i+=1
    if i==max_iter:
        break
```

## 3. Consider the following information on the stock of a company and options on it: 
    S0 = 49, x = 50, r = 0.03, 𝜎 = 0.2, T= 0.3846 (20 weeks), 𝜇 = 0.14.
    Using the Binomial Method (any one of the parameter choices) estimate the following and draw the graphs:

![image-20220427230026505](/Users/elliewu/Library/Application Support/typora-user-images/image-20220427230026505.png)

![image-20220428200951457](/Users/elliewu/Library/Application Support/typora-user-images/image-20220428200951457.png)

## 4. 

__American puts keep having higher value than European puts, and the reason would be American puts have the right to exercise early, while European puts can only be hold until maturity. __

![image-20220427230058115](/Users/elliewu/Library/Application Support/typora-user-images/image-20220427230058115.png)



## 5. Compare the convergence rates of the two methods

![image-20220427230300312](/Users/elliewu/Library/Application Support/typora-user-images/image-20220427230300312.png)





## 6. Use Halton’s Low-Discrepancy Sequences to price European Call options.



```python
The estimated call price is: 3.724505550012962
```