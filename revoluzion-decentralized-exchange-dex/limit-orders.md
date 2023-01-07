# Limit Orders

## <mark style="color:yellow;">Revoluzion Limit Orders Introduction</mark>

A limit order is an order to buy or sell a cryptocurrency at a specific price or better. On a decentralized exchange (DEX), limit orders allow users to set a specific price at which they want to buy or sell a token. The trade will only be executed if the market price of the token reaches the specified price or better.

For example, if you want to sell your RVZ tokens but only want to sell them at a price of $1 or higher, you can place a sell limit order at $1. If the market price of RVZ reaches $1 or higher, your sell order will be executed. If the market price does not reach $1, your sell order will remain open until it is either cancelled or the market price reaches the specified price.

Limit orders can be useful for traders who want to buy or sell tokens at a specific price or better, as they allow users to set their own price rather than accepting the current market price. However, it is important to note that limit orders may not be filled immediately, as they are only executed when the market price reaches the specified price.

### <mark style="color:yellow;">Revoluzion Limit Orders Safe To Use?</mark>

Revoluzion's limit orders are integrated with Gelato's backend infrastructure to facilitate automation. This integration allows Gelato's backend to directly manage all automation processes. Gelato's backend is a highly reliable and secure platform, trusted by many prominent projects including Pancakeswap.

### <mark style="color:yellow;">How Do I Use Revoluzion Limit Orders?</mark>

Tutorials and guides will be available in the near future.

### <mark style="color:yellow;">Revoluzion Limit Orders FAQ</mark>

<details>

<summary><mark style="color:yellow;">Why was my order not executed?</mark></summary>

Limit orders are designed to be executed at a specific price point, however, due to fluctuations in the Binance network's gas fees, the actual price at which the limit order is executed may differ slightly from the price specified in the order. This difference is usually minimal, but it can be more significant for small orders (those valued at less than approximately $1000). In these cases, the execution price may be slightly higher in order to cover the cost of gas fees. It is important to keep this potential variation in mind when placing limit orders.

Therefore your order may not be executed because:

* It wasn’t possible to fill the whole order at the desired price and amount due to price impact.
* One of the tokens in the limit order has fee / tax on transfer

</details>

<details>

<summary><mark style="color:yellow;">Can I submit a limit order for tokens with tax on transfer?</mark></summary>

It is generally not recommended to use tokens with a transfer / tax fee in conjunction with limit orders. Doing so carries an element of risk, as the transfer fee could potentially impact the execution of the limit order. It is important to carefully consider the potential consequences before proceeding with this combination of tools.

</details>

<details>

<summary><mark style="color:yellow;">Do I set slippage while using limit orders?</mark></summary>

Slippage is not a factor when using limit orders with Revoluzion limit orders. When placing a limit order, you specify both the input amount (e.g. 100,000 RVZ) and the desired output amount (e.g. 2 BNB). Revoluzion limit order ensures that you will receive no less than the specified output amount (2 BNB) for your input amount (100,000 RVZ) if the price for the pair reaches the desired level.&#x20;

It is important to note that using tokens with a transfer tax / fee in conjunction with limit orders may carry an element of risk and is generally not recommended.

</details>

<details>

<summary><mark style="color:yellow;">Why does the real execution price show 'never executes'?</mark></summary>

The "never executes" message in the real execution price field indicates that the transaction cannot be completed because there are not enough tokens to cover the gas fee. This typically occurs when attempting to swap a very small amount of tokens. To resolve this issue, you will need to increase the amount of tokens in the "input" field. This will ensure that there are sufficient funds to cover the gas fee, allowing the transaction to be completed.

</details>

<details>

<summary><mark style="color:yellow;">Why is there an expiration date for my limit orders?</mark></summary>

Limit orders on Revoluzion have an expiration date, which is displayed to users before they commit to placing the order. The expiration date serves as a security measure to prevent users from leaving their limit orders open for an extended period of time, which could potentially result in higher gas fees and prevent the order from being executed.&#x20;

While it is not possible to execute a limit order past its expiration date, users funds are safe and can still choose to cancel the order at any time.

</details>

<details>

<summary><mark style="color:yellow;">Why can’t I create limit orders below the market price?</mark></summary>

Unfortunately, stop limit orders are not currently available on Revoluzion, but they are planned to be implemented at a later date.

Limit orders and stop limit orders are two different types of orders that serve different purposes. Limit orders allow you to specify a price at which you would like to buy or sell an asset. These orders will only be executed if the market price reaches the specified level.

Stop limit orders, on the other hand, are used to limit potential losses on a trade. These orders involve setting a trigger price and a limit price. When the market price reaches the trigger price, a limit order is automatically placed at the limit price. This allows you to sell an asset at a predetermined price in order to minimize losses.

In summary, limit orders are used to set a target price for a trade, while stop limit orders are used to protect against potential losses.

</details>

<details>

<summary><mark style="color:yellow;">Why is my order not appearing in the order table or stuck in 'pending' status?</mark></summary>

The information displayed in the order history table is sourced from the subgraph, which may occasionally experience delays in updating. These delays are usually minimal, with a maximum duration of a few minutes.&#x20;

If you are experiencing an issue with the order history table, you can check the status of the subgraph by looking at the indicator in the bottom right corner of the table. This will provide information about the current status of the subgraph and whether it may be affecting the display of the order history.

</details>

<details>

<summary><mark style="color:yellow;">Where can I ask additional questions?</mark></summary>

If you have any questions or concerns, please feel free to reach out to us in our Revoluzion Telegram chat group or Discord server. Our team is always happy to help.

</details>
