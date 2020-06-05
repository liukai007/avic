# AVIC管理端接口文档

+ 2020年3月25日
    + 新增设备
    + 删除设备
    + 修改设备
    + 查询设备详情
    + 查询设备列表
+ 2020年3月26日
    + 新增设备资产
    + 删除设备资产
    + 修改设备资产
    + 查询设备资产详情
    + 查询设备资产列表
+ 2020年3月26日
    + 新增分类
    + 删除分类
    + 修改分类
    + 查询分类详情
    + 查询分类列表

## 设备管理
+ Data
    + equipmentName (String) 设备名
    + model (String)  设备型号
    + picture (String) 图片链接
    + categoryId (Long) 分类ID
    + brandId (Long) 品牌ID
    + controllable (int) 是否可控(1为可控 0为不可控)
    + readable (int)  是否可读 0不可读 1可读
    + communicationMode (int) 通信方式，0：单向，1：双向
    + lifeType (int) 寿命类型，0：时长，1：次数
    + recommendedLife (int) 建议寿命
    + warrantyPeriod (int) 质保期限
    + maintenanceFrequency (int) 保养频率，单位：月
    + webLink (String) 产品链接
    + centerControlUnit (int)  是否是中控  0非中控 1是中控
    + enabled (int)  - 使能  0禁止 1启用
    + creator (long) - 创建人
    + modifier (long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间
    + equipmentCommandList -设备命令列表
        + ID (long) 设备命令表ID 
        + equipmentId (long) 设备ID
        + commandId (long) 分类命令ID
        + commandFormat  (String) 命令格式
        + feedbackFormat (String) 反馈格式
        + enabled (int)  - 使能  0禁止 1启用
        + creator (long) - 创建人
        + modifier (long) - 修改人
        + created (date) - 创建时间
        + modified (date) - 修改时间
    + equipmentReadtypeList -设备读数类型关联表
        + ID (long) 设备命令表ID 
        + enabled (int)  - 使能  0禁止 1启用
        + creator (long) - 创建人
        + modifier (long) - 修改人
        + created (date) - 创建时间
        + modified (date) - 修改时间
        + equipmentId (long) 设备ID
        + readTypeId (long) 读数类型ID

   
### 新增设备 [POST] /equipment

+ Description

+ Request (application/json)

        {
          "data": {
            "brandId": 1,
            "categoryId": 1,
            "centerControlUnit": 0,
            "communicationMode": 0,
            "controllable": 0,
            "equipmentCommandList": [
              {
                "commandFormat": "commandFormat1",
                "commandId": 1,
                "feedbackFormat": "feedbackFormat1"
              }
            ],
             "equipmentReadtypeList": [
              {
                "readTypeId": 1
              }
            ]
            "equipmentName": "string1111",
            "lifeType": 0,
            "maintenanceFrequency": 0,
            "model": "string111",
            "modifier": 0,
            "picture": "string111",
            "readable": 0,
            "recommendedLife": 0,
            "warrantyPeriod": 0,
            "webLink": "string"
          }
        }
+ Response 200

+ Response 400

        
### 删除设备 [DEL] /equipment/{id}
+ Description

+ Response 200  

        
### 修改设备 [PATCH] /equipment/{id}

+ Description


+ Request (application/json)
    
        {
          "data": {
            "brandId": 1,
            "categoryId": 1,
            "centerControlUnit": 0,
            "communicationMode": 0,
            "controllable": 0,
            "equipmentCommandList": [
              {
                "id":1,
                "commandFormat": "commandFormat1",
                "commandId": 1,
                "equipmentId": 1,
                "feedbackFormat": "feedbackFormat1"
              }
            ],
            "equipmentReadtypeList": [
                          {
                            "id": 1,
                            "enabled": 1,
                            "creator": 0,
                            "modifier": 0,
                            "created": "2020-04-26 18:04:46",
                            "modified": "2020-04-26 18:04:48",
                            "equipmentId": 1,
                            "readTypeId": 1
                          }
                        ]，
            "equipmentName": "string1111",
            "lifeType": 0,
            "maintenanceFrequency": 0,
            "model": "string111",
            "modifier": 0,
            "picture": "string111",
            "readable": 0,
            "recommendedLife": 0,
            "warrantyPeriod": 0,
            "webLink": "string"
          }
        }
+ Response 200
+ Response 400

### 查询设备详情 [GET] /equipment/{id}
+ Description

+ Response 200
    
        {
          "data": {
            "id": 1,
            "enabled": 1,
            "creator": 0,
            "modifier": 43,
            "created": "2020-04-15 13:57:12",
            "modified": "2020-04-22 18:20:47",
            "equipmentName": "吊顶大音响",
            "model": "CS-1",
            "picture": "/api/static/image/1587382574498.jpg",
            "categoryId": 12,
            "brandId": 1,
            "controllable": 1,
            "readable": 1,
            "communicationMode": 1,
            "lifeType": 0,
            "recommendedLife": 1752000,
            "warrantyPeriod": 6,
            "maintenanceFrequency": 3,
            "webLink": "www.extron",
            "centerControlUnit": 1,
            "brandName": "Extron",
            "primaryCategoryId": 1,
            "primaryCategoryName": "音频",
            "categoryName": "01音箱",
            "equipmentCommandList": [
              {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2020-04-22 18:20:47",
                "modified": "2020-04-22 18:20:47",
                "equipmentId": 1,
                "commandId": 1,
                "commandFormat": "3E"
              },
              {
                "id": 2,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2020-04-22 18:20:47",
                "modified": "2020-04-22 18:20:47",
                "equipmentId": 1,
                "commandId": 2
              },
              {
                "id": 3,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2020-04-22 18:20:47",
                "modified": "2020-04-22 18:20:47",
                "equipmentId": 1,
                "commandId": 3
              },
              {
                "id": 19,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2020-04-22 18:20:47",
                "modified": "2020-04-22 18:20:47",
                "equipmentId": 1,
                "commandId": 9
              }
            ],
            "equipmentReadtypeList": [
              {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2020-04-26 18:04:46",
                "modified": "2020-04-26 18:04:48",
                "equipmentId": 1,
                "readTypeId": 1
              },
              {
                "id": 2,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2020-04-26 18:04:56",
                "modified": "2020-04-26 18:04:59",
                "equipmentId": 1,
                "readTypeId": 2
              }
            ]
          }
        }

### 查询设备列表 [GET] /equipment
+ Description

+ Parameters
    + page[number] (int)  页码  -非必填
    + page[size]  (int)   页尺  -非必填
    + filter[brandId] (long) 品牌ID
    + filter[primaryCategoryid] (long) 一级分类ID
    + filter[categoryId] (long) 二级分类ID
    + filter[communicationId] (int) 通信方式ID
    + filter[equipmentName] (string)  设备名字
    + filter[equipmentModel] (string) 设备型号 
    
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
        "self": "/equipment?page[number]=1&page[size]=10",
        "first": "/equipment?page[number]=1&page[size]=10",
        "last": "/equipment?page[number]=1&page[size]=10"
      },
          "data": [
            {
              "id": 1,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-03-23 16:43:27",
              "modified": "2020-03-23 16:43:30",
              "equipmentName": "灯",
              "model": "001",
              "picture": "http://static.budee.com/cms/upload/image/20200322/1584862487761035082.png",
              "categoryId": 2,
              "brandId": 1,
              "controllable": 0,
              "readable": 0,
              "communicationMode": 0,
              "lifeType": 0,
              "centerControlUnit": 0,
              "brandName": "brand1",
              "primaryCategoryId": 1,
              "primaryCategoryName": "中控",
              "categoryName": "中控分类1",
              "equipmentCommandList": []
            },
            {
              "id": 2,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-03-23 16:43:59",
              "modified": "2020-03-23 16:44:01",
              "equipmentName": "extron中控",
              "model": "112",
              "picture": "http://static.budee.com/cms/upload/image/20200322/1584862487761035082.png",
              "categoryId": 2,
              "brandId": 2,
              "controllable": 0,
              "readable": 0,
              "communicationMode": 0,
              "lifeType": 0,
              "centerControlUnit": 0,
              "brandName": "brand2",
              "primaryCategoryId": 1,
              "primaryCategoryName": "中控",
              "categoryName": "中控分类1",
              "equipmentCommandList": []
            },
            {
              "id": 3,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-03-25 18:41:07",
              "modified": "2020-03-25 18:57:56",
              "equipmentName": "string1111",
              "model": "string111",
              "picture": "string111",
              "categoryId": 1,
              "brandId": 1,
              "controllable": 0,
              "readable": 0,
              "communicationMode": 0,
              "lifeType": 0,
              "recommendedLife": 0,
              "warrantyPeriod": 0,
              "maintenanceFrequency": 0,
              "webLink": "string",
              "centerControlUnit": 0,
              "brandName": "brand1",
              "primaryCategoryId": 0,
              "categoryName": "中控",
              "equipmentCommandList": [
                {
                  "id": 1,
                  "enabled": 0,
                  "creator": 0,
                  "modifier": 0,
                  "created": "2020-03-25 18:57:56",
                  "modified": "2020-03-25 18:57:56",
                  "equipmentId": 3,
                  "commandId": 1,
                  "commandFormat": "commandFormat1",
                  "feedbackFormat": "feedbackFormat1"
                }
              ]
            }
          ]
        }


## 设备资产管理
+ Data
    + equipmentAssetName (String) 设备资产名
    + online (int) 是否在线：0 离线 1在线 2未知
    + runningStatus (int) 运行状态：0关闭 1运行 2警告    3故障  4其他
    + picture  (String) 图片链接
    + controlProtocolId  (Long) 控制协议ID
    + centerControlAssetId (Long) 所属中控的ID，如果没有所属中控，默认是0
    + gatewayAddr (String) IP/网关地址
    + centerControlIp (String) 中控IP
    + centerControlPort (int) 中控端口
    + serialNumber (String) 序列号
    + purchaseDate (date) 采购日期
    + serviceDate (date) 投入使用日期
    + supplier  (String) 供应商
    + maintenanceTelephone (String) 维修电话
    + collaborationSpaceId (Long) 协作空间ID 
    + usedLife (float) 已使用寿命 
    + failureNumber (int) 故障次数
    + enabled (int)  - 使能  0禁止 1启用
    + creator (long) - 创建人
    + modifier (long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间 
    + controlProtocolName (String) 控制协议名
    + equipment (Equipment) - 设备
        + equipmentName (String) 设备名
        + model (String)  设备型号
        + picture (String) 图片链接
        + categoryId (Long) 分类ID
        + brandId (Long) 品牌ID
        + controllable (int) 是否可控(1为可控 0为不可控)
        + readable (int)  是否可读 0不可读 1可读
        + communicationMode (int) 通信方式，0：单向，1：双向
        + lifeType (int) 寿命类型，0：时长，1：次数
        + recommendedLife (int) 建议寿命
        + warrantyPeriod (int) 质保期限
        + maintenanceFrequency (int) 保养频率，单位：月
        + webLink (String) 产品链接
        + centerControlUnit (int)  是否是中控  0非中控 1是中控
        + enabled (int)  - 使能  0禁止 1启用
        + creator (long) - 创建人
        + modifier (long) - 修改人
        + created (date) - 创建时间
        + modified (date) - 修改时间
        + equipmentCommandList -设备命令列表

   
### 新增设备资产 [POST] /equipmentasset

+ Description

+ Request (application/json)

        {
          "data": {
            "equipmentAssetName": "北筒灯",
            "equipmentId": 1,
            "online": 1,
            "runningStatus": 1,
            "picture": "http://static.budee.com/cms/upload/image/20200322/",
            "controlProtocolId": 1,
            "centerControlAssetId": 0,
            "gatewayAddr": "com2",
            "serialNumber": "007",
            "purchaseDate": "2020-03-23T08:42:09.000+0000",
            "serviceDate": "2020-03-23T08:42:07.000+0000",
            "supplier": "太平宝迪",
            "maintenanceTelephone": "13126822398",
            "collaborationSpaceId": 1,
            "usedLife": 1
        }
        }
        
+ Response 201

    {
      "data": {
        "id": 3,
        "type": "equipmentasset"
      }
    }

+ Response 400

        
### 删除设备资产 [DEL] /equipmentasset/{id}
+ Description

+ Response 200  

        
### 修改设备资产 [PATCH] /equipmentasset/{id}

+ Description


+ Request (application/json)

        {
          "data": {
            "id": 3,
            "equipmentAssetName": "北筒灯111",
            "equipmentId": 1,
            "online": 1,
            "runningStatus": 1,
            "picture": "http://static.budee.com/cms/upload/image/20200322/",
            "controlProtocolId": 1,
            "centerControlAssetId": 0,
            "gatewayAddr": "com2",
            "serialNumber": "007",
            "purchaseDate": "2020-03-23T08:42:09.000+0000",
            "serviceDate": "2020-03-23T08:42:07.000+0000",
            "supplier": "太平宝迪",
            "maintenanceTelephone": "13126822398",
            "collaborationSpaceId": 1,
            "usedLife": 1
          }
        }
    
        
+ Response 200
+ Response 400

### 查询设备资产详情 [GET] /equipmentasset/{id}
+ Description

+ Response 200
    
        {
          "data": {
            "id": 1,
            "enabled": 1,
            "creator": 0,
            "modifier": 55,
            "created": "2020-04-15 13:59:16",
            "modified": "2020-06-05 09:55:01",
            "equipmentAssetName": "中会中控设备",
            "equipmentId": 1,
            "online": 1,
            "runningStatus": 1,
            "picture": "",
            "controlProtocolId": 5,
            "centerControlAssetId": 0,
            "gatewayAddr": "192.168.1.30",
            "otherStatus": "",
            "centerControlIp": "192.168.1.30",
            "centerControlPort": 8889,
            "serialNumber": "1-001-0982",
            "purchaseDate": "2020-04-08 13:58:52",
            "serviceDate": "2019-06-01 13:58:56",
            "supplier": "北京太平宝迪科技发展有限公司",
            "maintenanceTelephone": "13126855981",
            "collaborationSpaceId": 1,
            "usedLife": 1,
            "failureNumber": 0,
            "readed": 1,
            "maintenanceDate": "2020-05-31T16:00:00.000+0000",
            "equipment": {
              "id": 1,
              "enabled": 1,
              "creator": 0,
              "modifier": 43,
              "created": "2020-04-15 13:57:12",
              "modified": "2020-05-22 18:25:42",
              "equipmentName": "IPCP Pro550(勿删)",
              "model": "550",
              "picture": "/api/static/image/1589872662993.jpg",
              "categoryId": 20,
              "brandId": 1,
              "controllable": 1,
              "readable": 1,
              "communicationMode": 1,
              "lifeType": 0,
              "recommendedLife": 3000,
              "warrantyPeriod": 10,
              "maintenanceFrequency": 1,
              "webLink": "string",
              "centerControlUnit": 1,
              "brandName": "Extron(勿删)",
              "primaryCategoryId": 3,
              "primaryCategoryName": "控制",
              "categoryName": "中控(勿删)",
              "equipmentCommandList": [
                {
                  "id": 1,
                  "enabled": 1,
                  "creator": 0,
                  "modifier": 0,
                  "created": "2020-05-22 18:25:42",
                  "modified": "2020-05-22 18:25:42",
                  "equipmentId": 1,
                  "commandId": 1,
                  "commandFormat": "commandFormat1",
                  "feedbackFormat": "feedbackFormat1",
                  "cmdName": "on"
                }
                  ],
                  "equipmentReadtypeList": [
                    {
                      "id": 1,
                      "enabled": 1,
                      "creator": 0,
                      "modifier": 0,
                      "created": "2020-04-27 19:04:50",
                      "modified": "2020-04-27 19:04:50",
                      "equipmentId": 1,
                      "readTypeId": 1,
                      "readTypeName": "CO2"
                    }
                  ]
                },
                "collaborationSpaceName": "中会(勿删)",
                "organizationName": "北京太平宝迪-真实数据(勿删)",
                "organizationId": 1,
                "buildingName": "北京云谷电子商务产业园2号楼",
                "buildingId": 1,
                "floorId": 9,
                "floorNum": 6,
                "controlProtocolName": "继电器协议"
              }
            }

### 查询设备资产列表 [GET] /equipmentasset
+ Description

+ Parameters
    + page[number] (int)  页码  -非必填
    + page[size]  (int)   页尺  -非必填
    + filter[brandid] (long)  品牌ID
    + filter[buildingid] (long)  楼宇ID
    + filter[collaborationSpaceid] (long) 
    + filter[equipmentModel] (string) 设备型号 
    + filter[equipmentName] (string)  设备名字
    + filter[floorid] (long)  楼层ID
    + filter[online] (int)  是否在线：0 离线 1在线 2未知
    + filter[organizationid] (long)  机构ID
    + filter[primaryCategoryid] (long)  一级分类
    + filter[secondCategoryid]  (long)  二级分类
    + filter[runningStatus] 运行状态：0关闭 1运行 2警告    3故障  4其他
    
    
+ Response 200

            {
              "meta": {
                "totalPages": 2,
                "totalElements": 17,
                "size": 10,
                "number": 1,
                "numberOfElements": 10,
                "first": true,
                "last": false,
                "sort": null
              },
          "links": {
            "self": "/equipmentasset?page[number]=1&page[size]=10",
            "first": "/equipmentasset?page[number]=1&page[size]=10",
            "next": "/equipmentasset?page[number]=2&page[size]=10",
            "last": "/equipmentasset?page[number]=2&page[size]=10"
          },
          "data": [
            {
              "id": 1,
              "enabled": 1,
              "creator": 0,
              "modifier": 55,
              "created": "2020-04-15 13:59:16",
              "modified": "2020-06-05 09:55:01",
              "equipmentAssetName": "中会中控设备",
              "equipmentId": 1,
              "online": 1,
              "runningStatus": 1,
              "picture": "",
              "controlProtocolId": 5,
              "centerControlAssetId": 0,
              "gatewayAddr": "192.168.1.30",
              "otherStatus": "",
              "centerControlIp": "192.168.1.30",
              "centerControlPort": 8889,
              "serialNumber": "1-001-0982",
              "purchaseDate": "2020-04-08 13:58:52",
              "serviceDate": "2019-06-01 13:58:56",
              "supplier": "北京太平宝迪科技发展有限公司",
              "maintenanceTelephone": "13126855981",
              "collaborationSpaceId": 1,
              "usedLife": 1,
              "failureNumber": 0,
              "readed": 1,
              "maintenanceDate": "2020-05-31T16:00:00.000+0000",
              "equipment": {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 43,
                "created": "2020-04-15 13:57:12",
                "modified": "2020-05-22 18:25:42",
                "equipmentName": "IPCP Pro550(勿删)",
                "model": "550",
                "picture": "/api/static/image/1589872662993.jpg",
                "categoryId": 20,
                "brandId": 1,
                "controllable": 1,
                "readable": 1,
                "communicationMode": 1,
                "lifeType": 0,
                "recommendedLife": 3000,
                "warrantyPeriod": 10,
                "maintenanceFrequency": 1,
                "webLink": "string",
                "centerControlUnit": 1,
                "brandName": "Extron(勿删)",
                "primaryCategoryId": 3,
                "primaryCategoryName": "控制",
                "categoryName": "中控(勿删)",
                "equipmentCommandList": [
                  {
                    "id": 1,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-22 18:25:42",
                    "modified": "2020-05-22 18:25:42",
                    "equipmentId": 1,
                    "commandId": 1,
                    "commandFormat": "commandFormat1",
                    "feedbackFormat": "feedbackFormat1",
                    "cmdName": "on"
                  }
                ],
                "equipmentReadtypeList": [
                  {
                    "id": 1,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-04-27 19:04:50",
                    "modified": "2020-04-27 19:04:50",
                    "equipmentId": 1,
                    "readTypeId": 1,
                    "readTypeName": "CO2"
                  }
                ]
              },
              "collaborationSpaceName": "中会(勿删)",
              "organizationName": "北京太平宝迪-真实数据(勿删)",
              "organizationId": 1,
              "buildingName": "北京云谷电子商务产业园2号楼",
              "buildingId": 1,
              "floorId": 9,
              "floorNum": 6,
              "controlProtocolName": "继电器协议",
              "categoryCommandList": [
                {
                  "commandCode": "Btn_Jl_Kai",
                  "description": "开"
                }
              ]
            },
            {
              "id": 2,
              "enabled": 1,
              "creator": 43,
              "modifier": 55,
              "created": "2020-04-17 18:30:02",
              "modified": "2020-06-04 18:24:03",
              "equipmentAssetName": "北筒灯（勿删)",
              "equipmentId": 23,
              "online": 1,
              "runningStatus": 1,
              "controlProtocolId": 5,
              "centerControlAssetId": 1,
              "gatewayAddr": "r1",
              "otherStatus": "",
              "serialNumber": "15822222-55",
              "purchaseDate": "2020-04-17 18:29:13",
              "serviceDate": "2018-09-01 18:29:17",
              "supplier": "宝迪",
              "maintenanceTelephone": "13126822398",
              "collaborationSpaceId": 1,
              "failureNumber": 0,
              "readed": 1,
              "maintenanceDate": "2020-05-31T16:00:00.000+0000",
              "equipment": {
                "id": 23,
                "enabled": 1,
                "creator": 55,
                "modifier": 55,
                "created": "2020-05-19 16:27:29",
                "modified": "2020-05-20 09:28:22",
                "equipmentName": "灯（勿删）",
                "model": "无",
                "picture": "/api/static/image/1589876775535.jpg",
                "categoryId": 45,
                "brandId": 26,
                "controllable": 1,
                "readable": 1,
                "communicationMode": 1,
                "lifeType": 0,
                "recommendedLife": 5000,
                "warrantyPeriod": 1,
                "maintenanceFrequency": 1,
                "webLink": "www.budee.com",
                "centerControlUnit": 0,
                "brandName": "其他(勿删)",
                "primaryCategoryId": 4,
                "primaryCategoryName": "环境电器",
                "categoryName": "灯光(勿删)",
                "equipmentCommandList": [
                  {
                    "id": 73,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-20 09:28:22",
                    "modified": "2020-05-20 09:28:22",
                    "equipmentId": 23,
                    "commandId": 1,
                    "commandFormat": "on",
                    "cmdName": "on"
                  },
                  {
                    "id": 74,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-20 09:28:22",
                    "modified": "2020-05-20 09:28:22",
                    "equipmentId": 23,
                    "commandId": 2,
                    "commandFormat": "off",
                    "cmdName": "off"
                  }
                ],
                "equipmentReadtypeList": [
                  {
                    "id": 86,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-20 09:28:22",
                    "modified": "2020-05-20 09:28:22",
                    "equipmentId": 23,
                    "readTypeId": 9,
                    "readTypeName": "运行状态"
                  },
                  {
                    "id": 85,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-20 09:28:22",
                    "modified": "2020-05-20 09:28:22",
                    "equipmentId": 23,
                    "readTypeId": 10,
                    "readTypeName": "是否在线"
                  }
                ]
              },
              "collaborationSpaceName": "中会(勿删)",
              "organizationName": "北京太平宝迪-真实数据(勿删)",
              "organizationId": 1,
              "buildingName": "北京云谷电子商务产业园2号楼",
              "buildingId": 1,
              "floorId": 9,
              "floorNum": 6,
              "controlProtocolName": "继电器协议",
              "categoryCommandList": [
                {
                  "commandCode": "Btn_Jl_Kai",
                  "description": "开"
                },
                {
                  "commandCode": "Btn_Jl_Guan",
                  "description": "关"
                }
              ]
            },
            {
              "id": 3,
              "enabled": 1,
              "creator": 43,
              "modifier": 55,
              "created": "2020-04-20 19:02:06",
              "modified": "2020-05-20 09:07:49",
              "equipmentAssetName": "黑色摄像头",
              "equipmentId": 3,
              "online": 2,
              "runningStatus": 4,
              "controlProtocolId": 1,
              "centerControlAssetId": 1,
              "gatewayAddr": "458",
              "serialNumber": "158288222-55",
              "purchaseDate": "2020-04-20 19:01:41",
              "serviceDate": "2020-04-15 19:01:44",
              "supplier": "宝迪",
              "maintenanceTelephone": "15062325154",
              "collaborationSpaceId": 1,
              "failureNumber": 0,
              "readed": 1,
              "maintenanceDate": "2020-05-14T16:00:00.000+0000",
              "equipment": {
                "id": 3,
                "enabled": 1,
                "creator": 43,
                "modifier": 50,
                "created": "2020-04-20 19:00:46",
                "modified": "2020-05-19 13:49:21",
                "equipmentName": "Sony-SRG-301SE(勿删)",
                "model": "301SE",
                "picture": "/api/static/image/1587380399163.jpg",
                "categoryId": 42,
                "brandId": 2,
                "controllable": 1,
                "readable": 1,
                "communicationMode": 1,
                "lifeType": 0,
                "recommendedLife": 1,
                "warrantyPeriod": 5,
                "maintenanceFrequency": 1,
                "webLink": "www.budee.com",
                "centerControlUnit": 0,
                "brandName": "Sony(勿删)",
                "primaryCategoryId": 2,
                "primaryCategoryName": "视频",
                "categoryName": "摄像头(勿删)",
                "equipmentCommandList": [
                  {
                    "id": 61,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-19 13:49:21",
                    "modified": "2020-05-19 13:49:21",
                    "equipmentId": 3,
                    "commandId": 47,
                    "commandFormat": "up",
                    "cmdName": "云台上"
                  },
                  {
                    "id": 62,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-19 13:49:21",
                    "modified": "2020-05-19 13:49:21",
                    "equipmentId": 3,
                    "commandId": 48,
                    "commandFormat": "down",
                    "cmdName": "云台下"
                  },
                  {
                    "id": 63,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-19 13:49:21",
                    "modified": "2020-05-19 13:49:21",
                    "equipmentId": 3,
                    "commandId": 49,
                    "commandFormat": "left",
                    "cmdName": "云台左"
                  },
                  {
                    "id": 64,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-19 13:49:21",
                    "modified": "2020-05-19 13:49:21",
                    "equipmentId": 3,
                    "commandId": 50,
                    "commandFormat": "right",
                    "cmdName": "云台右"
                  },
                  {
                    "id": 65,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-19 13:49:21",
                    "modified": "2020-05-19 13:49:21",
                    "equipmentId": 3,
                    "commandId": 51,
                    "commandFormat": "preset1",
                    "cmdName": "云台复位"
                  },
                  {
                    "id": 66,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-19 13:49:21",
                    "modified": "2020-05-19 13:49:21",
                    "equipmentId": 3,
                    "commandId": 52,
                    "commandFormat": "zoom+",
                    "cmdName": "画面放大"
                  },
                  {
                    "id": 67,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-19 13:49:21",
                    "modified": "2020-05-19 13:49:21",
                    "equipmentId": 3,
                    "commandId": 53,
                    "commandFormat": "zoom-",
                    "cmdName": "画面缩小"
                  },
                  {
                    "id": 68,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-19 13:49:21",
                    "modified": "2020-05-19 13:49:21",
                    "equipmentId": 3,
                    "commandId": 54,
                    "commandFormat": "preset1",
                    "cmdName": "预置位1"
                  },
                  {
                    "id": 69,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-19 13:49:21",
                    "modified": "2020-05-19 13:49:21",
                    "equipmentId": 3,
                    "commandId": 55,
                    "commandFormat": "preset2",
                    "cmdName": "预置位2"
                  },
                  {
                    "id": 70,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-19 13:49:21",
                    "modified": "2020-05-19 13:49:21",
                    "equipmentId": 3,
                    "commandId": 56,
                    "commandFormat": "preset3",
                    "cmdName": "预置位3"
                  }
                ],
                "equipmentReadtypeList": [
                  {
                    "id": 59,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-19 13:49:21",
                    "modified": "2020-05-19 13:49:21",
                    "equipmentId": 3,
                    "readTypeId": 9,
                    "readTypeName": "运行状态"
                  },
                  {
                    "id": 58,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-19 13:49:21",
                    "modified": "2020-05-19 13:49:21",
                    "equipmentId": 3,
                    "readTypeId": 10,
                    "readTypeName": "是否在线"
                  }
                ]
              },
              "collaborationSpaceName": "中会(勿删)",
              "organizationName": "北京太平宝迪-真实数据(勿删)",
              "organizationId": 1,
              "buildingName": "北京云谷电子商务产业园2号楼",
              "buildingId": 1,
              "floorId": 9,
              "floorNum": 6,
              "controlProtocolName": "网络协议",
              "categoryCommandList": [
                {
                  "commandCode": "Btn_SheXiangTou_Shang",
                  "description": "云台上"
                },
                {
                  "commandCode": "Btn_SheXiangTou_Xia",
                  "description": "云台下"
                },
                {
                  "commandCode": "Btn_SheXiangTou_Zuo",
                  "description": "云台左"
                },
                {
                  "commandCode": "Btn_SheXiangTou_You",
                  "description": "云台右"
                },
                {
                  "commandCode": "Btn_SheXiangTou_FuWei",
                  "description": "云台复位"
                },
                {
                  "commandCode": "Btn_SheXiangTou_FangDa",
                  "description": "画面放大"
                },
                {
                  "commandCode": "Btn_SheXiangTou_SuoXiao",
                  "description": "画面缩小"
                },
                {
                  "commandCode": "Btn_SheXiangTou_YuZhiW1",
                  "description": "预置位1"
                },
                {
                  "commandCode": "Btn_SheXiangTou_YuZhiW2",
                  "description": "预置位2"
                },
                {
                  "commandCode": "Btn_SheXiangTou_YuZhiW3",
                  "description": "预置位3"
                }
              ]
            },
            {
              "id": 4,
              "enabled": 1,
              "creator": 43,
              "modifier": 45,
              "created": "2020-04-21 14:12:33",
              "modified": "2020-06-04 20:46:51",
              "equipmentAssetName": "白色投影幕布（勿删）",
              "equipmentId": 20,
              "online": 1,
              "runningStatus": 0,
              "controlProtocolId": 5,
              "centerControlAssetId": 1,
              "gatewayAddr": "RLY1",
              "otherStatus": "",
              "serialNumber": "158288222-55",
              "purchaseDate": "2020-04-21 14:12:12",
              "serviceDate": "2020-04-14 14:12:14",
              "supplier": "宝迪",
              "maintenanceTelephone": "15062325154",
              "collaborationSpaceId": 1,
              "failureNumber": 0,
              "readed": 1,
              "maintenanceDate": "2020-05-13T16:00:00.000+0000",
              "equipment": {
                "id": 20,
                "enabled": 1,
                "creator": 55,
                "modifier": 55,
                "created": "2020-05-19 15:14:11",
                "modified": "2020-05-20 09:32:39",
                "equipmentName": "投影机（勿删）",
                "model": "FH550",
                "picture": "/api/static/image/1589872361264.jpg",
                "categoryId": 40,
                "brandId": 23,
                "controllable": 1,
                "readable": 1,
                "communicationMode": 1,
                "lifeType": 0,
                "recommendedLife": 5000,
                "warrantyPeriod": 5,
                "maintenanceFrequency": 2,
                "webLink": "https://www.appotronics.com/",
                "centerControlUnit": 0,
                "brandName": "光峰(勿删)",
                "primaryCategoryId": 2,
                "primaryCategoryName": "视频",
                "categoryName": "投影机(勿删)",
                "equipmentCommandList": [
                  {
                    "id": 80,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-20 09:32:39",
                    "modified": "2020-05-20 09:32:39",
                    "equipmentId": 20,
                    "commandId": 1,
                    "commandFormat": "on",
                    "cmdName": "on"
                  },
                  {
                    "id": 81,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-20 09:32:39",
                    "modified": "2020-05-20 09:32:39",
                    "equipmentId": 20,
                    "commandId": 2,
                    "commandFormat": "off",
                    "cmdName": "off"
                  }
                ],
                "equipmentReadtypeList": [
                  {
                    "id": 63,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-20 09:32:39",
                    "modified": "2020-05-20 09:32:39",
                    "equipmentId": 20,
                    "readTypeId": 9,
                    "readTypeName": "运行状态"
                  },
                  {
                    "id": 62,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-20 09:32:39",
                    "modified": "2020-05-20 09:32:39",
                    "equipmentId": 20,
                    "readTypeId": 10,
                    "readTypeName": "是否在线"
                  }
                ]
              },
              "collaborationSpaceName": "中会(勿删)",
              "organizationName": "北京太平宝迪-真实数据(勿删)",
              "organizationId": 1,
              "buildingName": "北京云谷电子商务产业园2号楼",
              "buildingId": 1,
              "floorId": 9,
              "floorNum": 6,
              "controlProtocolName": "继电器协议",
              "categoryCommandList": [
                {
                  "commandCode": "Btn_Jl_Kai",
                  "description": "开"
                },
                {
                  "commandCode": "Btn_Jl_Guan",
                  "description": "关"
                }
              ]
            },
            {
              "id": 5,
              "enabled": 1,
              "creator": 43,
              "modifier": 55,
              "created": "2020-04-21 16:00:14",
              "modified": "2020-06-04 18:24:04",
              "equipmentAssetName": "白色方形灯",
              "equipmentId": 23,
              "online": 1,
              "runningStatus": 1,
              "controlProtocolId": 5,
              "centerControlAssetId": 1,
              "gatewayAddr": "r3",
              "otherStatus": "",
              "serialNumber": "15822222-55",
              "purchaseDate": "2020-04-21 15:59:53",
              "serviceDate": "2020-04-21 15:59:56",
              "supplier": "宝迪",
              "maintenanceTelephone": "15062325154",
              "collaborationSpaceId": 1,
              "failureNumber": 0,
              "readed": 1,
              "maintenanceDate": "2020-05-20T16:00:00.000+0000",
              "equipment": {
                "id": 23,
                "enabled": 1,
                "creator": 55,
                "modifier": 55,
                "created": "2020-05-19 16:27:29",
                "modified": "2020-05-20 09:28:22",
                "equipmentName": "灯（勿删）",
                "model": "无",
                "picture": "/api/static/image/1589876775535.jpg",
                "categoryId": 45,
                "brandId": 26,
                "controllable": 1,
                "readable": 1,
                "communicationMode": 1,
                "lifeType": 0,
                "recommendedLife": 5000,
                "warrantyPeriod": 1,
                "maintenanceFrequency": 1,
                "webLink": "www.budee.com",
                "centerControlUnit": 0,
                "brandName": "其他(勿删)",
                "primaryCategoryId": 4,
                "primaryCategoryName": "环境电器",
                "categoryName": "灯光(勿删)",
                "equipmentCommandList": [
                  {
                    "id": 73,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-20 09:28:22",
                    "modified": "2020-05-20 09:28:22",
                    "equipmentId": 23,
                    "commandId": 1,
                    "commandFormat": "on",
                    "cmdName": "on"
                  },
                  {
                    "id": 74,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-20 09:28:22",
                    "modified": "2020-05-20 09:28:22",
                    "equipmentId": 23,
                    "commandId": 2,
                    "commandFormat": "off",
                    "cmdName": "off"
                  }
                ],
                "equipmentReadtypeList": [
                  {
                    "id": 86,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-20 09:28:22",
                    "modified": "2020-05-20 09:28:22",
                    "equipmentId": 23,
                    "readTypeId": 9,
                    "readTypeName": "运行状态"
                  },
                  {
                    "id": 85,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-20 09:28:22",
                    "modified": "2020-05-20 09:28:22",
                    "equipmentId": 23,
                    "readTypeId": 10,
                    "readTypeName": "是否在线"
                  }
                ]
              },
              "collaborationSpaceName": "中会(勿删)",
              "organizationName": "北京太平宝迪-真实数据(勿删)",
              "organizationId": 1,
              "buildingName": "北京云谷电子商务产业园2号楼",
              "buildingId": 1,
              "floorId": 9,
              "floorNum": 6,
              "controlProtocolName": "继电器协议",
              "categoryCommandList": [
                {
                  "commandCode": "Btn_Jl_Kai",
                  "description": "开"
                },
                {
                  "commandCode": "Btn_Jl_Guan",
                  "description": "关"
                }
              ]
            },
            {
              "id": 9,
              "enabled": 1,
              "creator": 43,
              "modifier": 45,
              "created": "2020-04-22 18:40:35",
              "modified": "2020-06-04 20:46:54",
              "equipmentAssetName": "中会议室空调",
              "equipmentId": 9,
              "online": 1,
              "runningStatus": 0,
              "controlProtocolId": 3,
              "centerControlAssetId": 1,
              "gatewayAddr": "com8",
              "otherStatus": "{\"AirConditionFanSeed\":\"Low\",\"AirConditionMode\":\"Cool\",\"AirConditionTemp\":\"20\"}",
              "serialNumber": "15822222-55",
              "purchaseDate": "2020-04-22 18:40:06",
              "serviceDate": "2020-04-22 18:40:09",
              "supplier": "宝迪",
              "maintenanceTelephone": "15062325154",
              "collaborationSpaceId": 1,
              "failureNumber": 0,
              "readed": 0,
              "equipment": {
                "id": 9,
                "enabled": 1,
                "creator": 43,
                "modifier": 55,
                "created": "2020-04-22 18:39:25",
                "modified": "2020-05-19 16:21:45",
                "equipmentName": "海林空调(勿删)",
                "model": "HL8002",
                "picture": "/api/static/image/1587551887998.jpg",
                "categoryId": 23,
                "brandId": 25,
                "controllable": 1,
                "readable": 1,
                "communicationMode": 1,
                "lifeType": 0,
                "recommendedLife": 20000,
                "warrantyPeriod": 6,
                "maintenanceFrequency": 6,
                "webLink": "www.extron",
                "centerControlUnit": 0,
                "brandName": "海林(勿删)",
                "primaryCategoryId": 4,
                "primaryCategoryName": "环境电器",
                "categoryName": "空调(勿删)",
                "equipmentCommandList": [
                  {
                    "id": 50,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-19 16:21:45",
                    "modified": "2020-05-19 16:21:45",
                    "equipmentId": 9,
                    "commandId": 1,
                    "commandFormat": "on",
                    "cmdName": "on"
                  },
                  {
                    "id": 26,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-19 16:21:45",
                    "modified": "2020-05-19 16:21:45",
                    "equipmentId": 9,
                    "commandId": 2,
                    "commandFormat": "off",
                    "cmdName": "off"
                  },
                  {
                    "id": 51,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-19 16:21:45",
                    "modified": "2020-05-19 16:21:45",
                    "equipmentId": 9,
                    "commandId": 38,
                    "commandFormat": "temp-gain",
                    "cmdName": "温度加"
                  },
                  {
                    "id": 52,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-19 16:21:45",
                    "modified": "2020-05-19 16:21:45",
                    "equipmentId": 9,
                    "commandId": 39,
                    "commandFormat": "temp-reduce",
                    "cmdName": "温度减"
                  },
                  {
                    "id": 53,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-19 16:21:45",
                    "modified": "2020-05-19 16:21:45",
                    "equipmentId": 9,
                    "commandId": 40,
                    "commandFormat": "mode-cold",
                    "cmdName": "制冷模式"
                  },
                  {
                    "id": 54,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-19 16:21:45",
                    "modified": "2020-05-19 16:21:45",
                    "equipmentId": 9,
                    "commandId": 41,
                    "commandFormat": "mode-ventilate",
                    "cmdName": "送风模式"
                  },
                  {
                    "id": 55,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-19 16:21:45",
                    "modified": "2020-05-19 16:21:45",
                    "equipmentId": 9,
                    "commandId": 42,
                    "commandFormat": "mode-hot",
                    "cmdName": "制热模式"
                  },
                  {
                    "id": 56,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-19 16:21:45",
                    "modified": "2020-05-19 16:21:45",
                    "equipmentId": 9,
                    "commandId": 43,
                    "commandFormat": "windSpeed-auto",
                    "cmdName": "自动风速"
                  },
                  {
                    "id": 57,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-19 16:21:45",
                    "modified": "2020-05-19 16:21:45",
                    "equipmentId": 9,
                    "commandId": 44,
                    "commandFormat": "windSpeed-low",
                    "cmdName": "低风速"
                  },
                  {
                    "id": 58,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-19 16:21:45",
                    "modified": "2020-05-19 16:21:45",
                    "equipmentId": 9,
                    "commandId": 45,
                    "commandFormat": "windSpeed-middle",
                    "cmdName": "中风速"
                  },
                  {
                    "id": 59,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-19 16:21:45",
                    "modified": "2020-05-19 16:21:45",
                    "equipmentId": 9,
                    "commandId": 46,
                    "commandFormat": "windSpeed-high",
                    "cmdName": "高风速"
                  }
                ],
                "equipmentReadtypeList": [
                  {
                    "id": 42,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-19 16:21:45",
                    "modified": "2020-05-19 16:21:45",
                    "equipmentId": 9,
                    "readTypeId": 6,
                    "readTypeName": "温度"
                  },
                  {
                    "id": 40,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-19 16:21:45",
                    "modified": "2020-05-19 16:21:45",
                    "equipmentId": 9,
                    "readTypeId": 9,
                    "readTypeName": "运行状态"
                  },
                  {
                    "id": 43,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-19 16:21:45",
                    "modified": "2020-05-19 16:21:45",
                    "equipmentId": 9,
                    "readTypeId": 10,
                    "readTypeName": "是否在线"
                  }
                ]
              },
              "collaborationSpaceName": "中会(勿删)",
              "organizationName": "北京太平宝迪-真实数据(勿删)",
              "organizationId": 1,
              "buildingName": "北京云谷电子商务产业园2号楼",
              "buildingId": 1,
              "floorId": 9,
              "floorNum": 6,
              "controlProtocolName": "串口协议",
              "categoryCommandList": [
                {
                  "commandCode": "Btn_Jl_Kai",
                  "description": "开"
                },
                {
                  "commandCode": "Btn_Jl_Guan",
                  "description": "关"
                },
                {
                  "commandCode": "Btn_KongTiao_WenDuJia",
                  "description": "温度加"
                },
                {
                  "commandCode": "Btn_KongTiao_WenDuJian",
                  "description": "温度减"
                },
                {
                  "commandCode": "Btn_KongTiao_ZhiLengMoShi",
                  "description": "制冷模式"
                },
                {
                  "commandCode": "Btn_KongTiao_SongFengMoShi",
                  "description": "送风模式"
                },
                {
                  "commandCode": "Btn_KongTiao_ZhiReMoShi",
                  "description": "制热模式"
                },
                {
                  "commandCode": "Btn_KongTiao_ZiDongFengSu",
                  "description": "自动风速"
                },
                {
                  "commandCode": "Btn_KongTiao_DiFengSu",
                  "description": "低风速"
                },
                {
                  "commandCode": "Btn_KongTiao_ZhongFengSu",
                  "description": "中风速"
                },
                {
                  "commandCode": "Btn_KongTiao_GaoFengSu",
                  "description": "高风速"
                }
              ]
            },
            {
              "id": 13,
              "enabled": 1,
              "creator": 51,
              "modifier": 55,
              "created": "2020-04-23 18:56:33",
              "modified": "2020-06-04 18:24:04",
              "equipmentAssetName": "南筒灯（勿删）",
              "equipmentId": 23,
              "online": 1,
              "runningStatus": 1,
              "controlProtocolId": 5,
              "centerControlAssetId": 1,
              "gatewayAddr": "r2",
              "otherStatus": "",
              "serialNumber": "SDF242342",
              "purchaseDate": "2020-04-23 18:56:21",
              "serviceDate": "2020-04-23 18:56:23",
              "supplier": "北京太平宝迪科技发展有限公司",
              "maintenanceTelephone": "18337428943",
              "collaborationSpaceId": 1,
              "failureNumber": 0,
              "readed": 1,
              "maintenanceDate": "2020-05-22T16:00:00.000+0000",
              "equipment": {
                "id": 23,
                "enabled": 1,
                "creator": 55,
                "modifier": 55,
                "created": "2020-05-19 16:27:29",
                "modified": "2020-05-20 09:28:22",
                "equipmentName": "灯（勿删）",
                "model": "无",
                "picture": "/api/static/image/1589876775535.jpg",
                "categoryId": 45,
                "brandId": 26,
                "controllable": 1,
                "readable": 1,
                "communicationMode": 1,
                "lifeType": 0,
                "recommendedLife": 5000,
                "warrantyPeriod": 1,
                "maintenanceFrequency": 1,
                "webLink": "www.budee.com",
                "centerControlUnit": 0,
                "brandName": "其他(勿删)",
                "primaryCategoryId": 4,
                "primaryCategoryName": "环境电器",
                "categoryName": "灯光(勿删)",
                "equipmentCommandList": [
                  {
                    "id": 73,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-20 09:28:22",
                    "modified": "2020-05-20 09:28:22",
                    "equipmentId": 23,
                    "commandId": 1,
                    "commandFormat": "on",
                    "cmdName": "on"
                  },
                  {
                    "id": 74,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-20 09:28:22",
                    "modified": "2020-05-20 09:28:22",
                    "equipmentId": 23,
                    "commandId": 2,
                    "commandFormat": "off",
                    "cmdName": "off"
                  }
                ],
                "equipmentReadtypeList": [
                  {
                    "id": 86,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-20 09:28:22",
                    "modified": "2020-05-20 09:28:22",
                    "equipmentId": 23,
                    "readTypeId": 9,
                    "readTypeName": "运行状态"
                  },
                  {
                    "id": 85,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-20 09:28:22",
                    "modified": "2020-05-20 09:28:22",
                    "equipmentId": 23,
                    "readTypeId": 10,
                    "readTypeName": "是否在线"
                  }
                ]
              },
              "collaborationSpaceName": "中会(勿删)",
              "organizationName": "北京太平宝迪-真实数据(勿删)",
              "organizationId": 1,
              "buildingName": "北京云谷电子商务产业园2号楼",
              "buildingId": 1,
              "floorId": 9,
              "floorNum": 6,
              "controlProtocolName": "继电器协议",
              "categoryCommandList": [
                {
                  "commandCode": "Btn_Jl_Kai",
                  "description": "开"
                },
                {
                  "commandCode": "Btn_Jl_Guan",
                  "description": "关"
                }
              ]
            },
            {
              "id": 14,
              "enabled": 1,
              "creator": 55,
              "modifier": 55,
              "created": "2020-04-28 10:25:09",
              "modified": "2020-06-05 09:50:00",
              "equipmentAssetName": "中会七合一传感器",
              "equipmentId": 14,
              "online": 1,
              "runningStatus": 1,
              "controlProtocolId": 3,
              "centerControlAssetId": 1,
              "gatewayAddr": "com7",
              "otherStatus": "{\"tvoc\":0.467,\"co2\":1144.0,\"pm10\":0.018000000000000002,\"ch2o\":0.131,\"pm25\":10.0,\"temperature\":31.7,\"humidity\":31.4}",
              "serialNumber": "10000000000001",
              "purchaseDate": "2020-04-27 10:22:44",
              "serviceDate": "2020-04-27 10:22:47",
              "supplier": "北京太平宝迪科技发展有限公司",
              "maintenanceTelephone": "13126855981",
              "collaborationSpaceId": 1,
              "failureNumber": 0,
              "readed": 0,
              "equipment": {
                "id": 14,
                "enabled": 1,
                "creator": 55,
                "modifier": 55,
                "created": "2020-04-28 10:21:18",
                "modified": "2020-06-04 17:36:13",
                "equipmentName": "7合一传感器(勿删)",
                "model": "SM300D2MOD",
                "picture": "/api/static/image/1588040411499.jpg",
                "categoryId": 22,
                "brandId": 14,
                "controllable": 1,
                "readable": 1,
                "communicationMode": 1,
                "lifeType": 0,
                "recommendedLife": 50000,
                "warrantyPeriod": 5,
                "maintenanceFrequency": 12,
                "webLink": "www.extron.com",
                "centerControlUnit": 0,
                "brandName": "DingDee(勿删)",
                "primaryCategoryId": 5,
                "primaryCategoryName": "传感器",
                "categoryName": "环境传感器(勿删)",
                "equipmentCommandList": [
                  {
                    "id": 42,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-06-04 17:36:13",
                    "modified": "2020-06-04 17:36:13",
                    "equipmentId": 14,
                    "commandId": 33,
                    "commandFormat": "status",
                    "cmdName": "status"
                  },
                  
                  {
                    "id": 93,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-06-04 17:36:13",
                    "modified": "2020-06-04 17:36:13",
                    "equipmentId": 14,
                    "commandId": 72,
                    "commandFormat": "status",
                    "cmdName": "读取甲醛"
                  },
                  {
                    "id": 94,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-06-04 17:36:13",
                    "modified": "2020-06-04 17:36:13",
                    "equipmentId": 14,
                    "commandId": 73,
                    "commandFormat": "status",
                    "cmdName": "读取二氧化碳"
                  },
                  {
                    "id": 95,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-06-04 17:36:13",
                    "modified": "2020-06-04 17:36:13",
                    "equipmentId": 14,
                    "commandId": 74,
                    "commandFormat": "status",
                    "cmdName": "读取TVOC"
                  }
                ],
                "equipmentReadtypeList": [
                  {
                    "id": 3,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-06-04 17:36:13",
                    "modified": "2020-06-04 17:36:13",
                    "equipmentId": 14,
                    "readTypeId": 1,
                    "readTypeName": "CO2"
                  },
                  {
                    "id": 4,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-06-04 17:36:13",
                    "modified": "2020-06-04 17:36:13",
                    "equipmentId": 14,
                    "readTypeId": 2,
                    "readTypeName": "PM2.5"
                  },
                  {
                    "id": 5,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-06-04 17:36:13",
                    "modified": "2020-06-04 17:36:13",
                    "equipmentId": 14,
                    "readTypeId": 3,
                    "unitName": "ug/m3",
                    "multiplying": 0.001,
                    "readTypeName": "PM10"
                  },
                  {
                    "id": 6,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-06-04 17:36:13",
                    "modified": "2020-06-04 17:36:13",
                    "equipmentId": 14,
                    "readTypeId": 4,
                    "unitName": "ug/m3",
                    "multiplying": 0.001,
                    "readTypeName": "总挥发性有机化合物"
                  },
                  {
                    "id": 7,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-06-04 17:36:13",
                    "modified": "2020-06-04 17:36:13",
                    "equipmentId": 14,
                    "readTypeId": 5,
                    "unitName": "ug/m3",
                    "multiplying": 0.001,
                    "readTypeName": "甲醛"
                  },
                  {
                    "id": 8,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-06-04 17:36:13",
                    "modified": "2020-06-04 17:36:13",
                    "equipmentId": 14,
                    "readTypeId": 6,
                    "readTypeName": "温度"
                  },
                  {
                    "id": 34,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-06-04 17:36:13",
                    "modified": "2020-06-04 17:36:13",
                    "equipmentId": 14,
                    "readTypeId": 10,
                    "readTypeName": "是否在线"
                  }
                ]
              },
              "collaborationSpaceName": "中会(勿删)",
              "organizationName": "北京太平宝迪-真实数据(勿删)",
              "organizationId": 1,
              "buildingName": "北京云谷电子商务产业园2号楼",
              "buildingId": 1,
              "floorId": 9,
              "floorNum": 6,
              "controlProtocolName": "串口协议",
              "categoryCommandList": [
                {
                  "commandCode": "status",
                  "description": "查看设备的状态"
                },
                {
                  "commandCode": "Btn_HuanJingChuanGanQi_DuQuWenDu",
                  "description": "读取温度"
                },
                {
                  "commandCode": "Btn_HuanJingChuanGanQi_DuQuTVOC",
                  "description": "读取TVOC"
                }
              ]
            },
            {
              "id": 15,
              "enabled": 1,
              "creator": 55,
              "modifier": 45,
              "created": "2020-04-28 14:12:00",
              "modified": "2020-06-05 09:59:15",
              "equipmentAssetName": "中会人体感应器",
              "equipmentId": 15,
              "online": 1,
              "runningStatus": 1,
              "controlProtocolId": 6,
              "centerControlAssetId": 1,
              "gatewayAddr": "FIO1",
              "otherStatus": "{\"OccupyState\":\"Idle\"}",
              "serialNumber": "10055555555",
              "purchaseDate": "2020-04-22 14:11:14",
              "serviceDate": "2020-04-27 14:11:17",
              "supplier": "北京太平宝迪科技发展有限公司",
              "maintenanceTelephone": "13126855981",
              "collaborationSpaceId": 1,
              "failureNumber": 0,
              "readed": 0,
              "equipment": {
                "id": 15,
                "enabled": 1,
                "creator": 55,
                "modifier": 55,
                "created": "2020-04-28 14:08:20",
                "modified": "2020-06-04 17:56:29",
                "equipmentName": "人感(勿删)",
                "model": "OCS 100",
                "picture": "/api/static/image/1588054032642.jpg",
                "categoryId": 46,
                "brandId": 1,
                "controllable": 1,
                "readable": 1,
                "communicationMode": 1,
                "lifeType": 0,
                "recommendedLife": 100000,
                "warrantyPeriod": 5,
                "maintenanceFrequency": 2,
                "webLink": "www.extron.com",
                "centerControlUnit": 0,
                "brandName": "Extron(勿删)",
                "primaryCategoryId": 5,
                "primaryCategoryName": "传感器",
                "categoryName": "人体传感器(勿删)",
                "equipmentCommandList": [],
                "equipmentReadtypeList": [
                  readTypeName": "运行状态"
                  },
                  {
                    "id": 38,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-05-13 10:53:35",
                    "modified": "2020-05-13 10:53:38",
                    "equipmentId": 15,
                    "readTypeId": 10,
                    "readTypeName": "是否在线"
                  }
                ]
              },
              "collaborationSpaceName": "中会(勿删)",
              "organizationName": "北京太平宝迪-真实数据(勿删)",
              "organizationId": 1,
              "buildingName": "北京云谷电子商务产业园2号楼",
              "buildingId": 1,
              "floorId": 9,
              "floorNum": 6,
              "controlProtocolName": "FlexIOPort"
            },
            {
              "id": 16,
              "enabled": 1,
              "creator": 55,
              "modifier": 55,
              "created": "2020-05-03 10:33:47",
              "modified": "2020-06-05 01:01:04",
              "equipmentAssetName": "中会智能电表",
              "equipmentId": 16,
              "online": 1,
              "runningStatus": 1,
              "controlProtocolId": 1,
              "centerControlAssetId": 1,
              "gatewayAddr": "192.168.1.203",
              "otherStatus": "{\"energyValue\":\"406.03\"}",
              "serialNumber": "112233333333333",
              "purchaseDate": "2020-05-02 10:33:03",
              "serviceDate": "2020-05-01 10:33:13",
              "supplier": "北京太平宝迪科技发展有限公司",
              "maintenanceTelephone": "13126855981",
              "collaborationSpaceId": 1,
              "failureNumber": 0,
              "readed": 0,
              "equipment": {
                "id": 16,
                "enabled": 1,
                "creator": 55,
                "modifier": 55,
                "created": "2020-05-03 10:05:44",
                "modified": "2020-06-04 17:56:14",
                "equipmentName": "智能电表(勿删)",
                "model": "113-II",
                "picture": "/api/static/image/1588471444899.jpg",
                "categoryId": 47,
                "brandId": 14,
                "controllable": 1,
                "readable": 1,
                "communicationMode": 1,
                "lifeType": 0,
                "recommendedLife": 50000,
                "warrantyPeriod": 20,
                "maintenanceFrequency": 12,
                "webLink": "www.budee.com",
                "centerControlUnit": 0,
                "brandName": "DingDee(勿删)",
                "primaryCategoryId": 5,
                "primaryCategoryName": "传感器",
                "categoryName": "电量传感器(勿删)",
                "equipmentCommandList": [
                  {
                    "id": 43,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-06-04 17:56:14",
                    "modified": "2020-06-04 17:56:14",
                    "equipmentId": 16,
                    "commandId": 33,
                    "commandFormat": "status",
                    "cmdName": "status"
                  }
                ],
                "equipmentReadtypeList": [
                  {
                    "id": 37,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-06-04 17:56:14",
                    "modified": "2020-06-04 17:56:14",
                    "equipmentId": 16,
                    "readTypeId": 9,
                    "readTypeName": "运行状态"
                  }
                ]
              },
              "collaborationSpaceName": "中会(勿删)",
              "organizationName": "北京太平宝迪-真实数据(勿删)",
              "organizationId": 1,
              "buildingName": "北京云谷电子商务产业园2号楼",
              "buildingId": 1,
              "floorId": 9,
              "floorNum": 6,
              "controlProtocolName": "网络协议",
              "categoryCommandList": [
                {
                  "commandCode": "status",
                  "description": "查看设备的状态"
                }
              ]
            }
          ]
        }
                


## 分类管理
+ Data
    + id (Long) ID
    + categoryName (String) 分类名
    + parentId (long) 上级分类ID
    + picture (String) 图片链接
    + description (String) 描述
    + displayOrder (int) 排序id
    + primaryCategoryName  (String) 一级分类名
    + enabled (int)  - 使能  0禁止 1启用
    + creator (long) - 创建人
    + modifier (long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间

   
### 新增分类 [POST] /category

+ Description

+ Request (application/json)

        {
          "data": {
            "parentId": 1,
            "categoryName": "中控分类2",
            "picture": "http://static.budee.com/cms/upload/image/20200322/1584862487761035082.png",
            "description": "http://static.budee.com/cms/upload/image/20200322/1584862487761035082.png",
            "displayOrder": 100
          }
        }
+ Response 200

        {
          "data": {
            "id": 3,
            "type": "category"
          }
        }

+ Response 400

        {
          "errors": [
            {
              "status": "400",
              "title": "Bad Request",
              "detail": "上级分类不存在"
            }
          ]
        }

        
### 删除分类 [DEL] /category/{id}
+ Description

+ Response 200  

        
### 修改分类 [PATCH] /category/{id}

+ Description


+ Request (application/json)
    
        {
          "data": {
            "id": 3,
            "parentId": 0,
            "categoryName": "中控分类2",
            "picture": "http://static.budee.com/cms/upload/image/20200322/1584862487761035082.png",
            "description": "http://static.budee.com/cms/upload/image/20200322/1584862487761035082.png",
            "displayOrder": 100
          }
        }
+ Response 200
+ Response 400

### 查询分类详情 [GET] /category/{id}
+ Description

+ Response 200
    
        {
          "data": {
            "id": 3,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2020-03-26 13:33:24",
            "modified": "2020-03-26 13:33:24",
            "parentId": 0,
            "categoryName": "中控分类2",
            "picture": "http://static.budee.com/cms/upload/image/20200322/1584862487761035082.png",
            "description": "http://static.budee.com/cms/upload/image/20200322/1584862487761035082.png",
            "displayOrder": 100
          }
        }

### 查询分类列表 [GET] /category
+ Description

+ Parameters
    + page[number] (int)  页码  -非必填
    + page[size]  (int)   页尺  -非必填
    + filter[brandId] (long) 品牌ID
    + filter[primaryCategoryid] (long) 一级分类ID
    + filter[categoryId] (long) 二级分类ID
    + filter[communicationId] (int) 通信方式ID
    + filter[equipmentName] (string)  设备名字
    + filter[equipmentModel] (string) 设备型号 
    
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
            "self": "/category?page[number]=1&page[size]=10",
            "first": "/category?page[number]=1&page[size]=10",
            "last": "/category?page[number]=1&page[size]=10"
          },
          "data": [
            {
              "id": 1,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-03-24 13:38:04",
              "modified": "2020-03-24 13:38:02",
              "parentId": 0,
              "categoryName": "中控",
              "picture": "http://static.budee.com/cms/upload/image/20200322/1584862487761035082.png",
              "description": "http://static.budee.com/cms/upload/image/20200322/1584862487761035082.png",
              "displayOrder": 100
            },
            {
              "id": 2,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "parentId": 1,
              "categoryName": "中控分类1",
              "picture": "http://static.budee.com/cms/upload/image/20200322/1584862487761035082.png",
              "description": "http://static.budee.com/cms/upload/image/20200322/1584862487761035082.png",
              "displayOrder": 100,
              "primaryCategoryName": "中控"
            },
            {
              "id": 3,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-03-26 13:33:24",
              "modified": "2020-03-26 13:33:24",
              "parentId": 0,
              "categoryName": "中控分类2",
              "picture": "http://static.budee.com/cms/upload/image/20200322/1584862487761035082.png",
              "description": "http://static.budee.com/cms/upload/image/20200322/1584862487761035082.png",
              "displayOrder": 100
            }
          ]
        }
