---
title: "MediaSession: setCameraActive() method"
short-title: setCameraActive()
slug: Web/API/MediaSession/setCameraActive
page-type: web-api-instance-method
browser-compat: api.MediaSession.setCameraActive
---

{{APIRef("Media Session API")}}

متد **`setCameraActive()`** از رابط {{domxref("MediaSession")}} برای اطلاع‌رسانی به عامل کاربر (user agent) استفاده می‌شود که آیا دوربین کاربر فعال در نظر گرفته می‌شود یا خیر.

این متد را بر روی شیء {{domxref("navigator.mediaSession", "mediaSession")}} در شیء `navigator` فراخوانی کنید.

توجه داشته باشید که وضعیت دوربین در خود {{domxref("MediaSession")}} پیگیری نمی‌شود و باید به‌طور جداگانه نگهداری شود.

## Syntax

```js-nolint
setCameraActive(active)
```

### Parameters

- `active`
  - : یک مقدار بولی (boolean) که نشان می‌دهد آیا دوربین فعال در نظر گرفته می‌شود یا نه.

### Return value

هیچ مقدار ({{jsxref("undefined")}}).

## Examples

در زیر نمونه‌ای از به‌روزرسانی وضعیت فعال بودن دوربین برای {{domxref('MediaSession')}} فعلی و همچنین گوش دادن به درخواست‌های تغییر وضعیت دوربین با استفاده از {{domxref("MediaSession.setActionHandler", "setActionHandler()")}} آورده شده است.

```js
let cameraActive = false;

navigator.mediaSession.setCameraActive(cameraActive);

navigator.mediaSession.setActionHandler("togglecamera", () => {
  cameraActive = !cameraActive;
  navigator.mediaSession.setCameraActive(cameraActive);
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}