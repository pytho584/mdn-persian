---
title: "MediaTrackConstraints: groupId property"
short-title: groupId
slug: Web/API/MediaTrackConstraints/groupId
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.groupId_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`groupId`** در دیکشنری {{domxref("MediaTrackConstraints")}} یک [`ConstrainDOMString`](/en-US/docs/Web/API/MediaTrackConstraints#constraindomstring) است که محدودیت‌های درخواستی یا اجباری اعمال‌شده بر مقدار ویژگی قابل‌محدودیت {{domxref("MediaTrackSettings.groupId", "groupId")}} را توصیف می‌کند.

در صورت نیاز، می‌توانید با بررسی مقدار {{domxref("MediaTrackSupportedConstraints.groupId")}} که توسط فراخوانی {{domxref("MediaDevices.getSupportedConstraints()")}} بازگردانده می‌شود، تعیین کنید که آیا این محدودیت پشتیبانی می‌شود یا خیر. با این حال، معمولاً این کار ضروری نیست، زیرا مرورگرها هر محدودیتی را که با آن آشنا نباشند نادیده می‌گیرند.

## مقدار

یک شیء مبتنی بر [`ConstrainDOMString`](/en-US/docs/Web/API/MediaTrackConstraints#constraindomstring) که یک یا چند گروه ID قابل‌قبول، ایده‌آل و/یا دقیق (اجباری) را مشخص می‌کند که به عنوان منبع محتوای رسانه قابل‌قبول هستند.

شناسه‌های گروه برای یک مبدأ (origin) مشخص، در طول یک جلسه مرور (browsing session) یکتا هستند و توسط همه منابع رسانه‌ای که از همان دستگاه فیزیکی می‌آیند به اشتراک گذاشته می‌شوند. برای مثال، میکروفون و بلندگوی یک هدست یکسان، شناسه گروه مشترکی خواهند داشت. این امر امکان استفاده از شناسه گروه را فراهم می‌کند تا مطمئن شوید دستگاه‌های صوتی و ورودی روی یک هدست قرار دارند؛ مثلاً با دریافت شناسه گروه دستگاه ورودی و مشخص کردن آن هنگام درخواست دستگاه خروجی.

با این حال، مقدار `groupId` توسط منبع محتوای تِرَک تعیین می‌شود و هیچ قالب خاصی توسط مشخصات الزامی نشده است (اگرچه نوعی GUID توصیه می‌شود). این بدان معناست که یک تِرَک مشخص، تنها یک مقدار برای `groupId` هنگام فراخوانی {{domxref("MediaStreamTrack.getCapabilities", "getCapabilities()")}} بازمی‌گرداند، و به خاطر داشته باشید که این مقدار در هر جلسه مرور تغییر خواهد کرد.

به همین دلیل، هنگام فراخوانی {{domxref("MediaStreamTrack.applyConstraints()")}} استفاده‌ای برای شناسه گروه وجود ندارد، زیرا تنها یک مقدار ممکن وجود دارد، و نمی‌توانید از آن برای اطمینان از استفاده از همان گروه در چندین جلسه مرور هنگام فراخوانی `getUserMedia()` استفاده کنید.

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