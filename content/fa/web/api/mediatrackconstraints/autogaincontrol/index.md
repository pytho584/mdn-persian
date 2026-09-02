---
title: "MediaTrackConstraints: autoGainControl property"
---

---
title: "MediaTrackConstraints: autoGainControl property"
short-title: autoGainControl
slug: Web/API/MediaTrackConstraints/autoGainControl
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.autoGainControl_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`autoGainControl`** در دیکشنری {{domxref("MediaTrackConstraints")}} یک [`ConstrainBoolean`](/en-US/docs/Web/API/MediaTrackConstraints#constrainboolean) است که محدودیت‌های درخواستی یا اجباری اعمال‌شده بر مقدار ویژگی قابل‌محدودسازیِ {{domxref("MediaTrackSettings.autoGainControl", "autoGainControl")}} را توصیف می‌کند.

در صورت نیاز، می‌توانید با بررسی مقدار {{domxref("MediaTrackSupportedConstraints.autoGainControl")}} که توسط یک فراخوانی به {{domxref("MediaDevices.getSupportedConstraints()")}} بازگردانده می‌شود، مشخص کنید که آیا این محدودیت پشتیبانی می‌شود یا خیر. با این حال، معمولاً این کار ضروری نیست؛ زیرا مرورگرها هر محدودیتی را که نمی‌شناسند نادیده می‌گیرند.

کنترل خودکار بهره (Automatic Gain Control) معمولاً قابلیتی است که میکروفون‌ها ارائه می‌دهند، اگرچه ممکن است منابع ورودی دیگری نیز آن را فراهم کنند.

## مقدار

اگر این مقدار یک `true` یا `false` ساده باشد، عامل کاربر (user agent) تلاش می‌کند تا رسانه را با کنترل خودکار بهره فعال یا غیرفعال، همان‌طور که مشخص شده، به دست آورد؛ اما اگر چنین کاری ممکن نباشد، درخواست شکست نمی‌خورد. اگر به‌جای آن مقدار به‌صورت یک شیء با فیلد `exact` داده شود، مقدار بولیِ آن فیلد، تنظیمِ اجباریِ قابلیت کنترل خودکار بهره را مشخص می‌کند؛ اگر این تنظیم قابل برآورده‌شدن نباشد، درخواست منجر به خطا می‌شود.

## مثال‌ها

نمونهٔ [Constraint exerciser](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints#example_constraint_exerciser) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [Capabilities, constraints, and settings](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaTrackConstraints")}}
- {{domxref("MediaDevices.getSupportedConstraints()")}}
- {{domxref("MediaTrackSupportedConstraints")}}
- {{domxref("MediaStreamTrack")}}