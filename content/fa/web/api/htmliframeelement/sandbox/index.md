---
title: "HTMLIFrameElement: sandbox property"
short-title: sandbox
slug: Web/API/HTMLIFrameElement/sandbox
page-type: web-api-instance-property
browser-compat: api.HTMLIFrameElement.sandbox
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`sandbox`** در {{domxref("HTMLIFrameElement")}} یک شیء زندهٔ {{domxref("DOMTokenList")}} برمی‌گرداند که محدودیت‌های اضافی اعمال‌شده بر رفتار محتوای تودرتو را نشان می‌دهد. این ویژگی، صفت محتوایی [`sandbox`](/en-US/docs/Web/HTML/Reference/Elements/iframe#sandbox) عنصر {{HTMLElement("iframe")}} را بازتاب می‌دهد.

## مقدار

یک شیء زندهٔ {{domxref("DOMTokenList")}}.

اگرچه خودِ ویژگی `sandbox` به این معنا فقط‌خواندنی است که نمی‌توانید شیء `DOMTokenList` را جایگزین کنید، اما همچنان می‌توانید مستقیماً به ویژگی `sandbox` مقداردهی کنید که معادل مقداردهی به ویژگی {{domxref("DOMTokenList/value", "value")}} آن است. همچنین می‌توانید شیء `DOMTokenList` را با روش‌های {{domxref("DOMTokenList/add", "add()")}}، {{domxref("DOMTokenList/remove", "remove()")}}، {{domxref("DOMTokenList/replace", "replace()")}} و {{domxref("DOMTokenList/toggle", "toggle()")}} تغییر دهید.

## مثال‌ها

```html
<iframe
  id="el"
  title="example"
  src="https://example.com"
  sandbox="allow-same-origin allow-scripts"></iframe>
```

```js
const el = document.getElementById("el");
console.log(Array.from(el.sandbox)); // خروجی: ["allow-same-origin", "allow-scripts"]

el.sandbox = "";
console.log(Array.from(el.sandbox)); // خروجی: []
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}