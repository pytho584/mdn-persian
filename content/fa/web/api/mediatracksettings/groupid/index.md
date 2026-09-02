---
title: "MediaTrackSettings: groupId property"
short-title: groupId
slug: Web/API/MediaTrackSettings/groupId
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.groupId_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`groupId`** در فرهنگ لغت {{domxref("MediaTrackSettings")}} یک رشتهٔ منحصربه‌فرد در طول جلسهٔ مرور (browsing session) است که گروه دستگاه‌هایی را شناسایی می‌کند که منبع {{domxref("MediaStreamTrack")}} را شامل می‌شود. این ویژگی به شما امکان می‌دهد تعیین کنید چه مقداری برای پیروی از محدودیت‌های مشخص‌شده‌تان برای این ویژگی انتخاب شده است، همان‌طور که در ویژگی {{domxref("MediaTrackConstraints.groupId")}} که هنگام فراخوانی {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}} ارائه کرده‌اید، توضیح داده شده است.

در صورت نیاز، می‌توانید با بررسی مقدار {{domxref("MediaTrackSupportedConstraints.groupId")}} که از طریق فراخوانی {{domxref("MediaDevices.getSupportedConstraints()")}} بازگردانده می‌شود، تشخیص دهید که آیا این محدودیت پشتیبانی می‌شود یا خیر. با این حال، معمولاً این کار ضروری نیست، زیرا مرورگرها هر محدودیتی را که با آن آشنایی ندارند نادیده می‌گیرند.

از آنجا که {{Glossary("RTP")}} این اطلاعات را شامل نمی‌شود، مسیرهای (tracks) مرتبط با یک {{domxref("RTCPeerConnection")}} از [WebRTC](/en-US/docs/Web/API/WebRTC_API) هرگز این ویژگی را شامل نخواهند شد.

## مقدار

یک رشته که مقدار آن یک شناسهٔ منحصربه‌فرد در طول جلسهٔ مرور برای گروهی از دستگاه‌هاست که منبع محتوای مسیر را شامل می‌شود. دو دستگاه اگر به یک دستگاه فیزیکی سخت‌افزاری تعلق داشته باشند، شناسهٔ گروه یکسانی دارند. برای مثال، یک هدست دارای دو دستگاه است: یک میکروفون که می‌تواند به عنوان منبع مسیرهای صوتی عمل کند و یک بلندگو که می‌تواند به عنوان خروجی صدا عمل کند.

شناسهٔ گروه در چندین جلسهٔ مرور قابل استفاده نیست. با این حال، می‌توان از آن برای اطمینان از اینکه ورودی و خروجی صوتی هر دو روی همان هدست انجام می‌شوند استفاده کرد، یا برای مثال، برای اطمینان از اینکه دوربین داخلی و میکروفون یک گوشی برای کنفرانس ویدیویی استفاده می‌شوند.

مقدار واقعی رشته، با این حال، توسط منبع مسیر تعیین می‌شود و هیچ تضمینی برای شکل آن وجود ندارد، اگرچه مشخصات (specification) توصیه می‌کند که یک GUID باشد.

از آنجا که این ویژگی در طول جلسات مرور پایدار نیست، کاربرد آن هنگام فراخوانی {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}} معمولاً محدود به اطمینان از این است که وظایف انجام‌شده در طول همان جلسهٔ مرور از دستگاه‌های یک گروه استفاده می‌کنند (یا اینکه از دستگاه‌های همان گروه استفاده نمی‌کنند). هیچ موقعیتی وجود ندارد که `groupId` هنگام فراخوانی `applyConstraints()` مفید باشد، زیرا مقدار آن قابل تغییر نیست.

## مثال‌ها

مثال [Constraint exerciser](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints#example_constraint_exerciser) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [API ضبط و جریان رسانه](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [قابلیت‌ها، محدودیت‌ها و تنظیمات](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaTrackSettings.deviceId")}}
- {{domxref("MediaTrackConstraints.groupId")}}
- {{domxref("MediaTrackSettings")}}