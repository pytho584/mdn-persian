---
title: "HTMLStyleElement: blocking property"
short-title: blocking
slug: Web/API/HTMLStyleElement/blocking
page-type: web-api-instance-property
browser-compat: api.HTMLStyleElement.blocking
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`blocking`** از {{domxref("HTMLStyleElement")}} یک شیء زنده از {{domxref("DOMTokenList")}} را برمی‌گرداند که شامل عملیات‌هایی است که باید هنگام واکشی یک منبع خارجی مسدود شوند. این ویژگی منعکس‌کنندهٔ ویژگی محتوایی [`blocking`](/en-US/docs/Web/HTML/Reference/Elements/style#blocking) عنصر {{HTMLElement("style")}} است.

## مقدار

یک شیء زنده از {{domxref("DOMTokenList")}}.

اگرچه ویژگی `blocking` خود فقط‌خواندنی است به این معنا که نمی‌توانید شیء `DOMTokenList` را جایگزین کنید، اما همچنان می‌توانید مستقیماً به ویژگی `blocking` مقداردهی کنید که معادل مقداردهی به ویژگی {{domxref("DOMTokenList/value", "value")}} آن است. همچنین می‌توانید شیء `DOMTokenList` را با استفاده از متدهای {{domxref("DOMTokenList/add", "add()")}}، {{domxref("DOMTokenList/remove", "remove()")}}، {{domxref("DOMTokenList/replace", "replace()")}} و {{domxref("DOMTokenList/toggle", "toggle()")}} تغییر دهید.

## مثال‌ها

```html
<style id="el" blocking="render">
  p {
    color: blue;
  }
</style>
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

- {{domxref("HTMLLinkElement.blocking")}}
- {{domxref("HTMLScriptElement.blocking")}}