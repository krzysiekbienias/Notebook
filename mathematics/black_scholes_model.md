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

```python

    @staticmethod
    def d1(strike: float,
           underlying_price: float,
           time_to_maturity: float,
           risk_free_rate: float,
           volatility: float,
           dividend: float = 0) -> float:
        """
        Description
        -----------
        This method calculates d1 ingredient that goes to Black-Scholes price.

        Parameters
        ----------
        strike
        underlying_price
        time_to_maturity
        risk_free_rate
        volatility
        dividend

        Returns
        -------

        """
        d1 = (np.log(underlying_price / strike) + (risk_free_rate
                                                   - dividend + 0.5 * volatility ** 2) * time_to_maturity) / (
                     np.sqrt(time_to_maturity) * volatility)
        return d1

    @staticmethod
    def d2(strike: float,
           underlying_price: float,
           time_to_maturity: float,
           risk_free_rate: float,
           volatility: float,
           dividend: float = 0) -> float:

        d2 = (np.log(underlying_price / strike) + (risk_free_rate
                                                   - dividend - 0.5 * volatility ** 2) * time_to_maturity) / (
                     np.sqrt(time_to_maturity) * volatility)
        return d2

```