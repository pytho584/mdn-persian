```markdown
---
title: "Location: protocol property"
short-title: protocol
slug: Web/API/Location/protocol
page-type: web-api-instance-property
browser-compat: api.Location.protocol
---

{{ApiRef("Location")}}

ویژگی **`protocol`** از رابط {{domxref("Location")}} یک رشته است که شامل پروتکل یا طرح (scheme) نشانی وب (URL) موقعیت مکانی، به همراه کاراکتر `":"` در انتها می‌باشد.

این ویژگی را می‌توان برای تغییر پروتکل نشانی وب تنظیم کرد. اگر رشتهٔ ارائه‌شده دارای `":"` نباشد، این کاراکتر به انتهای آن اضافه می‌شود. طرح ارائه‌شده باید با بقیهٔ نشانی وب سازگار باشد تا معتبر در نظر گرفته شود.

برای اطلاعات بیشتر به {{domxref("URL.protocol")}} مراجعه کنید.

## مقدار

یک رشته.

## مثال‌ها

```js
// Let's an <a id="myAnchor" href="https://developer.mozilla.org/en-US/Location.protocol"> element be in the document
const anchor = document.getElementById("myAnchor");
const result = anchor.protocol; // Returns:'https:'
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}
```