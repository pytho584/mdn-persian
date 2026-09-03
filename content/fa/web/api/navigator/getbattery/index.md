---
title: "Navigator: روش getBattery()"
short-title: getBattery()
slug: Web/API/Navigator/getBattery
page-type: web-api-instance-method
browser-compat: api.Navigator.getBattery
---

{{ApiRef("Battery API")}}{{securecontext_header}}

روش **`getBattery()`** اطلاعاتی در مورد باتری سیستم ارائه می‌دهد.
این روش یک قول (Promise) باتری بازمی‌گرداند که با یک شیء {{domxref("BatteryManager")}} حل می‌شود. این شیء ویژگی‌هایی برای دریافت وضعیت باتری و همچنین رویدادهایی برای نظارت بر تغییرات وضعیت باتری در اختیار شما قرار می‌دهد.
این روش {{domxref("Battery Status API", "", "", "nocode")}} را پیاده‌سازی می‌کند؛ برای جزئیات بیشتر، راهنمای استفاده از API و نمونه کد، به آن مستندات مراجعه کنید.

از Chrome 103 به بعد، روش `Navigator.getBattery()` از {{domxref("Battery Status API", "", "", "nocode")}} فقط در بافت‌های امن (secure context) در دسترس است.

> [!NOTE]
> دسترسی به این ویژگی ممکن است توسط دستور {{HTTPHeader("Permissions-Policy")}} با نام {{HTTPHeader("Permissions-Policy/battery", "battery")}} کنترل شود.

## نحو

```js-nolint
getBattery()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک {{JSxRef("Promise")}} که با یک شیء {{DOMxRef("BatteryManager")}} حل می‌شود. از این شیء می‌توانید برای دریافت اطلاعات وضعیت باتری استفاده کنید.

### استثناها

- `NotAllowedError` {{domxref("DOMException")}}
  - : استفاده از این ویژگی توسط [خط‌مشی مجوزها](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) مسدود شده است.

- `SecurityError` {{domxref("DOMException")}}
  - : عامل کاربر (User Agent) اطلاعات باتری را در بافت‌های ناامن در معرض نمایش قرار نمی‌دهد و این روش از یک بافت ناامن فراخوانی شده است.

## مثال‌ها

این مثال وضعیت فعلی شارژ باتری را دریافت می‌کند و یک کنترل‌کننده برای رویداد {{domxref("BatteryManager/chargingchange_event", "chargingchange")}} تنظیم می‌کند تا وضعیت شارژ در هر بار تغییر ثبت شود.

```js
let batteryIsCharging = false;

navigator.getBattery().then((battery) => {
  batteryIsCharging = battery.charging;

  battery.addEventListener("chargingchange", () => {
    batteryIsCharging = battery.charging;
  });
});
```

برای مثال‌ها و جزئیات بیشتر، به {{domxref("Battery Status API", "", "", "nocode")}} مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Battery Status API", "", "", "nocode")}}
- دستور {{HTTPHeader("Permissions-Policy")}} با نام {{HTTPHeader("Permissions-Policy/battery", "battery")}}