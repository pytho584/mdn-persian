---
title: "MediaTrackConstraints: restrictOwnAudio property"
short-title: restrictOwnAudio
slug: Web/API/MediaTrackConstraints/restrictOwnAudio
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.MediaStreamTrack.applyConstraints.restrictOwnAudio_constraint
---

{{APIRef("Media Capture and Streams")}}{{SeeCompatTable}}

خصوصیت **`restrictOwnAudio`** در دیکشنری {{domxref("MediaTrackConstraints")}} یک [`ConstrainBoolean`](/en-US/docs/Web/API/MediaTrackConstraints#constrainboolean) است که محدودیت‌های درخواستی یا اجباری اعمال‌شده بر مقدار خصوصیت قابل‌قید {{domxref("MediaTrackSettings.restrictOwnAudio","restrictOwnAudio")}} را مشخص می‌کند.

این خصوصیت کنترل می‌کند که آیا صدای سیستم منشأگرفته از تب در حال ضبط، از ضبط صفحه فیلتر شود یا خیر، که در برخی موارد امکان ضبط تمیزتر صفحه را فراهم می‌کند. برای مثال، اگر خود صفحه وب در حال ضبط، صوت یا ویدیوی تعبیه‌شده‌ای پخش کند، آن صدا در ضبط گنجانده می‌شود. از آنجا که این امر می‌تواند به اکوی نامطلوب منجر شود یا با منابع صوتی موردنظر از تب‌ها یا برنامه‌های دیگر تداخل ایجاد کند، حذف آن از ضبط مطلوب است.

در صورت نیاز، می‌توانید با بررسی مقدار {{domxref("MediaTrackSupportedConstraints.restrictOwnAudio")}} که توسط {{domxref("MediaDevices.getSupportedConstraints()")}} بازگردانده می‌شود، تعیین کنید که آیا این محدودیت پشتیبانی می‌شود یا خیر. با این حال، این کار به ندرت ضروری است، زیرا مرورگرها معمولاً هر محدودیتی را که نمی‌شناسند نادیده می‌گیرند.

## مقدار

یک مقدار [`ConstrainBoolean`](/en-US/docs/Web/API/MediaTrackConstraints#constrainboolean).

اگر مقدار `true` باشد، عامل کاربر تلاش می‌کند هر صدای منشأگرفته از تب‌ای که {{domxref("MediaDevices.getDisplayMedia()")}} را برای شروع ضبط صفحه فراخوانی کرده است حذف کند. اگر حذف صدا از طریق پردازش شکست بخورد، عامل کاربر ممکن است تمام صدای منشأگرفته از تب در حال ضبط را حذف کند.

> [!NOTE]
> اگر سطح نمایش ضبط‌شده شامل صدای سیستم نباشد، این تنظیم تأثیری نخواهد داشت.

اگر مقدار به صورت `exact` داده شود، مقدار بولی آن فیلد یک الزام دقیق برای ویژگی `restrictOwnAudio` را نشان می‌دهد؛ اگر عامل کاربر نتواند این الزام را برآورده کند، درخواست منجر به خطا می‌شود.

اگر مقدار `false` باشد، عامل کاربر تلاشی برای محدود کردن صدای سیستم منشأگرفته از تب در حال ضبط نخواهد کرد.

## مثال‌ها

```js
let isCapturingTabSystemAudioRestricted = displayStream
  .getAudioTracks()[0]
  .getSettings().restrictOwnAudio;
```

مثال [Constraint exerciser](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints#example_constraint_exerciser) نحوه استفاده از محدودیت‌های مسیر رسانه را نشان می‌دهد.

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