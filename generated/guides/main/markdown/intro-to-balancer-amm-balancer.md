## Intro to Balancer AMM


## Introduction


## Balancer Overview
Fernando Martinelli, a well-known Brazilian entrepreneur and Maker Community member, founded Balancer. In 2018, he tested the exchange on Block as the first project of Balancer labs. In 2019, he and his technical colleague Nikolai Mushegian released the exchange's whitepaper. An Automated Market Maker (AMM) called Balancer enables customers to generate programmable liquidity. AMMs are decentralized exchanges where instead of the traditional order book method to trade assets smart contract acts as a partner in every trade. These contracts contain a cluster of tokens, called a liquidity pool. These liquidity pools ensure constant liquidity for buyers and sellers so they do not have to wait for orders to match.
        
Key features of Balancer DEX include
1. **Valut** - Vault is a smart contract that controls all tokens in every balancer pool. It also serves as the gateway through which most operations in the exchange (Swaps, market entries, and exits) are carried out.
2. **Balancer Pools** - Balancer pools’ smart contracts determine how traders exchange tokens. They allow customization and also allows anybody to create a pool
3. **Smart Order Router (SOR)** - SOR identifies the best price for selling and buying orders in a transaction in either one or multiple liquidity pools. It increases parallel to the expansion and diversity of the Balancer pools as it gets new options to check from.
4. **veBAL** - BAL holders/LPs should lock/stake their BAL into veBAL to get a host of benefits in the new vote-escrowed (ve) system.
5. **Onchain Gauge System** - Since transitioning to the veModel, BAL emissions get distributed through the gauge system. Gauges allow LPs (liquidity providers) to stake their BPT to claim BAL from liquidity mining.








    


---
## Evaluation





##### Who founded Balancer?  
     
- [ ]  Sam Bankman-Fried
- [x]  Fernando Martinelli
- [ ]  Vitalik Buterin
- [ ]  Satoshi Nakamoto





##### What is Balancer?  
     
- [x]  Automated Market Maker
- [ ]  Lending and Borrowing Protocol
- [ ]  Staking Protocol
- [ ]  Centralized Crypto Exchange

    


---
## The Vault

The Vault is the smart contract used by Balancer. It is the smart contract that manages and holds all the tokens in a Balancer pool. It is also the portal through which most Balancer operations occur. It also separates accounting and token management from the pool logic. This architecture unifies several pool layouts under one roof; the Vault is agnostic to pool math and can support any system that meets a few criteria. This allows smart contracts much simpler as they now play a minor part in managing funds. If you have a great idea for a new trading system, you can create a custom pool that taps into Balancer's existing liquidity. This means you don't have to build your own decentralized exchange (DEX).

Furthermore, other decentralized pools' token accounting is paired with pool logic which makes multi-hop trading quite costly since ERC-20 has to be transferred at each hop. Balancer gains an advantage here since it stores all its tokens under one contract, The Vault. This difference allows for much greater swapping efficiency. Rather than transferring tokens on each step of a multi-hop trade, it only keeps internal records of which pool is holding what, transferring tokens only at the input and output steps. This reduction in token transfers makes the entire process highly gas efficient. Additionally, The Vault keeps track of the balances for arbitrary Ethereum addresses. Users have access to the Vault where they can store Internal Balances and make trades to/from them.

    


---
## Evaluation





##### Which one of these best defines a Balancer Vault?  
     
- [ ]  It is the smart contract that records and saves all the transactions
- [ ]  It is the smart contract that manages routing of all the orders
- [x]  It is the smart contract that manages and holds all the tokens in a Balancer pool. It is also the portal through which most Balancer operations occur.
- [ ]  It is the smart contract that holds all the veBAL

    


---
## Balancer Pools

Pools are the foundation of the Balancer Protocol and smart contracts that through which traders can swap between tokens on Balancer. What makes Balancer pools unique is their limitless flexibility; other exchanges have pools with constrained parameters, but Balancer can accommodate any composition or underlying math. This flexibility opens the door for customized pricing functions in trading pools.

## Weighted Pools
Balancer has about 1500 shared liquidity pools users can join. These pools can carry up to 8 assets and can have ratios other than the conventional 50-50 split. They range in size with the largest over a $37 million market cap. These pools use weighted maths and are called Weighted Pools. Weighted pools offer users the ability to choose their level of exposure to certain assets while still providing liquidity. This makes them a great choice for investors who want to diversify their portfolios without sacrificing liquidity. The higher a token's weight in a pool, the less impermanent loss it will experience in the event of a price surge. For example, [the Oracle Weighted Pool](https://app.balancer.fi/#/pool/0x5c6ee304399dbdb9c8ef030ab642b10820db8f56000200000000000000000014) with 80/20 ratio of BAL and WETH respectively. 


## Stable Pools
Stable Pools are created especially for assets like various stablecoins that are anticipated to regularly trade at close to parity. These use Stable Math (based on StableSwap, popularized by Curve) which allows for significantly larger trades before encountering substantial price impact, vastly increasing capital efficiency for like-kind swaps. These pools encounter lower price impacts. Since the stable pools are plugged into all the other pools on balancer swapping between stablecoins is frequently used for arbitrage when one token is paired with two different stable coins in different pools. The two largest stable tokens in use are for USD stablecoins and tokens that track Bitcoin that are [staBAL3-USD](https://app.balancer.fi/#/pool/0x06df3b2bbb68adc8b0e302443692037ed9f91b42000000000000000000000063) composed of DAI/USDC/USDT and [staBAL3-BTC](https://app.balancer.fi/#/pool/0xfeadd389a5c427952d8fdb8057d6c8ba1156cc56000000000000000000000066) composed of WBTC/renBTC/sBTC.


## Liquidity Bootstrapping Pools
LBPs, or Liquidity Bootstrapping Pools, are pools that have the ability to dynamically alter token weighting. Weighted Math with time-dependent weights is used in LBPs. The pool owner determines the starting and ending weights and times. The pool owner also has the authority to suspend swaps. This allows the users to incur less impermanent loss and allows the market to find the appropriate price for the new token. Liquidity bootstrapping pools are one of the most successful ways to launch a new token. The purpose of [Gitcoin's LBP](https://fjordfoundry.com/pools/mainnet/0xC065798F227b49C150bCDC6CDc43149A12c4d757), which is made up of AKITA and WETH, is to gradually return the Akita owned by the company (as given to it by Vitalik) to the community. When executing a slow sale with ongoing pressure, using an LBP is helpful. An example of LBP is [70/30/DAI/Temple](https://app.balancer.fi/#/pool/0xf88278315a1d5ace3aaa41712f60602e069208e6000200000000000000000375) pool


## MetaStable Pools
MetaStable Pools are an extension of Stable Pools that contain tokens with known exchange rates. Stable Math is used in conjunction with this established exchange rate in MetaStable Pools. They are great with tokens highly correlated but not pegged prices. For example, DAI/cDAI have a very strong correlation, but cDAI slowly accumulates lending fees by lending DAI to the Compound protocol and appreciates relative to DAI.  For example, Balancer MetaStable pools are ideal for the wstETH-WETH pair as the stETH asset is highly correlated but not pegged 1:1 to ETH as it accrues staking returns.


## Managed Pools
Managed Pools, which employ Weighted Math, let users create pools with a maximum of 50 tokens. These pools contain time-based weight-shifting methods akin to Liquidity Bootstrapping Pools, giving a framework for fund managers. These pools are feature rich. Features include Pool Managers, active token management, etc. WSBDapp is utilizing Balancer's Managed Pools to bring decentralized finance to their users. This allows their investors to participate in pools created and operated by the WSBDapp Team using the technology and control only available on Balancer.


## Boosted Pools
Boosted Pools offer the best of both worlds to Liquidity Providers and Swappers. Swappers can access deep stablecoin liquidity with near-parity exchange rates, while Liquidity Providers can have their liquidity positions sent to external protocols, such as Aave. This is a great way for both groups to get what they need and make the most out of their situation. These variations of stable pools instead contain the pool tokens of nested linear pools, which, in the case of the Aave example, maintain the correct balances of TOKEN and aTOKEN.

    


---
## Evaluation





##### Which of these pools is not present in Balancer?  
     
- [ ]  Liquidity Bootstrapping Pools
- [ ]  MetaStable Pools
- [ ]  Managed Pools
- [x]  Centralized Pools

    


---
## veBAL

## veBAL
In April 2022, Balancer adopted the vote escrowed model (veModel). Under this model, users who lock their veBAL tokens for a longer period of time have more voting rights in the Protocol. 

Instead of pure BAL, BPT of the 80/20 BAL/ETH pool can be locked into veBAL, similar to how CRV can be locked into veCRV. This has the big advantage of keeping BAL liquid as well as setting a precedent for other teams to do the same with their 80/20 Balancer pools. Alternatives to veBAL have been considered, like vebptBAL. The simplicity of veBAL — even though what is locked is not pure BAL — has however been the preferred option.

Users who invest in the BAL/WETH 80/20 Pool are rewarded with BPT (Balancer Pool Token). veBAL lockers also receive 75% of protocol fees. In addition to 75% of protocol revenues, veBAL holders also get 10% of all BAL minted weekly.

This means that:
1. BAL holders should lock their BAL into veBAL to get a host of benefits in the new vote-escrowed (ve) system.
2. Balancer LPs should stake their LP Tokens (BPTs, Balancer Pool Tokens) to continue to receive liquidity mining incentives

The new veBAL system has the following benefits
- Long-term alignment: By locking BPT, token holders will be encouraged to support Balancer over the long-term instead of speculating short-term.
- Predictability: Fully automated BAL minting and inflation schedule locked forever.
- Protocol revenue distribution: 75% of all fees generated by the protocol are proportionally distributed to veBAL holders. In addition to 75% of protocol revenues, veBAL holders also get 10% of all BAL minted weekly.
- Plug & play compatibility with Curve’s ecosystem: it's expected that many protocols and products built on top of Curve's ve system will also launch on top of veBAL given the contracts have been kept the same.


    


---
## Evaluation





##### How can one receive veBAL?  
     
- [x]  By locking BPT of the 80/20 BAL/ETH pool
- [ ]  By locking BAL for 1 year
- [ ]  By locking ETH for 1 year
- [ ]  By locking USDC





##### What are the additional benefits that veBAL holders receive?  
     
- [ ]  veBAL holders get 10% of all fees colleted
- [x]  75% of all fees generated by the protocol are proportionally distributed to veBAL holders
- [x]  veBAL holders get 10% of all BAL minted weekly
- [ ]  veBAL holders also get 2000 USDC every week

    


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
## Your Info





| Label | Type | Required |
| ----------- | ----------- | ---- |
| Name        | PublicShortInput   |  true    |


    

