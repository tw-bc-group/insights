# 雷达哔哔哔 - Ethereum for decentralized applications

![Ethereum for decentralized applications](https://upload-images.jianshu.io/upload_images/217988-c178b9527b06b960.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 标签：

Blockchain, DApps, Decentralized Applications, Ethereum

## 目标受众：

* 目标受众：区块链产品经理、架构师、开发人员

## 关注问题：

* 区块链技术起源于比特币，由于天生具备数字货币的特质，这项技术在 fintech 领域受到广泛关注，尤其获得了金融服务业的青睐。不过，区块链技术在以太坊（Ethereum）的拓展下，已经具备开发各种应用的能力，这些部署在区块链上通常含有内部代币激励并且开源的应用被称之为去中心化应用（Decentralized Application, DApp），DApp 就像现在的应用一样，能够惠及人们生活的方方面面，同时融入区块链的独特优势。

## 解决方案：

* 以太坊是一个部署和运行 DApp 的后端程序——智能合约（Smart Contracts）的去中心化平台。它提供了专门面向合约的编程语言 Solidity 和运行合约的虚拟机（EVM）实现，得益于其周边的开源生态，很多开源工具，如：Truffle, Ganache, MetaMask, MyEtherWallet 也让编写和部署智能合约变得更加方便。同时，以太坊还维护了多条测试链，如：Ropsten, Kovan 和 Rinbkey 辅助开发者测试合约，从而减少部署到主网的风险。

## 解读：

以太坊的强大之处在于它不仅内置了可用于转账的以太币，还围绕以太币构建了部署和运行智能合约的去中心化平台。智能合约就是一个“高度权威”的中间机构，任何人都可以利用智能合约定下“如果...那么...”的交易条款，然后把交易中的钱财用以太币的形式存入其中。一旦预设条件满足，合约就会自动执行，比如：把合约中的以太币打给交易的某一方。

有了智能合约，我们甚至可以在一个没有淘宝这种电商平台的情况下，和陌生的个体商户做买卖！

商家发布了一个买卖合约。合约里说（详细见下图）：
1. 商家有一件商品价值1块钱，顾客想要购买，需要往合约里存入1块钱
2. 商家确认合约里有1块钱之后就会发货
3. 然后顾客确认收货之后，合约自动把这1块钱打给商家

![第一回合](https://insights.thoughtworks.cn/wp-content/uploads/2018/12/1.jpeg)

如果你以为这就能达成交易，就too young too simple。 因为客户往合约里存入1块钱之后，如果商家没有发货，那么合约中规定的流程就没法继续下去，顾客也没法从合约中取出这1块钱。所以只要顾客不傻，他就不会打进去这1块钱，这次交易不可能完成。

商家可以这样改良买卖合约。合约里说（详细见下图）：
1. 商家先往合约里存入1块钱，证明自己有价值1块钱的商品
2. 顾客想要购买，需要得往合约里存入2块钱（想想为什么不能是1块钱？）
3. 商家确认合约里有3块钱之后就会发货
4. 然后顾客确认收货之后，合约自动把3块钱中的2块钱打给商家
5. 合约剩余的1块钱还给顾客

![第三回合](https://insights.thoughtworks.cn/wp-content/uploads/2018/12/2.jpeg)

通过这个例子，我们很惊奇地发现，在智能合约的辅助下，两个陌生人在没有中间人担保的情况下也可以完成一笔买卖的。

## Blip来源：

::Techniques (ASSESS[ 2017.11 | 2018.05 ])::

## 相关Blip：

* [Solidity | Languages and Frameworks | Technology Radar | ThoughtWorks](https://www.thoughtworks.com/radar/languages-and-frameworks/solidity)
* [Truffle | Languages and Frameworks | Technology Radar | ThoughtWorks](https://www.thoughtworks.com/radar/languages-and-frameworks/truffle)
* [Openzeppelin | Languages and Frameworks | Technology Radar | ThoughtWorks](https://www.thoughtworks.com/radar/languages-and-frameworks/openzeppelin)
* [Ethereum | Platforms | Technology Radar | ThoughtWorks](https://www.thoughtworks.com/radar/platforms/ethereum)
* [Quorum | Platforms | Technology Radar | ThoughtWorks](https://www.thoughtworks.com/radar/platforms/quorum)

## 延展阅读：

* [The General Theory of Decentralized Applications, Dapps](https://github.com/DavidJohnstonCEO/DecentralizedApplications)
* [Decentralized Applications](https://blockchainhub.net/decentralized-applications-dapps/)
* [Introduces and lists Ethereum dapps](https://github.com/ethereum/wiki/wiki/Decentralized-apps-(dapps))
* [购买合约源码](https://github.com/crypedit/purchase)

## 支持工具：

* [Solidity](https://solidity.readthedocs.io/en/v0.4.24/)
* [EVM](https://github.com/ethereum/wiki/wiki/Ethereum-Virtual-Machine-(EVM)-Awesome-List)
* [Truffle](https://github.com/trufflesuite/truffle)
* [Ganache](https://truffleframework.com/ganache)
* [MetaMask](https://metamask.io/)
* [MyEtherWallet](https://www.myetherwallet.com/)
