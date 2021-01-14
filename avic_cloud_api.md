# AVIC云网关 接口文档
https://github.com/liukai007/avic/edit/master/avic_cloud_api.md

+ 2020年01月14日
    + 驱动列表
    + 驱动新增
    + 驱动修改
    + 驱动删除
    + 网关列表
    + 网关注册
    + 网关删除
    + 设备添加
    + 设备资产列表
    + 设备状态监测
    + 设备保养列表
    + 设备寿命列表
    + 网关统计
    + 设备统计
    + 品牌统计
    + 分类统计
    + 控制协议统计
    + 受控情况统计
    + 资产使用情况
    + 空间使用排行
    + 资产排名
    + 空间能耗统计
    + 设备使用排行top10
    + 设备状态监测


### 驱动列表 [GET] /drive
+ Description

+ Parameters
    + data
        + belong (int)  0 本地 1 云端
        + equipmentName （string）设备名
        + filter[brandId] (long) 品牌id
        + filter[primaryCategoryId] (long)  一级分类id
        + filter[secondCategoryId] (long)   二级分类id
        + model （string）型号
        + firmware (string) 固件号
        + include (Array[string])
        + page[number] （int）页码
        + page[size] （int）条数
        + sort （Array[string]） 排序
        
+ Request (application/json)

+ ReturnData
    + id （long） 端口类型id
    + enabled （int）是否启用
    + creator （long）创建人
    + modifier （long）修改人
    + gatewayGid （long）本地驱动id
    + updateVersionId （long）更新版本id
    + equipmentName （string） 设备名称
    + model （string）型号
    + ispdu （int）是否pdu
    + severalPdu (int) 几口PDU
    + ycategoryId （long） 分类id
    + ybrandId （long）品牌id
    + lifeType (int) 寿命类型 0 时间 1 次
    + belong （int）本地 是0   云端是1
    + communicationMode （int） 通信方式，0：单向，1：双向  默认值是1
    + officialCertification (int) 官方认证是1  非官方认证是0
    + operation （int）0 无操作  1已上传  2下载 3 已下载（操作）
    + brandName （string） 品牌名
    + primaryCategoryName (string) 一级类名
    + secondCategoryName  （string) 二级类名
    + builtIn (int) 1内置  1内置的必须超级管理员才能修改
    + firmware （string）固件号
        
        
+ Response 200
    
        {
          "data": [
            {
              "id": 2,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-11 15:01:46",
              "modified": "2021-01-11 15:01:50",
              "gatewayGid": 2,
              "equipmentNameEn": "音频驱动",
              "equipmentName": "音频驱动",
              "model": "EXTRON",
              "ispdu": 0,
              "severalPdu": 0,
              "belong": 0,
              "officialCertification": 0,
              "operation": 0,
              "lifeType": 0,
              "communicationMode": 1,
              "builtIn": 0,
              "secondCategoryName": "温湿度类",
              "primaryCategoryName": "环境",
              "ycategoryId": 6,
              "ybrandId": 3
            },
            {
              "id": 3,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-14 10:24:53",
              "modified": "2021-01-14 10:24:55",
              "gatewayGid": 3,
              "equipmentNameEn": "测试驱动01",
              "equipmentName": "测试驱动01",
              "model": "AAAAA",
              "ispdu": 0,
              "severalPdu": 0,
              "belong": 0,
              "officialCertification": 0,
              "operation": 0,
              "lifeType": 1,
              "communicationMode": 1,
              "builtIn": 0,
              "brandName": "海林",
              "secondCategoryName": "环境",
              "ycategoryId": 2,
              "ybrandId": 2
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


### 驱动新增 [POST] /drive
+ Parameters
    + data
        + equipmentName （string） 设备名称
        + model （string）设备型号
        + ybrandId （long）品牌id
        + lifeType (int) 寿命类型 0 时间 1 次
        + recommended_life （string）建议使用寿命 次/小时
        + portTypeId  （long）接入网关协议id
        + communicationMode （int） 通信方式，0：单向，1：双向  默认值是1
        + ycategoryId （long） 分类id
        + warrantyPeriod (int) 质保期（年）
        + maintenanceFrequency （int）保养频率（月）
        + cmd_drive （json字符串） 驱动文件,例如:{'name':'xxx'} 
        + picture （string） 型号图片
+ Request (application/json)

        {
          "data": {
            "cmdDrive": {'data':'controll':'1111'}",
            "communicationMode": 1,
            "equipmentName": "摄像头驱动",
            "firmware": "固件号123",
            "lifeType": 0,
            "maintenanceFrequency": 18,
            "model": "型号：大华",
            "picture": "https://www.baidu.com",
            "portTypeId": 1,
            "recommendedLife": 1000, 
            "warrantyPeriod": 2,
            "ybrandId": 1,
            "ycategoryId": 5
          }
        }
+ Response 201

        {
          "data": {
            "id": 4,
            "type": "drive"
          }
        }

## 驱动修改  [PATCH]  /drive/{id}

+ Parameters
    + data
        + equipmentName （string） 设备名称
        + model （string）设备型号
        + ybrandId （long）品牌id
        + lifeType (int) 寿命类型 0 时间 1 次
        + recommended_life （string）建议使用寿命 次/小时
        + portTypeId  （long）接入网关协议id
        + communicationMode （int） 通信方式，0：单向，1：双向  默认值是1
        + ycategoryId （long） 分类id
        + warrantyPeriod (int) 质保期（年）
        + maintenanceFrequency （int）保养频率（月）
        + cmd_drive （json字符串） 驱动文件,例如:{'name':'xxx'} 
        + picture （string） 型号图片

+ Request (application/json)

        {
          "data": {
            "cmdDrive": {'data':'controll':'1111'}",
            "communicationMode": 1,
            "equipmentName": "摄像头驱动",
            "firmware": "固件号123",
            "lifeType": 0,
            "maintenanceFrequency": 18,
            "model": "型号：大华",
            "picture": "https://www.baidu.com",
            "portTypeId": 1,
            "recommendedLife": 1000, 
            "warrantyPeriod": 2,
            "ybrandId": 1,
            "ycategoryId": 5
          }
        }
        
+ Response 200

## 驱动删除  [DELETE]  /drive/{id}

+ Parameters
    + id (long)驱动id
      

+ Request (application/json)
        
+ Response 204


### 网关列表 [GET] /gatewayinfo
+ Description

+ Parameters
    + data
        + filter[gatewayName] (string)  网关名称
        + include (Array[string])
        + page[number] （int）页码
        + page[size] （int）条数
        + sort （Array[string]） 排序
        
+ Request (application/json)

+ ReturnData
    + id （long） 端口类型id
    + enabled （int）是否启用
    + creator （long）创建人
    + modifier （long）修改人
    + gatewayGid （long）本地驱动id
    + onlyCode （long）网关sn码
    + ipAddress （string） 网关ip地址
    + gatewayName （string）网关名称
    + organizationName （string） 机构名称
    + runningStatus （int）1 网关运行状态
    + spaceName (int) 协作空间名称
    + activeStartTime （string） 网关激活时间
    + activeEndTime (string) 网关激活截止时间
    + runTime （long）运行时长
    + yequipmentId
        
+ Response 200
    
        {
          "data": [
            {
                  "id": 1,
                  "enabled": 1,
                  "creator": 0,
                  "modifier": 0,
                  "created": "2021-01-11 13:52:23",
                  "modified": "2021-01-11 13:52:26",
                  "gatewayGid": 1,
                  "onlyCode": "YYYYEEEEE",
                  "ipAddress": "192.168.1.1",
                  "gatewayName": "中会议室网关",
                  "organizationName": "太平宝迪科技责任有限公司",
                  "serviceConfReg": 0,
                  "serviceCoreData": 0,
                  "serviceMetadata": 0,
                  "serviceCommand": 0,
                  "runningStatus": 1,
                  "conferenceReservationStatistics": 0,
                  "specializedAssetId": 0,
                  "activate": 1,
                  "spaceEntiy": {
                    "id": 1,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "spaceName": "中会",
                    "floorId": 1,
                    "displayOrder": 100
                  },
                  "gatewayActiveTime": {
                    "id": 2,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2020-12-30 16:06:21",
                    "modified": "2021-01-14 14:22:10",
                    "gatewayEquipmentId": 1,
                    "activeStartTime": "2020-12-30T08:06:21.000+0000",
                    "activeEndTime": "2021-01-30T08:06:21.000+0000",
                    "expire": 0,
                    "isSuccess": 0
                  },
                  "runTime": 744,
                  "yequipmentId": 1
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

 
### 网关注册/新增 [POST] /spacegateway
+ Parameters
    + data
        + filter[gatewayName] （string） 网关名称
        + filter[gatewaySn] （string）网关SN码
        + filter[spaceid] （string） 协作空间id
       
+ Request (application/json)

+ Response 201

        {
          "data": {
            "id": 4,
            "type": "drive"
          }
        }

## 网关删除  [DELETE]  /gatewayinfo/{id}

+ Parameters
    + id (long)网关id
      
+ Request (application/json)
        
+ Response 204        


### 设备添加 [POST] /equipment
+ Description

+ Parameters
    + data
        + anotherName (string)  别名
        + builtIn （int） 是否内置 1为内置 0为非内置
        + ycategoryId (long) 分类id
        + yequipmentIdGateway （long）网关ID
        + yporttypeId （long）端口类型id
        + ydriveId （long）驱动id
        + ypduId
        + ybrandId
        + controllable （int）是否可控 1 可控  0 不可控
        + equipmentName （string）中午名
        + equipmentNameEn （string）英文名
        + fixedAttribute （int）关联空间属性（0 无固定属性，1为环境  2 占位 3 能耗）
        + functionCode （int）0 无功能  1 是次数  2 是电表记录'
        + ispdu （int）0 非pdu 1是pdu
        + maintainData （date）保养日期
        + maintenanceTelephone （string）维修电话
        + online （int）是否在线：0 离线 1在线 2未知
        + otherStatus （string）其他数据 json格式
        + pduPortName （string）物理端口名
        + picture (string) 图片
        + portConfigContent （string）示例("{'HTTP':'192.168.1.2'}")
        + purchaseDate （date）采购日期
        + runningStatus （int）运行状态0关闭 1运行 2警告    3故障  4其他',
        + serialNumber （string）设备序列号
        + serviceDate （date）投入使用日期
        + supplier （string）供应商
        + pdus
            + anotherName （string）别名
            + cmdCodeOff （string）关命令core
            + cmdCodeOn （string）开命令core
            + electricCurrent （float）电流
            + intervalValue （long） 时间间隔
            + onOffState （int）'开关状态 1为开 0为关  2为未知状态
            + power （float）功率
            + pduPortNo （int）端口号
            + voltage （float）电压
            
        
+ Request (application/json)

+ ReturnData

        {
          "data": {
            "id": 4,
            "type": "equipment"
          }
        }
        
+ Response 201
       
+ Response 400
    
        {
          "errors": [
            {
              "status": "400",
              "title": "Bad Request"
            }
          ]
        } 



### 设备资产列表 [GET] /equipment/equipmentAssetOrMonitorOrMaintainOrLife

+ Description

+ Parameters
    + data
        + filter[gatewayid] (int)  网关id
        + filter[brandid] （int）品牌id
        + filter[primaryCategoryId] (long)  一级分类id
        + filter[secondCategoryId] (long)   二级分类id
        + filter[equipmentName] 设备名称）
        + filter[driveType] (string) 驱动型号
        + include (Array[string])
        + page[number] （int）页码
        + page[size] （int）条数
        + sort （Array[string]） 排序
        
+ Request (application/json)

+ ReturnData



### 设备状态监测 [GET] /equipment/equipmentAssetOrMonitorOrMaintainOrLife

+ Description

+ Parameters
    + data
        + filter[gatewayid] (int)  网关id
        + filter[brandid] （int）品牌id
        + filter[primaryCategoryId] (long)  一级分类id
        + filter[secondCategoryId] (long)   二级分类id
        + filter[equipmentName] 设备名称）
        + filter[driveType] (string) 驱动型号
        + filter[online] (int)  是否在线
        + filter[runningStatus] （int）运行状态
        + include (Array[string])
        + page[number] （int）页码
        + page[size] （int）条数
        + sort （Array[string]） 排序
        
+ Request (application/json)

+ ReturnData 
+ 
       {
          "data":  {
              "id": 1,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-14 17:01:00",
              "modified": "2021-01-14 17:01:00",
              "gatewayGid": 1,
              "flag": 0,
              "equipmentName": "网关",
              "equipmentNameEn": "网关",
              "anotherName": "网关",
              "online": 1,
              "runningStatus": 1,
              "otherStatus": "1",
              "purchaseDate": "2021-01-01T02:48:40.000+0000",
              "serviceDate": "2020-12-01T09:15:48.000+0000",
              "brandName": "DingDee",
              "portConfigContent": "1",
              "ispdu": 0,
              "controllable": 1,
              "builtIn": 0,
              "fixedAttribute": 0,
              "functionCode": 0,
              "lifetype": 1,
              "recommendedLife": 1,
              "totalTime": 0,
              "stateOfLife": 1,
              "readable": 0,
              "driveCmds": [],
              "gatewayName": "小会议室网关",
              "model": "485-RTU",
              "secondCategoryName": "音频",
              "ageLimit": 1,
              "yporttypeId": 1,
              "ydriveId": 1,
              "ycategoryId": 5,
              "ybrandId": 1,
              "yequipmentIdGateway": 2,
              "ypduId": 1
           }
   }

### 设备保养列表 [GET] /equipment/equipmentAssetOrMonitorOrMaintainOrLife

+ Description

+ Parameters
    + data
        + filter[readStaus] (int)  是否已读
        + filter[useYear] （int）使用年限
        + filter[maintainStart] (string)  开始保养日期,日期，格式：yyyy-MM-dd
        + filter[maintainEnd] (long)   结束保养日期,日期，格式：yyyy-MM-dd
        + include (Array[string])
        + page[number] （int）页码
        + page[size] （int）条数
        + sort （Array[string]） 排序
        
+ Request (application/json)

+ ReturnData 
+
         {
          "data":  {
              "id": 1,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-14 17:01:00",
              "modified": "2021-01-14 17:01:00",
              "gatewayGid": 1,
              "flag": 0,
              "equipmentName": "网关",
              "equipmentNameEn": "网关",
              "anotherName": "网关",
              "online": 1,
              "runningStatus": 1,
              "otherStatus": "1",
              "purchaseDate": "2021-01-01T02:48:40.000+0000",
              "serviceDate": "2020-12-01T09:15:48.000+0000",
              "brandName": "DingDee",
              "portConfigContent": "1",
              "ispdu": 0,
              "controllable": 1,
              "builtIn": 0,
              "fixedAttribute": 0,
              "functionCode": 0,
              "lifetype": 1,
              "recommendedLife": 1,
              "totalTime": 0,
              "stateOfLife": 1,
              "readable": 0,
              "driveCmds": [],
              "gatewayName": "小会议室网关",
              "model": "485-RTU",
              "secondCategoryName": "音频",
              "ageLimit": 1,
              "yporttypeId": 1,
              "ydriveId": 1,
              "ycategoryId": 5,
              "ybrandId": 1,
              "yequipmentIdGateway": 2,
              "ypduId": 1
           }
   }


### 设备寿命列表 [GET] /equipment/equipmentAssetOrMonitorOrMaintainOrLife

+ Description

+ Parameters
    + data
        + filter[lifeState] (int)  寿命状态
        + filter[lifeType] （int）寿命类型
        + include (Array[string])
        + page[number] （int）页码
        + page[size] （int）条数
        + sort （Array[string]） 排序
        
+ Request (application/json)

+ ReturnData 
+ 
         {
          "data":  {
              "id": 1,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-14 17:01:00",
              "modified": "2021-01-14 17:01:00",
              "gatewayGid": 1,
              "flag": 0,
              "equipmentName": "网关",
              "equipmentNameEn": "网关",
              "anotherName": "网关",
              "online": 1,
              "runningStatus": 1,
              "otherStatus": "1",
              "purchaseDate": "2021-01-01T02:48:40.000+0000",
              "serviceDate": "2020-12-01T09:15:48.000+0000",
              "brandName": "DingDee",
              "portConfigContent": "1",
              "ispdu": 0,
              "controllable": 1,
              "builtIn": 0,
              "fixedAttribute": 0,
              "functionCode": 0,
              "lifetype": 1,
              "recommendedLife": 1,
              "totalTime": 0,
              "stateOfLife": 1,
              "readable": 0,
              "driveCmds": [],
              "gatewayName": "小会议室网关",
              "model": "485-RTU",
              "secondCategoryName": "音频",
              "ageLimit": 1,
              "yporttypeId": 1,
              "ydriveId": 1,
              "ycategoryId": 5,
              "ybrandId": 1,
              "yequipmentIdGateway": 2,
              "ypduId": 1
           }
   }



