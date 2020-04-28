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
    + readtypeName  (string) 读数类型名
    + readValueType  (int) 读数值返回的类型(0 字符串类型 1 整数型 2 float型)
    + returnValue  (string) 返回值组(用英文逗号隔开不同的返回值)
    + enabled (int)  - 使能  0禁止 1启用
    + creator (long) - 创建人
    + modifier (long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间

   
### 新增读数类型 [POST] /readType

+ Description
    + Author Liukai
+ Request (application/json)

        {
          "data": {
            "readtypeName": "是否占用1",
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
            "id": 1,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2020-04-26 18:04:19",
            "modified": "2020-04-26 18:04:26",
            "readtypeName": "co2",
            "readValueType": 2
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
            "totalElements": 2,
            "size": 10,
            "number": 1,
            "numberOfElements": 2,
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
              "readtypeName": "co2",
              "readValueType": 2
            },
            {
              "id": 2,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-04-26 18:04:17",
              "modified": "2020-04-26 18:04:22",
              "readtypeName": "是否占用",
              "readValueType": 0,
              "returnValue": "on,off"
            }
          ]
        }
