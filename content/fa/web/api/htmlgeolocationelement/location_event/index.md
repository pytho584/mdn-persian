---
title: "HTMLGeolocationElement: location event"
short-title: location
slug: Web/API/HTMLGeolocationElement/location_event
page-type: web-api-event
status:
  - experimental
browser-compat: api.HTMLGeolocationElement.location_event
---

{{APIRef("HTML DOM")}}{{SeeCompatTable}}

رویداد **`location`** از رابط {{domxref("HTMLGeolocationElement")}} هر زمان که مرورگر داده‌های موقعیت مکانی را دریافت کند، یا زمانی که درخواست داده موقعیت مکانی ناموفق باشد و اطلاعات خطا دریافت شود، فعال می‌شود.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("location", (event) => { })

onlocation = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}}.

## مثال‌ها

### استفاده از `location` برای پاسخ به داده‌های موقعیت و خطاها

در [نمایش نقشه جاسازی‌شده](https://mdn.github.io/dom-examples/geolocation-element/embedded-map/) ما ([کد منبع](https://github.com/mdn/dom-examples/tree/main/geolocation-element/embedded-map))، از یک کنترل‌کننده رویداد `location` برای پاسخ به داده‌های موقعیت مکانی و خطاهای دریافتی استفاده کرده‌ایم:

```js
geo.addEventListener("location", () => {
  if (geo.position) {
    console.log(
      `${geo.position.coords.latitude},${geo.position.coords.longitude}`,
    );
    drawMap(geo.position.coords.latitude, geo.position.coords.longitude, geo);
  } else if (geo.error) {
    console.log(geo.error.message);
  }
});
```

اگر داده‌های موقعیت با موفقیت بازگردانده شوند، از طریق ویژگی {{domxref("HTMLGeolocationElement.position")}} به آن‌ها دسترسی پیدا می‌کنیم و مقادیر عرض جغرافیایی (latitude) و طول جغرافیایی (longitude) را بازیابی می‌کنیم. این مقادیر را در کنسول ثبت می‌کنیم و سپس با ارسال آن‌ها به تابع `drawMap()` همراه با یک ارجاع به شیء `HTMLGeolocationElement`، آن‌ها را روی نقشه رسم می‌کنیم. اگر درخواست داده ناموفق باشد، از طریق ویژگی {{domxref("HTMLGeolocationElement.error")}} به خطا دسترسی پیدا کرده و پیام خطا را در کنسول ثبت می‌کنیم.

برای توضیح کامل این مثال، به صفحه اصلی {{domxref("HTMLGeolocationElement")}} مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- عنصر {{htmlelement("geolocation")}}