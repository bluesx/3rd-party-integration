## 会员系统积分接口交互
### 交互图
&nbsp; &nbsp; ![](https://github.com/bluesx/3rd-party-integration/blob/master/site/images/member-points.jpg)
<br/>
### 交互说明
* 1.线上系统根据会员手机匹配ERP会员信息，如能匹配到，则读取线下会员积分，即以ERP会员积分初始化线上会员积分；如不能匹配到，则双方各自初始化积分为0.
* 2.线上系统根据不同场景会产生及消耗积分，如签到或购物产生积分，积分兑换消耗积分等，产生或消耗积分实时同步给ERP，ERP会员积分同时变更。
* 3.在必要的时候，ERP可以批量同步线上积分，以便核对(或对账)积分数据。



