# MEV

_"Ethereum is a dark forest" - Dan Robinson_


## What is MEV?
MEV is the quantitative value that can be extracted (primarily) 
from tx re-ordering, inclusion and optimization in a block before
it gets added to the blockchain. The "dark forest" refers to the 
mempool, a place where transactions sit before being picked up by 
miners to be added into a block. The term itself is maximal 
extractable value, or sometimes (rather confusingly) miner 
extractable value.

## Is it growing?
Based on various quantitative metrics, such as presented on 
the [Flashbots site](https://explore.flashbots.net), the total 
extracted MEV currently exceeds \\$600 M, with around \\$20M 
extracted in the last 30 days alone. A majority of this (over 99%) 
comes from arbitrage, and over 97% coming from just three 
protocols (uniswap v2, uniswap v3 and balancer v1). From the 
data, it's pretty clear that MEV is growing rapidly, and 
particularly thrives in high-volatility time (see May 20, 2021).

## Is it only on PoW ETH?
No. Effectively, any party capable of validating transactions 
on a PoW/PoS chain is can extract MEV (e.g. validators on PoS ETH,
rollup providers on Optimism etc.).

## Important references
+ [Flash Boys 2.0](https://arxiv.org/abs/1904.05234)
+ [The cost of decentralization](https://hackingdistributed.com/2017/08/13/cost-of-decent/)
+ [Front running dynamics](https://doi.org/10.1016/j.jet.2007.05.005)
+ [Tim Roughgarden - Incentives in P2P networks](http://theory.stanford.edu/~tim/f16/l/l5.pdf)
+ [Misaka on Twitter: Solana MEV](https://twitter.com/0xmisaka/status/1506318206281170964?lang=en), [Corresponding GitHub repo](https://github.com/0xMisaka/MEV-data-solana/blob/main/MEV-ARB-90-0322.ipynb)

# Why are we here?

We will focus primarily on _atomic arbitrage_, basically creating a
series of on-chain interactions that sequentially execute and 
check if some conditions are met. If the conditions are not met, 
the entire transaction set is reverted, kinda like an undo button. 
This space is incredibly competitive, and the probability of 
making a profitable trade is effectively 0. However, the goal 
here is to understand how MEV work, and eventually apply that to 
_long-tail_ MEV strats that have a higher EV. For an example of a 
long tail strat see [this](https://twitter.com/ChainsightLabs/status/1460824051010744327?ref_src=twsrc%5Etfw%7Ctwcamp%5Etweetembed%7Ctwterm%5E1460824051010744327%7Ctwgr%5E%7Ctwcon%5Es1_&ref_url=https%3A%2F%2Fcalblockchain.mirror.xyz%2Fc56CHOu-Wow_50qPp2Wlg0rhUvdz1HLbGSUWlB_KX9o) Twitter thread from Chainsight.