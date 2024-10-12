# DappLink 一键发钱包技术解决方案



# **一.概述**

DappLink 的一键发钱包技术解决方案旨在简化钱包开发和运维流程，旨在帮助 Web3 企业降低钱包的开发和运维成本，提供开箱即用的组件模块。

DappLink 的所有模块都是开源，任何人和企业都可以使用这套技术栈构建自己的钱包；同时，DappLink 也提供各个模块组件服务，任何人对接钱包都可以使用 DappLink 的组件服务接口。

DappLink 核心功能：

- 一键发去中心化(HD)钱包
- 一键发中心化(交易所)钱包
- 一键发 MPC 托管钱包
- 一键发 AA 钱包

# **二.一键发钱包架构设计**

![img](https://thewebthree.xyz/media/editor/36982017_20241012134024253507.png)

- **chain-explorer-api:**
- 功能：统一浏览器接口请求响应参数库，对接所有需要支持链的浏览器，如：Etherscan, Oklink, Solscan 和 NftScan 等。
- 代码 github 地址：https://github.com/dapplink-labs/chain-explorer-api
- **wallet-chain-node:**
- 功能：统一公链和浏览器 RPC 服务, 封装了所有链的节点 rpc 和浏览器 api，为钱包扫链业务层提供 RPC 服务接口
- github 地址：https://github.com/dapplink-labs/wallet-chain-node
- **key-locker:**：
- 功能：去中心化的密钥柜管理工具
- 代码 github 地址：https://github.com/dapplink-labs/key-locker
- **dapplink-secret：**
- 功能：门限共享秘密算法的底层库;
- 代码 github 地址
- **Nodejs 版本：** https://github.com/dapplink-labs/dapplink-secret
- **Java 版本：** https://github.com/dapplink-labs/beeKey_java
- **Dapp Js：** 并不是 DappLink 开发的，使用 trust wallet 或者 metamask js 改造的
- **skyeye：**
- 功能：行情聚合器物，聚合中心化交易所和去中心化的行情
- github 地址：https://github.com/the-web3/skyeye
- **trade：**
- 功能：背靠中心化交易所，支持中心化的闪兑，扛杆，期货，期权保险，双币投资，做市商等功能一个交易系统, 私有项目，
- 代码 Github 地址：项目未开源
- **wallet-sdk：**
- 功能：支持 60 多条主链的离线签名的 SDK
- 代码 github 地址: 未开源
- **tss:**
- 功能：MPC 托管系统代码代码
- 代码 Github 地址：项目未开源
- **linklayer:**
- 功能：跨链质押项目，为 MPC 托管系统提供安全性保障
- 代码 Github 地址: https://github.com/eniac-x-labs/linklayer
- **hailstone:**
- 功能：HD 钱包后端服务服务，对接到各个模块
- 代码 Github 地址: https://github.com/eniac-x-labs/hailstone
- **wallet-scanner:**
- 功能：统一充值，提现，归集，转冷，风控的钱包服务
- 代码 Github 地址: 代码未开源
- **centralized wallet servicer:**
- 功能：中心化钱包业务组件，调度签名机生成钱包地址，将业务地址递给 wallet-scanner，wallet-scanner 给其提供对应的钱包充值，提现，归集，转冷等交易信息
- 代码 Github 地址: 代码未开源

# **三.组件之间的交互流程**

## **1.wallet-chain-node 和 chain-explorer-api 的交互**

![img](https://thewebthree.xyz/media/editor/123_20241012134119323838.png)

## **2.wallet-chain-node 和 wallet-scanner 交互流程**

![img](https://thewebthree.xyz/media/editor/2589324_20241012134145348167.png)

## **3.wallet-chain-node, skeye, trade 和 hailstone 交互流程**

![img](https://thewebthree.xyz/media/editor/asdas3658_20241012134207959247.png)

## **4.离线签名的交互流程**

![img](https://thewebthree.xyz/media/editor/258sadasd_20241012134254354866.png)

## **5.MPC 交互流程图**

![img](https://thewebthree.xyz/media/editor/213123_20241012134314784696.png)

## **6.Linklayer 如何为 MPC 托管钱包提供安全性保障**

![img](https://thewebthree.xyz/media/editor/sad366_20241012134336917568.png)

## **7.闪兑业务流（中心化钱包）**

![img](https://thewebthree.xyz/media/editor/36asdasd_20241012134407555695.png)

## **8.key-locker 业务流程**

![img](https://thewebthree.xyz/media/editor/231231231231_20241012134442232444.png)

## **8. MPC 结合 TEE 和门限算法进行密钥备份**

![img](https://thewebthree.xyz/media/editor/asdasdasdasd5685858_20241012134510220661.png)

# **四.总结**

DappLink 的一键发钱包技术解决方案为 Web3 企业提供了一个全面、开源的工具集，旨在简化钱包的开发和运维，降低成本。通过一系列模块化组件，DappLink 支持去中心化钱包、中心化钱包、MPC 托管钱包和 AA 钱包的快速创建，确保企业可以快速适应市场需求。

在架构设计方面，DappLink 通过 **chain-explorer-api**、**wallet-chain-node**、**key-locker** 等核心模块实现了高效的功能集成。每个模块都有明确的功能定位，支持链的浏览器接口、节点 RPC 服务、密钥管理以及多种算法的应用，确保系统的安全性和可靠性。

组件之间的交互流程展示了 DappLink 如何通过高效的模块协作，实现钱包的充值、提现、风控等业务，同时为用户提供流畅的体验。这种设计不仅提升了系统的灵活性，还能应对复杂的交易需求。

总的来说，DappLink 的一键发钱包技术解决方案为 Web3 企业提供了高效、安全且灵活的数字资产管理工具，推动了区块链技术的广泛应用和普及。企业可以借助这些开源组件快速构建自有钱包，从而聚焦于业务创新和用户体验提升。