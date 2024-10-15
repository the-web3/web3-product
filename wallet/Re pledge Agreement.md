# The Web3 社区产品课程之重新质押协议底层实现逻辑



# **一.什么是重新质押**

重新质押是在已经质押的资产基础上，将其用于其他用途或多个协议。例如，你可以将质押的资产用于支持一个新的协议，同时继续在原有的协议中保留质押状态。

在一些区块链平台上，例如 Eigenlayer，用户可以将他们在 LSD 协议中质押的资产重新质押到 Eigenlayer 协议中。这种方式可以让用户在多个协议中获取奖励。

# **二. EigenLayer 重新质押底层实现逻辑**

## **1.EigenLayer 重新质押**

Eigenlayer 允许用户将他们已经质押的资产重新质押，以便在其网络中参与更多的协议和服务。这种重新质押的机制可以提高资产的利用率和安全性。

EigenLayer 重新质押协议目前已经支持以下 LSD 协议重新质押

![img](https://thewebthree.xyz/media/editor/212312_20241012112210044842.png)

EigenLayer 重新质押的流程如下

- 第一步：Staker 先将自己的资金质押给 LSD 协议
- 第二步：LSD 协议会 mint 出 xxxETH
- 第三步：用户将 mint 出来的 xxxETH 质押给 EigenLayer, 即可以完成重新质押

## **2.EigenLayer 重新质押底层逻辑**

![img](https://thewebthree.xyz/media/editor/dfgdfg_20241012112240809794.png)

# **三. LSD 产品和重新质押产品联动的过程**

## **1.EigenLayer 策略管理流程**

![img](https://thewebthree.xyz/media/editor/gfhfgh_20241012112307639229.png)

- 可以通过 addStrategiesToDepositWhitelist 将底层的质押策略添加到 StrategyManager
- 可以通过 removeStrategiesFromDepositWhitelist 将底层的质押策略从 StrategyManager 移除

## **2.EigenLayer 质押流程**

![img](https://thewebthree.xyz/media/editor/dfgdfgd_20241012112342173272.png)

- 第一步：Operator 先注册到质押协议，**注意：图中虽然画出了 AVS 的内容，但是咱们这里不讲 AVS 相关的内容，后面的文章会讲解，这里只讲重新质押协议**
- 第二步：Staker 将从 LSD 协议里面获取到的 xxxETH 通过 StrategyManager 质押到对应的策略里面，质押完成之后，Staker 的质押 Shares 会记录到合约里面，如果 Staker 已经 Delegate 过对应的 Operator，对应的 Operator 的质押份额会增加。
- 第三步：如果 Staker 是第一次质押，需要调用 delegateTo 将自己的质押份额转移想要 delegate 的 Operator，这样就完成了整个质押流程。

## **3. EigenLayer 排队取款流程**

![img](https://thewebthree.xyz/media/editor/12312312_20241012112415403881.png)

第一步：操作方式有两种

- 直接 undelegate: 直接 undelegate, 把和 operator 的绑定关系解除，并生成一笔排队取款的交易
- 排队取款：创建一笔排队取款的交易

第二步：当排队时间结束之后，条用完成排队取款拿出资金，整个质押的 shares 全部清零

## **4. EigenLayer 领取奖励流程**

![img](https://thewebthree.xyz/media/editor/324234234234_20241012112437295419.png)

- 第一步：提交奖励的 merkle 树根和付款的 Range 信息
- 第二步：从合约里面 claim 奖励

# **四. LSD 与 EigenLayer 的联动流程**

## 1. **mint 的 xxxETH 重新质押给 EigenLayer**

![img](https://thewebthree.xyz/media/editor/32423434_20241012112514366424.png)

## 2. **取款流程**

![img](https://thewebthree.xyz/media/editor/56456756_20241012112533209716.png)

# **五. 小结**

本文咱们主要讲了重新质押协议，里面也提到了和 Eigenlayer 重新质押写相关的 AVS 的内容，下一篇文章中我们将详细解释 EigenLayer AVS 是如何运作的。