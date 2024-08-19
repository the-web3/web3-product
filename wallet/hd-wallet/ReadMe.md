# The Web3 社区产品课程之去中心化钱包产品底层逻辑


## 一. 概述
本文档是一个通用型的去中心化钱包产品设计文档，我们知道的钱包如 ImToken, TokenPocket, Trust Wallet 和 MetaMask 等，他们的设计方式和这个文档里面设计方式大多都是类似。钱包有中心化钱包（也就是交易所钱包），去中心化钱包，硬件钱包（去中心化钱包和硬件钱包的设计方式都是 HD 钱包）和 MPC. 托管钱包等类别；在以太坊生态里面还有 Gnosis safe 和 AA 钱包。大家可能还听过社交恢复钱包，实际上，社交恢复这个功能在去中心化钱包，AA 钱包里面都可以正常去集成，在其他类型的钱包里面没有实际意义。

## 二. HD 钱包背后基础设施

### 1.名词解释
BIP32:  定义了层级确定性（HD）钱包的结构和功能。HD 钱包允许通过一个根种子生成一个树状结构的密钥对。每个密钥对（公钥和私钥）可以从一个主密钥派生出来，这样的结构让用户只需备份一个主种子，就能生成和恢复所有的子密钥。BIP32 引入了“确定性”和“层级”的概念，支持在不同的分支上生成子密钥，可以用于不同的账户、地址等。
关键点：
- 通过一个种子生成多个子密钥。
- 子密钥可以分层管理（父子关系）。
- 增强了钱包的可扩展性和安全性。

BIP39:定义了一种将随机数（entropy）转化为一组助记词的标准方法。这组助记词可以用于生成 HD 钱包的种子，并进一步派生出一系列的密钥对。助记词通常由 12、15、18、21 或 24 个单词组成，使用户能够更容易地备份和恢复钱包。BIP39 还包括了一个可选的助记词密码，进一步增强了钱包的安全性
关键点：
- 助记词生成和使用的标准。
- 允许通过助记词备份和恢复 HD 钱包。
- 提高了用户的易用性和安全性。

BIP44:基于 BIP32 和 BIP43，定义了一个多账户层级结构的标准，用于确定性钱包（HD Wallets）。它规定了一个 5 层路径的结构，用于生成账户、地址等。这一标准允许用户在同一主密钥下管理多个账户，每个账户可以有不同的币种和地址。路径的格式为 m / purpose' / coin_type' / account' / change / address_index，其中 purpose 通常是 44'

关键点：
- 标准化的路径结构，支持多账户、多币种管理。
- 允许用户轻松生成和管理不同账户和地址。
- 提高了钱包的组织性和可操作性。

BIP86:提出了基于单密钥 Taproot 输出的描述符钱包（Descriptor Wallet）的使用方法。Taproot 是比特币的一项升级，旨在提高交易隐私性和效率。BIP86 主要介绍如何在钱包中使用 Taproot 地址和单密钥输出，这样可以使得交易和脚本的执行更高效，同时隐藏未使用的脚本路径，从而提升隐私。BIP86 强调了使用简化的单密钥路径，而非复杂的多重签名或其他脚本路径。

关键点：
- 基于 Taproot 的地址生成和使用。
- 强调单密钥的隐私性和效率。
- 提供了一种简化的地址生成方法，适用于支持 Taproot 的钱包。

#### 一句话总结
- BIP32：定义了层级确定性（HD）钱包，支持通过种子生成子密钥。
- BIP39：提供了助记词生成和恢复 HD 钱包的方法。
- BIP44：定义了多账户路径结构，支持多个账户和币种的管理。
- BIP86：引入了基于单密钥 Taproot 输出的描述符钱包，提升了隐私性和效率。

### 2.HD 钱包推导简单流程
HD 钱包推导的流程可以概括为以下几个主要步骤。这个过程包括从种子生成根密钥，再从根密钥派生子密钥，以及最终生成加密地址。以下是一个简化的推导流程：

#### 2.1.生成随机熵（Entropy）
- 描述：首先，生成一定长度的随机熵，这是钱包的基础。熵的长度通常为 128 位、160 位或 256 位，对应 12、15 或 24 个助记词。
- 生成方式：可以使用硬件随机数生成器，或通过一些加密安全的算法生成。

#### 2.2.熵转换为助记词（Mnemonic Code）
- 描述：使用 BIP39 规定的算法，将熵转换为助记词。助记词是一组易记的单词（通常是 12、15、18、21 或 24 个单词），用户可以通过这组单词备份和恢复钱包。
- 过程：
  - 计算熵的校验和。
  - 将熵和校验和组合，并分割成多组，每组 11 位。
  - 使用 BIP39 单词表将每组 11 位的二进制数映射到一个单词，生成助记词列表。
#### 2.3.助记词转换为种子（Seed）
- 描述：使用助记词和可选的密码短语，通过 PBKDF2 算法生成一个种子。
- 过程：
  - 使用助记词作为输入，结合密码短语（如果有），生成 512 位的种子。
  - 种子作为 HD 钱包的根密钥推导的起点。
#### 2.4.从种子生成根密钥（Master Key）
- 描述：使用 BIP32 规定的 HMAC-SHA512 算法，从种子生成根私钥和根链码。
- 过程：
  - 将种子作为 HMAC-SHA512 的输入，使用固定的密钥 Bitcoin seed。
  - 输出的前 256 位作为根私钥（master private key），后 256 位作为根链码（master chain code）。
  - 根私钥和根链码共同构成根密钥。
#### 2.5.派生子密钥（Child Keys）
- 描述：从根密钥出发，根据特定的派生路径，逐层生成子私钥和子公钥。派生路径通常按照 BIP44 规定的格式 m / purpose' / coin_type' / account' / change / address_index。
- 过程：
  - 使用根密钥和链码，通过 HMAC-SHA512 算法和路径中的索引值，生成子私钥和子链码。
  - 从子私钥可以生成相应的子公钥。
  - 这个过程可以递归进行，从一个私钥派生出多个子私钥。
#### 2.6.生成公钥和地址
- 描述：使用子私钥或子公钥生成相应的加密地址。
- 过程：
  - 从私钥生成公钥。
  - 使用特定的地址编码方式（如 P2PKH、P2SH 或 P2WPKH），将公钥转换为区块链地址。
    
####2.7.使用和备份
- 备份：用户可以将助记词（和密码短语）安全地备份下来。只要拥有这些信息，就可以恢复整个钱包及其所有子账户和地址。
- 使用：用户可以使用派生出的私钥签署交易，或通过生成的地址接收资金。

```
简单流程图
1. 生成随机熵 (Entropy)
       ↓
2. 熵 → 助记词 (Mnemonic)
       ↓
3. 助记词 + 密码短语 → 种子 (Seed)
       ↓
4. 种子 → 根密钥 (Master Key)
       ↓
5. 根密钥 + 派生路径 → 子密钥 (Child Keys)
       ↓
6. 子密钥 → 公钥和地址 (Public Keys and Addresses)
```

## 四.HD 钱包产品逻辑架构

[![architecture](https://github.com/the-web3/web3-product/blob/main/assets/1515.png)](https://github.com/the-web3/web3-product)

1. 架构要点
- BlockChain 层是钱包 RPC 节点
- Services 层是钱包的数据处理，例如比特币的和地址相关的 UTXO 处理，根据地址获取历史交易记录的处理等
  - ElectrumX:  处理比特币的数据服务，这个是一个开源项目
  - Wallet-chain-node: 这个是 The Web3 实现的一个统一的钱包 RPC 服务层
  - Transaction Handle: 交易数据处理器，地址相关的交易处理等，一般可以用第三方服务，如 oklink 和浏览器数据服务
- middle platform: 中台服务是钱包的对接各服务模块，并且还是活动，dapp, 咨询等管理模块的服务端，上层对接统一 RPC 服务，对接 CEX 行情服务等。
  - CEX 行情服务：The Web3 社区实现了一个 skyeye 项目，对接了所有中心化交易所行情和主流的去中心化交易所行情供钱包使用。
  - middle platform services: 承接钱包的前端和后端的一个中间层服务，同时还是活动，dapp, 咨询等管理模块的服务端
- APP 端：钱包的核心功能所在
  - wallet-sdk:  The Web3 社区实现多链离线地址生成和离线签名的 SDK 项目
  - 本地数据库：用户存储加密的助记词编码，私钥，账户信息等

## 五. 功能模块
### 1. 生成助记词和验证助记词
[![architecture](https://github.com/the-web3/web3-product/blob/main/assets/1616.png)](https://github.com/the-web3/web3-product)


### 2. 导出助记词和私钥
[![architecture](https://github.com/the-web3/web3-product/blob/main/assets/1717.png)](https://github.com/the-web3/web3-product)


### 3. 导入助记词和私钥
[![architecture](https://github.com/the-web3/web3-product/blob/main/assets/1818.png)](https://github.com/the-web3/web3-product)


### 4. 转账背后的秘密
[![architecture](https://github.com/the-web3/web3-product/blob/main/assets/1919.png)](https://github.com/the-web3/web3-product)


### 5. 查看余额和交易记录
[![architecture](https://github.com/the-web3/web3-product/blob/main/assets/2020.png)](https://github.com/the-web3/web3-product)


### 6. 行情模块
#### 6.1 业务架构图
[![architecture](https://github.com/the-web3/web3-product/blob/main/assets/2121.png)](https://github.com/the-web3/web3-product)


#### 6.2 业务流程图
[![architecture](https://github.com/the-web3/web3-product/blob/main/assets/2222.png)](https://github.com/the-web3/web3-product)


### 7. DAPP 模块

#### 7.1 业务架构图
[![architecture](https://github.com/the-web3/web3-product/blob/main/assets/2323.png)](https://github.com/the-web3/web3-product)

#### 7.2 业务流程图
[![architecture](https://github.com/the-web3/web3-product/blob/main/assets/2424.png)](https://github.com/the-web3/web3-product)


## 六. UTXO 模型和账户模型简介
### 1.UTXO 模型
UTXO: 未话费的输入输出，一张图说明明白 UTXO

[![architecture](https://github.com/the-web3/web3-product/blob/main/assets/2525.png)](https://github.com/the-web3/web3-product)


### 2.账户模型
在账户模型中，每个用户或合约都有一个账户（Account），这些账户维护了一些关键的状态信息，比如余额、nonce 和存储（对于合约）。账户模型将区块链的状态表示为一个全局的状态树（通常是默克尔树或其他平衡二叉树），其中每个账户的状态都存储在这个状态树中。

账户模型类似于传统银行的账户余额模型

