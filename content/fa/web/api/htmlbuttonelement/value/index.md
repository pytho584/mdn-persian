---
title: "HTMLButtonElement: value property"
short-title: value
slug: Web/API/HTMLButtonElement/value
page-type: web-api-instance-property
browser-compat: api.HTMLButtonElement.value
---

{{ APIRef("HTML DOM") }}

خاصیت **`value`** در رابط {{DOMxRef("HTMLButtonElement")}} مقدار عنصر {{htmlelement("button")}} را به صورت یک رشته برمیگرداند، یا اگر مقداری تنظیم نشده باشد، رشتهٔ خالی را برمیگرداند. این خاصیت منعکسکنندهٔ ویژگی [`value`](/en-US/docs/Web/HTML/Reference/Elements/button#value) عنصر است.

## مقدار

یک رشته شامل مقدار عنصر {{htmlelement("button")}}.

## مثالها

```js
const buttonElement = document.getElementById("given-name");
console.log(`value: ${buttonElement.value}`);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("button")}}
- {{DOMXref("HTMLButtonElement.type")}}
- {{DOMXref("HTMLButtonElement.labels")}}