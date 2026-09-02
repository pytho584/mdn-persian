---
title: "MediaSession: setScreenshareActive() method"
---

---
title: "MediaSession: setScreenshareActive() method"
short-title: setScreenshareActive()
slug: Web/API/MediaSession/setScreenshareActive
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.MediaSession.setScreenshareActive
---

{{APIRef("Media Session API")}}{{SeeCompatTable}}

متد **`setScreenshareActive()`** از رابط {{domxref("MediaSession")}} برای نشان دادن این‌که آیا اشتراک‌گذاری صفحه کاربر فعال در نظر گرفته می‌شود یا نه، به عامل کاربر استفاده می‌شود.

این متد را بر روی شیء {{domxref("navigator.mediaSession", "mediaSession")}} از شیء `navigator` فراخوانی کنید.

توجه داشته باشید که وضعیت اشتراک‌گذاری صفحه در خود {{domxref("MediaSession")}} پیگیری نمی‌شود و باید به‌طور جداگانه پیگیری شود.

## سینتکس

```js-nolint
setScreenshareActive(active)
```

### پارامترها

- `active`
  - : یک مقدار بولین که نشان می‌دهد آیا اشتراک‌گذاری صفحه فعال در نظر گرفته می‌شود یا نه.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

در ادامه نمونه‌ای از به‌روزرسانی وضعیت فعال بودن اشتراک‌گذاری صفحه در {{domxref('MediaSession')}} جاری و همچنین گوش دادن به درخواست‌های تغییر وضعیت اشتراک‌گذاری صفحه با استفاده از {{domxref("MediaSession.setActionHandler", "setActionHandler()")}} ارائه شده است.

```js
let screenshareActive = false;

navigator.mediaSession.setCameraActive(cameraActive);

navigator.mediaSession.setActionHandler("togglescreenshare", () => {
  screenshareActive = !screenshareActive;
  navigator.mediaSession.setCameraActive(screenshareActive);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}