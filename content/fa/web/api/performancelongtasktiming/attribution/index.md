---
title: "PerformanceLongTaskTiming: attribution property"
---

---
title: "PerformanceLongTaskTiming: attribution property"
short-title: attribution
slug: Web/API/PerformanceLongTaskTiming/attribution
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PerformanceLongTaskTiming.attribution
---

{{SeeCompatTable}}{{APIRef("Performance API")}}

{{domxref("PerformanceLongTaskTiming")}} 接口的 **`attribution`** 只读属性返回一个 {{domxref('TaskAttributionTiming')}} 对象的数组。

## 值

一个由 {{domxref('TaskAttributionTiming')}} 对象组成的 {{jsxref("Array")}}。

## 示例

### 记录长任务的 attribution

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    entry.attribution.forEach((attributionEntry) => {
      console.log(attributionEntry);
    });
  });
});

observer.observe({ type: "longtask", buffered: true });
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- {{domxref('TaskAttributionTiming')}}