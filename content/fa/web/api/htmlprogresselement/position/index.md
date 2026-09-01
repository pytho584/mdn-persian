---
title: "HTMLProgressElement: position property"
short-title: position
slug: Web/API/HTMLProgressElement/position
page-type: web-api-instance-property
browser-compat: api.HTMLProgressElement.position
---

{{APIRef("HTML DOM")}}

**`position`** 只读属性，属于 {{DOMxRef("HTMLProgressElement")}} 接口，返回 {{HTMLElement("progress")}} 元素的当前进度。

## 值

对于确定进度条，返回当前值除以最大值的结果，即介于 `0.0` 和 `1.0` 之间的分数。

对于不确定进度条，该值始终为 `-1`。

## 示例

### HTML

```html
Determinate Progress bar: <progress id="pBar"></progress> Position:
<span>0</span>
```

### JavaScript

```js
const pBar = document.getElementById("pBar");
const span = document.getElementsByTagName("span")[0];

pBar.max = 100;
pBar.value = 0;

setInterval(() => {
  pBar.value = pBar.value < pBar.max ? pBar.value + 1 : 0;

  span.textContent = pBar.position;
}, 100);
```

{{EmbedLiveSample("Examples", "100%", 30)}}

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}