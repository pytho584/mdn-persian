---
title: "HTMLFormElement: relList property"
short-title: relList
slug: Web/API/HTMLFormElement/relList
page-type: web-api-instance-property
browser-compat: api.HTMLFormElement.relList
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`relList`** در {{domxref("HTMLFormElement")}} یک شیء زنده از نوع {{domxref("DOMTokenList")}} برمی‌گرداند که شامل مجموعه‌ای از انواع پیوند است؛ این انواع، رابطه بین منبع نمایش‌داده‌شده توسط عنصر {{HTMLElement("form")}} و سند فعلی را نشان می‌دهند. این ویژگی، ویژگی محتوایی [`rel`](/en-US/docs/Web/HTML/Reference/Attributes/rel) عنصر {{HTMLElement("form")}} را بازتاب می‌دهد.

## مقدار

یک شیء زنده از نوع {{domxref("DOMTokenList")}}.

اگرچه خود ویژگی `relList` از این نظر فقط‌خواندنی است که نمی‌توانید شیء `DOMTokenList` را جایگزین کنید، اما همچنان می‌توانید مستقیماً به ویژگی `relList` مقدار بدهید؛ این کار معادل مقداردهی به ویژگی {{domxref("DOMTokenList/value", "value")}} آن است. همچنین می‌توانید شیء `DOMTokenList` را با استفاده از متدهای {{domxref("DOMTokenList/add", "add()")}}، {{domxref("DOMTokenList/remove", "remove()")}}، {{domxref("DOMTokenList/replace", "replace()")}} و {{domxref("DOMTokenList/toggle", "toggle()")}} تغییر دهید.

## مثال‌ها

```js
const form = document.querySelector("form");
form.relList.forEach((relEntry) => {
  console.log(relEntry);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLAnchorElement.relList")}}
- {{domxref("HTMLLinkElement.relList")}}
- {{domxref("HTMLFormElement.rel")}}