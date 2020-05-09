<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [礼加服务端文档](#%E7%A4%BC%E5%8A%A0%E6%9C%8D%E5%8A%A1%E7%AB%AF%E6%96%87%E6%A1%A3)
  - [提交赠券订单](#%E6%8F%90%E4%BA%A4%E8%B5%A0%E5%88%B8%E8%AE%A2%E5%8D%95)
    - [url](#url)
    - [参数](#%E5%8F%82%E6%95%B0)
    - [结果](#%E7%BB%93%E6%9E%9C)
  - [支付赠券订单](#%E6%94%AF%E4%BB%98%E8%B5%A0%E5%88%B8%E8%AE%A2%E5%8D%95)
    - [url](#url-1)
    - [参数](#%E5%8F%82%E6%95%B0-1)
    - [结果](#%E7%BB%93%E6%9E%9C-1)
  - [赠券列表](#%E8%B5%A0%E5%88%B8%E5%88%97%E8%A1%A8)
    - [url](#url-2)
    - [参数](#%E5%8F%82%E6%95%B0-2)
    - [结果](#%E7%BB%93%E6%9E%9C-2)
  - [赠券详情](#%E8%B5%A0%E5%88%B8%E8%AF%A6%E6%83%85)
    - [url](#url-3)
    - [参数](#%E5%8F%82%E6%95%B0-3)
    - [结果](#%E7%BB%93%E6%9E%9C-3)
  - [分享赠券(状态是101的才可以分享)](#%E5%88%86%E4%BA%AB%E8%B5%A0%E5%88%B8%E7%8A%B6%E6%80%81%E6%98%AF101%E7%9A%84%E6%89%8D%E5%8F%AF%E4%BB%A5%E5%88%86%E4%BA%AB)
    - [url](#url-4)
    - [参数](#%E5%8F%82%E6%95%B0-4)
    - [结果](#%E7%BB%93%E6%9E%9C-4)
  - [接收赠券](#%E6%8E%A5%E6%94%B6%E8%B5%A0%E5%88%B8)
    - [url](#url-5)
    - [参数](#%E5%8F%82%E6%95%B0-5)
    - [结果](#%E7%BB%93%E6%9E%9C-5)
  - [提货-赠券](#%E6%8F%90%E8%B4%A7-%E8%B5%A0%E5%88%B8)
    - [url](#url-6)
    - [参数](#%E5%8F%82%E6%95%B0-6)
    - [结果](#%E7%BB%93%E6%9E%9C-6)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# 礼加服务端文档

## 提交赠券订单

### url
```angular2
/api/order/submitGift
```

### 参数

### 结果

```json
{
  "errno": 0,
  "errmsg": "",
  "data": {
    "orderInfo": {
      "id": 1, //订单ID
      "order_sn": "20200406110515724520",
      "user_id": 1098,
      "order_status": 101, //101未付款
      "shipping_fee": 0,
      "created_time": 1588993515,
      "goods_price": 507,
      "order_price": 507,
      "actual_price": 507,
      "change_price": 507,
      "print_info": "1、纯棉水洗色织格夏凉被【3】 "      
    }
  }
}
```

## 支付赠券订单

### url
```text
/api/order/wxPayGift
```

### 参数

```json
{
  "orderId": 1 //订单ID
}
```

### 结果

```json
{
  "errno": 0,
  "errmsg": "",
  "data": {
    "orderInfo": {
      "id": 1,
      "order_sn": "20200406110515724520",
      "user_id": 1098,
      "order_status": 201, //支付成功
      "print_info": "1、纯棉水洗色织格夏凉被【3】 ",
      "shipping_fee": 0,
      "pay_id": null,
      "pay_name": null,
      "pay_time": null,
      "change_price": 507,
      "actual_price": 507,
      "order_price": 507,
      "goods_price": 507,
      "created_time": 1588993515
    }
  }
}
```

## 赠券列表

### url

```text
/api/order/getGiftStampList
```

### 参数

```json
{
  "page": 1 //分页参数
}
```

### 结果

```json
{
  "errno": 0,
  "errmsg": "",
  "data": {
    "list": [
      {
        "id": 1,
        "order_id": 1,
        "user_id": 1100,
        "status": 101, //待赠送待提取
        "content": "1、纯棉水洗色织格夏凉被【3】 ",
        "share_time": 0,
        "share_code": "",               
      }
    ]
  }
}
```


## 赠券详情

### url

```text
/api/order/getGiftStampDetail
```

### 参数

```json
{
  "stampId": 1 //赠券id
}
```

### 结果

```json
{
  "errno": 0,
  "errmsg": "",
  "data": {
    "stampInfo": {
      "id": 1,
      "order_id": 1,
      "user_id": 1100,
      "status": 101,
      "content": "1、纯棉水洗色织格夏凉被【3】 ",
      "share_time": 0,
      "share_code": "",
      "give_time": 1588994254,      
      "order_status_text": "待赠送"
    },
    "orderGoods": [
      {
        "id": 1484,
        "order_id": 1,
        "goods_id": 1127052,
        "goods_name": "纯棉水洗色织格夏凉被",
        "goods_aka": "纯棉水洗色织格夏凉被",
        "product_id": 183,
        "number": 3,
        "retail_price": 169,
        "goods_specifition_name_value": "1条",
        "goods_specifition_ids": "17",
        "list_pic_url": "http://yanxuan.nosdn.127.net/4f483526cfe3b953f403ae02049df5b9.png",
        "user_id": 1098,
        "is_delete": 0
      }
    ],
    "handleOption": {
      "give": true,
      "pick": true
    },
    "goodsCount": 3
  }
}
```

## 分享赠券(状态是101的才可以分享)

### url

```text
/api/order/giveGiftStamp
```

### 参数

```json
{
  "stampId": 1 //赠券ID
}
```

### 结果
```json
{
  "errno": 0,
  "errmsg": "",
  "data": {
    "share_code": "629PWRnnUl8WPNTu" //分享码，赠券唯一的标示
  }
}
```

## 接收赠券

### url

```text
/api/order/acceptGiftStamp
```

### 参数

```json
{
  "share_code": "629PWRnnUl8WPNTu" //分享码，用于接收赠券
}
```

### 结果

```json
{
  "errno": 0,
  "errmsg": "",
  "data": {
    "stampInfo": {
      "id": 1,
      "order_id": 1,
      "user_id": 1099, //user_id 更新为当前用户
      "status": 101, // 赠券状态重置为101
      "content": "1、纯棉水洗色织格夏凉被【3】 ",
      "share_time": 1588994249,
      "share_code": "629PWRnnUl8WPNTu",    
    }
  }
}
```

## 提货-赠券

### url

```text
/api/order/pickGiftStamp
```

### 参数

```json
{
  "stampId": 1,
  "addressId": 101,
  "remark": "配送前请提前联系"
}
```

### 结果

```json
{
  "errno": 0,
  "errmsg": "",
  "data": {
    "stampInfo": {
      "id": 1,
      "order_id": 1,
      "user_id": 1100,
      "status": 103, //已提货
      "content": "1、纯棉水洗色织格夏凉被【3】 ",     
      "give_time": 1588994254,
      "pick_time": 1588994255,
      "country": 0,
      "province": 3,
      "city": 6,
      "district": 4,
      "adress": "太子湖北路1号",
      "remark": "配送前请提前致电",
      "mobile": "18686535085",
      "nickname": "不二"
    }
  }
}
```