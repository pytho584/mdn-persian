---
title: "HTMLGeolocationElement: isValid property"
short-title: isValid
slug: Web/API/HTMLGeolocationElement/isValid
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.HTMLGeolocationElement.isValid
---

{{APIRef("Navigation API")}}{{SeeCompatTable}}

خاصیت خواندنی **`isValid`** از رابط {{domxref("HTMLGeolocationElement")}} یک مقدار بولین بازمی‌گرداند که نشان می‌دهد عنصر {{htmlelement("geolocation")}} مرتبط معتبر (معتبر) یا نامعتبر (مسدود) است.

وقتی یک [مسدودکننده](/en-US/docs/Web/HTML/Reference/Elements/geolocation#geolocation_blocking) روی یک عنصر `<geolocation>` فعال باشد، از عملکرد آن جلوگیری می‌شود (نامعتبر می‌شود) – چه به صورت موقت و چه دائمی، بسته به دلیل.

می‌توانید دلیل نامعتبر بودن آن را از طریق خاصیت {{domxref("HTMLGeolocationElement.invalidReason")}} بیابید – برای فهرست کامل دلایل ممکن به آن صفحه مراجعه کنید.

## مقدار

یک مقدار بولین:

- اگر `true` باشد، عنصر `<geolocation>` معتبر و کاربردی است، یعنی می‌توان از آن برای درخواست داده‌های مکان استفاده کرد.
- اگر `false` باشد، عنصر `<geolocation>` نامعتبر و غیرفعال است، یعنی نمی‌توان از آن برای درخواست داده‌های مکان استفاده کرد.

پیش‌فرض `false` است.

## مثال‌ها

### استفاده پایه

```html
<geolocation></geolocation>
```

```js
const geo = document.querySelector("geolocation");
console.log(geo.isValid);
// true، به شرطی که عنصر `<geolocation>` به نحوی مسدود نشده باشد
```

برای یک مثال کامل‌تر که شامل `isValid` می‌شود، به صفحه {{domxref("HTMLGeolocationElement.invalidReason")}} مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- عنصر {{htmlelement("geolocation")}}