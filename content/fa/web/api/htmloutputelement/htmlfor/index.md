---
title: "HTMLOutputElement: htmlFor property"
short-title: htmlFor
slug: Web/API/HTMLOutputElement/htmlFor
page-type: web-api-instance-property
browser-compat: api.HTMLOutputElement.htmlFor
---

{{ APIRef("HTML DOM") }}

ویژگی فقط‌خواندنی **`htmlFor`** از {{domxref("HTMLOutputElement")}} یک شیء زنده {{domxref("DOMTokenList")}} برمی‌گرداند که شامل فهرستی از `id` عناصری است که مقادیر ورودی (یا به‌نوعی تحت‌تأثیر) محاسبه را فراهم می‌کنند. این ویژگی، ویژگی محتوایی [`for`](/en-US/docs/Web/HTML/Reference/Elements/output#for) عنصر {{HTMLElement("output")}} را بازتاب می‌دهد.

## مقدار

یک شیء زنده {{domxref("DOMTokenList")}}.

اگرچه خود ویژگی `htmlFor` به این معنا فقط‌خواندنی است که نمی‌توانید شیء `DOMTokenList` را جایگزین کنید، اما همچنان می‌توانید مستقیماً به ویژگی `htmlFor` مقداردهی کنید که معادل مقداردهی به ویژگی {{domxref("DOMTokenList/value", "value")}} آن است. همچنین می‌توانید شیء `DOMTokenList` را با استفاده از روش‌های {{domxref("DOMTokenList/add", "add()")}}، {{domxref("DOMTokenList/remove", "remove()")}}، {{domxref("DOMTokenList/replace", "replace()")}} و {{domxref("DOMTokenList/toggle", "toggle()")}} تغییر دهید.

## مثال‌ها

```js
const outputElem = document.getElementById("result");
for (const id of outputElem.htmlFor.split(" ")) {
  const elem = document.getElementById(id);
  elem.style.outline = "2px solid red";
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("output")}}