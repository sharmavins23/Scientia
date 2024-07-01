In [[Financial Economics|finance]], an option is a contract which conveys to its owner, the *holder*, the right, **but not the obligation,** to buy or sell a specific quantity of an [[Shares|underlying asset]] at a specified strike price on a specified date. Options are usually either European (as described previously), or American-style, where the buying/selling may be excised at a prior date.

Options can either be placed as 'call' or 'put' options. Options that convey to the holder the right to buy stock at a specified price is a call, and one that conveys the right to sell at a specified price is a put (though, investors do not need to own the underlying shares to buy or sell a put).

Traders tend to define options as "in the money" (ITM) or "out of the money" (OTM) by the strike price's position relative to the market value of the underlying stock. ITM options have strike prices that have been surpassed by the current stock price, whereas OTM options have strike prices that the underlying security has yet to reach. As such, OTM options have no intrinsic value. ITM options can also be exercised immediately. Finally, ATM is at the same price as current market value.

## Premiums

As options are effectively 'bets' on the directional movement of a stock, an option charges a premium. This premium is directly equivalent to the amount of risk on the option. For instance, suppose a person buys a call option on $SPY at $400 for 100 shares (with a premium of $100 per share). A call bets that $SPY will go up, so in the event that $SPY goes down to $0, rather than losing $40,000, the buyer is only entitled to losing the initial $10,000 investment.

Generally, premiums are priced via the [[Black-Scholes Model]].

## Leverage

Premiums fundamentally allow investors to trade stocks that they do not own. As such, their gains and losses can theoretically be amplified. In practice, a call option must be exercised to gain value from it even when ITM, but trading platforms (such as Robinhood) will buy option contracts close to expiry, which enables investors to net profits without exercising buying rights.

This leverage can be calculated simplfy from the option delta $\Delta$, the option's price $P_o$, and the total share price $P_s$:

$$
L=\frac{\Delta P_s}{P_o}
$$

For example, a long-term call of $SPY with a strike price of $K=\$415$ has a marked option price of $P_o=\$41.82$ and a $\Delta=0.5629$. Performing the calculation:

$$
\begin{align}
L &= \frac{0.5629 \times \$415}{\$41.82}\\
&= 5.586
\end{align}
$$

The buyer is effectively able to bet via 5.6 times his money's worth. As such, buying calls for $10,000 would return gains (or, and more likely, losses) equivalent to owning $55,000 worth of shares.

## Insurance

Call options can be used to increase leverage, and put options can be used as insurance to hedge against a stock value going down. For example, suppose an investor buys a stock at $15 per share. The investor then buys a put with a premium of $5 per share, where they can sell the stock they bought (at $15 per share) for $10 per share.

Suppose the stock increases to $20 per share. 