数据中心订单处理请求API
=====================
1.应用场景
--------------
  各公司业务系统出票完成的订单调用该API，由数据中心分析判断是否需要在关联公司创建订单
  
2.接口调用请求说明：
----------------
  http请求方式：POST<br />
  请求URL:<br />
  支持格式：JSON
  
3.调用示例：
--

<pre><code>
{ticket_order: 
	{"category": 1
	,"order_type": 1
	,"status": 1
	,"title": "xxxxx"
	,"customer": "{"id": "NN","name": "xxxx"}"
	,"creator": "{"id": "NN","name": "xx"}"
	,"creation_time": "YYYY-MM-DD hh: mm: ss"
	,"payment_amount",NNN
	,"issue_time": "YYYY-MM-DD hh: mm: ss"
	,"supplier_id": NNN
	,"supplier_name": xxxx
	,"supplier_type": N
	,"gross_profit": NN
	,"passenger_number": N
	,"capital_account_id": N
	,"capital_account_name": xxxx
	,"offer": NN
	,"creation_time": "YYYY-MM-DD hh: mm: ss"
	,"payment_amount": NN
	,"return_amount": NN
	,"adjust_amount": NN
	,"supplier_order": xxxx
	,"adjust_price_remark": 
	,"desk_issue_time": "YYYY-MM-DD hh: mm: ss"
	,"foreign_currency_json": {"amount": N,"Category": xx}
	,"category": N
	,"parent_id": NNNN
	,"issue_receivable": NNNN
	,"issue_payable": NNNN
	,"operator": {“id”: NNNN,"name": xx}
	,"sales": {“id”: NNNN,"name": xx}
	,"issuer": {“id”: NNNN,"name": xx}
	,"customer": {“id”: NNNN,"name": xx}}
pnr: [{
	"code": "xxxx"
	"number_of_people": "1"
	"type": N,"body": ""
	"big_code": ""
	"passenger": [{
		"name": "xxx"
		"gender": "x"
		"certificate_type": "xx"
		"certificate_number": "NNNNN"
		"nationality": "xx"
		"issuing_country": "xx"
		"birthday": "YYYY-MM-DD"
		"period_of_validity": "YYYY-MM-DD"
		"ticket_numbers": "["NNN-NNNNNNNN"]"
		"segment": "[{
			"flight_number": "xxxx"
			,"space": "x"
			,"departure_terminal": "xx"
			,"arrival_terminal": "xx"
			,"number_of_place": NN
			"departure_time": "YYYY-MM-DD hh: mm: ss"
			"arrival_time": "YYYY-MM-DD hh: mm: ss"
			,"departure_place_code": "xxx"
			,"arrival_place_code": "xxx"}]
		"price": "[{
			"type": "1"
			"pay_amount": NN
			,"tax": NN
			,"discount": NN
			,"rebates": NN
			,"return_money": NN
			,"after_rebates": NN
			,"after_return_money": NN
			,"number_of_people": NN
			,"ticket_price": NN
			,"issue_fare": NN
			,"after_issue_fare": NN
			,"pay_price": NN
			,"total_amount": NN
			,"agent_fee": NN
			,"adjust_fee": NN
			,"category": NN
			,"cost": NN
			,"handling_cost": NN
			,"zvalue": NN}]
	}]
}]}

</code></pre>
