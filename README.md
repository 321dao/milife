# 商品交易平台

## 简介
这个商品交易平台是为了演示DDD+TDD+CQRS+Event Sourcing 技术

## 建模练习
**商品交易平台** 这种交易平台比较常见，商家发布商品-》客户抢购商品-》客户支付订单-》客户评价订单
- 商家在平台上发布商品（发布商品后就不再改变商品信息，包括价格）
- 平台审核商品
- 上线审核通过的商品
- 客户抢购上线的商品 （抢购者最多只能抢购3个同种商品）
- 客户支付已经抢购的商品
- 客户评价商品（客户只能对已支付的商品评价一次）
- 商家查看商品抢购记录

## DDD建模
**限界上下文** 交易上下文、支付上下文

## 交易上下文
### 聚合根
- **商品**（ID、名称、价格、数量、序列号、抢购记录ID列表、评价ID列表、付款ID列表、商品状态）
- **抢购**（ID、商品ID、抢购者ID、数量）
- **订单**（ID、订单单项列表、总额）
- **商品评价**（ID、商品ID、抢购者ID、内容、时间）

> 注：商品聚合根的**抢购记录ID列表** 是为了保证条件【抢购者最多只能抢购3个同种商品】一致性</br>
> **评价ID列表**和**付款ID列表** 是为了保证条件【客户只能对已支付的商品评价一次】一致性

### 值对象
- **商家**、**抢购者**、**订单单项**等

## 支付上下文
### 聚合根
- **账户**（ID、名称、卡号、余额）
- **转账**（ID、转出账户ID、转入账户ID、转账金额，状态[开始、已转出、完成、失败]）

### 值对象
- **卡号**、**金额**、**状态**等

