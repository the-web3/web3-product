# The Web3 社区产品课程之以太坊 LSD 产品底层实现逻辑



# **一. LSD 产品概述**

以太坊 LSD（Liquid Staking Derivatives，流动性质押衍生品）是一类允许用户在以太坊网络上质押他们的以太币（ETH）并同时保持流动性的金融产品。通过这些产品，用户可以质押 ETH 以帮助验证网络，同时获得衍生品代币，代表他们在质押池中的份额。这些代币可以在 DeFi 生态系统中使用，或者用于交易，借贷和重新质押等操作，目前大多数都是重新质押给 EigenLayer。

## **1.常见的LSD 产品**

- **Lido（stETH):** 通过Lido，用户可以质押 ETH 并获得stETH代币，这种代币可以在各种 DeFi 协议和 Eigenlayer 重新质押协议中使用，同时自动积累质押奖励。
- **Rocket Pool（rETH）**: Rocket Pool允许用户质押ETH并获得rETH代币，同样地，rETH持有者也会自动获得质押奖励。
- **Frax Ether（FraxETH）**: Frax Finance推出的FraxETH是一个可流动的 ETH 质押衍生品，旨在结合部分算法稳定币的机制，以增强 ETH 质押的灵活性。
- **Ankr（ankrETH）**: Ankr 提供质押服务，用户质押 ETH 后可获得 ankrETH 代币，能够在多个DeFi平台和 Eigenlayer 重新质押协议上使用。

以上这些 LSD 产品都可以在 Defi 协议，交易所交易，并且还能重新质押给 Eigenlayer； 同时，LSD 产品为以太坊的质押者提供了一个灵活的选择，使他们能够在帮助保护网络的同时，仍然可以灵活地使用他们的资产。

# **二. LSD 产品功能流程**

## 1. **质押流程**

![img](https://thewebthree.xyz/media/editor/3423423_20241012111412727407.png)

- 第一步：用户把 ETH 质押到 Stake 合约(这个合约每个产品名字不一样，但实现的逻辑都是类似的)，收到质押 ETH 之后， mint xxxETH 给用户；用户可以灵活处理自己的资产，可以在二级市场交易，也可选择重新质押给 EigenLayer 等。
- 第二步：当质押的 ETH 的数量达到 32 个或者 32 个的倍数的时候，创建质押 pod 或者由链下服务调度把 ETH 质押给信标链合约，每 32 个 ETH 为一份，然后去启动信标链节点参与网络的共识。

## 2. **取款流程**

![img](https://thewebthree.xyz/media/editor/dfgdfgf_20241012111425751863.png)

- 第一步：Staker 发起提款请求，退回 xxxETH, xxxETH 被锁定到合约，提款请求进入排队取款期
- 第二步：排队取款到期之后，未满 32 个 ETH，销毁用户的 xxxETH, 并将 ETH 和收益的 ETH 返还给用户
- 第三步：排队取款到期之后，满 32 个 ETH，退出一个信标链节点，取回资金；销毁用户的 xxxETH 之后，将用户的 ETH 和质押收益返还给用户。

## 3. **奖励提取流程**

![img](https://thewebthree.xyz/media/editor/yhty_20241012111435944038.png)

- 第一步：信标节点参与网络共识，得到出块的奖励，奖励到达矿池，矿池进行抽成
- 第二步：奖励到达 LSD 产品，LSD 产品方抽成之后再将奖励发放给 staker
- 第三步：staker 从 LSD 产品里面 cliam 奖励。

# **四.LSD 产品小结**

以太坊的流动性质押衍生品（LSD，Liquid Staking Derivatives）是近年来备受关注的创新产品，尤其在以太坊转向权益证明（PoS）机制后。LSD 产品允许用户在参与以太坊质押的同时，仍然能够流动或交易其质押的资产，从而提供了灵活性和更高的资本效率。

这一节我们讲解了 LSD 产品的底层实现逻辑，下一讲我们将讲解 LSD 产品如何和重新质押产品结合的。