---
title: "HTMLGeolocationElement: position property"
short-title: position
slug: Web/API/HTMLGeolocationElement/position
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.HTMLGeolocationElement.position
---

{{APIRef("Navigation API")}}{{SeeCompatTable}}

خاصیت **`position`** از نوع فقط خواندنی در رابط {{domxref("HTMLGeolocationElement")}} یک شیء {{domxref("GeolocationPosition")}} را برمی‌گرداند که موقعیت کاربر را در صورت دریافت موفقیت‌آمیز داده‌های موقعیت مکانی نشان می‌دهد.

موقعیت دریافت‌شده ممکن است به‌روز باشد یا نباشد. موقعیت کاربر فقط یک بار هنگام فشار دادن دکمه کنترل عنصر `<geolocation>` دریافت می‌شود، مگر اینکه ویژگی [`watch`](/en-US/docs/Web/HTML/Reference/Elements/geolocation#watch) را روی `true` تنظیم کنید، که در این صورت هر بار که دستگاه کاربر جابه‌جا می‌شود یک موقعیت جدید دریافت می‌شود. برای خواندن موقعیت فعلی کاربر، باید خاصیت `position` را در پاسخ به رویداد {{domxref("HTMLGeolocationElement.location_event", "location")}} بخوانید.

اگر دریافت داده‌های موقعیت مکانی با شکست مواجه شود، اطلاعات خطای مربوطه در خاصیت {{domxref("HTMLGeolocationElement.error")}} در دسترس خواهد بود.

## مقدار

یک شیء {{domxref("GeolocationPosition")}}، یا `null` اگر دریافت داده‌های موقعیت مکانی شکست خورده باشد یا داده‌ها هنوز دریافت نشده باشند.

## مثال‌ها

### استفاده پایه

```html
<geolocation autolocate></geolocation>
```

```js
const geo = document.querySelector("geolocation");
geo.addEventListener("location", () => {
  if (geo.position) {
    console.log(
      `(${geo.position.coords.latitude},${geo.position.coords.longitude})`,
    );
  } else if (geo.error) {
    console.log(geo.error.message);
  }
});
```

برای یک مثال واقعی که شامل `position` است، به [راهنمای مثال نقشه جاسازی‌شده](/en-US/docs/Web/API/HTMLGeolocationElement#embedded_map_example) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- عنصر {{htmlelement("geolocation")}}