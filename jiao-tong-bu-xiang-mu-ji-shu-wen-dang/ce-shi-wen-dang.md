# 后端接口测试文档

## 接口说明

{% api-method method="post" host="http://ip:port/v1/login" path="" %}
{% api-method-summary %}
登录
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" type="string" required=true %}
application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="password" type="string" required=true %}
密码
{% endapi-method-parameter %}

{% api-method-parameter name="name" type="string" required=true %}
用户名
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "resultCode": 200,
    "message": "login in",
    "data": ""
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

![](../.gitbook/assets/image%20%2813%29.png)

{% api-method method="post" host="http://ip:port/v1/logout" path="" %}
{% api-method-summary %}
登出
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "resultCode": 200,
    "message": "logout success",
    "data": null
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="http://ip:port/v1/certificate" path="" %}
{% api-method-summary %}
上传证书
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" type="string" required=true %}
application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="certId" type="string" required=true %}
证书编号
{% endapi-method-parameter %}

{% api-method-parameter name="certType" type="string" required=true %}
证书类型
{% endapi-method-parameter %}

{% api-method-parameter name="entrustOrg" type="string" required=false %}
委托单位
{% endapi-method-parameter %}

{% api-method-parameter name="instrumentName" type="string" required=false %}
器具名称
{% endapi-method-parameter %}

{% api-method-parameter name="spec" type="string" required=false %}
型号/规格
{% endapi-method-parameter %}

{% api-method-parameter name="exportId" type="string" required=false %}
出厂编号
{% endapi-method-parameter %}

{% api-method-parameter name="madeByOrg" type="string" required=false %}
制造单位
{% endapi-method-parameter %}

{% api-method-parameter name="entrustOrgAdd" type="string" required=false %}
委托单位地址
{% endapi-method-parameter %}

{% api-method-parameter name="approver" type="string" required=false %}
批准人
{% endapi-method-parameter %}

{% api-method-parameter name="verifier" type="string" required=false %}
核验员
{% endapi-method-parameter %}

{% api-method-parameter name="calibratePerson" type="string" required=false %}
校准员
{% endapi-method-parameter %}

{% api-method-parameter name="calibrateDate" type="string" required=false %}
校准日期
{% endapi-method-parameter %}

{% api-method-parameter name="suggestNextCaliDate" type="string" required=false %}
建议下次校准日期
{% endapi-method-parameter %}

{% api-method-parameter name="isCompleted" type="boolean" required=false %}
是否完成
{% endapi-method-parameter %}

{% api-method-parameter name="isOpen" type="boolean" required=false %}
是否公开
{% endapi-method-parameter %}

{% api-method-parameter name="isDeleted" type="boolean" required=false %}
是否删除
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "resultCode": 200,
    "message": "OK",
    "data": "87b9d40f3f2f7644d0bd1c5241ac0bec9b278e73d1cffcd3a25aaba13136e656"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

![](../.gitbook/assets/image%20%2831%29.png)

{% api-method method="get" host="http://ip:port/v1/certificate/{certId}" path="" %}
{% api-method-summary %}
获取证书详情
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="certId" type="string" required=true %}
证书编号
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "resultCode": 200,
    "message": "OK",
    "data": {
        "certId": "GDQ2018-223-904",
        "certType": "校准证书",
        "entrustOrg": "厦门合诚工程检测有限公司",
        "instrumentName": "摆式仪",
        "spec": "BM-X5",
        "exportId": "1804003",
        "madeByOrg": "江苏威拓公路养护设备有限公司",
        "entrustOrgAdd": "厦门市海沧区诗山北路25号",
        "approver": "荆强强",
        "verifier": "刘路",
        "calibratePerson": "冷藏",
        "calibrateDate": "2018-09-16",
        "suggestNextCaliDate": "2019-05-15",
        "isCompleted": false,
        "isOpen": false,
        "isDeleted": false,
        "updateDate": "2019-03-07",
        "hasUpload": false
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

![](../.gitbook/assets/image%20%2836%29.png)

{% api-method method="post" host="http://ip:port/v1/changeStatus" path="" %}
{% api-method-summary %}
修改证书状态
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" type="string" required=true %}
application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="st" type="array" required=false %}

{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "resultCode": 200,
    "message": "",
    "data": [
        {
            "certId": "GDQ2018-223-902",
            "isOpen": false,
            "isCompleted": false,
            "isDeleted": false,
            "isChangedOnChain": true
        }
    ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

![](../.gitbook/assets/image%20%2814%29.png)

{% api-method method="post" host="http://ip:port/v1/certificate/openList" path="" %}
{% api-method-summary %}
获取公开的证书列表
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" type="string" required=true %}
application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="pageSize" type="string" required=true %}
每页数据量
{% endapi-method-parameter %}

{% api-method-parameter name="pageIndex" type="string" required=true %}
本次请求到页号
{% endapi-method-parameter %}

{% api-method-parameter name="isOpen" type="boolean" required=false %}
是否公开
{% endapi-method-parameter %}

{% api-method-parameter name="isCompleted" type="boolean" required=false %}
是否完成
{% endapi-method-parameter %}

{% api-method-parameter name="isDeleted" type="boolean" required=false %}
是否删除
{% endapi-method-parameter %}

{% api-method-parameter name="certType" type="string" required=false %}
证书类型
{% endapi-method-parameter %}

{% api-method-parameter name="certId" type="string" required=false %}
证书编号
{% endapi-method-parameter %}

{% api-method-parameter name="entrustOrg" type="string" required=false %}
委托单位
{% endapi-method-parameter %}

{% api-method-parameter name="instrumentName" type="string" required=false %}
器具名称
{% endapi-method-parameter %}

{% api-method-parameter name="startCreateDate" type="string" required=false %}
起始录入日期
{% endapi-method-parameter %}

{% api-method-parameter name="endCreateDate" type="string" required=false %}
结束录入日期
{% endapi-method-parameter %}

{% api-method-parameter name="startCalibDate" type="string" required=false %}
起始校准日期
{% endapi-method-parameter %}

{% api-method-parameter name="endCalibDate" type="string" required=false %}
结束校准日期
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "resultCode": 200,
    "message": "OK",
    "data": {
        "count": 10,
        "pageIndex": 1,
        "certs": [
            {
                "certId": "GDQ2018-223-920",
                "certType": "校准证书",
                "entrustOrg": "厦门合诚工程检测有限公司",
                "instrumentName": "摆式仪",
                "spec": "BM-X5",
                "exportId": "1804003",
                "madeByOrg": "江苏威拓公路养护设备有限公司",
                "entrustOrgAdd": "厦门市海沧区诗山北路25号",
                "approver": "荆强强",
                "verifier": "刘路",
                "calibratePerson": "冷藏",
                "calibrateDate": "2018-09-16",
                "suggestNextCaliDate": "2019-05-15",
                "isCompleted": true,
                "isOpen": true,
                "isDeleted": false,
                "updateDate": "2019-03-07",
                "hasUpload": true
            },
            {
                "certId": "GDQ2018-223-919",
                "certType": "校准证书",
                "entrustOrg": "厦门合诚工程检测有限公司",
                "instrumentName": "摆式仪",
                "spec": "BM-X5",
                "exportId": "1804003",
                "madeByOrg": "江苏威拓公路养护设备有限公司",
                "entrustOrgAdd": "厦门市海沧区诗山北路25号",
                "approver": "荆强强",
                "verifier": "刘路",
                "calibratePerson": "冷藏",
                "calibrateDate": "2018-09-16",
                "suggestNextCaliDate": "2019-05-15",
                "isCompleted": true,
                "isOpen": true,
                "isDeleted": false,
                "updateDate": "2019-03-07",
                "hasUpload": true
            },
            {
                "certId": "GDQ2018-223-918",
                "certType": "校准证书",
                "entrustOrg": "厦门合诚工程检测有限公司",
                "instrumentName": "摆式仪",
                "spec": "BM-X5",
                "exportId": "1804003",
                "madeByOrg": "江苏威拓公路养护设备有限公司",
                "entrustOrgAdd": "厦门市海沧区诗山北路25号",
                "approver": "荆强强",
                "verifier": "刘路",
                "calibratePerson": "冷藏",
                "calibrateDate": "2018-09-16",
                "suggestNextCaliDate": "2019-05-15",
                "isCompleted": true,
                "isOpen": true,
                "isDeleted": false,
                "updateDate": "2019-03-07",
                "hasUpload": true
            }
        ]
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

![](../.gitbook/assets/image%20%2815%29.png)

{% api-method method="post" host="http://ip:port/v1/certificate/draftList" path="" %}
{% api-method-summary %}
获取草稿证书列表
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" type="string" required=true %}
application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="pageSize" type="string" required=true %}
每页数据量
{% endapi-method-parameter %}

{% api-method-parameter name="pageIndex" type="string" required=true %}
本次请求到页号
{% endapi-method-parameter %}

{% api-method-parameter name="isOpen" type="boolean" required=false %}
是否公开
{% endapi-method-parameter %}

{% api-method-parameter name="isCompleted" type="boolean" required=false %}
是否完成
{% endapi-method-parameter %}

{% api-method-parameter name="isDeleted" type="boolean" required=false %}
是否删除
{% endapi-method-parameter %}

{% api-method-parameter name="certType" type="string" required=false %}
证书类型
{% endapi-method-parameter %}

{% api-method-parameter name="certId" type="string" required=false %}
证书编号
{% endapi-method-parameter %}

{% api-method-parameter name="entrustOrg" type="string" required=false %}
委托单位
{% endapi-method-parameter %}

{% api-method-parameter name="instrumentName" type="string" required=false %}
器具名称
{% endapi-method-parameter %}

{% api-method-parameter name="startCreateDate" type="string" required=false %}
起始录入日期
{% endapi-method-parameter %}

{% api-method-parameter name="endCreateDate" type="string" required=false %}
结束录入日期
{% endapi-method-parameter %}

{% api-method-parameter name="startCalibDate" type="string" required=false %}
起始校准日期
{% endapi-method-parameter %}

{% api-method-parameter name="endCalibDate" type="string" required=false %}
结束校准日期
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "resultCode": 200,
    "message": "OK",
    "data": {
        "count": 1002,
        "pageIndex": 1,
        "certs": [
            {
                "certId": "GDQ2018-223-902",
                "certType": "校准证书",
                "entrustOrg": "厦门合诚工程检测有限公司",
                "instrumentName": "摆式仪",
                "spec": "BM-X5",
                "exportId": "1804003",
                "madeByOrg": "江苏威拓公路养护设备有限公司",
                "entrustOrgAdd": "厦门市海沧区诗山北路25号",
                "approver": "荆强强",
                "verifier": "刘路",
                "calibratePerson": "冷藏",
                "calibrateDate": "2018-09-16",
                "suggestNextCaliDate": "2019-05-15",
                "isCompleted": false,
                "isOpen": false,
                "isDeleted": false,
                "updateDate": "2019-03-07",
                "hasUpload": true
            },
            {
                "certId": "GDQ2018-200-997",
                "certType": "校准证书",
                "entrustOrg": "厦门合诚工程检测有限公司",
                "instrumentName": "摆式仪",
                "spec": "BM-X5",
                "exportId": "1804003",
                "madeByOrg": "江苏威拓公路养护设备有限公司",
                "entrustOrgAdd": "厦门市海沧区诗山北路25号",
                "approver": "荆强强",
                "verifier": "刘路",
                "calibratePerson": "冷藏",
                "calibrateDate": "2018-09-16",
                "suggestNextCaliDate": "2019-05-15",
                "isCompleted": false,
                "isOpen": false,
                "isDeleted": false,
                "updateDate": "2019-03-07",
                "hasUpload": true
            },
            {
                "certId": "GDQ2018-200-995",
                "certType": "校准证书",
                "entrustOrg": "厦门合诚工程检测有限公司",
                "instrumentName": "摆式仪",
                "spec": "BM-X5",
                "exportId": "1804003",
                "madeByOrg": "江苏威拓公路养护设备有限公司",
                "entrustOrgAdd": "厦门市海沧区诗山北路25号",
                "approver": "荆强强",
                "verifier": "刘路",
                "calibratePerson": "冷藏",
                "calibrateDate": "2018-09-16",
                "suggestNextCaliDate": "2019-05-15",
                "isCompleted": false,
                "isOpen": false,
                "isDeleted": false,
                "updateDate": "2019-03-07",
                "hasUpload": true
            },
            {
                "certId": "GDQ2018-200-999",
                "certType": "校准证书",
                "entrustOrg": "厦门合诚工程检测有限公司",
                "instrumentName": "摆式仪",
                "spec": "BM-X5",
                "exportId": "1804003",
                "madeByOrg": "江苏威拓公路养护设备有限公司",
                "entrustOrgAdd": "厦门市海沧区诗山北路25号",
                "approver": "荆强强",
                "verifier": "刘路",
                "calibratePerson": "冷藏",
                "calibrateDate": "2018-09-16",
                "suggestNextCaliDate": "2019-05-15",
                "isCompleted": false,
                "isOpen": false,
                "isDeleted": false,
                "updateDate": "2019-03-07",
                "hasUpload": true
            },
            {
                "certId": "GDQ2018-200-996",
                "certType": "校准证书",
                "entrustOrg": "厦门合诚工程检测有限公司",
                "instrumentName": "摆式仪",
                "spec": "BM-X5",
                "exportId": "1804003",
                "madeByOrg": "江苏威拓公路养护设备有限公司",
                "entrustOrgAdd": "厦门市海沧区诗山北路25号",
                "approver": "荆强强",
                "verifier": "刘路",
                "calibratePerson": "冷藏",
                "calibrateDate": "2018-09-16",
                "suggestNextCaliDate": "2019-05-15",
                "isCompleted": false,
                "isOpen": false,
                "isDeleted": false,
                "updateDate": "2019-03-07",
                "hasUpload": true
            },
            {
                "certId": "GDQ2018-200-993",
                "certType": "校准证书",
                "entrustOrg": "厦门合诚工程检测有限公司",
                "instrumentName": "摆式仪",
                "spec": "BM-X5",
                "exportId": "1804003",
                "madeByOrg": "江苏威拓公路养护设备有限公司",
                "entrustOrgAdd": "厦门市海沧区诗山北路25号",
                "approver": "荆强强",
                "verifier": "刘路",
                "calibratePerson": "冷藏",
                "calibrateDate": "2018-09-16",
                "suggestNextCaliDate": "2019-05-15",
                "isCompleted": false,
                "isOpen": false,
                "isDeleted": false,
                "updateDate": "2019-03-07",
                "hasUpload": true
            },
            {
                "certId": "GDQ2018-200-992",
                "certType": "校准证书",
                "entrustOrg": "厦门合诚工程检测有限公司",
                "instrumentName": "摆式仪",
                "spec": "BM-X5",
                "exportId": "1804003",
                "madeByOrg": "江苏威拓公路养护设备有限公司",
                "entrustOrgAdd": "厦门市海沧区诗山北路25号",
                "approver": "荆强强",
                "verifier": "刘路",
                "calibratePerson": "冷藏",
                "calibrateDate": "2018-09-16",
                "suggestNextCaliDate": "2019-05-15",
                "isCompleted": false,
                "isOpen": false,
                "isDeleted": false,
                "updateDate": "2019-03-07",
                "hasUpload": true
            }
        ]
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

![](../.gitbook/assets/image%20%2828%29.png)

{% api-method method="post" host="http://ip:port/v1/certificate/deletedList" path="" %}
{% api-method-summary %}
获取回收站的证书列表
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" type="string" required=true %}
application/json
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="pageSize" type="string" required=true %}
每页数据量
{% endapi-method-parameter %}

{% api-method-parameter name="pageIndex" type="string" required=true %}
本次请求到页号
{% endapi-method-parameter %}

{% api-method-parameter name="isOpen" type="boolean" required=false %}
是否公开
{% endapi-method-parameter %}

{% api-method-parameter name="isCompleted" type="boolean" required=false %}
是否完成
{% endapi-method-parameter %}

{% api-method-parameter name="isDeleted" type="boolean" required=false %}
是否删除
{% endapi-method-parameter %}

{% api-method-parameter name="certType" type="string" required=false %}
证书类型
{% endapi-method-parameter %}

{% api-method-parameter name="certId" type="string" required=false %}
证书编号
{% endapi-method-parameter %}

{% api-method-parameter name="entrustOrg" type="string" required=false %}
委托单位
{% endapi-method-parameter %}

{% api-method-parameter name="instrumentName" type="string" required=false %}
器具名称
{% endapi-method-parameter %}

{% api-method-parameter name="startCreateDate" type="string" required=false %}
起始录入日期
{% endapi-method-parameter %}

{% api-method-parameter name="endCreateDate" type="string" required=false %}
结束录入日期
{% endapi-method-parameter %}

{% api-method-parameter name="startCalibDate" type="string" required=false %}
起始校准日期
{% endapi-method-parameter %}

{% api-method-parameter name="endCalibDate" type="string" required=false %}
结束校准日期
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "resultCode": 200,
    "message": "OK",
    "data": {
        "count": 6,
        "pageIndex": 1,
        "certs": [
            {
                "certId": "GDQ2018-223-920",
                "certType": "校准证书",
                "entrustOrg": "厦门合诚工程检测有限公司",
                "instrumentName": "摆式仪",
                "spec": "BM-X5",
                "exportId": "1804003",
                "madeByOrg": "江苏威拓公路养护设备有限公司",
                "entrustOrgAdd": "厦门市海沧区诗山北路25号",
                "approver": "荆强强",
                "verifier": "刘路",
                "calibratePerson": "冷藏",
                "calibrateDate": "2018-09-16",
                "suggestNextCaliDate": "2019-05-15",
                "isCompleted": false,
                "isOpen": false,
                "isDeleted": true,
                "updateDate": "2019-03-07",
                "hasUpload": true
            },
            {
                "certId": "GDQ2018-223-919",
                "certType": "校准证书",
                "entrustOrg": "厦门合诚工程检测有限公司",
                "instrumentName": "摆式仪",
                "spec": "BM-X5",
                "exportId": "1804003",
                "madeByOrg": "江苏威拓公路养护设备有限公司",
                "entrustOrgAdd": "厦门市海沧区诗山北路25号",
                "approver": "荆强强",
                "verifier": "刘路",
                "calibratePerson": "冷藏",
                "calibrateDate": "2018-09-16",
                "suggestNextCaliDate": "2019-05-15",
                "isCompleted": false,
                "isOpen": false,
                "isDeleted": true,
                "updateDate": "2019-03-07",
                "hasUpload": true
            },
            {
                "certId": "GDQ2018-223-918",
                "certType": "校准证书",
                "entrustOrg": "厦门合诚工程检测有限公司",
                "instrumentName": "摆式仪",
                "spec": "BM-X5",
                "exportId": "1804003",
                "madeByOrg": "江苏威拓公路养护设备有限公司",
                "entrustOrgAdd": "厦门市海沧区诗山北路25号",
                "approver": "荆强强",
                "verifier": "刘路",
                "calibratePerson": "冷藏",
                "calibrateDate": "2018-09-16",
                "suggestNextCaliDate": "2019-05-15",
                "isCompleted": false,
                "isOpen": false,
                "isDeleted": true,
                "updateDate": "2019-03-07",
                "hasUpload": true
            },
            {
                "certId": "GDQ2018-223-917",
                "certType": "校准证书",
                "entrustOrg": "厦门合诚工程检测有限公司",
                "instrumentName": "摆式仪",
                "spec": "BM-X5",
                "exportId": "1804003",
                "madeByOrg": "江苏威拓公路养护设备有限公司",
                "entrustOrgAdd": "厦门市海沧区诗山北路25号",
                "approver": "荆强强",
                "verifier": "刘路",
                "calibratePerson": "冷藏",
                "calibrateDate": "2018-09-16",
                "suggestNextCaliDate": "2019-05-15",
                "isCompleted": false,
                "isOpen": false,
                "isDeleted": true,
                "updateDate": "2019-03-07",
                "hasUpload": true
            },
            {
                "certId": "GDQ2018-223-916",
                "certType": "校准证书",
                "entrustOrg": "厦门合诚工程检测有限公司",
                "instrumentName": "摆式仪",
                "spec": "BM-X5",
                "exportId": "1804003",
                "madeByOrg": "江苏威拓公路养护设备有限公司",
                "entrustOrgAdd": "厦门市海沧区诗山北路25号",
                "approver": "荆强强",
                "verifier": "刘路",
                "calibratePerson": "冷藏",
                "calibrateDate": "2018-09-16",
                "suggestNextCaliDate": "2019-05-15",
                "isCompleted": false,
                "isOpen": false,
                "isDeleted": true,
                "updateDate": "2019-03-07",
                "hasUpload": true
            },
            {
                "certId": "GDQ2018-223-902",
                "certType": "校准证书",
                "entrustOrg": "厦门合诚工程检测有限公司",
                "instrumentName": "摆式仪",
                "spec": "BM-X5",
                "exportId": "1804003",
                "madeByOrg": "江苏威拓公路养护设备有限公司",
                "entrustOrgAdd": "厦门市海沧区诗山北路25号",
                "approver": "荆强强",
                "verifier": "刘路",
                "calibratePerson": "冷藏",
                "calibrateDate": "2018-09-16",
                "suggestNextCaliDate": "2019-05-15",
                "isCompleted": true,
                "isOpen": false,
                "isDeleted": true,
                "updateDate": "2019-03-07",
                "hasUpload": true
            }
        ]
    }
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

![](../.gitbook/assets/image%20%2810%29.png)



{% api-method method="post" host="http://ip:port/v1/uploadFile" path="" %}
{% api-method-summary %}
上传pdf证书文件
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" type="string" required=true %}
multipart/form-data
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-form-data-parameters %}
{% api-method-parameter name="certId" type="string" required=false %}
证书编号
{% endapi-method-parameter %}

{% api-method-parameter name="certFile" type="object" required=false %}
证书文件
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "resultCode": 200,
    "message": "",
    "data": "0b538709d3f75d7e9e22ec4dea2213ff76f9a656241f26f3fedbecd04c9ea81d"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

![](../.gitbook/assets/image%20%2811%29.png)

{% api-method method="get" host="http://ip:port/v1/downloadFile/{certId}" path="" %}
{% api-method-summary %}
下载pdf证书
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

![](../.gitbook/assets/image%20%2820%29.png)

