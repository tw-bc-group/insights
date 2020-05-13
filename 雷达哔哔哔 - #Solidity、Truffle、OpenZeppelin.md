# 雷达哔哔哔 - #Solidity、Truffle、OpenZeppelin
# 1. 推荐度：
Solidity: ASSESS[2017.NOV -> 2018.MAY]
Truffle: ASSESS[2017.NOV -> 2018.MAY]
OpenZeppelin: TRIAL[2018.MAY]

# 2. 所属象限：
Languages & Frameworks

# 3. 目标受众：
* 智能合约开发人员

# 4. 关注问题：
* Solidity 是一门语法类似于 JavaScript 的静态类型语言，是目前以太坊平台上智能合约编写的主要语言。
* Truffle 是一个将 web 开发经验带入以太坊平台的开发框架，它主要帮助开发者节省了很多手动工作，包括封装了智能合约的编译，库的链接等。提供了包含：Truffle、Ganache、Drizzle。
* OpenZeppelin 关注于区块链智能合约的安全，为开发者提供了很多直接可用的库与安全的方法。

# 5. 解读
随着社区对区块链智能合约的广泛关注，在开发人员着手写智能合约之前，本文将结合技术雷达列出的 Solidity、Truffle、OpenZeppelin，从实际开发着手，就以下几个方面给出建议：
* 智能合约的开发
* 智能合约的测试与调试
* 智能合约的部署

## a. 智能合约的开发
1. truffle init 可直接生成 Solidity 智能合约模版，其目录结构如图：
![](%E9%9B%B7%E8%BE%BE%E5%93%94%E5%93%94%E5%93%94%20-%20%23Solidity%E3%80%81Truffle%E3%80%81OpenZeppelin/F6505601-8936-4D72-A30A-AC329BB79BF4.png)
2. 在使用 Truffle 进行智能合约开发时，要注意 Solidity 语言中定义的 Event 与 Function 是具有不同作用的，Event 用来记录 Log，通常命名是以大写字母开头，在最新版本的 Solidity 中，推荐使用：emit Event() 的方式
![](%E9%9B%B7%E8%BE%BE%E5%93%94%E5%93%94%E5%93%94%20-%20%23Solidity%E3%80%81Truffle%E3%80%81OpenZeppelin/73E2D49A-2342-47E0-8751-F53C14685501.png)
3. 智能合约的编码过程中，因为后续的智能合约升级不能像现在的程序一样直接升级，因此可以采用“熔断器”模式，通过为智能合约设置状态值，而起到禁用当前合约的作用
![](%E9%9B%B7%E8%BE%BE%E5%93%94%E5%93%94%E5%93%94%20-%20%23Solidity%E3%80%81Truffle%E3%80%81OpenZeppelin/E11C6A87-826C-483D-ABBD-FF5E878B721E.png)
4. OpenZeppelin 在写智能合约中提供了很多有用的库，比如，安全的“加减乘除”可以有效的防止在使用 solidity 原生的“加减乘除”是出现的上溢和下溢问题。
![](%E9%9B%B7%E8%BE%BE%E5%93%94%E5%93%94%E5%93%94%20-%20%23Solidity%E3%80%81Truffle%E3%80%81OpenZeppelin/D5B3D4D2-F4A5-44A5-8A63-98DF7805DA9A.png)
5. 同时，OpenZeppelin 也提供了诸如 ERC20/ERC721 等多功能的库，在开发过程中只需继承就可以创建符合规则的 Token。

## b. 智能合约的测试与调试
1. Truffle 支持使用 NodeJs 写测试，在 test 目录下新建 *.js 文件即可：![](%E9%9B%B7%E8%BE%BE%E5%93%94%E5%93%94%E5%93%94%20-%20%23Solidity%E3%80%81Truffle%E3%80%81OpenZeppelin/C7F9C65B-76C9-4C3B-AC32-008554614107.png)

2. 在本地调试时，也可以通过安装 truffle 套件中的 Ganache-CLI 与命令`truffle console`连接。
![](%E9%9B%B7%E8%BE%BE%E5%93%94%E5%93%94%E5%93%94%20-%20%23Solidity%E3%80%81Truffle%E3%80%81OpenZeppelin/9C4BFC34-4CF4-4C9D-B24D-58D1E23D869A.png)

## c. 智能合约的部署
在区块链网络中，一切都是不可篡改的，所以，在智能合约的升级的过程中，其实不存在智能合约的代码更改，而是相当于部署了一个新的合约，而这个合约做着与原合约相同以及升级的事情，那么这个时候，如何关闭旧合约就成了一个问题。
实际上，解决这个问题有几个办法：
1. “熔断器”模式，可以帮助开发人员在合约升级后关闭合约的操作入口，为了能够使用历史数据，数据的导出也是需要手动迁移的

# 6. 工具：
VisualStudio Code / Sublime / IntellijIdea

# 7. 延展阅读：
[Solidity | Technology Radar | ThoughtWorks](https://www.thoughtworks.com/cn/radar/languages-and-frameworks/solidity)
[Truffle | Technology Radar | ThoughtWorks](https://www.thoughtworks.com/cn/radar/languages-and-frameworks/truffle)
[OpenZeppelin | Technology Radar | ThoughtWorks](https://www.thoughtworks.com/cn/radar/languages-and-frameworks/openzeppelin)
[以太坊黄皮书](https://github.com/ethereum/yellowpaper)
[Solidity v0.4.25 文档](https://solidity.readthedocs.io/en/v0.4.25/)
[Truffle Framework 官网](https://truffleframework.com/)
[OpenZeppelin 官网](https://openzeppelin.org/)

#技术/雷达哔哔哔