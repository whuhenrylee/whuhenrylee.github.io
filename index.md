# Panama Api
Panama Api提供了微信广告对应的广告主、广告、主体、账户等信息的通用查询功能  
文档版本：v1


0.通用
-----------


### 0.1 接口功能

1. 此接口文档所述接口均为标准HTTP协议接口，支持GET和POST两种方式数据传输，返回数据格式如无特殊说明均为json.
2. 接口所述时间戳如无特殊说明，精确到秒即可
3. 如无特殊声明，接口所有输入参数均不能包含特殊字符< > & ' " / \ 以及TAB、换行、回车键

### 0.2 地址

 接口路径：  
    /{version}/{mod}/{act}  
    version:版本号码,当前版本号码为 v1  
    mod:模块名称  
    act:动作名称  

### 0.3 通用参数

> 待定

### 0.4 访问控制

> 待定


1.广告主模块
-----------
### 1.1 获取广告主信息 
> 地址：v1/advertiser/detail  
> 方式：GET

#### 请求参数

|参数|类型|描述|必填|
|:----- |:----- |:----- |:-----|
|appid |string |公众号广告APPID| 是 |
|uid |int | 广告主uid | 是 |
|uin |int | 公众号uid | 是 |
|username |string | 公众号原始id | 是 |
|fields |json(array of string)| 需要获取的字段信息,具体见字段补充说明| 否 |

> 说明：appid/uid/uin/username 至少要填写一个

#### 字段补充说明
|字段|描述|是否可选|
|:----- |:----- |:----- |
|biz_info | 公众号基础信息 | 一定返回 |
|advertiser_info |广告主信息 | 一定返回 |
|qualification |资质信息 | 是 |
|op_labels |运营标签 | 是 |
|illegal_info |违规信息 | 是 |
|ban_info |处罚信息 | 是 |
|change_log |变更记录 | 是 |


#### 返回

```json
{
    "ret": 0,
    "msg": "",
    "data": {
        "biz_info": {
        	"appid":"wx4be5c665c12c76df",
        	"uin":3083169125,
        	"username":""
        	"nickname":"可口可乐中国",
        	"signature":"可口可乐中国官方微信",
        	"verify_info":"可口可乐饮料(上海)有限公司",
        	"cooperation":"可口可乐饮料(上海)有限公司",
        	"corporation_licence":"91310000795641927D",
        	"mp_operator_name":"曹佳"
        	"mp_operator_email":"rcao@coca-cola.com",
        	"mp_operator_phone":"+8613701225751",
        	"mp_operator_tel":"010－58610252",
        	"headurl":"http://wx.qlogo.cn/mmhead/Q3auHgzwzM6icoYmneQyMHByfH1UlJXyW0XkHIsdFJsVJ2OwBrVyUWQ"
        },
        "advertiser_info":{
        	"uid":1809895,
        	"bg_type":0,
        	"category":1112,
        	"category_name":"食品-冲调饮用",
        	"create_date":"20160520",
        	"inner_flag":0
        },
        "qualification":[{
        	"qualification_name":"《食品流通许可证》或《全国工业生产许可证》或《食品经营许可证》或《餐饮服务许可证》",
        	"qualification_url":"http://mmbiz.qpic.cn/mmbiz/0ZDV0j2REE3lWV0vmBn6Pk9NGn9csAlUtBb7GWwV00CcfuA8ibgw8M8sMib9SjVRhlgoXQX4kia0d9jjFr0T5D0Wg/0?wx_fmt=jpeg",
        	"launch_type":"0"
        }],
        "op_labels":[{
        	"type":1,
        	"label_id":10,
        	"label_name":"资讯类",
        	"create_time":1510735295
        }],
        "illegal_info":[{
        	"count":1,
        	"level":1 //违规级别
        }],
        "ban_info":{
        	"appid":"wx9b7312becfa82023",
			"begin_time":1513579966,
			"create_time":1482406272,
			"end_time":1513579966,
			"function_type":1,//处罚类型
			"status":1,
			"uid":54319,
			"update_time":151357996
        },
        "change_log":[{
        	"change_time":151357996,
        	"change_field":"",
        	"before":"明天怎样穿",
        	"after":"今天怎样穿"
        }]
    }
}
```

#### 接口示例

> 地址1：[advertiser/detail?uid=1809895](advertiser/detail?uid=1809895)  
> 地址2：[advertiser/detail?appid=1809895](advertiser/detail?appid=wx4be5c665c12c76df)

### 1.2 广告主查询
> 地址：v1/advertiser/list  
> 方式：GET

#### 请求参数

|参数|类型|描述|必填|
|:----- |:----- |:----- |:-----|
|q |string |查询参数，可以是名称/uid/uin/appid| 是 |
|page |int |从1开始| 是 |

#### 返回
```json
{
    "ret": 0,
    "msg": "",
    "datas":[{
    	"nickname":"我的一条",
    	"appid":"wx099e8607f32ec176",
    	"uid":4549698,
    	"uin":3215012219
    }],
    "total":20,
    "page":1
}
```

2.流量主模块
-----------
### 2.1 流量主详情
>待完成

### 2.2 流量主查询
> 地址：v1/publisher/list  
> 方式：GET

#### 请求参数

|参数|类型|描述|必填|
|:----- |:----- |:----- |:-----|
|q |string |查询参数，可以是名称/uid/publisherid/appid| 是 |
|page |int |从1开始| 是 |

#### 返回
```json
{
    "ret": 0,
    "msg": "",
    "datas":[{
    	"nickname":"我的一条",
    	"appid":"wx099e8607f32ec176",
    	"publisherid":4549698,
    	"uin":3215012219
    }],
    "total":20,
    "page":1
}
```

3.主体模块
-----------
### 3.1 查询主体信息
>待完成

4.服务商模块
-----------
>待完成

5.账户模块
-----------
>待完成

