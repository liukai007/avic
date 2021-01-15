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
    + 资产排名
    + 设备状态监测

+ 2020年01月15日
    + 机构新增
    + 机构禁用
    + 机构更新
    + 机构详情
    + 机构列表
    + 空间能耗统计
    + 设备使用排行
    + 空间使用排行
    + 设备资产排行
    + 楼宇新增
    + 楼宇删除
    + 楼宇更新
    + 楼宇详情
    + 楼宇列表
    + 资产使用情况-寿命展示
    + 资产使用情况-使用年限
    
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


## 设备状态监测  [GET]  /equipmentstatusmonitoring

+ Description
    + Author yhz

+ Parameters

+ ReturnData
    + runningCount （int）总设备运行数量
    + closeCount （int）总设备关闭数量
    + warnCount （int）总设备警告数量
    + faultCount (int) 总故障设备数量
    + controlledEquipment （int）可控设备数量
    + totalEquipment (int) 总设备数
    + equipmentStatusMonitoringList
        + runningNumber （int）设备运行数量
        + closeNumber （int）设备关闭数量
        + warnNumber （int）设备警告数量
        + faultNumber (int) 故障设备数量
        + onLine （int）在线数量
        + offLine （int）离线数量
              
+ Response 200

        {
          "data": {
            "runningCount": 15,
            "closeCount": 8,
            "warnCount": 5,
            "faultCount": 9,
            "controlledEquipment": 6,
            "totalEquipment": 0
            "equipmentStatusMonitoringList": [
              {
                "id": 1,
                "creator": 0,
                "created": "2021-01-14 15:25:00",
                "runningNumber": 10,
                "closeNumber": 10,
                "warnNumber": 2,
                "faultNumber": 3,
                "onLine": 10,
                "offLine": 15
              },
              {
                "id": 1,
                "creator": 0,
                "created": "2021-01-14 15:25:00",
                "runningNumber": 10,
                "closeNumber": 10,
                "warnNumber": 2,
                "faultNumber": 3,
                "onLine": 10,
                "offLine": 15
              }
            ]
          }
        }

## 机构管理
+ Data
    + ID  (long)  - ID
    + parentId (long) - 父ID
    + parentName  (string) -上级机构名称
    + fullName (string) - 全称
    + logo (string) - logo
    + abbreviation  (string) - 简称
    + park (string) - 位置
    + address (string) - 地址
    + contactNumber (string) - 电话号码
    + displayOrder (int) - 排序 
    + enabled (int)  - 使能  0禁止 1启用
    + creator (long) - 创建人
    + modifier (long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间

###  机构新增 [POST]  /organization
+ Description
    + Author Liukai
+ Request (application/json)

        {
          "data": {
            "parentId": 0,
            "fullName": "上海新瑞客科技有限公司",
            "logo": "https://static.mifanxing.com/article/image/31/84/5512991.jpg",
            "abbreviation": "简写",
            "park": "测试park",
            "address": "上海",
            "contactNumber": "13126822398",
            "displayOrder": 100
          }
        }

+ Response 201

    {
      "data": {
        "id": 22,
        "type": "organization"
      }
    }

+ Response 400
    
        {
          "errors": [
            {
              "status": "400",
              "code": "手机/电话号码格式不正确",
              "title": "Bad Request",
              "detail": "手机/电话号码格式不正确",
              "source": {
                "pointer": "Organization -> contactNumber"
              }
            }
          ]
        }


        {
          "errors": [
            {
              "status": "400",
              "code": "全称不能为空",
              "title": "Bad Request",
              "detail": "全称不能为空",
              "source": {
                "pointer": "Organization -> fullName"
              }
            }
          ]
        }
   
   
###  机构禁用 [DELETE]  /organization/{id}
+ Description
    + Author Liukai
+ Parameters
    + id (long) - id 
+ Response 204 


### 机构更新 [PATCH] /organization/{id}   
+ Description
    + Author Liukai 
+ Parameters
    + id (long) - id 
+ Response 200
    
        {
          "data": {
            "parentId": 0,
            "fullName": "上2海新瑞客科技有限公司",
            "logo": "https://static.mifanxing.com/article/image/31/84/5512991.jpg",
            "abbreviation": "简写1",
            "park": "测试park1",
            "address": "上海",
            "contactNumber": "13126822398",
            "displayOrder": 100
          }
        }

###  机构详情 [GET] /organization/{id}  
+ Description
    + Author Liukai 
+ Parameters
    + id (long) - id  
+ Response 200
    
        {
          "data": {
            "id": 22,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2021-01-15 11:38:38",
            "modified": "2021-01-15 11:51:27",
            "parentId": 0,
            "fullName": "上2海新瑞客科技有限公司",
            "logo": "https://static.mifanxing.com/article/image/31/84/5512991.jpg",
            "abbreviation": "简写1",
            "park": "测试park1",
            "address": "上海",
            "contactNumber": "13126822398",
            "displayOrder": 100
          }
        }

### 机构列表 [GET] /organization
+ Demo
    + /organization?sort=displayOrder,-modified&filter[fullName:like]=%公司%&page[number]=1&page[size]=10
+ Description
    + Author Liukai
+ Parameters
    + page[number] (int)  -页码
    + page[size]   (int)  -条数
    + sort  (string) -排序 例如 sort=displayOrder,-modified
    + filter[fullName:like] (string) -全名 例如 filter[fullName:like]=%公司%
+ Response 200
    
        {
          "meta": {
            "totalPages": 3,
            "totalElements": 12,
            "size": 5,
            "number": 1,
            "numberOfElements": 5,
            "first": true,
            "last": false,
            "sort": null
          },
          "links": {
            "self": "/organization?page[number]=1&page[size]=5",
            "first": "/organization?page[number]=1&page[size]=5",
            "next": "/organization?page[number]=2&page[size]=5",
            "last": "/organization?page[number]=3&page[size]=5"
          },
          "data": [
            {
              "id": 1,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-04 13:43:37",
              "modified": "2021-01-04 13:43:34",
              "parentId": 0,
              "fullName": "太平宝迪",
              "logo": "https://static.mifanxing.com/article/image/31/84/5512991.jpg",
              "abbreviation": "简写",
              "park": "测试park",
              "address": "北京方庄1",
              "contactNumber": "13126822398",
              "displayOrder": 100
            },
            {
              "id": 2,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-04 13:44:19",
              "modified": "2021-01-04 13:44:22",
              "parentId": 1,
              "fullName": "北京鼎迪",
              "logo": "https://static.mifanxing.com/article/image/31/84/5512991.jpg",
              "abbreviation": "简写",
              "park": "测试park",
              "address": "北京方庄2",
              "contactNumber": "13126822398",
              "displayOrder": 100,
              "parentName": "太平宝迪"
            },
            {
              "id": 3,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-04 13:45:02",
              "modified": "2021-01-04 13:45:05",
              "parentId": 1,
              "fullName": "杭州办事处",
              "logo": "https://static.mifanxing.com/article/image/31/84/5512991.jpg",
              "abbreviation": "简写",
              "park": "测试park",
              "address": "北京方庄2",
              "contactNumber": "13126822398",
              "displayOrder": 100,
              "parentName": "太平宝迪"
            },
            {
              "id": 4,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-04 13:45:23",
              "modified": "2021-01-04 13:45:26",
              "parentId": 1,
              "fullName": "东北办事处",
              "logo": "https://static.mifanxing.com/article/image/31/84/5512991.jpg",
              "abbreviation": "简写",
              "park": "测试park",
              "address": "北京方庄2",
              "contactNumber": "13126822398",
              "displayOrder": 100,
              "parentName": "太平宝迪"
            },
            {
              "id": 10,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-14 18:04:23",
              "modified": "2021-01-15 11:17:16",
              "parentId": 0,
              "fullName": "上海银十通科技有限公司221",
              "logo": "https://static.mifanxing.com/article/image/31/84/5512991.jpg",
              "abbreviation": "简写",
              "park": "测试park",
              "address": "北京方庄2122",
              "contactNumber": "13126822398",
              "displayOrder": 100
            }
          ]
        }
        
        ### 空间能耗统计 [GET] /logUsedTimesElectric/eneryStatistics
+ Description
    + Author lyf

+ Parameters
    + dateMinStr (string)  开始日期 格式：yyyy-MM-dd HH:mm:ss
    + dateMaxStr (string)  结束日期 格式：yyyy-MM-dd HH:mm:ss

+ ReturnData
    + powerConsumption (Integer) 总能耗
    + powerConsumptionHb (double) 能耗环比
    + totalWorkPowerConsumption (double)  总工作能耗
    + totalRestPowerConsumption (double)   总非工能耗
    + logUsedTimesElectricList
        + id （long）id
        + created （date） 创建时间
        + times （int） 使用次数
        + powerConsumption (double) 当日耗电量
        + duration (double) 使用时长
        + restPowerConsumption （double）非工能耗
        + workPowerConsumption （double）工作能耗
    + logEnergyGeneralList
        + voltage （double）电压
        + current （double）电流
        + power （double）功率
        + currentElectricValue （double）耗电量
        + analyzed （int）是否已经分析 0未分析  1分析
        + equipmentName （string）设备名称
        + yequipmentId （long）设备id

+ Response 200

            {
              "data": {
                "powerConsumption": 15,
                "powerConsumptionHb": 200,
                "totalWorkPowerConsumption": 10,
                "totalRestPowerConsumption": 5,
                "logUsedTimesElectricList": [
                  {
                    "id": 6,
                    "created": "2021-01-12 07:06:05",
                    "times": 2,
                    "powerConsumption": 10,
                    "duration": 5,
                    "groupingDate": "2021-01-12",
                    "restPowerConsumption": 5,
                    "workPowerConsumption": 15
                  }
                ],
                "logEnergyGeneralList": [
                  {
                    "id": 2,
                    "created": "2021-01-12 16:46:33",
                    "voltage": 1,
                    "current": 1,
                    "power": 1,
                    "currentElectricValue": 4,
                    "analyzed": 0,
                    "equipmentName": "云端新增0000",
                    "yequipmentId": 1
                  },
                  {
                    "id": 4,
                    "created": "2021-01-12 17:48:49",
                    "voltage": 1,
                    "current": 1,
                    "power": 1,
                    "currentElectricValue": 1,
                    "analyzed": 0,
                    "equipmentName": "云端新增0000",
                    "yequipmentId": 2
                  }
                ]
              }
            }



### 设备使用排行 [GET]/logEquipmentMalfunction/timesAndMalfunction
+ Description
    + Author lyf

+ Parameters
    + dateMinStr (string)  开始日期 格式：yyyy-MM-dd HH:mm:ss
    + dateMaxStr (string)  结束日期 格式：yyyy-MM-dd HH:mm:ss
    + rankId (int) 0 按使用时长 1  按故障次数

+ ReturnData
    + logEquipmentMalfunctionList
        + useTimes （long）使用次数
        + malfunctionTimes （long） 故障次数
        + duration （double） 使用时长
        + spaceName (string ) 协作空间名称
        + categoryId (long) 分类id
        + equipmentModel （string）设备型号
        + categoryName （string）分类名称
        + anotherName (string) 设备别名
        + usageRate （double） 使用率
        + yequipmentId （long）设备id

+ Response 200
        
        {
          "data": {
                "logEquipmentMalfunctionList": [
                      {
                        "useTimes": 20,
                        "malfunctionTimes": 5,
                        "duration": 3.5,
                        "equipmentName": "网关1",
                        "categoryId": 16,
                        "equipmentModel": "string",
                        "categoryName": "次类1",
                        "anotherName": "string",
                        "usageRate": 0.01,
                        "yequipmentId": 55
                      },
                      {
                        "useTimes": 6,
                        "malfunctionTimes": 1,
                        "duration": 3.5,
                        "equipmentName": "网关3",
                        "categoryId": 16,
                        "equipmentModel": "string",
                        "categoryName": "次类1",
                        "anotherName": "string",
                        "usageRate": 0.01,
                        "yequipmentId": 57
                      }
               
                ]
         }
    }


### 空间使用排行 [GET]GET /spacegateway/spaceRanking
+ Description
    + Author lyf

+ Parameters
    + dateMinStr (string)  开始日期 格式：yyyy-MM-dd HH:mm:ss
    + dateMaxStr (string)  结束日期 格式：yyyy-MM-dd HH:mm:ss
+ ReturnData
    + logEquipmentMalfunctionList
        + useTimes （long）使用次数
        + malfunctionTimes （long） 故障次数
        + duration （double） 使用时长
        + spaceName (string ) 协作空间名称
        + categoryId (long) 分类id
        + equipmentModel （string）设备型号
        + categoryName （string）分类名称
        + anotherName (string) 设备别名
        + usageRate （double） 使用率
        + yequipmentId （long）设备id

+ Response 200
        
        {
          "data": {
                "logEquipmentMalfunctionList": [
                  {
                    "useTimes": 76,
                    "malfunctionTimes": 10,
                    "duration": 7.5,
                    "spaceName": "协作空间1",
                    "equipmentName": "网关1",
                    "categoryId": 16,
                    "equipmentModel": "string",
                    "categoryName": "次类1",
                    "anotherName": "string",
                    "usageRate": 0.01,
                    "yequipmentId": 55
                  },
                  {
                    "useTimes": 6,
                    "malfunctionTimes": 1,
                    "duration": 3.5,
                    "spaceName": "协作空间4",
                    "equipmentName": "网关3",
                    "categoryId": 16,
                    "equipmentModel": "string",
                    "categoryName": "次类1",
                    "anotherName": "string",
                    "usageRate": 0,
                    "yequipmentId": 57
                  },
                  {
                    "useTimes": 34,
                    "malfunctionTimes": 1,
                    "duration": 2.4,
                    "spaceName": "协作空间2",
                    "equipmentName": "网关2",
                    "categoryId": 16,
                    "equipmentModel": "string",
                    "categoryName": "次类1",
                    "anotherName": "string",
                    "usageRate": 0,
                    "yequipmentId": 56
                  }
           ]
  }
    }

### 设备资产排行 [GET] /equipment/equipmentrank
+ Description
    + Author lyf

+ Parameters
    + page[page] (int)  页码
    + page[size] (int)  分页条数
    + include （Array[string]）
    + sort (Array[string]) 

+ ReturnData
    + id （long）设备id
    + equipmentName （string） 设备名称
    + anotherName （string） 设备别名
    + picture (string ) 设备图片
    + online (int) 是否在线
    + runningStatus （int）设备状态
    + purchaseDate （string）采购日期
    + serviceDate (string) 投入是有时间
    + supplier （string） 供应商
    + brandName （string）设备品牌
    + maintainData （string） 保养日期
    + model （string） 设备型号
    + purchasingCount 采购数量
    + purchasingRate  采购占比

+ Response 200
        
        {
        "data": [
            {
              "totalPages": 1,
              "totalElements": 4,
              "size": 10,
              "number": 1,
              "logEnergyGeneralList": null,
              "equipmentList": [
                {
                  "id": 62,
                  "enabled": 1,
                  "creator": 0,
                  "modifier": 0,
                  "created": "2021-01-15 15:01:00",
                  "modified": "2021-01-15 15:01:00",
                  "flag": 0,
                  "equipmentName": "设备1",
                  "equipmentNameEn": "string",
                  "anotherName": "string",
                  "picture": "string",
                  "online": 1,
                  "runningStatus": 2,
                  "otherStatus": "string",
                  "serialNumber": "string",
                  "purchaseDate": "2021-01-14T14:49:33.000+0000",
                  "serviceDate": "2021-01-14T14:49:33.000+0000",
                  "supplier": "string",
                  "maintenanceTelephone": "string",
                  "brandName": "网关品牌1",
                  "portConfigContent": "string",
                  "pduPortName": "string",
                  "pduPortNo": 0,
                  "pduInterval": 0,
                  "ispdu": 0,
                  "controllable": 1,
                  "builtIn": 0,
                  "fixedAttribute": 0,
                  "functionCode": 0,
                  "lifetype": 0,
                  "recommendedLife": 0,
                  "maintainData": "2021-01-14T14:49:33.000+0000",
                  "totalTime": 0,
                  "stateOfLife": 1,
                  "readable": 0,
                  "model": "string",
                  "purchasingCount": 7,
                  "purchasingRate": 0.33,
                  "ydriveId": 4,
                  "ycategoryId": 16,
                  "ybrandId": 4,
                  "yporttypeId": 0,
                  "yequipmentIdGateway": 55,
                  "ypduId": 0
                },
                {
                  "id": 55,
                  "enabled": 1,
                  "creator": 0,
                  "modifier": 0,
                  "created": "2021-01-15 15:01:00",
                  "modified": "2021-01-15 15:01:00",
                  "flag": 0,
                  "equipmentName": "网关1",
                  "equipmentNameEn": "string",
                  "anotherName": "string",
                  "picture": "string",
                  "online": 1,
                  "runningStatus": 1,
                  "otherStatus": "string",
                  "serialNumber": "string",
                  "purchaseDate": "2021-01-14T14:49:33.000+0000",
                  "serviceDate": "2021-01-14T14:49:33.000+0000",
                  "supplier": "string",
                  "maintenanceTelephone": "string",
                  "brandName": "网关品牌1",
                  "portConfigContent": "string",
                  "pduPortName": "string",
                  "pduPortNo": 0,
                  "pduInterval": 0,
                  "ispdu": 0,
                  "controllable": 1,
                  "builtIn": 0,
                  "fixedAttribute": 0,
                  "functionCode": 0,
                  "lifetype": 0,
                  "recommendedLife": 0,
                  "maintainData": "2021-01-14T14:49:33.000+0000",
                  "totalTime": 0,
                  "stateOfLife": 6,
                  "readable": 0,
                  "model": "string",
                  "purchasingCount": 6,
                  "purchasingRate": 0.29,
                  "ydriveId": 3,
                  "ycategoryId": 16,
                  "ybrandId": 4,
                  "yporttypeId": 0,
                  "yequipmentIdGateway": 0,
                  "ypduId": 0
                }
          ]
    }
  ]
}



### 楼宇管理 
+ Data
    + id (long)  - ID
    + buildingName  (string) 楼宇名称
    + organizationId (long)  机构ID
    + organizationName (string) 机构名称
    + displayOrder (int) - 排序 
    + enabled (int)  - 使能  0禁止 1启用
    + creator (long) - 创建人
    + modifier (long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间

  
### 楼宇新增 [POST] /building
+ Description
    + Author Liukai
+ Request (application/json)
    
        {
          "data": {
            "organizationId": 18,
            "buildingName": "京东望京研发部"
          }
        }

+ Response 201

        {
          "data": {
            "id": 5,
            "type": "building"
          }
        }

+ Response 400

        {
          "errors": [
            {
              "status": "400",
              "code": "名称不能为空",
              "title": "Bad Request",
              "detail": "名称不能为空",
              "source": {
                "pointer": "Building -> buildingName"
              }
            }
          ]
        }

### 楼宇删除 [DELETE] /building/{id}
+ Description
    + Author Liukai
+ Parameters
    + id (long) - id 
+ Response 204 
+ Response 400

         {
          "errors": [
            {
              "status": "400",
              "title": "Bad Request",
              "detail": "无法删除，它是某些楼层的关联数据！"
            }
          ]
        }

### 楼宇更新 [PATCH] /building/{id}
+ Description
    + Author Liukai
+ Parameters
    + id (long) - id 
+ Response 200
+ Response 400

        {
          "errors": [
            {
              "status": "400",
              "code": "名称不能为空",
              "title": "Bad Request",
              "detail": "名称不能为空",
              "source": {
                "pointer": "Building -> buildingName"
              }
            }
          ]
        }

### 楼宇详情 [GET] /building/{id}
+ Description
    + Author Liukai
+ Parameters
    + id (long) - id 
+ Response 200
 
        {
          "data": {
            "id": 6,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2021-01-15 15:41:28",
            "modified": "2021-01-15 15:43:16",
            "organizationId": 21,
            "buildingName": "天猫大楼1",
            "displayOrder": 100,
            "organizationName": "天猫"
          }
        }


### 楼宇列表 [GET]  /building
+ Description
    + Author Liukai
+ Parameters
    + page[number] (int)  -页码
    + page[size]   (int)  -条数
    + sort  (string) -排序 例如 sort=displayOrder,-modified
    + filter[organizationId] (long) -机构ID 例如 filter[organizationId]=1
    + filter[buildingName:like] (string) -楼宇名模糊查询 例如filter[buildingName:like]=%杭州%&
+ Response 200
 
        {
          "meta": {
            "totalPages": 1,
            "totalElements": 6,
            "size": 10,
            "number": 1,
            "numberOfElements": 6,
            "first": true,
            "last": true,
            "sort": null
          },
          "links": {
            "self": "/building?page[number]=1&page[size]=10",
            "first": "/building?page[number]=1&page[size]=10",
            "last": "/building?page[number]=1&page[size]=10"
          },
          "data": [
            {
              "id": 1,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-15 15:09:31",
              "modified": "2021-01-15 15:09:33",
              "organizationId": 17,
              "buildingName": "阿里巴巴1号楼",
              "displayOrder": 100,
              "organizationName": "阿里巴巴"
            },
            {
              "id": 2,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-07 14:16:40",
              "modified": "2021-01-07 14:16:42",
              "organizationId": 2,
              "buildingName": "国商控股大厦",
              "displayOrder": 100,
              "organizationName": "北京鼎迪"
            },
            {
              "id": 3,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-15 15:09:59",
              "modified": "2021-01-15 15:10:02",
              "organizationId": 17,
              "buildingName": "阿里巴巴2号楼",
              "displayOrder": 100,
              "organizationName": "阿里巴巴"
            },
            {
              "id": 4,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-15 15:10:50",
              "modified": "2021-01-15 15:10:53",
              "organizationId": 18,
              "buildingName": "京东亦庄研发部",
              "displayOrder": 100,
              "organizationName": "京东商城"
            },
            {
              "id": 5,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-15 15:13:49",
              "modified": "2021-01-15 15:31:54",
              "organizationId": 18,
              "buildingName": "京东望京研发部",
              "displayOrder": 100,
              "organizationName": "京东商城"
            },
            {
              "id": 6,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-15 15:41:28",
              "modified": "2021-01-15 15:43:16",
              "organizationId": 21,
              "buildingName": "天猫大楼1",
              "displayOrder": 100,
              "organizationName": "天猫"
            }
          ]
        }

  ### 资产使用情况 [GET]
/equipment/equipmentAssetOrMonitorOrMaintainOrLife

###寿命展示
+ Description
    + Author lyf
+ Parameters
    + filter[lifeState] （int）寿命状态（1 ,2,...）
    + filter[lifeType] (int) 寿命类型  0 时长 1次数
    + page[page] (int)  页码
    + page[size] (int)  分页条数
    + include （Array[string]）
    + sort (Array[string]) 

+ ReturnData
    + id （long）设备id
    + equipmentName （string） 设备名称
    + anotherName （string） 设备别名
    + picture (string ) 设备图片
    + online (int) 是否在线
    + runningStatus （int）设备状态
    + purchaseDate （string）采购日期
    + serviceDate (string) 投入使用时间
    + supplier （string） 供应商
    + brandName （string）设备品牌
    + maintainData （string） 保养日期
    + model （string） 设备型号
    + readable  (int) 已读未读
    + stateOfLife （int）寿命状态
    + lifetype （int） 寿命类型
    + gatewayName （string） 所属网关名称
    + ageLimit （int） 使用年限

+ Response 200
       
        {
        "data": [
            "data": [
                    {
                      "id": 64,
                      "enabled": 1,
                      "creator": 0,
                      "modifier": 0,
                      "created": "2021-01-15 16:03:01",
                      "modified": "2021-01-15 16:03:01",
                      "flag": 0,
                      "equipmentName": "设备3",
                      "equipmentNameEn": "string",
                      "anotherName": "string",
                      "picture": "string",
                      "online": 1,
                      "runningStatus": 2,
                      "otherStatus": "string",
                      "serialNumber": "string",
                      "purchaseDate": "2021-01-14T14:49:33.000+0000",
                      "serviceDate": "2012-11-20T14:49:33.000+0000",
                      "supplier": "string",
                      "maintenanceTelephone": "string",
                      "brandName": "品牌1",
                      "portConfigContent": "string",
                      "pduPortName": "string",
                      "pduPortNo": 0,
                      "pduInterval": 0,
                      "ispdu": 0,
                      "controllable": 1,
                      "builtIn": 0,
                      "fixedAttribute": 0,
                      "functionCode": 0,
                      "lifetype": 0,
                      "recommendedLife": 0,
                      "maintainData": "2021-01-14T14:49:33.000+0000",
                      "totalTime": 0,
                      "stateOfLife": 1,
                      "readable": 0,
                      "driveCmds": [
                        {
                          "id": 2,
                          "enabled": 1,
                          "creator": 0,
                          "modifier": 0,
                          "created": "2021-01-14 23:08:18",
                          "modified": "2021-01-14 23:08:18",
                          "flag": 0,
                          "method": "string",
                          "cmdName": "string",
                          "cmdCode": "string",
                          "parameter": "string",
                          "parameterType": "string",
                          "parameterDescription": "string",
                          "associatedStatus": 0,
                          "ydriveId": 4
                        }
                      ],
                      "gatewayName": "云网关1",
                      "model": "string",
                      "secondCategoryName": "主类1",
                      "ageLimit": 6,
                      "yporttypeId": 0,
                      "ydriveId": 4,
                      "ycategoryId": 16,
                      "ybrandId": 4,
                      "yequipmentIdGateway": 55,
                      "ypduId": 0
                    }
  
  
    }
  ]
}

###使用年限展示

+ Description
    + Author lyf
+ Parameters
    + filter[readStaus] （int）已读未读
    + filter[useYear] (int) 使用的年限（1，2，..,>5）
    + page[page] (int)  页码
    + page[size] (int)  分页条数
    + include （Array[string]）
    + sort (Array[string]) 

+ ReturnData
    + id （long）设备id
    + equipmentName （string） 设备名称
    + anotherName （string） 设备别名
    + picture (string ) 设备图片
    + online (int) 是否在线
    + runningStatus （int）设备状态
    + purchaseDate （string）采购日期
    + serviceDate (string) 投入使用时间
    + supplier （string） 供应商
    + brandName （string）设备品牌
    + maintainData （string） 保养日期
    + model （string） 设备型号
    + readable  (int) 已读未读
    + stateOfLife （int）寿命状态
    + lifetype （int） 寿命类型
    + gatewayName （string） 所属网关名称
    + ageLimit （int） 使用年限

+ Response 200
       
        {
        "data": [
                {
                  "id": 64,
                  "enabled": 1,
                  "creator": 0,
                  "modifier": 0,
                  "created": "2021-01-15 16:03:01",
                  "modified": "2021-01-15 16:03:01",
                  "flag": 0,
                  "equipmentName": "设备3",
                  "equipmentNameEn": "string",
                  "anotherName": "string",
                  "picture": "string",
                  "online": 1,
                  "runningStatus": 2,
                  "otherStatus": "string",
                  "serialNumber": "string",
                  "purchaseDate": "2021-01-14T14:49:33.000+0000",
                  "serviceDate": "2012-11-20T14:49:33.000+0000",
                  "supplier": "string",
                  "maintenanceTelephone": "string",
                  "brandName": "品牌1",
                  "portConfigContent": "string",
                  "pduPortName": "string",
                  "pduPortNo": 0,
                  "pduInterval": 0,
                  "ispdu": 0,
                  "controllable": 1,
                  "builtIn": 0,
                  "fixedAttribute": 0,
                  "functionCode": 0,
                  "lifetype": 0,
                  "recommendedLife": 0,
                  "maintainData": "2021-01-14T14:49:33.000+0000",
                  "totalTime": 0,
                  "stateOfLife": 1,
                  "readable": 0,
                  "driveCmds": [
                    {
                      "id": 2,
                      "enabled": 1,
                      "creator": 0,
                      "modifier": 0,
                      "created": "2021-01-14 23:08:18",
                      "modified": "2021-01-14 23:08:18",
                      "flag": 0,
                      "method": "string",
                      "cmdName": "string",
                      "cmdCode": "string",
                      "parameter": "string",
                      "parameterType": "string",
                      "parameterDescription": "string",
                      "associatedStatus": 0,
                      "ydriveId": 4
                    }
                  ],
                  "gatewayName": "云网关1",
                  "model": "string",
                  "secondCategoryName": "主类1",
                  "ageLimit": 6,
                  "yporttypeId": 0,
                  "ydriveId": 4,
                  "ycategoryId": 16,
                  "ybrandId": 4,
                  "yequipmentIdGateway": 55,
                  "ypduId": 0
                }
  
  ]
}

        
