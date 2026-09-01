---
title: "HTMLGeolocationElement: autolocate property"
short-title: autolocate
slug: Web/API/HTMLGeolocationElement/autolocate
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.HTMLGeolocationElement.autolocate
---

{{APIRef("Navigation API")}}{{SeeCompatTable}}

ویژگی **`autolocate`** از رابط {{domxref("HTMLGeolocationElement")}} یک مقدار بولین را دریافت و تنظیم می‌کند که نشان می‌دهد آیا مرورگر باید به‌محض رندر شدن عنصر {{htmlelement("geolocation")}} داده‌های موقعیت مکانی را درخواست کند یا خیر، به شرطی که مجوز استفاده از قابلیت `geolocation` از قبل صادر شده باشد.

این ویژگی، مقدار ویژگی [`autolocate`](/en-US/docs/Web/HTML/Reference/Elements/geolocation#autolocate) عنصر `<geolocation>` را منعکس می‌کند.

## مقدار

یک مقدار بولین:

- اگر `true` باشد، داده‌های موقعیت مکانی به‌محض رندر شدن عنصر `<geolocation>` درخواست می‌شوند، به شرطی که مجوز استفاده از قابلیت `geolocation` قبلاً صادر شده باشد.
- اگر `false` باشد، داده‌های موقعیت مکانی فقط زمانی درخواست می‌شوند که کاربر دکمه‌ی `<geolocation>` را فشار دهد.

مقدار پیش‌فرض `false` است.

اگر مجوز استفاده از قابلیت `geolocation` قبلاً صادر نشده باشد، ویژگی `autolocate` نادیده گرفته می‌شود.

## مثال‌ها

### استفاده‌ی پایه

```html
<geolocation autolocate></geolocation>
```

```js
const geo = document.querySelector("geolocation");
console.log(geo.autolocate); // true
```

برای یک مثال واقعی که شامل `autolocate` است، [شرح گام‌به‌گام مثال نقشه‌ی جاسازی‌شده](/en-US/docs/Web/API/HTMLGeolocationElement#embedded_map_example) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- عنصر {{htmlelement("geolocation")}}