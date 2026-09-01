---
title: "DeviceMotionEvent: requestPermission() static method"
short-title: requestPermission()
slug: Web/API/DeviceMotionEvent/requestPermission_static
page-type: web-api-static-method
browser-compat: api.DeviceMotionEvent.requestPermission_static
---

{{APIRef("Device Orientation Events")}}{{securecontext_header}}

متد ایستای **`requestPermission()``** از رابط {{domxref("DeviceMotionEvent")}} درخواست اجازه کاربر برای دسترسی به داده‌های حرکت دستگاه از حسگرهای شتاب‌سنج و ژیروسکوپ را می‌کند. این متد به {{Glossary("transient activation")}} (فعال‌سازی موقت) نیاز دارد، به این معنی که باید توسط یک رویداد UI مانند کلیک روی دکمه فراخوانی شود.

## Syntax

```js-nolint
DeviceMotionEvent.requestPermission()
```

### Parameters

هیچ.

### Return value

یک {{jsxref("Promise")}} که با یک رشته حل می‌شود که یا `"granted"` است یا `"denied"`.

### Exceptions

پرامیزی که برگردانده می‌شود با استثناهای زیر رد می‌شود:

- `NotAllowedError` {{domxref("DOMException")}}
  - : وضعیت مجوز `"prompt"` است و تابع فراخواننده {{Glossary("transient activation")}} ندارد.

## Security

[فعال‌سازی موقت کاربر](/en-US/docs/Web/Security/Defenses/User_activation) مورد نیاز است. کاربر باید با صفحه یا یک عنصر UI تعامل داشته باشد تا این ویژگی کار کند.

## Examples

### درخواست مجوز حرکت دستگاه هنگام کلیک

```js
document.querySelector("button").addEventListener("click", async () => {
  if (typeof DeviceMotionEvent.requestPermission !== "function") {
    // این ویژگی در دسترس نیست یا به مجوز نیاز ندارد.
    return;
  }

  const permission = await DeviceMotionEvent.requestPermission();
  if (permission === "granted") {
    window.addEventListener("devicemotion", (event) => {
      console.log(`Acceleration X: ${event.acceleration.x}`);
      console.log(`Acceleration Y: ${event.acceleration.y}`);
      console.log(`Acceleration Z: ${event.acceleration.z}`);
    });
  }
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("DeviceMotionEvent")}}
- {{domxref("DeviceOrientationEvent.requestPermission_static", "DeviceOrientationEvent.requestPermission()")}}
- رویداد {{domxref("Window.devicemotion_event", "devicemotion")}}
- {{domxref("Device orientation events/Detecting device orientation", "تشخیص جهت‌گیری دستگاه", "", "nocode")}}