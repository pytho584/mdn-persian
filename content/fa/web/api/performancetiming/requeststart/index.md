```
---
title: "PerformanceTiming: requestStart property"
short-title: requestStart
slug: Web/API/PerformanceTiming/requestStart
page-type: web-api-instance-property
status:
  - deprecated
browser-compat: api.PerformanceTiming.requestStart
---

{{ APIRef("PerformanceTiming") }} {{Deprecated_Header}}

> [!WARNING]
> 此属性所属的接口已在 [Navigation Timing Level 2 规范](https://w3c.github.io/navigation-timing/#obsolete) 中被废弃。请改用 {{domxref("PerformanceNavigationTiming")}} 接口。

传统的
**`PerformanceTiming.requestStart`**
只读属性返回一个 `unsigned long long` 类型的时间戳，表示浏览器从服务器或缓存发起获取实际文档请求的时刻，单位是自 UNIX 纪元起的毫秒数。如果请求开始后传输层失败并重新建立连接，此属性将对应新请求的时间。

## 值

一个 `unsigned long long` 类型的时间戳。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- 它所属的 {{domxref("PerformanceTiming")}} 接口。
```