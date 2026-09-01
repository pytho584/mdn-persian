---
title: "HTMLOutputElement: value property"
short-title: value
slug: Web/API/HTMLOutputElement/value
page-type: web-api-instance-property
browser-compat: api.HTMLOutputElement.value
---

{{ APIRef("HTML DOM") }}

خاصیت **`value`** از رابط {{DOMxRef("HTMLOutputElement")}} مقدار عنصر {{htmlelement("output")}} را به صورت یک رشته نمایش می‌دهد، یا اگر مقداری تنظیم نشده باشد، رشته خالی. این خاصیت محتویات عنصر را برمی‌گرداند یا تنظیم می‌کند، مشابه خاصیت {{domxref("Node.textContent","textContent")}}.

> [!NOTE]
> هنگامی که خاصیت `value` یک عنصر `<output>` تنظیم می‌شود، عنصر وارد حالت value می‌شود و مقدار پیش‌فرض فقط از طریق خاصیت {{DOMXref("HTMLOutputElement.defaultValue")}} قابل دسترسی است.

## مقدار

یک رشته شامل محتویات عنصر {{htmlelement("output")}}.

## مثال‌ها

```js
const outputElement = document.getElementById("log");
console.log(`value: ${outputElement.value}`);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("output")}}
- {{DOMXref("HTMLOutputElement.defaultValue")}}
- {{DOMXref("HTMLOutputElement.labels")}}
- {{DOMXref("HTMLOutputElement.htmlFor")}}