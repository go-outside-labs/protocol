## the ethereum blockchain 

<br>

* **[the ethereum yellow paper](https://ethereum.github.io/yellowpaper/paper.pdf)**
* the ethereum roadmap:

<br>
<p align="center">
<img width="600"  src="https://user-images.githubusercontent.com/1130416/234419153-76ab9f89-00e8-48e7-93c4-c8d880ec2007.png">
</p>
<br>

<br>

---

### tl; drs

<br>

##### evm execution 

* in native execution, evm will load the bytecode and execute the opcodes in the bytecodes one by one from the beginning.
* each opcode can be thought as doing the following steps:
  1. read elements from stack, memory, or storage
  2. perform some computation on these elements
  3. write back results to stack, memory, or storage

<br>

##### light clients

* light clients receive the block headers, which contain a merkle root (more on this later) that can be used to query full nodes to verify if a transaction is included in a particular block.

<br>

##### scalability

* **[eip-4844 tl; dr](eip-4844.md)**
* **[possible futures of the ethereum protocol, part 1: the merge, by vub](https://vitalik.eth.limo/general/2024/10/14/futures1.html)**
* **[possible futures for the ethereum protocol, part 2: the surge, by vub](https://vitalik.eth.limo/general/2024/10/17/futures2.html)**

<br>

##### rollups

* rollups move computation (and state storage) off-chain, but keep some data per tx on-chain, using compression tricks to replace data with computation wherever possible (but scalability is still limited by the data bandwidth of the underlying blockchain).
* an onchain smart contract maintains a state root (the merkle root) of the state of the rollup.
* anyone can publish a batch (collection of txs, compressed to form the previous state root and the new state root).
* the contract checks that the previous state root in the batch matches the current state root - if not, it switches the state root to the new state root.
* for depositing and withdrawing, txs can have input or output outside the rollup state (processed within the batches).
* optimistic (fraud proof) or zk (validity proof) rollups are solutions to know that the post-state roots in the batches are correct.

<br>

<p align="center">
<img width="250" src="https://user-images.githubusercontent.com/1130416/234379326-901ed83c-4bc5-4c97-bad8-3b9d96dfb1b7.png">
<img width="250" src="https://user-images.githubusercontent.com/1130416/234935489-f65f98a0-a6ac-4b86-b40d-e4aac97733b7.png">
<img width="250" src="https://user-images.githubusercontent.com/1130416/234379163-f55493b4-7ad5-4d0d-9021-0f722cbe34a6.png">
</p>

<br>

* optimistic l2s 
  * arbitrum one
    - started rollups
    - largest TVL
  * optimism
    - rollup from optimism collective, with a rich ecosystem of l2
    - tool to create l2 part of the superchain
  * mantle
    - l2 from bitdao

* zk-rollups l2s
  - zksync era
    - the leading zk-rollup and a zkevm (zk-rollups that use ethereum virtual machine to execute transactions are called zkevms)
    - the only zkevm that supports native account abstraction in the consensus layer of the chain
* starknet
  - zk-rollups from starkware
  - not a zkevm
  - used the cairo language
  - has recently open-souced their STARK prover
* polygon zkevm
  - part of polygon 2.0, an ecosystem of zk-rollups
  - converting polygon pos into a zk-validum
  - has their prover open-sourced
* linea
  - another recent zkevm from consensys

<br>

##### proposer-builder separation

* **[notes on pbs, by barnabe.eth](https://barnabe.substack.com/p/pbs)** (thoughts on in-protocol pbs, market structure and allocation mechanism, whole vs. partial block building, block vs. slot auctions, inclusion lists, capturing true pbs value via consensus bid and protocol capture)
* **[decentralizing the builder role, by j. charbonneau](https://joncharbonneau.substack.com/p/decentralizing-the-builder-role)**

<br>

##### inclusion lists

* **[inclusion list economics](https://efdn.notion.site/Inclusion-list-economics-b0d61d0e21a74963a54448e48d9adc8a)**
* **[eip-7547 inclusion list, by m. neuder](https://ethereum-magicians.org/t/eip-7547-inclusion-lists/17474)**

<br>


---

### cool resources

<br>

* **[what are rollups, by ef](https://ethereum.org/en/developers/docs/scaling/zk-rollups/)**
* **[upgrading ethereum book, by b. edgington](https://eth2book.info/bellatrix/)**
* **[an incomplete guide to rollups, by vub](https://vitalik.ca/general/2021/01/05/rollup.html)**
* **[validity rollups on bitcoin, by j. light](https://bitcoinrollups.org/)**
* **[covenants, by bitcoin optech](https://bitcoinops.org/en/topics/covenants/)**
* **[a rollup-centric ethereum roadmap](https://ethereum-magicians.org/t/a-rollup-centric-ethereum-roadmap/4698)**
* **[resources for mev on ethereum](https://github.com/autistic-symposium/mev-toolkit/tree/main/MEV_by_chains/MEV_on_Ethereum)**
* **[ef's ethereum protocol wiki](https://epf.wiki/#/)**
* **[ethereum transaction visualizer](https://github.com/naddison36/tx2uml)**

 