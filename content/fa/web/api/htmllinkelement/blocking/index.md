---
title: "HTMLLinkElement: blocking property"
short-title: blocking
slug: Web/API/HTMLLinkElement/blocking
page-type: web-api-instance-property
browser-compat: api.HTMLLinkElement.blocking
---

{{APIRef("HTML DOM")}}

خاصیت فقط‌خواندنی **`blocking`** در {{domxref("HTMLLinkElement")}} یک شیء {{domxref("DOMTokenList")}} زنده را برمی‌گرداند که شامل عملیاتی است که باید در هنگام واکشی یک منبع خارجی مسدود شوند. این خاصیت، ویژگی محتوایی [`blocking`](/en-US/docs/Web/HTML/Reference/Elements/link#blocking) عنصر {{HTMLElement("link")}} را منعکس می‌کند.

## مقدار

یک شیء {{domxref("DOMTokenList")}} زنده.

اگرچه خود خاصیت `blocking` از نظر اینکه نمی‌توانید شیء `DOMTokenList` را جایگزین کنید، فقط‌خواندنی است، اما همچنان می‌توانید مستقیماً به خاصیت `blocking` مقداردهی کنید، که معادل مقداردهی به خاصیت {{domxref("DOMTokenList/value", "value")}} آن است. همچنین می‌توانید با استفاده از روش‌های {{domxref("DOMTokenList/add", "add()")}}، {{domxref("DOMTokenList/remove", "remove()")}}، {{domxref("DOMTokenList/replace", "replace()")}} و {{domxref("DOMTokenList/toggle", "toggle()")}} شیء `DOMTokenList` را تغییر دهید.

## مثال‌ها

```html
<link
  id="el"
  rel="stylesheet"
  href="/example.css"
  blocking="render"
  crossorigin />
```

```js
const el = document.getElementById("el");
console.log(el.blocking); // Output: DOMTokenList ["render"]
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLScriptElement.blocking")}}
- {{domxref("HTMLStyleElement.blocking")}}