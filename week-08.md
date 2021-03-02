# Token
## 什么是token
  如今，基于区块链的Token将这个词重新定义为基于区块链的抽象概念，可以被拥有，并代表资产，货币或访问权

## 如何使用token
### *货币* 
   Token可以作为一种货币形式，其价值通过私人交易来确定。例如，ether或bitcoin
### *资源*
   Token可以表示在共享经济或资源共享环境中获得或生成的资源。例如，表示可通过网络共享的资的存储或CPU的Token
### *资产*
   Token可以代表内在或外在，有形或无形资产的所有权。例如，黄金，房地产，汽车，石油，能源等
### *访问*
   Token可以代表访问权限，可以访问数字或实体资产，例如论坛，专属网站，酒店房间，租车。
### *权益*
   Token可以代表数字组织（例如DAO）或法律虚拟主体（例如公司）中的股东权益
### *投票*
   Token可以代表数字或法律系统中的投票权。
### *收藏品*
   Token可以代表数字（例如CryptoPunks）或物理收藏品（例如绘画）
### *身份*
   Token可以代表数字（例如头像）或合法身份（例如国家ID）。
### *证明*
   Token可以代表某些机构或去中心化的信用系统（例如婚姻记录，出生证明，大学学位）的认证或事实证明。
### *实际用途*
   Token可用于访问或支付服务。

## 交易对手风险
  ``` 
  交易对手风险是交易中的其他方不能履行其义务的风险。由于在交易中增加了两个以上的交易方，某些类型的交易会产生额外的交易对手风险。例如，如果你持有贵金属存款证明并将其出售给某人，则该交易中至少有三方：卖方，买方和贵金属的保管人。有人持有有形资产，必要时他们成为一方并为涉及该资产的任何交易添加交易对手风险。当资产通过交换所有权信息而间接交易时，资产托管人有额外的交易对手风险。他们有资产吗？他们是否会根据Token的转让（例如证书，契约，所有权或数字Token）识别（或允许）所有权的转移？在数字Token的世界中，了解谁持有由Token表示的资产以及适用于该基础资产的规则很重要 
  ```
## 使用Tokens：效用或权益
大多数项目都以两种方式之一使用Token：要么是“实用Token”，要么是“权益Token”。很多时候，这两个角色是混合在一起的，难以区分

- `实用Token`是那些需要使用Token来支付服务，应用程序或资源的Token。实用Token的例子包括代表资源的Token，如共享存储，访问社交媒体网络等服务，或将ether作为以太坊平台的gas。相比之下，权益Token是代表创业公司股票的Token
- `股权Token`可以像享有利润和分红的无投票权股份一样有限，或者向去中心化自治组织的有投票权的股票一样广泛，其中平台是通过Token持有者的多数投票管理的

## Token标准
### ERC20 Token 标准
- 第一个标准由Fabian Vogelsteller于2015年11月引入，作为以太坊征求意见（ERC）。它被自动分配了GitHub发行号码20，从而获得了名字“ERC20 Token”。绝大多数Token目前都基于ERC20。ERC20征求意见最终成为以太坊改进建议EIP20，但大多仍以原名ERC20提及。你可以在这里阅读标准：https://github.com/ethereum/EIPs/blob/master/EIPS/eip-20.md
- ERC20是_可替换Token_的标准，意味着ERC20标记的不同单元是可互换的，没有唯一属性。
- ERC20标准为实现Token的合同定义了一个通用接口，这样任何兼容的Token都可以以相同的方式访问和使用
- 发布我们自己的ERC20Token
### ERC223 - 一种建议的Token合同接口标准
```
ERC223提案试图通过检测目的地地址是否是合同来解决无意中将Token转移到合同（可能支持或不支持Token）的问题。ERC223要求用于接受Token的契约实现名为+TokenFallback+的函数。如果传输的目的地是合同并且合同不支持Token（即不实现+TokenFallback+），则传输失败
```
### ERC777 - 一种建议的Token合同接口标准
#### 该提案有几个目标，包括:
- 提供ERC20兼容性界面
- 使用send功能传输Token，类似于ether传输
- 与ERC820兼容Token合同注册
- 合同和地址可以通过在发送之前调用TokensToSend函数来控制它们发送的Token
- 通过在接收者中调用TokensReceived函数来通知合同和地址
- Token传输交易包含 userData 和 operatorData 字段中的元数据
- 无论是发送到合同还是EOA，都以相同的方式运作

https://github.com/ethereum/EIPs/issues/777

### ERC721 - 不可替代的Token（契据）标准
ERC721提案是不可互换的Tokens标准，也称为契据,deeds。
```
不可互换的Token追踪独特事物的所有权。拥有的东西可以是数字项目，例如游戏物品或数字收藏品。或者，这种东西可以是物理事物，其物主通过Token进行跟踪，例如房屋，汽车，艺术品等。契约也可以代表负值的东西，例如贷款（债务），留置权，地役权等。ERC721标准对所有权由契约追踪的事物的性质没有限制或期望，只是它可以是唯一标识，在这个标准的情况下是由256位标识符实现的。

```
初步建议： https://github.com/ethereum/EIPs/issues/721

继续讨论： https://github.com/ethereum/EIPs/pull/841


## Token接口标准的扩展
### *所有者控制*
特定地址或一组地址（多重签名）具有特殊功能，例如黑名单，白名单，铸造，恢复等。
### *燃烧*
Token燃烧是指Token被转移到不可靠的地址或删除余额并减少供应时故意销毁。
### *Minting*
以可预测的速率添加Token的总供应量的能力，或通过Token创建者的“命令”添加的能力。
### *Crowdfunding*
提供Token销售的能力，例如通过拍卖，市场销售，反向拍卖等。
### *上限*
总供给的预定义和不可改变的限制，与“minting”功能相反。
### *恢复“后门”*
恢复资金，反向传输或拆除由指定地址或一组地址激活的Token（多重签名）的功能。
### *白名单*
限制Token传输仅限于列出的地址的功能。在经过不同司法管辖区的规则审核后，最常用于向“经认可的投资者”提供Token。通常有一种更新白名单的机制。
### *黑名单*
通过禁止特定地址来限制Token传输的能力。通常有更新黑名单的功能。
## ICO
https://www.investopedia.com/terms/i/initial-coin-offering-ico.asp












