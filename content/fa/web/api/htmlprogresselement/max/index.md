---
title: "HTMLProgressElement: max property"
short-title: max
slug: Web/API/HTMLProgressElement/max
page-type: web-api-instance-property
browser-compat: api.HTMLProgressElement.max
---

{{APIRef("HTML DOM")}}

ویژگی **`max`** در رابط {{DOMxRef("HTMLProgressElement")}} نشان‌دهندهٔ کران بالای محدودهٔ عنصر {{HTMLElement("progress")}} است.

## مقدار

یک عدد اعشاری (floating point) که بزرگ‌تر از صفر است. مقدار پیش‌فرض ۱٫۰ است.

## مثال‌ها

### HTML

```html
Progress: <progress id="pBar"></progress> <span>0</span>%
```

### JavaScript

```js
const pBar = document.getElementById("pBar");
const span = document.getElementsByTagName("span")[0];

console.log(`Default value of max: ${pBar.max}`);

pBar.max = 100;
pBar.value = 0;

setInterval(() => {
  pBar.value = pBar.value < pBar.max ? pBar.value + 1 : 0;

  span.textContent = Math.trunc(pBar.position * 100);
}, 100);
```

{{EmbedLiveSample("Examples", "100%", 30)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}