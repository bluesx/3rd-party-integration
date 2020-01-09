### 设备激活状态查询接口

### 1.设备激活状态查询
#### 1.1 接口描述
* ```
  设备调用获取配置接口成功获取配置后，轮询（1S-5S）此接口查询设备激活状态和绑定信息。
  ```

* 调用方：airPhone
#### 1.2 请求方式
> POST
#### 1.3 url
* 线上系统：
> /airPhone/heartbeatDetection
#### 1.4 数据方向
> airPhone-->51健康
#### 1.5 请求参数
| 参数名称 | 参数类型 | 是否必须 | 示例值 | 参数描述  |
| :---         |     :---      |     :--- | :--- | :--- |
| sn | string   | 是    |     | 设备的唯一标识 |
| time | long | 是    | 156156565656222 | unix时间戳 |
| sign | string | 是    |                 | 激活接口单独校验码的值 |
---------------------
#### 1.6 请求数据
 ``` 
{
  "sn":"",
  "time": 156156565656222,
  "sign":""
}
 ```
#### 1.7 返回参数
| 参数名称 |  | 参数类型 | 是否必须 | 示例值 | 参数描述  |
| :---         |     :---      |     :--- | :--- | :--- | :--- |
| msg   |      | string | 是    | 成功 | 对结果的描述 |
| code   |     | int | 是    | 10000    | 返回值: 10000(请求成功)，20000(请求失败)|
| data |  |  |  |  | |
|  | status | int | 是 |  | 表示激活情况0未激活，1已激活 |
|  | token | string | 是 |  | 用于接口校验 |
|  | uid | string   | 是 |  | 设备所属商户唯一标识 |
|  | codeId | string | 是 |  | 设备所属商户收款标识，支付接口将上传此参数用户商户收款 |
|  | codeName | string | 是 |  | 用于设备显示收款方名称 |
|  | cashierName | string | 是 |  | 用于显示收银点名称 |
|  | amount | int | 是 |  | 设备根据此金额判断二维码收款是用静态二维码还是正扫接口 |
|  | miniCard | string | 是 |  | 用于特殊设备，若返回此参数，台卡收款二维码直接用此参数生成 |
|  | productKey | string | 否 |  | 如果使用第三方语音服务（阿里云）需要返回此参数，通过阿里云平台获取 |
|  | deviceName | string | 否 |  | 如果使用第三方语音服务（阿里云）需要返回此参数，通过阿里云平台获取 |
|  | deviceSecret | string | 否 |  | 如果使用第三方语音服务（阿里云）需要返回此参数，通过阿里云平台获取 |
---------------------
#### 1.8 返回示例
```
{
  "msg":"成功",
  "code":"10000"
  "data":{}
}
```