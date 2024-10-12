# The Web3 产品课程之 Bitcoin 特性以及其生态产品体系详解



# **一. Bitcoin 概览**

## 1. **Bitcoin 简介**

比特币（Bitcoin）是由一个或一群化名为中本聪（Satoshi Nakamoto）的人在 2008 年提出，并于 2009 年开始发布的去中心化数字货币。它的出现标志着一种新型金融体系的诞生，具有以下主要特点：

- 去中心化：
- 比特币网络没有中央管理机构或中介机构，它通过一个称为区块链的分布式账本来记录所有交易。
- 区块链技术确保了所有参与者都可以查看和验证交易，提高了透明度和安全性。
- 有限供应：
- 比特币的总供应量被固定在2100万枚，这通过代码内的机制控制。
- 这一机制使比特币具备了抗通胀的特点。
- 点对点交易：
- 比特币允许用户之间直接进行交易，不需要通过银行或支付处理机构。
- 这种点对点交易减少了交易成本和处理时间。
- 安全性：
- 比特币使用加密技术确保交易的安全性和隐私性。
- 每一笔交易都需要通过复杂的数学算法进行验证，从而确保系统的完整性。
- 不可逆交易：
- 一旦比特币交易被确认，它就无法被撤销。这减少了欺诈的风险，但也意味着用户需要谨慎操作。
- 挖矿机制：
- 新的比特币通过一个称为挖矿的过程产生。矿工们使用计算能力来解决复杂的数学问题，成功解决问题的矿工将获得比特币奖励。
- 挖矿不仅生成新币，还维护和保护比特币网络的安全。
- 全球流通：
- 比特币可以在全球范围内进行交易，不受地域和国界的限制。
- 它为跨国支付提供了一种高效、低成本的替代方案。
- 隐私和匿名性：
- 虽然比特币交易是公开记录的，但用户身份是匿名的。交易是通过地址（类似于账号）进行的，而不是通过真实身份。

## 2. **Bitcoin 的升级次数介绍**

比特币自 2009 年发布以来，经历了多次重要升级。这些升级旨在提高比特币网络的安全性、效率和功能性。

并且比特币的 Taproot** 升级给比特币带来更多的可能性，Taproot 升级带动了 BRC20 和 Bitcoin-Layer2 的发展，这里我们不在做过多的介绍，在未来的 Layer2. 的课程中我们会深入讲解这部分的内容

- **P2SH（Pay-to-Script-Hash）**
- 时间：2012年
- BIP（Bitcoin Improvement Proposal）：BIP-0016
- 内容：允许更复杂的交易脚本，支持多重签名地址。这种升级使得比特币交易更加灵活和安全
- **比特币改进提案 BIP 66**
- 时间：2015年
- BIP：BIP-0066
- 内容：规范了交易中DER格式的签名，解决了交易签名的一致性问题，增强了网络的安全性。
- **CheckSequenceVerify（CSV）**
- 时间：2016年
- BIP：BIP-0112
- 内容：增加了相对时间锁功能，使得交易可以在指定的时间或块高度之后才生效，这为更复杂的支付通道铺平了道路。
- **Segregated Witness（SegWit）**
- 时间：2017年
- BIP：BIP-0141, BIP-0143, BIP-0144
- 内容：分离交易签名数据，提高了区块的有效容量，减小了交易体积，降低了交易费用。还解决了交易的可塑性问题，使得闪电网络等侧链解决方案成为可能。
- **隔离见证2x（SegWit2x）**
- 时间：2017年
- 内容：这次升级是对 SegWit 的后续提案，旨在进一步增加区块大小。然而，由于社区共识未达成，这次升级最终未能实现。
- **Taproot**
- 时间：2021年
- BIP：BIP-0340, BIP-0341, BIP-0342
- 内容：引入了 Schnorr 签名和默克尔化抽象语法树（MAST），增强了隐私性和执行脚本验证的功能，进一步提高了交易的灵活性和效率。这是自2017年 SegWit 以来最重要的一次升级。
- **MAST（Merkelized Abstract Syntax Trees）**
- 时间：2021年
- BIP：作为 Taproot 的一部分
- 内容：允许将多种条件的智能合约合并为一个，使得只有满足条件的部分才被公开，提高了隐私性和效率。
- **Schnorr Signatures**
- 时间：2021年
- BIP：作为 Taproot 的一部分
- 内容：提供了一种更高效和安全的签名算法，允许多重签名聚合，提高了交易的隐私性和可扩展性。

## 3. **UTXO 介绍**

UTXO（Unspent Transaction Output，未花费交易输出）模型是比特币及其他一些加密货币使用的一种记账方法。它与账户模型不同，通过追踪未花费的交易输出来记录每个地址的余额。以下是UTXO模型的详细介绍：

### 3.1 **模型解说**

在解说 UTXO 模型之前，我想先说说一个名词，叫做 Transaction，即交易，Transaction 和 UTXO 是相辅相成的，下面先来举个例子：

张三：通过挖矿得到了120个比特币，现在张三饿了，想要花费2个比特币去购买一个面包。这是只是举例而已，以现在比特币的价格，1个比特币就可以买到一大堆面包了。

现在我们假设，李四是面包店营业主

这样的话，在比特币中，张三付给李四将一次性付给李四 120 块，李四给张三找零 118 块，这里其实产生了两笔交易，咱们可以这样理解，张三的钱被分成了两份，其中 118 打给了自己，剩下的 2 块打给了李四。

交易与交易之间组成了网状关系，1 个交易的输出，成为了下 1 个交易的输入；下 1 个交易的输出，又成了下下 1 个交易的输入。所有的钱，在这个网络中流动，每 1 笔钱的去向、来源，都是可追溯的，而这也是区块链网络的一个重要特点。

上面的讲解可能大多数人都比较懵逼，接下来咱们用比较通俗的方式来说明 UTXO 和 Transaction 到底是什么

在现实生活中，一笔转账对应的事一个付款人和一个收款人，而在比特币种，一笔转账对应的事多个转账人和多个收款人。

现在咱们仔细分析一下上面的这个例子，对于张三买面包这个案列

- 付款人：张三 120块
- 收款人：张三 118块，李四 2块

张三的120，转118块给自己，转2块给李四，对应到交易里面，就是这笔交易有1个输入，2个输出！

下面来一个多输入，多输出的案例

考虑如下场景：用户A和用户B之间发生了一个交易T3，A 向 B 转 100 元。 A的100元，来自T1：C向A转的80元 + T2：D向A转的30元（共110元，但A只转了100元给B，10元找零返回给A的账号）。 同理，C向A转的这80元，来自用户E、F的某次交易...... D向A转的这30元，来自用户E的某次交易......

这个交易就有2个输入，2个输出： 2个输入（也就是2个UTXO）： T1: C向A转的80元 T2：D向A转的30元

2个输出： B：100元 A：10元（找零）

**当你理解上面的例子时，我们再来说一下UTXO，理解上面的例子对你理解UTXO会特别有帮助。**

- 比特币的交易中不是通过账户的增减来实现的，而是一笔笔关联的输入/输出交易事务。
- 每一笔的交易都要花费“输入”，然后产生“输出”，这个产生的“输出”就是所谓的“未花费过的交易输出”，也就是UTXO。每一笔交易事务都有一个唯一的编号，称为交易事务ID，这是通过哈希算法计算而来的，当需要引用某一笔交易事务中的“输出”时，主要提供交易事务ID和所处“输出”列表中的序号就可以了。
- 由于没有账户的概念，因此当“输入”部分的金额大于所需的“输出”时，必须给自己找零，这个找零也是作为交易的一部分包含在“输出”中。
- 旧的 UTXO不断消亡，新的UTXO不断产生。所有的UTXO，组成了UTXO Set 的数据库，存在于每个节点
- 任何1笔 UTXO，有且仅可能被1个交易花费1次
- 1 个 UTXO，具有如下的表达形式： 1 个 UTXO = 1个Transaction ID + Output Index

### 3.2 **UTXO模型的区块链钱包余额形式**

深刻理解了UTXO的概念，钱包就很容易理解了，某个人的钱包的余额 = 属于他的UTXO的总和；在这里，你会发现一个不同于现实世界的“银行”里的一个概念，在银行里，会存储每个账号剩余多少钱。但这里，我们存储的并不是每个账号的余额，而存的是1笔笔的交易，也就是1 笔笔的UTXO，每个账户的余额是通过UTXO计算出来的，而不是直接存储余额。

### **3.3.图说 UTXO**

![img](https://thewebthree.xyz/media/editor/123123123_20241012115826044529.png)

# **二. Bitcoin 钱包地址类型**

Bitcoin 钱包地址有几种不同的类型，每种类型都有其特定的用途和特点。主要的几种类型包括：

- P2PKH（Pay-to-PubKeyHash）地址：
- 格式：以1开头，例如，1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa。
- 特点：这是最传统和最常见的地址类型，广泛用于比特币的早期交易。
- 优点：兼容性好，几乎所有钱包和交易所都支持。
- 缺点：随着时间的推移，这种地址类型的使用效率较低，交易费用可能会较高。
- P2SH（Pay-to-Script-Hash）地址：
- 格式：以3开头，例如，3J98t1WpEZ73CNmQviecrnyiWrnqRhWNLy。
- 特点：这种地址允许更复杂的交易脚本，例如多重签名地址。
- 优点：支持更复杂的交易和脚本，安全性更高。
- 缺点：创建和管理比P2PKH地址更复杂。
- Bech32（SegWit）地址：
- 格式：以 bc1 开头，例如，bc1qar0srrr7xfkvy5l643lydnw9re59gtzzwfvenl。
- 特点：这是比特币改进提案BIP-0173中引入的新地址格式，旨在提高交易效率和减少费用。
- 优点：交易费用更低，处理速度更快，且有助于减少交易体积。
- 缺点：并非所有的钱包和交易所都支持这种地址类型，尽管支持率在逐步增加。
- Bech32m
- 格式：P2TR（Pay-to-Taproot）和使用 Bech32m 编码。P2TR 地址以“bc1p”开头
- 特点
- Bech32m 是基于比特币改进提案（BIP-350）设计的，主要用于生成更具鲁棒性的地址。它将地址表示为一串以字母和数字组成的字符串（不区分大小写），确保不会出现混淆字符。
- 与 Bech32 的区别在于校验和的算法不同，Bech32m 使用了新的校验和常数 0x2bc830a3，这一改动提高了校验的准确性，并且能够避免常见的人为错误。
- Bech32m 主要用于 Taproot 升级，为比特币未来的扩展性而设计。
- 优点：
- Bech32m 格式非常注重防止用户在手动输入地址时的复制和输入错误。通过精确的校验和设计，能够高效地检测和纠正错误输入
- Bech32m 编码不区分大小写，避免了用户在输入地址时因为大小写混淆而犯错误，提升了使用体验。
- Bech32m 使用了一种简洁、易于理解的格式，长度相对固定，使用的字符集限制在 32 个字符，避免了难以区分的字符（如 1 和 l、0 和 O），使得地址较为直观。
- Bech32m 可以检测单个字符的错误和交换错误，进一步减少手动输入地址的风险。
- 缺点：平台兼容性问题

每种地址类型都有其特定的应用场景和优缺点，用户可以根据自己的需求选择合适的地址类型来存储和交易比特币

# **四.比特币共识算法详解**

比特币的工作量证明（Proof of Work，PoW）共识算法是确保网络去中心化、安全性和交易有效性的核心机制。该算法通过复杂的计算任务让矿工竞争记账权，并通过难度调整机制维持区块生成时间的稳定。下面将详细介绍比特币PoW共识算法的运作原理、计算公式和难度调整机制。总之，比特币的工作量证明（PoW）共识算法通过要求矿工解决复杂的哈希难题来确保区块链的安全性和去中心化。难度调整机制确保区块生成速度相对稳定，而 PoW 的设计使得对区块链的攻击需要极高的计算资源，从而保证了比特币网络的安全性。

## **1.比特币 PoW 共识算法基本原理**

在比特币网络中，每个矿工都需要解决一个数学难题，即通过计算找到一个哈希值，该哈希值必须小于一个给定的目标值。这个目标值由网络设定，并根据网络整体的计算能力进行调整。挖矿的目标是通过反复尝试不同的“Nonce”（随机数）来找到符合条件的哈希值，从而获得区块打包权和区块奖励。

## **2.区块哈希计算公式**

矿工通过对区块头进行哈希运算来生成哈希值，区块头的内容包括：

- 前一个区块的哈希值
- 当前区块中的交易的默克尔树根
- 时间戳
- 当前难度
- Nonce（矿工试图找到的随机数）

使用SHA-256算法进行双重哈希计算：

```
Hash = SHA-256(SHA-256(Block_header + Nonce))
```

其中：

- Block_header 包括区块头信息，如前一个区块的哈希值、交易的默克尔树根、时间戳等。
- Nonce 是矿工尝试寻找的值，用来使得哈希结果满足难度要求。
- SHA-256 是比特币使用的哈希算法，结果是一个256位的二进制数。

矿工需要找到一个 Nonce 使得哈希结果符合以下条件：

![img](https://thewebthree.xyz/media/editor/20241012120347_20241012120408588954.png)

## **3.难度与目标值的关系**

比特币网络中的挖矿难度是通过目标值来表示的。目标值是矿工需要找到的哈希值的上限，难度越高，目标值越低，找到符合条件的哈希值的难度就越大。

**目标值公式**

目标值与难度成反比关系，可以用以下公式表示：

![img](https://thewebthree.xyz/media/editor/20241012120445_20241012120506780911.png)

其中：

- Max_Target 是比特币网络中难度为1时的最大目标值，通常为 2224−12^{224} - 12224−1 或者用科学计数法表示为约 1.16×10771.16 \times 10^{77}1.16×1077。
- Difficulty 是当前的挖矿难度系数。

目标值越低，矿工找到一个合格哈希值的概率越低，从而提高挖矿的计算难度。

**难度公式**

比特币的挖矿难度是一个相对值，表示找到一个满足目标哈希值的计算难度。它是根据网络整体的计算能力和出块时间进行调整的。

难度调整的公式为：

\text{Difficulty} = \frac{\text{Max\_Target}}{\text{Current\_Target}}

每2016个区块（约两周）比特币网络会调整一次难度。难度调整的目的是为了保证平均每10分钟生成一个新区块。

## **4.难度调整机制**

比特币的难度调整机制确保了出块时间的稳定性。比特币的设计目标是大约每10分钟产生一个区块。如果网络的计算能力（哈希率）上升，区块生成速度可能会快于10分钟，此时难度会增加；如果哈希率下降，区块生成速度减慢，难度则会降低。

难度每2016个区块（大约两周）调整一次，调整公式为：

![img](https://thewebthree.xyz/media/editor/20241012120558_20241012120627933858.png)

其中：

- Time_for_Last_2016_Blocks 是生成前2016个区块实际花费的时间。
- 2016 × 10 minutes 是理想情况下生成2016个区块所需的时间（两周）。

如果实际时间大于两周，说明区块生成速度变慢，难度会降低；如果时间小于两周，难度则会提高。

## **5.比特币 PoW 安全性**

PoW 提供了强大的安全性。攻击者要想修改区块链上的交易记录，不仅需要重写该区块的哈希值，还需要重写之后的所有区块，这意味着需要付出巨大的计算资源。这种设计使得修改历史记录的成本极高，确保了区块链的不可篡改性。

此外，矿工的哈希计算是通过消耗实际计算资源（电力、硬件等）完成的，这使得攻击成本非常高，确保了网络的安全性。

## **6.哈希率与难度的关系**

哈希率（Hash rate）是指整个比特币网络每秒钟进行的哈希运算次数。哈希率越高，矿工找到符合条件的哈希值的概率就越高。因此，比特币网络通过动态调整难度来应对哈希率的变化，确保区块生成时间保持在10分钟左右。

## **7.具体难度示例**

假设比特币当前难度为 10^12，而最大目标值 Max_Target 为 2224−12^{224} - 12224−1，那么当前的目标值可以计算为：

![img](https://thewebthree.xyz/media/editor/20241012120642_20241012120738377847.png)

这意味着矿工需要找到的哈希值必须小于这个目标值。

# **五.比特币脚本编程**

比特币脚本编程是比特币区块链的核心组成部分，它定义了如何验证和执行比特币交易。比特币的脚本是一种基于堆栈的编程语言，用来处理比特币的交易验证逻辑。比特币脚本的编写和使用并不像智能合约那样复杂，它主要用于验证交易的合法性，而不是执行复杂的程序逻辑。

以下是比特币脚本编程的一些基本概念和特点：

## **1.堆栈式语言**

比特币脚本使用堆栈（stack）来进行操作。每个操作码（opcode）会从堆栈中获取输入，然后对其进行处理，并将结果放回堆栈中。堆栈语言是一种后缀表达式语言，执行顺序是按照指令顺序来进行。

## **2.不可图灵完备**

比特币脚本并不是图灵完备的编程语言。这意味着它不能执行循环或递归，目的是确保脚本的执行是确定且有限的，从而避免像以太坊那样需要“Gas”机制来防止无限循环。

## **3.脚本结构**

比特币交易脚本一般分为两个部分：

- **锁定脚本（ScriptPubKey）**：规定接收方要花费比特币时需要满足的条件。
- **解锁脚本（ScriptSig）**：由花费者提供，证明他们有权花费这个比特币，通常是一个签名和公钥。

当一个比特币交易被广播时，比特币客户端会先执行解锁脚本，然后执行锁定脚本。如果整个执行流程成功且堆栈顶端有一个 True 值，那么交易被认为是合法的。

## **4.常见操作码**

比特币脚本包含一系列操作码，常见的操作码包括：

- **OP_DUP**：复制栈顶的元素。
- **OP_HASH160**：对栈顶的元素进行哈希操作。
- **OP_EQUALVERIFY**：验证两个栈顶元素是否相等。
- **OP_CHECKSIG**：检查提供的签名是否有效。

## **5.脚本的应用**

- **P2PKH（Pay-to-PubKey-Hash）**：最常见的交易类型，要求提供公钥和签名以解锁比特币。
- **P2SH（Pay-to-Script-Hash）**：允许使用复杂的自定义脚本，交易的条件由锁定脚本来定义。
- **多重签名（Multisig）**：需要多个签名来共同花费比特币，通常用于共享控制钱包。

## **6.示例**

以下是一个典型的 P2PKH 脚本示例：

**锁定脚本（ScriptPubKey）：**

- OP_DUP OP_HASH160 OP_EQUALVERIFY OP_CHECKSIG
- OP_DUP：复制栈顶的公钥。
- OP_HASH160：对公钥进行哈希，得到公钥的哈希值。
- ：预期的公钥哈希值。
- OP_EQUALVERIFY：验证两个哈希值是否相等。
- OP_CHECKSIG：检查签名是否有效。

**解锁脚本（ScriptSig）：**

- 
- 提供解锁这个比特币所需的签名和公钥。

比特币脚本是强大的工具，但由于其有限的表达能力，它主要用于交易验证和基本的多签名机制。想要编写更复杂的逻辑，通常需要借助二层协议或其他区块链平台。

详情请看：https://x.com/seek_web3/status/1810260720346665123

# **六.隔离见证**

隔离见证（Segregated Witness，简称SegWit）是比特币协议的一项升级，旨在解决区块链中的几个问题，特别是交易的扩展性和交易延展性问题。它最初由比特币核心开发者 Pieter Wuille 提出，并于 2017 年通过软分叉被引入比特币网络。

## **1.隔离见证的主要特点和作用**

- **提升区块容量**：隔离见证将交易签名数据（见证数据）从交易主体中分离出来，并放置在区块的另一部分中。这样可以有效地提升区块的有效容量，而不需要改变区块的实际大小限制。例如，一个 1MB 的区块通过隔离见证可以有效容纳更多的交易数据。
- **解决交易延展性问题**：在隔离见证引入之前，比特币的交易 ID 是基于交易的所有内容（包括签名数据）生成的。这意味着有人可以在不改变交易内容的情况下，修改签名的形式，导致交易 ID 改变，这种现象被称为交易延展性（Transaction Malleability）。隔离见证通过将签名数据与交易数据分离，解决了这一问题，使得交易 ID 不会因为签名的改变而受到影响。
- **为闪电网络铺平道路**：由于隔离见证解决了交易延展性的问题，它为闪电网络（Lightning Network）等 Layer 2 扩展解决方案铺平了道路。闪电网络依赖于比特币链上交易的可靠性和不可修改性来进行链下微支付。
- **提高安全性和降低交易费**：隔离见证的引入使得更多的交易能够被打包到区块中，从而降低了整体的交易费。此外，隔离见证还通过优化签名验证过程，提高了网络的安全性和效率。

在比特币中，隔离见证交易的地址通常以 "bc1" 开头（称为 bech32 地址格式），它们比传统的 P2PKH（以 "1" 开头）和 P2SH（以 "3" 开头）的地址更高效。

## **2.隔离见证的地址版本**

## **2.1. Bech32：隔离见证V0地址格式**

隔离见证（SegWit）是 2017 年 8 月发生的的比特币协议更新，SegWit 有效地将签名数据或见证数据与比特币交易分开或隔离，这样做使比特币区块能够容纳更多交易，从而提高比特币网络的可扩展性。此外，将签名数据与比特币交易分离为第二层扩展解决方案（Layer 2）提供了机会，如闪电网络。

Bech32 是一个与 SegWit 完全兼容的比特币地址。 许多人将 Bech32 地址称为 bc1 地址，因为它们的地址字符串总是以bc1开头。Bech32作为比特币改进提案（BIP-173）的一部分，在应用之前，比特币使用base58地址和截断的双SHA256校验和。

但是，这种实现有一些缺点，因为它使用混合大小写字母，导致base58 地址很难输入，并且在发送比特币时很容易出现输入错误。 想象一下，尝试正确输入 1BvBMSEYstWetqTFn5Au4m4GFg7xJaNVN2 而无需复制和粘贴， 会发现是一件很困难的事。此外，base58 地址用二维码来表示需要大量存储空间，并且解码也相对复杂且缓慢。将所有这些问题与双SHA256 校验和所需的时间较长结合起来，就会开始明白为什么需要切换。

### **2.2.产生Bech32地址**

Bech32 地址是从公钥创建的，如下所示：

- 对一个压缩的公钥（0x02 或 0x03 后跟 32 字节的 X 坐标值）： 0279be667ef9dcbbac55a06295ce870b07029bfcdb2dce28d959f2815b16f81798执行执行 SHA-256 哈希运算，得到0f715baf5d4c2ed329785cef29e562f73488c8a2bb9dbc5700b361d54b9b0554
- 再对哈希结果进行RIPEMD-160散列：751e76e8199196d454941c45d1b3a323f1433bd6
- 第 2 步的结果是一个 8 位无符号整数数组（基数 2^8=256），Bech32 编码将其转换为一个 5 位无符号整数数组（基数 2^5=32），因此我们“挤压”要获取的字节，如调用如下函数convertbits('751e76e8199196d454941c45d1b3a323f1433bd6', 8, 5)。

```bash
def convertbits(data, frombits, tobits, pad=True):
    """General power-of-2 base conversion."""
    acc = 0
    bits = 0
    ret = []
    maxv = (1 << tobits) - 1
    max_acc = (1 << (frombits + tobits - 1)) - 1
    for value in data:
        if value < 0 or (value >> frombits):
            return None
        acc = ((acc << frombits) | value) & max_acc
        bits += frombits
        while bits >= tobits:
            bits -= tobits
            ret.append((acc >> bits) & maxv)
    if pad:
        if bits:
            ret.append((acc << (tobits - bits)) & maxv)
    elif bits >= frombits or ((acc << (tobits - bits)) & maxv):
        return None
    return ret
```

- 得到5位无符号整数数组01110 10100 01111 00111 01101 11010 00000 11001 10010 00110 01011 01101 01000 10101 00100 10100 00011 10001 00010 11101 00011 01100 11101 00011 00100 01111 11000 10100 00110 01110 11110 10110，十六进制表示0e140f070d1a001912060b0d081504140311021d030c1d03040f1814060e1e16
- 对结果添加隔离见证版本号（Segwitness version）字节（当前版本为0），得到000e140f070d1a001912060b0d081504140311021d030c1d03040f1814060e1e16
- 使用上一步结果得到的数据和 HRP（主网为 bc，测试网为 tb），计算校验和0c0709110b15，附加到上一步结果，得到000e140f070d1a001912060b0d081504140311021d030c1d03040f1814060e1e160c0709110b15
- 将每个值映射到 Bech32的字符集（qpzry9x8gf2tvdw0s3jn54khce6mua7l，如00 -> q, 0e -> w,...）得到qw508d6qejxtdg4y5r3zarvary0c5xw7kv8f3t4

![img](https://thewebthree.xyz/media/editor/2312312312312_20241012120903672098.png)

- 最终得到一个 Bech32_encoded地址，bc1qw508d6qejxtdg4y5r3zarvary0c5xw7kv8f3t4

其中，bech32地址有四个组成部分：

- 人类可读部分 HRP
- 数字1作为分隔符
- base32编码后的字符串，包含有效的地址数据
- 使用 BCH 算法编码生成的的 6 字符 base-32 编码纠错码

支持 Bech32可以减小发送和接收比特币时出错的概率， 因为 Bech32 地址完全小写，而不是混合大小写，用户可以更轻松地共享并输入它们。如果用户在输入地址时确实出错，Bech32 地址还可以让您别哪些字符可能不正确。

### **2.3.Bech32m概览**

BIP173 定义了 Bech32 的通用校验和 base 32 编码格式，它用于版本 0（P2WPKH 和 P2WSH）的隔离见证输出和其他应用程序。但Bech32 有一个意想不到的缺陷：只要最后一个字符是 p，在它前面插入或删除任意数量的 q 字符，都不会使校验和无效。由于存在对两个特定长度的限制，这不会影响SegWit 版本 0 地址的现有使用，但可能会影响使用 Bech32 编码的未来使用，其他应用程序若使用bech32地址也可能会受到影响。

Bech32m 是Bech32的一个优化变体，可缓解这个插入缺陷和相关的问题，并修改了 BIP173 以将 Bech32m 用于版本 1 及更高版本的原生隔离见证输出，而Bech32 仍然用于版本 为0 的隔离见证输出。

**Bech32m**

Bech32m 修改了 Bech32 规范的校验和，用 0x2bc830a3 替换了最后异或到校验和中的常数 1。

```bash
BECH32M_CONST = 0x2bc830a3

def bech32m_polymod(values):
  GEN = [0x3b6a57b2, 0x26508e6d, 0x1ea119fa, 0x3d4233dd, 0x2a1462b3]
  chk = 1
  for v in values:
    b = (chk >> 25)
    chk = (chk & 0x1ffffff) << 5 ^ v
    for i in range(5):
      chk ^= GEN[i] if ((b >> i) & 1) else 0
      # k(x) = {29}x^5 + {22}x^4 + {20}x^3 + {21}x^2 + {29}x + {18}
      # {2}k(x) = {19}x^5 +  {5}x^4 +     x^3 +  {3}x^2 + {19}x + {13}
      # {4}k(x) = {15}x^5 + {10}x^4 +  {2}x^3 +  {6}x^2 + {15}x + {26}
      # {8}k(x) = {30}x^5 + {20}x^4 +  {4}x^3 + {12}x^2 + {30}x + {29}
      # {16}k(x) = {21}x^5 +     x^4 +  {8}x^3 + {24}x^2 + {21}x + {19}
  return chk

def bech32m_hrp_expand(s):
  return [ord(x) >> 5 for x in s] + [0] + [ord(x) & 31 for x in s]

def bech32m_verify_checksum(hrp, data):
  return bech32m_polymod(bech32m_hrp_expand(hrp) + data) == BECH32M_CONST

def bech32m_create_checksum(hrp, data):
  values = bech32m_hrp_expand(hrp) + data
  polymod = bech32m_polymod(values + [0,0,0,0,0,0]) ^ BECH32M_CONST
  return [(polymod >> 5 * (5 - i)) & 31 for i in range(6)]
```

Bech32 的所有其他方面保持不变，包括其人类可读部分（HRP)，可以使用以下代码编写同时解码 Bech32 和 Bech32m 的组合函数。它返回 None 表示失败，或 BECH32 / BECH32M 枚举值之一以指示根据相应标准进行解码。

```bash
class Encoding(Enum):
    BECH32 = 1
    BECH32M = 2

def bech32_bech32m_verify_checksum(hrp, data):
    check = bech32_polymod(bech32_hrp_expand(hrp) + data)
    if check == 1:
        return Encoding.BECH32
    elif check == BECH32M_CONST:
        return Encoding.BECH32M
    else:
        return None
```

SegWit 版本 0 输出（特别是 P2WPKH 和 P2WSH 地址）将继续使用 BIP173 中指定的 Bech32，隔离见证输出版本 1 到 16 的地址将使用 Bech32m。同样，编码的所有其他方面保持不变，包括bc（HRP）。要解码比特币网络地址，客户端软件应该使用 Bech32 和 Bech32m 解码器进行解码，或者使用同时支持两者的解码器。在这两种情况下，地址解码器都必须验证编码是否与解码的隔离见证版本（版本 0 的为 Bech32，其他版本的为 Bech32m）相匹配。如进行以下检查。

```bash
def decode(hrp, addr):
    hrpgot, data, spec = bech32_decode(addr)
    if hrpgot != hrp:
        return (None, None)
    decoded = convertbits(data[1:], 5, 8, False)
    # Witness programs are between 2 and 40 bytes in length.
    if decoded is None or len(decoded) < 2 or len(decoded) > 40:
        return (None, None)
    # Witness versions are in range 0..16.
    if data[0] > 16:
        return (None, None)
    # Witness v0 programs must be exactly length 20 or 32.
    if data[0] == 0 and len(decoded) != 20 and len(decoded) != 32:
        return (None, None)
    # Witness v0 uses Bech32; v1 through v16 use Bech32m.
    if data[0] == 0 and spec != Encoding.BECH32 or data[0] != 0 and spec != Encoding.BECH32M:
        return (None, None)
    # Success.
    return (data[0], decoded)
```

### **2.4.总结**

Bech32m 通过更改Bech32编码方案中使用的常量来消除此漏洞，因此更安全。Bech32m 被提议作为 SegWit 版本 1（即Taproot）地址的编码方案，它将由 Taproot 升级引入。在引入后，为隔离见证输出生成地址时，如果其见证版本为 0，则使用 Bech32 对其进行编码；如果其见证版本为 1 或更高，则使用 Bech32m 对其进行编码。

# **七. 读懂 Taproot 全流程**

## **1.Taproot 概述**

比特币改进提案（BIPs）是为比特币引入新功能和信息的设计文档，而 Taproot 升级则是三个 BIPs 的汇编，这三个 BIPs 分别是 Schnorr 签名(BIP 340)、Taproot (BIP 341)和TapScript (BIP 342)，这三个升级统称为 BIP Taproot，它将为比特币带来了更高效、更灵活、更私密的传输方式，其核心在于使用了 Schnorr 签名和 Merkel 抽象语法树(MAST)。

![img](https://thewebthree.xyz/media/editor/343434343_20241012121110217535.png)

Taproot的原理，简单来说，就是定义了一种输出和两种花费路径。如上图所示，有Alice和Bob两个参与者，Taproot的运作过程如下:

- 将Alice和Bob的公钥聚合为： C=P_A+P_B
- 加入MerkleRoot，公钥聚合为：P=C+H(C||MerkleRoot)G，其中 H(C||MerkleRoot) 表示C和MerkleRoot的组合hash
- 锁定脚本中填入聚合公钥P，格式类似Segwit：[ver] [P]。ver表示版本号，Taproot中ver=1。
- 花费路径有两个，二选一：
- 签名模式：Alice和Bob全部签名产生聚合签名，填入见证脚本。利用聚合公钥P,对签名进行验证后即可花费。
- 脚本模式：Alice和Bob，有一个拒绝签名，可以走脚本模式。此时Alice想要完成花费，那么见证脚本中需要填入：符合Script 1的执行数据D, Script 1, C, Hash 2 。为了验证签名，首先利用Script 1, Hash2，计算MerkleRoot，然后验证 P==C+H(C||MerkleRoot)G 是否成立，最后构建完整脚本D||Script 1并执行脚本，验证结果是否为真。当上述验证通过后，即可完成花费。

Taproot按照签名模式进行花费时，多个参与方和单个参与方在区块链上看起来都长得是一样的，所以许多区块链分析将不可用，从而为所有 Taproot 用户保留隐私。与此同时，Taproot的脚本花费模式让用户可以实现复杂的支出条件。Taproot可以有效压缩交易脚本字节数。签名模式下随着参与者增加，EDSA交易脚本大小线性增长，Taproot交易脚本大小保持不变。脚本模式下随着脚本数量的增加，EDSA交易脚本大小线性增长，Taproot交易脚本大小对数增长。

### **1.1. Huffman Tree**

给定N个权值作为N个叶子结点，构造一棵二叉树，若该树的带权路径长度达到最小，称这样的二叉树为最优二叉树，也称为哈夫曼树(Huffman Tree)。哈夫曼树是带权路径长度最短的树，权值较大的结点离根较近。

![img](https://thewebthree.xyz/media/editor/34545_20241012121136732968.png)

哈夫曼树的构造过程是利用贪心的思想，每次选择权重最小的两个结点组合成新的节点，加入到原始集合，重复上述过程，直至结束。如上图所示，存在权重集合为 (1, 2, 3, 4, 5) 的5个结点，构造哈夫曼树的过程如下：

- 从集合中选择权重最小的 1, 2 结点，组合成权重为3的结点，集合变成 (3,3,4,5)
- 从集合中选择权重最小的 3, 3 结点，组合成权重为6的结点，集合变成 (4, 5, 6)
- 从集合中选择权重最小的 4, 5 结点，组合成权重为9的结点，集合变成 (6, 9)
- 从集合中选择权重最小的 6, 9 结点，组合成权重为15的结点，集合变成 (15) , 构造过程结束

可以看出，在哈夫曼树中，权重越大的结点离根越近，权重越小的结点离根越远。

### **1.2.Huffman Tree在Taproot的应用**

Taproot相比于ECDSA多签算法，一大优势是Schnorr聚合签名可以将多个签名数据压缩合并成单个聚合签名。使用聚合签名技术后，交易脚本的字节数大大减少，可以有效减少交易费用的支出。当我们按照脚本模式进行花费时，借助MAST的树形结构，交易脚本大小随着脚本数量对数增长。然而利用Huffman Tree，可以通过改进MAST的构造过程，帮助我们进一步减少脚本花费模式下见证脚本的字节数，最终达到降低交易手续费的目的。

![img](https://thewebthree.xyz/media/editor/677876_20241012121212226787.png)

前文提到，当Taproot按照脚本模式进行花费时，需要提供脚本在MAST中的Proof。如上图，当我们想通过script_A进行花费，见证脚本中需要提供：

- 符合script_A的执行数据D
- script_A
- P
- TaggedHash(B), TaggedHash(C) TaggedHash表示带标签的hash，固定长度32字节，使用带标签的hash目的是减少hash碰撞

忽略前两项的字节数，可以看出，最后一项的字节数可以表示为 32*(d-1) ，d=3表示 script_A在MAST中的高度。换句话说，最后一项的字节数与脚本在MAST中高度线性相关。因此，对于 script_A, script_B, script_C 三个脚本，我们可以根据脚本使用频率赋予权重，构造哈夫曼树，作为MAST。最终，根据Huffman的特性，使用频率越高的 script , 在哈夫曼树中的高度越低，见证脚本中字节数越少，交易手续费越低。

总而言之，交易手续费与交易脚本的字节数息息相关。Taproot的聚合签名可以帮助我们有效减少按签名模式花费时的交易脚本字节数，但是利用Huffman构造MAST可以进一步帮助我们减少按脚本模式花费时的交易脚本字节数。

## **2.taproot交易过程**

Taproot的核心是由Schnorr 签名和MAST抽象语法树组成，Taproot交易过程本文主要从Taproot公钥的创建和Taproot的花费模式两个方面阐述。

### **2.1.创建Taproot公钥**

为了创建Taproot公钥，首先需要了解Taproot聚合公钥和聚合签名的产生过程。目前关注度较高的相关研究包括MuSig1和MuSig2。相比于MuSig2两轮通信，MuSig1最大的缺点在于它创建签名需要三轮通信，而每一轮通信都由来回传递的消息组成。由于本文未涉及网络间通信，因此这里主要讨论的是聚合公钥和聚合签名的基本生成过程。

**聚合公钥**

![img](https://thewebthree.xyz/media/editor/hgjgh_20241012121238125051.png)

从上图可以看出聚合公钥的生成过程可以分三步：1）相互传递公钥，并对所有公钥拼接进行一次聚合hash，生成c_all。 2）c_all和i的公钥拼接hash后生成因子c_i。 3) 根据因子c_i进行线性组合得到聚合公钥P_agg。

```bash
privkey1, pubkey1 = generate_key_pair(sha256(b'key0'))
privkey2, pubkey2 = generate_key_pair(sha256(b'key1'))
privkey3, pubkey3 = generate_key_pair(sha256(b'key2'))
pubkey_list = [pubkey1, pubkey2, pubkey3]

# 1) Aggregate hash of all public keys
pubkey_list_sorted = sorted([int.from_bytes(key.get_bytes()[1:], 'big') for key in pubkey_list])
L = b''
for px in pubkey_list_sorted:
    L += px.to_bytes(32, 'big')
Ln = hashlib.sha256(L).digest()

# 2) 3) Calculate the factor and generate the aggregate public key
musig_c = {}
aggregate_key = 0
for key in pubkey_list:
    musig_c[key] = hashlib.sha256(Ln + key.get_bytes()[1:]).digest()
    aggregate_key += key.mul(musig_c[key])
```

### **2.2.聚合签名**

![img](https://thewebthree.xyz/media/editor/56456456456456_20241012121256340949.png)

聚合签名的生成过程上图显示需要进行三轮通信，主要分成两大步：1）生成nonce并线性聚合生成R_agg。 2）各方利用私钥生成Schnorr签名并进行聚合，得到最终的聚合签名（R_agg, s1+s2+s3）。

```bash
# 1) generate nonce and aggregate
k1, R1 = generate_key_pair()
k2, R2 = generate_key_pair()
k3, R3 = generate_key_pair()
R_agg, negated = aggregate_schnorr_nonces([R1, R2, R3])

if negated:
    k1.negate()
    k2.negate()
    k3.negate()

msg = sha256(b'msg')

# 2) Aggregate signature
s1 = sign_musig(privkey1*musig_c[pubkey1], k1, R_agg, aggregate_key, msg)
s2 = sign_musig(privkey2*musig_c[pubkey2], k2, R_agg, aggregate_key, msg)
s3 = sign_musig(privkey3*musig_c[pubkey3], k3, R_agg, aggregate_key, msg)
sig = aggregate_musig_signatures([s1, s2, s3], R_agg)

# Verify the correctness of the signature
assert aggregate_key.verify_schnorr(sig, msg)
```

### **2.3.引入MAST抽象语法树**

![img](https://thewebthree.xyz/media/editor/xcxcc_20241012121320615850.png)

如上图所示，Taproot公钥主要由两部分组成，包括聚合公钥P和MAST结构形成的公钥tG。假设P是Alice,Bob,Charlie的聚合公钥，script_A,script_B,script_C是Alice,Bob,Charlie相关的脚本。那么，Taproot公钥创建过程如下：

- Alice,Bob和Charlie各自生成公私钥。

```bash
privkey_alice, pubkey_alice = generate_key_pair()
privkey_bob, pubkey_bob = generate_key_pair()
privkey_charlie, pubkey_charlie = generate_key_pair()
```

- 公钥聚合成pubkey_agg，并调整私钥，用于以后的签名。

```bash
c_map, pubkey_agg = generate_musig_key([pubkey_alice, pubkey_bob, pubkey_charlie])

privkey_alice_c = privkey_alice * c_map[pubkey_alice]
privkey_bob_c = privkey_bob * c_map[pubkey_bob]
privkey_charlie_c = privkey_charlie * c_map[pubkey_charlie]
```

- 创建脚本script_A,script_B,script_C

```bash
scriptA = CScript([pubkey_alice.get_bytes(), OP_CHECKSIG])
scriptB = CScript([pubkey_bob.get_bytes(), OP_CHECKSIG])
scriptC = CScript([pubkey_charlie.get_bytes(), OP_CHECKSIG])
```

- 构建MAST抽象语法树，计算MAST结构对应的私钥taptweak。上图中TaggedHash表示带标签的hash,固定长度32字节，计算方式是TaggedHash(tag, x) = sha256(sha256(tag) + sha256(tag) + x)；ver表示Tapscript版本号，当前值为0xc0；size表示scirpt的字节数；A&B表示A,B字典排序后按字节拼接。

```bash
TAPSCRIPT_VER = bytes([0xc0])

# 1) Compute TapLeaves A, B and C
# Method: ser_string(data) is a function which adds compactsize to input data.
hash_inputA = TAPSCRIPT_VER + ser_string(scriptA)
hash_inputB = TAPSCRIPT_VER + ser_string(scriptB)
hash_inputC = TAPSCRIPT_VER + ser_string(scriptC)
taggedhash_leafA = tagged_hash("TapLeaf", hash_inputA)
taggedhash_leafB = tagged_hash("TapLeaf", hash_inputB)
taggedhash_leafC = tagged_hash("TapLeaf", hash_inputC)

# Method: Returns tapbranch hash. Child hashes are lexicographically sorted and then concatenated.
def tapbranch_hash(l, r):
    return tagged_hash("TapBranch", b''.join(sorted([l, r])))

# 2) Compute Internal node TapBranch AB
# Method: use tapbranch_hash() function
internal_nodeAB = tapbranch_hash(taggedhash_leafA, taggedhash_leafB)

# 3) Compute TapTweak
rootABC = tapbranch_hash(internal_nodeAB, taggedhash_leafC)
taptweak = tagged_hash("TapTweak", pubkey_agg.get_bytes() + rootABC)
print("TapTweak:", taptweak.hex())
```

- 根据公式Q=P+tG合成taproot公钥,并生成segwit_address用于下文交易。

```bash
# generate Taproot pubkey
taptweak_pubkey = pubkey_agg.tweak_add(taptweak)

# generate segwit address
taptweak_pubkey_b = taptweak_pubkey.get_bytes()
taptweak_pubkey_b = bytes([taptweak_pubkey_b[0] & 1]) + taptweak_pubkey_b[1:]
segwit_version = 1
segwit_address = program_to_witness(segwit_version, taptweak_pubkey_b)
print('Segwit address:', segwit_address)
```

- 向Taproot地址转账50个btc

```bash
# Start node
test = util.TestWrapper()
test.setup()
node = test.nodes[0]

# Generate coins and create an output
tx = node.generate_and_send_coins(segwit_address)
print("Transaction {}, output 0\nsent to {}\n".format(tx.hash, segwit_address))
```

### **2.4.Taproot花费**

为了完成从上述Taproot地址向Bob个人转账0.5个btc,有两种支付途径：一种是Alice，Bob，Charlie都进行签名后形成聚合签名，完成向Bob的转账；另一种是通过MAST结构中的script向Bob进行转账。

- 创建交易原文，填充接受方地址，转账数量等数据。

```bash
spending_tx=CTransaction()

spending_tx.nVersion =2

spending_tx.nLockTime=0


outpoint = CoutPoint(int(tx.hash，16)，0)
spending_tx_in=CTxIn(outpoint)
spending_tx.vin =[spending tx in]

scriptpubkey =bytes(cscript([op 1, pubkey alice.get bytes()]))


amount_sat=int(0.5*100000000)
dest_output =CTxOut(nValue=amount sat, scriptPubKey=scriptpubkey)
spending_tx.vout =[dest_output]


print("Spending transaction:\n{}".format(spending tx))
Spending transaction:
CTransaction(nVersion=2 vin=[CTxIn(prevout=CoutPoint(hash=102517bf877c74489c83d4b58ala22e067526b79288076afba n=0)scriptSig= nsequence=0)]vout=[CTxOut(nValue=0.50000000 scriptPubKey=7280a8f376ega82ba8e44f1dcf254a8517ae7160f41ea9'73334a)wit=CTxWitness()nLockTime=0)
```

- 按照第一种方式进行转账，首先需要Alice，Bob，Charlie各自生成nonce并进行聚合，然后各自利用私钥进行Schnorr签名，最后进行签名的聚合操作。因此，这种方式最终的见证脚本是一个单独的签名,固定长度64字节。

```bash
# 生成密钥对和随机数  
k_alice, R_alice = generate_key_pair()  
k_bob, R_bob = generate_key_pair()  
k_charlie, R_charlie = generate_key_pair()  

# 聚合随机数  
R_agg, negated = aggregate_schnorr_nonces([R_alice, R_bob, R_charlie])  

# 如果聚合后的随机数被拒绝，则反签名  
if negated:  
    k_alice.negate()  
    k_bob.negate()  
    k_charlie.negate()  

# 创建sighash  
sighash = TaprootSignatureHash(spending_tx, [tx.vout[0]], SIGHASH_ALL_TAPROOT, input_index=0)  

# 单独签名并聚合部分签名  
e = musig_digest(R_agg, taptweak_pubkey, sighash)  
s_alice = sign_musig(privkey_alice_c, k_alice, R_agg, taptweak_pubkey, sighash)  
s_bob = sign_musig(privkey_bob_c, k_bob, R_agg, taptweak_pubkey, sighash)  
s_charlie = sign_musig(privkey_charlie_c, k_charlie, R_agg, taptweak_pubkey, sighash)  

# 聚合签名  
sig_agg = aggregate_musig_signatures([s_alice, s_bob, s_charlie, e], R_agg)  

# 将聚合签名添加到交易见证中  
spending_tx.wit.vtxinwit.append(CTxInWitness([sig_agg]))
```

- 测试第一种花费组建的交易原文合法并发送交易

```bash
# Test mempool acceptance  
assert node.test_transaction(spending_tx)  

# send transaction  
txid = node.sendrawtransaction(hexstring=str(spending_tx.serialize().hex()), maxfeerate=0)  
print("Success!", txid)
```

- 按照第二种方式进行转账，假设是Alice通过script_A完成向Bob的转账，那么见证脚本需要包括：1）[Stack element(s) satisfying TapScript_A] 2）[TapScript_A] 3）[Controlblock c]。其中[Controlblock c]表示的是TapScript_A相关的proof,长度为33+32n。33个字节中的首字节是聚合公钥和Taproot版本号共同计算得出，剩下32个字节表示的是聚合公钥的x坐标。32n表示的是TapScript_A的proof，在本例中n=2，指的是taggedhash_leafB和taggedhash_leafC。

```bash
# 创建TapLeafA的签名哈希  
sighashA = TaprootSignatureHash(spending_tx,   
                                [tx.vout[0]],  
                                SIGHASH_ALL_TAPROOT,  
                                input_index=0,  
                                scriptpath=True,  
                                tapscript=scriptA)  

# 使用私钥生成签名  
signatureA = privkey_alice.sign_schnorr(sighashA)  

# 打印签名  
print("Signature for TapLeafA: {}\n".format(signatureA.hex()))  

# 聚合公钥的字节表示  
pubkey_agg_b = pubkey_agg.get_bytes()  

# 创建控制块  
Controlblock = bytes([pubkey_agg_b[0] & 0x01 | 0xc0]) + pubkey_agg_b[1:] + taggedhash_leafB + taggedhash_leafC  

# 向交易添加见证  
# 提示：见证栈对于脚本路径 - [满足tapscript的元素] [TapLeaf.script] [controlblock]  
# 提示：tapscript的控制块在control_map[TapLeaf.script]中  
witness_elements = [signatureA, scriptA, Controlblock]  
spending_tx.wit.vtxinwit.append(CTxInWitness(witness_elements))
```

- 测试第二种花费组建的交易原文合法并发送交易

```bash
# Test mempool acceptance  
assert node.test_transaction(spending_tx)  

# send transaction  
txid = node.sendrawtransaction(hexstring=str(spending_tx.serialize().hex()), maxfeerate=0)  
print("Success!", txid)
```

### **2.2.总结**

总的来看，Taproot交易主要关注的是一种输出和两种花费模式。一种输出使得无论是个人交易还是多签交易，锁定脚本中公钥是一致的，无法从形式上进行区分。两种花费模式使得我们可以用更少的字节，实现更复杂的交易过程。

## **3.Tapscript交易结构**

### **3.1.Tapscript**

Taproot 升级是三个 BIPs 的汇编，这三个 BIPs 分别是 Schnorr 签名(BIP 340)、Taproot (BIP 341)和TapScript (BIP 342)。 而Tapscript是Taproot升级的第三部分，是对 Schnorr 和 Taproot 进行的补充。Tapscript主要是对升级机制和操作码进行了改进。

Tapscript 通过使用操作码 OP_SUCCESS可以轻松实现不可预见的未来升级。操作码（Opcode）是比特币脚本语言的运算符，Tapscript 保留了适用于 v0 见证脚本的大部分操作码，对少量操作码进行了更新。Tapscript交易结构的变化主要来自于锁定脚本和见证脚本，本文将通过一个具体例子介绍Tapscript交易各个字段的组成。

### **3.2.操作码**

Tapscript中操作码的改变有：1）OP_CHECKSIG/OP_CHECKSIGVERIFY操作码由原来的验证ECDSA签名变成验证Schnorr签名；2）禁用OP_CHECKMULTISIG/ OP_CHECKMULTISIGVERIFY这两个多签操作码；3）增加操作码OP_CHECKSIGADD，取代原来的多签操作码。

由于签名验证是比特币脚本中 CPU 最密集的操作，因此上述操作码变化对于实现基于 Schnorr 多重签名方案相关的效率提升至关重要。OP_CHECKSIG/OP_CHECKSIGVERIFY的改变自然是为了Taproot 升级中Schnorr签名能够使用。OP_CHECKSIGADD这种多重签名操作码通过要求见证人为每个公钥提供有效或无效的签名，从而避免在 k-of-n 多重签名脚本中浪费每个公钥的签名验证操作。

传统的2-of-3多重签名交易脚本如下：

- script:2 [PK0] [PK1] [PK2] 3 OP_CHECKMULTISIG
- 可能的见证脚本：[sig2] [sig1]

使用 Tapscript，实现相同的多重签名策略，其中脚本是:

- Tapscript: [PK0] [OP_CHECKSIG] [PK1] [OP_CHECKSIGADD] [PK2] [OP_CHECKSIGADD] [2] [OP_NUMEQUAL]
- 可能的见证脚本:[sig2] [sig1] []

从上述脚本中可以看出，传统的多重签名sig和PK的映射关系未知。对于签名sig1来说，需要与PK0,PK1, PK2分别进行一次轮询验证才能确定sig1是否验证通过，sig2同理。而Tapscript为每一个公钥都提供了有效或无效的签名，签名有效时，通过OP_CHECKSIGADD操作码进行累加，最后只需验证有效签名的数量是否达到阈值判断签名是否通过。OP_CHECKSIGADD省略了传统多签验证中的轮询过程，加快了多签验证的速度。

### **3.3.交易结构**

Tapscript沿用隔离见证中的交易结构，由下面几个字段组成。Tapscript规定交易输入必须是隔离见证花费。也就意味着txins中的script_sig一般为空，而witness字段存在数据。本文通过一个具体的例子来说明各个字段的内涵。

```bash
nVersion  
marker  
flag  
txins  
txouts  
witness  
nLockTime
```

- 下文是一个Taproot地址转账到普通地址的交易原文。交易原文是16进制表示，每两个字符表示一个字节。Taproot地址由聚合公钥和MAST结构对应的公钥组成：Q=P+tG。这里P表示A,B,C三人的聚合公钥，计算公式P=pubkey_agg(PKA, PKB, PKC)。tG表示单独的脚本[PKA] [OP_CHECKSIG] [PKB] [OP_CHECKSIGADD] [PKC] [OP_CHECKSIGADD] [2] [OP_NUMEQUAL]作为MAST的root计算得到的公钥,计算公式t=tagged_hash(P||root)。

![img](https://thewebthree.xyz/media/editor/343434342312312312_20241012121406612300.png)

- 如下图所示，第一行表示字段名字，()中的数字表示对应字段的字节数，第二行表示字段在上述交易原文中的对应数据。nVersion表示交易结构的版本标识。02000000是小端模式，低位字节在前，因此实际值为00000002。 marker是一个值必须为00的字段，flag表示是否存在见证脚本，也就是witness字段是否存在数据。

![img](https://thewebthree.xyz/media/editor/gfhfgh5656_20241012121434841774.png)

- txins第一个字节表示交易输入的个数，该交易中只有1个输入。当有多个输入时，下图结构会重复出现多次。previous hash表示的第一个输入的交易id，outpoint index表示在第一个输入交易中的索引。outpoint index之后第一个字节表示的解锁脚本的大小。由于Tapscript必须采用见证脚本，因此script_sig的大小为0，数据为空。nSequence表示的是相对时间锁：即从上一个交易开始，必须经过nSequence的时间交易才能生效。

![img](https://thewebthree.xyz/media/editor/3434_20241012121458154967.png)

- txouts第一个字节表示交易输出的个数，该交易中只有一个输出。当有多个输出时，下图结构会重复出现多次。value表示的是第一个输出收到的btc数量，80f0fa0200000000同样是小端模式，正常值为0000000002faf080,转化成十进制值为50000000。因此这里的value表示0.5个btc。接下来的字节表示锁定脚本的大小和锁定脚本，代表接收方的地址。16表示锁定脚本的大小是22字节。锁定脚本001482b672c4c6e8f7f06ba7d35950bc6e7925ab3f35，第一个字节00没有实际含义，对应操作码OP_0。第二个字节14，十进制为20，对应操作码为OP_PUSHBYTES_20，表示将接下来20个字节入栈。剩余的20个字节表示公钥hash。

![img](https://thewebthree.xyz/media/editor/1654_20241012121524123320.png)

- witness表示见证脚本，下文表示的是第一个交易输入对应的见证脚本，换句话说，每一个交易输入都有与之对应的见证脚本。当有多个交易输入时，下图结构会重复出现多次。witness第一个字节表示第一个交易输入对应的见证脚本的元素个数。前文提到交易原文代表Taproot地址向普通地址转账，而Taproot地址的花费有两种方式：所有参与方的聚合签名和通过脚本路径进行花费。下文见证元素大小不为1，因此不是采用聚合签名的方式，而是通过脚本路径进行花费。MAST由单个脚本[PKA] [OP_CHECKSIG] [PKB] [OP_CHECKSIGADD] [PKC] [OP_CHECKSIGADD] [2] [OP_NUMEQUAL]组成，记做script_1。那么与之对应的见证脚本结构应为Stack element(s) satisfying script_1, script_1,P。

![img](https://thewebthree.xyz/media/editor/fghfgh5555_20241012121553658662.png)

- 见证脚本结构中Stack element(s) satisfying script_1对应上图first_elemnet，second_elemnet，third_elemnet，分别代表C, B, A的签名。由于script_1是2-3多签，C没有进行签名，因此first_elemnet大小为0，second_elemnet,third_elemnet采用Schnorr签名，固定大小64字节。fourth_elemnet代表script_1，具体组成如下图所示：21是操作码OP_PUSHBYTES_21 ，表示将接下来33个字节入栈。ac是操作码OP_CHECKSIG，表示检查签名。ba是前文提到的OP_CHECKSIGADD操作码。52是操作码OP_2，表示数值2。9c是操作码OP_NUMEQUAL，用来判断两个数值是否相等。fifth_elemnet中首字节代表Tapscript版本号，剩余32字节表示聚合公钥P。

![img](https://thewebthree.xyz/media/editor/565655656_20241012121617067137.png)

- nLockTime代表交易允许被打包的最早时间。分四种情况：1）0 表示立即生效。 2）小于 500000000代表块高度，处于该块之前交易锁定。3）大于等于500000000代表Unix时间戳，处于该时刻之前交易锁定。4）交易输入的nSequence字段均为最大值0xffffffff时，nLockTime字段无效。

![img](https://thewebthree.xyz/media/editor/343467657_20241012121636590949.png)

### **3.4.总结**

从交易结构的角度来看，Tapscript沿用隔离见证的交易结构，主要改变在于公钥和签名的更新。如果忽略Tapscirpt版本号和奇偶性等前缀，公钥统一用32字节表示。见证脚本中签名采用Schnorr签名，总长度统一为64字节，省略了ECDSA签名中冗余字节。

## **4.基于Schnorr签名的多签方案MuSig**

随着 Taproot升级越来越接近，许多人对 MuSig 多重签名方案产生了浓厚的兴趣。MuSig 允许一个群体集体拥有一些比特币，并创建一个单一签名来授权支付。由于 MuSig 具有创新的密钥聚合特性，这个签名是一个规则的 Schnorr 签名，一旦 Taproot 被激活，它就可以被 Bitcoin 处理。当用于创建多个签名钱包时，MuSig 与传统的 n 个签名使用 CHECKMULTISIG 操作码相比，减少了交易费用，增加了隐私，后者需要 n 个公钥和块链上的 n 个 ECDSA 签名。

### **4.1.多重签名方案**

多重签名方案是签名和验证算法的结合，其中多个签名者(每个人都有自己的私钥/公钥)联合签名一个消息，从而产生一个单一的签名。然后，任何知道消息和签名者的公钥的人都可以验证这个单个签名。请注意，在比特币的上下文中，术语“ multisig”通常指的是 k-of-n 策略，其中 k 可能不同于 n。在密码学中，多重签名实际上只涉及 n 对 n 策略，尽管我们可以很容易地在 n 对 n 的情况上构造 k 对 n。

### **4.2.MuSig**

MuSig 是一个应用 Schnorr 数字签名算法来聚合公钥和签名的多签方案。MuSig 允许多个用户使用各自的私钥创建一个组合公钥，这个组合公钥与任何其他Schnorr公钥都是大小一致且无法区分的，包括单个用户的公钥。它进一步描述了创建公钥的用户如何能够共同安全地创建与公钥对应的签名。像公钥一样，这个签名也和其他的 Schnorr 签名没有什么区别。与传统的基于脚本的 multisig 相比，MuSig 使用更少的块空间并且有更多的私有空间，但它也可能需要参与者之间更多的交互性。

### **4.3.MuSig支持密钥聚合**

MuSig支持密钥聚合。密钥聚合是指看起来像单密钥签名的多重签名，但是相对于仅是参与者的公共密钥的功能的聚合公共密钥。因此验证者不需要知道原始参与者的公钥，只需给它们一个聚合的密钥。MuSig能生成简短的、体积固定的签名，不管签名者有多少、怎么签，在验证者看来都是一样的。在区块链系统中，验证效率是最重要的因素，除非确实需要更多的安全性，否则没有必要向验证者提供签名者更多的细节。这样做有一个明显的好处就是能够提高隐私性，因为它能隐藏具体签名者的信息。因此 MuSig 实际上也是 Schnorr 签名的密钥聚合方案。

### **4.4.MuSig在普通公钥模型中有可证明的安全性**

MuSig在普通公钥模型中有可证明的安全性。目前已经存在许多为 Schnorr 签名提供密钥聚合的多重签名方案，但是它们具有一些局限性，例如需要验证参与者实际上是否具有与其声称拥有的公共密钥相对应的私有密钥。可以证明普通公钥模型中的安全性就不会存在任何限制，参与者只需要提供他们的公钥。这就意味着签名者可以使用普通的密钥配对来参加多重签名，而不需要提供任何关于这些密钥生产及控制的具体方式的信息。在一些比特币情境中，个人签名者的密钥管理政策互不相同且有限制，这时候就很难获得关于密钥生成的信息，很好地增强了用户的隐私。

### **4.5.MuSig交互问题**

在实现上述优点的同时，也带来了一些问题。其中一个比较明显的问题就是MuSig需要更多签名者之间的交互。更准确地说，创建一个签名需要三轮通信，每轮通信都由来回传递的消息组成。下面的图显示了三轮通信的过程。你可以想象一个签名者是一个桌面钱包，另一个是 Blockstream Green 联署签名者，或者签名者共享一个他们试图关闭的 Lightning 通道。

![img](https://thewebthree.xyz/media/editor/3333242342342_20241012121747586695.png)

相比之下，使用 CHECKMULTISIG 的钱包只需要一轮通信: 它们接收一个交易就返回一个签名。例如，如果使用 MuSig在闪电网络中转发支付，隐私将得到改善，但支付时间将明显延长。随着通信延迟的增加，这个问题会变得更加严重。存储在保险箱中的 MuSig签名设备在创建签名之前需要其所有者访问两次。

### **4.6.MuSig2**

顾名思义，MuSig2是 MuSig的继承者。它提供了与 MuSig相同的功能和安全性，但却可以消除几乎所有签名者之间的交互。使用 MuSig2，签名者只需要两轮通信就可以创建签名，而且关键的是，其中一轮可以在签名者知道他们想要签名的消息之前进行预处理。一旦有一些消息需要签名，例如，一个比特币交易，这个过程就和现在的基于 checkmultisigns 的钱包一样: 将交易传输给签名者，然后收到一个签名的回复。MuSig2保留了 MuSig的简单性和效率，只是增加了少量的额外计算。

### **4.7.MuSig-DN**

多重签名方案允许一组签名者（每个人都有自己的密钥对）协作计算公共消息的签名。MuSig（又叫MuSig1），MuSig2，MuSig-DN一脉相承，都描述了一种多签解决方案。MuSig需要进行三轮通信完成一次多签。MuSig2在MuSig基础上消除了一轮通信，并允许使用类似于我们目前基于脚本的多重签名过程。 但MuSig2存储额外的数据，并需要非常小心确保签名软件或硬件不会被欺骗而在不知不觉中重复部分签名会话。MuSig-DN通过零知识证明和 Purify（一种有效的确定性随机数推导函数）的组合，保护 用户免受由于不良随机数生成器和虚拟机重置攻击引起的密钥泄露攻击。同时MuSig-DN不易受到重复会话攻击。

每个 Schnorr 或 ECDSA 签名都需要一个nonce，即签名者生成的秘密随机数。这些签名方案的安全性在很大程度上依赖于这种随机数的均匀随机生成，即使随机性中的轻微偏差也可能使攻击者从签名中提取密钥成为可能。糟糕随机性的一个简单而极端的例子，就是为不同的消息重用随机数。如果使用相同密钥和完全相同的随机数对两条不同消息进行签名，则可以立即从这两个签名中计算出该密钥。 为了避免签名过程中的这种脆弱性，通常使用确定性随机数，例如，使用哈希函数作为随机数 SHA256(sk, m) ，其中 sk 是签名者的密钥，m是要签名的消息。由于攻击者不知道 sk，因此产生的随机数仍然是不可预测的，即使它实际上是从确定性计算而不是真正的随机性得出的。由于 m 是散列函数输入的一部分，不同消息的签名将使用不同的随机数，这排除了不同消息的随机数重用。确定性随机数还可以防止回滚攻击，在这种攻击中，攻击者试图通过重置签名算法在两个不同的消息上获得具有相同随机数的签名。 由于这些优点，在生成签名时使用确定性随机数是轻而易举的，并且实际上所有签名的严肃实现都依赖于某种方法来确定性地导出随机数。然而，当涉及到多重签名时，如果天真地使用确定性随机数并不能防止暴露密钥，令人惊讶的是，情况恰恰相反具有确定性随机数的 MuSig 实现更容易暴露密钥。攻击的工作原理如下：恶意签名者与受害者为同一消息签名进行两次签名会话。由于消息在两个会话中是相同的，因此受害者确定性地生成完全相同的随机数。但是 MuSig 中没有任何内容会强制另一个恶意签名者确定性地生成他的随机数。恶意签名者可以使用任意随机数。因此，两个签名会话中的“聚合随机数”（根据所有签名者的随机数计算）将不同。最终拥有不同的聚合 nonce 与拥有不同的消息具有相同的效果，并且攻击者可以轻松地从这两次签名会话中提取受害者的密钥。

MuSig-DN是克服上述困难并在 MuSig 中安全使用确定性随机数的多签方案。 MuSig-DN 背后的主要思想是使用零知识证明来强制所有签名者确定性地生成他们的随机数。每个签名者从一个额外的秘密密钥（这里称为 nonce 密钥）、消息和所有签名者的公钥中派生出一个确定性的随机数。然后，签名者在第一轮 MuSig-DN 中传达他们的公共随机数以及证明他们的公共随机数已正确导出的非交互式零知识证明。所有其他签名者都可以使用与签名者的 nonce 密钥关联的附加公钥（这里称为主机密钥）来检查这些证明。如果任何签名者试图通过在不同的签名会话中发送两个不同的随机数来作弊，其他签名者将检测到它（因为两个随机数中的至少一个将具有无效的零知识证明）并简单地中止协议。 除此之外，MuSig-DN 的另一个主要贡献是 Purify，这是一种用于导出随机数的特定函数。与 SHA256 之类的散列函数相反，它是派生确定性随机数的典型选择。Purify 依靠椭圆曲线来提取看似随机的随机数，并 可以有效地与零知识证明框架一起使用。 MuSig-DN 的一个非常好的附加属性是：和MuSig2类似，签名会话只需要两轮通信即可完成。

![img](https://thewebthree.xyz/media/editor/453456767_20241012121814681444.png)

上图对Musig系列的多签方案进行了简单的对比。从上图来看，没有理由比 MuSig2 更喜欢 MuSig1。相比于MuSig2，MuSig-DN 的优势在于它支持确定性随机数，这避免了在签名会话和轮次之间保持状态的需要，减少重复会话攻击。但是MuSig-DN 的劣势在于不支持非交互式签名，同时实现复杂度和计算复杂度特别高。

总的来看，MuSig-DN是通过零知识证明和 Purify的组合，实现的确定性随机数多签方案。MuSig-DN避免了签名会话和轮次之间保持状态的需要，从而有效减少重复会话攻击。

### **4.8.并发会话安全**

MuSig2在并发会话下是安全的。在 MuSig中，每个签名者创建一个 nonce，在 MuSig2中，每个签名者创建两个以上的 nonces R_i,1, R_i,2在第一轮中将它们发送给其他签名者，并且有效地使用一个随机的线性组合 R_i = R_i,1 + b*R_i,2 来代替以前的一个 nonce R_i。系数 b 是应用于所有签名者的非参数、聚合公钥和消息的哈希函数的输出。和 MuSig一样，聚合起来也是 R = R_1 + ... + R_n。如果任何一个签名者改变了他们的任何一个非消息，每个其他的签名者将使用他们两个非消息的不同的、随机的线性组合。这样就避免了对其他两轮多重签名方案发现的攻击。

## **5. Sighash和Taproot**

### **5.1.Sighash简介**

为了确保没有人未经许可而花费持有者的 BTC，需要进行签名才能完成一次BTC花费。由于一个交易的输入、输出都可能具有多个，那么签名也具有多种类型。SIGHASH 就是一种类型标志，用于指示交易的哪一部分被签名。 通过选择不同的SIGHASH，可以有效的应对不同的应用场景。

### **5.2.Sighash用途**

![img](https://thewebthree.xyz/media/editor/545676778678789_20241012121835792912.png)

尽管比特币网络仅定义了四个值，但SIGHASH_ANYONECANPAY通过按位 | 可以将其与前三个值组合在一起，导致目前SIGHASH总共有六个可能的值。如上图所示，是可以添加到交易中的数字签名的 6 种不同标志组合。 值得注意的是，一个交易的不同的输入可以使用不同的 SIGHASH 标志，从而实现支出条件的复杂组合。

![img](https://thewebthree.xyz/media/editor/bvbnbn_20241012121857673079.png)

- SIGHASH_ALL（0x01）：这是我们所知道的每个用户的钱包的默认设置。它对每个交易的所有输入和输出进行签名，对交易的任何更改都将使签名无效。这实质上是“我只同意使用输入和输出必须精确，接受地址才能得到的比特币”。这是我们每个人常用的交易签名类型，通过花费特定的输入来创建特定的输出。
- SIGHASH_NONE（0x02）：这将签署交易的所有输入，但不签署任何输出。实际上，它会产生一条授权语：“我可以参与这项交易，但是我并不特别在意它的去向”。从表面上看这似乎是不安全的，似乎没有签署任何输出就在浪费金钱。确实，如果你仅用一个输入创建一个tx并用对其进行签名SIGHASH_NONE，那么矿工将能够简单地将输出更改为他们控制的输出。该结构相当于创建特定金额的“不记名支票”或“空白支票”。它对输入进行承诺，但允许更改输出锁定脚本。任何人都可以将自己的比特币地址写入输出锁定脚本并兑换交易。可用的应用场景是满足“我同意花我的钱，只要其他所有人也花钱”的情形。预计其他签名者中的一个将随后使用该笔SIGHASH_ALL交易来确保交易的所有输出，并将款项发送至双方同意的输出集。
- SIGHASH_SINGLE（0x03）：这种签名对所有输入以及一个相应的输出进行签名。相应的输出是与签名具有相同索引的输出（即，如果您的输入为vin 0，则你要签名的输出必须为vout 0）。这实际上是说：“只要这笔钱都到了这个地址，我同意参加所有这些输入的交易”。可用的应用场景是A和B需要向某人支付1.5 BTC，A出资1 BTC。B出资0.5BTC。因此，A可以使用SIGHASH_SINGLE创建1个BTC输入和一个1.5 BTC输出到需要付款的人的交易。然后，B可以为其更改地址添加输出，并使用SIGHASH_ALL或SIGHASH_SINGLE来完成交易。
- SIGHASH_ALL | SIGHASH_ANYONECANPAY（0x81）：与相似SIGHASH_ALL，并对所有输出进行签名。但是，它仅签名一个输入。从本质上说，“只要以下接收者收到这些款项，我就同意参加此交易。我不在乎此交易的任何其他投入。可用的应用的场景是这种结构可以用来做“众筹”交易，试图筹集资金的人可以用单笔输出来构建一个交易，单笔输出将“目标”金额付给众筹发起人。这样的交易显然是无效的，因为它没有输入。但是现在其他人可以添加自己的输入来修改它，实现捐赠。他们用ALL | ANYONECANPAY签名自己的输入，除非收集到足够的输入以达到输出的价值，否则交易无效，每次捐赠是一项“抵押”，直到募集到整个目标金额，筹款人才能收取。
- SIGHASH_NONE | SIGHASH_ANYONECANPAY（0x82）：与相似SIGHASH_NONE，但仅在其中输入一个签名。这本质上就像在说：“我可以发送此BTC。实际上，我甚至不在乎它是否在此交易中发送。这是签名的便条，说包括该笔交易在内的任何交易都可以花费此BTC”。可用的应用场景是不提供任何保证，只用作花费证明。这样的签名允许任何人定义输入，并将该输入包括在具有任意输出的任何其他签名中。通过做出这样的签名，可以在没有任何控制的情况下花费BTC。
- SIGHASH_SINGLE | SIGHASH_ANYONECANPAY（0x83）：类似SIGHASH_SINGLE，不同之处在于，它仅对包含它的输入和相应的输出进行签名。这表示“我绝对想将这么多的BTC移至该输出，但是我不在乎此交易中的任何其他输入和输出”。可用应用场景是A向B转账染色币：
- A用一个输入和一个输出创建一个交易：
- 输入0：一个来自A的染色币
- 输出0： 一个比特币给到A
- B看到A的交易可以添加交易：
- 输入1：一个来自B的比特币
- 输出1：一个染色币给到B

本质上讲，这允许A持有的1染色币的输入进行签名，并以1 BTC输出至其控制的地址。然后，A发布此无效的交易，无效的原因是因为没有1 BTC的输入。最后，任何想要购买1个BTC的染色币的人都可以添加一个大于等于1 BTC的输入，一个要求1染色币的输出从而完成这笔交易。

### **5.3.Sighash和Taproot**

在bip118中提议引入一种新型的SIGHASH叫做SIGHASH_ANYPREVOUT。此种SIGHASH描述了一种用于 tapscript (BIP 342) 交易的新型公钥。 它允许这些公钥的签名不承诺所花费的确切 UTXO。 即通过删除先前输出（以及可选的见证脚本 和值)，允许将签名交易动态重新绑定到另一个需要相同密钥授权的先前输出。并且，此种SIGHASH标志是从SIGHASH_NOINPUT重命名为而来，以反映虽然任何 prevout 都可能与签名一起使用，但输入的某些方面仍然被提交，即输入 nSequence 值，以及支出 条件和金额。

总的来看，Sighash是一种签名类型标志。利用不同的签名类型，我们可以选择对交易的输入和输出的不同部分进行签名，从而有效的在不同场景中完成BTC的花费。

### **6.Taproot 是 SegWit 的延续**

在隔离见证（Segwit）升级时，比特币的脚本规则进行了一次大规模的升级，提出了两种全新的脚本规则P2WPKH （Pay to Witness Public Key Hash）和 P2WSH （Pay to Witness Script Hash），现在以 bc1 开头的地址，都是采用了上述的脚本规则之一。P2WPKH 通常用在普通的地址上，而P2WSH 通常用在多签地址中。另外，在隔离见证的升级中，脚本中还预留了一个版本号（Version）的概念，所有之前的 Segwit 脚本规则都采用了 V0 作为版本号，所以也可以称为 Segwit V0。而 Taproot 则是在 Segwit 的框架上进行了升级，版本号升级为 V1，也可以称作P2TR(Pay to Taproot)。

SegWit V0 根据锁定的地址不同，区分为P2WPKH（锁定到公钥哈希）和P2WSH（锁定到脚本哈希），这两种脚本规则完全不同，因此很容易区分开来。但升级至SegWit V1后，这将难以区分。

Segwit V1输出可通过两种方式花费：

- 密钥路径（Key Path）花费：它将witness program视为公钥，并允许使用该公钥的签名进行花费。
- 脚本路径（Script Path）花费：它将witness program视为执行脚本，允许使用预先提交的脚本来花费输出。

使用Musig的公钥、签名聚合方案，通过密钥路径（Key Path）进行花费，能够实现n-of-n的多签交易，而这种方式的实现与使用单个公钥进行花费没有区别。

### **6.1.从SegWit V0过渡到SegWit V1**

SegWit交易结构

Segwit v1遵循与Segwit v0相同的输出脚本模式:

- Segwit 输出：[1B Version] [SegWit program]
- Segwit V0 输出: [00] [20B public key digest](https://thewebthree.xyz/4/P2WPKH) 或[00] [32B script digest](https://thewebthree.xyz/4/P2WSH)
- Segwit V1 输出：[01] [33B public key]

可以看到，在SegWit V1中，33字节的公钥编码与一般的压缩公钥编码类似，不同之处在于字节总数为奇数。

- Y-坐标: 偶数-[00] 或 奇数-[01]
- X-坐标: [32B x-coordinate]
- 33 字节公钥编码：[1B oddness] [32B x-coordinate]

![img](https://thewebthree.xyz/media/editor/bvnvbnvb_20241012121923411490.png)

通过在输出的scriptPubKey中为pubkey提供有效的签名，可以使用**密钥路径**使用输出，花费的witness只是简单的sig（签名），而如果public key 使用了taproot进行调整，则输出可以使用**脚本路径**进行花费。

### **6.2.构造SegWit V0（2-2多重签名）**

- 首先生成一个密钥对，使用bip-schnorr和bip-taproot pubkey编码规则对公钥进行编码，然后将witness version和witness program编码为bech32地址。创建Scriptpubkey，向生成地址发送btc，生成一笔交易输出

```bash
# Generate individual key pairs
privkey1, pubkey1 = generate_key_pair()
privkey2, pubkey2 = generate_key_pair()

# Create the spending script
multisig_script = CScript([CScriptOp(OP_2), pubkey1.get_bytes(), pubkey2.get_bytes(), CScriptOp(OP_2), CScriptOp(OP_CHECKMULTISIG)])

# Hash the spending script
script_hash = sha256(multisig_script)

# Generate the address
version = 0
address = program_to_witness(version, script_hash)
print("bech32 address is {}".format(address))

# Generate coins and create an output
tx = node.generate_and_send_coins(address)
print("Transaction {}, output 0\nsent to {}\n".format(tx.hash, address))
```

- 通过创建CTransaction对象并填充所需字段的方式，手动生成交易原文。
- nVersion
- nLocktime
- tx_vin
- tx_vout
- tx.wit.vtxinwit

```bash
# Create a spending transaction
spending_tx = test.create_spending_transaction(tx.hash)
```

- 对构造的交易进行ECDSA签名
- 先前的签名哈希标志：
- 0x01 - **SIGHASH_ALL**
- 0x02 - **SIGHASH_NONE**
- 0x03 - **SIGHASH_SINGLE**
- 0x81 - **SIGHASH_ALL | SIGHASH_ANYONECANPAY**
- 0x82 - **SIGHASH_NONE | SIGHASH_ANYONECANPAY**
- 0x83 - **SIGHASH_SINGLE | SIGHASH_ANYONECANPAY**
- 升级Taproot后新增的签名哈希标志
- 0x00 - **SIGHASH_ALL_TAPROOT**

``> 用法类似于0x01 **SIGHASH_ALL**

在SegWit V0中使用SIGHASH_ALL，在SegWit V1中使用SIGHASH_ALL_TAPROOT进行替换

```bash
# Generate the segwit v0 signature hash for signing
sighash = SegwitV0SignatureHash(script=multisig_script,
                                txTo=spending_tx,
                                inIdx=0,
                                hashtype=SIGHASH_ALL,
                                amount=100_000_000)

# Sign using ECDSA and append the SIGHASH byte
sig1 = privkey1.sign_ecdsa(sighash) + chr(SIGHASH_ALL).encode('latin-1')
sig2 = privkey2.sign_ecdsa(sighash) + chr(SIGHASH_ALL).encode('latin-1')

print("Signatures:\n- {},\n- {}\n".format(sig1.hex(), sig2.hex()))
```

- 花费SegWit V0交易输出(P2WSH)

```bash
# Construct witness and add it to the script.
# For a multisig P2WSH input, the script witness is the signatures and the scipt
witness_elements = [b'', sig1, sig2, multisig_script]
spending_tx.wit.vtxinwit.append(CTxInWitness(witness_elements))

print("Spending transaction:\n{}\n".format(spending_tx))
print("Transaction weight: {}\n".format(node.decoderawtransaction(spending_tx.serialize().hex())['weight']))
```

### **6.3构造SegWit V1（2-2多重签名）**

相较于SegWit V0，SegWit V1主要有以下几点不同：

- 采用Schnorr签名替换ECDSA签名方案
- 采用Musig聚合签名和聚合公钥方案
- 改进签名哈希和脚本的操作码

```bash
# Generate individual key pairs
privkey1, pubkey1 = generate_key_pair()
privkey2, pubkey2 = generate_key_pair()

# Generate a 2-of-2 aggregate MuSig key using the same pubkeys as before
# Method: generate_musig_key(ECPubKey_list)
c_map, agg_pubkey = generate_musig_key([pubkey1, pubkey2])

# Multiply individual keys with challenges
privkey1_c =  c_map[pubkey1] * privkey1
privkey2_c =  c_map[pubkey2] * privkey2
pubkey1_c =  c_map[pubkey1] * pubkey1 
pubkey2_c =  c_map[pubkey2] * pubkey2

# Create a segwit v1 address for the MuSig aggregate pubkey
# Witness program ([1B oddness] [32B x-coordinate])
pubkey_data = agg_pubkey.get_bytes()
program_musig = bytes([pubkey_data[0] & 1]) + pubkey_data[1:]
print("Musig witness program is {}".format(program.hex()))

version = 0x01
address_musig = program_to_witness(version, program_musig)
print("Musig address is {}".format(address))
print("2-of-2 musig: ", address_musig)

# Generate coins and create an output
tx = node.generate_and_send_coins(address_musig)
print("Transaction {}, output 0\nsent to {}\n".format(tx.hash, address_musig))

# Create sighash for ALL (0x00)
sighash_musig = TaprootSignatureHash(spending_tx, [tx.vout[0]], SIGHASH_ALL_TAPROOT, input_index=0)

# Generate individual nonces for participants and an aggregate nonce point
# Remember to negate the individual nonces if necessary
nonce1 = generate_schnorr_nonce()
nonce2 = generate_schnorr_nonce()
R_agg, negated = aggregate_schnorr_nonces([nonce1.get_pubkey(), nonce2.get_pubkey()])
if negated:
  R_agg.negate()
  nonce1.negate()
  nonce2.negate()

# Create an aggregate signature
# Method: sign_musig(privkey, nonce, R_agg, agg_pubkey, sighash_musig)
# Method: aggregate_musig_signatures(partial_signature_list, R_agg)
s1 = sign_musig(privkey1_c, nonce1, R_agg, agg_pubkey, sighash_musig)
s2 = sign_musig(privkey2_c, nonce2, R_agg, agg_pubkey, sighash_musig)
sig_agg = aggregate_musig_signatures([s1, s2], R_agg)
print("Aggregate signature is {}\n".format(sig_agg.hex()))

# Add witness to transaction
spending_tx.wit.vtxinwit.append(CTxInWitness([sig_agg]))

# Get transaction weight
print("Transaction weight: {}\n".format(node.decoderawtransaction(spending_tx.serialize().hex())['weight']))

print("Success!")
```

SegWit V1 MuSig输出比SegWit V0 P2WSH输出的权重大约低30%，对于更大的n-of-n多重签名交易，交易权重会更加地减少。由于交易费用是基于交易权重，这些权重的节省直接转化为费用的节省。此外，通过使用MuSig聚合密钥和签名，不会透露正在使用的多签名方案，这有利于交易的隐私性和安全性。

### **6.4.SegWit Version 1 是否能兼容 SegWit version 0 (面试题目)**

总地来看，SegWit Version 1的改动不大，主要集中在以下几个方面：

- 「**弃用OP_CHECKMULTISIG**」：这个操作码的效率较低，因为它有时需要尝试多个公钥与签名的组合，这些运行逻辑可以被更高效地处理。而且，它与不兼容批量验证（批量验证相较于单独验证能更快地验证一个块中的所有签名）。但由于该操作码应用广泛，新增了一个操作码OP_CHECKSIGADD用于替换，该操作码根据签名检查是否成功的状态增加了一个计数器。
- 「**用Schnorr签名代替ECDSA**」：SegWit Version 0中所有采用ECDSA签名的操作码都将改为采用Schnorr签名，因为Schnorr签名更高效。而且，ECDSA签名不支持批量验证，这与这与bip-taproot的设计目标相冲突。
- 「**改进签名哈希**」：SegWit Version 1对签名的哈希做了一些改进，以解决一些长期存在的问题。

在升级至Taproot后，由于BIP-341中提到的升级目标与现有的SegWit Version 0脚本类型并不兼容，无法使用SegWit Verion 0的脚本花费 SegWit Version 1的输出，因此，未升级的节点是无法验证SegWit Version 1 的交易的。虽然如此，但是这个升级是必要的，能够通过不大的改动显著提升比特币网络的隐私性和安全性。

# **八. 铭文和符文协议**

## **1.OmniUSDT**

Omni Protocol（原名 Mastercoin 协议）是一个运行在比特币网络上的去中心化协议，它通过在比特币区块链上嵌入数据，实现了发行和转移数字资产的功能。这种协议不需要修改比特币协议本身，而是通过利用比特币区块链中的**OP_RETURN字段**或其他数据嵌入方式，记录额外信息，从而约定新的协议。

### **1.1.Omni Protocol 的工作原理**

- **嵌入数据**：Omni Protocol 使用比特币交易中的空闲字段（如 OP_RETURN 字段）来存储协议相关的数据。比特币交易包含一些可供用户自定义的数据字段，Omni 利用这些字段嵌入特定的指令和数据，表示用户在协议层面上的行为（如创建资产、转账等）。
- **解读数据**：比特币网络节点并不会执行这些额外的数据，它们只会被视为比特币交易的一部分。然而，运行 Omni 相关软件的节点可以读取这些嵌入在交易中的数据，并根据 Omni 协议的约定进行解读，从而理解这些交易的实际含义。这些操作可以包括：
- 创建新的数字资产（如稳定币、代币等）。
- 资产转移（在 Omni 协议层面完成的代币转账）。
- 记录智能合约指令。
- **资产发行**：通过 Omni 协议，用户可以在比特币区块链上发行自己的数字资产。这些资产（如 USDT）在技术上依赖比特币区块链的安全性和共识机制，但在功能上具有更高层次的灵活性，比如跨资产交易、创建去中心化应用（Dapps）等。
- **交易执行**：尽管 Omni 协议的交易嵌入在比特币交易中，但实际的协议行为和资产转移由 Omni 节点执行。这些节点会识别比特币交易中的协议数据，并按照协议规则更新各用户的 Omni 资产余额。

### **1.2. Omnit 工作流**

![img](https://thewebthree.xyz/media/editor/45453453453453453_20241012122010743873.png)

### **1.3.Omni Protocol 的优点**

- **依赖比特币的安全性**：Omni 协议的所有操作都建立在比特币区块链之上，因此它继承了比特币网络的安全性和去中心化特性。
- **无需修改比特币协议**：Omni 协议通过现有的比特币交易字段工作，无需对比特币协议本身进行修改。
- **支持多种资产类型**：通过 Omni，用户可以创建和交易各种类型的数字资产，包括稳定币（如 Tether 的早期版本）。

## **2.NFT**

不熟悉 NFT 的人应该从以太坊开始。其中一个著名协议是ERC721，它定义了获取和转移所有权的智能合约方法。一些名人或品牌，如 BAYC 或 Azuki，也持有流行的 ERC721 NFT。Ordinals 协议有其定义和名称，称为数字艺术品。它可以拥有所有者，并且可以在不支付强制性特许权使用费的情况下进行交易。此外，其内容必须完全在链上 - 这意味着它无法更新。

在深入研究比特币序数 NFT 之前，让我们先看看比特币区块链中的交易是如何运作的。

## **3.序数理论**

![img](https://thewebthree.xyz/media/editor/9sd52asd_20241012122032819144.png)

## **4.稀有聪**

比特币的最小单位是聪，没有一个聪都有一个编号，具备独特历史条件或者区块属性的聪被称为稀有聪

- 创世区块里面的聪
- 第一区块里面的聪
- 特定高度的聪，如比特币减半的时候产生区块链里面的聪

## **5.见证字段**

比特币脚本是一种基于堆栈的语言，对于一笔交易的话，有一个锁定脚本(输入)和一个解锁脚本(输出)

### **5.1.脚本示例**

以下是一个典型的 P2PKH 脚本示例：

**锁定脚本（ScriptPubKey）**：

- OP_DUP OP_HASH160 OP_EQUALVERIFY OP_CHECKSIG
- OP_DUP：复制栈顶的公钥。
- OP_HASH160：对公钥进行哈希，得到公钥的哈希值。
- ：预期的公钥哈希值。
- OP_EQUALVERIFY：验证两个哈希值是否相等。
- OP_CHECKSIG：检查签名是否有效。

**解锁脚本（ScriptSig）**：

- 
- 提供解锁这个比特币所需的签名和公钥。

SegWit 升级的时候在交易输出里面引入一个新的见证字段，以保护交易的隐私性和提高性能， taproot 升级之后，见证字段可以容纳更大的数据，将近 400000 字节。

## **6.铭文**

可以刻在 statoshi 上的任意文本，包含但不限于文本，图像，视频；在 taproot 中，铭文被刻入到 pay-to-taproot 的输出类型中，铭文内容不执行条件里，由 OP_FALSE OP_IF[content]OP_ENDIF 组成，组成完成之后推送到见证字段，所以其不会影响原始的脚本。

铭文格式：

- OP_FALSE
- OP_IF
- OP_PUSH "命令"
- OP_1
- OP_PUSH "文本类型"
- OP_0
- OP_PUSH "DappLink"
- OP_ENDIF

以上的铭文呢，只能进行 mint 和 transfer, 很难在去中心化环境里面进行买卖交易。

### **6.1. 铭文的优势**

- 和IPFS相比，数据存在了Bitcoin链上，更安全
- 和Arweave很相似，只不过Bitcoin的网络和共识更能保证数据安全
- 重复inscribe：只认第一次inscribe的内容，re-inscribe无效

### **6.2.基于 PSBT 的去中心化 marketplace**

![img](https://thewebthree.xyz/media/editor/sdfsdfdf_20241012122106030271.jpg)

基于这一特性，可以实现去中心化的ask&bid。以ask为例：

- 卖方把NFT的sat作为input，把出价作为output，然后进行SINGLE|ANYONECANPAY签名，最后把这个PSBT发布到marketplace
- 买方补充input（包含付款和fee），补充output（接收sat），签名后广播交易到Bitcoin网络

一些具体实现

- <https://github.com/magicdao-oss/msigner>
- <https://github.com/casey/ord/issues/802>
- 具体实现会比上述流程多一些dummy input和output，主要用于对齐sat的转移

![img](https://thewebthree.xyz/media/editor/dfsdfsdfsdfsdfsdfsd_20241012122127846308.png)

# **九.BRC20 协议**

## **1.协议概述**

BRC -20 代币标准于 2023 年 3 月 8 日创建的比特币实验性可替代代币标准，它利用 JSON 数据的序数铭文来部署代币合约、铸造代币和转移代币。

## **2.协议的细节**

![img](https://thewebthree.xyz/media/editor/453453453_20241012122148789735.png)

### **2.1.mint**

链上：inscribe一个表示mint operation的sat，并立即 transfer 给 minter 地址

```bash
{
    "p": "brc20",
    "op": "mint",
    "tick": "ordi",
    "amt": 1000
}
```

链下

- 判断state[tick]存在，amt 不能超过其lim，累计 amt 不能超过其 max
- state[tick]["balances"][minter]+=amt

![img](https://thewebthree.xyz/media/editor/dsfsdfdsf654646_20241012122211325178.png)

### **2.2.transfer**

**链上**

- 先inscribe一个表示transfer operation 的 sat，发给 sender 地址

```bash
{
    "p": "brc20",
     "op": "transfer",
    "tick": "ordi",
    "amt": 1000
}
```

- sender再构造一笔交易吧这个 sat 发给receiver
- 需要 2 比交易，不友好

**链下**

- 判断state[tick]["balances"][sender]>=amt
- account_state[tick]["balances"][sender]-=amt
- account_state[tick]["balances"][receiver]+=amt

![img](https://thewebthree.xyz/media/editor/dfdf631565416_20241012122233268438.png)

## **3.一些brc-20例子**

- <https://ordinalswallet.com/brc20>

## **4.基于PSBT的交易**

只能定量定价地ask/bid，以ask为例

- 卖方先 inscribe 一个 transfer 的 sat
- 用这个 sat 构造 PSBT，发布到交易平台
- 买方通过构造完整交易，买下这个 sat

例子：<https://ordinalswallet.com/brc20/ORDI>

# **十. RGB 协议与 RGB++ 协议**

## **1.RGB 协议**

RGB 协议中的 **一次性密封** 和 **客户端验证** 是核心技术方案，允许协议在保证安全性和隐私性的同时，减少对区块链网络的负担。这两项技术方案紧密结合，形成了一个既高效又去中心化的资产管理与智能合约执行体系。

### **1.1.一次性密封技术方案**

**一次性密封** 技术基于比特币的 UTXO 模型，但它的应用不局限于交易输出，而是扩展到了状态控制和验证。一次性密封的目标是防止同一状态被多次花费，并通过哈希承诺来控制状态更新，确保资产的唯一性。

#### **1.1.1 密封点概念**

密封点是某一特定资产的状态锚定点，它通常由一个比特币 UTXO 表示，但不局限于此。密封点被“密封”后，只能使用一次。一旦被使用，它将被“花费”，无法再次用于其他交易或状态更新。

**工作流程**：

- **生成密封点**：资产所有者通过链上交易将资产锁定在某个 UTXO（或其他链上表示形式）中，形成一个一次性密封点。
- **状态更新**：当所有者希望更新状态或转移资产时，必须“打开”该密封点。打开的过程类似于比特币的 UTXO 花费，需要所有者的私钥签名来证明对密封点的控制权。
- **状态承诺**：新的状态会生成一个哈希承诺，该承诺将作为链上交易的一部分提交，从而记录状态更新的证明。
- **关闭密封点**：旧的密封点一旦被使用，就不可再用，以防止双重花费。

#### **1.1.2.一次性密封的实现**

- **链上部分**：密封点的创建和使用会通过比特币 UTXO（或其他链上资产表示形式）进行，链上只记录状态的承诺哈希值，而不记录状态的具体内容。
- **链下部分**：状态更新和资产管理的具体细节在链下进行，通过链下的验证和签名过程，确保状态更新的合法性。

#### **1.1.3.一次性密封的作用**

- **防双重花费**：通过一次性密封的设计，确保同一个资产状态只能被花费一次，防止双重花费问题。
- **状态唯一性**：每次状态更新需要打开一个新的密封点，旧的密封点无法再次使用，从而确保状态更新的不可逆性和唯一性。

### **1.2.客户端验证技术方案**

**客户端验证** 是 RGB 协议中链下资产状态管理的核心技术。与传统区块链上智能合约执行不同，RGB 的智能合约和资产状态管理在用户的客户端自行完成，链上只记录状态承诺。通过这种机制，RGB 实现了链下高效执行和状态隐私保护。

#### **1.2.1.链下验证机制**

- **状态承诺（State Commitment）**：RGB 协议通过链下数据计算出资产或状态的哈希承诺，并将该承诺发布到区块链上。状态承诺是链上唯一需要的记录，用于证明状态更新的合法性，但状态的具体细节不会公开。
- **验证节点**：每个客户端都是独立的验证节点，持有状态数据和验证规则，能够在链下自行验证状态的合法性和一致性。
- **链下签名和验证**：当资产转移或智能合约状态更新时，资产的持有者会生成一个签名并将新的状态承诺发送给接收方，接收方通过客户端验证确保状态的正确性。

**工作流程**：

- **状态创建**：初始状态在链下生成，并通过哈希承诺的方式记录在链上。
- **状态更新**：当发生状态变化时，发起方生成一个新的状态承诺（新哈希值），并通过链下签名来保证该更新的合法性。
- **验证路径**：每个客户端保留完整的状态验证路径，能够追溯并验证每个状态的更新过程。客户端通过这些路径验证每个状态的正确性。
- **链上发布**：新的状态承诺在链上发布，以确保所有参与者都能追踪到最新的状态变化。

#### **1.2.2.客户端验证的作用**

- **隐私保护**：链上只记录状态的承诺，不记录状态的具体内容。这意味着具体的交易、资产转移等操作都在链下进行，从而保护用户的隐私。
- **去中心化**：每个客户端都可以独立完成状态的验证，无需依赖中心化节点或矿工。通过客户端验证，所有参与者都可以自行验证链下的资产转移和状态更新。
- **高效性**：客户端验证减少了链上负担，链上只需要记录最小化的数据，状态的具体操作在链下完成，从而显著提升了系统的效率。

### **1.3.一次性密封和客户端验证的结合**

**一次性密封** 和 **客户端验证** 是 RGB 协议的两大支柱，二者相辅相成，为 RGB 提供了链下执行和去中心化验证的核心框架。

#### **1.3.1.结合的工作机制**

- **密封点创建和状态锚定**：当用户发行或转移资产时，密封点通过链上 UTXO 锁定。这个密封点是资产状态的唯一锚定点，后续的状态更新必须通过密封点来控制。
- **链下状态更新**：状态的更新和资产转移都在链下进行。用户通过客户端生成新的状态承诺，并将其与链上的密封点相链接，链上仅存储状态更新的哈希值。
- **一次性密封的花费和验证**：在密封点“打开”的过程中，客户端验证用户的签名和状态更新的合法性。旧密封点被“花费”后，状态数据的更改会触发新的密封点创建。
- **链上状态发布**：新的状态承诺会在链上记录下来，允许其他参与者追踪状态变化并验证状态的合法性。

#### **1.3.2.技术优势**

- **降低链上负担**：通过链下执行和客户端验证，减少了区块链的交易量和存储需求。
- **增强隐私性**：链上只记录最小的信息，而状态更新在链下完成，保护了用户的资产细节和交易隐私。
- **高效防篡改性**：一次性密封防止双重花费，客户端验证确保状态的真实性和不可篡改性。
- **去中心化验证**：无需依赖中心化矿工或验证节点，所有验证操作都在用户端完成，提升了系统的去中心化程度。

### **1.4.RGB 流程图示**

![img](https://thewebthree.xyz/media/editor/erwer2434_20241012122302106125.png)

## **2.RGB++ 协议**

RGB++ 基于 RGB 协议，把 RGB 客户端验证变成了 CKB 链，本质上和 RGB 协议是一样的，只是 CKB 链赋予了 RGB++ 的更多可能性性，支持更复杂的应用场景。例如，增加一些高级的智能合约功能、多资产组合管理、动态状态管理，跨链兼容性和更复杂的金融应用和去中心化应用（dApps）等。

### **2.1.RGB++ 交易流程**

![img](https://thewebthree.xyz/media/editor/sdasdasd_20241012122322493384.png)

**链外计算**

- 选中下一次要使用的一次性密封条，例如 btc_utxo#2
- 链外计算并生成一笔将要发送到 CKB 上的 RGB++ 交易: CKB_TX_B
- 链外计算 commitment = hash(CKB_TX_B | btc_utxo#1 | btc_utxo#2)

**BTC 交易提交**

- 生成并发送一笔比特币交易 Bitcoin_TX_A, 输入消耗 btc_utxo#1，输出通过 OP_RETURN 加入上面的 commitment

**CKB 交易提交**

- 发送上述 CKB 交易 CKB_TX_B
- 用户的最新状态由 CKB_TX_B.output.data 维护
- 下一次变更状态需要使用 btc_utxo#2、CKB_TX_B.output

**链上验证**

- Bitcoin 验证相关的 utxo 只能被指定用户花费一次
- CKB 上存在 Bitcoin 的轻客户端，它可以验证 Bitcoin 上的相关交易存在 Bitcoin 链上
- Bitcoin 的相关交易作为 ckb 交易的 witness 被提交上来，协助验证
- CKB 进一步验证该 btc 交易花费了正确的 utxo
- CKB 进一步验证该 btc 交易承诺了正确的 commitment
- CKB 验证 CKB 上的状态转移符合预订的合约规则

### **2.1.RGB++ 客户端**

不同于 RGB 协议，RGB++ 的所有交易都在 CKB 上并由 CKB 脚本约束验证，因此 RGB++ 无须独立客户端，用户只需要访问 Bitcoin 和 CKB 轻客户端即可验证所有交易。其中 CKB 轻客户端同样使用 PoW 算法可以实现最近的若干个块头即可验证所有历史交易和状态，进而利用同构绑定验证 RGB++ 的所有交易。

# **十一. 转移证明（Proof of Transfer, PoX）**

**转移证明（Proof of Transfer, PoX）** 是 Stacks 网络中的核心共识机制。它结合了**燃烧证明（Proof of Burn, PoB）** 和比特币区块链，通过将比特币转移到另一个地址（而不是销毁），来提供去中心化、安全性和对 Stacks 区块链的支持。PoX 允许矿工通过锁定比特币并将其转移给 STX 持有者，来参与区块生产，并获得 STX 奖励。

## **1.什么是转移证明（Proof of Transfer, PoX）**

**PoX 共识机制** 是一种创新的区块链共识协议，它利用比特币的稳定性和安全性，为 Stacks 区块链提供支持。矿工通过锁定和转移比特币来竞选区块创建权，而不是像传统的 PoW 那样通过耗费计算能力来挖矿。

在 PoX 中，矿工的角色是通过发送比特币（BTC）来参与 Stacks 网络的共识过程。相比于燃烧比特币（PoB），PoX 通过将比特币分发给 Stacks 网络中的 STX 持有者，形成一种双链的经济激励机制。

以下是 PoX 机制的详细工作流程：

### **1.1.矿工锁定和转移比特币**

- 每个区块周期中，矿工需要锁定一定数量的比特币（BTC），并将这些 BTC 转移给 Stacks 网络中的 STX 代币持有者。
- 这个转移的过程在比特币区块链上进行，矿工通过将比特币发送到特定的地址来参与 PoX 的竞选过程。此地址属于 STX 持有者，而不是一个不可花费的“燃烧地址”。

### **1.2.转移比特币以竞选区块**

- 矿工通过发送比特币给 STX 持有者，表明了他们的贡献，从而竞选成为下一个 Stacks 区块的生产者。
- 矿工转移的比特币数量越多，他们竞选成功的概率就越高。这个过程类似于燃烧证明中的比特币销毁机制，但不同的是，比特币不会被永久销毁，而是分发给 STX 持有者。

### **1.3.区块奖励与交易费**

- 成功创建区块的矿工将获得区块奖励（STX 代币）和网络中的交易费用。
- 这使得矿工既通过锁定和转移比特币来参与网络共识，又能通过赢取区块奖励来获取经济回报。

### **1.4.STX 持有者的奖励**

- 与传统 PoW 或 PoS 共识不同，PoX 还允许 STX 代币持有者通过参与网络共识来获得奖励。STX 持有者通过锁定他们的 STX 代币，能够定期收到矿工转移的比特币奖励。
- 这些 STX 持有者为网络提供了一定的稳定性和安全性，因为他们的参与帮助保证了 Stacks 网络的去中心化特性。

## **2.PoX 的主要特性**

### **2.1.比特币与 Stacks 的双链经济**

- PoX 是一种独特的双链机制，将比特币和 Stacks 紧密连接在一起。比特币是最安全、最去中心化的区块链之一，而 Stacks 利用 PoX 从比特币的安全性中受益。
- 通过 PoX，Stacks 网络的矿工在比特币网络上转移比特币，锁定并转发给 STX 持有者。这种机制使得比特币不仅仅是 Stacks 的安全基础，还为 STX 持有者提供了一种额外的收入来源。

### **2.2. 安全性**

- Stacks 网络通过依赖比特币区块链来确保其安全性。比特币作为全球最成熟的区块链之一，提供了高度的安全性和去中心化，PoX 通过将矿工转移的比特币与 Stacks 进行连接，继承了这种安全性。

### *2.4.能源效率**

- 与传统的工作量证明（PoW）相比，PoX 不需要消耗大量能源进行挖矿。矿工无需通过算力竞争，而是通过转移比特币来获得竞选权。这大大降低了 Stacks 网络的能耗，同时维持了高水平的安全性。

### **2.5.去中心化与激励机制**

- PoX 激励机制不仅奖励矿工，还鼓励 STX 持有者参与网络。他们通过锁定 STX 获得定期的比特币分红，这种双重激励机制有助于保证网络的去中心化，并鼓励长期持有者参与 Stacks 生态系统。

### **2.6.PoX 与其他共识机制的比较**

![img](https://thewebthree.xyz/media/editor/20241012124236_20241012124255915114.png)

**点击图片可查看完整电子表格**

## **3.转移证明的优势**

- **比特币的强大安全性:** 通过在比特币上执行交易，PoX 将 Stacks 网络与比特币的安全性紧密结合。由于比特币是全球最安全的区块链，PoX 利用比特币的区块确认机制，继承了比特币的稳固安全性。
- **能源节约:** 与 PoW 系统相比，PoX 减少了能源消耗。矿工不需要进行密集的计算，只需通过转移比特币来参与区块创建，极大地降低了挖矿的能耗。
- **双重激励机制:** PoX 不仅为矿工提供奖励，还为 STX 持有者创造了新的收入来源。STX 持有者可以通过锁定代币定期获得比特币，这种双重激励机制有助于增加网络的活跃度和参与度。
- **长期经济模型:** PoX 是一种长期可持续的经济模型。通过依赖比特币，Stacks 避免了自己构建复杂的 PoW 系统，并且为 STX 持有者提供了额外的收入来源，吸引了更多参与者。

## **4.转移证明的挑战与潜在问题**

**矿工集中化的风险:** 大量比特币的所有权可能集中在少数几个人手中，这可能导致矿工之间的竞争减少，最终可能威胁到网络的去中心化。

**比特币价格波动的影响:** 比特币的价格波动可能会影响 PoX 机制的稳定性。在比特币价格高企时，矿工可能不愿意通过转移大量比特币参与网络竞选，进而影响 Stacks 网络的矿工数量。

**依赖比特币:** PoX 依赖比特币网络的安全性和去中心化。这意味着如果比特币网络面临攻击或去中心化问题，Stacks 网络也可能受到连带影响。

## **5. POX 图示**

![img](https://thewebthree.xyz/media/editor/523asdasd_20241012122423111192.png)

矿工运行启用挖矿功能的 Stacks 节点参与 PoX 机制。节点实现 PoX 机制，通过四个关键阶段确保正确处理和激励：

- 注册：矿工通过向网络发送共识数据来注册未来的选举
- 承诺：注册矿工转移比特币以参与选举。承诺的 BTC 将被发送给一组参与的 STX 代币持有者
- 选举：可验证的随机函数选择一名矿工，在新的任期内将区块写入 Stacks 区块链
- 组装：当选的矿工通过从内存池中提取交易来编写新区块，并以新的 STX 代币形式收集奖励

矿工在每次提交领导者区块时将比特币提交到**两个**地址。提交到每个地址的金额必须相同。地址是从当前堆叠参与者的奖励集中选择的。地址是使用可验证随机函数选择的，并且确定给定区块的正确两个地址需要监控 Stacks 链。

PoX 挖矿是对烧毁证明 (PoB) 挖矿的一种修改，其中承诺的比特币不是发送到烧毁地址，而是转移到参与堆叠协议的合格 STX 持有者。

# **十二.比特币 Layer2 方案及项目**

![img](https://thewebthree.xyz/media/editor/362561dfdsdf_20241012122444660294.png)

# **十三.比特币跨桥项目 FBTC**

## **1.铸币流程**

![img](https://thewebthree.xyz/media/editor/fgdfgdfg1641654165_20241012122511329046.png)

- 用户将原生 BTC 转移到预先配置的托管地址。
- 的用户与 Bridge 合约进行交互并发起铸币请求。
- 实时监控链上事件的桥接监视器检测到铸造请求。
- Bridge Monitor 还监控比特币主链上的 BTC 存款交易。
- Bridge Monitor 将铸币请求发送给 TSS Gateway。
- TSS 网关发起合约以确认 Bridge 合约的铸造。多个 TSS 节点通过 MPC 算法共同签名构建交易签名。每个 TSS 节点都运行一个独立的风险控制系统，该系统验证存款交易和铸造请求，以确保 FBTC 铸造的安全。
- 在目标链上确认铸造交易后，FBTC 代币即被铸造。

## **2.燃烧币流程**

![img](https://thewebthree.xyz/media/editor/dfgdfg216165165_20241012122536419080.png)

- 用户与 Bridge 合约进行交互并发起销毁请求。
- 桥接合约会销毁合格用户的 FBTC 代币。
- 桥梁监视器 (Bridge Monitor) 监视烧毁请求事件。
- 桥接监控器将提款请求发送至 TSS 网关。
- TSS 网关发起 BTC 转账，将指定数量的 BTC 转账到符合条件的用户预先设置的提现地址。多个 TSS 节点通过 MPC 算法共同签名构建交易签名。每个 TSS 节点都运行一个独立的风险控制系统，用于验证 BTC 转账交易和销毁请求，以确保 FBTC 解包的安全。
- 在比特币主链上确认提现交易后，TSS Gateway 调用 Bridge 合约确认提现请求已被处理。

## **3.跨链流程**

![img](https://thewebthree.xyz/media/editor/dfsdfsdfs6541641654_20241012122555157725.png)

- 用户与源链的桥合约进行交互，发起跨链请求。
- 桥接合约会烧毁用户的 FBTC。
- 桥接监视器实时监控源链上的事件，并立即检测到跨链请求。
- 桥接监视器将跨链请求发送至TSS网关。
- TSS Gateway 向目标链上的 Bridge 合约发起合约调用，以确认 FBTC 跨链操作。多个具有单独风险控制的 TSS 节点共同签署确认交易。
- 在目标链上确认跨链交易后，将为用户铸造指定数量的 FBTC 代币。

# **十四.几个知名的比特币生态项目简介**

## **1.Babylon**

Babylon 项目设计了可扩展比特币的安全协议，以保护去中心化的世界。Babylon 主要利用了比特币的三个特征：

- 比特币资产
- 比特币 PoW 保护的时间戳服务器
- 比特币世界上最具抗审查性的区块空间。

Babylon 是一套比特币安全共享协议。目前，它包括两个协议：

- 比特币时间戳：该协议将任何数据（如 PoS 区块链）的简洁且可验证的时间戳发送到比特币；
- 比特币质押：该协议允许比特币资产通过无需信任（和自我托管）的质押为任何去中心化系统提供经济保障。

Babylon 底层基于 Cosmos SDK 构建Babylon 节点， 使用 BTC 进行质押，架构图如下：

![img](https://thewebthree.xyz/media/editor/xcvxcvxcv56353_20241012122616026128.png)

### **1.1.顶部组件 Bitcoin 相关**

- **Vigilante Reporter** 和 **Vigilante Submitter**：监控比特币网络并向Babylon项目报告相关网络数据和信息。
- **Checkpointing Monitor**：监视区块链的检查点，确保数据的一致性。
- **BTC Staking Monitor** 和 **BTC Staker**：比特币的质押和奖励机制模块。

### **1.2.中部主体，Babylon 节点**

- **Epoching**、**Checkpointing**：处理区块链时间段和检查点的组件，用于维护网络的安全和数据一致性。
- **BTC Checkpoint**、**BTC Light Client**：会验证 Vigilante Reporter 报告的 Babylon BTC 检查点，并根据 BTC Light Client 模块根据检查点的深度向 Checkpointing 模块提供这些检查点的确认状态。
- **Zone Concierge**：模块从连接的IBC 轻客户端中提取经过验证的消费者区域标头，并根据承载它们的 Babylon 交易的比特币确认状态维护它们的比特币确认状态。它通过IBC连接使用可验证证明将比特币确认状态传达给消费者区域
- **BRT Staking**、**Finality**、**Incentive**：质押机制、网络最终性保证以及激励分发。

### **1.3.底部组件**

- **EOTS Manager**：管理一次性签名 (EOTS) 公共随机性。
- **Finality Provider**：一个独立程序，允许注册和维护最终性提供者。它监控最终性提供者是否包含在活动集中，提交可提取一次性签名 (EOTS) 公共随机性，并为区块提交最终性投票。最终性投票是通过连接到独立 EOTS 管理器守护程序创建的，该守护程序 负责安全维护最终性提供者的私钥。
- **Covenant Emulator**：契约模拟委员会成员使用的独立程序。它通过监控待处理的质押请求、验证其内容并提交必要的签名来模拟契约功能。

### **1.4.底部的连接部分**

- **CometBFT**：基于 tendermint 改造的共识算法模块，用于在多个节点之间达成一致。
- **IBC Relayer**：Cosmos 跨链通信中继器，在不同的区块链之间传递状态信息；IBC 中继器维护 Babylon 与其他消费者区域 (CZ) 之间的IBC 协议连接。它负责更新 Babylon 账本中的 CZ 轻客户端，以启用检查点，并将检查点信息传播到部署在 CZ 内的 Babylon 智能合约。有不同的 IBC 中继器实现可以实现此功能。最值得注意的是：
- Cosmos Relayer：一个用 Go 编写的功能齐全的中继器。
- Babylon Relayer：Cosmos Relayer 的包装器，可以维持单向的 IBC 连接。建议在 Consumer Zone 未部署 Babylon 智能合约时使用。
- Hermes Relayer：一个用 Rust 编写的功能齐全的中继器。
- **Babylon Contract**：CosmWasm 智能合约旨在部署在消费者区域。它启用比特币检查点功能[，](https://cosmwasm.com/)而无需在消费者区域的代码库中引入侵入性更改。基于比特币检查点功能，消费者区域可以根据其检查点在比特币分类账中的纳入情况做出决策（例如执行 BTC 辅助解除绑定请求）。

## **2.stacks**

Stacks 是一个开源项目，旨在通过将智能合约和去中心化应用（dApps）引入比特币区块链，从而扩展比特币的功能。它通过名为 "Proof of Transfer" (PoX) 的共识机制，将新一代的区块链与比特币连接起来。

### **1.核心组件**

**Stacks 区块链：**Stacks 区块链是一个独立的区块链，与比特币紧密耦合。它通过 PoX 共识机制利用比特币的安全性和稳定性来实现自身的去中心化和安全性。

**Proof of Transfer (PoX)：** PoX 是一种独特的共识机制，允许 Stacks 区块链重用比特币的算力。矿工通过在比特币网络上支出 BTC 来竞选新的 Stacks 区块的创建权，从而在 Stacks 网络上获取奖励。

**Clarity 智能合约语言：**Clarity 是 Stacks 网络上使用的智能合约语言，专为安全和可预测性而设计。它是一种非图灵完备的语言，这意味着它在执行时的行为是可预测的，并且可以在执行前完全分析其运行结果。

### **2.POX 共识算法详解**

Proof of Transfer (PoX) 是一种创新的共识机制，旨在利用现有区块链（如比特币）的安全性来保护新兴区块链（如 Stacks）的网络。PoX 通过让矿工在比特币区块链上支出 BTC 来竞选新块的生成权，并将这些 BTC 奖励给参与者，从而实现新旧区块链的连接和安全共享。

### **3.参与者**

- **矿工（Miners）**：在 PoX 机制中，矿工通过支出比特币来竞争 Stacks 区块的创建权。
- **堆叠者（Stackers）**：持有 STX 代币并愿意参与 Stacking 的用户。他们通过锁定 STX 代币来支持网络的稳定性和安全性，并获得 BTC 奖励。

### **4.工作流程**

- **矿工提交 BTC**：矿工将一定数量的比特币（BTC）发送到指定的比特币地址。这些比特币被称为“竞选比特币”。
- **选择区块创建者**：使用加权随机选择算法，从所有提交了竞选比特币的矿工中选出一个矿工来创建下一个 Stacks 区块。
- **分发 BTC 奖励**：选出的矿工创建新的 Stacks 区块，且之前提交的 BTC 奖励会分发给参与 Stacking 的堆叠者。

### **5.主要功能**

- **智能合约：** 通过 Clarity 编写和执行智能合约，使开发者能够创建复杂的 dApps，同时利用比特币的安全性。
- **去中心化应用（dApps）：**开发者可以在 Stacks 平台上创建和部署去中心化应用，这些应用可以与比特币直接交互，并使用 BTC 作为主要货币。
- **Stacking：**Stacks 代币持有者可以通过参与 Stacking 来帮助保护网络并获得 BTC 奖励。Stacking 类似于质押，但它通过锁定 STX 代币并参与 PoX 机制来实现。

### **6.实际应用**

Stacks 已经有多个实际应用和项目在其平台上运行，包括去中心化金融（DeFi）、NFT 市场以及社交媒体平台。这些应用展示了 Stacks 如何利用比特币的安全性和 Clarity 智能合约的灵活性来创建创新的区块链解决方案。

# **十五.总结**

在本文中，我们探讨了比特币的关键特性以及一些具有代表性的比特币生态系统项目。尽管我们只涉及了部分项目，但值得注意的是，比特币生态系统中还包含许多其他知名项目。例如，近期备受关注的 Nervos Network（CKB），以及多个基于以太坊改良的侧链和第二层解决方案。这里不再详细展开介绍这些项目。

**注意：本文仅用于 Bitcoin 产品生态学习，不构成任何投资建议, 文章内容是从 The Web3 社区产品课程课件资料里提取而来，部分内容可能不完整，若阅读过程中造成困扰，可以联系 The Web3 小伙伴帮忙解答**