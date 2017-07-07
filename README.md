# 数据中心订单处理请求API

标签（空格分隔）： API文档 数据中心 出票完成订单

---
See my [About](/about/) page for details.
1.应用场景
--------------
 各公司业务系统出票完成的订单调用该API，由数据中心分析判断是否需要在关联公司创建订单
  
2.接口调用请求说明：
----------------
  http请求方式：POST<br />
  请求URL:待定<br />
  支持格式：JSON
  
3.调用示例：
--

<pre><code>
{ticket_order: 
	{"company_id": "LMBJ"
	,"token": "2977727d3c2d047d7a58f186f4d57738"
	,"category": "1"
	,"status": "1"
	,"client_order_id": "1001"
	,"client_parent_order_id": "1000"
	,"title": "北京香港20人团"
	,"type": "国际散客"
	,"customer": "{"id": "8001","name": "任逍遥国际旅行社"}"
	,"creator": "{"id": "101","name": "张三"}"
	,"create_time": "2017-06-30 11:43:00"
	,"issue_time": "2017-06-30 15:43:00"
	,"supplier_id": "900"
	,"supplier_name": "在路上北京"
	,"supplier_type": "1"
	,"gross_profit": "100"
	,"passenger_number": "1"
	,"capital_account_id": "601"
	,"capital_account_name": "在路上北京BSP"
	,"offer": "700"
	,"payment_amount": "600"
	,"return_amount": "0"
	,"adjust_amount": "0"
	,"supplier_order": "0"
	,"adjust_price_remark": ""
	,"desk_issue_time": "2017-06-30 15:43:00"
	,"foreign_currency_json": {"amount": "0","Category": ""}
	,"issue_receivable": "700"
	,"issue_payable": "600"
	,"sales": {“id": "103","name": "李双双"}
	,"issuer": {“id": "105","name": "张双双"}}
pnr: [{
	"code": "XT60TR"
	"number_of_people": "1"
	"type": "1"
	"body": "....."
	"big_code": "ET6305"
	"passenger": [{
		"name": "张晶晶"
		"gender": "女"
		"certificate_type": "身份证"
		"certificate_number": "0102345645646546546"
		"nationality": "中国"
		"issuing_country": "中国"
		"birthday": "1990-01-01"
		"period_of_validity": "2020-02-15"
		"ticket_numbers": "["999-1112265894"]"}]
	"segment": "[{
		"flight_number": "CA951"
		,"space": "A"
		,"departure_terminal": "北京"
		,"arrival_terminal": "香港"
		,"number_of_place": "1"
		"departure_time": "2017-10-01 11:00"
		"arrival_time": "2017-10-01 15:30"
		,"departure_place_code": "PEK"
		,"arrival_place_code": "HKG"}]
	"price": "[{
		"type": "1"
		"pay_amount": "600"
		,"tax": "50"
		,"discount": "0"
		,"rebates": "0"
		,"return_money": "0"
		,"after_rebates": "0"
		,"after_return_money": "0"
		,"number_of_people": "1"
		,"ticket_price": "650"
		,"issue_fare": "0"
		,"after_issue_fare": "0"
		,"pay_price": "550"
		,"total_amount": "0"
		,"agent_fee": "0"
		,"adjust_fee": "0"
		,"category": "1"
		,"cost": "0"
		,"handling_cost": "0"
		,"zvalue": "0"}]
	}]}
</code></pre>
4.入参说明
--
>ticket_order参数说明
参数                    | 说明
------------------------| ---------------
company_id              | 公司代码：由平台统一分配
token                   | 调用接口凭证:MD5(company_id + client_order_id + create_time + 密码(统一分配))
category                | 订单分类：出票单,改期单,退票单,废票单
status                  | 状态：1（已出票）当前只推送已出票的订单
client_order_id         | 各业务系统唯一订单号：
client_parent_order_id  | 原始订单号(改期/退票对应的原单号)
title                   | 订单团号
type                    | 订单分类：1国内散客，2国内团队，3国际散客，4国际团队，5境外电子散客，6境外电子团队，7计划外
customer                | 客户信息：各公司的业务系统的客户id和客户名称 <br>格式：{"id": "8001","name": "任逍遥国际旅行社"}
creator                 | 创建人的员工id和员工姓名 <br>格式：{"id": "101","name": "张三"}
create_time           | 创建时间 timestamp
issue_time              | 出票时间 timestamp
supplier_id             | 供应商编号
supplier_name           | 供应商名称
supplier_type           | 供应商分类：1临时供应商 2固定供应商
gross_profit            | 利润
passenger_number        | 乘客数量
capital_account_id      | 支付方式编号
capital_account_name    | 支付方式名称
offer                   | 总应收
payment_amount          | 总应付
return_amount           | 总后返
adjust_amount           | 调整金额
supplier_order          | 供应商交易单号(第三方采购时)
adjust_price_remark     | 票台调价备注
desk_issue_time         | 待出票时间 timestamp
foreign_currency_json   | 外币信息  示例：{"amount": "1000","Category": "港币"}
issue_receivable        | 实收金额
issue_payable           | 实付金额
sales                   | 销售的员工id和员工姓名
issuer                  | 出票人的员工id和员工姓名

>pnr参数说明
参数                    | 说明
------------------------| ---------------
code                    | PNR小编码
number_of_people        | 人数
type                    | 分类：1应付供应商 2应收客户
body                    | PNR文本信息
big_code                | PNR大编码

>passenger参数说明
参数                    | 说明
------------------------| ---------------
name                    | 乘客姓名
gender                  | 乘客性别
certificate_type        | 证件类型：身份证/护照/....
certificate_number      | 证件号
issuing_country         | 证件发行国
period_of_validity      | 证件有效期
nationality             | 国籍
birthday                | 出生年月日
ticket_numbers          | 票号 示例：["999-1112265894","999-1112265895"]

>segment参数说明
参数                    | 说明
------------------------| ---------------
flight_number           | 航班号
space                   | 舱位
departure_place_code    | 出发机场三字码
arrival_place_code      | 到达机场三字码
departure_terminal      | 出发航站楼
arrival_terminal        | 到达航站楼
number_of_place         | 座位数
departure_time          | 出发时间
arrival_time            | 到达时间

>price
参数                    | 说明
------------------------| ---------------
type                    | 分类：1成人，2儿童，3婴儿
pay_amount              | 总应付
tax                     | 税金
discount                | 折扣金额
rebates                 | 返点
return_money            | 返钱金额
after_rebates           | 后返点
after_return_money      | 后返钱
number_of_people        | 人数
ticket_price            | 票面价
issue_fare              | 出票价：为最终出票时付给航司的价格（票面价-优惠价）
after_issue_fare        | 后返出票价
pay_price               | 应付单价
total_amount            | 总价
agent_fee               | 代理费
adjust_fee              | 调整价格
cost                    | 退票费
handling_cost           | 手续费
zvalue                  | Z值

5.返回值
--
正确时的返回JSON数据包结果：
<code>{"errcode":0,"errmsg":"ok"}</code>
错误时的返回JSON数据包结果：
<code>{"errcode":1,"errmsg":"invalid supplier name"}</code>
