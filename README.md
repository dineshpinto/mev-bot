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
extracted MEV currently exceeds $600M, with around $20M
extracted in the last 30 days alone. A majority of this (over 99%)
comes from arbitrage, and over 97% coming from just three
ETH protocols (uniswap v2, uniswap v3 and balancer v1). Further,
looking at the growth in MEV over time and complexity of solving the
issue (solutions include random tx ordering etc.), it's clear that MEV
is here to stay.

## Is it only on PoW ETH?

No. Effectively, any party capable of validating transactions
on a PoW/PoS chain is can extract MEV (e.g. validators on PoS ETH,
rollup providers on Optimism etc.).

## Important references

### Theory
+ [Front running dynamics - Bernhardt & Taub](https://doi.org/10.1016/j.jet.2007.05.005)
+ [Incentives in P2P networks - Roughgarden](http://theory.stanford.edu/~tim/f16/l/l5.pdf)
+ [Mechanism Design Basics - Roughgarden](https://timroughgarden.org/f13/l/l2.pdf)
+ [SoK: Transparent Dishonesty: front-running attacks on Blockchain - Eskandari et. al.](https://arxiv.org/abs/1902.05164)
+ [Winner determination in combinatorial auction generalizations - Sandholm et. al.](https://www.cs.cmu.edu/~sandholm/generalizations.aamas02.pdf)
+ [Quantifying Blockchain Extractable Value: How dark is the forest?](https://arxiv.org/pdf/2101.05511v2.pdf)
+ [A2MM: Mitigating Frontrunning, Transaction Reordering and Consensus Instability in Decentralized Exchanges - Zhou et. al.](https://arxiv.org/pdf/2106.07371.pdf)
+ [Maximizing Extractable Value from Automated Market Makers - Bartoletti et. al.](https://arxiv.org/pdf/2106.01870.pdf)
+ [Cyclic Arbitrage in Decentralized Exchanges - Wang et. al.](https://arxiv.org/pdf/2105.02784.pdf)
+ [Frontrunner Jones and the Raiders of the Dark Forest: An Empirical Study of Frontrunning on the Ethereum Blockchain - Torres and Camino](https://arxiv.org/pdf/2102.03347.pdf)

### OG work
+ [Flash Boys 2.0 - Daian et. al.](https://arxiv.org/abs/1904.05234)
+ [Anatomy of an MEV Strategy: Synthetix - Miller](https://bertcmiller.com/2021/09/05/mev-synthetix.html)
+ [Flash Boys: A Wall Street Revolt - Lewis](https://ia801606.us.archive.org/13/items/B-001-000-192/B-001-000-192.pdf)
+ [The cost of decentralization in 0x and EtherDelta - Bentov et. al.](https://hackingdistributed.com/2017/08/13/cost-of-decent/)
+ [0x: An open protocol for decentralized exchange on the Ethereum blockchain - Warren and Bandeali](https://github.com/0xProject/whitepaper)
+ [Ethereum: A secure decentralised generalised transaction ledger - Gavin Wood](https://gavwood.com/paper.pdf)

### Paradigm Research
+ [MEV and Me - Noyles](https://research.paradigm.xyz/MEV) 
+ [Ethereum Blockspace - Who Gets What and Why - Konstantopoulos and Zhang](https://research.paradigm.xyz/ethereum-blockspace)
+ [Ethereum Reorgs After The Merge - Konstantopoulos and Buterin](https://www.paradigm.xyz/2021/07/ethereum-reorgs-after-the-merge)
+ [Ethereum is a Dark Forest - Robinson and Konstantopoulos](https://www.paradigm.xyz/2020/08/ethereum-is-a-dark-forest)

### Basics
+ [MEV — A Deep Dive](https://medium.com/@liamzhang/mev-a-deep-dive-part-1-3f389ef16d32)

### GitHub repos and Twitter threads
+ [bertmiller/sMEV](https://github.com/bertmiller/sMEV)
+ [0xMisaka/MEV-data-solana](https://github.com/0xMisaka/MEV-data-solana/blob/main/MEV-ARB-90-0322.ipynb) + [@0xMisaka](https://twitter.com/0xmisaka/status/1506318206281170964?lang=en)
+ [@bertcmiller](https://twitter.com/bertcmiller/status/1402665992422047747)
+ [@hasufl](https://twitter.com/hasufl/status/1439938607142277121)
+ [@onewayfunction](https://twitter.com/onewayfunction)
+ [@SiegeRhino2](https://twitter.com/SiegeRhino2)

# Why are we here?

We will focus primarily on _atomic arbitrage_, basically creating a
series of on-chain interactions that sequentially execute and
check if some conditions are met. If the conditions are not met,
the entire transaction set is reverted, kinda like an undo button.

The atomic arbitrage space is incredibly competitive, and the probability of
making a profitable trade on the larger DeFi protocols is practically 0.
However, the goal here is to understand how MEV works, implement some basic strats,
and eventually apply that to _long-tail_ MEV strats that have a higher EV.
For an example of a long tail strat
see [this Chainsight Twitter thread](https://twitter.com/ChainsightLabs/status/1460824051010744327?ref_src=twsrc%5Etfw%7Ctwcamp%5Etweetembed%7Ctwterm%5E1460824051010744327%7Ctwgr%5E%7Ctwcon%5Es1_&ref_url=https%3A%2F%2Fcalblockchain.mirror.xyz%2Fc56CHOu-Wow_50qPp2Wlg0rhUvdz1HLbGSUWlB_KX9o).
