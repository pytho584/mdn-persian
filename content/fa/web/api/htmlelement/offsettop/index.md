---
title: "HTMLElement: offsetTop property"
short-title: offsetTop
slug: Web/API/HTMLElement/offsetTop
page-type: web-api-instance-property
browser-compat: api.HTMLElement.offsetTop
---

{{ APIRef("HTML DOM") }}

خاصیت فقط‌خواندنی **`offsetTop`** از رابط {{domxref("HTMLElement")}}، فاصله از حاشیه بیرونی عنصر جاری (شامل margin آن) تا لبه بالایی padding عنصر {{domxref("HTMLelement.offsetParent","offsetParent")}} (نزدیک‌ترین جد دارای موقعیت‌یابی) را برمی‌گرداند.

## مقدار

یک عدد.

## مثال‌ها

```js
const d = document.getElementById("div1");
const topPos = d.offsetTop;

if (topPos > 10) {
  // object offset is more
  // than 10 pixels from its parent
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [تعیین ابعاد عناصر](/en-US/docs/Web/API/CSS_Object_Model/Determining_the_dimensions_of_elements)
- {{domxref("Element.clientTop")}}
- {{domxref("Element.scrollTop")}}
- {{domxref("HTMLElement.offsetHeight")}}
- {{domxref("HTMLElement.offsetWidth")}}
- {{domxref("HTMLElement.offsetLeft")}}
- {{domxref("Element.getBoundingClientRect()")}}