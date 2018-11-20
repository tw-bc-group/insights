# 雷达哔哔哔 - Ethereum for decentralized applications

![Ethereum for decentralized applications](https://upload-images.jianshu.io/upload_images/217988-c178b9527b06b960.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 标签：

Blockchain, DApps, Decentralized Applications, Ethereum

## 目标受众：

* 目标受众：区块链产品经理、架构师、开发人员

## 关注问题：

* 区块链技术起源于比特币，由于天生具备数字货币的特质，这项技术在 fintech 领域受到广泛关注，尤其获得了金融服务业的青睐。不过，区块链技术在以太坊（Ethereum）的拓展下，已经具备开发各种应用的能力，这些部署在区块链上通常含有内部代币激励并且开源的应用被称之为去中心化应用（Decentralized Application, DApp），DApp 就像现在的应用一样，能够惠及人们生活的方方面面，同时融入区块链的独特优势。

## 解决方案：

* 以太坊是一个部署和运行 DApp 的后端程序——智能合约（Smart Contracts）的去中心化平台。它提供了专门面向合约的编程语言 Solidity 和运行合约的虚拟机（EVM）实现，得益于其周边的开源生态，很多开源工具，如：Truffle, Ganache, MetaMask, MyEtherWallet 也让编写和部署智能合约变得更加方便。同时，以太坊还维护了多条测试链，如：Ropsten, Kovan 和 Rinbkey 辅助开发者测试合约，减少部署到主网的风险。

## 解读：

想象一个场景，我们在一个没有淘宝这种电商平台下，怎么和个体商家做交易？

假想一下，商家发布了一个合约，合约里说，我这里有一件商品价值1块钱，你给这个合约打入一块钱，我就把商品发过去，然后你那边确认收货之后，我就收到这1块。

![第一回合](https://upload-images.jianshu.io/upload_images/217988-e0e24f705c4c683d.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

听上去不错，但是这里面有问题。如果用户打进1块钱，商家根本没有货，那用户只能白白浪费一块钱。只要用户不傻，他就不会打进去这1块钱，这个交易不可能完成。

怎么办？商家说那好，我先打进去1块钱表示我这里有1块钱的商品，这样就能确保我发货。然后用户打入1块钱，然后商家发货，用户签收，商家得到2块钱。

![第二回合](https://upload-images.jianshu.io/upload_images/217988-1ce43a937d7c29f8.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

听上去不错，但是这里面还是有问题。如果用户收到货之后，不去触发签收操作呢？对于用户而言，没啥损失，但是商家不仅损失了商品，还损失了1块钱。

怎么办？用户说那好，你先打进去1块钱，我打进去2块钱。我收到商品之后，自然会触发签收操作，那样你就得到了2块钱，返还我1块钱。如果我不进行这样的操作，就会损失1块钱呢。

![第三回合](https://upload-images.jianshu.io/upload_images/217988-48a43efdd6fb35ab.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

听上去不错，不过我们稍微钻点牛角尖，就会说刚才方案还是有漏洞，商家可能会用1块钱套住用户2块钱的，就是不发货。那商家就得和用户一样打进去2块钱，但是用户收货之后，完全会考虑我只损失1块钱，你损失了3块钱，那我就不签收哈哈哈。

![第四回合](https://upload-images.jianshu.io/upload_images/217988-777f295a7f7f90c3.jpeg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

不过，我们还是基于理性经济人的假设，商家是想通过买东西赚钱的，所以他在抵押1块钱的情况下，一定会发货。

通过这个例子，我们很容易发现，在没有中间人担保的场景下，两个陌生人也是可能完成一笔交易的。这里面充满了博弈的套路，在实际编码的过程中，最好有两个人扮演不同的角色，然后坐到一起，从自己的利益出发，达成交易，而且使交易的信任成本最小化。

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
* [Truffle](https://github.com/trufflesuite/truffle)
* [Ganache](https://truffleframework.com/ganache)
