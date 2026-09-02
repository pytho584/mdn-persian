---
title: "MediaTrackConstraints: displaySurface property"
short-title: displaySurface
slug: Web/API/MediaTrackConstraints/displaySurface
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.displaySurface_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`displaySurface`** از دیکشنری {{domxref("MediaTrackConstraints")}} یک [`ConstrainDOMString`](/en-US/docs/Web/API/MediaTrackConstraints#constraindomstring) است که مقدار ترجیحی برای ویژگی قابل‌محدودیت {{domxref("MediaTrackSettings.displaySurface","displaySurface")}} را توصیف می‌کند.

این ویژگی توسط برنامه تنظیم می‌شود تا نوع سطح نمایش (`window`, `browser`, یا `monitor`) مورد ترجیح برنامه را به عامل کاربر (user agent) شناسایی کند. این ویژگی بر آنچه کاربر می‌تواند برای اشتراک‌گذاری انتخاب کند، تأثیری ندارد، اما ممکن است برای نمایش گزینه‌ها به ترتیب متفاوت استفاده شود.

در صورت نیاز، می‌توانید با بررسی مقدار {{domxref("MediaTrackSupportedConstraints.displaySurface")}} که توسط فراخوانی {{domxref("MediaDevices.getSupportedConstraints()")}} بازگردانده می‌شود، تعیین کنید که آیا این محدودیت پشتیبانی می‌شود یا خیر. با این حال، معمولاً این کار ضروری نیست، زیرا مرورگرها هر محدودیتی را که با آن آشنا نباشند نادیده می‌گیرند.

## مقدار

یک [`ConstrainDOMString`](/en-US/docs/Web/API/MediaTrackConstraints#constraindomstring) که نوع سطح نمایش ترجیحی توسط برنامه را مشخص می‌کند. این مقدار _منابع نمایش را در رابط کاربری مرورگر اضافه یا حذف نمی‌کند_، اما ممکن است آن‌ها را مرتب‌سازی کند. شما نمی‌توانید از این ویژگی برای محدود کردن کاربر به زیرمجموعه‌ای از سه مقدار سطح نمایش `window`، `browser` و `monitor` استفاده کنید — اما، همانطور که در زیر خواهید دید، می‌توانید ببینید چه چیزی انتخاب شده و آن را رد کنید.

به [چگونگی تعریف محدودیت‌ها](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints#how_constraints_are_defined) مراجعه کنید.

> [!NOTE]
> شما نمی‌توانید [`monitorTypeSurfaces: "exclude"`](/en-US/docs/Web/API/MediaDevices/getDisplayMedia#monitortypesurfaces) را همزمان با `displaySurface: "monitor"` تنظیم کنید، زیرا این دو تنظیم متناقض هستند. تلاش برای انجام این کار منجر به شکست فراخوانی `getDisplayMedia()` مربوطه با خطای `TypeError` می‌شود.

## یادداشت‌های استفاده

پس از ایجاد رسانه نمایش توسط {{domxref("MediaDevices.getDisplayMedia", "getDisplayMedia()")}}، می‌توانید تنظیمات انتخاب‌شده توسط عامل کاربر را با فراخوانی {{domxref("MediaStreamTrack.getSettings", "getSettings()")}} روی {{domxref("MediaStreamTrack")}} ویدیوی رسانه نمایش بررسی کنید و سپس مقدار شیء {{domxref("MediaTrackSettings.displaySurface", "displaySurface")}} از شیء {{domxref("MediaTrackSettings")}} بازگردانده‌شده را بررسی کنید.

برای مثال، اگر برنامه شما ترجیح می‌دهد یک مانیتور را به اشتراک نگذارد — به این معنی که احتمالاً یک پس‌زمینه غیرمحتوایی در حال ضبط است — می‌تواند از کدی مشابه این استفاده کند:

```js
let mayHaveBackdropFlag = false;
let displaySurface = displayStream
  .getVideoTracks()[0]
  .getSettings().displaySurface;

if (displaySurface === "monitor") {
  mayHaveBackdropFlag = true;
}
```

پس از این کد، اگر سطح نمایش موجود در جریان از نوع `monitor` باشد، `mayHaveBackdrop` برابر با `true` خواهد بود. کدهای بعدی می‌توانند از این پرچم برای تعیین اینکه آیا پردازش ویژه‌ای انجام شود، مانند حذف یا جایگزینی پس‌زمینه، یا "برش" نواحی نمایش جداگانه از فریم‌های ویدیوی دریافتی، استفاده کنند.

## مثال‌ها

در اینجا چند نمونه از اشیاء محدودیت برای `getDisplayMedia()` آورده شده است که از ویژگی `displaySurface` استفاده می‌کنند.

```js
dsConstraints = { displaySurface: "window" }; // 'browser' and 'monitor' are also possible
applyConstraints(dsConstraints);
// The user still may choose to share the monitor or the browser,
// but we indicated that a window is preferred.
```

علاوه بر این، به مثال
[تمرین‌کننده محدودیت](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints#example_constraint_exerciser) مراجعه کنید
که نحوه استفاده از محدودیت‌ها را نشان می‌دهد.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [API ضبط صفحه](/en-US/docs/Web/API/Screen_Capture_API)
- [استفاده از API ضبط صفحه](/en-US/docs/Web/API/Screen_Capture_API/Using_Screen_Capture)
- [قابلیت‌ها، محدودیت‌ها و تنظیمات](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaTrackConstraints")}}
- {{domxref("MediaDevices.getSupportedConstraints()")}}
- {{domxref("MediaTrackSupportedConstraints")}}