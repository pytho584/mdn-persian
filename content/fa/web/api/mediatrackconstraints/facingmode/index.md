---
title: "MediaTrackConstraints: facingMode property"
short-title: facingMode
slug: Web/API/MediaTrackConstraints/facingMode
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.facingMode_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`facingMode`** در شیء (دیکشنری) {{domxref("MediaTrackConstraints")}} یک [`ConstrainDOMString`](/en-US/docs/Web/API/MediaTrackConstraints#constraindomstring) است که محدودیت‌های درخواستی یا اجباری اعمال‌شده بر روی مقدار ویژگی قابل‌قید {{domxref("MediaTrackSettings.facingMode", "facingMode")}} را توصیف می‌کند.

در صورت نیاز، می‌توانید با بررسی مقدار {{domxref("MediaTrackSupportedConstraints.facingMode")}} که توسط فراخوانی {{domxref("MediaDevices.getSupportedConstraints()")}} بازگردانده می‌شود، تعیین کنید که آیا این محدودیت پشتیبانی می‌شود یا خیر. با این حال، معمولاً این کار ضروری نیست، زیرا مرورگرها هر محدودیتی را که با آن آشنا نباشند نادیده می‌گیرند.

از آنجا که {{Glossary("RTP")}} این اطلاعات را شامل نمی‌شود، مسیرهای (tracks) مرتبط با یک {{domxref("RTCPeerConnection")}} متعلق به [WebRTC](/en-US/docs/Web/API/WebRTC_API) هرگز این ویژگی را شامل نخواهند شد.

## مقدار

یک شیء مبتنی بر [`ConstrainDOMString`](/en-US/docs/Web/API/MediaTrackConstraints#constraindomstring) که یک یا چند حالت روبه‌رو (facing mode) قابل‌قبول، ایده‌آل و/یا دقیق (اجباری) را برای یک مسیر ویدیویی مشخص می‌کند.

یک مقدار `exact` در این مورد نشان می‌دهد که حالت روبه‌روی مشخص‌شده الزاماً مورد نیاز است؛ برای مثال:

```js
const constraints = {
  facingMode: { exact: "user" },
};
```

این بدان معناست که تنها یک دوربین روبه‌روی کاربر قابل‌قبول است؛ اگر دوربین روبه‌روی کاربری وجود نداشته باشد یا کاربر اجازه استفاده از آن دوربین را ندهد، درخواست رسانه ناموفق خواهد بود.

مقدارهای مجاز زیر برای حالت روبه‌رو تعریف شده‌اند. این‌ها ممکن است نشان‌دهنده دوربین‌های جداگانه باشند، یا ممکن است جهت‌هایی باشند که یک دوربین قابل تنظیم می‌تواند به سمت آن‌ها نشانه رود.

- `"user"`
  - : منبع ویدیو به سمت کاربر است؛ این شامل، برای مثال، دوربین جلوی یک گوشی هوشمند می‌شود.
- `"environment"`
  - : منبع ویدیو رو به دور از کاربر است و بنابراین محیط اطراف او را نشان می‌دهد. این دوربین پشت گوشی هوشمند است.
- `"left"`
  - : منبع ویدیو به سمت کاربر است اما به سمت چپ او؛ مانند دوربینی که به سمت کاربر نشانه رفته اما از روی شانه چپ او.
- `"right"`
  - : منبع ویدیو به سمت کاربر است اما به سمت راست او؛ مانند دوربینی که به سمت کاربر نشانه رفته اما از روی شانه راست او.

## مثال‌ها

مثال [Constraint exerciser](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints#example_constraint_exerciser) را ببینید.

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