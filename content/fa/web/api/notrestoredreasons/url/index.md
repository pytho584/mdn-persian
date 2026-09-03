---
title: "NotRestoredReasons: url property"
short-title: url
slug: Web/API/NotRestoredReasons/url
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.NotRestoredReasons.url
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

**`url`** 只读属性属于 {{domxref("NotRestoredReasons")}} 接口，返回一个字符串，表示被导航页面或 {{htmlelement("iframe")}} 的 URL。

## 值

一个字符串。

如果文档位于跨源 `<iframe>` 中，`url` 将返回 `null`。

## 示例

有关示例，请参阅 [监控 bfcache 阻塞原因](/en-US/docs/Web/API/Performance_API/Monitoring_bfcache_blocking_reasons)。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [监控 bfcache 阻塞原因](/en-US/docs/Web/API/Performance_API/Monitoring_bfcache_blocking_reasons)
- {{domxref("PerformanceNavigationTiming.notRestoredReasons")}}