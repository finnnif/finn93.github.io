---
title: 公交API
---

[TOC]

>请求前缀:
http://61.164.37.75:55555/BusService/

## 1.获取全部公交车线路名称及线路ID

###Path : 
    /Require_AllRouteData

###Request parameters: 

参数名 | 是否必要 | 参数含义 | 备注
--------- | ------------- | ---------- | ----------
TimeStamp | YES | 时间戳 | 填123

###Full request:
    http://61.164.37.75:55555/BusService/Require_AllRouteData/?TimeStamp=123

###JSON format:

```
{
  "TimeStamp": "2016-11-17 22:26:37",
  "RouteList": [{
  	"RouteID": 320001,
  	"RouteName": "专线1"
  }, {
  	"RouteID": 120010,
  	"RouteName": "1路"
  }, {
  	"RouteID": 840010,
  	"RouteName": "假日1线"
  }, 
  ...
     {
  	"RouteID": 7282201,
  	"RouteName": "7282201"
  }]
  "IsNewData": "1"
}
```
   
###Return parameters:

参数名 | 参数含义 | 备注
--------- | ------------- | ----------
RouteID | 线路ID | 用于获取线路详情
RouteName | 线路名称 | N/A

-

## 2.获取公交线路详情

###Path : 
    /Require_RouteStatData

###Request parameters: 

参数名 | 是否必要 | 参数含义 | 备注
--------- | ------------- | ---------- | ----------
RouteID | YES | 公交线路ID | N/A

###Full request:
    http://61.164.37.75:55555/BusService/Require_RouteStatData/?RouteID=923110

###JSON format :
    太长了,自己去看!

###Part of the return parameters:

参数名 | 参数含义 | 备注
--------- | ------------- | ---------- | ----------
SegmentID | 线路段ID | 用于获取线路段详情
SegmentName | 线路段名称(起步车站名称) | N/A
FirstTime | 首班车发车时间 | N/A
LastTime | 末班车发车时间 | N/A
StationID | 站台ID | N/A
StationName | 站点名称 | N/A

-

##3.获取公交线路段详情

###Path :
    /Query_ByRouteID

###Request parameters: 

参数名 | 是否必要 | 参数含义 | 备注
--------- | ------------- | ---------- | ----------
RouteID | YES | 公交线路ID | N/A
Segmentid | YES | 公交线路段ID | N/A

###Full request:
    http://61.164.37.75:55555/BusService/Query_ByRouteID/?RouteID=122150&Segmentid=26596599

###JSON format such as:
```
{
    "RouteID": 122150,
    "RunBusNum": 0,
    "RStaRealTInfoList": [{
    	"StationID": "1134051503",
    	"RStanum": 17,
    	"ExpArriveBusStaNum": 1,
    	"StopBusStaNum": 0,
    	"BusType": 0
    }, {
    	"StationID": "1144021501",
    	"RStanum": 23,
    	"ExpArriveBusStaNum": 1,
    	"StopBusStaNum": 0,
    	"BusType": 0
    }],
    "IsEnd": null
}
```

###Part of the return parameters:

参数名 | 参数含义 | 备注
--------- | ------------- | ---------- | ----------
RStanum | 车辆已到达站点 | 在该线路段从(0)起的第n个站点
ExpArriveBusStaNum | 到达该站的车辆数 | N/A
StopBusStaNum | 正在停站的车辆数(maybe) | N/A


## e.g
785 去公司
http://61.164.37.75:55555/BusService/Query_ByRouteID/?RouteID=927850&Segmentid=26597292

311 去公司
http://61.164.37.75:55555/BusService/Query_ByRouteID/?RouteID=923110&Segmentid=26597414

311 回家
http://61.164.37.75:55555/BusService/Query_ByRouteID/?RouteID=923110&Segmentid=26597415


