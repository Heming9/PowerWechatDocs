---
title: 数据统计与分析
date: 2021-09-12
---

## 访问留存

头部代码

```go

import (
  "github.com/ArtisanCloud/power-wechat/src/kernel/power"
  "github.com/golang-module/carbon"
  "net/http"
)

const TIMEZONE = "asia/shanghai"
const DATETIME_FORMAT = "20060102"

```

---

### 小程序日留存

```go
now := time.Now().Add(-5 * 24 * time.Hour)
from := now.Format(services.DATETIME_FORMAT)
to := now.Format(services.DATETIME_FORMAT)

MiniProgramApp.DataCube.GetDailyRetainInfo(from, to)
```

[微信官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/data-analysis/visit-retain/analysis.getDailyRetain.html)

---

### 小程序月留存

```go
from := "20210906"
to := "20210912"

MiniProgramApp.DataCube.GetMonthlyRetainInfo(from, to)
```

[微信官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/data-analysis/visit-retain/analysis.getMonthlyRetain.html)

---

### 小程序周留存

```go
from := "20170201"
to := "20170228"

MiniProgramApp.DataCube.GetWeeklyRetainInfo(from, to)
```

[微信官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/data-analysis/visit-retain/analysis.getWeeklyRetain.html)



## 日汇总统计数据

### 小程序数据概况

```go
now := time.Now().Add(-5 * 24 * time.Hour)
from := now.Format(services.DATETIME_FORMAT)
to := now.Format(services.DATETIME_FORMAT)

MiniProgramApp.DataCube.GetDailySummary(from, to)
```

[微信官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/data-analysis/analysis.getDailySummary.html)

## 访问趋势

### 小程序数据日趋势

```go
now := time.Now().Add(-5 * 24 * time.Hour)

from := now.Format(services.DATETIME_FORMAT)
to := now.Format(services.DATETIME_FORMAT)

MiniProgramApp.DataCube.GetDailyVisitTrend(from, to)
```

[微信官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/data-analysis/visit-trend/analysis.getDailyVisitTrend.html)

---

### 小程序数据月趋势

注：(能查询到的最新数据为上一个自然月的数据)

```go
from := "20210831"
to := "20210930"

MiniProgramApp.DataCube.GetMonthlyVisitTrend(from, to)
```

[微信官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/data-analysis/visit-trend/analysis.getMonthlyVisitTrend.html)

---

### 小程序数据周趋势

```go
from := "20210906"
to := "20210912"

rs, err := MiniProgramApp.DataCube.GetWeeklyVisitTrend(from, to)
```

[微信官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/data-analysis/visit-trend/analysis.getWeeklyVisitTrend.html)

## 性能/运行性能数据

```go
now := time.Now().Add(-5 * 24 * time.Hour)
beginTimestamp := now.Unix()
endTimestamp := now.Add(2 * 24 * time.Hour).Unix()

options := &power.HashMap{
  "time": power.HashMap{
    "end_timestamp":   endTimestamp,
    "begin_timestamp": beginTimestamp,
  },
  "module": "10022",
  "params": []power.StringMap{
    power.StringMap{

      "field": "networktype",
      "value": "wifi",
    },
    power.StringMap{
      "field": "device_level",
      "value": "1",
    },
    power.StringMap{
      "field": "device",
      "value": "1",
    },
  },
}

MiniProgramApp.DataCube.GetPerformanceData(options)
```

[微信官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/data-analysis/analysis.getPerformanceData.html)

## 用户画像数据

### 新增或活跃用户的画像分布

```go
from := "20210906"
to := "20210912"

MiniProgramApp.DataCube.GetUserPortrait(from, to)
```

[微信官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/data-analysis/analysis.getUserPortrait.html)

## 访问分布数据



```go
from := "20210906"
to := "20210906"

MiniProgramApp.DataCube.GetVisitDistribution(from, to)
```

[微信官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/data-analysis/analysis.getVisitDistribution.html)

## 访问页面数据

```go
from := "20210906"
to := "20210912"

MiniProgramApp.DataCube.GetVisitPage(from, to)
```

[微信官方文档](https://developers.weixin.qq.com/miniprogram/dev/api-backend/open-api/data-analysis/analysis.getUserPortrait.html)