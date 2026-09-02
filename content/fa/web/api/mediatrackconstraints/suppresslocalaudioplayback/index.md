---
title: "MediaTrackConstraints: suppressLocalAudioPlayback property"
short-title: suppressLocalAudioPlayback
slug: Web/API/MediaTrackConstraints/suppressLocalAudioPlayback
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.MediaStreamTrack.applyConstraints.suppressLocalAudioPlayback_constraint
---

{{APIRef("Media Capture and Streams")}}{{SeeCompatTable}}

ویژگی **`suppressLocalAudioPlayback`** در دیکشنریِ {{domxref("MediaTrackConstraints")}} یک [`ConstrainBoolean`](/en-US/docs/Web/API/MediaTrackConstraints#constrainboolean) است که محدودیت‌های درخواستی یا اجباریِ اعمال‌شده بر مقدارِ ویژگیِ محدودیت‌پذیری به نام {{domxref("MediaTrackSettings.suppressLocalAudioPlayback","suppressLocalAudioPlayback")}} را توصیف می‌کند. این ویژگی کنترل می‌کند که وقتی یک زبانه ضبط می‌شود، آیا صدای در حال پخش در آن زبانه همچنان از بلندگوهای محلی کاربر پخش خواهد شد یا نه.

در صورت نیاز، می‌توانید با بررسی مقدار {{domxref("MediaTrackSupportedConstraints.suppressLocalAudioPlayback")}} که توسط فراخوانی {{domxref("MediaDevices.getSupportedConstraints()")}} بازگردانده می‌شود، تعیین کنید که آیا این محدودیت پشتیبانی می‌شود یا خیر. با این حال، معمولاً این کار ضروری نیست، زیرا مرورگرها هر محدودیتی را که نشناسند نادیده می‌گیرند.

## مقدار

یک مقدار [`ConstrainBoolean`](/en-US/docs/Web/API/MediaTrackConstraints#constrainboolean).

اگر این مقدار یک `true` یا `false` ساده باشد، عامل کاربر (user agent) در صورت امکان تلاش می‌کند رسانه را با فعال یا غیرفعال بودن پخش صوتی محلی، مطابق آنچه مشخص شده، به دست آورد؛ اما اگر این امکان وجود نداشته باشد، درخواست با شکست مواجه نخواهد شد.

اگر مقدار به‌صورت `ideal` داده شده باشد، مقدار بولیِ آن فیلد نشان‌دهندهٔ یک تنظیم ایدئال برای قابلیت سرکوب پخش صوتی محلی است؛ اگر این تنظیم برآورده نشود، درخواست به خطا منجر می‌شود.

## مثال‌ها

```js
let isLocalAudioSuppressed = displayStream
  .getVideoTracks()[0]
  .getSettings().suppressLocalAudioPlayback;
```

نمونهٔ [Constraint exerciser](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints#example_constraint_exerciser) نحوه استفاده از محدودیت‌های مسیر رسانه را نشان می‌دهد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [Capabilities, constraints, and settings](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaTrackConstraints")}}
- {{domxref("MediaDevices.getSupportedConstraints()")}}
- {{domxref("MediaTrackSupportedConstraints")}}
- {{domxref("MediaStreamTrack")}}