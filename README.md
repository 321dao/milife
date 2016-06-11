# milife
练习建模项目（商品交易），主要练习技能：DDD+TDD+CQRS+Event Sourcing

## 简介
这个商品交易平台是为了演示DDD+TDD+CQRS+Event Sourcing实现过程

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

### 交易上下文

### 支付上下文
