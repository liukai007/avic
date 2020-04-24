# AVIC迭代3管理端接口文档

+ 2020年4月24日
    + 新增智能场景
    + 删除智能场景
    + 修改智能场景
    + 查询智能场景详情
    + 查询智能场景列表


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

+ Response 204 

        
### 修改智能场景 [PATCH] /intelligentScene/{id}

+ Description


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
比如：http://127.0.0.1:8080/intelligentScene?page[number]=1&page[size]=10&filter[sceneName:like]=%%E8%87%AA%
+ Description

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
              "opened": 1
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
              "opened": 1
            }
          ]
        }


 

