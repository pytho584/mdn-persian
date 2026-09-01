---
title: "HTMLImageElement: referrerPolicy property"
short-title: referrerPolicy
slug: Web/API/HTMLImageElement/referrerPolicy
page-type: web-api-instance-property
browser-compat: api. HTMLImageElement.referrerPolicy
---

{{APIRef("HTML DOM")}}

ویژگی **`referrerPolicy`** از رابط {{domxref("HTMLImageElement")}} تعیین می‌کند که کدام ارجاع‌دهنده (referrer) هنگام واکشی منبع ارسال شود. این ویژگی منعکس‌کننده ویژگی محتوای `referrerpolicy` عنصر `<img>` (مشاهده [`referrerpolicy`](/en-US/docs/Web/HTML/Reference/Elements/img#referrerpolicy) در HTML) است.

## مقدار

یک رشته (string) که مقدار آن یکی از `no-referrer`، `no-referrer-when-downgrade`، `origin`، `origin-when-cross-origin`، `same-origin`، `strict-origin`، `strict-origin-when-cross-origin` یا `unsafe-url` است. برای معانی هر یک، به مستندات HTML [`<img>`](/en-US/docs/Web/HTML/Reference/Elements/img#referrerpolicy) مراجعه کنید.

## مثال‌ها

```js
const img = new Image();
img.src = "img/logo.png";
img.referrerPolicy = "origin";

const div = document.getElementById("divAround");
div.appendChild(img); // واکشی تصویر با استفاده از origin به عنوان ارجاع‌دهنده
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLAnchorElement.referrerPolicy")}}
- {{domxref("HTMLAreaElement.referrerPolicy")}}
- {{domxref("HTMLIFrameElement.referrerPolicy")}}