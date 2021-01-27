- [黄皮书](#黄皮书)
- [客户端分类](#客户端分类)
- [轻量级以太坊客户端](#轻量级以太坊客户端)
- [SPV - 比特币中的简单支付验证](#spv---比特币中的简单支付验证)
- [完整节点的硬件要求](#完整节点的硬件要求)
- [基于以太坊的区块链首次同步](#基于以太坊的区块链首次同步)
- [JSON-RPC接口](#json-rpc接口)
## 黄皮书
- 以太坊由名为“黄皮书”的正式规范定义,以太坊的规范定义在一篇结合了英文和数学的（正式的）规范的论文中
- 参考: https://github.com/wanshan1024/ethereum_yellowpaper/blob/master/ethereum_yellow_paper_cn.pdf

## 客户端分类
- 完整的节点
- testnet节点
- 本地私有区块链,参见`ganache`  
- 服务提供商提供的基于云的以太坊客户端,参见`infura` 
- 轻量级客户端,不会存储区块链的本地副本或验证块和交易,可以创建和广播交易

## 轻量级以太坊客户端
- 管理钱包中的私钥和以太坊地址
- 创建，签署和广播交易
- 使用数据与智能合约进行交互
- 浏览并与DApps交互
- 提供到区块浏览器等外部服务的链接
- 转换ether单位并从外部来源检索汇率
- 将web3实例作为JavaScript对象注入到Web浏览器中
- 使用另一个客户端提供/注入浏览器的web3实例
- 在本地或远程以太网节点上访问RPC服务

## SPV - 比特币中的简单支付验证
- 解决了人们在支付验证时如何处理超大规模区块数据的难题
- 利用了区块的结构信息及`Merkle Tree`的强大搜索能力，从而能实现对交易信息的快速定位
- 不运行全节点也可以验证支付，用户只需要保存所有的区块头（Block Header）就可以了
- SPV参考: https://www.jianshu.com/p/39be41dfb5fa
- `Merkle Tree`: https://brilliant.org/wiki/merkle-tree/  
  
**Merkle Tree**    
 
![Merkle Tree_Efficiency](images/Merkle_trees.png)  



**Merkle Tree的效率模拟**    

![Merkle Tree_Efficiency](images/merkle_tree_effeciency.webp)   

当区块大小由16笔交易（4KB）急剧增加至65,535笔交易（16MB）时，Merkle的搜索路径长度增长却极其缓慢。这样一来，只需要一个区块头部结构，再加一个这样的搜索路径的开销，一个节点就能花费很小的代价快速定位一个交易

转自：https://www.jianshu.com/p/39be41dfb5fa

## 完整节点的硬件要求
**最低要求：**
- 2核心CPU。
- 固态硬盘（SSD），至少80GB可用空间。
- 最小4GB内存，如果你使用HDD而不是SSD，则至少8GB。
- 8+ MBit/sec下载速度的互联网。

**推荐规格：**
- 4个以上核心的快速CPU。
- 16GB+ RAM。
- 至少有500GB可用空间的快速SSD。
- 25+ MBit/sec下载速度的互联网。

## 基于以太坊的区块链首次同步
- 新客户端在到达区块2,283,397之前会进展迅速。该块在2016年9月18日开采，标志着DoS攻击的开始。从这个区块到2,700,031区块（2016年11月26日），交易验证变得非常缓慢，内存密集并且I/O密集
- 大多数以太坊客户端包括一个选项，可以执行“快速”同步，跳过交易的完整验证，同步到区块链的顶端后，再恢复完整验证

## JSON-RPC接口
- RPC接口作为端口+8545+上的HTTP服务提供。出于安全原因，默认情况下，它仅受限于从本地主机（你自己的计算机的IP地址为+127.0.0.1+）接受连接
- Using curl to call the web3_clientVersion function over JSON-RPC:`curl -X POST -H "Content-Type: application/json" --data \'{"jsonrpc":"2.0","method":"web3_clientVersion","params":[],"id":1}' \http://localhost:8545`
- JSON-RPC 2.0规范格式化，http://www.jsonrpc.org/specification
- 请求中的id参数，在批处理时，为每个请求设置不同的 id，然后将其与来自JSON-RPC服务器的每个响应中的+id+进行匹配。实现这个最简单的方法是维护一个计数器并为每个请求增加值


