### 订单数据结构

```js
'itemId' : String, //订单号
'title' : String, //订单的标题
'type' : String, //订单的类型
'money' :Number, //交易额
'complete' : {
	type : Boolean,
	default : false //是否已经完成了订单，缴纳了金额
},
'fee' : Number, //平台抽取佣金
'startDate' : String, //订单开始的时间
'endDate' : String, //订单完成的时间
'userId1' : String, //发起订单的用户
'userId2' : String, //接受订单的用户
'abuserId' : Array, //邀请接受订单的用户
'online' : {
	type : Boolean,
	default : true //是否为线上的模式
},
'address' : String, //订单的服务地址，只在online为false才有效
'details' : String //对于订单的详情

//如果，userId1是本用户账号，userId2为空值，就代表订单待接受
//如果，userId1是本用户账号，userId2有单值，且complete为false就代表正在执行，待付款
//如果，userId1不是本用户账号，abuserId数组中有本用户账户，就证明是被邀请的，
//若拒绝就会删除掉数组中的名字，若接受就将userId2赋值为该值，清空abuserId数组
//如果，userId1不是本用户账号，userId2为本用户账号，且complete为false就代表已接受，正在执行
//如果只要userId1或者2为本用户账号，complete为true，就是已完成，endDate就是完成时间

```