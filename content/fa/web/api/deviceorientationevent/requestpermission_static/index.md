---
title: "DeviceOrientationEvent: requestPermission() static method"
short-title: requestPermission()
slug: Web/API/DeviceOrientationEvent/requestPermission_static
page-type: web-api-static-method
browser-compat: api.DeviceOrientationEvent.requestPermission_static
---

{{APIRef("Device Orientation Events")}}{{securecontext_header}}

متد ایستای **`requestPermission()`** از رابط {{domxref("DeviceOrientationEvent")}}، مجوز کاربر را برای دسترسی به داده‌های جهت‌گیری دستگاه از سنسورهای شتاب‌سنج و ژیروسکوپ درخواست می‌کند. همچنین می‌تواند برای دسترسی به داده‌های مغناطیس‌سنج زمانی‌ که جهت‌گیری مطلق مورد نیاز است، مجوز درخواست کند. این متد به {{Glossary("transient activation")}} (فعال‌سازی گذرا) نیاز دارد؛ یعنی باید توسط یک رویداد واسط کاربری مانند کلیک روی دکمه فعال شود.

## نحو (Syntax)

```js-nolint
DeviceOrientationEvent.requestPermission()
DeviceOrientationEvent.requestPermission(absolute)
```

### پارامترها

- `absolute` {{optional_inline}}
  - : یک مقدار بولی که نشان می‌دهد آیا داده‌های جهت‌گیری مطلق مورد نیاز است یا خیر. وقتی `true` باشد، درخواست مجوز شامل سنسور مغناطیس‌سنج نیز می‌شود. پیش‌فرض `false` است.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با رشته‌ای که یا `"granted"` است یا `"denied"`، حل می‌شود.

### استثناها

پرامیس بازگشتی با استثناهای زیر رد می‌شود:

- `NotAllowedError` {{domxref("DOMException")}}
  - : وضعیت مجوز `"prompt"` است و تابع فراخوانی‌شده {{Glossary("transient activation")}} ندارد.

## امنیت

[فعال‌سازی گذرای کاربر](/en-US/docs/Web/Security/Defenses/User_activation) الزامی است. کاربر باید با صفحه یا یک عنصر واسط کاربری تعامل کند تا این قابلیت کار کند.

## مثال‌ها

### درخواست مجوز جهت‌گیری دستگاه با کلیک

```js
document.querySelector("button").addEventListener("click", async () => {
  if (typeof DeviceOrientationEvent.requestPermission !== "function") {
    // این قابلیت در دسترس نیست یا نیازی به مجوز ندارد.
    return;
  }

  const permission = await DeviceOrientationEvent.requestPermission();
  if (permission === "granted") {
    window.addEventListener("deviceorientation", (event) => {
      console.log(`Alpha: ${event.alpha}`);
      console.log(`Beta: ${event.beta}`);
      console.log(`Gamma: ${event.gamma}`);
    });
  }
});
```

### درخواست مجوز جهت‌گیری مطلق

وقتی داده‌های جهت‌گیری مطلق مورد نیاز است (مثلاً برای برنامه‌های مبتنی بر قطب‌نما)، مقدار `true` را به‌عنوان پارامتر `absolute` پاس دهید. این کار علاوه بر این، دسترسی به مغناطیس‌سنج را نیز درخواست می‌کند.

```js
document.querySelector("button").addEventListener("click", async () => {
  if (typeof DeviceOrientationEvent.requestPermission !== "function") {
    return;
  }

  const permission = await DeviceOrientationEvent.requestPermission(true);
  if (permission === "granted") {
    window.addEventListener("deviceorientationabsolute", (event) => {
      console.log(`Absolute alpha: ${event.alpha}`);
    });
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("DeviceOrientationEvent")}}
- {{domxref("DeviceMotionEvent.requestPermission_static", "DeviceMotionEvent.requestPermission()")}}
- رویداد {{domxref("Window.deviceorientation_event", "deviceorientation")}}
- رویداد {{domxref("Window.deviceorientationabsolute_event", "deviceorientationabsolute")}}
- {{domxref("Device orientation events/Detecting device orientation", "تشخیص جهت‌گیری دستگاه", "", "nocode")}}