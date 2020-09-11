
Proof of work is a concensus mechanism which allows anyone to extand the chain with additional blocks, by providing a piece of data that is both difficult to produce and easy to verify (according to certain parameters). Proof of work also serves the basis for the security and distribution of the coin.

Grin has an average block time of 60 seconds and employs Cuckoo Cycle[^1], a memory bound proof of work algorithm, or more specifically, a variation of it named *Cuckatoo* that is meant to simplify ASICs.

??? info "Cuckoo Cycle"
    The algorithm finds length-42 cycles in a bipartite graph. The current (and final) Grin PoW is Cuckatoo32+, in which a graph must have atleast 2^32^ + 2^32^ nodes. For a comprehensive introduction, read [here](../../wiki/miscellaneous/cuckoo-cycle).

    !!! quote ""
        Q: Why use a memory-hard proof of work? </br> A: The point is that chips dominated by memory have rather different characteristics from computational chips; they run much cooler, dissipating less heat per unit of area. This shifts the mining cost from mostly opex (electricity) to mostly capex (hardware cost), which delays obsolescense and allows mining in places with higher electricity costs.


### Two Algorithms

Grin has two PoW algorithms:

* Cuckatoo32+, The primary algorithm, meant to be *ASIC-friendly*. Begins at 10% and evolves to 100% over 2 years.
* Cuckaroo29, The secondary algorithm, aimed to be *ASIC-resistant*. Begins at 90% and decreases to 0% after 2 years.

During the first 2 years of Grin, the algorithms gradually balance themselves to satisfy the current ratio, starting from 90/10 and eventually becoming 0/100, such that the only proof of work remaining after those 2 years would be Cuckatoo32+. This period included scheduled hardforks every 6 months, in which Cuckaroo29 was modified in order to interrupt possible ASIC development for it.


!!! note ""
	The above simplifies a bit, since in practice Cuckatoo31+ was initially the primary PoW but was phased out completely after 18 months, for reasons we won’t discuss here. You can read about it on this [post](https://forum.grin.mw/t/grin-improvement-proposal-1-put-later-phase-outs-on-hold-and-rephrase-primary-pow-commitment/4653).


### ASICs

ASICs are special pieces of hardware especially designed to solve a specific proof of work algorithm as quickly and efficiently as possible. The common arguments against them are how they raise the barrier to entry for mining, and the centralization that may occur when a single ASIC manufacturer has complete market dominance.

These issues are mostly solved once a mature, competitive market for ASICs appears. However, as apparent with Bitcoin, this natural proccess may take time. Grin’s Cuckatoo32+ simplifies ASIC design in hope to reduce the time until they become widely distributed and accessible.

The choice of upholding some ASIC-resistance in the first 2 years was made to ensure fair initial distribution, in which no single party has an unproportional mining advantage at launch, before the market becomes populated and competitive enough.

Let’s see why *encouraging* ASIC development might be benficial[^2] in the first place:

#### Security

The security of a chain depends both on the amount of capital allocated to mine it (CAPEX), and on the costs of electricity & operation (OPEX). But, the CAPEX is only relevant if the the mining hardware's main function is to mine our specific chain, and are mostly useless otherwise. We want to avoid having the chain prone to attack by large hardware operators who own no stake in its success (no skin-in-the-game), since they can attack it and divert their hardware to other uses without incurring any loss to their capital.

Therefore, to achieve optimal security, two conditions must be met:

*  ASICs exist and perform significantly better than general-purpose hardware.
* The chain has the largest economic value for its specific ASIC. If the same proof of work is used by a bigger chain or serves another purpose, we encounter the same issue as described above.

#### Inevitability

There’s increasingly more evidence that ASICs are inevitable, as dedicated hardware will always have ways in which it can improve upon general purpose hardware. While it *is* possible to make ASIC manufacturing more difficult, over a long period it is likely to end up as a centralizing force in it self, as it makes the chain vulnerable to secret ASIC operations[^3].

[^1]: [Cuckoo Cycle](https://github.com/tromp/cuckoo)

[^2]: [ASICs and Decentralization FAQ](https://download.wpsoftware.net/bitcoin/asic-faq.pdf)

[^3]: [The State of Cryptocurrency Mining](https://blog.sia.tech/the-state-of-cryptocurrency-mining-538004a37f9b)