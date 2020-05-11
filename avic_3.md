# AVIC迭代3管理端接口文档

+ 2020年4月24日
    + 新增智能场景
    + 删除智能场景
    + 修改智能场景
    + 查询智能场景详情
    + 查询智能场景列表

+ 2020年4月26日
    + 新增或者修改智能场景设备命令详情
    + 查询智能场景设备命令详情

+ 2020年4月26日
    + 新增或者修改智能场景条件集
    + 查询智能场景条件集

+ 2020年4月27日
    + 新增读数类型
    + 删除读数类型
    + 修改读数类型
    + 查询读数类型景详情
    + 查询读数类型列表

+ 2020年4月30日
    + 环境数据分析接口
    + 当前协作空间环境数据

+ 2020年5月04日
    + 数据总览-协作空间使用次数接口
    + 数据总览-协作空间使用电量接口

+ 2020年5月04日
    + 机构统计接口
    + 楼宇统计接口
    + 协作空间统计接口
    + 受控情况接口
    + 品牌统计接口
    + 分类统计接口
    + 控制协议统计接口

+ 2020年5月06日
    + 协作空间统计-次数&电量统计
    
+ 2020年5月09日
    + 协作空间统计-使用次数排名(协作空间)&故障报警排名(协作空间)
    + 使用年限统计
    + 寿命统计
    
## 智能场景
+ Data
    + id (long) ID
    + sceneName (string) 场景名称
    + sceneType (int)  场景类型 (0为触发类，1为条件类)
    + collaborationId (int) 协作空间ID
    + opened (int) 是否开启 (1表示开启，0表示关闭)
    + enabled (int)  - 使能  0禁止 1启用
    + creator (long) - 创建人
    + modifier (long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间
    + collaborationName  (string) 协作空间名称

   
### 新增智能场景 [POST] /intelligentScene

+ Description
    + Author Liukai
+ Request (application/json)

        {
          "data": {
            "sceneName": "空调自动1",
            "sceneType": 1,
            "collaborationId": 1,
            "opened": 1
          }
        }
+ Response 200

        {
          "data": {
            "id": 3,
            "type": "intelligentScene"
          }
        }

+ Response 400

        {
          "errors": [
            {
              "status": "400",
              "title": "Bad Request",
              "detail": "该智能场景名称已经存在"
            }
          ]
        }

        
### 删除智能场景 [DEL] /intelligentScene/{id}
+ Description
    + Author Liukai
+ Response 204 

        
### 修改智能场景 [PATCH] /intelligentScene/{id}

+ Description
    + Author Liukai

+ Request (application/json)
    
        {
          "data": {
            "id": 1,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2020-04-24 17:21:33",
            "modified": "2020-04-24 17:21:37",
            "sceneName": "空调自动",
            "sceneType": 1,
            "collaborationId": 1,
            "opened": 1,
            "collaborationName": "中会"
          }
        }
+ Response 200
+ Response 400

### 查询智能场景详情 [GET] /intelligentScene/{id}
+ Description
    + Author Liukai
+ Response 200
    
        {
          "data": {
            "id": 1,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2020-04-24 17:21:33",
            "modified": "2020-04-24 17:21:37",
            "sceneName": "空调自动场景",
            "sceneType": 1,
            "collaborationId": 1,
            "opened": 1,
            "collaborationName": "中会"
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

### 查询智能场景列表 [GET] /intelligentScene

+ Description
    + Author Liukai

    比如：http://127.0.0.1:8080/intelligentScene?page[number]=1&page[size]=10&filter[sceneName:like]=%%E8%87%AA%

+ Parameters
    + page[number] (int)  页码  -非必填
    + page[size]  (int)   页尺  -非必填
    + filter[sceneName:like] (string)  场景名称
    + filter[sceneType] (int)  场景类型 场景类型 (0为触发类，1为条件类)
    + filter[collaborationId] (long) 协作空间ID

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
            "self": "/intelligentScene?page[number]=1&page[size]=10",
            "first": "/intelligentScene?page[number]=1&page[size]=10",
            "last": "/intelligentScene?page[number]=1&page[size]=10"
          },
          "data": [
            {
              "id": 1,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-04-24 17:21:33",
              "modified": "2020-04-24 17:21:37",
              "sceneName": "空调自动场景",
              "sceneType": 1,
              "collaborationId": 1,
              "opened": 1，
              "collaborationName": "中会"
            },
            {
              "id": 2,
              "enabled": 1,
              "creator": 55,
              "modifier": 55,
              "created": "2020-04-24 17:42:14",
              "modified": "2020-04-24 17:42:14",
              "sceneName": "空调自动",
              "sceneType": 1,
              "collaborationId": 1,
              "opened": 1，
              "collaborationName": "中会"
            }
          ]
        }

## 智能场景设备命令详情

+ Data
    + id (long) ID
    + enabled (int)  - 使能  0禁止 1启用
    + creator (long) - 创建人
    + modifier (long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间
    + sceneId  (long)
    + equipmentassetId  (long) 资产设备ID
    + equipmentCmdId  (long) 设备命令ID
    + cmdName  (string)  命令名称
    + primaryCategoryName  (string) 一级分类名称
    + primaryCategoryId (string) 一级分类ID
    + secondCategoryName  (string)  二级分类名称
    + secondCategoryId (long) 二级分类ID （如果为0，这一级分类则为null,一级分类名，二级分类名都为null）
    + equipmentName  (string) 设备名
    + equipmentModel  (string) 设备型号

   
### 新增或者修改智能场景设备命令详情 [POST] /intelligentSceneDetails

+ Description
    + Author Liukai

+ Request (application/json)

        {
          "data": {
            "intelligentSceneDetailsList": [
              {
                "sceneId": 1,
                "equipmentassetId": 1,
                "equipmentCmdId": 2
              },
              {
                "sceneId": 1,
                "equipmentassetId": 1,
                "equipmentCmdId": 3
              }
            ]
          }
        }

        
+ Response 201(添加)

        {
          "data": {
            "type": "IntelligentSceneDetails"
          }
        }

+ Response 200 (修改)


+ Response 400

        {
          "errors": [
            {
              "status": "400",
              "code": "命令ID不能为空",
              "title": "Bad Request",
              "detail": "命令ID不能为空",
              "source": {
                "pointer": "IntelligentSceneDetails -> equipmentCmdId"
              }
            }
          ]
        }
        

### 查询智能场景设备命令详情 [GET] /intelligentSceneDetails/{intelligentSceneId}
+ Description
    + Author Liukai
    
+ Parameters
    + intelligentSceneId (long) 智能场景ID

+ Response 200
    
        {
          "data": {
            "intelligentSceneDetailsList": [
              {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2020-04-26 15:33:29",
                "modified": "2020-04-26 15:33:32",
                "sceneId": 1,
                "equipmentassetId": 1,
                "equipmentCmdId": 1,
                "secondCategoryId": 0,
                "equipmentName": "吊顶大音响",
                "equipmentModel": "CS-1"
              },
              {
                "id": 2,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2020-04-26 15:58:38",
                "modified": "2020-04-26 15:58:40",
                "sceneId": 1,
                "equipmentassetId": 1,
                "equipmentCmdId": 2,
                "secondCategoryId": 0,
                "equipmentName": "吊顶大音响",
                "equipmentModel": "CS-1"
              },
              {
                "id": 3,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2020-04-26 15:58:52",
                "modified": "2020-04-26 15:58:55",
                "sceneId": 1,
                "equipmentassetId": 1,
                "equipmentCmdId": 3,
                "primaryCategoryName": "音频",
                "primaryCategoryId": 1,
                "secondCategoryName": "01音箱",
                "secondCategoryId": 12,
                "equipmentName": "吊顶大音响",
                "equipmentModel": "CS-1",
                "cmdName": "01音箱"
              }
            ]
          }
        }   


## 智能场景条件集


    
+ Data
    + conditionalRelation (int) 条件关系（0 与， 1或 ）
    + conditionalRelationName  (string)  条件关系名
    + intelligentSceneConditionList (list) 条件关系集合
        + id (long) ID
        + enabled (int)  - 使能  0禁止 1启用
        + creator (long) - 创建人
        + modifier (long) - 修改人
        + created (date) - 创建时间
        + modified (date) - 修改时间
        + sceneId  (long)
        + equipmentassetId  (long) 资产设备ID
        + readTypeId (long) 读数类型ID
        + readTypeName (string) 读数类型名称
        + conditionalRelation  (int)  所有条件关系ID
        + conditionalRelationName (string)  所有条件关系名
        + judgeCondition  (int) 判断符号ID
        + judgeConditionName (string) 判断符号名
        + readValue (string) 对应值（进行判断的值）
        + equipmentName  (string) 设备名称
        + equipmentModel (string) 设备型号


   
### 新增或者修改智能场景条件集 [POST]  /intelligentSceneCondition

+ Description
    + Author Liukai
+ Request (application/json)

        {
          "data": {
            "intelligentSceneConditionList": [
              {
                "sceneId": 1,
                "equipmentassetId": 1,
                "readTypeId": 1,
                "conditionalRelation": 0,
                "judgeCondition": 0,
                "readValue": "18.0"
              },
              {
                "sceneId": 1,
                "equipmentassetId": 1,
                "readTypeId": 2,
                "conditionalRelation": 0,
                "judgeCondition": 0,
                "readValue": "on"
              }
            ]
          }
        }
        
+ Response 201(添加)

        {
          "data": {
            "type": "IntelligentSceneCondition"
          }
        }

+ Response 200 (修改)


+ Response 400

        {
          "errors": [
            {
              "status": "400",
              "code": "命令ID不能为空",
              "title": "Bad Request",
              "detail": "命令ID不能为空",
              "source": {
                "pointer": "IntelligentSceneDetails -> equipmentCmdId"
              }
            }
          ]
        }
        

### 查询智能场景条件集 [GET] /intelligentSceneCondition/{intelligentSceneId}
+ Description
    + Author Liukai
+ Parameters
    + intelligentSceneId (long) 智能场景ID

+ Response 200
    
        {
          "data": {
            "conditionalRelation": 0,
            "conditionalRelationName": "与",
            "intelligentSceneConditionList": [
              {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2020-04-26 18:02:15",
                "modified": "2020-04-26 18:02:13",
                "sceneId": 1,
                "equipmentassetId": 1,
                "readTypeId": 1,
                "conditionalRelation": 0,
                "judgeCondition": 0,
                "readValue": "18.0",
                "equipmentName": "吊顶大音响",
                "equipmentModel": "CS-1",
                "readTypeName": "co2",
                "conditionalRelationName": "与",
                "judgeConditionName": "等于"
              },
              {
                "id": 2,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2020-04-26 18:06:55",
                "modified": "2020-04-26 18:06:58",
                "sceneId": 1,
                "equipmentassetId": 1,
                "readTypeId": 2,
                "conditionalRelation": 0,
                "judgeCondition": 0,
                "readValue": "on",
                "equipmentName": "吊顶大音响",
                "equipmentModel": "CS-1",
                "readTypeName": "是否占用",
                "conditionalRelationName": "与",
                "judgeConditionName": "等于"
              }
            ]
          }
        } 



## 读数类型(主要是设备的其他返回值，在数据库中固定下来)
+ Data
    + id (long) ID
    + readtypeNameChinese  (string) 读数类型中文名
    + readtypeName  (string) 读数类型英文名
    + readValueType  (int) 读数值返回的类型(0 字符串类型 1 整数型 2 float型)
    + returnValue  (string) 返回值组(用英文逗号隔开不同的返回值)
    + enabled (int)  - 使能  0禁止 1启用
    + creator (long) - 创建人
    + modifier (long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间
    + returnValueList (List) 返回值数组 （针对字符串类型，方便用户选择，不用手动填写）

   
### 新增读数类型 [POST] /readType

+ Description
    + Author Liukai
+ Request (application/json)

        {
          "data": {
            "readtypeNameChinese"："占用",
            "readtypeName": "ocuppy",
              "readValueType": 0,
              "returnValue": "on,off1"
          }
        }
+ Response 200

        {
          "data": {
            "id": 3,
            "type": "readType"
          }
        }

+ Response 400

        {
          "errors": [
            {
              "status": "400",
              "code": "读数类型名不能为空",
              "title": "Bad Request",
              "detail": "读数类型名不能为空",
              "source": {
                "pointer": "ReadType -> readtypeName"
              }
            }
          ]
        }

        
### 删除读数类型 [DEL] /readType{id}
+ Description
    + Author Liukai
+ Response 204 
+ Response 400

        {
          "errors": [
            {
              "status": "400",
              "title": "Bad Request",
              "detail": "内置读数类型不能删除"
            }
          ]
        }

        
### 修改读数类型 [PATCH] /readType{id}

+ Description
    + Author Liukai

+ Request (application/json)
    
        {
          "data": {
            "readtypeNameChinese"："占用",
            "readtypeName": "是否占用1",
              "readValueType": 0,
              "returnValue": "on,off1"
          }
        }
+ Response 200
+ Response 400

### 查询读数类型详情 [GET] /readType/{id}
+ Description
    + Author Liukai
+ Response 200
    
        {
          "data": {
            "id": 8,
            "enabled": 1,
            "creator": 55,
            "modifier": 55,
            "created": "2020-04-30 14:49:24",
            "modified": "2020-04-30 14:49:24",
            "readtypeNameChinese": "占用",
            "readtypeName": "OccupyState",
            "readValueType": 0,
            "returnValue": "Occupy,Idle",
            "builtIn": 0,
            "returnValueList": [
              "Occupy",
              "Idle"
            ]
          }
        }

### 查询读数类型列表 [GET] /readType

+ Description
    + Author Liukai

+ Parameters
    + page[number] (int)  页码  -非必填
    + page[size]  (int)   页尺  -非必填
    + filter[readtypeName:like] (string)  读数类型名称
    + filter[readValueType] (int)  读数返回值类型读数值返回的类型 (0 字符串类型 1 整数型 2 float型)

+ Response 200

            {
          "meta": {
            "totalPages": 1,
            "totalElements": 8,
            "size": 10,
            "number": 1,
            "numberOfElements": 8,
            "first": true,
            "last": true,
            "sort": null
          },
          "links": {
            "self": "/readType?page[number]=1&page[size]=10",
            "first": "/readType?page[number]=1&page[size]=10",
            "last": "/readType?page[number]=1&page[size]=10"
          },
          "data": [
            {
              "id": 1,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-04-26 18:04:19",
              "modified": "2020-04-26 18:04:26",
              "readtypeNameChinese": "CO2",
              "readtypeName": "co2",
              "readValueType": 2,
              "builtIn": 1
            },
            {
              "id": 2,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-04-26 18:04:17",
              "modified": "2020-04-26 18:04:22",
              "readtypeNameChinese": "PM2.5",
              "readtypeName": "pm25",
              "readValueType": 2,
              "returnValue": "",
              "builtIn": 1
            },
            {
              "id": 3,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-04-27 17:43:56",
              "modified": "2020-04-27 17:46:33",
              "readtypeNameChinese": "PM10",
              "readtypeName": "pm10",
              "readValueType": 2,
              "returnValue": "",
              "builtIn": 1
            },
            {
              "id": 4,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "modified": "2020-04-27 18:48:34",
              "readtypeNameChinese": "总挥发性有机化合物",
              "readtypeName": "tvoc",
              "readValueType": 2,
              "builtIn": 1
            },
            {
              "id": 5,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-04-27 18:48:31",
              "modified": "2020-04-27 18:48:38",
              "readtypeNameChinese": "甲醛",
              "readtypeName": "ch2o",
              "readValueType": 2,
              "builtIn": 1
            },
            {
              "id": 6,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-04-30 10:39:54",
              "modified": "2020-04-30 10:39:57",
              "readtypeNameChinese": "温度",
              "readtypeName": "temperature",
              "readValueType": 2,
              "builtIn": 1
            },
            {
              "id": 7,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-04-30 10:40:36",
              "modified": "2020-04-30 10:40:39",
              "readtypeNameChinese": "湿度",
              "readtypeName": "humidity",
              "readValueType": 2,
              "builtIn": 1
            },
            {
              "id": 8,
              "enabled": 1,
              "creator": 55,
              "modifier": 55,
              "created": "2020-04-30 14:49:24",
              "modified": "2020-04-30 14:49:24",
              "readtypeNameChinese": "占用",
              "readtypeName": "OccupyState",
              "readValueType": 0,
              "returnValue": "Occupy,Idle",
              "builtIn": 0
            }
          ]
        }

## 环境数据分析接口  [GET]  /logEnvironment

+ Description
    + Author Liukai

+ Parameters
    + collaborationSpaceId (long)  协作空间ID  
    + dateType  (int)   时间类型 1：月，2：周，3：日
    + dateMinStr (string)  开始日期 格式：yyyy-MM-dd HH:mm:ss
    + dateMaxStr (string)  结束日期 格式：yyyy-MM-dd HH:mm:ss

+ ReturnData
    + created (date) 创建日期
    + equipmentassetId (long) 资产设备ID
    + collaborationId (long)  协作空间ID
    + temperature (float)  温度  
    + humidity (float)   湿度
    + co2 (float)   co2
    + pm25 (float)   pm2.5
    + pm10 (float)   pm10
    + tvoc (float)   总挥发性有机化合物
    + ch2o (float)   甲醛
              
+ Response 200

        {
          "data": [
            {
              "created": "2020-04-28 00:00:00",
              "equipmentassetId": 14,
              "collaborationId": 1,
              "temperature": 26.1,
              "humidity": 25.7,
              "co2": 698,
              "pm25": 97,
              "pm10": 173,
              "tvoc": 188,
              "ch2o": 52
            },
            {
              "created": "2020-04-28 00:00:00",
              "equipmentassetId": 14,
              "collaborationId": 1,
              "temperature": 25.8,
              "humidity": 23.9,
              "co2": 611,
              "pm25": 44,
              "pm10": 79,
              "tvoc": 133,
              "ch2o": 37
            },
            {
              "created": "2020-04-29 00:00:00",
              "equipmentassetId": 14,
              "collaborationId": 1,
              "temperature": 26.6,
              "humidity": 28.2,
              "co2": 742,
              "pm25": 59,
              "pm10": 105,
              "tvoc": 215,
              "ch2o": 60
            },
            {
              "created": "2020-04-29 00:00:00",
              "equipmentassetId": 14,
              "collaborationId": 1,
              "temperature": 26.6,
              "humidity": 28.1,
              "co2": 715,
              "pm25": 53,
              "pm10": 95,
              "tvoc": 198,
              "ch2o": 56
            },
            {
              "created": "2020-04-30 00:00:00",
              "equipmentassetId": 14,
              "collaborationId": 1,
              "temperature": 26.7,
              "humidity": 28.5,
              "co2": 703,
              "pm25": 49,
              "pm10": 88,
              "tvoc": 191,
              "ch2o": 53
            },
            {
              "created": "2020-04-30 00:00:00",
              "equipmentassetId": 14,
              "collaborationId": 1,
              "temperature": 26.7,
              "humidity": 28.5,
              "co2": 703,
              "pm25": 49,
              "pm10": 88,
              "tvoc": 191,
              "ch2o": 53
            }
          ]
        }

## 当前协作空间环境数据  [GET] /logEnvironment/currentEnvironment

+ Description
    + Author Liukai

+ Parameters
    + collaborationSpaceId (long)  协作空间ID (必填)
    + equipmentAssetId (long) 非必填 （最好填入不然自动选择一个）

+ ReturnData
    + temperature (float)  温度  
    + humidity (float)   湿度
    + co2 (float)   co2
    + pm25 (float)   pm2.5
    + pm10 (float)   pm10
    + tvoc (float)   总挥发性有机化合物
    + ch2o (float)   甲醛
              
+ Response 200
    
        {
          "data": {
            "temperature": 26.8,
            "humidity": 28.7,
            "co2": 706,
            "pm25": 54,
            "pm10": 96,
            "tvoc": 192,
            "ch2o": 54
          }
        }
        


## 数据总览-协作空间使用次数接口  [GET] /logUsedTimesElectric/times

+ Description
    + Author Liukai
    + 已经自动排好序了

+ Parameters
    + dateMaxStr (long)  结束日期（格式：yyyy-MM-dd HH:mm:ss）
    + dateMinStr (long) 开始日期 （格式：yyyy-MM-dd HH:mm:ss）
    + organizationId  (long) 机构ID

+ ReturnData
    + collaborationSpaceName (string)  协作空间名  
    + collaborationSpaceId (long)   协作空间id
    + times (int)   次数
    + organizationName (string)   机构名
    + organizationId (long)   机构ID

              
+ Response 200
    
        {
          "data": [
            {
              "collaborationSpaceName": "大会",
              "collaborationSpaceId": 2,
              "times": 34,
              "organizationName": "北京太平宝迪-真实数据(请勿删)",
              "organizationId": 1
            },
            {
              "collaborationSpaceName": "中会",
              "collaborationSpaceId": 1,
              "times": 9,
              "organizationName": "北京太平宝迪-真实数据(请勿删)",
              "organizationId": 1
            }
          ]
        }


## 数据总览-协作空间使用电量接口  [GET]  /logUsedTimesElectric/energy

+ Description
    + Author Liukai
    + 已经自动排好序了

+ Parameters
    + dateMaxStr (long)  结束日期（格式：yyyy-MM-dd HH:mm:ss）
    + dateMinStr (long) 开始日期 （格式：yyyy-MM-dd HH:mm:ss）
    + organizationId  (long) 机构ID

+ ReturnData
    + collaborationSpaceName (string)  协作空间名  
    + collaborationSpaceId (long)   协作空间id
    + powerConsumption (double)   电量合计
    + organizationName (string)   机构名
    + organizationId (long)   机构ID
              
+ Response 200
    
        {
          "data": [
            {
              "collaborationSpaceName": "中会",
              "collaborationSpaceId": 1,
              "powerConsumption": 18.08999,
              "organizationName": "北京太平宝迪-真实数据(请勿删)",
              "organizationId": 1
            },
            {
              "collaborationSpaceName": "大会",
              "collaborationSpaceId": 2,
              "powerConsumption": 3,
              "organizationName": "北京太平宝迪-真实数据(请勿删)",
              "organizationId": 1
            }
          ]
        }

## 数据总览-机构统计（机构详情接口）  [GET]  /Organization


+ ReturnData
    + id (long)  机构ID  
    + enabled (long)   是否开启
    + creator (long)   创建人
    + created (Date)   创建时间
    + modified (long)   修改人
    + parentId (long)  父ID  
    + fullName (string)   机构名
    + logo (string)   logo
    + abbreviation (string)   简称
    + park (string)   园区
    + address (string)   地址
    + contactNumber (string)   联系电话
    + displayOrder (long)   排序
+ Response 200



          {
          "data": [
                {
                  "id": 1,
                  "enabled": 1,
                  "creator": 0,
                  "modifier": 55,
                  "created": "2020-04-09 17:07:25",
                  "modified": "2020-04-28 10:29:56",
                  "parentId": 0,
                  "fullName": "北京太平宝迪-真实数据(请勿删)",
                  "logo": "/api/static/image/1586423198264.jpg",
                  "abbreviation": "北京太平宝迪-真实数据(请勿删)",
                  "park": "北京太平宝迪-真实数据(请勿删)",
                  "address": "北京太平宝迪-真实数据(请勿删)",
                  "contactNumber": "010606055653",
                  "displayOrder": 100
                }
          ]
        }
        
        
        
        
## 数据总览-楼宇统计  [GET]  /building/info

+ ReturnData
    + organizationId (long)  机构ID  
    + organizationName (string)   机构名称
    + total (Integer)   数量
    + id (long)   楼宇ID
    + enabled (long)   是否开启
    + creator (long)  创建人 
    + modifier (long)   修改人
    + created (date)   创建时间
    + modified (date)   修改时间
    + organizationId (long)   机构ID
    + buildingName (string)   楼宇名称
    + displayOrder (Integer)   排序
+ Response 200




       {
       "data": [
                {
                  "organizationId": 1,
                  "organizationName": "北京太平宝迪-真实数据(请勿删)",
                  "total": 1,
                  "data": [
                    {
                      "id": 1,
                      "enabled": 1,
                      "creator": 0,
                      "modifier": 0,
                      "created": "2020-04-09 17:27:44",
                      "modified": "2020-04-09 18:46:45",
                      "organizationId": 1,
                      "buildingName": "北京云谷电子商务产业园2号楼",
                      "displayOrder": 100
                    }
                  ]
                }
          ]
        }
        
        

## 数据总览-协作空间统计  [GET]  /collaborationSpace/info

+ ReturnData
    + organizationId (long)  机构ID  
    + organizationName (string)   机构名称
    + total (Integer)   数量
    + id (long)   楼宇ID
    + enabled (long)   是否开启
    + creator (long)  创建人 
    + modifier (long)   修改人
    + created (date)   创建时间
    + modified (date)   修改时间
    + fullName (string)   协作空间名称
    + logo (string)   logo
    + floorId (long)   楼层ID
    + displayOrder (Integer)   排序
+ Response 200



        {
           "data": [
                       {
                  "organizationId": 7,
                  "organizationName": "耐克运动鞋",
                  "total": 2,
                  "data": [
                    {
                      "id": 4,
                      "enabled": 1,
                      "creator": 51,
                      "modifier": 51,
                      "created": "2020-04-22 10:43:04",
                      "modified": "2020-04-22 10:43:04",
                      "fullName": "中央会议是",
                      "logo": "/api/static/image/1587523378847.png",
                      "floorId": 10,
                      "displayOrder": 100
                    },
                    {
                      "id": 5,
                      "enabled": 1,
                      "creator": 51,
                      "modifier": 51,
                      "created": "2020-04-22 10:43:40",
                      "modified": "2020-04-22 10:44:02",
                      "fullName": "多媒体会议室3",
                      "logo": "/api/static/image/1587523414134.png",
                      "floorId": 12,
                      "displayOrder": 100
                    }
                  ]
                }
          ]
        }



## 数据总览-受控情况统计  [GET]/equipmentasset/info

+ Parameters
    + id (long)  机构ID
   

+ ReturnData
    + organizationId (long) 机构ID  
    + organizationName (string)   机构名称
    + controlled (Integer)   可控设备
    + uncontrollable (Integer)   不可控设备
              
+ Response 200




        {
          "data": [
            {
              "organizationId": null,
              "organizationName": null,
              "controlled": 12,
              "uncontrollable": 0
            }
          ]
        }
        
        
        
## 数据总览-品牌统计  [GET]/brand/info

+ Parameters
    + id (long)  机构ID
   

+ ReturnData
    + id (long) 品牌ID  
    + enabled (Integer)   是否可用
    + creator (Long)    创建人
    + modifier (long)   修改人
    + modified (date) 修改时间
    + created(date)  创建时间
    + brandName (string)   品牌名称
    + logo (string)   logo
    + description (string)   描述
    + website (string) 网址  
    + displayOrder (Integer)   排序
    + total (Integer)   数量
              
+ Response 200




        {
          "data": [
            {
              "id": 1,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-04-08 10:05:31",
              "modified": "2020-04-09 10:05:21",
              "brandName": "Extron",
              "logo": "/api//static/image/1586311163195.png",
              "description": "每天都会有数百万的人们感受着 Extron 视音频信号处理、分配和控制产品所带来的极致体验。我们先进的技术创造了更加清晰的图像、更高品质的声音、更便捷的控制以及更可靠的系统。我们功能强大的资产管理工具也能够帮助技术专家们有效地管理企事业单位中部署的大量视音频系统。",
              "website": "https://www.extron.cn/",
              "displayOrder": 5,
              "total": 9
            }
            ]
        }
        
        
## 数据总览-分类统计  [GET]/category/info

+ Parameters
    + id (long)  机构ID
   

+ ReturnData
    + id (long) 品牌ID  
    + enabled (Integer)   是否可用
    + creator (Long)    创建人
    + modifier (long)   修改人
    + modified (date) 修改时间
    + created(date)  创建时间
    + parentId (long)   父ID
    + categoryName (string)   分类名称
    + description (string)   描述
    + picture (string) 图片  
    + displayOrder (Integer)   排序
    + equipmentAssetTotal (Integer)   数量
              
+ Response 200



        {
          "data": [
            {
              "id": 3,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-04-09 13:56:08",
              "modified": "2020-04-09 13:56:08",
              "parentId": 0,
              "categoryName": "控制",
              "picture": "/api/static/image/1586411757375.png",
              "description": "控制相关设备",
              "displayOrder": 5,
              "equipmentAssetTotal": 0
            }
            ]
            
        }
            
            
            
## 数据总览-控制协议统计  [GET]/controlprotocol/info

+ Parameters
    + id (long)  机构ID
   

+ ReturnData
    + id (long) 协议ID  
    + protocolName (String)   协议名称
    + description (String)    描述
    + equipmentAssetTotal (long)   数量
              
+ Response 200





        {
          "data": [
            {
              "id": 1,
              "protocolName": "网络协议",
              "description": "网络协议1",
              "equipmentAssetTotal": 5
            }]}

## 协作空间统计-次数&电量统计  [GET] /logUsedTimesElectric/energyAndTimesCollaboration
+ Description
    + Author Liukai

+ Parameters
    + dateStr (string) 日期  格式：yyyy-MM-dd
    + collaborationId (long) 协作空间ID
    + dateType (int)  日期类型 时间类型 0：年， 1：月，2：周

+ ReturnData
    + weekYearMonth (int)  哪周/哪月/哪年
    + eneryValueSum (double) 本月/本年/本周电量
    + times (int)  本月/本年/本周 使用次数
    + timesTb (double)    次数同比率
    + eneryValueTb (double)  电量同比率
    + timesHb (double)     次数环比率
    + eneryValueHb (double) 电量环比率
    + logUsedTimesElectricList
        +  created  (date) 时间
        +  times (int)  次数
        +  powerConsumption  (double)
              
+ Response 200

        {
          "data": {
            "weekYearMonth": 5,
            "eneryValueSum": 12.32,
            "times": 6,
            "timesTb": 0,
            "eneryValueTb": 120.00000000000001,
            "timesHb": 500,
            "eneryValueHb": 1132,
            "logUsedTimesElectricList": [
              {
                "id": 2,
                "created": "2020-05-02 00:00:00",
                "organizationId": 1,
                "collaborationId": 1,
                "times": 0,
                "powerConsumption": 6.96
              },
              {
                "id": 3,
                "created": "2020-05-01 00:00:00",
                "organizationId": 1,
                "collaborationId": 1,
                "times": 0,
                "powerConsumption": 0
              },
              {
                "id": 4,
                "created": "2020-05-03 00:00:00",
                "organizationId": 1,
                "collaborationId": 1,
                "times": 2,
                "powerConsumption": 1.13001
              },
              {
                "id": 5,
                "created": "2020-05-04 00:00:00",
                "organizationId": 1,
                "collaborationId": 1,
                "times": 1,
                "powerConsumption": 2.11
              },
              {
                "id": 6,
                "created": "2020-05-05 00:00:00",
                "organizationId": 1,
                "collaborationId": 1,
                "times": 0,
                "powerConsumption": 2.11999
              },
              {
                "id": 7,
                "created": "2020-05-06 00:00:00",
                "organizationId": 1,
                "collaborationId": 1,
                "times": 3,
                "powerConsumption": 0
              }
            ]
          }
        }

## 协作空间统计-使用次数排名(协作空间)&故障报警排名(协作空间) [GET] /logEquipmentMalfunction/timesAndMalfunction
+ Description
    + Author Liukai

+ Parameters
    + dateStr (string) 日期  格式：yyyy-MM-dd
    + collaborationId (long) 协作空间ID
    + dateType (int)  日期类型 时间类型 0：年， 1：月，2：周
    + rankId (int) 排序 :0 次数 1 故障, 默认值是次数0

+ ReturnData
    + logEquipmentMalfunctionList
        +  equipmentassetId (long)  资产设备ID
        +  malfunctionTimes (int)  故障次数
        +  useTimes  (int)  使用次数
        +  equipmentName  (string)  设备名字
        +  equipmentModel (string) 设备型号
        +  categoryName (string)  分类名字
        +  categoryId (long)  分类ID
              
+ Response 200

        {
          "data": {
            "logEquipmentMalfunctionList": [
              {
                "equipmentassetId": 1,
                "malfunctionTimes": 5,
                "useTimes": 55,
                "equipmentName": "中控设备1",
                "equipmentModel": "zk1",
                "categoryName": "extron中控",
                "categoryId": 20
              },
              {
                "equipmentassetId": 3,
                "malfunctionTimes": 2,
                "useTimes": 4,
                "equipmentName": "黑色摄像头",
                "equipmentModel": "1566-78",
                "categoryName": "圆形摄像头",
                "categoryId": 16
              },
              {
                "equipmentassetId": 4,
                "malfunctionTimes": 0,
                "useTimes": 0,
                "equipmentName": "ex投影幕布",
                "equipmentModel": "884823-985",
                "categoryName": "投影幕布",
                "categoryId": 17
              },
              {
                "equipmentassetId": 20,
                "malfunctionTimes": 0,
                "useTimes": 0,
                "equipmentName": "法拉利2020",
                "equipmentModel": "2020",
                "categoryName": "01音箱",
                "categoryId": 12
              },
              {
                "equipmentassetId": 7,
                "malfunctionTimes": 0,
                "useTimes": 0,
                "equipmentName": "ex投影幕布",
                "equipmentModel": "884823-985",
                "categoryName": "投影幕布",
                "categoryId": 17
              },
              {
                "equipmentassetId": 9,
                "malfunctionTimes": 0,
                "useTimes": 0,
                "equipmentName": "海林空调",
                "equipmentModel": "HL-1525",
                "categoryName": "空调",
                "categoryId": 23
              },
              {
                "equipmentassetId": 13,
                "malfunctionTimes": 0,
                "useTimes": 0,
                "equipmentName": "圆筒灯",
                "equipmentModel": "IS-10023",
                "categoryName": "筒灯",
                "categoryId": 15
              }
            ]
          }
        }



## 协作空间统计-使用年限统计[GET] /equipmentasset/ageLimitInfo

+ ReturnData
    + ageLimit (int) 使用年限(1,2,3,4,5,6)
    + category
        +  id (long)  分类ID
        +  enabled (int)  是否启用
        +  creator  (Long)  创建人
        +  modifier  (long)  修改人
        +  created (date) 创建日期
        +  modified (date)  修改日期
        +  parentId (long)  父ID
        +  categoryName  (string)  分类名字
        +  picture (string) 图片
        +  description (string)  描述
        +  displayOrder (long)  排序
      + equipment
        +  id (long)  设备ID
        +  enabled (int)  是否启用
        +  creator  (Long)  创建人
        +  modifier  (long)  修改人
        +  created (date) 创建日期
        +  modified (date)  修改日期
        +  equipmentName (string)  设备名称
        +  model  (string)  设备型号
        +  picture (string) 图片
        +  categoryId (int)  设备分类ID
        +  brandId (int)  品牌id
        +  controllable  (int)  是否可控
        +  readable (int) 是否可读 0不可读 1可读
        +  communicationMode (int)  通信方式，0：单向，1：双向
        +  lifeType (int)  寿命类型，0：时长，1：次数'
        +  recommendedLife  (int)  建议寿命
        +  warrantyPeriod (int) 质保期限
        +  maintenanceFrequency (int)  保养频率，单位：月'
        +  webLink (string)  产品链接
        +  centerControlUnit (int)  是否是中控  0非中控 1是中控
     + total (int) 数量
              
+ Response 200

            {
            "data": [
                "ageLimit": 2,
              "category": [
                {
                  "id": 15,
                  "enabled": 1,
                  "creator": 43,
                  "modifier": 43,
                  "created": "2020-04-17 19:13:30",
                  "modified": "2020-04-17 19:13:30",
                  "parentId": 14,
                  "categoryName": "筒灯",
                  "picture": "/api/static/image/1587121999040.jpg",
                  "description": "圆形灯具",
                  "displayOrder": 100
                }
              ],
              "equipment": [
                {
                  "id": 2,
                  "enabled": 1,
                  "creator": 43,
                  "modifier": 43,
                  "created": "2020-04-17 18:27:26",
                  "modified": "2020-04-22 18:25:06",
                  "equipmentName": "圆筒灯",
                  "model": "IS-10023",
                  "picture": "/api/static/image/1587119209780.jpg",
                  "categoryId": 15,
                  "brandId": 1,
                  "controllable": 1,
                  "readable": 0,
                  "communicationMode": 0,
                  "lifeType": 1,
                  "recommendedLife": 1,
                  "warrantyPeriod": 3,
                  "maintenanceFrequency": 6,
                  "webLink": "www.budee.com",
                  "centerControlUnit": 0
                }
              ],
              "total": 1
            }
             ]
            }
