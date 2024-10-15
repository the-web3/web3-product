# 一.Ethereum 和其生态产品相关知识点详细介绍

以太坊（Ethereum）是一个开源的区块链平台，它不仅支持比特币那样的数字货币交易，还支持更复杂的应用程序，这些应用程序是通过智能合约来实现。

## 1,以太坊的几个重要概念

### 1.1.智能合约

智能合约（Smart Contracts）是以太坊最重要的特性之一。智能合约是一段存储在以太坊区块链上的代码，它可以自动执行协议的条款。例如，你可以创建一个智能合约来管理众筹活动，当筹款达到目标时，合约会自动将资金转给项目方。

### 1.2.以太币 (ETH)

以太坊的原生货币称为以太币（Ether，简称 ETH）。ETH 是用于支付以太坊网络上的交易费用和计算服务的代币。用户需要支付 ETH 来执行智能合约和转账。

### 1.3.以太坊虚拟机 (EVM)

以太坊虚拟机（Ethereum Virtual Machine，EVM）是以太坊的核心组件。EVM 是一个图灵完备的虚拟机，它可以执行用以太坊脚本语言（如 Solidity）编写的任意代码。EVM 使得智能合约的执行变得可能。

### 1.4.DApps (去中心化应用)

去中心化应用（Decentralized Applications，DApps）是基于以太坊区块链和智能合约构建的应用程序。与传统应用不同，DApps 没有中央服务器，数据和应用逻辑是分布式的，这使得它们更加透明和安全。

### 1.5.以太坊 2.0

以太坊 2.0 是以太坊的下一代版本，旨在提高网络的可扩展性、安全性和可持续性。以太坊 2.0 引入了股权证明（Proof of Stake, PoS）共识机制，而不是现有的工作量证明（Proof of Work, PoW）。这将大幅减少能耗并提高交易处理速度。

### 1.6.ERC 标准

ERC 标准是以太坊的技术规范，用于创建代币和其他合约。最著名的是 ERC-20 标准，它定义了一种通用的接口，使得代币可以在不同的 DApp 之间互操作。ERC-721 是另一种标准，用于创建非同质化代币（NFT），这些代币具有独特性和不可互换性。

## 2.ETH2.0 和 ETH1.0

以太坊1.0和以太坊2.0（ETH1.0和ETH2.0）是以太坊区块链平台的两个主要版本，它们在共识机制、性能、扩展性等方面有显著的差异。以下是对两者的详细比较：

### 2.1.以太坊1.0（ETH1.0）

- **共识机制：**工作量证明（Proof of Work, PoW）：ETH1.0 使用PoW共识机制，矿工通过解决复杂的数学问题来验证交易并添加区块。这一过程能耗高，效率较低。
- **性能：**吞吐量：ETH1.0每秒只能处理大约15-30笔交易，存在扩展性瓶颈，尤其在网络负载高峰期，交易确认时间和手续费会显著增加。
- **安全性：**矿池集中化：PoW机制导致矿池的集中化问题，少数大型矿池控制了大部分算力，可能带来中心化风险。
- **智能合约和DApps：**ETH1.0支持智能合约和去中心化应用（DApps），这些应用程序已经广泛应用于各种领域，如去中心化金融（DeFi）、游戏和供应链管理。

### 2.2.以太坊2.0（ETH2.0）*

- **共识机制**：权益证明（Proof of Stake, PoS）：ETH2.0 使用PoS共识机制，验证者通过质押ETH来获得验证区块的机会。PoS大幅减少能耗，提高了效率和安全性。
- **性能：**
- 分片链（Sharding）：ETH2.0引入了分片技术，通过将区块链分成多个并行链（分片），每个分片处理不同的交易，从而显著提高了网络的吞吐量。预计 ETH2.0 将能够处理数千甚至数万笔交易每秒。
- 信标链（Beacon Chain）：ETH2.0的核心链，负责协调分片和验证者活动，确保整个网络的同步和共识。
- **安全性：**去中心化和抗攻击性：PoS 机制下，恶意攻击者需要持有大量ETH，成本高昂，使得网络更安全。此外，验证者被随机选择，进一步分散风险。
- **智能合约和DApps：**ETH2.0保留了对智能合约和DApps的支持，同时通过更高的吞吐量和更低的费用，提升了用户体验和应用性能。
- **过渡过程：**合并（The Merge）：ETH2.0并不是从零开始的新区块链，而是对ETH1.0的升级。合并将ETH1.0的现有链和ETH2.0的PoS链结合，实现无缝过渡。

### 2.3.主要改进和优点

- 能耗：ETH2.0通过 PoS 机制大幅减少了能源消耗，相比 PoW 机制更环保。
- 扩展性：分片技术和信标链的引入显著提高了网络的扩展性和吞吐量。
- 去中心化：ETH2.0通过随机选择验证者和经济激励机制，增强了去中心化程度和安全性。
- 经济模型：ETH2.0引入了新的经济模型，通过质押和奖励机制，进一步激励网络参与者，提高网络的稳定性和安全性。

### 2.4.ETH2.0 中的 Epoch, Slot, Block 和 Block 状态

![img](https://thewebthree.xyz/media/editor/0_20241012101208925103.png)

- ETH2.0 按照 epocho 出块
- 每一个 epocho 有 32 slot
- 每一个 slot 可以承载 1 个块

**Slot（时隙）**

- 定义：Slot 是以太坊2.0中最基本的时间单位，每个slot都有一个指定的时间长度。在每个 slot 中，可能会有一个区块被提议并添加到链中。
- 时间长度：一个 slot 的长度为 12 秒。这意味着每 12 秒会有一个新的 slot。
- 功能：在每个 slot 中，网络中的验证者将有机会提议一个新的区块。这些提议者是通过权益证明（PoS）随机选择的。

**Epoch（纪元）**

- 定义：Epoch 是由多个连续的slot组成的更长时间段。在 Eth2.0 中，Epoch 用于管理和组织验证者的活动。
- 组成：一个 Epoch 由 32 个 slot 组成。
- 时间长度：由于一个 slot 是12秒，一个 Epoch 的总长度是 384 秒（即6.4分钟）。
- 功能：Epoch 是用来实现共识机制的一部分。在每个 Epoch 结束时，网络会进行状态和共识的检查和调整，包括对验证者的奖励和惩罚。

**Block（区块）**

- 定义：Block 是包含交易和其他相关数据的记录单元。在以太坊2.0中，每个slot可能会有一个区块被提议，但不保证每个 slot 都有区块。
- 内容：一个区块包含区块头、交易列表、状态根哈希、签名等数据。
- 创建过程：在每个 slot 开始时，网络会随机选出一个验证者来提议区块。该验证者将创建一个包含新交易和其他必要信息的区块，并广播到网络中。

**Safe（安全）**

“Safe”状态指的是一个区块已经被多数验证者接受和认可，并且它很可能会成为最终的区块，但还没有达到完全最终确定的状态。

- 条件：一个区块被认为是“safe”时，意味着它已经收到了足够多的验证者投票（attestations），通常超过了一个特定的阈值，但还没有达到最终确定的标准。
- 安全性：在“safe”状态下，区块的存在是相对安全的，不太可能被回滚或被一个不同的区块链分支所替代。
- 作用：这个状态用来提高网络对区块的信任度，即使在它还没有被完全最终确定之前。它帮助节点和用户判断哪些区块在短期内是可信的。

**Finalized（最终确定）**

“Finalized”状态指的是一个区块已经被永久地添加到区块链中，并且不可能被回滚或替代。这是区块链中最强的确认状态。

- 条件：一个区块被认为是“finalized”时，必须通过了严格的共识验证，通常需要超过2/3的验证者投票同意。具体来说，两个连续的epoch被最终确定时，意味着在这两个epoch之间的所有区块都被最终确定。
- 安全性：一旦区块达到“finalized”状态，它不可逆转，保证了区块链的最终一致性和数据的永久性。这种状态防止了分叉和双花攻击的可能性。
- 作用：最终确定的区块为用户和应用提供了最高级别的交易安全性和网络信任度。

### 2.5.以太坊钱包确认位

![img](https://thewebthree.xyz/media/editor/1_20241012101244554406.png)

## 3.以太坊常用的共识客户端

- **Prysm**：由Prysmatic Labs开发，是以太坊2.0中最流行的共识客户端之一，使用Go语言编写。Prysm客户端以稳定性和高效性能著称，支持广泛的验证器和节点。
- **Lighthouse**：由Sigma Prime开发的一个共识客户端，使用Rust语言编写。Lighthouse以其安全性和高性能著称，特别注重确保系统的可靠性。
- **Teku**：由ConsenSys开发，是一个使用Java语言编写的以太坊2.0共识客户端。Teku设计初衷是为了满足机构和企业的需求，具备很好的可扩展性和稳定性。
- **Nimbus**：由Status开发，使用Nim语言编写。Nimbus以其低资源占用和轻量级设计闻名，适合在资源受限的设备上运行，如移动设备和嵌入式系统。
- **Lodestar**：由ChainSafe开发，使用JavaScript（TypeScript）编写。Lodestar是一个较新的客户端，主要面向JavaScript开发者社区，便于开发者进行Web3集成。

# 二.以太坊交易类型

在智能合约开发中，我们需要了解不同的交易类型，这对我们的合约交易发送和交易解析等息息相关。以太坊网络中的交易类型多种多样，每种类型都有其特定的用途和特点。

## 1. 主流的几种交易类型

### 1.1.Legacy 交易

在以太坊上，Legacy交易是指在EIP-1559之前的传统交易类型。这些交易类型依赖于第一价格拍卖机制来确定交易费用。以下是对Legacy交易类型的详细介绍：

#### 1.1.1.Legacy交易的结构

Legacy交易的结构包括以下字段：

- **nonce**：发送方账户的交易序号
- **gasPrice**：每单位 gas 的价格
- **gasLimit**：交易消耗的最大 gas 量
- **to**：接收方地址
- **value**：转移的以太币数量
- **data**：交易的附加数据（可选）
- **v, r, s**：交易的签名

#### 1.1.2.交易字段详细说明

- **nonce**：每个账户有一个递增的nonce值。每次发送交易，nonce值都会增加，以确保交易的唯一性和顺序性。例如，账户发送的第一笔交易nonce为0，第二笔为1，依此类推。
- **gasPrice**：这是用户愿意为每个gas单位支付的费用。矿工根据gasPrice的高低优先打包交易。gasPrice的单位为gwei（1 ETH = 10^9 gwei）。高gasPrice通常会导致交易更快被确认。
- **gasLimit**：这是用户愿意为交易支付的最大gas量。它限制了交易执行过程中可以消耗的gas总量。设置gasLimit过低可能导致交易失败（但仍需支付已消耗的gas），而设置过高则可能浪费资金。
- **to**：接收方的以太坊地址。对于普通交易，这是一个常规的地址。对于合约创建交易，此字段为空，表示将部署一个新合约。
- **value**：表示转移的以太币数量，单位为wei（1 ETH = 10^18 wei）。用户可以在交易中指定转移的金额。
- **data**：这是一个可选字段，包含交易的附加数据。对于调用合约函数的交易，data字段包含合约调用的详细信息。对于合约创建交易，data字段包含合约的字节码。
- **v, r, s**：这些是签名字段，用于验证交易的发送者。通过这些字段，可以确认交易确实是由拥有相应私钥的账户发送的。

#### 1.2.3.Legacy交易的执行流程

- **交易创建**：用户创建交易并指定所有必要的字段，包括nonce、gasPrice、gasLimit、to、value和data。
- **交易签名**：用户使用其私钥对交易进行签名，生成v、r、s字段。
- **交易广播**：签名后的交易被广播到以太坊网络。
- **交易验证**：矿工节点接收交易并进行验证，包括检查nonce、签名和账户余额等。
- **交易打包**：矿工将交易打包到区块中，优先打包gasPrice较高的交易。
- **交易执行**：区块被挖出后，交易在以太坊虚拟机（EVM）中执行，根据交易类型（转账或合约调用）改变账户状态。
- **交易确认**：交易被多个区块确认后，交易被视为最终确定。

#### 1.1.4.Legacy交易的优势与劣势

**优势**

- **简单易理解**：交易费用机制简单明了，用户通过指定gasPrice来确定交易费用。
- **灵活性**：用户可以根据需要灵活调整gasPrice以提高交易确认速度。

**劣势**

- **费用波动大**：在网络拥堵时，交易费用可能会迅速飙升，导致用户难以预测和控制费用。
- **用户体验差**：用户需要手动调整gasPrice以确保交易被及时确认，增加了使用的复杂性。
- **矿工激励不稳定**：矿工可能会优先选择高gasPrice的交易，导致低费用交易长时间等待确认。

### 1.2.EIP1559 交易

EIP-1559 是以太坊改进提案中的一个重要提案，它对以太坊的交易费用机制进行了重大改进，旨在解决交易费用的不确定性和网络拥堵问题。以下是对 EIP-1559 交易的详细介绍：

#### 1.2.1.EIP-1559 的背景

在 EIP-1559 之前，以太坊的交易费用是通过“第一价格拍卖”机制确定的，即用户在交易中指定愿意支付的 gas 价格，矿工优先打包出价最高的交易。这种机制导致以下问题：

- **费用波动**：当网络拥堵时，交易费用可能会迅速飙升。
- **用户体验差**：用户很难确定合适的 gas 价格，经常要么支付过高的费用，要么交易迟迟未被确认。

#### 1.2.2.EIP-1559 的改进

EIP-1559 引入了一种新的费用结构，包括基本费用（base fee）、小费（tip）和 gas 限额（gas limit），以改善上述问题。

**基本费用**：基本费用是根据网络需求动态调整的最低费用。每个区块都会设定一个基本费用，这个费用会根据网络的拥堵情况自动调整：

- **机制**：基本费用在区块容量达到目标值时增加，在区块容量低于目标值时减少。
- **目的**：使交易费用更加可预测，减少用户手动调整 gas 价格的需求。

**小费：**用户可以选择支付额外的小费（priority fee）给矿工，以激励矿工优先处理他们的交易：

- **功能**：提高交易被打包的优先级。
- **灵活性**：用户可以根据需要设置小费的高低。

**最大费用：**用户在交易中指定愿意支付的最大费用（max fee），包括基本费用和小费：

- **保障**：确保用户不会支付超过预期的费用。
- **计算**：实际支付的费用为基本费用加上小费，剩余部分退还给用户。

#### 1.2.3.EIP-1559 交易的结构

- **nonce**：发送方账户的交易序号。
- **maxFeePerGas**：用户愿意支付的每单位 gas 的最大费用。
- **maxPriorityFeePerGas**：用户愿意支付的每单位 gas 的小费。
- **gasLimit**：交易允许消耗的最大 gas 量。
- **to**：接收方地址。
- **value**：交易中发送的以太币数量。
- **data**：交易附加数据，通常为合约调用数据。
- **v, r, s**：交易的签名。

#### 1.2.4.EIP-1559 交易的执行流程

- **交易创建**：用户创建一个包含 maxFeePerGas 和 maxPriorityFeePerGas 的交易。
- **交易签名**：用户使用其私钥对交易进行签名，生成v、r、s字段。
- **交易广播**：签名后的交易被广播到以太坊网络。
- **交易验证**：矿工节点接收交易并进行验证，包括检查nonce、签名和账户余额等。
- **基本费用确定**：矿工根据网络状态确定当前区块的基本费用。
- **费用计算**：矿工从用户提供的 maxFeePerGas 中扣除基本费用，剩余部分作为小费。
- **交易打包**：矿工优先打包小费较高的交易，以最大化收益。
- **交易确认**：交易被打包到区块中，用户支付的总费用为基本费用加小费。

#### 1.2.5.EIP-1559 的优势

- **费用预测性**：基本费用的动态调整使得交易费用更加可预测，改善用户体验。
- **网络稳定性**：通过自动调整基本费用，EIP-1559 有助于缓解网络拥堵。
- **矿工激励**：小费机制仍然为矿工提供了足够的激励，确保网络安全。

#### 1.2.6.实际应用中的变化

自 EIP-1559 实施以来，以太坊的交易费用结构发生了显著变化：

- **用户体验改善**：用户不再需要频繁调整 gas 价格，交易费用更加稳定。
- **费用燃烧机制**：基本费用部分被销毁（burned），减少了以太币的供应，可能对 ETH 的长期价值产生积极影响。

### 1.3. Legacy 交易与 EIP-1559 交易的对比

EIP-1559交易引入了基本费用（base fee）和小费（priority fee）机制，改善了Legacy交易中的一些问题：

- **费用预测性**：EIP-1559的基本费用根据网络需求动态调整，使交易费用更加可预测。
- **用户体验**：用户不再需要频繁调整gasPrice，简化了交易的创建和提交过程。
- **费用销毁机制**：EIP-1559中的基本费用部分被销毁，减少了以太币的供应，可能对ETH的长期价值产生积极影响。

总结来说，Legacy交易是以太坊早期采用的交易机制，尽管简单直接，但在网络拥堵和用户体验方面存在明显不足。EIP-1559交易通过引入新的费用机制，显著改善了这些问题，提高了网络的整体性能和用户体验。

### 1.4.EIP-4844 和 Blob 交易

在以太坊扩展方案中，Rollups 提供了一种有效的方法来提高网络的吞吐量和降低交易费用。Rollups 主要有两种类型：Optimistic Rollups 和 ZK-Rollups。在这些扩展方案中，blob 交易是一种新兴的概念，特别是与以太坊改进提案EIP-4844 相关。EIP-4844，也被称为“Proto-Danksharding”，引入了一种新的交易类型，称为 blob-carrying transactions（携带数据块的交易），用于更高效地存储和传输大量数据 blobs。

#### 1.4.1.Blob 交易的特点

- **高效的数据传输**：Blob 交易允许 Rollups 提交大块数据（blobs）到以太坊主链。这些数据包含了 Rollup 内部的所有交易详细信息。
- **独立于主链状态**：Blob 数据不会直接影响以太坊主链的状态，这意味着它们不会增加主链的存储需求。这些数据主要用于验证和重建 Rollup 的状态。
- **费用优化**：由于 blob 数据不直接影响主链状态，处理这些数据的费用通常较低，从而降低了整体交易成本。

#### 1.4.2.Blob 交易类别

##### 1.4.2.1.数据可用性交易 (Data Availability Transactions)

这些交易主要用于确保 Rollups 提交的 blob 数据在以太坊网络中是可用和可验证的。数据可用性是 Rollups 安全性的重要组成部分，因为链下计算需要基于链上的数据进行验证。

- **提交和验证**：Blob 数据提交到以太坊主链，并通过专门的验证机制确保数据的完整性和可用性。
- **数据存储**：Blob 数据不会永久存储在以太坊主链上，而是通过优化的存储方案（如短期存储或外部存储）来管理。

##### 1.4.2.2.状态更新交易 (State Update Transactions)

这种交易类型用于提交 Rollup 状态的更新信息。虽然具体的交易细节在 blob 中，但状态更新交易会包含指向这些 blob 的引用，以确保主链上的状态可以被正确更新和验证。

- **状态根更新**：每个状态更新交易会包含一个新的状态根，这个状态根是通过处理 blob 数据得到的。
- **验证机制**：状态根的更新和 blob 数据的处理需要通过加密验证机制来确保其准确性和安全性。

#### 1.4.3.Blob 交易的结构

Blob 交易的结构与传统以太坊交易有一定的区别，它引入了一些新的字段来处理和管理 blob 数据。以下是 blob 交易的一些关键字段：

- **nonce**：发送方账户的交易序号。
- **gasPrice**：每单位 gas 的价格。
- **gasLimit**：交易消耗的最大 gas 量。
- **to**：接收方地址，通常为空，因为 blob 交易主要用于数据提交。
- **value**：转移的以太币数量，通常为 0。
- **blobData**：包含实际的 blob 数据。
- **blobVersion**：blob 数据的版本号，用于处理不同版本的 blob 交易格式。
- **blobRoot**：blob 数据的 Merkle 根，用于数据验证。
- **v, r, s**：交易的签名。

#### 1.4.4.Blob 交易的执行流程

- **交易创建**：Rollup 协调器创建一个包含大量交易数据的 blob，并将其打包成 blob 交易。
- **提交到主链**：将 blob 交易提交到以太坊主链，包含 blob 数据和相关的验证信息。
- **验证和存储**：以太坊网络验证 blob 数据的完整性和可用性，并将其存储在优化的存储方案中。
- **状态更新**：Rollup 通过处理 blob 数据更新其状态，并将新的状态根提交到以太坊主链进行记录。

## 2. 基于业务常见的交易类别

### 2.1. 创建合约的交易

创建合约的交易用于在以太坊网络上部署智能合约。其特点是 to 字段为空，data 字段包含合约的字节码。其字段包括：

- **nonce**：发送方账户的交易序号。
- **gasPrice**：每单位 gas 的价格。
- **gasLimit**：交易消耗的最大 gas 量。
- **to**：为空。
- **value**：部署合约时发送的以太币数量。
- **data**：包含合约的字节码。
- **v, r, s**：交易的签名。

### 2.2.ERC20 代币交易

ERC20 是以太坊上最常见的代币标准，用于创建和管理代币。ERC20 代币交易涉及调用代币合约的 transfer 或 approve 等函数。这些交易的 to 字段指向代币合约地址，data 字段包含具体的函数调用和参数。

### 2.3. ERC721 和 ERC1155 交易

ERC721 和 ERC1155 是用于不可替代代币（NFT）的标准。ERC721 代表单个不可替代代币，而 ERC1155 支持多种类型的代币（包括可替代和不可替代代币）。这些交易涉及调用 NFT 合约的 transferFrom 或 safeTransferFrom 等函数。

### 2.4. 内部交易

内部交易是由智能合约内部触发的交易，例如一个合约调用另一个合约或执行自身的函数。这些交易不会直接显示在区块链上，而是通过事件日志（logs）或工具（如 Etherscan）来跟踪。

我们都知道，解析内部交易需要运行 archive 节点, 并且节点需要开启 debug 模块。社区有很多追踪内部交易的工具，如 ETHTX; 当然，使用第三方节点直接解析追踪，例如使用 erigon 节点。

- ETHTX
- https://github.com/EthTx/ethtx_ce
- https://github.com/EthTx/ethtx
- Erigon 节点
- https://github.com/ledgerwatch/erigon

## 3. 总结

熟悉 Legacy, Eip1559 和 Blob 交易类型，能帮助我们更好，更高效的开发我们的程序，如果我们进行转账和 Call 合约时，需要更好的用户体验和手续费预测，选用 EIP1559 交易类型，但如果我们对用户体验和手续费的准确预测要求不高，或不希望 ETH 销毁，我们使用 Legacy；对于 L2 rollup 交易到 Ethereum 上，我们选用的是 Blob 交易类型。

熟悉合约创建，ERC20, ERC721 和 ERC1559 和内部交易等类别，当我们需要做数据统计系统，数据分类系统，基于交易的业务平台如"数字货币追踪"，"defi 数据平台"，"浏览器"等系统特别有用。

# 三.Ethereum 生态产品体系

![img](https://thewebthree.xyz/media/editor/2_20241012101510397733.png)

# 四.Ethereum 生态产品框架详解

以太坊生态有很多产品线，前面的课程中我们已经讲了钱包和 NFT 相关的产品，Defi 产品我们后面会有相应的专题课程，因此 Ethereum 的产品课程我们主要围绕着以下这些项目展开

- LSD 产品
- EigenLayer 重新质押协议
- EigenLayer 共享安全模型
- Layer2
- DA
- 桥，浏览器和水龙头

## 1.LSD 产品

我们知道，要起一个信标链节点参与以太坊网络的共识需要 32 个 ETH，很多散户是没有 32 个 ETH 的，为了让散户也能参与到 ETH 的质押获取收益，就催生了LSD 产品，当然，开发 LSD 产品的项目方也能赚到钱，所有市场上涌现出来很多 LSD 的产品；例如 lido, mantle-lsd, binance-lsd, swell 等项目。

### 1.1. 质押逻辑图

![img](https://thewebthree.xyz/media/editor/3_20241012101554415670.png)

### 1.2. 取回质押逻辑图

![img](https://thewebthree.xyz/media/editor/4_20241012101627066805.png)

- 用户首先请求取回质押，并退回质押凭证 Token, 进入排队取款期
- 排队取款期内，请求退回质押的用户的 ETH 达到 32 个，直接退出一个信标链节点，把资金返还给用户
- 如果排队取款期结束，还是没达到 32 ETH， LSD 产品里面未质押的资金给到用户

### 1.3. Cliam 奖励逻辑

![img](https://thewebthree.xyz/media/editor/5_20241012101714490736.png)

- 矿池参与出块获得奖励，一部分奖励给自己，一部分奖励给到 LSD
- LSD 产品抽取一部分收益，剩余的按照用户的质押情况分发给用户

## 2.EigenLayer

### 2.1. 重新质押逻辑图

![img](https://thewebthree.xyz/media/editor/6_20241012101754554167.png)

### 2.2. EigenLayer & LinkLayer 逻辑图

![img](https://thewebthree.xyz/media/editor/7_20241012101816033126.png)

- 第一步：节点运营注册到 EigenLayer 合约
- 第二步：staker 质押对应的资金到策略合约
- 第三步：staker 把资金的质押 shares 委托给 operator
- 第四步：节点运营商参与网络的计算，验证获得奖励，并将奖励按照预先设定的分成比例分 staker
- 第五步：Operator 和 Staker 分别取 cliam 自己的奖励

## 3.Layer2 之名词解释

### 3.1 什么是 Layer2

Layer 2（第二层）是指在区块链技术和网络协议中用于扩展基础区块链（Layer 1）的解决方案。其目的是提高交易速度、降低交易费用，并增强网络的可扩展性和效率。Layer 2 通过在主链之外处理大量交易，然后将结果批量提交到主链，从而减轻主链的负担。以下是 Layer 2 的一些关键特点和技术：

- 扩展性：Layer 2 解决方案可以处理更多的交易量，从而缓解 Layer 1（如以太坊和比特币）上的拥堵问题。
- 成本降低：通过在链下处理交易，Layer 2 可以显著降低用户的交易费用。
- 提高速度：由于交易不需要在主链上逐一确认，Layer 2 可以大幅提高交易处理速度。
- 安全性：尽管交易在链下处理，但 Layer 2 解决方案仍依赖于主链的安全性来保证最终的交易结果是可信和不可篡改的。

### 3.2.常见的 Layer 2 解决方案

#### 3.2.1.状态通道（State Channels）

这种方法允许两方或多方在链下进行多次交易，只在交易结束时将最终状态提交到区块链。一个典型的例子是闪电网络（Lightning Network），主要用于比特币。

#### 3.2.2.侧链（Sidechains）

侧链是一条独立的区块链，使用其自身的共识机制，但通过双向锚定与主链（母链）连接。侧链可以自由地实现不同的功能和优化，同时主链依旧保持其主要的安全和稳定性。

#### 3.2.3.Rollups

Rollups 通过将大量交易打包到一个单一交易中，并将其提交到主链。这种方法可以分为两种类型：乐观 Rollups（Optimistic Rollups）和零知识 Rollups（zk-Rollups）。

- Op Rollups：假设交易是有效的，只有在有争议时才进行验证
- Zk Rollups：通过零知识证明技术，在提交交易数据的同时，保证其正确性。

#### 3.2.4.Plasma

Plasma 是一种框架，允许创建多层的子链结构，每层都可以处理大量的交易。尽管其理论基础较强，但在实际应用中面临一定的挑战。

但在 l2beat 网站上，除了 rollups 之外，其他的解决方案都全部定义为侧链

### 3.3 Op Rollup

Optimistic Rollups 是一种基于承诺链（commit chain）和执行链（execution chain）的 Layer2 扩展方案。它将大量交易数据存储在链外的执行链上，并定期将执行结果提交到链上的承诺链中。通过链外计算和链上争议解决机制，Optimistic Rollups 实现了高性能的智能合约执行，同时保留了以太坊的去中心化特性。

``Optimistic Rollups 主流的项目

- Arbitrum
- Optimism
- 基于 OpStack 改造的 Layer2

### 3.4. Zk Rollup

zk-Rollups 是一种基于零知识证明（Zero-Knowledge Proofs）的 Layer2 扩展方案。它通过将大量交易数据压缩成证明，并在链上发布摘要来实现高吞吐量和低成本的交易。zk-Rollups 提供了更高的隐私保护和交易验证效率，但相对来说实现和部署的技术门槛较高。

``ZK-Rollups 主流的项目

- PolygonZkEVM
- Scroll
- Starknet
- ZksyncEra
- Linea
- 基于 Polygon CDK, Scroll 和 ZkSyncEra 等改造的项目

### 3.5.Sequencer

L2 交易执行与排序

### 3.6.RollUp Services

提交交易数据和交易证明的服务

### 3.7.模块化

目前的 L2 区块链项目中，模块化已然成为标配； 我们都知道，模块化这个词源于Mustafa Albasan 和 Vitalik 在 2018 年共同撰写的，题为《数据可用性采样和欺诈证明》，后经 Celestia 发扬光大。

模块化，可组合落到 Layer2 上是非常合适的，但是在 Layer3 上又是怎样表现的呢，我们如何理解模块化可组合的 Layer3 呢？

模块化能行得通主要源于区块链公链架构的可组合特性，一个成熟的公链包括：

- 结算层（Settlement layer）负责资产的交易状态转移和确定；
- DA层（Data Availability）负责交易数据的状态变数据可用性，以供交易验证：
- 执行层（Execution layer）负责处理交易的执行逻辑，包括智能合约的调用和执行；
- 共识层（Consensus Layer）负责所有节点就某一版本的交易历史达成一致性；
- 跨链通信层（Interoperability Layer）负责不同区块链网络的消息通信和状态管理。

以上各个区块链组件分工明确，各司其职构成了区块链的可信和去中心化特性

### 3.8.数据可用层

数据可用层（Data Availability Layer）是指处理和保证数据可用性的一层。数据可用性是指数据在需要时可以被访问、验证和使用，这对于区块链系统中的数据完整性和安全性至关重要。数据可用层的设计目标是确保所有参与者能够访问和验证区块链上发布的数据，从而保证整个系统的透明性和可靠性。

#### 3.8.1数据可用层的关键功能

- **数据存储和分发**：数据可用层负责存储区块链生成的数据，并确保这些数据可以被所有节点访问。它提供一种分布式数据存储机制，以确保数据的持久性和冗余性。
- **数据验证**：该层还提供验证机制，允许节点快速验证数据的完整性和正确性。数据验证是确保数据没有被篡改或损坏的关键步骤。
- **数据检索**：数据可用层需要确保数据在需要时可以被高效地检索和访问。无论是进行交易验证、智能合约执行，还是数据分析，都依赖于快速的数据检索能力。
- **冗余和容错**：为了防止数据丢失或损坏，数据可用层通常会实现数据冗余和容错机制，例如通过分布式哈希表（DHT）或复制数据到多个节点。

#### 3.8.2.数据可用层在区块链架构中的位置

在分层的区块链架构中，数据可用层通常与其他层（如结算层和执行层）相互配合，以确保整个系统的高效运行。具体来说，数据可用层为结算层和执行层提供了可靠的数据存储和访问服务。

#### 3.8.3.数据可用层的实现方式

- **链上数据可用性：**在传统区块链系统中，所有数据都存储在链上（如比特币和以太坊），这确保了数据的可用性。然而，这种方式可能导致区块链膨胀和性能问题。
- **链下数据可用性：**一些现代区块链系统采用链下数据存储来解决链上数据膨胀的问题。例如，Rollup技术将大部分交易数据存储在链下，并仅在链上存储数据的摘要或证明。
- **分片技术：**分片技术将区块链分割成多个小片，每个小片存储一部分数据。这种方法提高了系统的可扩展性和数据处理能力，但需要有效的数据可用性方案来保证每个小片的数据可访问性和完整性。

#### 3.8.4数据可用层的挑战

- **数据可用性攻击：**数据可用性攻击是指恶意节点在不提供全部数据的情况下发布区块，使其他节点无法验证数据的完整性。解决这一问题需要设计有效的数据可用性证明机制。
- **存储和带宽限制：**随着区块链数据量的增加，存储和带宽需求也会显著增加。数据可用层需要高效的存储和分发机制，以应对不断增长的数据需求。
- **隐私和安全：**确保数据的隐私和安全也是数据可用层的重要挑战之一。需要设计加密和访问控制机制来保护敏感数据。

#### 3.8.5.数据可用到的算法

**数据可用性证明（Data Availability Proofs）**

数据可用性证明是一种方法，用于验证发布的数据是否实际存在且可访问。这些证明对于防止数据可用性攻击（例如，区块发布者声称发布了数据但实际上没有）非常重要。

- Kate Commitments：
- 一种基于多项式承诺的方案，可以高效地验证大数据集的可用性。它使用KZG（Kate-Zaverucha-Goldberg）承诺来证明特定数据块已被正确发布。
- Data Availability Sampling：
- 一种随机抽样技术，节点通过随机抽取和验证少量数据片段来确定整个数据集的可用性。此方法降低了验证成本，使得即使资源有限的轻节点也能参与验证。

**纠删码（Erasure Coding）**

纠删码是一种数据编码技术，用于提高数据存储的冗余性和可靠性。通过将数据分成多个片段并添加冗余信息，即使部分片段丢失或损坏，数据仍然可以恢复。

- Reed-Solomon Codes：
- 一种广泛使用的纠删码，能够从任意 k 个有效片段中恢复出原始数据，其中 k 是编码参数。这种编码在存储和分布式系统中被广泛应用。
- LDPC Codes（Low-Density Parity-Check Codes）：
- 一种高效的纠删码，使用稀疏矩阵进行编码和解码，适用于需要高冗余和低延迟的系统。

**分布式哈希表（DHT）**

DHT是一种分布式存储系统，节点通过哈希函数确定数据的位置，并在网络中存储和检索数据。

- Kademlia：
- 一种常见的DHT实现，使用XOR距离度量来确定节点之间的距离并高效地路由数据请求。Kademlia的分布式特性使其适用于去中心化网络中的数据存储和检索。

**密码学技术**

加密和哈希算法在确保数据的完整性和安全性方面发挥关键作用。

- Merkle Trees：
- Merkle树是一种哈希树结构，用于高效和安全地验证大数据集的完整性。通过根哈希（Merkle Root），节点可以快速验证任何数据片段是否属于数据集的一部分。
- 零知识证明（ZKP）：
- 零知识证明允许一方在不透露具体数据的情况下，证明其拥有某些数据的知识。ZKP在数据可用性和隐私保护方面有广泛应用，例如zk-SNARKs（零知识简洁非交互知识论证）。

**数据分片（Data Sharding）**

数据分片将大数据集分割成更小的片段，并分布在不同的节点上，以提高系统的可扩展性和数据可用性。

以太坊2.0 分片（Ethereum 2.0 Sharding）：以太坊2.0采用分片技术，将区块链状态和交易负载分割成多个平行运行的分片链。每个分片链独立处理交易和状态，但通过信标链（Beacon Chain）实现统一的共识和数据可用性。

#### **3.8.6.数据可用层实例**

- **以太坊 2.0：**在以太坊 2.0 的分片设计中，信标链和分片链需要协同工作，数据可用层在保证每个分片链数据的可用性方面发挥重要作用。
- **Celestia：**Celestia 专注于构建一个专门的数据可用层，通过分离共识和数据可用性来提高区块链的可扩展性和效率。
- **EigenDa**: 是一种新兴的数据可用性（Data Availability, DA）解决方案，专注于通过创新的技术方法来确保区块链和去中心化应用中的数据可用性。EigenDA 结合了多种先进的密码学和数据分发技术，以实现高效、可靠和可扩展的数据可用性。

#### **3.8.7.去中心化存储网络**

去中心化存储网络利用分布式存储技术来提高数据的可用性和抗审查性。

- **IPFS（InterPlanetary File System）：**IPFS是一种分布式文件系统，使用内容寻址和DHT来存储和检索数据。通过分布式存储，IPFS确保数据在网络中具有高可用性和冗余性。
- **Filecoin：**基于IPFS的去中心化存储网络，Filecoin通过经济激励机制确保数据存储的可靠性和持久性。存储节点通过提供存储空间和检索服务获得代币奖励。

## **4.Layer2 之 OP Rollup 代表项目 OpStack**

### **4.1. OVM 版本产品架构图**

![img](https://thewebthree.xyz/media/editor/a_20241012101902221108.png)

### **4.2. OpStack 没有 Fraud Proof 版本产品架构图**

![img](https://thewebthree.xyz/media/editor/b_20241012101937849660.png)

## **5.Layer2 Zk Rollup 代表项目之 PolygonZkevm**

### **5.1. PolygonZkevm 产品架构图**

![img](https://thewebthree.xyz/media/editor/12312_20241012102020585778.png)

## **6. EigenDa 产品**

### **6.1. EigenDa产品架构图**

![img](https://thewebthree.xyz/media/editor/1231231312_20241012102047696573.png)

## 7. 浏览器产品

![img](https://thewebthree.xyz/media/editor/asdas_20241012102113207411.png)

## **8.水龙头产品**

![img](https://thewebthree.xyz/media/editor/asdasdas_20241012102141818487.png)

## 9.Layer2 代表产品 OpStack 和 Polygon 的桥产品

### **9.1 Ethereum L2 的 OP Stack 官方桥产品底层逻辑**

![img](https://thewebthree.xyz/media/editor/ewer_20241012102203715698.png)

### **9.2 Ethereum L2 的 Polygon 官方桥产品底层逻辑**

![img](https://thewebthree.xyz/media/editor/sddas_20241012102229485750.png)

### **9.3. 第三方快速桥**

#### **9.3.1. 不带交易 Swap 的桥**

![img](https://thewebthree.xyz/media/editor/ewrwe_20241012102249010694.png)

#### **9.3.1. 带交易 Swap 的桥**

![img](https://thewebthree.xyz/media/editor/qweqweqw_20241012102316368718.png)

- 带 Swap 的可以在原链上 Swap 之后在跨链，或者跨链到目标链上再进行 Swap。

# **五.总结**

本文咱们讲了以太坊生态的中比较有代表的性的项目的产品框架

- LSD 产品
- Layer2 代表产品
- OP
- Polygon
- EigenLayer 质押模型
- AVS 共享安全
- EigenDA 产品
- 浏览器
- 水龙头
- Layer2 官方桥和第三方

在接下来的文章中呢，我们将会分拆讲解各个产品的细节的底层实现逻辑。