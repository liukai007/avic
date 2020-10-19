# AVIC网关 接口文档

+ 2020年4月24日
    + 网关基本信息修改
    + 网关基本信息详情

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

   
### 网关基本信息修改 [PATCH] /gatewayInfo/{id}

+ Description
    + Author Liukai
    
+ Parameters
    + id (long) 网关设备ID
    
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
