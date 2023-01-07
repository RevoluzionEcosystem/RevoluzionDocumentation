---
description: Revoluzion Rewards Documentation
---

# Revoluzion Dual Rewards

## <mark style="color:yellow;">Dual Rewards System</mark>

At Revoluzion, we believe that it's important for investors to be rewarded for their commitment to our project. Rather than just waiting for the price of our token to potentially increase, we offer various ways for holders to earn rewards for their loyalty. These include dividends, diamond hand rewards, and other forms of compensation. By actively rewarding our token holders, we hope to create a strong sense of community and encourage long-term engagement with our platform.

Revoluzion is a pioneering project that has been the first ever to introduced a dual rewards system that utilizes smart contract technology to automatically distribute rewards to token holders. Our Diamond Hand program is the first of its kind, offering holders the opportunity to earn rewards for maintaining a minimum holding of 1 million RVZ tokens over a specified timeframe.&#x20;

This innovative system ensures that all eligible holders receive an equal share of the rewards, regardless of the size of their holdings. By automating the distribution process, we aim to create a transparent and fair rewards system that encourages long-term engagement with our project. We are proud to be leading the way in this area and hope to set a standard for other projects to follow.

{% hint style="success" %}
Did you know that Revoluzion uses a portion of the funding generated from various sources to fund our reward system? In addition to the buy and sell tax, a percentage of the funding from services provided by Revoluzion is also distributed to the Dividend and Diamond Hand pools for our RVZ token holders.&#x20;

This means that by holding RVZ tokens, you can benefit not only from the buy and sell tax, but also from a portion of the funding generated from the services we provide. This helps to create a diverse and sustainable reward system that benefits our token holders and encourages long-term engagement with our project.
{% endhint %}

### <mark style="color:yellow;">Dividend Rewards</mark>

Revoluzion offer a rewards program that allows token holders to earn automatic BUSD BEP-20 rewards directly deposited to their wallets by holding their RVZ tokens. Here's how it works:

* 4% of every buy and sell transaction on our platform is redistributed to all token holders, directly into their wallets.
* The delivery of auto-claim rewards will depend on the volume of buy and sell transactions occurring on the platform, including the number of holders eligible for rewards.
* Investors can also manually claim their rewards at any time through our dApp rewards tab, although there may be gas fee charges associated with this option.

By offering this rewards program, we hope to encourage long-term engagement with our project and create a strong sense of community among our token holders.

{% code overflow="wrap" lineNumbers="true" %}
```solidity
function shouldDistribute(address shareholder) internal view returns (bool) {
        return shareholderClaims[shareholder] + minPeriod < block.timestamp && getUnpaidEarnings(shareholder) > minDistribution;
    }

    /**
     * @dev Distribute dividend to the shareholders and update dividend information.
     */
    function distributeDividend(address shareholder) internal {
        if (shares[shareholder].amount == 0) {
            return;
        }

        uint256 amount = getUnpaidEarnings(shareholder);
        if (amount > 0) {
            totalDistributed = totalDistributed.add(amount);
            rewardToken.transfer(shareholder, amount);
            shareholderClaims[shareholder] = block.timestamp;
            shares[shareholder].totalRealised = shares[shareholder].totalRealised.add(amount);
            shares[shareholder].totalExcluded = getCumulativeDividends(shares[shareholder].amount);
        }
    }

    /**
     * @dev Get the cumulative dividend for the given share.
     */
    function getCumulativeDividends(uint256 share) internal view returns (uint256) {
        return share.mul(dividendsPerShare).div(dividendsPerShareAccuracyFactor);
    }
    
    /**
     * @dev Get unpaid dividend that needed to be distributed for the given address.
     */
    function getUnpaidEarnings(address shareholder) public view returns (uint256) {
        if (shares[shareholder].amount == 0) {
            return 0;
        }

        uint256 shareholderTotalDividends = getCumulativeDividends(shares[shareholder].amount);
        uint256 shareholderTotalExcluded = shares[shareholder].totalExcluded;

        if (shareholderTotalDividends <= shareholderTotalExcluded) {
            return 0;
        }

        return shareholderTotalDividends.sub(shareholderTotalExcluded);
    }

    /**
     * @dev Add the address to the array of shareholders.
     */
    function addShareholder(address shareholder) internal {
        shareholderIndexes[shareholder] = shareholders.length;
        shareholders.push(shareholder);
    }

    /**
     * @dev Remove the address from the array of shareholders.
     */
    function removeShareholder(address shareholder) internal {
        shareholders[shareholderIndexes[shareholder]] = shareholders[shareholders.length - 1];
        shareholderIndexes[shareholders[shareholders.length - 1]] = shareholderIndexes[shareholder];
        shareholders.pop();
    }

    function claimDividend() external {
        distributeDividend(_msgSender());
    }

}
```
{% endcode %}

{% hint style="info" %}
Automated distribution of rewards occurs during every swap, the swap threshold are also dependant on volume and swap threshold reached.&#x20;

Flow chart is sell happen <mark style="color:green;">**>>**</mark> <mark style="color:green;"></mark><mark style="color:green;"></mark> tokens store in smart contract <mark style="color:green;">**>>**</mark> <mark style="color:green;"></mark><mark style="color:green;"></mark> threshold met for swap <mark style="color:green;">**>>**</mark> <mark style="color:green;"></mark><mark style="color:green;"></mark> distribution sent to dividend / dh contract ** **<mark style="color:green;">**>>**</mark> <mark style="color:green;"></mark><mark style="color:green;"></mark> calculations dividend per share factor per token ** **<mark style="color:green;">**>>**</mark> <mark style="color:green;"></mark><mark style="color:green;"></mark> distribution of few holders per sell txn depending on gas fee settings.
{% endhint %}

{% code overflow="wrap" lineNumbers="true" %}
```solidity
// Dividends are paid out automatically when threshold are met
// period of 1 hour
// minimum 1 usd

{
      dividendsPerShareAccuracyFactor = 10**36;
        minPeriod = 1 hours;
        minDistribution = 1 * (10**rewardToken.decimals());
    }
```
{% endcode %}

Every time there is a sell, the system will automatically distribute rewards to a group of one to five holders. The amount of the rewards is based on the volume and a threshold of 1 USD per 60 minutes. However, the process of distributing the rewards is more complex and involves a cycle that may take some time to reach your specific wallet address. The distribution of rewards is also subject to a gas limit rate.

{% hint style="success" %}
As a token holder of Revoluzion, you have the opportunity to claim your rewards at any time that you wish. Simply visit the following link to claim your rewards: [https://revoluzion.app/rewards](https://revoluzion.app/rewards)
{% endhint %}

### <mark style="color:yellow;">Diamond Hand Rewards</mark>

Revoluzion have also implemented a system called "Diamond Hand" that rewards token holders for their loyalty who maintains an amount above of 1 million RVZ tokens. Here's how it works:

* 2% of every buy and sell transaction on our platform is deposited into the Diamond Hand wallet.
* Every week, all holders with more than 1 million total tokens will receive a share of the Diamond Hand rewards.
* The rewards are distributed equally among all eligible holders, regardless of the size of their holdings.
* Holders are still eligible for the rewards even if they sell some of their tokens as long as they maintain a holding of at least 1 million RVZ tokens throughout the entire period.
* Team, marketing, and ecosystem wallets will not be eligible for Diamond Hand rewards. All rewards are reserved for token holders only.

{% code overflow="wrap" lineNumbers="true" %}
```solidity
    function process(uint256 gas) external override onlyTokenAndOwner {
        uint256 holderCount = holders.length;

        if (holderCount == 0) {
            return;
        }

        uint256 gasUsed = 0;
        uint256 gasLeft = gasleft();
        uint256 iterations = 0;

        while (gasUsed < gas && iterations < holderCount) {
            if (currentIndex >= holderCount) {
                currentIndex = 0;
            }

            if (IERC20Extended(_token).balanceOf(holders[currentIndex]) >= minTokenRequired && shouldDistribute(holders[currentIndex])) {
                distributeDiamond(holders[currentIndex]);
            } else if (IERC20Extended(_token).balanceOf(holders[currentIndex]) < minTokenRequired) {
                diamonds[holders[currentIndex]].eligible = false;
                removeHolder(holders[currentIndex]);

                uint256 current = rewardToken.balanceOf(address(this));
                diamondsPerHolder = diamondsPerHolderAccuracyFactor.mul(current).div(holders.length);
            }

            if (block.timestamp > diamondCycleEnd) {
                
                diamondCycleStart = diamondCycleEnd;
                diamondCycleEnd = diamondCycleEnd + diamondCycle;
                previousCycleEnd = diamondCycleStart - 1;

                uint256 current = rewardToken.balanceOf(address(this));
                prevDiamondsPerHolder = diamondsPerHolder;
                diamondsPerHolder = diamondsPerHolderAccuracyFactor.mul(current).div(holders.length);

            }

            gasUsed = gasUsed.add(gasLeft.sub(gasleft()));
            gasLeft = gasleft();
            currentIndex++;
            iterations++;
        }
    }
    
    function shouldDistribute(address holder) internal view returns (bool) {
        return 
            holderClaims[holder] < (previousCycleEnd + 1) && 
            diamonds[holder].eligible == true && 
            diamonds[holder].eligibleTime + diamondCycle <= previousCycleEnd;
    }
```
{% endcode %}

Diamond hand rewards are paid out on a periodic basis, with a frequency of one payout every 168 hours, or approximately every 7 days. The following code illustrates this behavior:

{% code overflow="wrap" lineNumbers="true" %}
```solidity
// Rewards are paid out of every 7 days period
// Rewards are paid out at equal rate to all holders of any amount
// Holders are free to buy / sell RVZ as long they maintain 1 million RVZ constant

{
diamondsPerHolderAccuracyFactor = 10**36;
        diamondCycle = 168 hours;
        diamondCycleStart = block.timestamp;
        diamondCycleEnd = diamondCycleStart + diamondCycle;
        previousCycleEnd = block.timestamp - 1;
        minTokenRequired = 1000000000000000000;
    }
```
{% endcode %}

By offering this rewards program, we hope to incentivize long-term engagement with our project and create a strong sense of community among our token holders.
