# 雷达哔哔哔 - Corda

## 标签：

* Blockchain，DLT

## 目标受众：

* 区块链架构师，开发人员

## 关注问题：

* 作为一个联盟链平台，Corda 允许不同组织之间直接达成没有中间人参与的交易，这大大提高了交易的效率。但是“传统”区块链平台要求所有用户复制所有交易，这带来了大量的重复和浪费，性能很难满足现实商业世界的要求，另外，尽管有加密技术存在，大家依然担心数据的隐私性是否能够得到足够保证。

## 解决方案

* Corda 在继承了区块链点对点网络的基础上，将网络区分为不同的兼容区（ compatility zone），每个兼容区内可以部署不同的智能合约（smart contract），同时辅以可插拔的共识机制（pluggable consensus），以便针对不同类型的应用对共识算法进行优化。同时，在交易数据的存储上，作为联盟链的 Corda 采用了每个节点只需存储与自己参与或需要知道的数据，全网共识由兼容区内的公证人（Notary）节点集群来保证。

## 解读

随着区块链热度的逐渐消退，公众对于区块链技术的看法逐渐趋于理性，依然对区块链技术保持热忱的人们开始思考区块链究竟能带来怎样的商业价值，这就要求各大区块链平台针对普及区块链遇到的阻力提供解决方案。Corda 作为其中的一员，将关注点投入在如下几个方面：

* 隐私性（privacy）
* 交易可终结性（transaction finality）
* 参与方身份认证（legally identified parties）
* 可扩展性（ability to scale）
* 开发者效率和企业级集成（developer productivity and enterprise integration）

### 隐私性（privacy）

将我所有的交易数据发布到所有节点（包括竞争对手）？任何一位企业管理者在听到这样的提案时都没法坦然接受这样的技术“革命”吧？更何况很多行业还面临着合规性审计的压力。

Corda 选择只让交易相关方存储交易数据。如何阻止“双花”（double spend）？交给公证人（Notary）节点吧。

### 交易可终结性（transaction finality）

什么？我付了钱还要等6个区块才能确认交易达成？还会分叉？那交易到底是发生了还是没发生？我的交易是薛定谔的猫吗？

别担心，Corda 将网络分为不同的兼容区（compatibility zone），并允许在每个兼容区内自主配置共识算法（pluggable consensus），以帮助兼容区内的节点以最快速度达成共识。

### 参与方身份认证（legally identified parties）

公有链每个客户端和节点都不需要使用物理世界中真实存在的身份进行交易，而对于真实商业世界中的交易，我的交易对手方对我考虑一笔交易至关重要。Corda  作为联盟链，使用业界已经比较成熟的 X509 证书为每个节点提供身份。

### 可扩展性（ability to scale）

区块链平台主要的性能瓶颈在于处理每笔交易并达成共识的过程中，这里存在着巨大的网络开销和计算工作。

在 Corda 中，达成共识主要由公证人节点负责。公证人节点的效率和可扩展性决定了整个平台的可扩展性。Corda 为公证人节点设计了良好的可扩展性，随着网络中参与者数量的增加，公证人节点也可以水平扩容。

### 开发者效率和企业级集成（developer productivity and enterprise integration）

Corda 选择了已经发展成熟 JVM 平台以及 Kotlin 语言作为开发工具，关系型数据库作为数据存储。大部分企业的 IT 部门早已经在这些领域驾轻就熟，大大降低了企业拥抱新技术的技术切换成本。

## Blip 来源

::Platforms (ASSESS[ 2017.11 | 2018.05 ])::
> [Corda | Techniques | Technology Radar | ThoughtWorks](https://www.thoughtworks.com/radar/platforms/corda)

## 相关 Blip

* [Blockchain beyond bitcoin | Techniques | Technology Radar | ThoughtWorks](https://www.thoughtworks.com/radar/techniques/blockchain-beyond-bitcoin)
* [Ethereum | Platforms | Technology Radar | ThoughtWorks](https://www.thoughtworks.com/radar/platforms/ethereum)
* [Hyperledger | Platforms | Technology Radar | ThoughtWorks](https://www.thoughtworks.com/radar/platforms/hyperledger)
* [Quorum | Platforms | Technology Radar | ThoughtWorks](https://www.thoughtworks.com/radar/platforms/quorum)

## 延展阅读

* [Corda Introduction](https://www.corda.net/discover/technology.html)
* [分布式账本 Corda](https://www.jianshu.com/p/8c5ed8f96078)
* [Ethereum VS Hyperledger Fabric VS Corda](https://medium.com/@philippsandner/comparison-of-ethereum-hyperledger-fabric-and-corda-21c1bb9442f6)
