![Ethereum for decentralized applications](https://upload-images.jianshu.io/upload_images/217988-c178b9527b06b960.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 标签：
Blockchain，DApp，Ethereum

## 目标受众：
* 目标受众：区块链开发人员

## 关注问题：
DApp 是一种运行在去中心化 P2P 网络上，没有任何一个节点可以获得完全控制权并且源码开放，含有内部激励的网络应用。

DApp和App之间最大的不同就在这D（Decentralized）上，这个D有两层含义，第一它具备分布式（Distributed）的特征，第二它具备分权（Decentralized）的特征。

分布式理解起来比较简单，这个app是部署到多个节点上的，不用害怕单点故障。
关键是这个分权比较难以理解。在这里，分权其实也包含两层含义。第一点，应用的开发者在上线应用之后，就不能随意修改升级应用内容，当然更加不可能修改数据；第二点，应用本身具有博弈的特点，都把用户想象成理性经济人，做事之前考虑成本，这也是为什么大多数DApp都有它内置的代币（Token，也作通证）。


## 解决方案：
DApp 是去中心化应用（Decentralized Application）的简称。与之相对的是中心化应用（Centralized Application），比如现在常见的BS模式下的 web 应用。而中心化应用通常会出于可用性的考虑将实例部署到多个节点上，形成分布式应用。所以说，中心化应用可以是分布式的，也可以是非分布式，但是去中心化应用一定是分布式的。那么由此就会引出一个思考，去中心化应用和现在的分布式应用的区别到底在哪里呢？去中心化应用具有四个基本特点：

* 开源
* 内部货币
* 去中心化的共识机制
* 无单点故障缺陷

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

## 相关Blip

## 延展阅读：
* [Decentralized Applications](https://blockchainhub.net/decentralized-applications-dapps/)
* [Introduces and lists Ethereum dapps](https://github.com/ethereum/wiki/wiki/Decentralized-apps-(dapps))

## 支持工具：
* [Solidity](https://solidity.readthedocs.io/en/v0.4.24/)
* [Truffle](https://github.com/trufflesuite/truffle)
* [Ganache](https://truffleframework.com/ganache)
