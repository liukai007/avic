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
            "modifier": 0,
            "created": "2020-03-23 16:41:40",
            "modified": "2020-03-23 16:41:42",
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
            "usedLife": 1,
            "equipment": {
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
            }
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
                "totalPages": 1,
                "totalElements": 2,
                "size": 10,
                "number": 1,
                "numberOfElements": 2,
                "first": true,
                "last": true,
                "sort": null
              },
              "links": {
                "self": "/equipmentasset?page[number]=1&page[size]=10",
                "first": "/equipmentasset?page[number]=1&page[size]=10",
                "last": "/equipmentasset?page[number]=1&page[size]=10"
              },
              "data": [
                {
                  "id": 1,
                  "enabled": 1,
                  "creator": 0,
                  "modifier": 0,
                  "created": "2020-03-23 16:41:40",
                  "modified": "2020-03-23 16:41:42",
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
                  "usedLife": 1,
                  "equipment": {
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
                  "collaborationSpaceName": "协作空间1",
                  "organizationName": "北京太平宝迪",
                  "organizationId": 1,
                  "buildingName": "云谷",
                  "buildingId": 1,
                  "floorId": 1,
                  "floorNum": 6
                },
                {
                  "id": 2,
                  "enabled": 1,
                  "creator": 0,
                  "modifier": 0,
                  "created": "2020-03-23 16:44:45",
                  "modified": "2020-03-23 16:44:47",
                  "equipmentAssetName": "中控1",
                  "equipmentId": 2,
                  "online": 1,
                  "runningStatus": 1,
                  "picture": "http://static.budee.com/cms/upload/image/20200322/",
                  "controlProtocolId": 1,
                  "centerControlAssetId": 0,
                  "gatewayAddr": "192.168.1.122",
                  "centerControlIp": "192.168.1.122",
                  "centerControlPort": 8008,
                  "serialNumber": "008",
                  "purchaseDate": "2020-03-24T10:32:11.000+0000",
                  "serviceDate": "2020-03-24T10:32:15.000+0000",
                  "supplier": "12",
                  "maintenanceTelephone": "13555555555",
                  "collaborationSpaceId": 2,
                  "usedLife": 1000,
                  "equipment": {
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
                  "collaborationSpaceName": "协作空间2",
                  "organizationName": "北京太平宝迪",
                  "organizationId": 1,
                  "buildingName": "云谷",
                  "buildingId": 1,
                  "floorId": 1,
                  "floorNum": 6
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

    
