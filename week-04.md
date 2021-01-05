
# 钱包
- 以太坊钱包包含密钥，而不是ether或令牌
- 每个用户都有一个包含密钥的钱包
- 钱包真的是包含私钥/公钥的钥匙串
- 用户使用密钥签署交易，从而证明他们拥有ether
- ether储存在区块链上ether储存在区块链上

## 钱包类型 
- 非确定性钱包 nondeterministic wallet
  - 非确定性（随机）钱包
- 确定性钱包 deterministic wallet
  - 确定性（种子）钱包
  - HD 钱包 (BIP-32/BIP-44)
  - 种子和助记词（BIP-39）
## 钱包最佳实践
-  基于 BIP-39 的助记词
-  基于 BIP-32 的HD钱包
-  基于 BIP-43 的多用途HD钱包
-  基于 BIP-44 的多币种和多账户钱包
## 生成助记词
1. 创建一个128到256位的随机序列（熵）。
2. 通过取其SHA256哈希的第一部分（熵长度/32）来创建随机序列的校验和。
3. 将校验和添加到随机序列的末尾。
4. 将序列按照11bits划分。
5. 将每个11bits的值映射到预定义字典中的2048个词中的一个。
6. 助记词就是单词的序列。
7. PBKDF2密钥扩展函数的第一个参数是步骤6产生的助记词
8. PBKDF2密钥扩展函数的第二个参数是盐。盐由用户提供的密码字符串和“mnemonic”组合起来。
9. PBKDF2使用2048轮HMAC-SHA512哈希算法，扩展助记词和盐，生成512位的种子。
## 从种子创建HD钱包
## HD钱包密钥标识符（路径）
HD path | Key described
----    | ----
m/0 | The first (0) child private key from the master private key (m)
m/0/0 | The first grandchild private key of the first child (m/0)
m/0'/0 | The first normal grandchild of the first hardened child (m/0')
m/1/0 | The first grandchild private key of the second child (m/1)
M/23/17/0/0 | The first great-great-grandchild public key of the first great-grandchild of the 18th grandchild of the 24th child
## BIP-44指定了包含五个预定义层级的结构
`m / purpose' / coin_type' / account' / change / address_index` 


- 第一级“purpose”始终设置为+44'+
- 第二级“coin_type”指定加密货币类型，允许多货币HD钱包，其中每种货币在第二级下具有其自己的子树。标准文件中定义了几种货币，称为SLIP0044
- 一些例子: Ethereum 是 m/44'/60', Ethereum Classic is m/44'/61', Bitcoin 是 m/44'/0', 所有货币的 Testnet 是 m/44'/1'.
- 树的第三层“account”, 允许用户将他们的钱包分割成逻辑上的子账户，用于会计或组织管理目的。例如HD钱包可能包含两个以太坊“账户”： m/44'/60'/0' 和 m/44'/60'/1'. 每个账户都是自己的子树的根
- 在路径的第四层“change”时，HD钱包有两个子树，一个用于创建接收地址，另一个用于创建零钱地址。以太坊只使用“接收”路径，因为没有零钱地址这样的东西
- 例如，在主账户中以太坊付款的第三个接收地址为M/44'/60'/0'/0/2

HD path | Key described
----    | ----
m/0 | The first (0) child private key from the master private key (m)
m/0/0 | The first grandchild private key of the first child (m/0)
m/0'/0 | The first normal grandchild of the first hardened child (m/0')
m/1/0 | The first grandchild private key of the second child (m/1)
M/23/17/0/0 | The first great-great-grandchild public key of the first great-grandchild of the 18th grandchild of the 24th child








