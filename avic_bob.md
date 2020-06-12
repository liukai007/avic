# AVIC北京银行其他接口文档

+ 2020年6月12日
    + 中控设备统计
    

### 中控设备统计 [GET] /equipmentasset/bob/centralControl/statistics

+ Description
    + Author Liukai
+ Parameters
  
+ ReturnData
    + sum (long) 设备数量
    + normal (long) 正常设备数量
    + malfunction (long) 故障设备数量
    
+ Response 200

        {
          "data": {
            "sum": 2,
            "normal": 1,
            "malfunction": 1
          }
        }
