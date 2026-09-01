---
title: "HTMLIFrameElement: privateToken property"
short-title: privateToken
slug: Web/API/HTMLIFrameElement/privateToken
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.HTMLIFrameElement.privateToken
---

{{APIRef("HTML DOM")}}{{SeeCompatTable}}

خاصیت **`privateToken`** از رابط {{domxref("HTMLIFrameElement")}} یک رشته (string) است که شیء گزینه‌های یک عملیات [private state token](/en-US/docs/Web/API/Private_State_Token_API/Using) را نشان می‌دهد؛ این شیء همان ساختار خاصیت [`privateToken`](/en-US/docs/Web/API/RequestInit#privatetoken) در دیکشنری `RequestInit` را دارد.

این ویژگی محتوای ویژگی [`privateToken`](/en-US/docs/Web/HTML/Reference/Elements/iframe#privatetoken) عنصر `<iframe>` مرتبط را منعکس می‌کند.

## مقدار

یک رشته.

## مثال‌ها

```html
<iframe id="el" privateToken="{version: 1,operation: 'token-request'}">
</iframe>
```

```js
const el = document.getElementById("el");
console.log(el.privateToken);
// Logs "{version: 1,operation: 'token-request'}"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Private State Token API](/en-US/docs/Web/API/Private_State_Token_API)