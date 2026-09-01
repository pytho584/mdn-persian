---
title: "HTMLAreaElement: protocol property"
short-title: protocol
slug: Web/API/HTMLAreaElement/protocol
page-type: web-api-instance-property
browser-compat: api.HTMLAreaElement.protocol
---

{{ApiRef("HTML DOM")}}

ویژگی **`protocol`** از رابط {{domxref("HTMLAreaElement")}}، رشته‌ای است که پروتکل یا طرح (scheme) `href` عنصر `<area>` را به‌همراه `":"` پایانی در بر می‌گیرد.

این ویژگی قابل تنظیم است تا پروتکل URL تغییر کند. اگر کاراکتر `":"` در انتهای رشتهٔ ارائه‌شده وجود نداشته باشد، به آن اضافه می‌شود. برای اینکه طرح ارائه‌شده معتبر باشد، باید با بقیهٔ URL سازگار باشد.

برای اطلاعات بیشتر، {{domxref("URL.protocol")}} را ببینید.

## مقدار

یک رشته.

## مثال‌ها

### گرفتن پروتکل یک پیوند area

```js
// An <area id="myArea" href="https://developer.mozilla.org/en-US/HTMLAreaElement"> element is in the document
const area = document.getElementById("myArea");
area.protocol; // returns 'https:'
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("HTMLAreaElement")}} که این ویژگی به آن تعلق دارد.