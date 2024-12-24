# Valuation option

* $S_{t}$ price at $t$ (at valuation date)
*  $K$ strike
*  $r$ spot rate
*  $\sigma$ volatility
*  $T$ expiry
*  $t$ valuation date
*  $\tau=T-t$ time to maturity 

Define

$$
d_{1}:=\frac{\log\frac{S_{t}}{K}+(r+\frac{1}{2}\sigma^{2})\tau}{\sigma\sqrt{\tau}}
$$
$$
d_{2}:=\frac{\log\frac{S_{t}}{K}+(r-\frac{1}{2}\sigma^{2})\tau}{\sigma\sqrt{\tau}}
$$

Price of call option 
$$
p^{BS}(S_{t},K,\sigma,\tau,r)=-S_{t}\mathcal{N}(-d_{1})+Ke^{-r\tau}\mathcal{N}(-d_{2})
$$

