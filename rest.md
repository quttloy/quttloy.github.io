# 客服后台v1.5.0版本接口文档

## 问诊描述模板管理

### 1、新增模版

**URL**: `http://localhost:8080/gyenno-admin/inquiryConditionFormwork/api/`

**请求方式**：`POST`

**请求参数**：

| 参数名称  | 参数说明          | 请求类型 | 是否必须 | 数据类型 |
| :-------- | :---------------- | :------- | :------- | :------- |
| code      | 模板code          | body     | 是       | string   |
| sketch    | 模板名称          | body     | 是       | string   |
| condition | 模板内容/病情描述 | body     | 是       | string   |

**请求示例**：

```json
{
    "code": "SMCS",
    "sketch": "测试模版名",
    "condition": "测试描述"
}
```

**响应示例**：

```json
{
	"code": 200, 
	"data": {
        "id": "89asdkljlasdlkj989",			// id
        "code": "SMCS",						// 模板code
        "sketch": "测试模版名",				 // 模板名称
        "condition": "测试描述",			  // 描述/内容
        "createdAt": "2020-05-21 14:00:00",
        "updatedAt": "2020-05-21 14:00:00"
    },
	"message": "模板保存成功",
	"success": true
}
```

---

### 2、修改模板

**URL**: `http://localhost:8080/gyenno-admin/inquiryConditionFormwork/api/`

**请求方式**: `PUT`

**请求参数**：

| 参数名称  | 参数说明          | 请求类型 | 是否必须 | 数据类型 |
| :-------- | :---------------- | :------- | :------- | :------- |
| id        | 模板id            | body     | 是       | string   |
| code      | 模板code          | body     | 是       | string   |
| sketch    | 模板名称          | body     | 是       | string   |
| condition | 模板内容/病情描述 | body     | 是       | string   |

**请求示例**：

```json
{
    "id": "89asdkljlasdlkj989"
    "code": "SMCS",
    "sketch": "测试模版名",
    "condition": "测试描述"
}
```

**响应示例**：

```json
{
	"code": 200, 
	"data": {
        "id": "89asdkljlasdlkj989",
        "code": "SMCS",
        "sketch": "测试模版名",
        "condition": "测试描述",
        "createdAt": "2020-05-21 14:00:00",
        "updatedAt": "2020-05-21 14:20:00"
    },
	"message": "模板保存成功",
	"success": true
}
```

---

### 3、模板列表查询

**URL**: `http://localhost:8080/gyenno-admin/inquiryConditionFormwork/api/list`

**请求方式**: `GET`

**请求参数**：

| 参数名称   | 参数说明                       | 请求类型 | 是否必须 | 数据类型 |
| :--------- | :----------------------------- | :------- | :------- | :------- |
| searchText | 模糊查询、code/名称/描述       | query    | 否       | string   |
| pageSize   | 单页长度                       | query    | 是       | int      |
| pageNo     | 页码                           | query    | 是       | int      |
| sortField  | 排序字段，默认设置为 createdAt | query    | 是       | string   |
| descFlg    | 排序方式（0:升序，1:倒序）     | qeury    | 是       | int      |

**响应示例**：

```json
{
	"code": 200, 
	"data": {
        "list": [
            {
                "id": "89asdkljlasdlkj989",
                "code": "SMCS",
                "sketch": "测试模版名",
                "condition": "测试描述",
                "createdAt": "1590040800000",
                "updatedAt": "1590042000000"
            },
            {
                "id": "89asdkljlasdlkj989",
                "code": "SMCS",
                "sketch": "测试模版名",
                "condition": "测试描述",
                "createdAt": "1590040800000",
                "updatedAt": "1590042000000"
            }
            ...
        ],
        "pageInfo": {
			"pageNum": 1,
			"pageSize": 10,
			"totalPage": 67,
			"totalRecord": 666
		}
    },
	"message": "模板保存成功",
	"success": true
}
```

---

### 4、单个模版数据查询

*接口提供，可不使用*

**URL**:  `http://localhost:8080/gyenno-admin/inquiryConditionFormwork/api/{id}`

​	URL示例：`http://localhost:8080/gyenno-admin/inquiryConditionFormwork/89asdkljlasdlkj989`

**请求方式**: `GET`

**请求参数**: 无， id由url传入

**响应示例**：

```json
{
	"code": 200, 
	"data": {
        "id": "89asdkljlasdlkj989",
        "code": "SMCS",
        "sketch": "测试模版名",
        "condition": "测试描述",
        "createdAt": "1590040800000",
        "updatedAt": "1590042000000"
    },
	"message": "模板保存成功",
	"success": true
}
```

---

### 5、模版数据删除

**URL**: `http://localhost:8080/gyenno-admin/inquiryConditionFormwork/api/{id}`

**请求方式**: `DELETE`

**请求参数**: 无， id由url传入

**响应示例**：

```json
{
	"code": 200, 
	"data": {
        "id": "89asdkljlasdlkj989",
        "code": "SMCS",
        "sketch": "测试模版名",
        "condition": "测试描述",
        "createdAt": "1590040800000",
        "updatedAt": "1590042000000"
    },
	"message": "模板保存成功",
	"success": true
}
```

---

## 问诊服务订单

### 字典

**问诊类型 - INQUIRY_TYPE** 

| code | 描述     |
| ---- | -------- |
| 1    | 图文问诊 |
| 2    | 电话问诊 |

**购买渠道 - INQUIRY_PURCHASE_CHANNEL**

| code | 描述      |
| ---- | --------- |
| 1    | 医动力app |

### 1、订单分页查询

订单字段说明参考数据报告列表页面下的说明

**URL**: `http://localhost:8080/gyenno-admin/inquiryOrder/list`

**请求方式**: `GET`

**请求参数**：

| 参数名称        | 参数说明                                              | 请求类型 | 是否必须 | 数据类型 |
| :-------------- | :---------------------------------------------------- | :------- | :------- | :------- |
| searchText      | 模糊查询、购买人姓名，手机号，订单编号，产品/服务名称 | query    | 否       | string   |
| inquryType      | 问诊类型，1、图文问诊；2、电话问诊                    | query    | 否       | string   |
| orderStatus     | 订单状态code                                          | query    | 否       | string   |
| purchaseChannel | 购买渠道，                                            |          |          |          |
| pageSize        | 单页长度                                              | query    | 是       | int      |
| pageNo          | 页码                                                  | query    | 是       | int      |
| sortField       | 排序字段，默认设置为 createdAt                        | query    | 是       | string   |
| descFlg         | 排序方式（0:升序，1:倒序）                            | qeury    | 是       | int      |

---

**响应示例**：

```json
{
    "code": 200, 
	"data": {
        "list": [
			{
				"cancelTime": "",
				"cancelable": true,
				"couponLZist": [
					{
						"codeArr": "",
						"count": 0,
						"name": ""
					}
				],
				"createTime": "",
				"discount": 0,
				"doctorId": "",
				"doctorName": "",
				"noDataReportSum": 0,
				"orderNumber": "",
				"orderPrice": 0,
				"paymentAmount": 0,
				"paymentChannel": "",
				"paymentChannelCode": "",
				"paymentTime": "",
				"pendingReportSum": 0,
				"phone": "",
				"projectCode": "",
				"purchaseChannel": "",
				"purchaseChannelCode": "",
				"refundMoney": 0,
				"refundTimes": 0,
				"refundableMoney": 0,
				"serviceEndTime": "",
				"serviceStartTime": "",
				"serviceType": "",
				"serviceTypeCode": "",
				"status": "",
				"statusCode": "",
				"supplier": "",
				"userId": "",
				"userName": ""
			}
		],
		"pageInfo": {
			"pageNum": 1,
			"pageSize": 10,
			"totalPage": 67,
			"totalRecord": 666
		}
    },
	"message": "请求成功",
	"success": true
}
```





### 2、查询单个订单信息

**URL**: `http://localhost:8080/gyenno-admin/inquiryOrder/{orderNumber}`

**请求方式**: `GET`

**请求参数**：无

**响应示例**：

```json
{
    "code": 200, 
	"data": {
        "cancelTime": "",
        "cancelable": true,
        "couponList": [
            {
                "codeArr": "",
                "count": 0,
                "name": ""
            }
        ],
        "createTime": "",
        "discount": 0,
        "doctorId": "",
        "doctorName": "",
        "orderNumber": "",
        "orderPrice": 0,
        "paymentAmount": 0,
        "paymentChannel": "",
        "paymentChannelCode": "",
        "paymentTime": "",
        "phone": "",
        "projectCode": "",
        "purchaseChannel": "",
        "purchaseChannelCode": "",
        "refundMoney": 0,
        "refundTimes": 0,
        "refundableMoney": 0,
        "serviceEndTime": "",
        "serviceStartTime": "",
        "serviceType": "",
        "serviceTypeCode": "",
        "status": "",
        "statusCode": "",
        "supplier": "",
        "userId": "",
        "userName": ""
    },
	"message": "请求成功",
	"success": true
}
```



### 3、全部导出

**URL**: `http://localhost:8080/gyenno-admin/inquiryOrder/exportAll`

**请求方式**: `GET`

**请求参数**：

| 参数名称        | 参数说明                                              | 请求类型 | 是否必须 | 数据类型 |
| :-------------- | :---------------------------------------------------- | :------- | :------- | :------- |
| searchText      | 模糊查询、购买人姓名，手机号，订单编号，产品/服务名称 | query    | 否       | string   |
| inquryType      | 问诊类型，1、图文问诊；2、电话问诊                    | query    | 否       | string   |
| orderStatus     | 订单状态code                                          | query    | 否       | string   |
| purchaseChannel | 购买渠道，                                            |          |          |          |
| pageSize        | 单页长度                                              | query    | 是       | int      |
| pageNo          | 页码                                                  | query    | 是       | int      |
| sortField       | 排序字段，默认设置为 createdAt                        | query    | 是       | string   |
| descFlg         | 排序方式（0:升序，1:倒序）                            | qeury    | 是       | int      |



---

### 4、批量导出

**URL**: `http://localhost:8080/gyenno-admin/inquiryOrder/exportByIds`

**请求方式**: `GET`

**请求参数**：

| 参数名称   | 参数说明     | 请求类型 | 是否必须 | 数据类型 |
| :--------- | :----------- | :------- | :------- | :------- |
| searchText | 订单id，数组 | query    | 否       | string   |



---

### 5、订单取消

**URL**: `http://localhost:8080/gyenno-admin/inquiryOrder/cancel/`

**请求方式**: `PUT`

**请求参数**：

| 参数名称           | 参数说明              | 请求类型 | 是否必须 | 数据类型 |
| :----------------- | :-------------------- | :------- | :------- | :------- |
| orderNumber        | 订单id                | body     | 是       | string   |
| moneyOperationCode | 取消订单小窗-资金操作 | body     | 是       | string   |
| reason             | 取消理由              | body     | 是       | string   |

**请求示例**：

```json
{
    "orderNumber": "PO12315464"
    "moneyOperationCode": "1",
    "reason": "想退就退"
}
```

**响应示例**：

```JSON
{
    "code": 200, 
	"data": {
        "reason":"测试",
        "operationCode":"1",
        "orderNumber":"PO2020042717505413232",
        "createTime":1587981079000,
        "moneyOperation":"不退款”，
        "operationCode":"1",
        "operatorId":1005572
    },
	"message": "取消订单成功",
	"success": true
}
```



---

### 6、订单退费

**URL**: `http://localhost:8080/gyenno-admin/inquiryOrder/refund`

**请求方式**: `PUT`

**请求参数**：

| 参数名称            | 参数说明                           | 请求类型 | 是否必须 | 数据类型 |
| :------------------ | :--------------------------------- | :------- | :------- | :------- |
| orderNumber         | 订单id                             | body     | 是       | string   |
| fileName            | 审批/证明文件名，多个文件名用,隔开 | body     | 是       | string   |
| urls                | 文件url，多个url用,隔开            | body     | 是       | string   |
| orderRefundTypeCode | 订单退费小窗-退费方式下拉框的code  | body     | 是       | string   |
| money               | 退款金额                           | body     | 是       | number   |
| orderStatusCode     | 订单退费小窗-订单状态下拉框的code  | body     | 是       | string   |
| reason              | 理由                               | body     | 是       | string   |

**请求示例**：

```json
{
    "orderNumber": "PO12315464",
    "fileName": "文件111.txt",
    "urls": "http://www.dmsd.cn/asdaskljlk.txt",
    "orderRefundTypeCode": "1",
    "money": "12.35",
    "orderStatusCode": "1",
    "reason": "欠债还钱，天经地义"
}
```

**响应示例**：

```json
{
    "code": 200, 
	"data": {
        "reason":"测试服务医生处退款",
        "orderNumber":"PO2020042714000613208",
        "fileNum":1,
        "operationCode":"2",
        "refundTypeCode":"2",
        "refundType":"部分退",
        "money":"0.02",
        "createTime":1588143116000,
        "moneyOperation":"不退款",
        "orderStatusCode":"2",
        "state":"保持当前状态",
        "operatorId":1005572,
        "moneyOperationCode":"0"
    },
	"message": "取消订单成功",
	"success": true
}
```





---

### 7、添加备注

**URL**: `http://localhost:8080/gyenno-admin/inquiryOrder/remark`

**请求方式**: `POST`

**请求参数**：

| 参数名称    | 参数说明 | 请求类型 | 是否必须 | 数据类型 |
| :---------- | :------- | :------- | :------- | :------- |
| orderNumber | 订单id   | body     | true     | string   |
| remark      | 备注内容 | body     | true     | string   |

**请求示例**：

```json
{
    "orderNumber": "PO2016842454",
    "remark": "测试"
}
```

**响应示例**：

```json
{
    "code": 200, 
	"data": {
        // 插入的备注信息
        ...
    },
	"message": "请求成功",
	"success": true
}
```



---

### 8、查询备注列表

**URL**: `http://localhost:8080/gyenno-admin/inquiryOrder/remark/list`

**请求方式**: `GET`

**请求参数**：

| 参数名称    | 参数说明 | 请求类型 | 是否必须 | 数据类型 |
| :---------- | :------- | :------- | :------- | :------- |
| orderNumber | 订单id   | query    | true     | string   |

**响应示例**：

```json
{
    "code": 200, 
	"data": [
        {
            "id", "asdasdas",
            "operator": "1005527",
            "operatorName": "吴宏远",
            "remark": "balabala",
            "createTime": 1524987456
        },
        {
            "id", "asdasdas",
            "operator": "1005527",
            "operatorName": "吴宏远",
            "remark": "balabala",
            "createTime": 1524987456
        }
    ],
	"message": "请求成功",
	"success": true
}
```



## 老接口复用

问诊服务订单操作历史查询的接口，由全部服务订单下的操作历史接口来复用