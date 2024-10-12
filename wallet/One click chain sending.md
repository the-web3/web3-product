# The Web3 社区产品课程之一键发链



# **一. 公链类别**

- Layer1: 意义不大
- Layer2: 有意义
- Layer3: 未来有意义

# **二. Layer2 的模块**

![img](https://thewebthree.xyz/media/editor/2858933sds_20241012133331704041.png)

# **三.一键发链的模块解析**

## **1.Rollup**

- 交易数据的 Rollup

![img](https://thewebthree.xyz/media/editor/dsasd36994_20241012133353144541.png)

- 交易证明的 Rollup

![img](https://thewebthree.xyz/media/editor/wqee3639633_20241012133417575977.png)

## **2.证明模块**

- 欺诈证明：主要用在 op rollup, 出发点是 sequencer 是不做恶的，但是我们乐观的认为，其实 sequencer 是有做恶的风险，欺诈证明就是用来防止 sequencer 及其相关组件作恶。
- 有效证明：主要用在 zk(基于零知识证明) rollup, 对每一笔交易都进行 zk 证明，链下 zk prove 生成证明，提交到链上验证

### **2.1.欺诈证明模块抽象**

![img](https://thewebthree.xyz/media/editor/36921455asdasd_20241012133439070675.png)

### **2.2.有效证明**

![img](https://thewebthree.xyz/media/editor/2312sdasdf666_20241012133459535822.png)

## **3.faster finality network**

快速最终验证网络

- zk rollup: 需要几个小时的证明 L2->L1 的提现才能成功
- op rollup: 需要 7 天的欺诈证明时间，才能提现成功
- 加快二层区块的最终确定
- 当前状态
- 少则 10 多分钟
- 多则时间更长
- 二层区块的最终确定
- 几秒钟之内完成区块的最终确定

![img](https://thewebthree.xyz/media/editor/1231asdasd_20241012133522166865.png)

# **四.总结**