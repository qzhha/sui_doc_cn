---
标题：关于 Sui
---

Sui 是第一个从头开始设计的无需许可的第 1 层(Layer 1)区块链，旨在使创建者和开发人员能够构建满足未来 web3 十亿级用户量体验的应用。 Sui 具有水平可扩展性，可以以无与伦比的速度和低成本支持广泛的应用程序开发。

## Sui 是什么

Sui 是一个智能合约平台，由一组不需许可的验证者维护，其作用类似于其他区块链系统中的验证者(validators)或矿工(miners)。

Sui 为常见使用场景提供了可扩展性和前所未有的低延迟体验，并且 Sui 使得绝大多数事务可以并行处理，从而更好地利用计算资源，并提供了增加通过更多资源来增加吞吐量的选项。 Sui 使用更简单、延迟更低的原语(primitives)来处理常见用例而非其他公链中的共识层，例如支付交易和资产转移。这在区块链世界中是史无前例的，这样的设计能支持许多新的对延迟敏感的分布式应用程序，例如游戏和实体销售点的零售支付等等。

Sui 使用 [Rust](https://www.rust-lang.org) 编写，支持使用 [Move 编程语言](https://golden.com/wiki/Move_(programming_language)-MNA4DZ6) 编写智能合约，来定义资产(这些资产可能会有一个所有者(owner))。Move 程序定义了对这些资产的操作，包括创建资产、将这些资产转移给新所有者以及改变资产的操作。

Sui 有一个名为 SUI 的原生代币，供应量固定。 SUI 代币用于支付 gas，也可用作一个时期内的[委托权益证明](https://learn.bybit.com/blockchain/delegated-proof-of-stake-dpos/)。这个时期内验证者的投票权是这个委托权益赋予的能力。一个周期(epoch)内，验证者会根据委托给他们的权益重新分配。在任何周期，验证者们都是 [拜占庭容错](https://pmg.csail.mit.edu/papers/osdi99.pdf)的。在周期结束时，验证者通过处理交易收取的费用(矿工费)将根据他们对系统运行的贡献进行分配。同时，验证者可以分享一些费用作为奖励给委托给他们的用户。

Sui 基于许多最先进的 [同行评审作品(peer-reviewed works)](../contribute/research-papers.md) ，并经过了多年公开源码(open source)下的开发。

## 并行协议——系统设计的突破

Sui 能够无上限的水平扩展，以满足应用程序需求，同时保持每笔交易的交易成本(gas)极低。它的系统设计突破消除了现有区块链中的一个关键瓶颈：需要将所有交易列表进行排序以达成全球范围的共识。鉴于大多数事务不会与其他事务竞争相同的资源，因此这种计算会浪费资源。

Sui 通过在因果独立的事务上实现并行协议，在可扩展性方面取得了重大飞跃。 Sui 验证者使用拜占庭一致性广播提交此类交易，消除了全球共识的开销，同时又不牺牲安全性和可用性。

只有 Sui 新颖的数据模型才有可能实现这一突破。由于其以对象为中心的视图和 Move 的强大所有权类型，依赖项被显式编码。因此，Sui 在大多数对象上都能并行执行事务，而少数影响共享状态的事务会通过拜占庭容错共识排序再并行执行。

### 亮点

* 无与伦比的可扩展性，即时结算
* 主流开发者可以使用的安全智能合约语言
* 能够定义丰富且可组合的链上资产
* 为 web3 应用提供更好的用户体验

Sui 是当今唯一可以随着 web3 的增长而扩展的区块链，同时实现行业领先的性能、成本、可编程性和可用性。随着我们推动主网的发布，我们将展示超出现有系统（传统系统和区块链系统）的交易处理能力的能力。我们将 Sui 视为第一个互联网规模的可编程区块链平台，是 web3 的基础层。

## 无与伦比的可扩展性，即时结算

如今，由于吞吐量有限，随着网络使用量的增加，现有区块链的用户必须支付相当大的税款(gas fee)。此外，高延迟限制了应用程序的响应能力。这些因素导致了 web3 中非常常见的糟糕用户体验：

* 游戏速度慢且玩起来贵得令人望而却步
* 投资者在去中心化金融 (DeFi) 中来不及清算抵押不足的贷款时会损失资金
* 大容量、低价值、频繁交易的大众市场服务，如小额支付和优惠券，因为定价原因（gas 给的低）被排除在网络之外
* 由于高昂的gas fee，人为地抬高了资产的底价

Sui 横向扩展以满足应用程序的需求。网络容量与增量成正比增长