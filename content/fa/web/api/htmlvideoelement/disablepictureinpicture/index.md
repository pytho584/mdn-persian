---
title: "HTMLVideoElement: disablePictureInPicture property"
---

---
title: "HTMLVideoElement: disablePictureInPicture property"
short-title: disablePictureInPicture
slug: Web/API/HTMLVideoElement/disablePictureInPicture
page-type: web-api-instance-property
browser-compat: api.HTMLVideoElement.disablePictureInPicture
---

{{APIRef("Picture-in-Picture API")}}

ویژگی {{domxref("HTMLVideoElement")}} با نام **`disablePictureInPicture`**، بازتاب‌دهندهٔ صفت HTML است که نشان می‌دهد آیا قابلیت تصویر-در-تصویر (Picture-in-Picture) برای عنصر جاری غیرفعال شده است یا نه.

این مقدار صرفاً نمایانگر یک درخواست از طرف وب‌سایت به عامل کاربر (user agent) است. ممکن است پیکربندی کاربر، رفتار نهایی را تغییر دهد؛ برای مثال، کاربران فایرفاکس می‌توانند تنظیم `media.videocontrols.picture-in-picture.respect-disablePictureInPicture` را تغییر دهند تا درخواست غیرفعال‌سازی حالت تصویر-در-تصویر (PiP) نادیده گرفته شود.

## مقدار

یک مقدار بولی (boolean) که اگر قابلیت تصویر-در-تصویر برای این عنصر غیرفعال شده باشد، مقدار آن `true` است؛ یعنی عامل کاربر نباید این ویژگی را به کاربران پیشنهاد دهد یا به‌صورت خودکار آن را درخواست کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}