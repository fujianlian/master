# 比特币原理

比特币系统与传统的银行和支付系统不同，是基于去中心化的信任。在比特币中，信任不是通过中央权威机构授权而来，而是通过比特币系统中不同用户相互交互自发达成，这是比特币的一个显著特性。

**注意** 从千分之一比特币(1毫比特币）到一亿分之一比特币（1聪比特币），比特币网络可以处理任意小额交易。在本书中，我们将用“比特币”这个术语来表示任意数量的比特币货币，从最小单元（1聪）到可被挖出的所有比特币总数 （21,000,000）。

## 比特币交易

一笔交易就是告知全网：比特币的持有者已授权把它转帐给其他人。而新持有者可以通过产生另一笔交易，转账给另外的人，依此类推形成一条所有权的链。

### 交易输入输出

交易就像复式记账法账簿中的行。简单来说，每一笔交易包含一个或多个“输入”，就像比特币账户的借方。这笔交易的另一面，有一个或多个“输出”，就像比特币账户的贷方。这些输入和输出的总额（借方和贷方）不需要相等。相反，当输出加起来略少于输入数量时，两者的差额就代表了一笔隐含的“矿工费”，这笔矿工费由成功打包交易到区块链账簿的矿工收取

### 交易链

Alice支付Bob咖啡时使用一笔之前的交易作为输入。

Alice从她朋友Joe那里用现金换了点比特币。那笔交易创建了被Alice的密钥锁定的比特币。在她支付Bob咖啡店的新交易中使用了之前的交易作为输入，输出是支付咖啡的金额和多余部分的找零。交易形成了一条链，最近交易的输入对应以前交易的输出。Alice用密钥签名解锁了之前交易的输出，从而向比特币网络证明她拥有这笔钱。她将买咖啡的这笔支付到Bob的地址上，明确指明要求是Bob签名才能消费这笔钱，否则就“阻止”那笔输出。这就实现了在Alice和Bob之间价值转移。下图展示了从Joe到Alice再到Bob的交易链。

![2.2 比特币交易 - 图2](https://static.sitestack.cn/projects/MasterBitcoin2CN/mbc2_0204.png)

### 找零

许多比特币交易都会包括新所有者的地址（买方地址）和当前所有者的地址（称为找零地址）的输出。这是因为交易输入，就像纸币那样能够不能被再分割。如果您在商店购买了5美元的商品，但是使用20美元的美金来支付商品，会收到15美元的找零。相同的概念适用于比特币交易输入。如果您购买了一个价格为5比特币的商品，但是你的输入中只有20比特币这一项，那么您需要产生两个输出：一个5个比特币的输出发送给店主，另一个15比特币的输出返回自己作为找零（减去任何适用的交易费用）。重要的是，出于隐私的原因，找零地址不必与输入时提供的地址相同，通常是所有者钱包中的新地址。

不同的钱包可以在合并所有输入，用来匹配自己的付款金额时使用不同的策略。它们可能会聚合许多小输入，或者使用等于或大于所需付款的输入。除非钱包中的输入，刚好汇总起来与所需付款（加上交易费用）完全相等，否则钱包一定会产生一些找零。这与人们如何处理现金非常相似。如果你总是用钱包中的最大面额支付时，那么钱包中的零钱就会越来越多。如果你只使用零钱，整钱就会越来越多。人们总是无意识地在这两个极端之间找到平衡，而比特币钱包开发商也力图实现这种平衡。

总的来讲，交易是将钱从交易输入移至输出。输入通常是前一笔交易的输出的引用，表示价值从何而来。交易输出将约定金额发送到新的所有者的比特币地址，并将找零输出返回原来所有者的地址。 一笔交易的输出可以被当做另一笔新交易的输入，这样随着钱从一个地址被移动到另一个地址，就形成了一条所有权链

## 比特币挖矿

一笔交易吧只有被挖矿节点验证且加到一个区块中之后，这个交易才会成为这个共享账簿（区块链）的一部分。关于挖矿的详细描述请见第10章。比特币系统的信任是建立在计算的基础上的。交易被打包在一起放进区块中时需要极大的计算量来证明，但是验证这个证明只需少量计算就可以。

挖矿在比特币系统中有两个重要作用：

▷ 挖矿节点依据比特币的共识规则验证所有交易。 因此，挖矿过程会拒绝无效或不合规交易，以此保障比特币交易的安全性。

▷ 挖矿在构建区块时会创造新的比特币，就像中央银行发行新的纸币一样。每个区块创造的比特币数量是固定的，并且会逐渐减少。

挖矿在成本和报酬之间取得了良好的平衡。 挖矿耗费电力来解决数学问题。 矿工挖矿成功将会获得新的比特币和交易费作为奖励。 但是，只有其他矿工正确验证了所有的交易，符合共识规则的要求，才能拿到奖励。 这种微妙的平衡为没有中央权威机构的比特币提供安全保障。

描述挖矿最好将其类比为一个巨大的多人数独游戏。一旦有人发现正解之后，这个数独游戏会自动重置，并调整难度，使得游戏每次都需要大约10分钟才能解决。想象一个有好几千行和列的大型数独游戏。如果给你一个已经完成的数独谜底， 你可以很快地验证它。然而，如果这个数独只有几个方格里有数字其余方格都为空，就会花费非常长的时间才能解决。这个数独游戏的困难度可以通过改变其大小（更多或更少行列）来调整，但即使非常大时验证结果也是相当容易的。比特币中的 “谜题” 是基于哈希加密算法的，有类似的特点：不对称，解起来困难而验证很容易，而且它的困难度可以调整。

寻找一个区块的交易正解，也被称为工作量证明，整个网络需要进行每秒亿万次哈希计算。这个工作量证明算法指的用SHA256加密算法重复不断对区块头和一个随机数字进行哈希计算，直到出现一个和预设目标值相匹配的解。第一个找到这个解的矿工就是赢得这局竞赛，并会将此区块发布到区块链中。

### 区块中的挖矿交易记录

新交易不断地从用户钱包和其他应用流入比特币网络。当比特币网络上的节点看到这些交易时，会先将它们放到节点自行维护的一个临时的未经验证的交易池中。当矿工构建一个新区块时， 会将这些交易从这个交易池中拿出来放到一个新区块中，然后通过尝试解决一个难题（也叫工作量证明）以证明这个新区块的有效性。

这些交易被加进新区块时，以交易费用和其它的一些规则进行排序。矿工一旦从网络上收到一个新区块， 就知道自己在这个区块上的解题竞赛已经输掉了，然后马上开始下一个新区块的挖矿。它会立刻将一些交易和最新那个区块的数字指纹放在一起开始构建下一个新区块，并开始工作量证明计算。每个矿工会在他的区块中包含一个特殊的交易，将新生成的比特币（当前每区块为12.5比特币）作为矿工费支付到他自己的比特币地址，再加上块中所有交易的交易费用的总和作为自己的报酬。如果他找到了使得新区块有效的解法，他就会得到这笔报酬，因为这个新区块被加入到了区块链总账中，他添加的这笔报酬交易也会变成可消费的。 参与矿池挖矿的Jing设置了他的软件，构建新区块时会将报酬地址设为整个矿池的地址。然后根据各自上一轮贡献的工作量将所得的报酬分给Jing和其他参与矿池挖矿的矿工。

**区块为什么不容易撤销？（即比特币为什么很安全）**

一个新诞生的区块，像链子一样一个连着一个（区块链），一直连到0号区块，即创世区块。随着时间变长，这个区块链的高度也随之增长，每个区块和整个区块链的计算难度也随之增加。按惯例来说，一个区块获得六次以上“确认”时就被认为是不可撤销的了，因为要撤销和重建六个区块需要巨量的计算。