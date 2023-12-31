## Fees and Rewards


## Fees Overview


There are a few different types of fees on Balancer, each one collected in order to support a healthy ecosystem. For example, Liquidity Providers collect swap fees from users who trade with pools; this acts as an incentive for them to continue providing liquidity, which helps facilitate trades.        

## Swap Fees
When traders use a pool to trade, they pay swap fees. For pools that inherit from BasePool, these fees can be customized with a minimum value of 0.0001% and a maximum value of 10%. 

The fees go to Liquidity Providers in exchange for them putting their tokens in the pool to facilitate trades. Trade fees are collected at the time of a swap, and it goes directly into the pool, growing the pool's balance

## Protocol Fees 
Protocol Fees are a percentage of swap fees collected by pools. These go to the DAO Treasury to be used or held as the DAO sees fit. At deployment, Protocol Fees for swaps were set to 0%. These fees were activated by a governance vote and were later raised to 50% by a subsequent proposal. For the most up-to-date protocol fee data, please call `getSwapFeePercentage()` on the ProtocolFeesCollector contract.

For example, if a pool has a 1% swap fee, and there was a 10% protocol swap fee, 0.9% of each trade would be collected for the LPs, and 0.1% would be collected to the protocol fee collector contract.

## Static and Dynamic Fees
At the time of pool creation, the pool creator defines the fee and the owner. If the owner is set to an uncontrolled address (typically the zero address) then the swap fee is static. If the owner sets it to a controlled address, that address can set the fee at will, therefore making the swap fee dynamic.

## Flash Loan Fees
Flash Loan fees are a type of Protocol Fee on Balancer. The fees collected as interest on flash loans go to the DAO Treasury.

    


---
## Evaluation





##### Where are the swap fee directed?  
     
- [ ]  It goes back to the users to incentivize them
- [x]  It goes directly into the pool, growing the pool's balance
- [ ]  It go to the protocol rewards
- [ ]  It go to the veBAL Holders

    


---
## Rewards Overview

## Rewards for Liquidity Providers
Swap fees go to Liquidity Providers in exchange for them putting their tokens in the pool to facilitate trades. Trade fees are collected at the time of a swap, and it goes directly into the pool, growing the pool's balance

Along with the Swap fees, eligible pools also get Liquidity Mining rewards based on the new Gauge System
The amount received by each LP will depend on:
1. How much the pool they are providing liquidity to receives
2. What share of the pool’s liquidity they have

They can also get their rewards boosted by securing veBAL

## Rewards for veBAL Holders
**veBAL** - After locking the 80/20 BAL/ETH BPT, the user have a non-zero balance of veBAL and will be able to help govern Balancer protocol, also benefiting from other rewards.

* 75% of protocol revenues collected by the protocol fee collector gets distributed to veBAL holders. The other 25% of the fees will be kept by the DAO treasury as a reserve.

* Also 10% of the BAL minted every week i.e. 14,500 BAL goes to the veBAL holders.  It helps veBAL holders avoid dilution and compensates for the impermanent loss risk of LPing 

* veBAL holders can also claim Bribes from https://hiddenhand.finance/balancer

## Rewards for Liquidity Providers with veBAL
The veBAL system implements a multiplier based upon the time locking mechanism. Locking the same amount of BPT for a longer period will yield a higher incentive multiplier for a user.

The maximum boost possible for liquidity mining incentives is 2.5x. For tooling, calculate your boost [here](https://balancer.tools/boost).


    


---
## Evaluation





##### Which one of these is not a parameter while distributing the Liquidity Mining rewards to Liquidity Providers?  
     
- [ ]  How much the pool they are providing liquidity to receives
- [ ]  What share of the pool’s liquidity they have
- [ ]  How much are they boosted by securing veBAL
- [x]  How much BAL do they hold

    


---
## Gauge System

## Gauge System Overview
Since transitioning to the veModel, BAL emissions get distributed through the gauge system. Gauges allow LPs (liquidity providers) to stake their BPT to claim BAL from liquidity mining. The amount that each LP receives depends on the following:
1. The allocation of BAL that the Pool receives
2. The share of the LP in the Pool
3. The boost applied to LP share based on the amount of veBAL that they hold

## BAL Emissions
Currently the inflation is 145,000 BAL per week. Every 4 years the inflation will be halved, with gradual steps every year starting one year after the launch of the new tokenomics system. This would mean a final BAL supply of about 94,000,000 BAL.

In the Guage System, all liquidity mining BAL minted will be distributed through the gauge system. Gauges are contracts that allow LPs (liquidity providers) to stake their BPT (Balancer Pool Token) and periodically claim BAL from liquidity mining.

## Gauge Types
There are five gauge types: 
1. **Liquidity Mining Committee** - This is an allowance for the Liquidity Mining committee to grant LM to strategic partnerships for Balancer protocol with the expectation that long term these partners will accrue veBAL to ensure they get LM through their own gauge. The LM committee should not accumulate BAL, that is, it commits to sending any unused BAL for any given week to the DAO treasury (not later than 7 days from receiving it). This pool gets  10% of LM Rewards i.e. 14,500 BAL
2. **veBAL** - It is meant to keep locking 80/20 BPT attractive as it helps veBAL holders avoid dilution and compensates for the impermanent loss risk of LPing. This pool gets  10% of LM Rewards i.e. 14,500 BAL
3. **Ethereum Mainnet Pools** - LM that is distributed to mainnet. This pool gets  56% of LM Rewards i.e. 81,200 BAL
4. **Polygon Pools** - LM that is distributed to Polygon. This pool gets  17% of LM Rewards i.e. 24,650 BAL
5. **Arbitrum Pools** - LM that is distributed to Arbitrum. This pool gets  7% of LM Rewards i.e. 10,150 BAL

    


---
## Evaluation





##### How much BAL are minted weekly as part of the inflation schedule?  
     
- [ ]  145,00 BAL
- [x]  145,000 BAL
- [ ]  1450 BAL
- [ ]  145,0000 BAL





##### What percentage of BAL minted goes to veBAL gauge?  
     
- [ ]  20%
- [ ]  25%
- [ ]  50%
- [x]  10%

    


---
## Your Info





| Label | Type | Required |
| ----------- | ----------- | ---- |
| Name        | PublicShortInput   |  true    |


    

