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
    + 网关详情
    + 网关编辑
    + 设备添加
    + 设备修改
    + 设备删除
    + 设备详情
    + 设备列表
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
    + 资产统计-品牌统计
    + 资产统计-分类统计
    + 资产统计-受控状态统计
    + 资产统计-控制协议统计
    + 设备保养信息更已读
    + 楼层新增
    + 楼层删除
    + 楼层更新
    + 楼层列表
    + 协作空间增加
    + 协作空间删除
    + 协作空间更新
    + 协作空间详情
    + 协作空间列表
+ 2020年01月18日
    + Email配置添加
+ 2020年01月20日
    + 云端用户登录
    + 云端用户退出登录
    + 云端用户增加
    + 云端用户禁用
    + 云端用户更新
    + 云端用户详情
    + 云端用户列表
    + 云端当前用户
+ 2020年01月21日
    + 设备开合统计
    + 用户人数统计
    + Email 发送
    + 设备日志列表
    + 系统日志列表
    + 设备保养个数
    + 空间能耗排行
    + 设备能耗排行
+ 2021年01月26日
    + 云端角色管理
        + 云端角色新增
        + 云端角色删除
        + 云端角色修改
        + 云端角色详情
        + 云端角色列表
    + 云端权限管理
        + 权限列表
        + 分组的api权限列表
        + 当前用户的页面权限列表
        + 权限组列表  
    
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
    + id （long）驱动id
    + enabled （int）是否启用
    + creator （long）创建人
    + modifier （long）修改人
    + gatewayGid （long）本地网关id(用于数据同步)
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
        + sort string 排序   (运行时长（反序）：-runTime，正序：runTime) 网关注册时间（-activeStartTime，activeStartTime）
        
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
    + runningStatus （int）1 网关运行状态 （运行状态：0关闭 1运行 2警告    3故障  4其他）
    + spaceName (int) 协作空间名称
    + activeStartTime （string） 网关激活时间
    + activeEndTime (string) 网关激活截止时间
    + isSuccess （int） （是否授权成功 0不成功  1成功，默认是0，付钱完毕修改为1）
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

 
### 网关注册 [POST] /spacegateway
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
### 网关编辑 [PATCH] /spacegateway
+ Parameters
    + Requestparams
    
        + filter[gatewayName] （string） 网关名称
        + filter[gatewaySn] （string）网关SN码
        + filter[spaceid] （string） 协作空间id
       
+ Request (application/json)

+ Response 200

        {
          "data": {
           
          }
        }

## 网关删除  [DELETE]  /gatewayinfo/{id}

+ Parameters
    + id (long)网关id
      
+ Request (application/json)
        
+ Response 204        

### 网关详情 [Get] /gatewayinfo
+ Parameters
   
        
       
+ Request (application/json)

+ Response 200



   
+ Request (application/json)       


### 设备添加 [POST] /equipment
+ Description

+ Parameters
    + data
        + id (long)  设备id
        + equipmentName （string）设备名称
        + equipmentNameEn (string)  自动生成唯一号
        + anotherName (string)   设备别名
        + picture  (string) 设备图片url
        + online (int) 是否在线：0 离线 1在线 2未知
        + runningStatus (int) 运行状态：0关闭 1运行 2警告    3故障  4其他
        + otherStatus （string）其他数据，json格式
        + serialNumber （string）设备序列号
        + serviceDate （string） 投入使用日期
        + supplier (string)  供应商
        + maintenanceTelephone （string）维修电话
        + brandName (string)  品牌名称
        + portConfigContent (string)   使用json，map的key是使用端口类型名，易于扩展
        + pduPortName  (string) 
        + pduPortNo (int) 
        + pduInterval (int) 
        + ispdu （int）0 非pdu 1是pdu
        + controllable （int）是否可控 1 可控  0 不可控
        + builtIn （int） 是否内置 1为内置 0为非内置
        + fixedAttribute （int） 0 无固定属性，1为环境  2 占位 3 能耗
        + functionCode (int)  0 无功能  1 是次数  2 是电表记录
        + lifetype （int）寿命类型 0 时长 1 次数 
        + recommendedLife (int)  建议使用寿命
        + maintainData (string)   保养日期
        + totalTime  (int) 累计运行总时长，单位小时 (每日四舍五入)
        + stateOfLife (int) 寿命状态(1 全新 2 良好 3 一般 4 可用 5 极好 6更换)
        + readable (int) 1 已读 0 未读
        + driveCmds 
            + associatedStatus  (int) 
            + cloudCid  (int) 云端id
            + cmdAlias (string)  cmd别名
            + cmdCode (string) 前端页面可以识别的code
            + cmdName (string) 命令的名字
            + created (string) 
            + creator (string)
            + enabled (int) 
            + flag (int) 
            + gatewayGid (int) 网关id
            + id (int)  自增主键
            + method (string) get put post delete
            + modified (string)  
            + modifier (int)
            + parameter (string)  参数,使用逗号进行隔开,如果3个参数
            + parameterDescription (string)
            + parameterType (string) 参数的类型
            + ydriveId (int) 本地驱动id
        + pdus
            + anotherName  (string) 
            + cloudCid  (int) 云端id
            + cmdCodeOff (string)  开命令CODE
            + cmdCodeOn (string) 关命令CODE
            + created (string) 
            + creator (string) 
            + electricCurrent (int) 电流
            + enabled (int) 
            + flag (int) 
            + gatewayGid (int) 网关id
            + id (int)  自增主键
            + intervalValue (int) 前端的按钮 时间间隔
            + modified (string)  
            + modifier (int)
            + onOffState (int)  开关状态 1为开 0为关  2为未知状态（如果设备连线断掉即为未知状态）
            + pduPortNo (int) 和设备用这个序列号是绑定的。（1端口- 2端口）
            + power (int)  功率
            + voltage (int) 电压
            + yequipmentId (int) PDU的设备的ID
            + yequipmentIdJoin (int) 连入的设备ID
        + equipmentBtnGroups 
            + cloudCid  (int) 云端id
            + cmdBtnGroups
                + cloudCid  (int) 云端id
                + cmdAlias  (string) 命令的名字
                + cmdCode  (string) 命令的Code
                + cmdName  (string) 命令的名字
                + created  (string) 
                + creator  (int) 
                + enabled  (int) 
                + flag  (int) 云端id
                + forbidden  (int) 是否禁用
                + id  (int) 云端id
                + modified  (string) 
                + modifier  (int) 
                + ydrivecmdId  (int) 驱动cmd的ID
                + yequipmentbtngroupId  (int) 设备组ID
            + created (string) 
            + creator (int) 
            + enabled (int) 
            + flag (int) 
            + equipmentBtnGroups
                +
            + gatewayGid (int) 网关id
            + groupAndGroup (string)  这个是编组，不同的编组默认使用逗号隔开。（目前只支持2个组编组，同时出发的第二个组才触发命令）
            + groupName (string) 组名
            + groupNameAlias (string)   组别称
            + groupType (int) 1 开关组 2 输入组 3 输出组 4 预设组 5编组组
            + id (int)  自增主键id
            + modified (string)
            + modifier (int)  
         + portTypes 
            + builtIn (int)
            + cloudCid (int)  云端id
            + created (string)
            + creator (int)
            + defaultValue (string) 默认值  如果没有配置就是使用这个默认值，减少配置。
            + description (string) 描述
            + enabled (int)
            + flag (int)
            + gatewayGid (int) 网关id用于数据同步
            + id (int) 自增主键ID
            + modified (string)
            + modifier (int)
            + parentIdPorttype (int) 如果是本身就是父ID，则为0
            + probableValueList (string) 返回值使用英文（英文可以避免乱码），字符串用逗号隔开  on,off,on-off,等等
            + typeName (string) 端口类型名/属性名 类型名字：串口
            属性名：属性名比如波特率
            + valueType (int)  0 字符串类型 1 整数型 2 FLOAT型 等多种类型，可以写成枚举类放到代码中。
        + model （string） 设备品牌
        + primaryCategoryName （string） 一级分类名
        + secondCategoryName （string）二级分类名
        + ageLimit （int） 使用年限（1-6年）
        + yequipmentIdGateway （int） 所属网关设备id
        + yporttypeId （int） 设备端口类型id
        + ydriveId （string）设备驱动id
        + ycategoryId （int） 设备类型id
        + ybrandId （int）  设备品牌id
        + ypduId （int）设备pdu的id
        
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



### 设备编辑 [PATCH] /equipment/{id}
+ Description

+ Parameters
    + data
        + id (long)  设备id
        + equipmentName （string）设备名称
        + equipmentNameEn (string)  自动生成唯一号
        + anotherName (string)   设备别名
        + picture  (string) 设备图片url
        + online (int) 是否在线：0 离线 1在线 2未知
        + runningStatus (int) 运行状态：0关闭 1运行 2警告    3故障  4其他
        + otherStatus （string）其他数据，json格式
        + serialNumber （string）设备序列号
        + serviceDate （string） 投入使用日期
        + supplier (string)  供应商
        + maintenanceTelephone （string）维修电话
        + brandName (string)  品牌名称
        + portConfigContent (string)   使用json，map的key是使用端口类型名，易于扩展
        + pduPortName  (string) 
        + pduPortNo (int) 
        + pduInterval (int) 
        + ispdu （int）0 非pdu 1是pdu
        + controllable （int）是否可控 1 可控  0 不可控
        + builtIn （int） 是否内置 1为内置 0为非内置
        + fixedAttribute （int） 0 无固定属性，1为环境  2 占位 3 能耗
        + functionCode (int)  0 无功能  1 是次数  2 是电表记录
        + lifetype （int）寿命类型 0 时长 1 次数 
        + recommendedLife (int)  建议使用寿命
        + maintainData (string)   保养日期
        + totalTime  (int) 累计运行总时长，单位小时 (每日四舍五入)
        + stateOfLife (int) 寿命状态(1 全新 2 良好 3 一般 4 可用 5 极好 6更换)
        + readable (int) 1 已读 0 未读
        + driveCmds 
            + associatedStatus  (int) 
            + cloudCid  (int) 云端id
            + cmdAlias (string)  cmd别名
            + cmdCode (string) 前端页面可以识别的code
            + cmdName (string) 命令的名字
            + created (string) 
            + creator (string)
            + enabled (int) 
            + flag (int) 
            + gatewayGid (int) 网关id
            + id (int)  自增主键
            + method (string) get put post delete
            + modified (string)  
            + modifier (int)
            + parameter (string)  参数,使用逗号进行隔开,如果3个参数
            + parameterDescription (string)
            + parameterType (string) 参数的类型
            + ydriveId (int) 本地驱动id
        + pdus
            + anotherName  (string) 
            + cloudCid  (int) 云端id
            + cmdCodeOff (string)  开命令CODE
            + cmdCodeOn (string) 关命令CODE
            + created (string) 
            + creator (string) 
            + electricCurrent (int) 电流
            + enabled (int) 
            + flag (int) 
            + gatewayGid (int) 网关id
            + id (int)  自增主键
            + intervalValue (int) 前端的按钮 时间间隔
            + modified (string)  
            + modifier (int)
            + onOffState (int)  开关状态 1为开 0为关  2为未知状态（如果设备连线断掉即为未知状态）
            + pduPortNo (int) 和设备用这个序列号是绑定的。（1端口- 2端口）
            + power (int)  功率
            + voltage (int) 电压
            + yequipmentId (int) PDU的设备的ID
            + yequipmentIdJoin (int) 连入的设备ID
        + equipmentBtnGroups 
            + cloudCid  (int) 云端id
            + cmdBtnGroups
                + cloudCid  (int) 云端id
                + cmdAlias  (string) 命令的名字
                + cmdCode  (string) 命令的Code
                + cmdName  (string) 命令的名字
                + created  (string) 
                + creator  (int) 
                + enabled  (int) 
                + flag  (int) 云端id
                + forbidden  (int) 是否禁用
                + id  (int) 云端id
                + modified  (string) 
                + modifier  (int) 
                + ydrivecmdId  (int) 驱动cmd的ID
                + yequipmentbtngroupId  (int) 设备组ID
            + created (string) 
            + creator (int) 
            + enabled (int) 
            + flag (int) 
            + equipmentBtnGroups
                +
            + gatewayGid (int) 网关id
            + groupAndGroup (string)  这个是编组，不同的编组默认使用逗号隔开。（目前只支持2个组编组，同时出发的第二个组才触发命令）
            + groupName (string) 组名
            + groupNameAlias (string)   组别称
            + groupType (int) 1 开关组 2 输入组 3 输出组 4 预设组 5编组组
            + id (int)  自增主键id
            + modified (string)
            + modifier (int)  
         + portTypes 
            + builtIn (int)
            + cloudCid (int)  云端id
            + created (string)
            + creator (int)
            + defaultValue (string) 默认值  如果没有配置就是使用这个默认值，减少配置。
            + description (string) 描述
            + enabled (int)
            + flag (int)
            + gatewayGid (int) 网关id用于数据同步
            + id (int) 自增主键ID
            + modified (string)
            + modifier (int)
            + parentIdPorttype (int) 如果是本身就是父ID，则为0
            + probableValueList (string) 返回值使用英文（英文可以避免乱码），字符串用逗号隔开  on,off,on-off,等等
            + typeName (string) 端口类型名/属性名 类型名字：串口
            属性名：属性名比如波特率
            + valueType (int)  0 字符串类型 1 整数型 2 FLOAT型 等多种类型，可以写成枚举类放到代码中。
        + driveReadtypes
            + decimalPlaces (int)
            + cloudCid (int)  云端id
            + created (string)
            + creator (int)
            + ifLog (int)  1 加入日志  0 不加入日志
            + multiply (int) 数据矫正  相乘
            + enabled (int)
            + flag (int)
            + gatewayGid (int) 网关id用于数据同步
            + id (int) 自增主键ID
            + modified (string)
            + modifier (int)
            + plus (float) 数据矫正 相加或相减
            + readTypeAlias (string)  
            + unitName (string) 单位名称
            + ydriveId (int) 驱动ID
            + yreadtypeId (int) 读数类型ID
      
     
        + model （string） 设备品牌
        + primaryCategoryName （string） 一级分类名
        + secondCategoryName （string）二级分类名
        + ageLimit （int） 使用年限（1-6年）
        + yequipmentIdGateway （int） 所属网关设备id
        + yporttypeId （int） 设备端口类型id
        + ydriveId （string）设备驱动id
        + ycategoryId （int） 设备类型id
        + ybrandId （int）  设备品牌id
        + ypduId （int）设备pdu的id
        
+ Request (application/json)

+ ReturnData

        {
          "data": {
            "id": 4,
            "type": "equipment"
          }
        }
        
+ Response 200
       
+ Response 400
    
        {
          "errors": [
            {
              "status": "400",
              "title": "Bad Request"
            }
          ]
        } 


### 设备编辑 [DELETE] /equipment/{id}
+ Description

+ Parameters
    + id (long) 设备ID
+ Request (application/json)

+ ReturnData

        {
          "data": {
            "id": 4,
            "type": "equipment"
          }
        }
        
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



### 设备列表 [GET] /equipment/equipmentAssetOrMonitorOrMaintainOrLife

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

        + id (long)  设备id
        + equipmentName （string）设备名称
        + equipmentNameEn (string)  自动生成唯一号
        + anotherName (string)   设备别名
        + picture  (string) 设备图片url
        + online (int) 是否在线：0 离线 1在线 2未知
        + runningStatus (int) 运行状态：0关闭 1运行 2警告    3故障  4其他
        + otherStatus （string）其他数据，json格式
        + serialNumber （string）设备序列号
        + serviceDate （string） 投入使用日期
        + supplier (string)  供应商
        + maintenanceTelephone （string）维修电话
        + brandName (string)  品牌名称
        + portConfigContent (string)   使用json，map的key是使用端口类型名，易于扩展
        + pduPortName  (string) 
        + pduPortNo (int) 
        + pduInterval (int) 
        + ispdu （int）0 非pdu 1是pdu
        + controllable （int）是否可控 1 可控  0 不可控
        + builtIn （int） 是否内置 1为内置 0为非内置
        + fixedAttribute （int） 0 无固定属性，1为环境  2 占位 3 能耗
        + functionCode (int)  0 无功能  1 是次数  2 是电表记录
        + lifetype （int）寿命类型 0 时长 1 次数 
        + recommendedLife (int)  建议使用寿命
        + maintainData (string)   保养日期
        + totalTime  (int) 累计运行总时长，单位小时 (每日四舍五入)
        + stateOfLife (int) 寿命状态(1 全新 2 良好 3 一般 4 可用 5 极好 6更换)
        + readable (int) 1 已读 0 未读
        + driveCmds 
            + associatedStatus  (int) 
            + cloudCid  (int) 云端id
            + cmdAlias (string)  cmd别名
            + cmdCode (string) 前端页面可以识别的code
            + cmdName (string) 命令的名字
            + created (string) 
            + creator (string)
            + enabled (int) 
            + flag (int) 
            + gatewayGid (int) 网关id
            + id (int)  自增主键
            + method (string) get put post delete
            + modified (string)  
            + modifier (int)
            + parameter (string)  参数,使用逗号进行隔开,如果3个参数
            + parameterDescription (string)
            + parameterType (string) 参数的类型
            + ydriveId (int) 本地驱动id
        + pdus
            + anotherName  (string) 
            + cloudCid  (int) 云端id
            + cmdCodeOff (string)  开命令CODE
            + cmdCodeOn (string) 关命令CODE
            + created (string) 
            + creator (string) 
            + electricCurrent (int) 电流
            + enabled (int) 
            + flag (int) 
            + gatewayGid (int) 网关id
            + id (int)  自增主键
            + intervalValue (int) 前端的按钮 时间间隔
            + modified (string)  
            + modifier (int)
            + onOffState (int)  开关状态 1为开 0为关  2为未知状态（如果设备连线断掉即为未知状态）
            + pduPortNo (int) 和设备用这个序列号是绑定的。（1端口- 2端口）
            + power (int)  功率
            + voltage (int) 电压
            + yequipmentId (int) PDU的设备的ID
            + yequipmentIdJoin (int) 连入的设备ID
        + equipmentBtnGroups 
            + cloudCid  (int) 云端id
            + cmdBtnGroups
                + cloudCid  (int) 云端id
                + cmdAlias  (string) 命令的名字
                + cmdCode  (string) 命令的Code
                + cmdName  (string) 命令的名字
                + created  (string) 
                + creator  (int) 
                + enabled  (int) 
                + flag  (int) 云端id
                + forbidden  (int) 是否禁用
                + id  (int) 云端id
                + modified  (string) 
                + modifier  (int) 
                + ydrivecmdId  (int) 驱动cmd的ID
                + yequipmentbtngroupId  (int) 设备组ID
            + created (string) 
            + creator (int) 
            + enabled (int) 
            + flag (int) 
            + equipmentBtnGroups
                +
            + gatewayGid (int) 网关id
            + groupAndGroup (string)  这个是编组，不同的编组默认使用逗号隔开。（目前只支持2个组编组，同时出发的第二个组才触发命令）
            + groupName (string) 组名
            + groupNameAlias (string)   组别称
            + groupType (int) 1 开关组 2 输入组 3 输出组 4 预设组 5编组组
            + id (int)  自增主键id
            + modified (string)
            + modifier (int)  
         + portTypes 
            + builtIn (int)
            + cloudCid (int)  云端id
            + created (string)
            + creator (int)
            + defaultValue (string) 默认值  如果没有配置就是使用这个默认值，减少配置。
            + description (string) 描述
            + enabled (int)
            + flag (int)
            + gatewayGid (int) 网关id用于数据同步
            + id (int) 自增主键ID
            + modified (string)
            + modifier (int)
            + parentIdPorttype (int) 如果是本身就是父ID，则为0
            + probableValueList (string) 返回值使用英文（英文可以避免乱码），字符串用逗号隔开  on,off,on-off,等等
            + typeName (string) 端口类型名/属性名 类型名字：串口
            属性名：属性名比如波特率
            + valueType (int)  0 字符串类型 1 整数型 2 FLOAT型 等多种类型，可以写成枚举类放到代码中。
        + driveReadtypes
            + decimalPlaces (int)
            + cloudCid (int)  云端id
            + created (string)
            + creator (int)
            + ifLog (int)  1 加入日志  0 不加入日志
            + multiply (int) 数据矫正  相乘
            + enabled (int)
            + flag (int)
            + gatewayGid (int) 网关id用于数据同步
            + id (int) 自增主键ID
            + modified (string)
            + modifier (int)
            + plus (float) 数据矫正 相加或相减
            + readTypeAlias (string)  
            + unitName (string) 单位名称
            + ydriveId (int) 驱动ID
            + yreadtypeId (int) 读数类型ID
      
     
        + model （string） 设备品牌
        + primaryCategoryName （string） 一级分类名
        + secondCategoryName （string）二级分类名
        + ageLimit （int） 使用年限（1-6年）
        + yequipmentIdGateway （int） 所属网关设备id
        + yporttypeId （int） 设备端口类型id
        + ydriveId （string）设备驱动id
        + ycategoryId （int） 设备类型id
        + ybrandId （int）  设备品牌id
        + ypduId （int）设备pdu的id

        


### 设备状态监测列表 [GET] /equipment/equipmentAssetOrMonitorOrMaintainOrLife

+ Description

+ Parameters
    + data
        + filter[gatewayid] (int)  网关id
        + filter[brandid] （int）品牌id
        + filter[primaryCategoryId] (long)  一级分类id
        + filter[secondCategoryId] (long)   二级分类id
        + filter[equipmentName] 设备名称）
        + filter[driveType] (string) 驱动型号
        + filter[online] (int)  是否在线：0 离线 1在线 2未知
        + filter[runningStatus] （int）运行状态：0关闭 1运行 2警告    3故障  4其他
        + include (Array[string])
        + page[number] （int）页码
        + page[size] （int）条数
        + sort （Array[string]） 排序
        
+ Request (application/json)

+ ReturnData 

        + id (long)  设备id
        + equipmentName （string）设备名称
        + equipmentNameEn (string)  自动生成唯一号
        + anotherName (string)   设备别名
        + picture  (string) 设备图片url
        + online (int) 是否在线：0 离线 1在线 2未知
        + runningStatus (int) 运行状态：0关闭 1运行 2警告    3故障  4其他
        + otherStatus （string）其他数据，json格式
        + serialNumber （string）设备序列号
        + serviceDate （string） 投入使用日期
        + supplier (string)  供应商
        + maintenanceTelephone （string）维修电话
        + brandName (string)  品牌名称
        + portConfigContent (string)   使用json，map的key是使用端口类型名，易于扩展
        + pduPortName  (string) 
        + pduPortNo (int) 
        + pduInterval (int) 
        + ispdu （int）0 非pdu 1是pdu
        + controllable （int）是否可控 1 可控  0 不可控
        + builtIn （int） 是否内置 1为内置 0为非内置
        + fixedAttribute （int） 0 无固定属性，1为环境  2 占位 3 能耗
        + functionCode (int)  0 无功能  1 是次数  2 是电表记录
        + lifetype （int）寿命类型 0 时长 1 次数 
        + recommendedLife (int)  建议使用寿命
        + maintainData (string)   保养日期
        + totalTime  (int) 累计运行总时长，单位小时 (每日四舍五入)
        + stateOfLife (int) 寿命状态(1 全新 2 良好 3 一般 4 可用 5 极好 6更换)
        + readable (int) 1 已读 0 未读
        + driveCmds 
            + associatedStatus  (int) 
            + cloudCid  (int) 云端id
            + cmdAlias (string)  cmd别名
            + cmdCode (string) 前端页面可以识别的code
            + cmdName (string) 命令的名字
            + created (string) 
            + creator (string)
            + enabled (int) 
            + flag (int) 
            + gatewayGid (int) 网关id
            + id (int)  自增主键
            + method (string) get put post delete
            + modified (string)  
            + modifier (int)
            + parameter (string)  参数,使用逗号进行隔开,如果3个参数
            + parameterDescription (string)
            + parameterType (string) 参数的类型
            + ydriveId (int) 本地驱动id
        + pdus
            + anotherName  (string) 
            + cloudCid  (int) 云端id
            + cmdCodeOff (string)  开命令CODE
            + cmdCodeOn (string) 关命令CODE
            + created (string) 
            + creator (string) 
            + electricCurrent (int) 电流
            + enabled (int) 
            + flag (int) 
            + gatewayGid (int) 网关id
            + id (int)  自增主键
            + intervalValue (int) 前端的按钮 时间间隔
            + modified (string)  
            + modifier (int)
            + onOffState (int)  开关状态 1为开 0为关  2为未知状态（如果设备连线断掉即为未知状态）
            + pduPortNo (int) 和设备用这个序列号是绑定的。（1端口- 2端口）
            + power (int)  功率
            + voltage (int) 电压
            + yequipmentId (int) PDU的设备的ID
            + yequipmentIdJoin (int) 连入的设备ID
        + equipmentBtnGroups 
            + cloudCid  (int) 云端id
            + cmdBtnGroups
                + cloudCid  (int) 云端id
                + cmdAlias  (string) 命令的名字
                + cmdCode  (string) 命令的Code
                + cmdName  (string) 命令的名字
                + created  (string) 
                + creator  (int) 
                + enabled  (int) 
                + flag  (int) 云端id
                + forbidden  (int) 是否禁用
                + id  (int) 云端id
                + modified  (string) 
                + modifier  (int) 
                + ydrivecmdId  (int) 驱动cmd的ID
                + yequipmentbtngroupId  (int) 设备组ID
            + created (string) 
            + creator (int) 
            + enabled (int) 
            + flag (int) 
            + equipmentBtnGroups
                +
            + gatewayGid (int) 网关id
            + groupAndGroup (string)  这个是编组，不同的编组默认使用逗号隔开。（目前只支持2个组编组，同时出发的第二个组才触发命令）
            + groupName (string) 组名
            + groupNameAlias (string)   组别称
            + groupType (int) 1 开关组 2 输入组 3 输出组 4 预设组 5编组组
            + id (int)  自增主键id
            + modified (string)
            + modifier (int)  
         + portTypes 
            + builtIn (int)
            + cloudCid (int)  云端id
            + created (string)
            + creator (int)
            + defaultValue (string) 默认值  如果没有配置就是使用这个默认值，减少配置。
            + description (string) 描述
            + enabled (int)
            + flag (int)
            + gatewayGid (int) 网关id用于数据同步
            + id (int) 自增主键ID
            + modified (string)
            + modifier (int)
            + parentIdPorttype (int) 如果是本身就是父ID，则为0
            + probableValueList (string) 返回值使用英文（英文可以避免乱码），字符串用逗号隔开  on,off,on-off,等等
            + typeName (string) 端口类型名/属性名 类型名字：串口
            属性名：属性名比如波特率
            + valueType (int)  0 字符串类型 1 整数型 2 FLOAT型 等多种类型，可以写成枚举类放到代码中。
        + driveReadtypes
            + decimalPlaces (int)
            + cloudCid (int)  云端id
            + created (string)
            + creator (int)
            + ifLog (int)  1 加入日志  0 不加入日志
            + multiply (int) 数据矫正  相乘
            + enabled (int)
            + flag (int)
            + gatewayGid (int) 网关id用于数据同步
            + id (int) 自增主键ID
            + modified (string)
            + modifier (int)
            + plus (float) 数据矫正 相加或相减
            + readTypeAlias (string)  
            + unitName (string) 单位名称
            + ydriveId (int) 驱动ID
            + yreadtypeId (int) 读数类型ID
      
     
        + model （string） 设备品牌
        + primaryCategoryName （string） 一级分类名
        + secondCategoryName （string）二级分类名
        + ageLimit （int） 使用年限（1-6年）
        + yequipmentIdGateway （int） 所属网关设备id
        + yporttypeId （int） 设备端口类型id
        + ydriveId （string）设备驱动id
        + ycategoryId （int） 设备类型id
        + ybrandId （int）  设备品牌id
        + ypduId （int）设备pdu的id

### 设备保养列表 [GET] /equipment/equipmenmaintain

+ Description

+ Parameters
    + data
        + filter[readStaus] (int)  是否已读
        + filter[useYear] （int）使用年限
        + filter[maintainStart] (string)  开始保养日期,日期，格式：yyyy-MM-dd
        + filter[maintainEnd] (long)   结束保养日期,日期，格式：yyyy-MM-dd
        + page[page] （int）页码
        + page[size] （int）条数
      
        
+ Request (application/json)

+ ReturnData 
    
        + id (long)  设备id
        + equipmentName （string）设备名称
        + equipmentNameEn (string)  自动生成唯一号
        + anotherName (string)   设备别名
        + picture  (string) 设备图片url
        + online (int) 是否在线：0 离线 1在线 2未知
        + runningStatus (int) 运行状态：0关闭 1运行 2警告    3故障  4其他
        + otherStatus （string）其他数据，json格式
        + serialNumber （string）设备序列号
        + serviceDate （string） 投入使用日期
        + supplier (string)  供应商
        + maintenanceTelephone （string）维修电话
        + brandName (string)  品牌名称
        + portConfigContent (string)   使用json，map的key是使用端口类型名，易于扩展
        + pduPortName  (string) 
        + pduPortNo (int) 
        + pduInterval (int) 
        + ispdu （int）0 非pdu 1是pdu
        + controllable （int）是否可控 1 可控  0 不可控
        + builtIn （int） 是否内置 1为内置 0为非内置
        + fixedAttribute （int） 0 无固定属性，1为环境  2 占位 3 能耗
        + functionCode (int)  0 无功能  1 是次数  2 是电表记录
        + lifetype （int）寿命类型 0 时长 1 次数 
        + recommendedLife (int)  建议使用寿命
        + maintainData (string)   保养日期
        + totalTime  (int) 累计运行总时长，单位小时 (每日四舍五入)
        + stateOfLife (int) 寿命状态(1 全新 2 良好 3 一般 4 可用 5 极好 6更换)
        + thisMaintenanceDate (string) 本次保养时间
        + readable (int) 1 已读 0 未读
        + driveCmds 
            + associatedStatus  (int) 
            + cloudCid  (int) 云端id
            + cmdAlias (string)  cmd别名
            + cmdCode (string) 前端页面可以识别的code
            + cmdName (string) 命令的名字
            + created (string) 
            + creator (string)
            + enabled (int) 
            + flag (int) 
            + gatewayGid (int) 网关id
            + id (int)  自增主键
            + method (string) get put post delete
            + modified (string)  
            + modifier (int)
            + parameter (string)  参数,使用逗号进行隔开,如果3个参数
            + parameterDescription (string)
            + parameterType (string) 参数的类型
            + ydriveId (int) 本地驱动id
        + pdus
            + anotherName  (string) 
            + cloudCid  (int) 云端id
            + cmdCodeOff (string)  开命令CODE
            + cmdCodeOn (string) 关命令CODE
            + created (string) 
            + creator (string) 
            + electricCurrent (int) 电流
            + enabled (int) 
            + flag (int) 
            + gatewayGid (int) 网关id
            + id (int)  自增主键
            + intervalValue (int) 前端的按钮 时间间隔
            + modified (string)  
            + modifier (int)
            + onOffState (int)  开关状态 1为开 0为关  2为未知状态（如果设备连线断掉即为未知状态）
            + pduPortNo (int) 和设备用这个序列号是绑定的。（1端口- 2端口）
            + power (int)  功率
            + voltage (int) 电压
            + yequipmentId (int) PDU的设备的ID
            + yequipmentIdJoin (int) 连入的设备ID
        + equipmentBtnGroups 
            + cloudCid  (int) 云端id
            + cmdBtnGroups
                + cloudCid  (int) 云端id
                + cmdAlias  (string) 命令的名字
                + cmdCode  (string) 命令的Code
                + cmdName  (string) 命令的名字
                + created  (string) 
                + creator  (int) 
                + enabled  (int) 
                + flag  (int) 云端id
                + forbidden  (int) 是否禁用
                + id  (int) 云端id
                + modified  (string) 
                + modifier  (int) 
                + ydrivecmdId  (int) 驱动cmd的ID
                + yequipmentbtngroupId  (int) 设备组ID
            + created (string) 
            + creator (int) 
            + enabled (int) 
            + flag (int) 
            + equipmentBtnGroups
                +
            + gatewayGid (int) 网关id
            + groupAndGroup (string)  这个是编组，不同的编组默认使用逗号隔开。（目前只支持2个组编组，同时出发的第二个组才触发命令）
            + groupName (string) 组名
            + groupNameAlias (string)   组别称
            + groupType (int) 1 开关组 2 输入组 3 输出组 4 预设组 5编组组
            + id (int)  自增主键id
            + modified (string)
            + modifier (int)  
         + portTypes 
            + builtIn (int)
            + cloudCid (int)  云端id
            + created (string)
            + creator (int)
            + defaultValue (string) 默认值  如果没有配置就是使用这个默认值，减少配置。
            + description (string) 描述
            + enabled (int)
            + flag (int)
            + gatewayGid (int) 网关id用于数据同步
            + id (int) 自增主键ID
            + modified (string)
            + modifier (int)
            + parentIdPorttype (int) 如果是本身就是父ID，则为0
            + probableValueList (string) 返回值使用英文（英文可以避免乱码），字符串用逗号隔开  on,off,on-off,等等
            + typeName (string) 端口类型名/属性名 类型名字：串口
            属性名：属性名比如波特率
            + valueType (int)  0 字符串类型 1 整数型 2 FLOAT型 等多种类型，可以写成枚举类放到代码中。
        + driveReadtypes
            + decimalPlaces (int)
            + cloudCid (int)  云端id
            + created (string)
            + creator (int)
            + ifLog (int)  1 加入日志  0 不加入日志
            + multiply (int) 数据矫正  相乘
            + enabled (int)
            + flag (int)
            + gatewayGid (int) 网关id用于数据同步
            + id (int) 自增主键ID
            + modified (string)
            + modifier (int)
            + plus (float) 数据矫正 相加或相减
            + readTypeAlias (string)  
            + unitName (string) 单位名称
            + ydriveId (int) 驱动ID
            + yreadtypeId (int) 读数类型ID
      
     
        + model （string） 设备品牌
        + primaryCategoryName （string） 一级分类名
        + secondCategoryName （string）二级分类名
        + ageLimit （int） 使用年限（1-6年）
        + yequipmentIdGateway （int） 所属网关设备id
        + yporttypeId （int） 设备端口类型id
        + ydriveId （string）设备驱动id
        + ycategoryId （int） 设备类型id
        + ybrandId （int）  设备品牌id
        + ypduId （int）设备pdu的id
        
        
         {
          "data":  {
                "id": 141,
                  "enabled": 1,
                  "creator": 0,
                  "modifier": 0,
                  "created": "2021-01-26 11:00:32",
                  "modified": "2021-01-26 11:00:32",
                  "flag": 0,
                  "equipmentName": "七合一环境传感器888",
                  "equipmentNameEn": "1d8923ca-0a58-46c5-a065-62ddcb3245f7",
                  "anotherName": "测试222",
                  "picture": "http://static.mifanxing.com/wx/image/119/27/1800035.jpg?w=320&h=180",
                  "online": 0,
                  "runningStatus": 0,
                  "serialNumber": "asdadsadd",
                  "purchaseDate": "2021-01-14 10:51:51",
                  "serviceDate": "2021-01-15 10:51:54",
                  "supplier": "测试",
                  "maintenanceTelephone": "15770713407",
                  "brandName": "Sony",
                  "portConfigContent": "{'baudRate':'9600','dataBit':'8','stopBit':'1','parityBit':'N','startBit':'1'}",
                  "ispdu": 0,
                  "controllable": 1,
                  "builtIn": 0,
                  "fixedAttribute": 1,
                  "functionCode": 0,
                  "lifetype": 0,
                  "totalTime": 0,
                  "readable": 0,
                  "driveCmds": [],
                  "gatewayName": "小小网关1",
                  "model": "sw010",
                  "primaryCategoryName": "传感器",
                  "secondCategoryName": "电量传感器(勿删)",
                  "ageLimit": 1,
                  "thisMaintenanceDate": "2021-07-15",
                  "yequipmentIdGateway": 136,
                  "yporttypeId": 2,
                  "ydriveId": 175
           }
   }


### 设备寿命列表 [GET] /equipment/equipmentAssetOrMonitorOrMaintainOrLife

+ Description

+ Parameters
    + data
        + filter[lifeState] (int)  寿命状态（1,2,3..->差 良 优...）
        + filter[lifeType] （int）寿命类型(0 时长 1 次)
        + include (Array[string])
        + page[number] （int）页码
        + page[size] （int）条数
        + sort （Array[string]） 排序
        
+ Request (application/json)

+ ReturnData 
    
        + id (long)  设备id
        + equipmentName （string）设备名称
        + equipmentNameEn (string)  自动生成唯一号
        + anotherName (string)   设备别名
        + picture  (string) 设备图片url
        + online (int) 是否在线：0 离线 1在线 2未知
        + runningStatus (int) 运行状态：0关闭 1运行 2警告    3故障  4其他
        + otherStatus （string）其他数据，json格式
        + serialNumber （string）设备序列号
        + serviceDate （string） 投入使用日期
        + supplier (string)  供应商
        + maintenanceTelephone （string）维修电话
        + brandName (string)  品牌名称
        + portConfigContent (string)   使用json，map的key是使用端口类型名，易于扩展
        + pduPortName  (string) 
        + pduPortNo (int) 
        + pduInterval (int) 
        + ispdu （int）0 非pdu 1是pdu
        + controllable （int）是否可控 1 可控  0 不可控
        + builtIn （int） 是否内置 1为内置 0为非内置
        + fixedAttribute （int） 0 无固定属性，1为环境  2 占位 3 能耗
        + functionCode (int)  0 无功能  1 是次数  2 是电表记录
        + lifetype （int）寿命类型 0 时长 1 次数 
        + recommendedLife (int)  建议使用寿命
        + maintainData (string)   保养日期
        + totalTime  (int) 累计运行总时长，单位小时 (每日四舍五入)
        + stateOfLife (int) 寿命状态(1 全新 2 良好 3 一般 4 可用 5 极好 6更换)
        + readable (int) 1 已读 0 未读
        + driveCmds 
            + associatedStatus  (int) 
            + cloudCid  (int) 云端id
            + cmdAlias (string)  cmd别名
            + cmdCode (string) 前端页面可以识别的code
            + cmdName (string) 命令的名字
            + created (string) 
            + creator (string)
            + enabled (int) 
            + flag (int) 
            + gatewayGid (int) 网关id
            + id (int)  自增主键
            + method (string) get put post delete
            + modified (string)  
            + modifier (int)
            + parameter (string)  参数,使用逗号进行隔开,如果3个参数
            + parameterDescription (string)
            + parameterType (string) 参数的类型
            + ydriveId (int) 本地驱动id
        + pdus
            + anotherName  (string) 
            + cloudCid  (int) 云端id
            + cmdCodeOff (string)  开命令CODE
            + cmdCodeOn (string) 关命令CODE
            + created (string) 
            + creator (string) 
            + electricCurrent (int) 电流
            + enabled (int) 
            + flag (int) 
            + gatewayGid (int) 网关id
            + id (int)  自增主键
            + intervalValue (int) 前端的按钮 时间间隔
            + modified (string)  
            + modifier (int)
            + onOffState (int)  开关状态 1为开 0为关  2为未知状态（如果设备连线断掉即为未知状态）
            + pduPortNo (int) 和设备用这个序列号是绑定的。（1端口- 2端口）
            + power (int)  功率
            + voltage (int) 电压
            + yequipmentId (int) PDU的设备的ID
            + yequipmentIdJoin (int) 连入的设备ID
        + equipmentBtnGroups 
            + cloudCid  (int) 云端id
            + cmdBtnGroups
                + cloudCid  (int) 云端id
                + cmdAlias  (string) 命令的名字
                + cmdCode  (string) 命令的Code
                + cmdName  (string) 命令的名字
                + created  (string) 
                + creator  (int) 
                + enabled  (int) 
                + flag  (int) 云端id
                + forbidden  (int) 是否禁用
                + id  (int) 云端id
                + modified  (string) 
                + modifier  (int) 
                + ydrivecmdId  (int) 驱动cmd的ID
                + yequipmentbtngroupId  (int) 设备组ID
            + created (string) 
            + creator (int) 
            + enabled (int) 
            + flag (int) 
            + equipmentBtnGroups
                +
            + gatewayGid (int) 网关id
            + groupAndGroup (string)  这个是编组，不同的编组默认使用逗号隔开。（目前只支持2个组编组，同时出发的第二个组才触发命令）
            + groupName (string) 组名
            + groupNameAlias (string)   组别称
            + groupType (int) 1 开关组 2 输入组 3 输出组 4 预设组 5编组组
            + id (int)  自增主键id
            + modified (string)
            + modifier (int)  
         + portTypes 
            + builtIn (int)
            + cloudCid (int)  云端id
            + created (string)
            + creator (int)
            + defaultValue (string) 默认值  如果没有配置就是使用这个默认值，减少配置。
            + description (string) 描述
            + enabled (int)
            + flag (int)
            + gatewayGid (int) 网关id用于数据同步
            + id (int) 自增主键ID
            + modified (string)
            + modifier (int)
            + parentIdPorttype (int) 如果是本身就是父ID，则为0
            + probableValueList (string) 返回值使用英文（英文可以避免乱码），字符串用逗号隔开  on,off,on-off,等等
            + typeName (string) 端口类型名/属性名 类型名字：串口
            属性名：属性名比如波特率
            + valueType (int)  0 字符串类型 1 整数型 2 FLOAT型 等多种类型，可以写成枚举类放到代码中。
        + driveReadtypes
            + decimalPlaces (int)
            + cloudCid (int)  云端id
            + created (string)
            + creator (int)
            + ifLog (int)  1 加入日志  0 不加入日志
            + multiply (int) 数据矫正  相乘
            + enabled (int)
            + flag (int)
            + gatewayGid (int) 网关id用于数据同步
            + id (int) 自增主键ID
            + modified (string)
            + modifier (int)
            + plus (float) 数据矫正 相加或相减
            + readTypeAlias (string)  
            + unitName (string) 单位名称
            + ydriveId (int) 驱动ID
            + yreadtypeId (int) 读数类型ID
      
     
        + model （string） 设备品牌
        + primaryCategoryName （string） 一级分类名
        + secondCategoryName （string）二级分类名
        + ageLimit （int） 使用年限（1-6年）
        + yequipmentIdGateway （int） 所属网关设备id
        + yporttypeId （int） 设备端口类型id
        + ydriveId （string）设备驱动id
        + ycategoryId （int） 设备类型id
        + ybrandId （int）  设备品牌id
        + ypduId （int）设备pdu的id
        
        
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


## 设备状态监测(图表展示)  [GET]  /equipmentstatusmonitoring

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


### 空间使用排行 [GET]/spacegateway/spaceRanking
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

  ### 资产使用情况 


###寿命展示 [GET] /equipment/equipmentAssetOrMonitorOrMaintainOrLife
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

###使用年限展示 [GET] /equipment/equipmentAssetOrMonitorOrMaintainOrLife

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


### 资产统计 

####      品牌统计 [GET]/brand/info
+ Description
    + Author lyf
    
+ Parameters
    + page[page] (int)  页码
    + page[size] (int)  分页条数
    + include （Array[string]）
    + sort (Array[string]) 
    + collaborationSpaceId (long) 协作空间id
    + id （long） 机构id
+ ReturnData

    + id （long） 品牌id
    + brandName (string) 品牌名称
    + logo （string） 品牌logo
    + description (string) 描述
    + website (string) 描述
    + displayOrder （int） 排序
    + totals （int） 设备资产数量
        
+ Response 200

            {
        "data": [
                {
                  "id": 4,
                  "enabled": 1,
                  "creator": 0,
                  "modifier": 0,
                  "created": "2021-01-14 22:52:24",
                  "modified": "2021-01-14 22:52:24",
                  "brandName": "品牌1",
                  "logo": "string",
                  "description": "string",
                  "website": "string",
                  "displayOrder": 0,
                  "totals": 8
                },
                {
                  "id": 5,
                  "enabled": 1,
                  "creator": 0,
                  "modifier": 0,
                  "created": "2021-01-14 22:53:03",
                  "modified": "2021-01-14 22:53:03",
                  "brandName": "品牌2",
                  "logo": "string",
                  "description": "string",
                  "website": "string",
                  "displayOrder": 0,
                  "totals": 4
                },
                {
                  "id": 6,
                  "enabled": 1,
                  "creator": 0,
                  "modifier": 0,
                  "created": "2021-01-14 22:53:09",
                  "modified": "2021-01-14 22:53:09",
                  "brandName": "品牌3",
                  "logo": "string",
                  "description": "string",
                  "website": "string",
                  "displayOrder": 0,
                  "totals": 4
                },
                {
                  "id": 7,
                  "enabled": 1,
                  "creator": 0,
                  "modifier": 0,
                  "created": "2021-01-14 22:53:15",
                  "modified": "2021-01-14 22:53:15",
                  "brandName": "品牌4",
                  "logo": "string",
                  "description": "string",
                  "website": "string",
                  "displayOrder": 0,
                  "totals": 2
                },
                {
                  "id": 8,
                  "enabled": 1,
                  "creator": 0,
                  "modifier": 0,
                  "created": "2021-01-14 22:53:21",
                  "modified": "2021-01-14 22:53:21",
                  "brandName": "品牌5",
                  "logo": "string",
                  "description": "string",
                  "website": "string",
                  "displayOrder": 0,
                  "totals": 1
                }
  ]
  
  ]
}


####      分类统计[GET]/category/categorystatistics
+ Description
    + Author lyf
    
+ Parameters
+ ReturnData

    + id （long） 类型id
    + parentIdCategory (long) 父级id
    + categoryName （string） 类型名称
    + picture (string) 图片路径
    + description (string) 描述
    + displayOrder （int） 排序
    + equipmentAssetTotal （int） 设备资产数量
        
+ Response 200

            {
            "data": [
            {
              "id": 12,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-14 22:59:24",
              "modified": "2021-01-14 22:59:24",
              "parentIdCategory": 0,
              "categoryName": "主类2",
              "picture": "string",
              "description": "string",
              "displayOrder": 0,
              "equipmentAssetTotal": 0
            },
            {
              "id": 11,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-14 22:59:06",
              "modified": "2021-01-14 22:59:06",
              "parentIdCategory": 0,
              "categoryName": "主类1",
              "picture": "string",
              "description": "string",
              "displayOrder": 0,
              "equipmentAssetTotal": 19
            },
            {
              "id": 15,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-14 22:59:40",
              "modified": "2021-01-14 22:59:40",
              "parentIdCategory": 0,
              "categoryName": "主类5",
              "picture": "string",
              "description": "string",
              "displayOrder": 0,
              "equipmentAssetTotal": 0
            },
            {
              "id": 13,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-14 22:59:30",
              "modified": "2021-01-14 22:59:30",
              "parentIdCategory": 0,
              "categoryName": "主类3",
              "picture": "string",
              "description": "string",
              "displayOrder": 0,
              "equipmentAssetTotal": 0
            },
            {
              "id": 14,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-14 22:59:35",
              "modified": "2021-01-14 22:59:35",
              "parentIdCategory": 0,
              "categoryName": "主类4",
              "picture": "string",
              "description": "string",
              "displayOrder": 0,
              "equipmentAssetTotal": 0
            }
          ]
  
  ]
}


####      控制协议[GET]/drive/controllprotocol
+ Description
    + Author lyf
    
+ Parameters
+ ReturnData

    + id （long）驱动id
    + equipmentName (string) 驱动名称
    + totals （int） 设备资产数量
        
+ Response 200

            {
            "data": [
                {
                  "id": 3,
                  "enabled": 1,
                  "creator": 0,
                  "modifier": 0,
                  "created": "2021-01-14 23:07:19",
                  "modified": "2021-01-14 23:07:19",
                  "equipmentName": "驱动1",
                  "totals": 6
                },
                {
                  "id": 4,
                  "enabled": 1,
                  "creator": 0,
                  "modifier": 0,
                  "created": "2021-01-14 23:08:18",
                  "modified": "2021-01-14 23:08:18",
                  "equipmentName": "驱动2",
                  "totals": 7
                },
                {
                  "id": 5,
                  "enabled": 1,
                  "creator": 0,
                  "modifier": 0,
                  "created": "2021-01-14 23:08:29",
                  "modified": "2021-01-14 23:08:29",
                  "equipmentName": "驱动3",
                  "totals": 3
                },
                {
                  "id": 6,
                  "enabled": 1,
                  "creator": 0,
                  "modifier": 0,
                  "created": "2021-01-14 23:09:02",
                  "modified": "2021-01-14 23:09:02",
                  "equipmentName": "驱动4",
                  "totals": 3
                }
              ]
  
  ]
}



####      受控状态统计[GET] /equipment/equipmentcontrolled
+ Description
    + Author lyf
    
+ Parameters

+ ReturnData

    + organizationId （long） 机构id
    + organizationName (string) 机构名称
    + logo （string） 品牌logo
    + controlled (int) 可控设备资产数量
    + uncontrollable (int) 不可控设备资产数量

        
+ Response 200

            {
                 "data": [
                {
                  "organizationId": null,
                  "organizationName": null,
                  "controlled": 19,
                  "uncontrollable": 0
                }
            ]
  
 
}


####      设备保养信息更新已读[PATCH] /equipment/readOperate
+ Description
    + Author lyf
    
+ Parameters
    +RequestBody

        {
          "data": {
        
            "id": 71,
            "readable": 1
          }
       }
        
+ ReturnData
+ Response 200

##  楼层管理
+ Data
    + id (long)  - ID
    + floorNum  (int) 楼层号
    + buildingName  (string) 楼宇名称
    + buildingId (long)  楼宇ID
    + enabled (int)  - 使能  0禁止 1启用
    + creator (long) - 创建人
    + modifier (long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间

### 楼层新增 [POST] /floor
+ Description
    + Author Liukai
+ Request (application/json)
   
        {
        	"data": {
        		"buildingId": 2,
        		"floorNum": 6
        	}
        } 
+ Response 201

        {
          "data": {
            "id": 7,
            "type": "floor"
          }
        }
+ Response 400

        {
          "errors": [
            {
              "status": "400",
              "title": "Bad Request",
              "detail": "楼宇不存在"
            }
          ]
        }

### 楼层删除 [DELETE] /floor/{id}
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
              "detail": "无法删除，它是某些协作空间的关联数据！"
            }
          ]
        }
### 楼层更新  [PATCH] /floor/{id}
+ Description
    + Author Liukai
+ Parameters
    + id (long) - id 
+ Request (application/json)
   
        {
        	"data": {
        		"buildingId": 2,
        		"floorNum": 6
        	}
        } 
+ Response 200 
+ Response 400 

        {
          "errors": [
            {
              "status": "400",
              "title": "Bad Request",
              "detail": "楼宇不存在"
            }
          ]
        }
### 楼层列表 [GET] /floor
+ Description
    + Author Liukai
+ Parameters
    + id (long) - id 
+ Response 200 

        {
          "meta": {
            "totalPages": 1,
            "totalElements": 5,
            "size": 10,
            "number": 1,
            "numberOfElements": 5,
            "first": true,
            "last": true,
            "sort": null
          },
          "links": {
            "self": "/floor?page[number]=1&page[size]=10",
            "first": "/floor?page[number]=1&page[size]=10",
            "last": "/floor?page[number]=1&page[size]=10"
          },
          "data": [
            {
              "id": 1,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-07 14:17:08",
              "modified": "2021-01-07 14:17:10",
              "buildingId": 2,
              "floorNum": 6,
              "buildingName": "国商控股大厦"
            },
            {
              "id": 2,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-14 19:30:50",
              "modified": "2021-01-14 19:30:52",
              "buildingId": 3,
              "floorNum": 15,
              "buildingName": "阿里巴巴2号楼"
            },
            {
              "id": 3,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-15 15:39:06",
              "modified": "2021-01-15 15:39:08",
              "buildingId": 5,
              "floorNum": 1,
              "buildingName": "京东望京研发部"
            },
            {
              "id": 6,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-13 16:06:24",
              "modified": "2021-01-13 16:06:26",
              "buildingId": 2,
              "floorNum": 6,
              "buildingName": "国商控股大厦"
            },
            {
              "id": 7,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-15 16:25:28",
              "modified": "2021-01-15 16:33:19",
              "buildingId": 2,
              "floorNum": 16,
              "buildingName": "国商控股大厦"
            }
          ]
        }

### 协作空间管理
+ Data
    + id  (long)  - id
    + spaceName  (string)  -协作空间名字
    + logo  (string)  - logo 
    + floorId  (long) - 楼层ID
    + displayOrder  (int) - 排序 
    + floorNum  (int) -楼层号码
    + buildingId  (long) - 楼宇ID
    + buildingName  (string)  - 楼宇名字
    + organizationId  (long) - 机构ID
    + organizationName  (string)  -机构名字
    + unitPrice  (int) - 会议室单价每小时
    + seatingCapacity  (int) - 协作空间容量 

## 协作空间增加 [POST] /collaborationspace
+ Description
    + Author Liukai
+ Parameters 
+ Request (application/json)
  
        {
          "data": {
            "logo": "logo",
            "floorId": 2,
            "spaceName": "中会议室1",
            "unitPrice": 200,
            "seatingCapacity": 100
          }
        }  
+ Response 201

        {
          "data": {
            "id": 11,
            "type": "collaborationspace"
          }
        }
+ Response 400

        {
          "errors": [
            {
              "status": "400",
              "code": "全称不能为空",
              "title": "Bad Request",
              "detail": "全称不能为空",
              "source": {
                "pointer": "CollaborationSpace -> spaceName"
              }
            }
          ]
        }


## 协作空间删除 [DELETE] /collaborationspace/{id}
+ Description
    + Author Liukai
+ Parameters
+ Response 204
+ Response 400

## 协作空间更新  [PATCH] /collaborationspace/{id}
+ Description
    + Author Liukai
+ Parameters
    + id (long) - id 
+ Request (application/json)
    
        {
          "data": {
            "logo": "logo",
            "floorId": 2,
            "spaceName": "中会议室1",
            "unitPrice": 2001,
            "seatingCapacity": 100
          }
        }

+ Response 200
+ Response 400
    
        {
          "errors": [
            {
              "status": "400",
              "code": "全称不能为空",
              "title": "Bad Request",
              "detail": "全称不能为空",
              "source": {
                "pointer": "CollaborationSpace -> spaceName"
              }
            }
          ]
        }

## 协作空间详情 [GET] /collaborationspace/{id}
+ Description
    + Author Liukai
+ Parameters
    + id (long) - id 
+ Response 200
    
        {
          "data": {
            "id": 4,
            "spaceName": "协作空间2",
            "logo": "logo",
            "floorId": 1,
            "displayOrder": 0,
            "floorNum": 6,
            "buildingId": 2,
            "buildingName": "国商控股大厦",
            "organizationId": 2,
            "organizationName": "北京鼎迪",
            "unitPrice": 0,
            "seatingCapacity": 0
          }
        }

## 协作空间列表 [GET] /collaborationspace
+ Description
    + Author Liukai  
+ Parameters
    +  page[number] (int)  -页码
    +  page[size] (int)  -条数
    +  organizationId (long) -机构ID
    +  buildingId  (long) - 楼宇ID
    +  floorId  (long) - 楼层ID
    +  fullName (string) -机构名字
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
            "self": "/collaborationSpace?page[number]=1&page[size]=10",
            "first": "/collaborationSpace?page[number]=1&page[size]=10",
            "last": "/collaborationSpace?page[number]=1&page[size]=10"
          },
          "data": [
            {
              "id": 3,
              "spaceName": "协作空间1",
              "floorId": 7,
              "displayOrder": 0,
              "floorNum": 16,
              "buildingId": 2,
              "buildingName": "国商控股大厦",
              "organizationId": 2,
              "organizationName": "北京鼎迪",
              "unitPrice": 0,
              "seatingCapacity": 0,
              "logo": "logo",
              "created": "2021-01-14 23:52:23",
              "modified": "2021-01-14 23:52:23"
            },
            {
              "id": 4,
              "spaceName": "协作空间2",
              "floorId": 1,
              "displayOrder": 0,
              "floorNum": 6,
              "buildingId": 2,
              "buildingName": "国商控股大厦",
              "organizationId": 2,
              "organizationName": "北京鼎迪",
              "unitPrice": 0,
              "seatingCapacity": 0,
              "logo": "logo",
              "created": "2021-01-14 23:52:52",
              "modified": "2021-01-14 23:52:52"
            },
            {
              "id": 5,
              "spaceName": "协作空间3",
              "floorId": 1,
              "displayOrder": 0,
              "floorNum": 6,
              "buildingId": 2,
              "buildingName": "国商控股大厦",
              "organizationId": 2,
              "organizationName": "北京鼎迪",
              "unitPrice": 0,
              "seatingCapacity": 0,
              "logo": "logo",
              "created": "2021-01-14 23:52:57",
              "modified": "2021-01-14 23:52:57"
            },
            {
              "id": 6,
              "spaceName": "协作空间4",
              "floorId": 1,
              "displayOrder": 0,
              "floorNum": 6,
              "buildingId": 2,
              "buildingName": "国商控股大厦",
              "organizationId": 2,
              "organizationName": "北京鼎迪",
              "unitPrice": 0,
              "seatingCapacity": 0,
              "logo": "logo",
              "created": "2021-01-14 23:53:01",
              "modified": "2021-01-14 23:53:01"
            },
            {
              "id": 7,
              "spaceName": "协作空间5",
              "floorId": 1,
              "displayOrder": 0,
              "floorNum": 6,
              "buildingId": 2,
              "buildingName": "国商控股大厦",
              "organizationId": 2,
              "organizationName": "北京鼎迪",
              "unitPrice": 0,
              "seatingCapacity": 0,
              "logo": "logo",
              "created": "2021-01-14 23:53:10",
              "modified": "2021-01-14 23:53:10"
            },
            {
              "id": 8,
              "spaceName": "协作空间6",
              "floorId": 1,
              "displayOrder": 0,
              "floorNum": 6,
              "buildingId": 2,
              "buildingName": "国商控股大厦",
              "organizationId": 2,
              "organizationName": "北京鼎迪",
              "unitPrice": 0,
              "seatingCapacity": 0,
              "logo": "logo",
              "created": "2021-01-14 23:53:14",
              "modified": "2021-01-14 23:53:14"
            },
            {
              "id": 9,
              "spaceName": "协作空间7",
              "floorId": 1,
              "displayOrder": 0,
              "floorNum": 6,
              "buildingId": 2,
              "buildingName": "国商控股大厦",
              "organizationId": 2,
              "organizationName": "北京鼎迪",
              "unitPrice": 0,
              "seatingCapacity": 0,
              "logo": "logo",
              "created": "2021-01-14 23:53:19",
              "modified": "2021-01-14 23:53:19"
            },
            {
              "id": 10,
              "spaceName": "协作空间8",
              "floorId": 1,
              "displayOrder": 0,
              "floorNum": 6,
              "buildingId": 2,
              "buildingName": "国商控股大厦",
              "organizationId": 2,
              "organizationName": "北京鼎迪",
              "unitPrice": 0,
              "seatingCapacity": 0,
              "logo": "logo",
              "created": "2021-01-14 23:53:29",
              "modified": "2021-01-14 23:53:29"
            }
          ]
        }
### Email配置添加 [POST] /emailSmtpConfig
+ Description
    + Author lyf
+ Data
    + id  (long)  - id
    + gatewayGid  (string)  本地网关id
    + emailAddress  (string)  邮箱地址
    + emailServerAddress  (string) - 邮箱服务地址
    + smtpDomain  (string) -  STMP域
    + smtpPassword  (string) -STMP密码
    + smtpPort  (int) - STMP端口
    + smtpUsername  (string)  - STMP用户名
    + sslSwitch  (int) - STMP SSL 1 开启 0 关闭 
+ Request (application/json)
   
        {
        	"data": {
        		"cloudCid": 0,
                "created": "2021-01-18T06:45:28.577Z",
                "creator": 0,
                "emailAddress": "string",
                "emailServerAddress": "string",
                "enabled": 0,
                "flag": 0,
                "gatewayGid": 0,
                "id": 0,
                "modified": "2021-01-18T06:45:28.577Z",
                "modifier": 0,
                "smtpDomain": "string",
                "smtpPassword": "string",
                "smtpPort": 0,
                "smtpUsername": "string",
                "sslSwitch": 0,
                "yequipmentIdGateway": 0
        	}
        } 
+ Response 201

        {
          "data": {
            "id": 7,
            "type": "emailSmtpConfig"
          }
        }


## 云端用户管理
+ Data
    + id (long)  - ID
    + userName (string)  - 用户名
    + passWord  (string)  - 密码
    + headPortrait  (string) - 头像
    + organizationId   (long) -机构ID
    + company (string) - 公司
    + department  (string) - 部门
    + contactNumber (string) - 联系电话
    + mailbox  (string) - 邮件地址
    + organizationId   (long) - 机构ID 
    + roleCloudIds (List<long>) - 角色ID组（里面存放Long型）
    + roleClouds (List) - 角色对象内容
        +  id  (long)  -角色ID
        +  roleName  (string) - 角色名字
        +  roleDescription (string) - 角色描述
        +  organizationId   (long) - 机构ID 
        +  permissionCloudIds (list<Long>) - 权限ID组
        +  assetIds (Map) - 存放一个map (map存放了角色权限资源)
            + 0 (key值 设备资产) value类型为
            + 1 (key值 机构) value类型为
            + 2 (key值 楼宇) value类型为
            + 3 (key值 楼层) value类型为
            + 4 (key值 协作空间) value类型为
            + 5 (key值 API权限)  value类型为
            + 6 (key值 页面权限) value类型为
        +  organizations  --暂时无用
        +  buildings  --暂时无用
        +  floors  --暂时无用
        +  collaborationSpaces --暂时无用
        +  equipments --暂时无用
        +  pagePermissions --暂时无用
        +  apiPermissions --暂时无用
    + enabled (int)  - 使能  0禁止 1启用
    + creator (long) - 创建人
    + modifier (long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间

### 云端用户登录 [POST]  /usercloud/login
+ Description
    + Author Liukai
    + 在headers中增加一个key ,key为authorization，value为下面data里面的数据。
+ Request (application/json)

        {
          "data": {
            "passWord": "lk123456",
            "userName": "lk"
          }
        }

+ Response 200

        {
          "data": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJleHAiOjE2MTExMjk3NDMsInVzZXJJZCI6ImxrIn0.zyOrpAcq8x1vYyWHMfcjnFnKrhDDHHO320s46Xu524k"
        }

+ Response 400
        
        {
          "errors": [
            {
              "status": "400",
              "title": "Bad Request",
              "detail": "用户被禁用"
            }
          ]
        }

+ Response 403

        {
          "errors": [
            {
              "status": "403",
              "title": "Forbidden",
              "detail": "用户名或密码错误！"
            }
          ]
        }

### 云端用户退出登录 [POST] /usercloud/logout
+ Description
    + Author Liukai
    + 携带header中的authorization
+ Response 200


### 云端用户增加 [POST] /usercloud
+ Description
    + Author Liukai
+ Request (application/json)
    
        {
          "data": {
            "id": 18,
            "userName": "cy",
            "passWord":"cy123456",
            "headPortrait": "headPortraitString",
            "company": "家人公司",
            "department": "IIT",
            "contactNumber": "13126122398",
            "mailbox": "85077@qq.com",
            "roleCloudIds": [
              1,
              14
            ]
          }
        }        
        
+ Response 201

        {
          "data": {
            "id": 18,
            "type": "usercloud"
          }
        }

+ Response 400
    

        {
          "errors": [
            {
              "status": "400",
              "title": "Bad Request",
              "detail": "请登录,再新增用户."
            }
          ]
        }
    
        {
          "errors": [
            {
              "status": "400",
              "code": "手机/电话号码格式不正确",
              "title": "Bad Request",
              "detail": "手机/电话号码格式不正确",
              "source": {
                "pointer": "UserCloud -> contactNumber"
              }
            }
          ]
        }

###  云端用户禁用  [DELETE] /usercloud/{id}
+ Description
    + Author Liukai
+ Parameters
    + id (long) - id 
+ Response 204
+ Response 400

### 云端用户更新 [PATCH] /usercloud/{id}
+ Description
    + Author Liukai
+ Parameters
    + id (long) - id 
+ Request (application/json)
    
        {
        	"data": {
        		"userName": "cy1",
        		"headPortrait": "headPortraitString",
        		"company": "家人公司",
        		"department": "IIT",
        		"contactNumber": "13126122398",
        		"mailbox": "85077@qq.com",
        		"organizationId": 1,
        		"roleCloudIds": [
        			1,
        			14
        		]
        	}
        }

+ Response 200

+ Response 400
    
        {
          "errors": [
            {
              "status": "400",
              "code": "手机/电话号码格式不正确",
              "title": "Bad Request",
              "detail": "手机/电话号码格式不正确",
              "source": {
                "pointer": "UserCloud -> contactNumber"
              }
            }
          ]
        }


### 云端用户详情 [GET] /usercloud/{id}
+ Description
    + Author Liukai
+ Parameters
    + id (long) - id 
+ Response 200

        {
          "data": {
            "id": 18,
            "userName": "cy1",
            "headPortrait": "headPortraitString",
            "company": "家人公司",
            "department": "IIT",
            "contactNumber": "13126122398",
            "mailbox": "85077@qq.com",
            "organizationId": 1,
            "roleCloudIds": [
              1,
              14
            ],
            "roleClouds": [
              {
                "id": 1,
                "roleName": "SUPER_ADMIN",
                "permissionCloudIds": [],
                "assetIds": {},
                "organizations": [],
                "buildings": [],
                "floors": [],
                "collaborationSpaces": [],
                "equipments": [],
                "pagePermissions": [],
                "apiPermissions": {}
              },
              {
                "id": 14,
                "roleName": "拼多多管理员",
                "permissionCloudIds": [],
                "assetIds": {},
                "organizations": [],
                "buildings": [],
                "floors": [],
                "collaborationSpaces": [],
                "equipments": [],
                "pagePermissions": [],
                "apiPermissions": {}
              }
            ]
          }
        }

### 云端用户列表 [GET] /usercloud
+ Description
    + Author Liukai
+ Parameters
    + page[number] (int)  -页码
    + page[size] (int)  -条数
    + sort  (string) -排序 例如 sort=displayOrd1er,-modified
    + filter[userName:like] (string) -全名 例如 filter[userName:like]=%sdff%

+ Request (application/json)
+ Response 200
    
        {
          "meta": {
            "totalPages": 2,
            "totalElements": 14,
            "size": 10,
            "number": 1,
            "numberOfElements": 10,
            "first": true,
            "last": false,
            "sort": null
          },
          "links": {
            "self": "/usercloud?page[number]=1&page[size]=10",
            "first": "/usercloud?page[number]=1&page[size]=10",
            "next": "/usercloud?page[number]=2&page[size]=10",
            "last": "/usercloud?page[number]=2&page[size]=10"
          },
          "data": [
            {
              "id": 1,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-04 18:40:38",
              "modified": "2021-01-15 18:38:41",
              "userName": "admin",
              "headPortrait": "$2a$04$u7s5wq8J7US4bQLI3bizzOnSvOAs7epeMOwHfRd8BgmoLPx5sdwDe",
              "company": "budee",
              "department": "It",
              "contactNumber": "13126822398",
              "mailbox": "8507@qq.com",
              "organizationId": 0
            },
            {
              "id": 5,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-14 18:04:26",
              "modified": "2021-01-15 18:38:41",
              "userName": "628a94cb-aec8-4ee5-9dce-a20024cdc326",
              "organizationId": 10
            },
            {
              "id": 7,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-14 18:37:14",
              "modified": "2021-01-15 18:38:41",
              "userName": "d314c821-df0c-4c4f-8c70-69ab1e008168",
              "organizationId": 17
            },
            {
              "id": 8,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-15 09:49:11",
              "modified": "2021-01-15 18:38:41",
              "userName": "b6cff098-1dce-415d-a55f-97af0f110bc4",
              "organizationId": 18
            },
            {
              "id": 9,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-15 09:51:06",
              "modified": "2021-01-15 18:38:41",
              "userName": "be55a3ef-91c1-478a-b7d6-dddefb8bb268",
              "organizationId": 19
            },
            {
              "id": 10,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-15 09:52:55",
              "modified": "2021-01-15 18:38:41",
              "userName": "b7084b06-b1cb-4364-877e-83b915ae7495",
              "organizationId": 20
            },
            {
              "id": 11,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-15 09:54:10",
              "modified": "2021-01-15 18:38:41",
              "userName": "6d62a942-7c14-4e94-9800-1ab9c84643c7",
              "organizationId": 21
            },
            {
              "id": 12,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-15 11:38:38",
              "modified": "2021-01-15 18:38:41",
              "userName": "3e2288da-3117-48d4-a2eb-87cc6e5fab04",
              "organizationId": 22
            },
            {
              "id": 13,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-15 11:42:07",
              "modified": "2021-01-15 18:38:41",
              "userName": "f289d8fd-b1c1-48d0-b180-071175379bb4",
              "organizationId": 23
            },
            {
              "id": 14,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-18 14:45:29",
              "modified": "2021-01-18 14:45:29",
              "userName": "91c4e7a9-ef7a-41a2-ab2f-4b5859f40dfd",
              "organizationId": 24
            }
          ]
        }

### 云端当前用户 [GET] /usercloud/currentUserInfo
+ Description
    + Author Liukai
+ Request (application/json)
+ Response 200

        {
          "data": {
            "id": 1,
            "userName": "admin",
            "headPortrait": "$2a$04$u7s5wq8J7US4bQLI3bizzOnSvOAs7epeMOwHfRd8BgmoLPx5sdwDe",
            "company": "budee",
            "department": "It",
            "contactNumber": "13126822398",
            "mailbox": "8507@qq.com",
            "organizationId": 0,
            "roleCloudIds": [
              1
            ],
            "roleClouds": [
              {
                "id": 1,
                "roleName": "SUPER_ADMIN",
                "permissionCloudIds": [],
                "assetIds": {},
                "organizations": [],
                "buildings": [],
                "floors": [],
                "collaborationSpaces": [],
                "equipments": [],
                "pagePermissions": [],
                "apiPermissions": {}
              }
            ]
          }
        }
        
        
### 设备开合统计 [GET]/logEquipmentMalfunction/equipmentopenclosestatistics

+ Description
    + Author lyf
+ Data
+ Request (application/json)
   
+ ReponseData
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
                "logEquipmentTimesMalfunctiontimesList": null
              }
        }

### 用户人数统计 [GET]/usercloud/usercountStatistics

+ Description
    + Author lyf
+ Data
+ Request (application/json)
   
+ ReponseData
     + userCount （int） 用人数
     + lastLoginTime (string) 上次登录时间
       
+ Response 200

        {
          "data": {
                "userCount": 3,
                "lastLoginTime": "2021-01-20 20:15:04"
        }
        }
        
### Email发送 [POST]/emailSmtpConfig/sendmaill

+ Description
    + Author lyf
+ Data
+ Request (application/json)
    + emailServerAddress （string）邮箱地址
    + emailAddress （string） 邮件服务地址
    + smtpUsername （string）STMP用户名
    + smtpPassword （string） STMP用密码
    + smtpPort （int） STMP端口
    + mailContent （string）发送的邮箱内容
    + receiveMail （string） 发送的目的邮箱地址

+ Response 201

        "邮件发送成功'"

+ Response 400

        {
              "errors": [
                {
                  "status": "400",
                  "title": "Bad Request",
                  "detail": "Mail server connection failed; nested exception is com.sun.mail.util.MailConnectException: Couldn't connect to host, port: iotadmin001@163.com, 0; timeout -1;\n  nested exception is:\n\tjava.net.UnknownHostException: iotadmin001@163.com. Failed messages: com.sun.mail.util.MailConnectException: Couldn't connect to host, port: iotadmin001@163.com, 0; timeout -1;\n  nested exception is:\n\tjava.net.UnknownHostException: iotadmin001@163.com"
                }
              ]
        }


### 设备日志列表 [GET] /logEquipment
+ Description

+ Parameters
    + data
        + authorization (string)  令牌
        + dateMaxStr (string) 结束时间
        + page[number] （int）页码
        + page[size] （int）条数
        + sort （Array[string]） 排序
        + dateMinStr （string）开始时间
        + eventContent （string）事件内容
        + eventResult （int）1执行成功，0执行失败'
        + filter[equipmentId] （long）设备id
        + filter[logLevel] （int）日志级别 0:错误 1:警告 2:信息 3:调试
        + filter[userId] （long）用户id
        + gatewayId （long）网关id
        
+ Request (application/json)

+ ReturnData
    + id （long） 端口类型id
    + enabled （int）是否启用
    + creator （long）创建人
    + modifier （long）修改人
    + gatewayGid （long）本地驱动id
    + logLevel （int）日志级别   0:错误       1:警告    2:信息    3:调试
    + operateType （int） 0 常规操作 1是场景操作 2是计划任务
    + operateId （long）实际操作id就是场景日志的id或者计划任务的ID
    + eventContent （string） 事件内容
    + eventResult （int）1执行成功，0执行失败
    + malfunctionTimes (int) 故障次数
    + analyzed （int） 是否被统计 0未被分析，1已经被分析
    + readed (int) 0未读，1已读
    + upload （int）0未上传，1已经上传
    + gatewayName （string）网关名
    + userName （string）用户名称
    + equipmentModel （string）型号
    + equipmentName （string）设备名称
    + yequipmentId （long）设备id
        
+ Response 200
    
        {
          "data": [
            {
              "id": 1,
              "enabled": 1,
              "creator": 1,
              "modifier": 0,
              "created": "2021-01-20 18:02:25",
              "modified": "2021-01-20 18:02:25",
              "gatewayGid": 83968,
              "flag": 0,
              "logLevel": 1,
              "operateType": 0,
              "operateId": 0,
              "eventContent": "没有电量设备，可以进行电量统计",
              "eventResult": 0,
              "malfunctionTimes": 0,
              "analyzed": 0,
              "readed": 1,
              "upload": 0,
              "gatewayName": "测试网关",
              "userName": "用户1",
              "equipmentModel": "sw010",
              "equipmentName": "中控",
              "yequipmentId": 136
            },
            {
              "id": 2,
              "enabled": 1,
              "creator": 1,
              "modifier": 0,
              "created": "2021-01-20 18:02:28",
              "modified": "2021-01-20 18:02:28",
              "gatewayGid": 83969,
              "flag": 0,
              "logLevel": 1,
              "operateType": 0,
              "operateId": 0,
              "eventContent": "没有电量设备，可以进行电量统计",
              "eventResult": 0,
              "malfunctionTimes": 0,
              "analyzed": 0,
              "readed": 1,
              "upload": 0,
              "gatewayName": "测试网关",
              "userName": "用户1",
              "equipmentModel": "sw010",
              "equipmentName": "中控",
              "yequipmentId": 136
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


### 系统日志列表 [GET] /logSystem
+ Description

+ Parameters
    + data
        + authorization (string)  令牌
        + dateMaxStr (string) 结束时间
        + page[number] （int）页码
        + page[size] （int）条数
        + sort （Array[string]） 排序
        + dateMinStr （string）开始时间
        + eventContent （string）事件内容
        + filter[userId] （long）用户id
        
+ Request (application/json)

+ ReturnData
    + id （long） 端口类型id
    + enabled （int）是否启用
    + creator （long）创建人
    + modifier （long）修改人
    + eventContent （string） 事件内容
    + userName （string）用户名称
    + yequipmentIdGateway （long）中控设备ID
        
+ Response 200
    
        {
          "data": [
            {
              "id": 1036,
              "enabled": 1,
              "creator": 1,
              "created": "2020-12-01 19:41:05",
              "eventContent": "插入日志",
              "userName": "用户1",
              "yequipmentIdGateway": 0
            },
            {
              "id": 1037,
              "enabled": 1,
              "creator": 1,
              "created": "2020-12-01 19:43:00",
              "eventContent": "插入日志",
              "userName": "用户1",
              "yequipmentIdGateway": 0
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


### 空间能耗排行 [GET] /logUsedTimesElectric
+ Description

+ Parameters
    + data
        + authorization (string)  令牌
        + dateMaxStr (string) 结束时间
        + page[number] （int）页码
        + page[size] （int）条数
        + sort （string） 排序 （正序 eneryValueSum 反序 -eneryValueSum）
        + dateMinStr （string）开始时间
        
+ Request (application/json)

+ ReturnData
    + id （long） 端口类型id
    + enabled （int）是否启用
    + creator （long）创建人
    + modifier （long）修改人
    + onlyCode （string） 序列号
    + ipAddress （string）IP地址
    + publicIpAddress （string）公网ip
    + location （string）地理位置
    + organizationName （string）机构
    + collaborationSpace （string）协作空间
    + cpuId （string）cpuid
    + diskId （string）硬盘唯一码
    + mainboardId （string）主板唯一号
    + realLocation （string）实时位置
    + versionNo （string）版本
    + serviceConfReg （int）1正常 0异常
    + serviceCoreData （int）1正常 0异常
    + serviceMetadata （int）1正常 0异常
    + serviceCommand （int）1正常 0异常
    + runningStatus （int）运行状态 （1正常 0异常）
    + environmentEquipmentIds （string）环境设备id
    + holderEquipmentIds （string）占位器（判断会议室是否有人）
    + energyEquipmentIds (string) 记录耗能设备的电量
    + conferenceReservationStatistics （int）0不启用预约系统计数  1使用自带预约系统 2使用第三方预约系统计数
    + specializedAssetId （long）
    + activate （int）激活状态（1 激活 0未激活）
    + eneryValueTb （double）能耗同步
    + eneryValueHb (Double) 能耗环比
    + eneryValueSum （double）使用能耗
    + times （int）使用次数
    + ranking （int）排名
    + yequipmentId （long）设备id
        
+ Response 200
    
        {
          "data": [
            {
              "id": 17,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "modified": "2021-01-22 14:46:30",
              "gatewayGid": 2,
              "onlyCode": "阿莎",
              "ipAddress": "阿三哥",
              "gatewayName": "测试网关",
              "serviceConfReg": 0,
              "serviceCoreData": 0,
              "serviceMetadata": 0,
              "serviceCommand": 0,
              "conferenceReservationStatistics": 0,
              "specializedAssetId": 0,
              "activate": 0,
              "eneryValueSum": 0,
              "times": 0,
              "ranking": 2,
              "yequipmentId": 132
            },
            {
              "id": 16,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-21 14:22:07",
              "modified": "2021-01-21 19:23:19",
              "gatewayGid": 2,
              "flag": 0,
              "onlyCode": "YzhjOWNmMmEyMzMxNGU0M2M4OWE3OTMxOWRlZTIyYWU=",
              "ipAddress": "127.0.0.1",
              "publicIpAddress": "127.0.0.1",
              "gatewayName": "中会网关1",
              "cloudAddress": "127.0.0.1",
              "location": "太平宝迪",
              "organizationName": "太平宝迪",
              "collaborationSpace": "太平宝迪",
              "cpuId": "1",
              "diskId": "2",
              "mainboardId": "2",
              "realLocation": "3",
              "versionNo": "4",
              "serviceConfReg": 4,
              "serviceCoreData": 0,
              "serviceMetadata": 0,
              "serviceCommand": 0,
              "runningStatus": 1,
              "environmentEquipmentIds": "1",
              "holderEquipmentIds": "1",
              "energyEquipmentIds": "1",
              "conferenceReservationStatistics": 1,
              "specializedAssetId": 2,
              "activate": 0,
              "eneryValueTb": 277.78,
              "eneryValueHb": 41.67,
              "eneryValueSum": 34,
              "times": 33,
              "ranking": 1,
              "yequipmentId": 136
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

### 设备保养个数统计 [get]/equipment/equipmentmaintenancecount

+ Description
    + Author lyf
+ Data
+ Request (application/json)
   
 
+ ReponseData
    + runningCount 运行个数
    + offCount 关闭个数
    + malfunctionCount 故障数
    + offLineCount 离线个数
    + equipmentCount 设备总数
    + warnCount 报警数
    + maintainCount 设备保养个数
+ Response 201

         
        {
          "data": {
                    "runningCount": 3,
                    "offCount": "",
                    "malfunctionCount": 3,
                    "offLineCount":0
                    "equipmentCount": 3,
                    "warnCount":0 ,
                    "maintainCount": 5
                }
        }

+ Response 400


### 设备能耗排行 [GET] /logUsedTimesElectric/equipmentPage
+ Description

+ Parameters
    + data
        + authorization (string)  令牌
        + dateMaxStr (string) 结束时间
        + page[number] （int）页码
        + page[size] （int）条数
        + sort （string） 排序 （正序 currentElectricValue 反序 -currentElectricValue）
        + dateMinStr （string）开始时间
        
+ Request (application/json)

+ ReturnData
    + id （long） 端口类型id
    + enabled （int）是否启用
    + creator （long）创建人
    + modifier （long）修改人
    + voltage （double） 电压
    + current （double）电流
    + power （double）当前功率
    + currentElectricValue （double）能耗
    + analyzed （int）是否已经分析 0未分析  1分析
    + equipmentName （string）设备名
    + anotherName （string）别名
    + model （string）型号
    + gatewayName （string）网关名
    + currentElectricValueHb （double）环比
    + currentElectricValueTb （double）同比
    + yequipmentId （long）设备id
    + ranking （int）排行
        
+ Response 200
    
        {
          "data": [
            {
              "totalPages": 1,
              "totalElements": 2,
              "size": 10,
              "number": 1,
              "logEnergyGeneralList": [
                {
                  "id": 5,
                  "created": "2021-01-22 14:25:22",
                  "gatewayGid": 1,
                  "voltage": 6,
                  "current": 7,
                  "power": 2,
                  "currentElectricValue": 9,
                  "analyzed": 0,
                  "equipmentName": "七合一环境传感器",
                  "anotherName": "中会七合一",
                  "model": "SM300D2MOD",
                  "gatewayName": "测试中控",
                  "currentElectricValueHb": 350,
                  "currentElectricValueTb": 125,
                  "yequipmentId": 142,
                  "ranking": 1
                },
                {
                  "id": 10,
                  "created": "2021-01-22 17:02:40",
                  "gatewayGid": 1,
                  "voltage": 48,
                  "current": 9,
                  "power": 2,
                  "currentElectricValue": 4,
                  "analyzed": 0,
                  "equipmentName": "七合一环境传感器",
                  "anotherName": "修改",
                  "model": "SM300D2MOD",
                  "gatewayName": "测试中控",
                  "currentElectricValueHb": 300,
                  "yequipmentId": 143,
                  "ranking": 2
                }
              ],
              "equipmentList": null,
              "gateInfoListDtoList": null
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

## 云端角色管理
+ Data
    + id (long)  - ID
    + roleName (string) - 角色名
    + roleDescription (string) -角色描述
    + organizationId (long)  -机构ID
    + isAdmin  (int)  -是否是管理员 0 非管理员 1 超管 2租户管理员(系统生成) 
    + permissionCloudIds (list<long>) -权限id的list
    + assetIds (Map) - 存放一个map (map存放了角色权限资源)
        + 0 (key值 设备资产) value类型为Set<String>
            + 特殊值 
                + CollaborationSpace_ID_Equipment_1 -协作空间ID下面所有的设备 (中间的ID是数字)
                + CollaborationSpace_ID_Equipment_0  -协作空间ID下面没有一个设备 (中间的ID是数字)
        + 1 (key值 机构) value类型为Set<String>
            + 特殊值 
                + Organization_ID_Organization_1 -机构ID下面所有子机构 (中间的ID是数字)
                + Organization_ID_Organization_0 -机构ID下面没有一个机构 (中间的ID是数字)
        + 2 (key值 楼宇) value类型为Set<String>
            + 特殊值 
                + Organization_ID_Building_1 -机构ID下面所有楼宇 (中间的ID是数字)
                + Organization_ID_Building_0 -机构ID下面没有一个楼宇 (中间的ID是数字)
        + 3 (key值 楼层) value类型为Set<String>
            + 特殊值 
                + Building_ID_Floor_1 -楼宇ID下面所有楼层 (中间的ID是数字)
                + Building_ID_Floor_0 -楼宇ID下面没有一个楼层 (中间的ID是数字)
        + 4 (key值 协作空间) value类型为Set<String>
            + 特殊值 
                + Floor_ID_CollaborationSpace_1 -楼层ID下面所有协作空间 (中间的ID是数字)
                + Floor_ID_CollaborationSpace_0 -楼层ID下面没有一个协作空间 (中间的ID是数字)
        + 5 (key值 API权限)  value类型为Set<String>
        + 6 (key值 页面权限) value类型为Set<String>
    + organizations (list<Organization>)
        + id (long) -id 
        + fullName (string) 机构全名
    + buildings (list<Building>)
        + id  (long) -id
        + buildingName (string) 楼宇名
    + floors (list<Floor>)
        + id (long) 楼层ID
        + floorNum  (int)  楼层(第几层)
    + collaborationSpaces (list<CollaborationSpace>)
        + id (long) -id
        + spaceName (string)  -协作空间名
    + equipments (list<Equipment>)
        + id (long) -id
        + equipmentName (string) 设备名字
    + pagePermissions (list<>)
        + id (long) -id
        + permissionType (int) 权限类型，0：api，1：页面
        + permissionGroup (int) 0：不需要分组
        + permissionName (string)  权限名
        + permissionDescribe (string) 权限描述
    + apiPermissions (map<Integer,List<PermissionCloud>>)
        + key值通过接口 （/permissionCloud/findPermissionsGroup） 进行匹配就可以了
        + value值
            + id (long)  -id
            + permissionType (int) 权限类型，0：api，1：页面
            + permissionGroup (int)  0：不需要分组，1：品牌，2：分类，3：分类命令，4：设备型号，5：设备资产，6：控制协议，7：机构，8：楼宇，9：楼层，10：协作空间，11：用户，12：角色，13：权限，14：系统日志，15：设备日志，16：邮箱配置，17：采集间隔配置，18：智慧场景  100：其他
            + permissionName   (string) 权限名
            + permissionDescribe (string) 权限描述
    + enabled (int)  - 使能  0禁止 1启用
    + creator (long) - 创建人
    + modifier (long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间

### 云端角色新增  [POST] /rolecloud
+ Description
    + Author Liukai
+ Request (application/json)
    
        {
        	"data": {
        		"roleName": "公牛空间管理员2",
        		"roleDescription": "公牛空间管理员权限,有该机构的最大权限2",
        		"organizationId": 30,
        		"isAdmin": 0,
        		"permissionCloudIds": [],
        		"assetIds": {
        			"0": [],
        			"1": [
        				"30"
        			],
        			"2": [
        				"14",
        				"15"
        			],
        			"3": [
        				"25",
        				"26",
        				"27",
        				"28"
        			],
        			"4": [
        				"13",
        				"14"
        			],
        			"5": [
        				"12",
        				"15"
        			],
        			"6": [
        				"3",
        				"5"
        			]

        		}
        	}
        }

+ Response 201
    
        {
          "data": {
            "id": 36,
            "type": "rolecloud"
          }
        }
+ Response 400

        {
          "errors": [
            {
              "status": "400",
              "title": "Bad Request",
              "detail": "用户登录异常，请重新登录，然后再保存角色"
            }
          ]
        }

       {
          "errors": [
            {
              "status": "400",
              "title": "Bad Request",
              "detail": "新角色中机构权限超过授权者的最大权限"
            }
          ]
        }  

### 云端角色删除 [DELETE] /rolecloud/{id}
+ Description
    + Author Liukai
+ Parameters
    + id (long) - id  
+ Request (application/json)
+ Response 204

### 云端角色修改  [PATCH] /rolecloud/{id}
+ Description
    + Author Liukai
+ Parameters
    + id (long) - id   
+ Request (application/json)

        {
        	"data": {
        		"roleName": "公牛空间管理员25",
        		"roleDescription": "公牛空间管理员权限,有该机构的最大权限2",
        		"organizationId": 30,
        		"isAdmin": 0,
        		"permissionCloudIds": [],
        		"assetIds": {
        			"0": [],
        			"1": [
        				"30"
        			],
        			"2": [
        				"14",
        				"15"
        			],
        			"3": [
        				"25",
        				"26",
        				"27",
        				"28"
        			],
        			"4": [
        			]
        		}
        	}
        }
+ Response 200
+ Response 400
    
        {
          "errors": [
            {
              "status": "400",
              "title": "Bad Request",
              "detail": "角色中机构权限超过授权者的最大权限"
            }
          ]
        }

### 云端角色详情 [GET] /rolecloud/{id}
+ Description
    + Author Liukai
+ Parameters
    + id (long) - id   
+ Request (application/json)
+ Response 200

        {
          "data": {
            "id": 38,
            "enabled": 1,
            "creator": 1,
            "modifier": 1,
            "created": "2021-01-26 14:32:15",
            "modified": "2021-01-26 16:11:19",
            "roleName": "公牛空间管理员34",
            "roleDescription": "公牛空间管理员权限,有该机构的最大权限2",
            "organizationId": 30,
            "isAdmin": 0,
            "permissionCloudIds": [],
            "assetIds": {
              "0": [
                "3"
              ],
              "1": [
                "30"
              ],
              "2": [
                "14",
                "15"
              ],
              "3": [
                "25",
                "26",
                "27",
                "28"
              ],
              "4": [
                "13",
                "14"
              ]
            },
            "organizations": [
              {
                "id": 30,
                "fullName": "公牛空间"
              }
            ],
            "buildings": [
              {
                "id": 14,
                "buildingName": "大楼1号"
              },
              {
                "id": 15,
                "buildingName": "大楼2号"
              }
            ],
            "floors": [
              {
                "id": 25,
                "floorNum": 12
              },
              {
                "id": 26,
                "floorNum": 11
              },
              {
                "id": 27,
                "floorNum": 11
              },
              {
                "id": 28,
                "floorNum": 12
              }
            ],
            "collaborationSpaces": [
              {
                "id": 13,
                "spaceName": "报告厅1"
              },
              {
                "id": 14,
                "spaceName": "报告厅2"
              }
            ],
            "equipments": [
              {
                "id": 3,
                "equipmentName": "七合一（勿删）"
              }
            ],
            "pagePermissions": [
              {
                "id": 3,
                "permissionType": 1,
                "permissionGroup": 0,
                "permissionName": "admin_log",
                "permissionDescribe": "日志"
              },
              {
                "id": 5,
                "permissionType": 1,
                "permissionGroup": 0,
                "permissionName": "admin_info_tips",
                "permissionDescribe": "信息提示"
              }
            ],
            "apiPermissions": {
              "1": [
                {
                  "id": 7,
                  "permissionType": 0,
                  "permissionGroup": 1,
                  "permissionName": "brand:list",
                  "permissionDescribe": "品牌列表"
                },
                {
                  "id": 8,
                  "permissionType": 0,
                  "permissionGroup": 1,
                  "permissionName": "brand:details",
                  "permissionDescribe": "品牌详情"
                },
                {
                  "id": 9,
                  "permissionType": 0,
                  "permissionGroup": 1,
                  "permissionName": "brand:add",
                  "permissionDescribe": "品牌添加"
                }
              ],
              "2": [
                {
                  "id": 12,
                  "permissionType": 0,
                  "permissionGroup": 2,
                  "permissionName": "category:list",
                  "permissionDescribe": "分类列表"
                },
                {
                  "id": 13,
                  "permissionType": 0,
                  "permissionGroup": 2,
                  "permissionName": "category:details",
                  "permissionDescribe": "分类详情"
                }
              ]
            }
          }
        }
    
+ Response 400

### 云端角色列表  [GET]  /rolecloud
+ Description
    + Author Liukai
+ Parameters
    + page[number] (int)  -页码
    + page[size] (int)  -条数
    + sort  (string) -排序 例如 sort=-modified
    + filter[roleName:like] (string) -全名 例如 filter[roleName:like]=%sdff%  
+ Response 200
    
        {
          "meta": {
            "totalPages": 3,
            "totalElements": 13,
            "size": 5,
            "number": 1,
            "numberOfElements": 5,
            "first": true,
            "last": false,
            "sort": null
          },
          "links": {
            "self": "/rolecloud?page[number]=1&page[size]=5",
            "first": "/rolecloud?page[number]=1&page[size]=5",
            "next": "/rolecloud?page[number]=2&page[size]=5",
            "last": "/rolecloud?page[number]=3&page[size]=5"
          },
          "data": [
            {
              "id": 1,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-04 14:28:58",
              "modified": "2021-01-04 14:29:00",
              "roleName": "SUPER_ADMIN",
              "roleDescription": "超级管理员，不可删除",
              "organizationId": 0,
              "isAdmin": 1
            },
            {
              "id": 2,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-20 13:55:59",
              "modified": "2021-01-20 13:56:01",
              "roleName": "太平宝迪中会议室管理员",
              "roleDescription": "太平宝迪中会议室管理员",
              "organizationId": 1,
              "isAdmin": 0
            },
            {
              "id": 7,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-14 18:04:26",
              "modified": "2021-01-14 18:04:26",
              "roleName": "上海银十通科技有限公司管理员",
              "organizationId": 10,
              "isAdmin": 2
            },
            {
              "id": 12,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-14 18:37:13",
              "modified": "2021-01-14 18:37:13",
              "roleName": "阿里巴巴管理员",
              "roleDescription": "阿里巴巴管理员权限,有该机构的最大权限",
              "organizationId": 17,
              "isAdmin": 2
            },
            {
              "id": 13,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2021-01-15 09:49:11",
              "modified": "2021-01-15 09:49:11",
              "roleName": "京东商城管理员",
              "roleDescription": "京东商城管理员权限,有该机构的最大权限",
              "organizationId": 18,
              "isAdmin": 2
            }
          ]
        }
    
+ Response 400

## 云端权限管理
+ Data
    + id (long)  - ID
    + permissionType (int) -权限类型，0：api，1：页面
    + permissionGroup (int)  -权限组 0：不需要分组，1：品牌，2：分类，3：分类命令，4：设备型号，5：设备资产，6：控制协议，7：机构，8：楼宇，9：楼层，10：协作空间，11：用户，12：角色，13：权限，14：系统日志，15：设备日志，16：邮箱配置，17：采集间隔配置，18：智慧场景  100：其他
    + permissionName (string) -权限名
    + permissionDescribe (string)  -权限描述
    + url (string) -访问路径
    + enabled (int)  - 使能  0禁止 1启用
    + creator (long) - 创建人
    + modifier (long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间

### 权限列表  [GET] /permissionCloud
+ Description
    + Author Liukai
    + 得到所有可见权限
+ Parameters
    + page[number] (int)  -页码
    + page[size] (int)  -条数
+ Response 200

        {
          "meta": {
            "totalPages": 15,
            "totalElements": 74,
            "size": 5,
            "number": 1,
            "numberOfElements": 5,
            "first": true,
            "last": false,
            "sort": null
          },
          "links": {
            "self": "/permissionCloud?page[number]=1&page[size]=5",
            "first": "/permissionCloud?page[number]=1&page[size]=5",
            "next": "/permissionCloud?page[number]=2&page[size]=5",
            "last": "/permissionCloud?page[number]=15&page[size]=5"
          },
          "data": [
            {
              "id": 3,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-04-16 10:23:47",
              "modified": "2020-04-16 10:23:50",
              "permissionType": 1,
              "permissionGroup": 0,
              "permissionName": "admin_log",
              "permissionDescribe": "日志"
            },
            {
              "id": 5,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-04-16 10:23:58",
              "modified": "2020-04-16 10:24:00",
              "permissionType": 1,
              "permissionGroup": 0,
              "permissionName": "admin_info_tips",
              "permissionDescribe": "信息提示"
            },
            {
              "id": 6,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-04-16 10:24:03",
              "modified": "2020-04-16 10:24:06",
              "permissionType": 1,
              "permissionGroup": 0,
              "permissionName": "admin_rbac",
              "permissionDescribe": "权限管理"
            },
            {
              "id": 7,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-11-06 11:13:24",
              "modified": "2020-11-06 11:13:24",
              "permissionType": 0,
              "permissionGroup": 1,
              "permissionName": "brand:list",
              "permissionDescribe": "品牌列表"
            },
            {
              "id": 8,
              "enabled": 1,
              "creator": 0,
              "modifier": 0,
              "created": "2020-11-06 11:13:24",
              "modified": "2020-11-06 11:13:24",
              "permissionType": 0,
              "permissionGroup": 1,
              "permissionName": "brand:details",
              "permissionDescribe": "品牌详情"
            }
          ]
        }

### 分组的api权限列表 [GET] /permissionCloud/findApiPermissions
+ Description
    + Author Liukai
+ Parameters
+ Response 200
        
        {
          "data": {
            "1": [
              {
                "id": 7,
                "permissionType": 0,
                "permissionGroup": 1,
                "permissionName": "brand:list",
                "permissionDescribe": "品牌列表"
              },
              {
                "id": 8,
                "permissionType": 0,
                "permissionGroup": 1,
                "permissionName": "brand:details",
                "permissionDescribe": "品牌详情"
              },
              {
                "id": 9,
                "permissionType": 0,
                "permissionGroup": 1,
                "permissionName": "brand:add",
                "permissionDescribe": "品牌添加"
              },
              {
                "id": 10,
                "permissionType": 0,
                "permissionGroup": 1,
                "permissionName": "brand:remove",
                "permissionDescribe": "品牌删除"
              },
              
              {
                "id": 35,
                "permissionType": 0,
                "permissionGroup": 6,
                "permissionName": "protocol:remove",
                "permissionDescribe": "控制协议删除"
              },
              {
                "id": 36,
                "permissionType": 0,
                "permissionGroup": 6,
                "permissionName": "protocol:update",
                "permissionDescribe": "控制协议修改"
              }
            ],
            "7": [
              {
                "id": 57,
                "permissionType": 0,
                "permissionGroup": 7,
                "permissionName": "user:list",
                "permissionDescribe": "用户列表"
              },
              {
                "id": 58,
                "permissionType": 0,
                "permissionGroup": 7,
                "permissionName": "user:details",
                "permissionDescribe": "用户详情"
              },
              {
                "id": 59,
                "permissionType": 0,
                "permissionGroup": 7,
                "permissionName": "user:add",
                "permissionDescribe": "用户添加"
              },
              {
                "id": 60,
                "permissionType": 0,
                "permissionGroup": 7,
                "permissionName": "user:remove",
                "permissionDescribe": "用户删除"
              },
              {
                "id": 61,
                "permissionType": 0,
                "permissionGroup": 7,
                "permissionName": "user:update",
                "permissionDescribe": "用户修改"
              }
            ],
            "8": [
              {
                "id": 62,
                "permissionType": 0,
                "permissionGroup": 8,
                "permissionName": "role:list",
                "permissionDescribe": "角色列表"
              },
              {
                "id": 63,
                "permissionType": 0,
                "permissionGroup": 8,
                "permissionName": "role:details",
                "permissionDescribe": "角色详情"
              },
              {
                "id": 64,
                "permissionType": 0,
                "permissionGroup": 8,
                "permissionName": "role:add",
                "permissionDescribe": "角色添加"
              },
              {
                "id": 65,
                "permissionType": 0,
                "permissionGroup": 8,
                "permissionName": "role:remove",
                "permissionDescribe": "角色删除"
              },
              {
                "id": 68,
                "permissionType": 0,
                "permissionGroup": 9,
                "permissionName": "permission:groupapi:list",
                "permissionDescribe": "分组api列表"
              }
            ],
            "10": [
              {
                "id": 69,
                "permissionType": 0,
                "permissionGroup": 10,
                "permissionName": "logsystem:list",
                "permissionDescribe": "系统日志列表"
              },
              {
                "id": 70,
                "permissionType": 0,
                "permissionGroup": 10,
                "permissionName": "logsystem:export",
                "permissionDescribe": "系统日志导出"
              }
            ],
            "12": [
              {
                "id": 73,
                "permissionType": 0,
                "permissionGroup": 12,
                "permissionName": "emailconfig:details",
                "permissionDescribe": "邮件配置详情"
              },
              {
                "id": 74,
                "permissionType": 0,
                "permissionGroup": 12,
                "permissionName": "emailconfig:add",
                "permissionDescribe": "邮件配置增加"
              },
              {
                "id": 75,
                "permissionType": 0,
                "permissionGroup": 12,
                "permissionName": "emailconfig:update",
                "permissionDescribe": "邮件配置修改"
              }
            ],
            "13": [
              {
                "id": 76,
                "permissionType": 0,
                "permissionGroup": 13,
                "permissionName": "collectionintervalconfig:list",
                "permissionDescribe": "采集间隔配置列表"
              },
              {
                "id": 77,
                "permissionType": 0,
                "permissionGroup": 13,
                "permissionName": "collectionintervalconfig:details",
                "permissionDescribe": "采集间隔配置详情"
              },
              {
                "id": 78,
                "permissionType": 0,
                "permissionGroup": 13,
                "permissionName": "collectionintervalconfig:add",
                "permissionDescribe": "采集间隔配置添加"
              },
              {
                "id": 79,
                "permissionType": 0,
                "permissionGroup": 13,
                "permissionName": "collectionintervalconfig:remove",
                "permissionDescribe": "采集间隔配置删除"
              },
              {
                "id": 80,
                "permissionType": 0,
                "permissionGroup": 13,
                "permissionName": "collectionintervalconfig:update",
                "permissionDescribe": "采集间隔配置修改"
              }
            ],
            "14": [
              {
                "id": 82,
                "permissionType": 0,
                "permissionGroup": 14,
                "permissionName": "intelligentScene:add",
                "permissionDescribe": "智能场景添加"
              },
              {
                "id": 83,
                "permissionType": 0,
                "permissionGroup": 14,
                "permissionName": "intelligentScene:remove",
                "permissionDescribe": "智能场景删除"
              },
              {
                "id": 84,
                "permissionType": 0,
                "permissionGroup": 14,
                "permissionName": "intelligentScene:update",
                "permissionDescribe": "智能场景修改"
              },
              {
                "id": 85,
                "permissionType": 0,
                "permissionGroup": 14,
                "permissionName": "intelligentScene:details",
                "permissionDescribe": "智能场景详情"
              },
              {
                "id": 86,
                "permissionType": 0,
                "permissionGroup": 14,
                "permissionName": "intelligentScene:list",
                "permissionDescribe": "智能场景列表"
              }
            ],
            "15": [
              {
                "id": 87,
                "permissionType": 0,
                "permissionGroup": 15,
                "permissionName": "readtype:add",
                "permissionDescribe": "读数类型添加"
              },
              {
                "id": 88,
                "permissionType": 0,
                "permissionGroup": 15,
                "permissionName": "readtype:remove",
                "permissionDescribe": "读数类型删除"
              }
            ],
            "16": [
              {
                "id": 92,
                "permissionType": 0,
                "permissionGroup": 16,
                "permissionName": "videolink:details",
                "permissionDescribe": "视频链接详情"
              }
            ],
            "17": [
              {
                "id": 95,
                "permissionType": 0,
                "permissionGroup": 17,
                "permissionName": "scheduledTask:update",
                "permissionDescribe": "计划任务修改"
              },
              {
                "id": 96,
                "permissionType": 0,
                "permissionGroup": 17,
                "permissionName": "scheduledTask:list",
                "permissionDescribe": "计划任务列表"
              },
              {
                "id": 97,
                "permissionType": 0,
                "permissionGroup": 17,
                "permissionName": "scheduledTask:details",
                "permissionDescribe": "计划任务详情"
              }
            ],
            "18": [],
            "19": [],
            "20": [],
            "21": [],
            "100": [
              {
                "id": 81,
                "permissionType": 0,
                "permissionGroup": 100,
                "permissionName": "file:upload",
                "permissionDescribe": "文件上传"
              }
            ]
          }
        }

### 当前用户的页面权限列表 [GET] /permissionCloud/findPagePermissionsByCurrent
+ Description
    + Author Liukai
+ Parameters
+ Response 200

        {
          "data": [
            {
              "id": 3,
              "permissionName": "admin_log"
            },
            {
              "id": 5,
              "permissionName": "admin_info_tips"
            },
            {
              "id": 6,
              "permissionName": "admin_rbac"
            }
          ]
        }

### 权限组列表 [GET] /permissionCloud/findPermissionsGroup
+ Description
    + Author Liukai
    + 得到权限组名
+ Parameters
+ Response 200

        {
          "data": [
            {
              "id": 1,
              "nameEn": "BRAND",
              "nameCh": "品牌"
            },
            {
              "id": 2,
              "nameEn": "CATEGORY",
              "nameCh": "分类"
            },
            {
              "id": 3,
              "nameEn": "CATEGORY_COMMAND",
              "nameCh": "分类命令"
            },
            {
              "id": 4,
              "nameEn": "EQUIPMENT",
              "nameCh": "设备型号"
            },
            {
              "id": 5,
              "nameEn": "EQUIPMENT_ASSET",
              "nameCh": "设备资产"
            },
            {
              "id": 6,
              "nameEn": "CONTROL_PROTOCOL",
              "nameCh": "控制协议"
            },
            {
              "id": 7,
              "nameEn": "USER",
              "nameCh": "用户"
            },
            {
              "id": 8,
              "nameEn": "ROLE",
              "nameCh": "角色"
            },
            {
              "id": 9,
              "nameEn": "PERMISSION",
              "nameCh": "权限"
            },
            {
              "id": 10,
              "nameEn": "LOG_SYSTEM",
              "nameCh": "系统日志"
            },
            {
              "id": 11,
              "nameEn": "LOG_EQUIPMENT",
              "nameCh": "设备日志"
            },
            {
              "id": 12,
              "nameEn": "COLLECTION_INTERVAL_",
              "nameCh": "邮箱配置"
            },
            {
              "id": 13,
              "nameEn": "EMAIL_CONFIG",
              "nameCh": "采集间隔配置"
            },
            {
              "id": 14,
              "nameEn": "INTELLIGENTSCENE",
              "nameCh": "智能场景"
            },
            {
              "id": 15,
              "nameEn": "READTYPE",
              "nameCh": "读数类型"
            },
            {
              "id": 16,
              "nameEn": "VIDEOLINK",
              "nameCh": "视频链接"
            },
            {
              "id": 17,
              "nameEn": "SCHEDULEDTASK",
              "nameCh": "计划任务"
            },
            {
              "id": 100,
              "nameEn": "OTHER",
              "nameCh": "其他"
            }
          ]
        }
