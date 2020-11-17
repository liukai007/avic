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
    + 上周设备使用次数
    + 品牌设备统计
    + 分类设备统计
+ 2020年10月23日
    + 健康状况
    + 会议室使用情况统计/能耗统计
    + 上周设备耗能排行
    + Email配置详情
    + Email配置添加
    + Email配置修改
+ 2020年10月30日
    + 系统日志列表
    + 设备日志列表
    + 智能场景列表
    + 智能场景日志列表
+ 2020年11月2日
    + 设备链路添加
    + 设备链路详情
    + 设备链路删除
    + 设备链路修改
    + 设备列表
+ 2020年11月3日
    + 计划任务列表
    + 计划任务日志列表
    + 驱动列表
+ 2020年11月5日
    + 智能场景添加
    + 智能场景删除
    + 智能场景修改
    + 智能场景详情
+ 2020年11月9日
    + 计划任务添加
    + 计划任务删除
    + 计划任务修改
    + 计划任务详情
    + 远程服务台-设备详情
    + 远程服务台-设备列表
+ 2020年11月11日
    + 设备命令别称保存以及修改
    + 设备命令别名列表
+ 2020年11月13日
    + 设备按钮组添加/修改
    + 按钮组详情
    + 组和按钮添加、修改
    + 设备按钮组删除
+ 2020年11月17日
    + 品牌列表


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

## 上周设备使用次数  [GET]  /timesMalfunction/timesAndMalfunction

+ Description


+ Parameters
    + dateMinStr (string)  开始日期 格式：yyyy-MM-dd HH:mm:ss

+ ReturnData
    + equipmentId (long) 设备id
    + useTimes (int) 使用次数
    + malfunctionTimes (int)  故障次数  
    + equipmentName (string)   设备名称
    + model (string)   设备型号
    + timesHb (Double)   环比（周）

+ Response 200

        {
          "data": [
            {
              "equipmentId": 1,
              "useTimes": 20,
              "malfunctionTimes": 4,
              "equipmentName": "中会中控",
              "model": "SM300D2MOD",
              "timesHb": 33.33
            },
            {
              "equipmentId": 2,
              "useTimes": 5,
              "malfunctionTimes": 1,
              "equipmentName": "七合一环境传感器",
              "model": "SM300D2MOD"
            }
          ]
        }

## 品牌设备统计  [GET]  /equipment/brandStatistics

+ Description


+ Parameters

+ ReturnData
    + equipmentsum （int）设备总数
        + id (long) 品牌id
        + enabled (int) 是否使用
        + creator (long)  创建人  
        + modifier (long)   修改人
        + brandName (string)   品牌名称
        + website (string)   网址
        + displayOrder （int） 排序
        + total （int）数量

+ Response 200

        {
          "data": {
            "equipmentsum": 3,
            "brands": [
              {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "brandName": "extron",
                "website": "www。",
                "displayOrder": 100,
                "total": 1
              },
              {
                "id": 2,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "brandName": "baidu",
                "website": "www.baidu.com",
                "displayOrder": 100,
                "total": 2
              },
              {
                "id": 3,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "brandName": "企鹅",
                "website": "www.qie",
                "displayOrder": 100,
                "total": 0
              }
            ]
          }
        }
        
## 分类设备统计  [GET]  /equipment/categoryStatistics

+ Description


+ Parameters

+ ReturnData
    + equipmentsum （int） 设备总数
        + id (long) 分类id
        + enabled (int) 是否使用
        + creator (long)  创建人  
        + modifier (long)   修改人
        + categoryName (string)   分类名称
        + displayOrder （int） 排序
        + total （int）数量
        + created （data）创建时间
        + modified （data）修改时间
        + parentId （long）父id

+ Response 200

         {
          "data": {
            "equipmentsum": 3,
            "categories": [
              {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2020-10-20 14:09:15",
                "modified": "2020-10-20 14:09:13",
                "parentId": 0,
                "categoryName": "传感器",
                "displayOrder": 100,
                "total": 1
              },
              {
                "id": 2,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2020-10-20 14:09:44",
                "modified": "2020-10-20 14:09:41",
                "parentId": 1,
                "categoryName": "环境传感器",
                "displayOrder": 100,
                "total": 2
              },
              {
                "id": 3,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2020-10-27 11:02:40",
                "categoryName": "灯",
                "displayOrder": 100,
                "total": 0
              }
            ]
          }
        }

## 健康状况  [GET]  /GatewayManagement

+ Description


+ Parameters

+ ReturnData
    + id (long) id
    + enabled (int) 是否使用
    + creator (long)  创建人  
    + modifier (long)   修改人
    + created （data）创建时间
    + modified （data）修改时间
    + equipmentId （long）本地设备id
    + onlyCode （string）序列号
    + ipAddress （string）网关IP地址
    + gatewayName （string）网关名字
    + cloudAddress （string）云地址
    + location （string）地址 （手动填入的地址）
    + organizationName （string）所属机构
    + collaborationSpace （string）协作空间
    + cpuId （string）cpuid
    + diskId （string）硬盘唯一码
    + mainboardId （string）主板唯一号
    + realLocation （string）实时的位置
    + versionNo （string）版本
    + serviceConfReg （int）配置和注册（1正常 0异常）
    + serviceCoreData （int）核心数据服务（1正常 0 异常）
    + serviceMetadata （int）元数据服务（1正常 0 异常）
    + serviceCommand （int）命令服务（1正常 0异常）
    + cloudCommunicateTime （data）上次云通讯时间
    + runningStatus （int）
    + cpuUsage （float）cpu使用率（%）
    + totalMem （float）总内存（gb）
    + totalhd   （float）硬盘大小（gb）
    + usedhd （float）已用硬盘（gb）
    + ioUsage （float）硬盘使用率（%）
    + running （int）运行状态
    + equipmentNumber （long）设备数量
    + loadAverage （float）cup负载
    + memUsage （float）内存使用率（%）
    + beenUsed （float） 已使用内存（Gb）

+ Response 200

        {
          "data": {
            "id": 2,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2020-10-19 11:39:50",
            "modified": "2020-10-23 14:20:01",
            "equipmentId": 1,
            "onlyCode": "YzhjOWNmMmEyMzMxNGU0M2M4OWE3OTMxOWRlZTIyYWU=",
            "ipAddress": "192.168.2.43",
            "gatewayName": "中会网关1",
            "cloudAddress": "budee.com:9094",
            "location": "中国  北京 北京市 联通",
            "organizationName": "宝迪",
            "collaborationSpace": "中会议室",
            "cpuId": "51060400FFFBEBBF",
            "diskId": "L3MLCHC21213062",
            "mainboardId": "TOBEFILLEDBYO.E.M.",
            "realLocation": "中国  北京 北京市 联通",
            "versionNo": "1",
            "serviceConfReg": 1,
            "serviceCoreData": 1,
            "serviceMetadata": 1,
            "serviceCommand": 1,
            "cloudCommunicateTime": "2020-10-19 13:52:16",
            "runningStatus": 1,
            "cpuUsage": 61,
            "totalMem": 7.67,
            "totalhd": 916,
            "usedhd": 13,
            "ioUsage": 1,
            "running": 1,
            "equipmentNumber": 3,
            "loadAverage": 1.11,
            "memUsage": 71,
            "beenUsed": 5.44
          }
        }


### 会议室使用情况统计/能耗统计 [GET] /logUsedTimesElectric/energyAndTimes
+ Description
    + Author Liukai

+ Parameters
    + dateStr (string)  日期，格式：yyyy-MM-dd
    + dateType (int)  时间类型  0：年，1：月，2：周

+ ReturnData
    + id (long) ID
    + gatewayEquipmentId (long) 网关设备ID
    + times  (long)  次数
    + powerConsumption (float) 能耗量
    + created （data）创建时间
              
+ Response 200
    
        {
          "data": [
            {
              "id": 233,
              "created": "2020-10-19 00:00:00",
              "gatewayEquipmentId": 1,
              "times": 4,
              "powerConsumption": 0.98
            },
            {
              "id": 228,
              "created": "2020-10-20 00:00:00",
              "gatewayEquipmentId": 1,
              "times": 1,
              "powerConsumption": 9
            },
            {
              "id": 229,
              "created": "2020-10-21 00:00:00",
              "gatewayEquipmentId": 1,
              "times": 0,
              "powerConsumption": 61
            }
          ]
        }


## 上周设备耗能排行  [GET]  /timesMalfunction/energy

+ Description


+ Parameters
    + dateMinStr (string)  开始日期 格式：yyyy-MM-dd HH:mm:ss

+ ReturnData
    + equipmentId (long) 设备id
    + electricValueSum (Double) 耗电量
    + equipmentName (string)   设备名称
    + model (string)   设备型号
    + eneryValueHb (Double)   环比（周）

+ Response 200

        {
          "data": [
            {
              "equipmentId": 2,
              "equipentName": "七合一环境传感器",
              "electricValueSum": 2.2,
              "eneryValueHb": -12,
              "model": "SM300D2MOD"
            }
          ]
        }

## Email配置
+ Data
    + id (long) ID
    + emailAddress (string) Email地址
    + emailServerAddress (string) Email服务器地址
    + smtpUsername (string) smtp用户名
    + smtpPassword (string) smtp密码
    + smtpDomain (string) smtp域名
    + sslSwitch  (int)  SSL是否开启 1为SSL 0为非ssl
    + smtpPort (int) smtp端口
    + enabled (int)  - 使能  0禁止 1启用
    + creator (long) - 创建人
    + modifier (long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间


### Email配置详情 [GET] /emailSmtpConfig
+ Description
    + Author Liukai
+ Parameters
+ 
+ ReturnData
    + id (long) ID
    + emailAddress (string) Email地址
    + emailServerAddress (string) Email服务器地址
    + smtpUsername (string) smtp用户名
    + smtpPassword (string) smtp密码
    + smtpDomain (string) smtp域名
    + sslSwitch  (int)  SSL是否开启 1为SSL 0为非ssl
    + smtpPort (int) smtp端口
    + enabled (int)  - 使能  0禁止 1启用
    + creator (long) - 创建人
    + modifier (long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间
              
+ Response 200

### Email配置添加 [POST] /emailSmtpConfig
+ Description
    + Author Liukai

+ Parameters
    + data
        + emailAddress (string) Email地址
        + emailServerAddress (string) Email服务器地址
        + smtpUsername (string) smtp用户名
        + smtpPassword (string) smtp密码
        + smtpDomain (string) smtp域名
        + sslSwitch  (int)  SSL是否开启 1为SSL 0为非ssl
        + smtpPort (int) smtp端口
      
+ ReturnData
    + id (long) ID
    + type (string) emailSmtpConfig

              
+ Response 200

        {
          "data": {
            "id": 1,
            "type": "emailSmtpConfig"
          }
        } 

### Email配置修改 [PATCH] /emailSmtpConfig/{id}
+ Description
    + Author Liukai

+ Parameters
    + id (long) ID 
    + data
        + emailAddress (string) Email地址
        + emailServerAddress (string) Email服务器地址
        + smtpUsername (string) smtp用户名
        + smtpPassword (string) smtp密码
        + smtpDomain (string) smtp域名
        + sslSwitch  (int)  SSL是否开启 1为SSL 0为非ssl
        + smtpPort (int) smtp端口
    
+ Response 200



## 系统日志列表  [GET]  /logSystem

+ Description


+ Parameters
    + dateMinStr (string)  开始日期 格式：yyyy-MM-dd HH:mm:ss
    + dateMaxStr （string）结束日期 格式：yyyy-MM-dd HH:mm:ss
    + eventContent （string）事件内容
    + filter[userId] （long）用户id
    + page[number] （int）页码
    + page[size] （int）条数
    + sort （Array[string]） 排序

+ ReturnData
    + id (long) 系统日志id
    + enabled (int) 是否启用
    + creator (Long)  创建人  
    + created (datetime)   创建时间
    + eventContent (string)   日志内容

+ Response 200

        {
          "data": [
            {
              "id": 1,
              "enabled": 1,
              "creator": 0,
              "created": "2020-10-29 11:53:30",
              "eventContent": "$2a$04$Xsk3KBc.yHjysEUBOZO7WO7HgUy70OMf34n/N/Imo0YcpJBtkd5rW用户--用户名或密码错误！"
            },
            {
              "id": 2,
              "enabled": 1,
              "creator": 0,
              "created": "2020-10-29 11:59:40",
              "eventContent": "admin用户--用户名或密码错误！"
            }
          ]
        }
    
    
## 设备日志列表  [GET]  /logEquipment

+ Description


+ Parameters
    + dateMinStr (string)  开始日期 格式：yyyy-MM-dd HH:mm:ss 必填
    + dateMaxStr （string）结束日期 格式：yyyy-MM-dd HH:mm:ss 必填
    + eventContent （string）事件内容
    + eventResult (int) 执行结果
    + filter[equipmentId] （long）设备id
    + filter[logLevel] （int）日志级别 0:错误 1:警告 2:信息 3:调试
    + filter[userId] （long）用户id
    + page[number] （int）页码
    + page[size] （int）条数
    + sort （Array[string]） 排序

+ ReturnData
    + id (long) 设备日志id
    + enabled (int) 是否启用
    + creator (Long)  创建人  
    + created (datetime)   创建时间
    + eventContent (string)  事件内容
    + logLevel （int）日志级别   0:错误       1:警告    2:信息    3:调试
    + operateType （int）0 常规操作 1是场景操作 2是计划任务
    + operateId （long）实际操作id就是场景日志的id或者计划任务的ID
    + eventResult （int） 1执行成功，0执行失败
    + malfunctionTimes （int）防止出现大量错误日志，把表填满
    + analyzed （int）是否被统计 0未被分析，1已经被分析
    + readed （int）0未读，1已读'
    + upload （int）0未上传，1已经上传        日志是否上传的标志位.'
    + userName （string）用户名
    + equipmentModel （string）设备型号
    + equipmentName （string）设备名称

+ Response 200

        {
          "data": [
            {
              "id": 2,
              "enabled": 1,
              "creator": 1,
              "modifier": 0,
              "created": "2020-10-23 10:23:11",
              "modified": "2020-10-23 10:23:11",
              "logLevel": 1,
              "operateType": 0,
              "operateId": 0,
              "eventContent": "没有电量设备，可以进行电量统计",
              "eventResult": 0,
              "malfunctionTimes": 0,
              "analyzed": 0,
              "readed": 0,
              "upload": 0,
              "userName": "admin"
            }
            {
              "id": 6,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-10-23 11:53:12",
              "modified": "2020-10-23 11:53:12",
              "logLevel": 0,
              "equipmentId": 3,
              "operateType": 0,
              "operateId": 0,
              "eventContent": "电量值异常不可能为0或者是第一次使用",
              "eventResult": 0,
              "malfunctionTimes": 0,
              "analyzed": 0,
              "readed": 0,
              "upload": 0,
              "equipmentModel": "sw010",
              "equipmentName": "中会智能电表"
            }
          ]
        }


## 智能场景列表  [GET]  /intelligentScene

+ Description


+ Parameters
    + filter[sceneName] (string)  场景名称
    + filter[sceneType] （int）场景类型 0为触发类型，1为条件类型
    + page[number] （int）页码
    + page[size] （int）条数
    + sort （Array[string]） 排序

+ ReturnData
    + id (long) 设备日志id
    + enabled (int) 是否启用
    + creator (Long)  创建人  
    + created (datetime)   创建时间
    + sceneName (string)  场景名称
    + sceneType （int）0为触发类型，1为条件类型
    + opened （int）1表示开启，0表示关闭
    + running （int）是否运行

+ Response 200

        {
          "data": [
            {
              "id": 1,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-10-28 17:14:01",
              "modified": "2020-10-28 17:14:04",
              "sceneName": "关闭会议",
              "sceneType": 0,
              "opened": 1,
              "running": 1
            }
          ]
        }

## 智能场景日志列表  [GET]  /intelligentScene/sceneLog

+ Description


+ Parameters
    + dateMinStr (string)  开始日期 格式：yyyy-MM-dd HH:mm:ss 必填
    + dateMaxStr （string）结束日期 格式：yyyy-MM-dd HH:mm:ss 必填
    + eventContent （string）事件内容
    + eventResult (int) 执行结果
    + filter[userId] （long）用户id
    + sceneName (string)  场景名称
    + sceneType （int）0为触发类型，1为条件类型
    + page[number] （int）页码
    + page[size] （int）条数
    + sort （Array[string]） 排序

+ ReturnData
    + id (long) 设备日志id
    + creator (Long)  创建人  
    + created (datetime)   创建时间
    + operateType (int)  0 常规操作 1是场景操作 2是计划任务
    + sceneTaskId （long）智能场景id
    + eventContent （string） 事件内容
    + eventResult （int）1成功 0失败
    + sceneName （string）智能场景名称
    + userName （string）用户名称
    + sceneType （int）0为触发类型，1为条件类型

+ Response 200

        {
          "data": [
            {
              "id": 1,
              "creator": 1,
              "created": "2020-10-28 17:19:12",
              "operateType": 1,
              "sceneTaskId": 1,
              "eventContent": "执行关闭会议",
              "eventResult": 1,
              "sceneName": "关闭会议",
              "userName": "admin"
            },
            {
              "id": 2,
              "creator": 1,
              "created": "2020-10-28 17:20:08",
              "operateType": 1,
              "sceneTaskId": 1,
              "eventContent": "执行关闭会议",
              "eventResult": 1,
              "sceneName": "关闭会议",
              "userName": "admin"
            }
          ]
        }


## 设备链路添加  [post]  /equipmentLink

+ Description


+ Parameters
    + data
        + communicationMode (string)  通讯方式（0 音频 1 视频 2 网络 .......）
        + leftEquipmentId （long）左端设备id
        + linkClassify （int） 1 单向 2 双向（连接分类）
        + linkName (string) 设备链路名
        + rightEquipmentId （long）右端设备id

+ ReturnData


+ Response 201

        {
            "data": {
                "id": 3,
                "type": "equipmentLink"
            }
        }

## 设备链路详情  [GET]  /equipmentLink/{id}

+ Description


+ Parameters
    + id (long)  设备链路id
 

+ ReturnData
    + id (long) 设备日志id
    + creator (Long)  创建人  
    + created (datetime)   创建时间
    + linkName (string)  链路名称
    + linkClassify （int）通讯方式（0 音频 1 视频 2 网络 .......）
    + communicationMode （int） 连接分类（1 单向 2 双向）
    + leftEquipmentId （long）左端设备id
    + rightEquipmentId （long）右端设备id
    + leftEquipmentName （string）左端设备名
    + rightEquipmentName （string）右端设备名

+ Response 200

        {
          "data": {
            "id": 1,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2020-11-02 16:45:30",
            "modified": "2020-11-02 16:45:30",
            "linkName": "传感器",
            "linkClassify": 0,
            "communicationMode": 1,
            "leftEquipmentId": 1,
            "rightEquipmentId": 2,
            "leftEquipmentName": "中会中控",
            "rightEquipmentName": "七合一环境传感器"
          }
        }

## 设备链路删除  [DELETE]  /equipmentLink/{id}

+ Description


+ Parameters
    + id (long)  设备链路id
 

+ ReturnData

+ Response 204

## 设备链路修改  [PATCH]  /equipmentLink/{id}

+ Description


+ Parameters
    + data
        + communicationMode (string)  通讯方式（0 音频 1 视频 2 网络 .......）
        + leftEquipmentId （long）左端设备id
        + linkClassify （int） 1 单向 2 双向（连接分类）
        + linkName (string) 设备链路名
        + rightEquipmentId （long）右端设备id
    + id （long）链路id
+ ReturnData


+ Response 200

### 设备列表 [GET] /equipment
+ Description

+ Parameters
    + equipmentName (string)  设备名
    + filter[brandId] （long）品牌ID
    + filter[categoryId] （long）分类Id
    + model (string)型号
    + online （int）0 离线 1在线 2未知（是否在线）
    + runningStatus (int)  运行状态（0关闭 1运行 2警告 3故障 4其他）
    + page[number] （int）页码
    + page[size] （int）条数
    + sort （Array[string]） 排序

+ ReturnData
    + id （long） 端口类型id
    + enabled （int）是否启用
    + creator （long）创建人
    + modifier （long）修改人
    + updateVersionId （long）跟云端同步使用
    + cloudEquipmentId （long）云端id
    + equipmentName （string） 设备名
    + equipmentNameEn （string）自动生成唯一号
    + online （int） 是否在线：0 离线 1在线 2未知
    + runningStatus （int）运行状态 0关闭 1运行 2警告    3故障  4其他
    + serialNumber （string）设备序列号
    + purchaseDate （data）采购日期
    + maintenanceTelephone （string）维修电话
    + gatewayId （long）网关id
    + driveId （long） 驱动id
    + ispdu （int）0 非pdu 1是pdu
    + controllable （int）是否可控 1 可控  0 不可控
    + builtIn （int）是否内置 1为内置 0为非内置
    + fixedAttribute （int）0 无固定属性，1为环境  2 占位 3 能耗
    + functionCode （int）'0 无功能  1 是次数  2 是电表记录'
    + maintainData （data）保养日期
    + brandName （string）品牌名
    + model （string）型号
    + categroyName （string）分类名
        
        
+ Response 200
    
        {
          "data": [
            {
              "id": 1,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-10-18 09:18:51",
              "modified": "2020-10-18 09:18:56",
              "cloudEquipmentId": 0,
              "updateVersionId": 0,
              "equipmentName": "中会中控",
              "equipmentNameEn": "zhz",
              "online": 0,
              "runningStatus": 0,
              "serialNumber": "122",
              "purchaseDate": "2020-10-18T01:18:13.000+0000",
              "maintenanceTelephone": "13126822398",
              "gatewayId": 1,
              "driveId": 2,
              "ispdu": 0,
              "controllable": 1,
              "builtIn": 0,
              "fixedAttribute": 0,
              "functionCode": 0,
              "maintainData": "2020-10-21T10:42:01.000+0000",
              "brandName": "baidu",
              "model": "sw010",
              "categroyName": "传感器"
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

### 计划任务列表 [GET] /scheduledTask
+ Description

+ Parameters
    + filter[sceneName] (string)  计划任务名


+ ReturnData
    + id （long） 端口类型id
    + enabled （int）是否启用
    + creator （long）创建人
    + modifier （long）修改人
    + taskName （string）计划任务名
    + taskYear （string）年
    + taskMonth （string） 月
    + taskWeekbymonth （string）每月第几周
    + taskWeek （string） 周
    + taskDay （string）日
    + taskHour （string）时
    + taskMinute （string）分
    + taskSecond （string）秒
    + frequency （int）0 日 1周 2月 3年（频率）
        
        
+ Response 200
    
        {
          "data": [
            {
              "id": 1,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-10-29 11:26:17",
              "modified": "2020-10-29 11:26:19",
              "taskName": "每日定时关闭",
              "taskYear": "2020",
              "taskMonth": "10",
              "taskWeekbymonth": "25"
            },
            {
              "id": 2,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-10-30 11:06:29",
              "modified": "2020-10-30 11:06:29",
              "taskName": "关投影",
              "taskYear": "*",
              "taskMonth": "*",
              "taskWeekbymonth": "*",
              "taskWeek": "?",
              "taskDay": "*/1",
              "taskHour": "16",
              "taskMinute": "00",
              "taskSecond": "00",
              "frequency": 0
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

### 计划任务日志列表 [GET] /scheduledTask/scheduledLog
+ Description

+ Parameters
    + dateMinStr (string)  开始日期 格式：yyyy-MM-dd HH:mm:ss 必填
    + dateMaxStr （string）结束日期 格式：yyyy-MM-dd HH:mm:ss 必填
    + eventResult (int) 执行结果 （执行成功1  执行失败0）
    + sceneName (string)  任务名称
    + page[number] （int）页码
    + page[size] （int）条数
    + sort （Array[string]） 排序

+ ReturnData
    + id （long） 端口类型id
    + enabled （int）是否启用
    + creator （long）创建人
    + modifier （long）修改人
    + operateType （int）0 常规操作 1是场景操作 2是计划任务
    + sceneTaskId （long）计划任务id
    + eventContent （string） 事件内容
    + eventResult （int）执行成功1  执行失败0
    + sceneName （string） 任务名
    + userName （string）用户名
        
        
+ Response 200
    
        {
          "data": [
            {
              "id": 6,
              "creator": 1,
              "created": "2020-10-29 11:27:41",
              "operateType": 2,
              "sceneTaskId": 1,
              "eventContent": "执行每日定时关闭",
              "eventResult": 1,
              "sceneName": "每日定时关闭",
              "userName": "admin"
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

### 驱动列表 [GET] /drive
+ Description

+ Parameters
    + belong (int)  0 本地 1 云端
    + equipmentName （string）设备名
    + filter[brandId] (long) 品牌id
    + filter[categoryId] (long)  分类id
    + model （string）型号
    + page[number] （int）页码
    + page[size] （int）条数
    + sort （Array[string]） 排序

+ ReturnData
    + id （long） 端口类型id
    + enabled （int）是否启用
    + creator （long）创建人
    + modifier （long）修改人
    + cloudDriveId （long）云驱动id
    + updateVersionId （long）更新版本id
    + equipmentName （string） 设备名称
    + model （string）型号
    + categoryId （long） 分类id
    + brandId （long）品牌id
    + belong （int）本地 是0   云端是1
    + operation （int）0 无操作  1已上传  2下载 3 已下载（操作）
    + brandName （string） 品牌名
    + categoryName （string）分类名
    + firmware （string）固件
        
        
+ Response 200
    
        {
          "data": [
            {
              "id": 3,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-10-27 11:01:47",
              "modified": "2020-10-27 11:01:51",
              "updateVersionId": 0,
              "equipmentName": "中控",
              "model": "W101",
              "categoryId": 3,
              "brandId": 3,
              "firmware": "q101",
              "belong": 0,
              "operation": 0,
              "brandName": "企鹅",
              "categoryName": "灯"
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


### 智能场景添加 [POST] /intelligentScene

+ Description
    

+ Parameters
    + data
        + creator (long) 创建人
        + builtIn （int） 默认是内置的0  1表示内置  0表示非内置
        + displayOrder （int） 排序
        + enabled （int）是否启用
        + isFront （int）是否前台展示 1表示前台展示 0表示非前台展示
        + opened （int）1表示开启，0表示关闭
        + running （int）是否运行中
        + sceneEndTime （date）启用时间
        + sceneName （string）场景名
        + sceneStartTime （date）场景到期时间
        + sceneType （int）0为触发类型，1为条件类型
        + sceneTaskConditions
            + conditionalRelation （int）关联条件 0 and  1 or
            + creator （long）创建人
            + enabled （int）是否启用
            + equipmentId （long）设备id
            + judgeCondition （判断条件）0 ==等于， 1  !=不等于， 2 <小于，  3 >大于，  4  <=小于等于， 5 >=大于等于
            + operateType （int）1是场景操作 2是计划任务
            + readTypeId （long）读数类型id
            + readValue （string）读数值 可以是字符串也可以是具体的类型。根据读数类型进行转换
        + sceneTaskDetails 
            + creator （long）创建人
            + driveCmdId （long）驱动命令id
            + enabled （int）是否启用
            + equipmentId （long）设备id
            + operateType （int）1是场景操作 2是计划任务
            + parameter （string）参数
    
+ Request (application/json)

        {
        	"data": {
        		"builtIn": 0,
        		"creator": 0,
        		"displayOrder": 0,
        		"enabled": 0,
        		"isFront": 0,
        		"opened": 0,
        		"running": 0,
        		"sceneEndTime": "2020-11-05 14:13:47",
        		"sceneName": "string",
        		"sceneStartTime": "2020-11-05 14:13:47",
        		"sceneTaskConditions": [{
        			"conditionalRelation": 0,
        			"creator": 0,
        			"enabled": 0,
        			"equipmentId": 0,
        			"judgeCondition": 0,
        			"operateType": 0,
        			"readTypeId": 0,
        			"readValue": "string",
        			"sceneTaskId": 0
        		}],
        		"sceneTaskDetails": [{
        			"creator": 0,
        			"driveCmdId": 0,
        			"enabled": 0,
        			"equipmentId": 0,
        			"operateType": 0,
        			"parameter": "string",
        
        		}],
        		"sceneType": 0
        	}
        }
+ Response 201

        {
          "data": {
            "id": 3,
            "type": "IntelligentScene"
          }
        }


### 智能场景删除 [DELETE] /intelligentScene/{id}

+ Description

    
+ Parameters
    + id (long) 场景ID
    
+ Request (application/json)

+ Response 204

+ Response 400

            {
              "errors": [
                {
                  "status": "400",
                  "title": "Bad Request"
                }
              ]
            }


### 智能场景修改 [POST] /intelligentScene/{id}

+ Description
    

+ Parameters
    + data
        + creator (long) 创建人
        + builtIn （int） 默认是内置的0  1表示内置  0表示非内置
        + displayOrder （int） 排序
        + enabled （int）是否启用
        + isFront （int）是否前台展示 1表示前台展示 0表示非前台展示
        + opened （int）1表示开启，0表示关闭
        + running （int）是否运行中
        + sceneEndTime （date）启用时间
        + sceneName （string）场景名
        + sceneStartTime （date）场景到期时间
        + sceneType （int）0为触发类型，1为条件类型
        + sceneTaskConditions
            + id （long）条件id
            + conditionalRelation （int）关联条件 0 and  1 or
            + creator （long）创建人
            + enabled （int）是否启用
            + equipmentId （long）设备id
            + judgeCondition （判断条件）0 ==等于， 1  !=不等于， 2 <小于，  3 >大于，  4  <=小于等于， 5 >=大于等于
            + operateType （int）1是场景操作 2是计划任务
            + readTypeId （long）读数类型id
            + readValue （string）读数值 可以是字符串也可以是具体的类型。根据读数类型进行转换
        + sceneTaskDetails 
            + id (long) 详情表id
            + creator （long）创建人
            + driveCmdId （long）驱动命令id
            + enabled （int）是否启用
            + equipmentId （long）设备id
            + operateType （int）1是场景操作 2是计划任务
            + parameter （string）参数
    
+ Request (application/json)

        {
        	"data": {
        		"builtIn": 0,
        		"creator": 0,
        		"displayOrder": 0,
        		"enabled": 0,
        		"isFront": 0,
        		"opened": 0,
        		"running": 0,
        		"sceneEndTime": "2020-11-05T06:51:25.601Z",
        		"sceneName": "string",
        		"sceneStartTime": "2020-11-05T06:51:25.601Z",
        		"sceneTaskConditions": [{
        		    "id": 0,
        			"conditionalRelation": 0,
        			"creator": 0,
        			"enabled": 0,
        			"equipmentId": 0,
        			"judgeCondition": 0,
        			"operateType": 0,
        			"readTypeId": 0,
        			"readValue": "string",
        			"sceneTaskId": 0
        		},
        		{
        			"conditionalRelation": 0,
        			"creator": 0,
        			"enabled": 0,
        			"equipmentId": 0,
        			"judgeCondition": 0,
        			"operateType": 0,
        			"readTypeId": 0,
        			"readValue": "string",
        			"sceneTaskId": 0
        		}
        		],
        		"sceneTaskDetails": [{
        		    "id": 0,
        			"creator": 0,
        			"driveCmdId": 0,
        			"enabled": 0,
        			"equipmentId": 0,
        			"operateType": 0,
        			"parameter": "string",
        		},
        		{
        			"creator": 0,
        			"driveCmdId": 0,
        			"enabled": 0,
        			"equipmentId": 0,
        			"operateType": 0,
        			"parameter": "string",
        		}
        		],
        		"sceneType": 0
        	}
        }

+ Response 200


### 智能场景详情 [GET] /intelligentScene/{id}

+ Description

    
+ Parameters
    + id (long) 场景ID

+ ReturnData

    + data
        + id （long）场景id
        + creator (long) 创建人
        + builtIn （int） 默认是内置的0  1表示内置  0表示非内置
        + displayOrder （int） 排序
        + enabled （int）是否启用
        + isFront （int）是否前台展示 1表示前台展示 0表示非前台展示
        + opened （int）1表示开启，0表示关闭
        + running （int）是否运行中
        + sceneEndTime （date）启用时间
        + sceneName （string）场景名
        + sceneStartTime （date）场景到期时间
        + sceneType （int）0为触发类型，1为条件类型
        + sceneTaskConditions
            + id （long）条件id
            + conditionalRelation （int）关联条件 0 and  1 or
            + creator （long）创建人
            + enabled （int）是否启用
            + equipmentId （long）设备id
            + judgeCondition （判断条件）0 ==等于， 1  !=不等于， 2 <小于，  3 >大于，  4  <=小于等于， 5 >=大于等于
            + operateType （int）1是场景操作 2是计划任务
            + readTypeId （long）读数类型id
            + readValue （string）读数值 可以是字符串也可以是具体的类型。根据读数类型进行转换
            + sceneTaskId （long）场景id
            + equipmentName （string）设备名
            + model （string）型号
        + sceneTaskDetails 
            + id (long) 详情表id
            + creator （long）创建人
            + driveCmdId （long）驱动命令id
            + enabled （int）是否启用
            + equipmentId （long）设备id
            + operateType （int）1是场景操作 2是计划任务
            + parameter （string）参数
            + sceneTaskId （long）智能场景id
            + equipmentName （string）设备名
            + cmdName （string）命令名
            + secondCategoryId （long）二级分类
            + secondCategoryName （string）二级分类名
            + primaryCategoryId （long）一级分类
            + primaryCategoryName （string）一级分类名
            + model （string）型号
    
+ Request (application/json)


+ Response 200

        {
          "data": {
            "id": 2,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2020-10-28 17:14:45",
            "modified": "2020-10-28 17:14:48",
            "sceneName": "观影模式",
            "sceneType": 1,
            "opened": 1,
            "running": 1,
            "displayOrder": 100,
            "sceneTaskDetails": [
              {
                "id": 2,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2020-11-04 16:40:55",
                "modified": "2020-11-04 16:40:58",
                "operateType": 1,
                "sceneTaskId": 2,
                "equipmentId": 1,
                "driveCmdId": 1,
                "equipmentName": "中会中控",
                "cmdName": "查找",
                "secondCategoryId": 1,
                "secondCategoryName": "传感器",
                "model": "sw010"
              },
              {
                "id": 3,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2020-11-05 10:24:26",
                "modified": "2020-11-05 10:24:26",
                "operateType": 1,
                "sceneTaskId": 2,
                "equipmentId": 2,
                "driveCmdId": 1,
                "equipmentName": "七合一环境传感器",
                "cmdName": "查找",
                "parameter": "28",
                "secondCategoryId": 2,
                "secondCategoryName": "环境传感器",
                "primaryCategoryId": 1,
                "primaryCategoryName": "传感器",
                "model": "SM300D2MOD"
              }
            ],
            "sceneTaskConditions": [
              {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2020-11-04 16:39:06",
                "modified": "2020-11-04 16:39:08",
                "operateType": 1,
                "sceneTaskId": 2,
                "equipmentId": 2,
                "readTypeId": 1,
                "conditionalRelation": 0,
                "judgeCondition": 0,
                "readValue": "10",
                "equipmentName": "七合一环境传感器",
                "model": "SM300D2MOD"
              }
            ]
          }
        }



### 计划任务添加 [POST] /scheduledTask

+ Description
    

+ Parameters
    + data
        + creator (long) 创建人
        + builtIn （int） 默认是内置的0  1表示内置  0表示非内置
        + displayOrder （int） 排序
        + enabled （int）是否启用
        + taskDay （string）天
        + taskHour （string）小时
        + taskMonth （string）月
        + taskName （string）任务名
        + taskSecond （string）秒
        + taskWeek （string）周
        + taskYear （string）年
        + sceneStartTime （date） 启用时间
        + sceneEndTime （date）计划任务到期时间 必须小于启动时间
        + sceneTaskConditions
            + conditionalRelation （int）关联条件 0 and  1 or
            + creator （long）创建人
            + enabled （int）是否启用
            + equipmentId （long）设备id
            + judgeCondition （判断条件）0 ==等于， 1  !=不等于， 2 <小于，  3 >大于，  4  <=小于等于， 5 >=大于等于
            + operateType （int）1是场景操作 2是计划任务
            + readTypeId （long）读数类型id
            + readValue （string）读数值 可以是字符串也可以是具体的类型。根据读数类型进行转换
        + sceneTaskDetails 
            + creator （long）创建人
            + driveCmdId （long）驱动命令id
            + enabled （int）是否启用
            + equipmentId （long）设备id
            + operateType （int）1是场景操作 2是计划任务
            + parameter （string）参数
    
+ Request (application/json)

        {
          "data": {
            "sceneTaskConditions": [
              {
                "conditionalRelation": 0,
                "equipmentId": 1,
                "judgeCondition": 0,
                "operateType": 2,
                "readTypeId": 1,
                "readValue": "5"
              }
            ],
            "sceneTaskDetails": [
              {
                "driveCmdId": 2,
                "equipmentId": 2,
                "operateType": 2,
                "parameter": "15"
              }
            ],
            "taskDay": "*/1",
            "taskHour": "10",
            "taskMinute": "00",
            "taskMonth": "*",
            "taskName": "定时打扫",
            "taskSecond": "00",
            "taskWeek": "?",
            "taskWeekbymonth": "*",
            "taskYear": "*",
            "sceneStartTime": "2020-11-05 11:27:06",
            "sceneEndTime": "2020-11-09 11:27:06"
          }
        }
+ Response 201

        {
          "data": {
            "id": 3,
            "type": "ScheduledTask"
          }
        }


### 计划任务删除 [DELETE] /scheduledTask/{id}

+ Description

    
+ Parameters
    + id (long) 任务ID
    
+ Request (application/json)

+ Response 204

+ Response 400

            {
              "errors": [
                {
                  "status": "400",
                  "title": "Bad Request"
                }
              ]
            }


### 计划任务详情 [GET] /intelligentScene/{id}

+ Description

    
+ Parameters
    + id (long) 场景ID

+ ReturnData

    + data
        + id （long）场景id
        + creator (long) 创建人
        + builtIn （int） 默认是内置的0  1表示内置  0表示非内置
        + displayOrder （int） 排序
        + enabled （int）是否启用
        + taskName （string）任务名
        + taskYear （string）年
        + taskMonth （string）月
        + taskWeekbymonth （string）每月的第几周(1,2,3,4,5)
        + taskWeek （string）周
        + taskDay （string）天
        + taskHour （string）小时
        + taskMinute (string) 分
        + taskSecond （string）秒
        + sceneTaskConditions
            + id （long）条件id
            + conditionalRelation （int）关联条件 0 and  1 or
            + creator （long）创建人
            + enabled （int）是否启用
            + equipmentId （long）设备id
            + judgeCondition （判断条件）0 ==等于， 1  !=不等于， 2 <小于，  3 >大于，  4  <=小于等于， 5 >=大于等于
            + operateType （int）1是场景操作 2是计划任务
            + readTypeId （long）读数类型id
            + readValue （string）读数值 可以是字符串也可以是具体的类型。根据读数类型进行转换
            + sceneTaskId （long）场景id
            + equipmentName （string）设备名
            + model （string）型号
        + sceneTaskDetails 
            + id (long) 详情表id
            + creator （long）创建人
            + driveCmdId （long）驱动命令id
            + enabled （int）是否启用
            + equipmentId （long）设备id
            + operateType （int）1是场景操作 2是计划任务
            + parameter （string）参数
            + sceneTaskId （long）智能场景id
            + equipmentName （string）设备名
            + cmdName （string）命令名
            + secondCategoryId （long）二级分类
            + secondCategoryName （string）二级分类名
            + primaryCategoryId （long）一级分类
            + primaryCategoryName （string）一级分类名
            + model （string）型号
    
+ Request (application/json)


+ Response 200

        {
          "data": {
            "id": 6,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2020-11-05 11:27:06",
            "modified": "2020-11-09 19:13:52",
            "taskName": "定时打扫",
            "taskYear": "*",
            "taskMonth": "*",
            "taskWeekbymonth": "*",
            "taskWeek": "?",
            "taskDay": "*/1",
            "taskHour": "10",
            "taskMinute": "00",
            "taskSecond": "00",
            "sceneTaskDetails": [
              {
                "id": 4,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2020-11-05 11:27:20",
                "modified": "2020-11-09 19:13:52",
                "operateType": 2,
                "sceneTaskId": 6,
                "equipmentId": 2,
                "driveCmdId": 2,
                "equipmentName": "七合一传感器",
                "cmdName": "插入",
                "parameter": "15",
                "secondCategoryId": 2,
                "secondCategoryName": "环境传感器",
                "primaryCategoryId": 1,
                "primaryCategoryName": "传感器",
                "model": "SM300D2MOD"
              }
            ],
            "sceneTaskConditions": [
              {
                "id": 3,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2020-11-05 11:27:22",
                "modified": "2020-11-09 19:13:52",
                "operateType": 2,
                "sceneTaskId": 6,
                "equipmentId": 1,
                "readTypeId": 1,
                "conditionalRelation": 0,
                "judgeCondition": 0,
                "readValue": "5",
                "equipmentName": "中控",
                "model": "W101"
              }
            ]
          }
        }



### 计划任务修改 [POST] /scheduledTask/{id}

+ Description
    

+ Parameters
    + data
        + creator (long) 创建人
        + builtIn （int） 默认是内置的0  1表示内置  0表示非内置
        + displayOrder （int） 排序
        + enabled （int）是否启用
        + taskDay （string）天
        + taskHour （string）小时
        + taskMonth （string）月
        + taskName （string）任务名
        + taskSecond （string）秒
        + taskWeek （string）周
        + taskYear （string）年
        + sceneStartTime （date） 启用时间
        + sceneEndTime （date）计划任务到期时间 必须小于启动时间
        + sceneTaskConditions
            + id （long）条件id （id也传到后端）
            + conditionalRelation （int）关联条件 0 and  1 or
            + creator （long）创建人
            + enabled （int）是否启用
            + equipmentId （long）设备id
            + judgeCondition （判断条件）0 ==等于， 1  !=不等于， 2 <小于，  3 >大于，  4  <=小于等于， 5 >=大于等于
            + operateType （int）1是场景操作 2是计划任务
            + readTypeId （long）读数类型id
            + readValue （string）读数值 可以是字符串也可以是具体的类型。根据读数类型进行转换
        + sceneTaskDetails 
            + id （long）任务详情id （id也传到后端）
            + creator （long）创建人
            + driveCmdId （long）驱动命令id
            + enabled （int）是否启用
            + equipmentId （long）设备id
            + operateType （int）1是场景操作 2是计划任务
            + parameter （string）参数
    
+ Request (application/json)

        {
          "data": {
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2020-11-05 11:27:06",
            "modified": "2020-11-09 19:13:52",
            "taskName": "打扫机器人",
            "taskYear": "*",
            "taskMonth": "*",
            "taskWeekbymonth": "*",
            "taskWeek": "?",
            "taskDay": "*/1",
            "taskHour": "10",
            "taskMinute": "00",
            "taskSecond": "00",
            "sceneTaskDetails": [
              {
                "id": 4,
                "operateType": 2,
                "equipmentId": 2,
                "driveCmdId": 2,
                "parameter": "20"
              }
            ],
            "sceneTaskConditions": [
              {
                "id": 3,
                "operateType": 2,
                "equipmentId": 1,
                "readTypeId": 1,
                "conditionalRelation": 0,
                "judgeCondition": 0,
                "readValue": "10"
              }
            ]
          }
        }

+ Response 200


### 远程服务台-设备详情 [GET] /DeviceButtonDetails/{id}

+ Description
    + Author Liukai
    
+ Parameters
    + id (long) 设备ID

+ ReturnData

    + data
        + id (long) 设备id
        + enabled 
        + creator 
        + modifier
        + created
        + modified
        + cloudEquipmentId （long）云端id
        + updateVersionId （long）同步id
        + equipmentName （string）设备名
        + anotherName （string）设备别名
        + equipmentNameEn （string）设备英文名
        + online （int） 是否在线：0 离线 1在线 2未知
        + runningStatus （int）运行状态：0关闭 1运行 2警告    3故障  4其他'
        + serialNumber （string）设备序列号
        + purchaseDate （date）采购日期
        + maintenanceTelephone （string）维修电话
        + gatewayId （long）网关id
        + driveId （long）驱动id
        + ispdu （int）0 非pdu 1是pdu
        + controllable （int ）是否可控 1 可控  0 不可控
        + builtIn （int）是否内置（1为内置 0为非内置）
        + fixedAttribute （int）关联空间属性（0 无固定属性，1为环境  2 占位 3 能耗）
        + functionCode （int）0 无功能  1 是次数  2 是电表记录
        + maintainData （date）保养日期
        + brandName （string）品牌名称
        + model （string）型号
        + equipmentBtnGroups
            + id （long） 端口类型id
            + enabled （int）是否启用
            + creator （long）创建人
            + modifier （long）修改人
            + equipmentId （long）设备id
            + groupNameAlias （string）组别称
            + groupName （string） 组名
            + groupType （int）组类型（1 开关组 2 输入组 3 输出组 4 预设组 5编组组）
            + groupAndGroup （string） 编组
            + cmdBtnGroups
                + id （long）命令按钮组id
                + enabled
                + assetBtnGroupId （long）设备按钮组ID
                + driveCmdId （long）命令id
                + cmdName （string）命令名
                + cmdCode （string）命令code
                + cmdAlias (string) 命令别称 
                + forbidden （int）1是禁用  0不禁用
                
    
+ Request (application/json)


+ Response 200

        {
          "data": {
            "id": 1,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2020-10-18 09:18:51",
            "modified": "2020-10-18 09:18:56",
            "cloudEquipmentId": 0,
            "updateVersionId": 0,
            "equipmentName": "中控",
            "anotherName": "中会中控",
            "equipmentNameEn": "zhz",
            "online": 0,
            "runningStatus": 0,
            "serialNumber": "122",
            "purchaseDate": "2020-10-18 09:18:13",
            "maintenanceTelephone": "13126822398",
            "gatewayId": 1,
            "driveId": 3,
            "ispdu": 0,
            "controllable": 1,
            "builtIn": 0,
            "fixedAttribute": 0,
            "functionCode": 0,
            "maintainData": "2020-10-21 18:42:01",
            "brandName": "企鹅",
            "model": "W101",
            "equipmentBtnGroups": [
              {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2020-10-26 15:12:05",
                "modified": "2020-10-26 15:12:07",
                "equipmentId": 1,
                "groupNameAlias": "开关组",
                "groupName": "开关组",
                "groupType": 1,
                "cmdBtnGroups": [
                  {
                    "id": 1,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-10-26 15:16:53",
                    "modified": "2020-10-26 15:16:55",
                    "assetBtnGroupId": 1,
                    "driveCmdId": 1,
                    "cmdName": "开",
                    "cmdCode": "Btn_Jl_Kai",
                    "cmdAlias": "on",
                    "forbidden": 0
                  }
                ]
              },
              {
                "id": 2,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2020-10-26 15:12:41",
                "modified": "2020-10-26 15:12:45",
                "equipmentId": 1,
                "groupNameAlias": "输入组",
                "groupName": "输入组",
                "groupType": 2,
                "cmdBtnGroups": [
                  {
                    "id": 2,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-10-26 15:17:13",
                    "modified": "2020-10-26 15:17:17",
                    "assetBtnGroupId": 2,
                    "driveCmdId": 2,
                    "cmdName": "关",
                    "cmdCode": "Btn_Jl_Guan",
                    "cmdAlias": "off",
                    "forbidden": 1
                  }
                ]
              },
              {
                "id": 3,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2020-10-26 15:14:36",
                "modified": "2020-10-26 15:14:39",
                "equipmentId": 1,
                "groupNameAlias": "输出组",
                "groupName": "输出组",
                "groupType": 3,
                "cmdBtnGroups": [
                  {
                    "id": 3,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-10-26 15:17:35",
                    "modified": "2020-10-26 15:17:42",
                    "assetBtnGroupId": 3,
                    "driveCmdId": 2,
                    "cmdName": "关",
                    "cmdCode": "Btn_Jl_Guan",
                    "cmdAlias": "off",
                    "forbidden": 1
                  },
                  {
                    "id": 4,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-10-26 15:33:16",
                    "modified": "2020-10-26 15:33:23",
                    "assetBtnGroupId": 3,
                    "driveCmdId": 1,
                    "cmdName": "开",
                    "cmdCode": "Btn_Jl_Kai",
                    "cmdAlias": "on",
                    "forbidden": 0
                  }
                ]
              },
              {
                "id": 4,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2020-10-26 15:15:11",
                "modified": "2020-10-26 15:15:13",
                "equipmentId": 1,
                "groupNameAlias": "编组组",
                "groupName": "编组组",
                "groupType": 5,
                "groupAndGroup": "2,3",
                "equipmentBtnGroups": [
                  {
                    "id": 2,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-10-26 15:12:41",
                    "modified": "2020-10-26 15:12:45",
                    "equipmentId": 1,
                    "groupNameAlias": "输入组",
                    "groupName": "输入组",
                    "groupType": 2,
                    "cmdBtnGroups": [
                      {
                        "id": 2,
                        "enabled": 1,
                        "creator": 0,
                        "modifier": 0,
                        "created": "2020-10-26 15:17:13",
                        "modified": "2020-10-26 15:17:17",
                        "assetBtnGroupId": 2,
                        "driveCmdId": 2,
                        "cmdName": "关",
                        "cmdCode": "Btn_Jl_Guan",
                        "cmdAlias": "off",
                        "forbidden": 1
                      }
                    ]
                  },
                  {
                    "id": 3,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-10-26 15:14:36",
                    "modified": "2020-10-26 15:14:39",
                    "equipmentId": 1,
                    "groupNameAlias": "输出组",
                    "groupName": "输出组",
                    "groupType": 3,
                    "cmdBtnGroups": [
                      {
                        "id": 3,
                        "enabled": 1,
                        "creator": 0,
                        "modifier": 0,
                        "created": "2020-10-26 15:17:35",
                        "modified": "2020-10-26 15:17:42",
                        "assetBtnGroupId": 3,
                        "driveCmdId": 2,
                        "cmdName": "关",
                        "cmdCode": "Btn_Jl_Guan",
                        "cmdAlias": "off",
                        "forbidden": 1
                      },
                      {
                        "id": 4,
                        "enabled": 1,
                        "creator": 0,
                        "modifier": 0,
                        "created": "2020-10-26 15:33:16",
                        "modified": "2020-10-26 15:33:23",
                        "assetBtnGroupId": 3,
                        "driveCmdId": 1,
                        "cmdName": "开",
                        "cmdCode": "Btn_Jl_Kai",
                        "cmdAlias": "on",
                        "forbidden": 0
                      }
                    ]
                  }
                ]
              }
            ]
          }
        }


### 远程服务台-设备列表 [GET] /equipment/controlledDevice
+ Description

+ Parameters
    + page[number] （int）页码
    + page[size] （int）条数
    + sort （Array[string]） 排序

+ ReturnData
    + id （long） 端口类型id
    + enabled （int）是否启用
    + creator （long）创建人
    + modifier （long）修改人
    + updateVersionId （long）跟云端同步使用
    + cloudEquipmentId （long）云端id
    + equipmentName （string） 设备名
    + equipmentNameEn （string）自动生成唯一号
    + online （int） 是否在线：0 离线 1在线 2未知
    + runningStatus （int）运行状态 0关闭 1运行 2警告    3故障  4其他
    + serialNumber （string）设备序列号
    + purchaseDate （data）采购日期
    + maintenanceTelephone （string）维修电话
    + gatewayId （long）网关id
    + driveId （long） 驱动id
    + ispdu （int）0 非pdu 1是pdu
    + controllable （int）是否可控 1 可控  0 不可控
    + builtIn （int）是否内置 1为内置 0为非内置
    + fixedAttribute （int）0 无固定属性，1为环境  2 占位 3 能耗
    + functionCode （int）'0 无功能  1 是次数  2 是电表记录'
    + maintainData （data）保养日期
    + brandName （string）品牌名
    + model （string）型号
    + categroyName （string）分类名
        
        
+ Response 200
    
            {
              "data": [
                {
                  "id": 1,
                  "enabled": 1,
                  "creator": 0,
                  "modifier": 0,
                  "created": "2020-10-18 09:18:51",
                  "modified": "2020-10-18 09:18:56",
                  "cloudEquipmentId": 0,
                  "updateVersionId": 0,
                  "equipmentName": "中控",
                  "anotherName": "中会中控",
                  "equipmentNameEn": "zhz",
                  "online": 0,
                  "runningStatus": 0,
                  "serialNumber": "122",
                  "purchaseDate": "2020-10-18 09:18:13",
                  "maintenanceTelephone": "13126822398",
                  "gatewayId": 1,
                  "driveId": 3,
                  "ispdu": 0,
                  "controllable": 1,
                  "builtIn": 0,
                  "fixedAttribute": 0,
                  "functionCode": 0,
                  "maintainData": "2020-10-21 18:42:01",
                  "brandName": "企鹅"
                },
                {
                  "id": 2,
                  "enabled": 1,
                  "creator": 0,
                  "modifier": 0,
                  "created": "2020-10-20 14:06:01",
                  "modified": "2020-10-20 14:06:04",
                  "cloudEquipmentId": 0,
                  "updateVersionId": 0,
                  "equipmentName": "七合一传感器",
                  "anotherName": "中会七合一传感器",
                  "equipmentNameEn": "7he1",
                  "online": 0,
                  "runningStatus": 0,
                  "otherStatus": "{\"tvoc\":0.388,\"co2\":1018.0,\"pm10\":0.057,\"ch2o\":0.109,\"pm25\":32.0,\"temperature\":25.7,\"humidity\":19.3}",
                  "serialNumber": "11",
                  "purchaseDate": "2020-10-20 14:05:49",
                  "maintenanceTelephone": "13126822398",
                  "gatewayId": 1,
                  "driveId": 1,
                  "portTypeId": 1,
                  "portConfigContent": "{\"aa\":\"aa\"}",
                  "ispdu": 0,
                  "controllable": 1,
                  "builtIn": 0,
                  "fixedAttribute": 1,
                  "functionCode": 0,
                  "maintainData": "2020-10-28 18:42:06",
                  "brandName": "extron"
                },
                {
                  "id": 3,
                  "enabled": 1,
                  "creator": 0,
                  "modifier": 0,
                  "created": "2020-10-23 11:30:57",
                  "modified": "2020-10-23 11:30:59",
                  "cloudEquipmentId": 0,
                  "updateVersionId": 0,
                  "equipmentName": "智能电表",
                  "anotherName": "中会智能电表",
                  "equipmentNameEn": "sdf",
                  "online": 0,
                  "runningStatus": 0,
                  "gatewayId": 0,
                  "driveId": 2,
                  "ispdu": 0,
                  "controllable": 1,
                  "builtIn": 0,
                  "fixedAttribute": 0,
                  "functionCode": 0,
                  "maintainData": "2020-10-15 18:42:13",
                  "brandName": "baidu"
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


### 设备命令别称保存以及修改 [PATCH] /equipmentCmdAlias/saveOrUpdate

+ Description
    

+ Parameters
    + data
        + cmdAlias (string) 设备命令别称
        + driveCmdId （int）驱动命令id
        + equipmentId （long） 设备id
        + forbidden （int）是否禁用 1表示禁用 0表示不禁用，默认为0

    
+ Request (application/json)

            {
              "data": [
                {
                  "cmdAlias": "开",
                  "driveCmdId": 1,
                  "equipmentId": 2,
                  "forbidden": 0
                },
                    {
                  "cmdAlias": "关",
                  "driveCmdId": 2,
                  "equipmentId": 2,
                  "forbidden": 0
                }
              ]
            }
            
+ Response 200

### 设备命令别名列表 [GET] /equipmentCmdAlias/asset/{id}
+ Description

+ Parameters


+ ReturnData
    + id （long） 端口类型id
    + enabled （int）是否启用
    + creator （long）创建人
    + modifier （long）修改人
    + equipmentId （long）设备id
    + driveCmdId （long）驱动命令id
    + cmdAlias （string） 设备命令别称
    + forbidden （int）是否禁用 1表示禁用 0表示不禁用，默认为0
    + command （string） 命令名

        
        
+ Response 200
    
        {
          "data": [
            {
              "id": 3,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-11-11 10:39:15",
              "modified": "2020-11-11 10:39:15",
              "equipmentId": 2,
              "driveCmdId": 1,
              "cmdAlias": "开",
              "forbidden": 0,
              "command": "on"
            },
            {
              "id": 4,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-11-11 10:39:19",
              "modified": "2020-11-11 10:39:19",
              "equipmentId": 2,
              "driveCmdId": 2,
              "cmdAlias": "关",
              "forbidden": 0,
              "command": "off"
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


### 读数类型列表 [GET] /readType
+ Description

+ Parameters


+ ReturnData
    + id （long） 读数类型id
    + enabled （int）是否启用
    + creator （long）创建人
    + modifier （long）修改人
    + readtypeNameChinese （string）读数类型中文名
    + readtypeNameEnglish （string）读数类型英文名
    + readValueType （int） 读数值返回的类型(0 字符串类型 1 整数型 2 float型)
    + builtIn （int）是否内置 1为内置 0为非内置
    + readtypeFunction （int） 0 常规属性  1 统计次数  2统计电量   3是否在线  4运行状态

        
        
+ Response 200
    
        {
          "data": [
            {
              "id": 1,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-10-21 18:42:11",
              "modified": "2020-10-21 18:42:14",
              "readtypeNameChinese": "CO2",
              "readtypeNameEnglish": "co2",
              "readValueType": 2,
              "builtIn": 1,
              "readtypeFunction": 0
            },
            {
              "id": 2,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-10-21 18:45:13",
              "modified": "2020-10-21 18:45:16",
              "readtypeNameChinese": "PM2.5",
              "readtypeNameEnglish": "pm25",
              "readValueType": 2,
              "builtIn": 1,
              "readtypeFunction": 0
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

### 一级分类列表 [GET] /category
+ Description

+ Parameters


+ ReturnData
    + id （long） 读数类型id
    + enabled （int）是否启用
    + creator （long）创建人
    + modifier （long）修改人
    + parentId （long）父id
    + categoryName （string）分类名
    + displayOrder （int） 排序

        
        
+ Response 200
    
        {
          "data": [
            {
              "id": 1,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-10-20 14:09:15",
              "modified": "2020-10-20 14:09:13",
              "parentId": 0,
              "categoryName": "传感器",
              "displayOrder": 100
            },
            {
              "id": 3,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-10-27 11:02:40",
              "parentId": 0,
              "categoryName": "灯",
              "displayOrder": 100
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

### 二级分类列表 [GET] /category/secondCategory
+ Description

+ Parameters


+ ReturnData
    + id （long） 读数类型id
    + enabled （int）是否启用
    + creator （long）创建人
    + modifier （long）修改人
    + parentId （long）父id
    + categoryName （string）分类名
    + displayOrder （int） 排序

        
        
+ Response 200
    
        {
          "data": [
            {
              "id": 2,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-10-20 14:09:44",
              "modified": "2020-10-20 14:09:41",
              "parentId": 1,
              "categoryName": "环境传感器",
              "displayOrder": 100
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


### 按钮组详情 [GET] /equipmentBtnGroup/DeviceButtonDetails

+ Description
    

+ Parameters
    + data
        + id (long) 组ID
        + equipmentId （long）设备ID
        + groupNameAlias （string）组别称
        + groupName （string）组名
        + groupType （int） 1 开关组 2 输入组 3 输出组 4 预设组 5编组组
        + groupAndGroup （string）编组 用逗号隔开
        + cmdBtnGroups
            + id （long）命令按钮组ID
            + assetBtnGroupId （long）设备按钮组ID
            + driveCmdId （long）驱动命令ID
            + cmdName （string）命令名
            + cmdCode （string） 命令core

    
+ Request (application/json)

        {
          "data": [
            {
              "id": 1,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-10-26 15:12:05",
              "modified": "2020-10-26 15:12:07",
              "equipmentId": 1,
              "groupNameAlias": "开关组",
              "groupName": "开关组",
              "groupType": 1,
              "cmdBtnGroups": [
                {
                  "id": 1,
                  "enabled": 1,
                  "creator": 0,
                  "modifier": 0,
                  "created": "2020-10-26 15:16:53",
                  "modified": "2020-10-26 15:16:55",
                  "assetBtnGroupId": 1,
                  "driveCmdId": 1,
                  "cmdName": "on",
                  "cmdCode": "Btn_Jl_Kai"
                }
              ]
            },
            {
              "id": 2,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-10-26 15:12:41",
              "modified": "2020-10-26 15:12:45",
              "equipmentId": 1,
              "groupNameAlias": "输入组",
              "groupName": "输入组",
              "groupType": 2,
              "cmdBtnGroups": [
                {
                  "id": 2,
                  "enabled": 1,
                  "creator": 0,
                  "modifier": 0,
                  "created": "2020-10-26 15:17:13",
                  "modified": "2020-10-26 15:17:17",
                  "assetBtnGroupId": 2,
                  "driveCmdId": 2,
                  "cmdName": "off",
                  "cmdCode": "Btn_Jl_Guan"
                }
              ]
            },
            {
              "id": 3,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-10-26 15:14:36",
              "modified": "2020-10-26 15:14:39",
              "equipmentId": 1,
              "groupNameAlias": "输出组",
              "groupName": "输出组",
              "groupType": 3,
              "cmdBtnGroups": [
                {
                  "id": 3,
                  "enabled": 1,
                  "creator": 0,
                  "modifier": 0,
                  "created": "2020-10-26 15:17:35",
                  "modified": "2020-10-26 15:17:42",
                  "assetBtnGroupId": 3,
                  "driveCmdId": 2,
                  "cmdName": "off",
                  "cmdCode": "Btn_Jl_Guan"
                },
                {
                  "id": 4,
                  "enabled": 1,
                  "creator": 0,
                  "modifier": 0,
                  "created": "2020-10-26 15:33:16",
                  "modified": "2020-10-26 15:33:23",
                  "assetBtnGroupId": 3,
                  "driveCmdId": 1,
                  "cmdName": "on",
                  "cmdCode": "Btn_Jl_Kai"
                }
              ]
            },
            {
              "id": 4,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-10-26 15:15:11",
              "modified": "2020-10-26 15:15:13",
              "equipmentId": 1,
              "groupNameAlias": "编组组",
              "groupName": "编组组",
              "groupType": 5,
              "groupAndGroup": "2,3",
              "equipmentBtnGroups": [
                {
                  "id": 2,
                  "enabled": 1,
                  "creator": 0,
                  "modifier": 0,
                  "created": "2020-10-26 15:12:41",
                  "modified": "2020-10-26 15:12:45",
                  "equipmentId": 1,
                  "groupNameAlias": "输入组",
                  "groupName": "输入组",
                  "groupType": 2
                },
                {
                  "id": 3,
                  "enabled": 1,
                  "creator": 0,
                  "modifier": 0,
                  "created": "2020-10-26 15:14:36",
                  "modified": "2020-10-26 15:14:39",
                  "equipmentId": 1,
                  "groupNameAlias": "输出组",
                  "groupName": "输出组",
                  "groupType": 3
                }
              ]
            }
          ]
        }
            
+ Response 200


### 组和按钮添加、修改 [POST] /equipmentBtnGroup/DisplayGroup

+ Description
    

+ Parameters
    + data
        + id (long) 组id （修改传id）
        + equipmentId （long） 设备id
        + groupName （string） 组名
        + groupNameAlias （string）组别名
        + groupType （int）1 开关组 2 输入组 3 输出组 4 预设组 5编组组
        + cmdBtnGroups
            + id （long）命令按钮组ID （修改传id）
            + driveCmdId  （long）驱动命令id
    
+ Request (application/json)

        {
          "data": [
            {
              "cmdBtnGroups": [
                {
                  "driveCmdId": 1
                },{
                 "driveCmdId": 2
                }
              ],
              "equipmentId": 1,
              "groupName": "开关组",
              "groupNameAlias": "灯光开关组",
              "groupType": 1
            }
          ]
        }
+ Response 200

### 设备按钮组添加/修改 [POST] /equipmentBtnGroup

+ Description
    

+ Parameters
    + data
        + id (long) 组id （修改传id）
        + equipmentId （long） 设备id
        + groupName （string） 组名
        + groupNameAlias （string）组别名
        + groupType （int）1 开关组 2 输入组 3 输出组 4 预设组 5编组组
        + groupAndGroup （string）这个是编组，不同的编组默认使用逗号隔开

    
+ Request (application/json)

        {
          "data": [
            {
              "equipmentId": 2,
              "groupAndGroup": "1,5",
              "groupName": "编组组",
              "groupNameAlias": "灯光编组组",
              "groupType": 5
            }
          ]
        }
+ Response 200

### 设备按钮组删除 [DELETE] /equipmentBtnGroup/delete
+ Parameters
    + assetId(long) 资产id (必填) 
    + id (long) 资产按钮组id (必填)

如：http://192.168.2.10:8989/equipmentBtnGroup/delete?eqId=1&id=1


+ ReturnData
 

+ Request (application/json)
               
+ Response 204

+ Response 400

        {
          "errors": [
            {
              "status": "400",
              "title": "Bad Request",
              "detail": "资产按钮组已经关联了编组组,请先删除"
            }
          ]
        }


### 品牌列表 [GET] /brand
+ Description
    + Author Liukai

+ ReturnData

    + data
        + id (long) 品牌id
        + brandName （string） 品牌名称
        + logo （string）logo
        + description （string）描述
        + website （string）网站
        + displayOrder （int）排序

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
                "self": "/brand?page[number]=1&page[size]=10",
                "first": "/brand?page[number]=1&page[size]=10",
                "last": "/brand?page[number]=1&page[size]=10"
              },
              "data": [
                {
                  "id": 1,
                  "enabled": 1,
                  "creator": 0,
                  "modifier": 0,
                  "brandName": "extron",
                  "website": "www。",
                  "displayOrder": 100
                },
                {
                  "id": 2,
                  "enabled": 1,
                  "creator": 0,
                  "modifier": 0,
                  "brandName": "baidu",
                  "website": "www.baidu.com",
                  "displayOrder": 100
                },
                {
                  "id": 3,
                  "enabled": 1,
                  "creator": 0,
                  "modifier": 0,
                  "brandName": "企鹅",
                  "website": "www.qie",
                  "displayOrder": 100
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
