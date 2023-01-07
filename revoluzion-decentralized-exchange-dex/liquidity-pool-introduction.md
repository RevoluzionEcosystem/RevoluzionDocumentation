# Liquidity Pool Introduction

### <mark style="color:yellow;">Revoluzion Liquidity Pool Introduction</mark>

Revoluzion decentralized exchange (DEX) is a type of cryptocurrency exchange that operates on a decentralized platform the BNB blockchain (BEP20), and allows users to buy and sell tokens directly with one another without the need for a central authority.

Revoluzion liquidity pool is a pool of assets, typically tokens, that are provided by users on a DEX. These pools, also known as liquidity pools or liquidity providers (LPs), allow users to trade tokens with one another on the DEX. When a user wants to buy or sell a token, they can do so by accessing the liquidity pool and executing the trade.

LPs earn trading fees whenever a trade is made using the liquidity they have provided. They also have the option to remove their liquidity from the pool at any time (Unless lock somewhere for a period of time), although doing so may result in impermanent loss, which is the difference in value between holding tokens in an automated market maker (AMM) versus holding them in your wallet.

{% hint style="success" %}
Revoluzion is currently planning to launch its decentralized exchange on the Binance Smart Chain (previously known as the BNB chain). In the future, the company plans to expand to the Ethereum and Polygon networks as well
{% endhint %}

In summary, Revoluzion liquidity pool is a pool of assets on a DEX that allows users to trade tokens with one another and earn trading fees as LPs.

Utilizing the new Uniswap V3 Calculation:

$$
L = \frac{\Delta y}{\Delta\sqrt{P}}L=ΔPΔy
$$

$$
L = \frac{\Delta y}{\Delta\sqrt{P}}L=ΔPΔy\sqrt{xy} = \frac{y_1 - y_0}{\sqrt{P_1} - \sqrt{P_0}}xy=P1−P0y1−y0\sqrt{xy} (\sqrt{P_1} - \sqrt{P_0}) = y_1 - y_0xy(P1−P0)=y1−y0\sqrt{xy} (\sqrt{\frac{y_1}{x_1}} - \sqrt{\frac{y_0}{x_0}}) = y_1 - y_0xy(x1y1−x0y0)=y1−y0\textrm{Since } \sqrt{x_1y_1} = \sqrt{x_0y_0} = \sqrt{xy} = L,Since x1y1=x0y0=xy=L,\sqrt{\frac{x_1y_1y_1}{x_1}} - \sqrt{\frac{x_0y_0y_0}{x_0}} = y_1 - y_0x1x1y1y1−x0x0y0y0=y1−y0\sqrt{y_1^2} - \sqrt{y_0^2} = y_1 - y_0y12−y02
=y1−y0y_1 - y_0 = y_1 - y_0y1−y0=y1−y0
$$

{% hint style="success" %}
Revoluzion has implemented the Uniswap V3 router, with additional modifications, to optimize the use of the smart contract router for the Binance Smart Chain (BSC). This custom implementation allows for improved functionality and suitability for the BSC network.
{% endhint %}

### <mark style="color:yellow;">Advance Documentation</mark>

Looking for more advanced mathematical calculations and documentation? Click the link below for more information on UniSwap V3 Calculation Documentation.

{% embed url="https://uniswapv3book.com/docs/milestone_1/calculating-liquidity/" %}
UniSwap V3 Calculation Documentation
{% endembed %}
