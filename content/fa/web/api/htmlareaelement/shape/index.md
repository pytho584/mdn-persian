---
title: "HTMLAreaElement: shape property"
short-title: shape
slug: Web/API/HTMLAreaElement/shape
page-type: web-api-instance-property
browser-compat: api.HTMLAreaElement.shape
---

{{APIRef("HTML DOM")}}

خاصیت **`shape`** از رابط {{DOMxRef("HTMLAreaElement")}} شکل ناحیه را در یک نقشهٔ تصویری مشخص می‌کند. این خاصیت منعکس‌کنندهٔ صفت [`shape`](/en-US/docs/Web/HTML/Reference/Elements/area#shape) در عنصر {{htmlelement("area")}} است.

## مقدار

یک رشته؛ `rect`، `circle` یا `poly`.

## مثال‌ها

```js
const areaElement = document.getElementById("imageMapArea");
console.log(areaElement.shape);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{DOMXref("HTMLAreaElement.coords")}}
- {{DOMXref("HTMLAreaElement.alt")}}
- {{DOMXref("HTMLMapElement")}}
- {{HTMLElement("area")}}
- {{HTMLElement("map")}}
- {{HTMLElement("a")}}