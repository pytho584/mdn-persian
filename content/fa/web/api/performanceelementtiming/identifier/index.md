---
title: "PerformanceElementTiming: identifier property"
short-title: identifier
slug: Web/API/PerformanceElementTiming/identifier
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PerformanceElementTiming.identifier
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

**`identifier`** 只读属性属于 {{domxref("PerformanceElementTiming")}} 接口，返回元素上 [`elementtiming`](/en-US/docs/Web/HTML/Reference/Attributes/elementtiming) 属性的值。

## 值

一个字符串。

## 示例

### 使用 `identifier`

在此示例中，通过添加 [`elementtiming`](/en-US/docs/Web/HTML/Reference/Attributes/elementtiming) 属性来观察一个 {{HTMLElement("img")}} 元素。注册了一个 {{domxref("PerformanceObserver")}} 来获取所有类型为 `"element"` 的性能条目，并使用 `buffered` 标志来访问观察器创建之前的数据。 [`elementtiming`](/en-US/docs/Web/HTML/Reference/Attributes/elementtiming) 的值为 `big-image`。因此，调用 `entry.identifier` 会返回字符串 `big-image`。

```html
<img
  src="image.jpg"
  alt="a nice image"
  elementtiming="big-image"
  id="myImage" />
```

```js
const observer = new PerformanceObserver((list) => {
  list.getEntries().forEach((entry) => {
    if (entry.identifier === "big-image") {
      console.log(entry.naturalWidth);
    }
  });
});
observer.observe({ type: "element", buffered: true });
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}