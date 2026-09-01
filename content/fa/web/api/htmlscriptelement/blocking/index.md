---
title: "HTMLScriptElement: blocking property"
short-title: blocking
slug: Web/API/HTMLScriptElement/blocking
page-type: web-api-instance-property
browser-compat: api.HTMLScriptElement.blocking
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`blocking`** از {{domxref("HTMLScriptElement")}} یک شیء زندهٔ {{domxref("DOMTokenList")}} برمی‌گرداند که شامل عملیات‌هایی است که باید هنگام واکشی یک منبع خارجی مسدود شوند. این ویژگی، ویژگی محتوایی [`blocking`](/en-US/docs/Web/HTML/Reference/Elements/script#blocking) عنصر {{HTMLElement("script")}} را بازتاب می‌دهد.

## Value

یک شیء زندهٔ {{domxref("DOMTokenList")}}.

اگرچه خود ویژگی `blocking` به این معنا فقط‌خواندنی است که نمی‌توانید شیء `DOMTokenList` را جایگزین کنید، همچنان می‌توانید مستقیماً به ویژگی `blocking` مقدار اختصاص دهید که معادل مقداردهی به ویژگی {{domxref("DOMTokenList/value", "value")}} آن است. همچنین می‌توانید شیء `DOMTokenList` را با استفاده از متدهای {{domxref("DOMTokenList/add", "add()")}}، {{domxref("DOMTokenList/remove", "remove()")}}، {{domxref("DOMTokenList/replace", "replace()")}} و {{domxref("DOMTokenList/toggle", "toggle()")}} تغییر دهید.

## Examples

```html
<script id="el" async blocking="render"></script>
```

```js
const el = document.getElementById("el");
console.log(el.blocking); // Output: "render"
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("HTMLLinkElement.blocking")}}
- {{domxref("HTMLStyleElement.blocking")}}
