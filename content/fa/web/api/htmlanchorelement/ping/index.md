---
title: "HTMLAnchorElement: ping property"
short-title: ping
slug: Web/API/HTMLAnchorElement/ping
page-type: web-api-instance-property
browser-compat: api.HTMLAnchorElement.ping
---

{{ApiRef("HTML DOM")}}

ویژگی **`ping`** در رابط {{domxref("HTMLAnchorElement")}} فهرستی از نشانی‌های اینترنتی است که با فاصله جدا شده‌اند. وقتی روی پیوند کلیک شود، مرورگر درخواست‌های {{HTTPMethod("POST")}} با بدنه‌ی «PING» به آن نشانی‌ها ارسال می‌کند.

این ویژگی منعکس‌کنندهٔ ویژگی `ping` عنصر {{HTMLElement("a")}} است.

> [!NOTE]
> این ویژگی در فایرفاکس کارایی ندارد و استفاده از آن ممکن است به دلیل نگرانی‌های مربوط به حریم خصوصی و امنیت محدود باشد.

## مثال

```html
<a
  id="exampleLink"
  href="https://example.com"
  ping="https://example-tracking.com https://example-analytics.com"
  >Example Link</a
>
```

```js
const anchorElement = document.getElementById("exampleLink");
console.log(anchorElement.ping); // Output: "https://example-tracking.com https://example-analytics.com"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی {{domxref("HTMLAreaElement.ping")}}