---
title: "DelegatedInkTrailPresenter: presentationArea property"
short-title: presentationArea
slug: Web/API/DelegatedInkTrailPresenter/presentationArea
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.DelegatedInkTrailPresenter.presentationArea
---

{{APIRef("Ink API")}}{{SeeCompatTable}}

**`presentationArea`** 只读属性，属于 {{domxref("DelegatedInkTrailPresenter")}} 接口，返回渲染墨迹笔画时被限制在其内部的 {{domxref("Element")}}（元素）。

如果之前的 {{domxref("Ink.requestPresenter", "Ink.requestPresenter()")}} 方法调用中包含了具体的 `presentationArea` 元素定义，那么返回的就是该元素。否则，返回默认值，即包含该元素的视口（viewport）。

这个区域始终是元素边框盒（border box）的客户端坐标，因此移动元素或滚动元素不需要开发者重新计算。

## 值

一个 {{domxref("Element")}}。

## 示例

```js
async function inkInit() {
  const ink = navigator.ink;
  const presenter = await ink.requestPresenter({ presentationArea: canvas });
  console.log(presenter.presentationArea);

  // …
}
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}