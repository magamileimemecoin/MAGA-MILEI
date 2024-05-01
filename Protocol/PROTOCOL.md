# MAGA MILEI Protocol: Decentralized Finance Features and Mechanisms

**Overview**

The MAGA MILEI Protocol is a decentralized finance (DeFi) token deployed on the Binance Smart Chain (BSC), featuring two innovative components: 
static rewards for users and an LP acquisition mechanism. Here's how they operate:

Each MAGA MILEI transaction incurs dual 5% fees, totaling 10% of the transaction amount. The first fee is redistributed to all existing holders via a 
rebasing mechanism, while the remaining 5% accrues internally until sufficient capital is amassed for an LP acquisition. Once this threshold is met, 
the accumulated tokens are split, with half converted to BNB and the remainder supplied to the PancakeSwap contract for liquidity.

**LP Acquisition**

Any standard token transaction can indirectly trigger the LP acquisition mechanism, as transfers evaluate specific conditions. These conditions include 
whether the sender differs from the LP pair and if the accumulation threshold has been surpassed. If met, the swapAndLiquify function is executed with 
the current contract's MAGA MILEI balance, dividing it into two halves while accounting for any truncation. The first half is swapped for BNB via 
the PancakeSwap Router, momentarily reducing the MAGA MILEI token price. Subsequently, the resulting BNB balance and remaining MAGA MILEI tokens 
are supplied to the MAGA MILEI-BNB liquidity pool via the Router. The current recipient of LP units is specified as the owner of the MAGA MILEI contract.

**Static Reward (Reflection)**

MAGA MILEI token balances are computed in two ways. The first method is familiar to most users, involving a fixed number of units associated with a user's 
address. The second method, relevant to static rewards, represents a user's balance as a proportion of the total token supply, akin to dynamic rebasing 
mechanisms like Ampleforth. Upon each taxed transaction, 5% meant for redistribution to token holders is deducted from the total "proportion" supply, 
increasing a user's percentage of the total supply.However, not all users are integrated into this system; thus, the 5% fee is rewarded to a subset of the 
total MAGA MILEI token holders. The contract owner holds the authority to introduce or exclude users from the dynamic balance system as desired.
