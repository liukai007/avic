# AVIC网关 接口文档

+ 2020年10月19日
    + 网关基本信息修改(登录页面使用该接口)
    + 网关基本信息详情
    + 物理端口添加
    + 物理端口删除
    + 物理端口详情
    + 物理端口修改
    + 物理端口列表
+ 2020年10月20日
    + 云端地址访问测试
+ 2020年10月21日
    + 端口类型列表
+ 2020年10月22日
    + 环境数据分析接口
    + 当前协作空间环境数据

## 网关基本信息
+ Data
    + id (long) ID
    + equipmentId (long) 设备ID
    + onlyCode (string)  设备序列号
    + ipAddress (string) 网关IP地址
    + gatewayName (string) 网关名字
    + cloudAddress (string) 云地址
    + organizationName  (string) 所属机构
    + collaborationSpace  (string) 协作空间
    + location (string) 地址 （手动填入的地址）
    + realLocation  (string) 真实地址（不需要填入API自动获取）
    + versionNo  (long) 版本号
    + serviceConfReg (int) 配置和注册服务 （1正常 0异常）
    + serviceCoreData (int) core数据服务 （1正常 0异常）
    + serviceMetadata (int) 元数据服务 （1正常 0异常）
    + serviceCommand(int) 命令服务（1正常 0异常）
    + cloudCommunicateTime (Date) 云端最后一次通信时间
    + enabled (int)  - 使能  0禁止 1启用
    + creator (long) - 创建人
    + modifier (long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间

   
### 网关基本信息修改(登录页面使用该接口) [PATCH] /gatewayInfo/baseInfo

+ Description
    + Author Liukai
    
+ Parameters
    + data (string) 网关内容 （使用json数据）
    
+ Request (application/json)

        {
          "data": {
            "id": 2,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2020-10-19 11:39:50",
            "modified": "2020-10-19 14:23:00",
            "equipmentId": 1,
            "onlyCode": "YzhjOWNmMmEyMzMxNGU0M2M4OWE3OTMxOWRlZTIyYWU=",
            "ipAddress": "192.168.2.43",
            "gatewayName": "中会网关1",
            "cloudAddress": "budee.com:9094",
            "location": "北京市海淀区",
            "organizationName": "宝迪",
            "collaborationSpace": "中会议室",
            "realLocation": "北京市丰台区方庄XXX街道",
            "versionNo": "1",
            "serviceConfReg": 1,
            "serviceCoreData": 1,
            "serviceMetadata": 1,
            "serviceCommand": 1,
            "cloudCommunicateTime": "2020-10-19 13:52:16",
            "runningStatus": 1
          }
        }
+ Response 200

        
### 网关基本信息详情 [GET] /gatewayInfo/baseInfo
+ Description
    + Author Liukai
+ Response 200
    
        {
          "data": {
            "id": 2,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2020-10-19 11:39:50",
            "modified": "2020-10-19 14:23:00",
            "equipmentId": 1,
            "onlyCode": "YzhjOWNmMmEyMzMxNGU0M2M4OWE3OTMxOWRlZTIyYWU=",
            "ipAddress": "192.168.2.43",
            "gatewayName": "中会网关1",
            "cloudAddress": "budee.com:9094",
            "location": "北京市海淀区",
            "organizationName": "宝迪",
            "collaborationSpace": "中会议室",
            "realLocation": "北京市丰台区方庄XXX街道",
            "versionNo": "1",
            "serviceConfReg": 1,
            "serviceCoreData": 1,
            "serviceMetadata": 1,
            "serviceCommand": 1,
            "cloudCommunicateTime": "2020-10-19 13:52:16",
            "runningStatus": 1
          }
        }

+ Response 400
    
        {
          "errors": [
            {
              "status": "400",
              "title": "Bad Request"
            }
          ]
        }


### 云端地址访问测试 [GET] /gatewayInfo/accessCloudTest

+ Description
    + Author Liukai
+ Parameters
    + cloudAddress (string)  云地址
+ Response 200  //测试成功
+ Response 400  //测试失败
    

### 物理端口添加 [POST] /physicalPort

+ Description
    

+ Parameters
    + data
        + address (string) 物理地址
        + builtIn （int） 默认是内置的0  1表示内置  0表示非内置
        + creator （long） 创建人
        + equipmentId （long）设备id
        + modifier （long）修改人
        + occupy （int）占用空闲（0空闲 1占用）
        + portName （string）物理端口名 com1 com2
        + portTypeId （long）端口类型id
    
+ Request (application/json)

            {
              "data": {
                "address": "天津",
                "builtIn": 1,
                "creator": 0,
                "equipmentId": 1,
                "modifier": 0,
                "occupy": 1,
                "portName": "COM2",
                "portTypeId": 2
              }
            }
+ Response 201

        {
          "data": {
            "id": 3,
            "type": "PhysicalPort"
          }
        }


### 物理端口删除 [DELETE] /physicalPort/{id}

+ Description
    + Author Liukai
    
+ Parameters
    + id (long) 物理端口ID
    
+ Request (application/json)

+ Response 204

+ Response 400

            {
              "errors": [
                {
                  "status": "400",
                  "title": "Bad Request",
                  "detail": "该物理端口为内置端口，不可删除"
                }
              ]
            }


### 物理端口详情 [GET] /physicalPort/{id}

+ Description
    + Author Liukai
    
+ Parameters
    + id (long) 物理端口ID

+ ReturnData

    + data
        + id (long) 物理端口id
        + portName （string） 物理端口名 com1 com2
        + address （string）物理地址
        + portType
            + id （long） 端口类型id
            + enabled （int）是否启用
            + creator （long）创建人
            + modifier （long）修改人
            + updateVersionId （long）跟云端同步使用
            + typeName （string）端口类型名/属性名 
            类型名字：串口
            属性名：属性名比如波特率 
            + parentId （long） 父id
            + valueType （int）0 字符串类型 1 整数型 2 FLOAT型 等多种类型
            + probableValueList （string） 返回值
    
+ Request (application/json)


+ Response 200

        {
          "data": {
            "id": 1,
            "portName": "网口",
            "address": "北京",
            "portType": {
              "id": 1,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "updateVersionId": 0,
              "typeName": "RS-485",
              "parentId": 0,
              "valueType": 0,
              "probableValueList": "ON"
            }
          }
        }

### 物理端口修改 [POST] /physicalPort/{id}

+ Description
    

+ Parameters
    + data
        + address (string) 物理地址
        + builtIn （int） 默认是内置的0  1表示内置  0表示非内置
        + creator （long） 创建人
        + equipmentId （long）设备id
        + modifier （long）修改人
        + occupy （int）占用空闲（0空闲 1占用）
        + portName （string）物理端口名 com1 com2
        + portTypeId （long）端口类型id
    
+ Request (application/json)

            {
              "data": {
                "address": "天津",
                "builtIn": 1,
                "creator": 0,
                "equipmentId": 1,
                "modifier": 0,
                "occupy": 1,
                "portName": "COM2",
                "portTypeId": 2
              }
            }
+ Response 200


### 物理端口列表 [GET] /physicalPort
+ Description
    + Author Liukai

+ ReturnData

    + data
        + id (long) 物理端口id
        + portName （string） 物理端口名 com1 com2
        + address （string）物理地址
        + equipmentId （long）设备id
        + portTypeId （long）端口类型id
        + occupy （int）使用空闲（0 空闲 1使用）
        + builtIn （int）是否内置（1内置 0非内置）
        + portType
            + id （long） 端口类型id
            + enabled （int）是否启用
            + creator （long）创建人
            + modifier （long）修改人
            + updateVersionId （long）跟云端同步使用
            + typeName （string）端口类型名/属性名 
            类型名字：串口
            属性名：属性名比如波特率 
            + parentId （long） 父id
            + valueType （int）0 字符串类型 1 整数型 2 FLOAT型 等多种类型
            + probableValueList （string） 返回值
        + equipment
            + id （long）设备id
            + cloudEquipmentId （long）云端id
            + updateVersionId （long）同步id
            + equipmentName （string）设备资产名称  必须唯一在同一个网关中
            + equipmentNameEn （string）唯一码
            + online （int）是否在线 0 离线 1在线 2未知
            + runningStatus （int） 运行状态：0关闭 1运行 2警告    3故障  4其他
            + serialNumber （string）设备序列号
            + purchaseDate （datatime） 采购日期
            + maintenanceTelephone （string） 维修电话
            + gatewayId （long）网关id 如果当前设备是网关则这个值为0
            + driveId （long）驱动id
            + ispdu （int）0 非pdu 1是pdu
            + controllable （int）是否可控 1 可控  0 不可控
            + builtIn （int）是否内置 1为内置 0为非内置
+ Response 200
    
        {
          "meta": {
            "totalPages": 1,
            "totalElements": 3,
            "size": 10,
            "number": 1,
            "numberOfElements": 3,
            "first": true,
            "last": true,
            "sort": null
          },
          "links": {
            "self": "/PhysicalPort?page[number]=1&page[size]=10",
            "first": "/PhysicalPort?page[number]=1&page[size]=10",
            "last": "/PhysicalPort?page[number]=1&page[size]=10"
          },
          "data": [
            {
              "id": 1,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "equipmentId": 1,
              "portName": "网口",
              "portTypeId": 1,
              "address": "北京",
              "occupy": 1,
              "builtIn": 1,
              "portType": {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "updateVersionId": 0,
                "typeName": "RS-485",
                "parentId": 0,
                "valueType": 0,
                "probableValueList": "ON"
              },
              "equipment": {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2020-10-18 09:18:51",
                "modified": "2020-10-18 09:18:56",
                "cloudEquipmentId": 1,
                "updateVersionId": 0,
                "equipmentName": "中会中控",
                "equipmentNameEn": "zhz",
                "online": 0,
                "runningStatus": 0,
                "serialNumber": "122",
                "purchaseDate": "2020-10-18T01:18:13.000+0000",
                "maintenanceTelephone": "13126822398",
                "gatewayId": 0,
                "driveId": 0,
                "ispdu": 0,
                "controllable": 1,
                "builtIn": 0
              }
            }
          ]
        }

+ Response 400
    
        {
          "errors": [
            {
              "status": "400",
              "title": "Bad Request"
            }
          ]
        }

### 端口类型列表 [GET] /portType
+ Description
    + Author Liukai

+ ReturnData

    + data
        + id （long） 端口类型id
        + enabled （int）是否启用
        + creator （long）创建人
        + modifier （long）修改人
        + updateVersionId （long）跟云端同步使用
        + typeName （string）端口类型名/属性名 
            类型名字：串口
            属性名：属性名比如波特率 
        + parentId （long） 父id
        + valueType （int）0 字符串类型 1 整数型 2 FLOAT型 等多种类型
        + probableValueList （string） 返回值
+ Response 200
    
        {
          "data": [
            {
              "id": 1,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-10-19 18:10:04",
              "modified": "2020-10-19 18:10:08",
              "updateVersionId": 0,
              "typeName": "RS-485",
              "parentId": 0,
              "valueType": 0,
              "probableValueList": ""
            },
            {
              "id": 2,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-10-19 13:51:17",
              "modified": "2020-10-19 13:51:17",
              "updateVersionId": 0,
              "typeName": "RS-232",
              "parentId": 0,
              "valueType": 0,
              "defaultValue": "",
              "probableValueList": ""
            },
            {
              "id": 7,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-10-19 18:14:15",
              "modified": "2020-10-19 18:14:17",
              "updateVersionId": 0,
              "typeName": "NetWork",
              "parentId": 0,
              "valueType": 0
            }
          ]
        }
+ Response 400
    
        {
          "errors": [
            {
              "status": "400",
              "title": "Bad Request"
            }
          ]
        }


## 环境数据分析接口  [GET]  /logEnvironment

+ Description
    + Author Liukai

+ Parameters
    + dateType  (int)   时间类型 1：月，2：周，3：日
    + dateMinStr (string)  开始日期 格式：yyyy-MM-dd HH:mm:ss
    + dateMaxStr (string)  结束日期 格式：yyyy-MM-dd HH:mm:ss

+ ReturnData
    + created (date) 创建日期
    + equipmentassetId (long) 资产设备ID
    + temperature (float)  温度  
    + humidity (float)   湿度
    + co2 (float)   co2
    + pm25 (float)   pm2.5
    + pm10 (float)   pm10
    + tvoc (float)   总挥发性有机化合物
    + ch2o (float)   甲醛
    + highLow (int)  1表示高  0表示低 （在周、日两个时间类型中不起作用）
              
+ Response 200

        {
          "data": [
            {
              "created": "2020-10-20 14:00:00",
              "equipmentassetId": 2,
              "temperature": 26,
              "humidity": 33.9,
              "co2": 1228,
              "pm25": 90,
              "pm10": 0.107,
              "tvoc": 0.6,
              "ch2o": 0.149
            },
            {
              "created": "2020-10-20 15:00:00",
              "equipmentassetId": 2,
              "temperature": 23,
              "humidity": 33.8,
              "co2": 1111,
              "pm25": 90,
              "pm10": 0.101,
              "tvoc": 0.6,
              "ch2o": 0.111
            },
            {
              "created": "2020-10-20 16:00:00",
              "equipmentassetId": 2,
              "temperature": 23,
              "humidity": 33.8,
              "co2": 1111,
              "pm25": 90,
              "pm10": 0.101,
              "tvoc": 0.6,
              "ch2o": 0.111
            },
            {
              "created": "2020-10-20 17:00:00",
              "equipmentassetId": 2,
              "temperature": 23,
              "humidity": 33.8,
              "co2": 1111,
              "pm25": 90,
              "pm10": 0.101,
              "tvoc": 0.6,
              "ch2o": 0.111
            }
          ]
        }

## 当前协作空间环境数据  [GET] /logEnvironment/currentEnvironment

+ Description
    + Author Liukai

+ Parameters

+ ReturnData
    + temperature (float)  温度  
    + humidity (float)   湿度
    + co2 (float)   co2
    + pm25 (float)   pm2.5
    + pm10 (float)   pm10
    + tvoc (float)   总挥发性有机化合物
    + ch2o (float)   甲醛
    + environmentLevel (int) 环境级别 4表示差，3表示中 2表示良 1表示优  0无评级
              
+ Response 200
    
        {
          "data": {
            "temperature": 25.7,
            "humidity": 19.3,
            "co2": 1018,
            "pm25": 32,
            "pm10": 0.057,
            "tvoc": 0.388,
            "ch2o": 0.109,
            "environmentLevel": 3
          }
        }
