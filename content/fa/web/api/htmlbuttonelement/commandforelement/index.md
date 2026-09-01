---
title: "HTMLButtonElement: commandForElement property"
short-title: commandForElement
slug: Web/API/HTMLButtonElement/commandForElement
page-type: web-api-instance-property
browser-compat: api.HTMLButtonElement.commandForElement
---

{{APIRef("Invoker Commands API")}}

ویژگی **`commandForElement`** در رابط {{domxref("HTMLButtonElement")}}، عنصری را که باید توسط یک دکمه کنترل شود، دریافت و تنظیم می‌کند.

این ویژگی معادل جاوااسکریپتی ویژگی HTML [`commandfor`](/en-US/docs/Web/HTML/Reference/Elements/button#commandfor) است.

## مقدار

ارجاع به یک {{domxref("Element")}} موجود که دکمه آن را کنترل می‌کند.

## مثال‌ها

```js
const popover = document.getElementById("mypopover");
const toggleBtn = document.getElementById("toggleBtn");

toggleBtn.commandForElement = popover;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Invoker Commands API", "Invoker Commands API", "", "nocode")}}
- {{domxref("HTMLButtonElement.command")}}
- {{domxref("CommandEvent")}}