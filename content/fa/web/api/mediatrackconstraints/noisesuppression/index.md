---
title: "MediaTrackConstraints: noiseSuppression property"
short-title: noiseSuppression
slug: Web/API/MediaTrackConstraints/noiseSuppression
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.noiseSuppression_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`noiseSuppression`** از دیکشنری {{domxref("MediaTrackConstraints")}} یک [`ConstrainBoolean`](/en-US/docs/Web/API/MediaTrackConstraints#constrainboolean) است که محدودیت‌های درخواستی یا اجباری اعمال‌شده بر مقدار ویژگی قابل‌محدودیت {{domxref("MediaTrackSettings.noiseSuppression","noiseSuppression")}} را توصیف می‌کند.

در صورت نیاز، می‌توانید با بررسی مقدار {{domxref("MediaTrackSupportedConstraints.noiseSuppression")}} که توسط فراخوانی {{domxref("MediaDevices.getSupportedConstraints()")}} بازگردانده می‌شود، تعیین کنید که آیا این محدودیت پشتیبانی می‌شود یا خیر. با این حال، معمولاً این کار ضروری نیست، زیرا مرورگرها هر محدودیتی را که با آن آشنا نباشند نادیده می‌گیرند.

سرکوب نویز معمولاً توسط میکروفون‌ها ارائه می‌شود، اگرچه می‌تواند توسط سایر منابع ورودی نیز ارائه شود.

## مقدار

اگر این مقدار یک `true` یا `false` ساده باشد، عامل کاربر (user agent) تلاش می‌کند تا در صورت امکان، رسانه‌ای با سرکوب نویز فعال یا غیرفعال (مطابق مشخص‌شده) به دست آورد، اما در صورت عدم امکان، شکست نخواهد خورد. اگر مقدار به‌جای آن به‌صورت یک شیء با فیلد `exact` داده شود، مقدار بولی آن فیلد یک تنظیم الزامی برای ویژگی سرکوب نویز را مشخص می‌کند. اگر این تنظیم قابل برآورده شدن نباشد، درخواست منجر به خطا خواهد شد.

## مثال‌ها

به مثال [تمرین‌کننده محدودیت‌ها](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints#example_constraint_exerciser) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [API ضبط و جریان‌های رسانه](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [قابلیت‌ها، محدودیت‌ها و تنظیمات](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaTrackConstraints")}}
- {{domxref("MediaDevices.getSupportedConstraints()")}}
- {{domxref("MediaTrackSupportedConstraints")}}
- {{domxref("MediaStreamTrack")}}