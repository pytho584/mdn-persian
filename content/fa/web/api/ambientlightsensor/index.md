---
title: "AmbientLightSensor"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AmbientLightSensor"
translated_by: "n8n + AI"
---

# AmbientLightSensor

رابط **`AmbientLightSensor`** از [Sensor API](/en-US/docs/Web/API/Sensor_APIs) شدت روشنایی محیط اطراف دستگاه میزبان را برمی‌گرداند.

برای استفاده از این حسگر، کاربر باید از طریق [Permissions API](/en-US/docs/Web/API/Permissions_API) مجوز `'ambient-light-sensor'` را صادر کند.

این قابلیت ممکن است توسط یک [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) تنظیم‌شده روی سرور مسدود شود.

این رابط از `Sensor` و `EventTarget` ارث‌بری می‌کند.

> [!NOTE]
> این رابط فقط در محیط‌های امن (HTTPS) در دسترس است و هنوز در مرحله آزمایشی قرار دارد.

## سازنده

- `AmbientLightSensor()` {{Experimental_Inline}}
  - : یک شیء جدید `AmbientLightSensor` می‌سازد.

## ویژگی‌های نمونه

- `illuminance` (فقط خواندنی، آزمایشی)
  - : میزان نور فعلی (بر حسب [لوکس](https://en.wikipedia.org/wiki/Lux)) محیط اطراف دستگاه میزبان را برمی‌گرداند.

## متدهای نمونه

`AmbientLightSensor` متد اختصاصی ندارد، اما متدها را از رابط‌های والد خود، `Sensor` و `EventTarget`، به ارث می‌برد.

## رویدادها

`AmbientLightSensor` رویداد اختصاصی ندارد، اما رویدادها را از رابط والد خود، `Sensor`، به ارث می‌برد.

## مثال

```js
if ("AmbientLightSensor" in window) {
  const sensor = new AmbientLightSensor();
  sensor.addEventListener("reading", (event) => {
    console.log("Current light level:", sensor.illuminance);
  });
  sensor.addEventListener("error", (event) => {
    console.log(event.error.name, event.error.message);
  });
  sensor.start();
}
```

## مشخصات

برای اطلاعات دقیق، به [صفحه مشخصات](https://w3c.github.io/ambient-light/) مراجعه کنید.

## سازگاری مرورگرها

اطلاعات سازگاری را می‌توانید در [جدول MDN](https://developer.mozilla.org/en-US/docs/Web/API/AmbientLightSensor#browser_compatibility) مشاهده کنید.