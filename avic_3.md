# AVIC管理端接口文档

## 机构
+ mate
    + total (int) 总数
+ Data
    + id (long) 机构id
    + enabled (int) 状态
    + creator (int) 创建人
    + modifier (int) 修改人
    + created (datetime) 创建时间
    + modified (datetime) 修改时间
    + parentId (int)  上级机构id
    + fullName (string) 全称
    + logo (int)    
    + abbreviation (string) 简称
    + park (string) 园区
    + address (string) 地址
    + contactNumber (string) 联系电话
    + displayOrder (int) 排序

   
### 机构统计 [get] /Organization/id

+ Description

+ Request (application/json)

        {
         "meta": {
            "total": 3
         },
         "data": [
         {
          "id": 6,
          "enabled": 1,
          "creator": 0,
          "modifier": 0,
          "created": "2020-04-09 17:24:41",
          "modified": "2020-04-09 17:24:52",
          "parentId": 1,
          "fullName": "技术部实验室",
          "logo": "/api/static/image/1586424245804.jpg",
          "abbreviation": "实验室",
          "park": "云谷",
         "address": "北京丰台",
         "contactNumber": "+86 123468",
         "displayOrder": 100
       }
+ Response 200

+ Response 400

        

