---
title: PerformanceNavigation
slug: Web/API/PerformanceNavigation
page-type: web-api-interface
status:
  - deprecated
browser-compat: api.PerformanceNavigation
---

{{APIRef("Performance API")}}{{Deprecated_Header}}

遗留的 **`PerformanceNavigation`** 接口表示与如何导航到当前文档有关的信息。

> [!WARNING]
> 该接口已在 [Navigation Timing Level 2 规范](https://w3c.github.io/navigation-timing/#obsolete) 中弃用。
> 请改用 {{domxref("PerformanceNavigationTiming")}} 接口。

可以通过调用 {{domxref("Performance.navigation")}} 只读属性来获得此类型的对象。

## 实例属性

_`PerformanceNavigation` 接口不继承任何属性。_

- {{domxref("PerformanceNavigation.type")}} {{ReadOnlyInline}} {{deprecated_inline}}
  - : 一个 `unsigned short`，指示如何导航到此页面。可能的值有：
    - `TYPE_NAVIGATE` (0)
      - : 页面通过点击链接、书签、表单提交、脚本，或在地址栏中输入 URL 来访问。
    - `TYPE_RELOAD` (1)
      - : 页面通过点击“重新加载”按钮或使用 {{domxref("Location.reload()")}} 方法来访问。
    - `TYPE_BACK_FORWARD` (2)
      - : 页面通过历史记录导航来访问。
    - `TYPE_RESERVED` (255)
      - : 使用其他任何方式。

- {{domxref("PerformanceNavigation.redirectCount")}} {{ReadOnlyInline}} {{deprecated_inline}}
  - : 一个 `unsigned short`，表示在到达该页面之前执行的重定向次数。

## 实例方法

_`PerformanceNavigation` 接口不继承任何方法。_

- {{domxref("PerformanceNavigation.toJSON()")}} {{deprecated_inline}}
  - : 一个 {{Glossary("Serialization","序列化器")}}，返回表示 `PerformanceNavigation` 对象的 JSON 对象。

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- 允许访问此类型对象的 {{domxref("Performance")}}。
- {{domxref("PerformanceNavigationTiming")}}（Navigation Timing Level 2 的一部分），已取代此 API。