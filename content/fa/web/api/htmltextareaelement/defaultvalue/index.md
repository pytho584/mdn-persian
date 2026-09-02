---
title: "HTMLTextAreaElement: defaultValue property"
short-title: defaultValue
slug: Web/API/HTMLTextAreaElement/defaultValue
page-type: web-api-instance-property
browser-compat: api.HTMLTextAreaElement.defaultValue
---

{{ APIRef("HTML DOM") }}

خاصیت **`defaultValue`** در رابط {{DOMxRef("HTMLTextAreaElement")}} محتوای متنی پیش‌فرض این ناحیه متنی را نشان می‌دهد. خواندن و نوشتن این مقدار معادل خواندن و نوشتن {{domxref("Node.textContent", "textContent")}} روی عنصر {{htmlelement("textarea")}} است.

## مقدار

یک رشته (string).

## مثال‌ها

در مثال زیر، `defaultValue` همچنان مقداری را برمی‌گرداند که در ابتدا در HTML نوشته شده بود. اگر یک مقدار پیش‌فرض، چه از طریق HTML و چه از طریق خاصیت `defaultValue`، تعیین شود، ورودی کاربر مقدار `value` را به‌روزرسانی می‌کند اما مقدار `defaultValue` را بازنویسی نمی‌کند.

```js
const textareaElement = document.getElementById("comment");
console.log(textArea.defaultValue);
textArea.defaultValue = "This is the default text now!";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLElement("textarea")}}
- {{DOMXref("HTMLTextAreaElement.value")}}