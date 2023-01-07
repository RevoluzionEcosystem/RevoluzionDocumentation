---
description: Revoluzion (RVZ) Token Introduction
---

# Revoluzion Token Information

## <mark style="color:yellow;">What is Revoluzion Token and why should you invest in it?</mark>&#x20;

Fairly simple, Revoluzion is a unique deflationary token with a built-in mechanism for injecting liquidity through buyback and burn. In addition to tax accumulation, a portion of the revenue from all services provided by the Revoluzion ecosystem, including the Launchpad platform, DEX swap, and utility functions, is used to buy back and burn the token.&#x20;

This helps to increase the value of the token over time and make it more attractive to investors. To learn more about the Revoluzion token and its future development plans, check out our pitch deck, which provides a complete introduction to the token and its features.

{% embed url="https://drive.google.com/file/d/16-GgR0w2RbKOmg8hkOSmYJgJsCts2eX1/view?usp=sharing" %}
**Revoluzion Pitch Deck**
{% endembed %}

### <mark style="color:yellow;">Auto BuyBack and TriggerZeus Codes</mark>

{% code overflow="wrap" lineNumbers="true" %}
```solidity
// Buyback related functions

    function setAutoBuybackSettings(bool _enabled, uint256 _cap, uint256 _amount, uint256 _period) external authorized {
        autoBuybackEnabled = _enabled;
        autoBuybackCap = _cap;
        autoBuybackAccumulator = 0;
        autoBuybackAmount = _amount;
        autoBuybackBlockPeriod = _period;
        autoBuybackBlockLast = block.number;
    }

    function setBuybackMultiplierSettings(uint256 numerator, uint256 denominator, uint256 length) external authorized {
        require(numerator / denominator <= 2 && numerator > denominator);
        buybackMultiplierNumerator = numerator;
        buybackMultiplierDenominator = denominator;
        buybackMultiplierLength = length;
    }

    function setBuyBacker(address acc, bool add) external authorized {
        buyBacker[acc] = add; 
    }

    function clearBuybackMultiplier() external authorized {
        buybackMultiplierTriggeredAt = 0;
    }
    
    function triggerAutoBuyback() internal {
        buyTokens(autoBuybackAmount, DEAD);
        autoBuybackBlockLast = block.number;
        autoBuybackAccumulator = autoBuybackAccumulator.add(autoBuybackAmount);
        if (autoBuybackAccumulator > autoBuybackCap) {
            autoBuybackEnabled = false;
        }
    }

    function triggerZeusBuyback(uint256 amount, bool triggerBuybackMultiplier) external authorized {
        buyTokens(amount, DEAD);
        if (triggerBuybackMultiplier) {
            buybackMultiplierTriggeredAt = block.timestamp;
            emit BuybackMultiplierActive(buybackMultiplierLength);
        }
    }

    function buyTokens(uint256 amount, address to) internal swapping {
        address[] memory path = new address[](2);
        path[0] = router.WETH();
        path[1] = address(this);

        router.swapExactETHForTokensSupportingFeeOnTransferTokens {
            value: amount
        } (0, path, to, block.timestamp);
    }

}
```
{% endcode %}

### <mark style="color:yellow;">Auto Add Liquidity Codes</mark>

{% code overflow="wrap" lineNumbers="true" %}
```solidity
// Liquidity related functions.

    function _initializeLiquidityBuyBack() internal {
        targetLiquidity = 25;
        targetLiquidityDenominator = 100;

        buybackMultiplierNumerator = 200;
        buybackMultiplierDenominator = 100;
        buybackMultiplierLength = 30 minutes;
    }

    function getLiquidityBacking(uint256 accuracy) public view returns (uint256) {
        return accuracy.mul(balanceOf(pair).mul(2)).div(getCirculatingSupply());
    }

    function setTargetLiquidity(uint256 _target, uint256 _denominator) external authorized {
        targetLiquidity = _target;
        targetLiquidityDenominator = _denominator;
    }
//
    
    if (amountToLiquify > 0) {
            router.addLiquidityETH{
                value: amountBNBLiquidity
            } (address(this), amountToLiquify, 0, 0, autoLiquidityReceiver, block.timestamp);
            emit AutoLiquify(amountBNBLiquidity, amountToLiquify);
        }
```
{% endcode %}
