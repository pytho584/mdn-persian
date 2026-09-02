---
title: "MediaSession: setMicrophoneActive() method"
short-title: setMicrophoneActive()
slug: Web/API/MediaSession/setMicrophoneActive
page-type: web-api-instance-method
browser-compat: api.MediaSession.setMicrophoneActive
---

{{APIRef("Media Session API")}}

متد **`setMicrophoneActive()`** از رابط {{domxref("MediaSession")}} برای اطلاع‌رسانی به عامل کاربر (user agent) استفاده می‌شود که آیا میکروفون کاربر در حال حاضر بی‌صدا (muted) در نظر گرفته می‌شود یا خیر.

این متد را روی شیء {{domxref("navigator.mediaSession", "mediaSession")}} متعلق به شیء `navigator` فراخوانی کنید.

توجه داشته باشید که وضعیت میکروفون در خود {{domxref("MediaSession")}} ردیابی نمی‌شود و باید به‌طور جداگانه نگهداری شود.

## نحو (Syntax)

```js-nolint
setMicrophoneActive(active)
```

### پارامترها

- `active`
  - : یک مقدار بولی (boolean) که نشان می‌دهد آیا میکروفون بی‌صدا در نظر گرفته می‌شود یا نه.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

در زیر نمونه‌ای از به‌روزرسانی وضعیت بی‌صدا بودن میکروفون برای {{domxref('MediaSession')}} فعلی و همچنین گوش دادن به درخواست‌های تغییر وضعیت بی‌صدا با استفاده از {{domxref("MediaSession.setActionHandler", "setActionHandler()")}} آورده شده است.

```js
let microphoneActive = false;

navigator.mediaSession.setMicrophoneActive(microphoneActive);

navigator.mediaSession.setActionHandler("togglemicrophone", () => {
  microphoneActive = !microphoneActive;
  navigator.mediaSession.setMicrophoneActive(microphoneActive);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}