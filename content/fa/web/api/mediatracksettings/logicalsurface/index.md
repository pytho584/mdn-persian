---
title: "MediaTrackSettings: logicalSurface property"
short-title: logicalSurface
slug: Web/API/MediaTrackSettings/logicalSurface
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.logicalSurface_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`logicalSurface`** در فرهنگ لغت {{domxref("MediaTrackSettings")}} مشخص می‌کند که آیا ناحیه نمایشی که در حال ضبط است یک سطح منطقی (logical surface) است یا خیر. سطوح منطقی سطوحی هستند که لزوماً به طور کامل روی صفحه نمایش دیده نمی‌شوند، یا حتی ممکن است کاملاً خارج از صفحه باشند؛ مانند بافرهای پشتیبان پنجره‌ها (جایی که تنها بخشی از بافر بدون اسکرول کردن پنجره‌ی محتوا قابل مشاهده است) و زمینه‌های رندر خارج از صفحه (offscreen rendering contexts).

## مقدار

یک مقدار بولین که اگر ویدیوی موجود در جریان ویدیوی ضبط‌شده از یک سطح نمایش منطقی گرفته شده باشد، `true` است.

رایج‌ترین سناریویی که در آن یک سطح نمایش ممکن است منطقی باشد، زمانی است که سطح انتخاب‌شده شامل کل ناحیه محتوای یک پنجره باشد که برای نمایش یکجا روی صفحه بیش از حد بزرگ است. از آنجا که پنجره‌ای که سطح را در خود دارد باید اسکرول شود تا بقیه محتوا نمایش داده شود، آن سطح یک سطح منطقی است.

یک سطح نمایش قابل مشاهده (یعنی سطحی که برای آن `logicalSurface` مقدار `false` برمی‌گرداند) بخشی از یک سطح نمایش منطقی است که در حال حاضر روی صفحه نمایش دیده می‌شود.

به عنوان مثال، یک عامل کاربر (user agent) _ممکن است_ به کاربر اجازه دهد انتخاب کند که آیا کل سند (یک `browser` با مقدار `logicalSurface` برابر با `true`) را به اشتراک بگذارد یا فقط بخش قابل مشاهده فعلی سند را (که در آن `logicalSurface` سطح `browser` برابر با `false` است).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Screen Capture API](/en-US/docs/Web/API/Screen_Capture_API)
- [استفاده از API ضبط صفحه](/en-US/docs/Web/API/Screen_Capture_API/Using_Screen_Capture)
- [قابلیت‌ها، محدودیت‌ها و تنظیمات](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaDevices.getDisplayMedia()")}}
- {{domxref("MediaStreamTrack.getConstraints()")}}
- {{domxref("MediaStreamTrack.applyConstraints()")}}
- {{domxref("MediaStreamTrack.getSettings()")}}