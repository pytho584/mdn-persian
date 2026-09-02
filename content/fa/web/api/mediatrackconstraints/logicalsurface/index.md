---
title: "MediaTrackConstraints: logicalSurface property"
short-title: logicalSurface
slug: Web/API/MediaTrackConstraints/logicalSurface
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.logicalSurface_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`logicalSurface`** از دیکشنری {{domxref("MediaTrackConstraints")}} یک [`ConstrainDOMString`](/en-US/docs/Web/API/MediaTrackConstraints#constraindomstring) است که محدودیت‌های درخواستی یا اجباری اعمال‌شده بر مقدار ویژگی قابل‌محدودیت {{domxref("MediaTrackSettings.logicalSurface","logicalSurface")}} را توصیف می‌کند.

این ویژگی برای مشخص کردن این استفاده می‌شود که آیا {{domxref("MediaDevices.getDisplayMedia", "getDisplayMedia()")}} باید به کاربر اجازه دهد سطوح نمایشی را انتخاب کند که لزوماً به طور کامل روی صفحه قابل مشاهده نیستند، مانند پنجره‌های پنهان یا محتوای کامل پنجره‌هایی که به اندازه کافی بزرگ هستند که برای دیدن تمام محتوای آنها نیاز به پیمایش است.

در صورت نیاز، می‌توانید با بررسی مقدار {{domxref("MediaTrackSupportedConstraints.logicalSurface")}} که توسط فراخوانی {{domxref("MediaDevices.getSupportedConstraints()")}} بازگردانده می‌شود، تعیین کنید که آیا این محدودیت پشتیبانی می‌شود یا خیر. با این حال، معمولاً این کار ضروری نیست زیرا مرورگرها هر محدودیتی که با آن آشنا نباشند را نادیده می‌گیرند.

## مقدار

یک [`ConstrainBoolean`](/en-US/docs/Web/API/MediaTrackConstraints#constrainboolean) که مقدار آن `true` است اگر سطوح منطقی (logical surfaces) باید در میان انتخاب‌های موجود برای کاربر مجاز باشند.

به [چگونگی تعریف محدودیت‌ها](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints#how_constraints_are_defined) مراجعه کنید.

## نکات استفاده

می‌توانید تنظیمات انتخاب‌شده توسط عامل کاربر را پس از ایجاد رسانه نمایشی توسط {{domxref("MediaDevices.getDisplayMedia", "getDisplayMedia()")}} با فراخوانی {{domxref("MediaStreamTrack.getSettings", "getSettings()")}} روی {{domxref("MediaStreamTrack")}} ویدئوی رسانه نمایشی بررسی کنید و سپس مقدار شیء {{domxref("MediaTrackSettings.logicalSurface", "logicalSurface")}} از شیء {{domxref("MediaTrackSettings")}} بازگردانده‌شده را بررسی کنید.

به عنوان مثال، اگر برنامه شما نیاز دارد بداند که آیا سطح نمایشی انتخاب‌شده یک سطح منطقی است:

```js
let isLogicalSurface = displayStream
  .getVideoTracks()[0]
  .getSettings().logicalSurface;
```

پس از این کد، `isLogicalSurface` برابر `true` است اگر سطح نمایشی موجود در جریان یک سطح منطقی باشد؛ یعنی سطحی که ممکن است کاملاً روی صفحه نباشد، یا حتی ممکن است کاملاً خارج از صفحه باشد.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [API ضبط صفحه](/en-US/docs/Web/API/Screen_Capture_API)
- [استفاده از API ضبط صفحه](/en-US/docs/Web/API/Screen_Capture_API/Using_Screen_Capture)
- [قابلیت‌ها، محدودیت‌ها و تنظیمات](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaTrackConstraints")}}
- {{domxref("MediaDevices.getSupportedConstraints()")}}
- {{domxref("MediaTrackSupportedConstraints")}}