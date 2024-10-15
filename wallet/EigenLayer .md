# The Web3 社区产品课程之 EigenLayer 的产品细节逻辑



# **一.概述**

# **二. 产品架构**

## **1.重新质押的解释**

![img](https://thewebthree.xyz/media/editor/231231_20241012111014631525.png)

- 质押 ETH 到 LSD 产品会获得质押的凭证 xxxETH，这个凭证是一个 ERC20 Token; 可以和 ETH 1:1 兑换，也就是说它是和 ETH 等价。
- 将 LSD mint 出来的 xxxETH 再质押 EigenLayer, 这也就是 EigenLayer 为什么称为重新质押的原因。

## **2.2. EigenLayer（半成品）**

![img](https://thewebthree.xyz/media/editor/werwer_20241012111024972801.png)

- 第一步：节点运营注册到 EigenLayer 合约, 可以接受其他 Staker 委托质押权益给他
- 第二步：staker 质押对应的资金到策略合约
- 第三步：staker 把资金的质押 shares 委托给 operator
- 第四步：节点运营商参与网络的计算，验证获得奖励，并将奖励按照预先设定的分成比例分 staker
- 第五步：Operator 和 Staker 分别取 cliam 自己的奖励

# **三. 功能实现细节**

## **1.节点注册**

- 注册成为节点运营商，可以接受 Staker 委托质押份额
- 注册成为节点（Bls key 的注册），将 Bls key 注册到 BlsRegistery
- 注册成为节点，可以接受未来作恶是的罚没

## **2.Staker 质押和委托**

- Staker 质押时候，将资金打对应的 strategy, 获得对应质押份额，可以选择对应 operator 将质押份额委托 Operator
- 质押可以获得 EigenLayer 的 Eigen 代币

## **3.取回质押**

- 执行 undelegate 或者排队取款，排时间 delay 的区块的时间
- 过了 Delay 的时间，就可以把钱取出来