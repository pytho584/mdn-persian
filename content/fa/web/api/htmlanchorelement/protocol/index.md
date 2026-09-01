---
title: "HTMLAnchorElement: protocol property"
short-title: protocol
slug: Web/API/HTMLAnchorElement/protocol
page-type: web-api-instance-property
browser-compat: api.HTMLAnchorElement.protocol
---

{{ApiRef("HTML DOM")}}

ویژگی **`protocol`** در رابط {{domxref("HTMLAnchorElement")}} یک رشته است که پروتکل یا طرح (scheme) موجود در `href` عنصر `<area>` را شامل می‌شود، به همراه «`:`» پایانی.

این ویژگی قابل تنظیم است تا پروتکل URL تغییر کند. اگر رشتهٔ داده‌شده «`:`» انتهایی نداشته باشد، به آن اضافه می‌شود. طرح داده‌شده باید با بقیهٔ URL سازگار باشد تا معتبر در نظر گرفته شود.

برای اطلاعات بیشتر، {{domxref("URL.protocol")}} را ببینید.

## مقدار

یک رشته.

## مثال‌ها

### دریافت پروتکل یک پیوند anchor

```js
// An <a id="myAnchor" href="https://developer.mozilla.org/en-US/HTMLAnchorElement"> element is in the document
const anchor = document.getElementById("myAnchor");
anchor.protocol; // returns 'https:'
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("HTMLAnchorElement")}} که این ویژگی به آن تعلق دارد.