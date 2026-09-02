---
title: "MediaTrackSettings: deviceId property"
short-title: deviceId
slug: Web/API/MediaTrackSettings/deviceId
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.deviceId_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`deviceId`** در فرهنگ لغت {{domxref("MediaTrackSettings")}} یک رشته است که به‌طور یکتا منبع مربوط به {{domxref("MediaStreamTrack")}} را برای مبدأ (origin) مربوط به نشست مرورگر شناسایی می‌کند. این ویژگی به شما امکان می‌دهد تعیین کنید چه مقداری برای برآوردن قیدهای (constraints) مشخص‌شده‌تان برای این ویژگی انتخاب شده است، همان‌طور که در ویژگی {{domxref("MediaTrackConstraints.deviceId")}} که هنگام فراخوانی {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}} ارائه کرده‌اید، توضیح داده شده است.

در صورت نیاز، می‌توانید با بررسی مقدار {{domxref("MediaTrackSupportedConstraints.deviceId")}} که از فراخوانی {{domxref("MediaDevices.getSupportedConstraints()")}} بازگردانده می‌شود، تعیین کنید که آیا این قید پشتیبانی می‌شود یا خیر. با این حال، معمولاً این کار ضروری نیست، زیرا مرورگرها هر قیدی را که با آن آشنا نباشند نادیده می‌گیرند.

از آنجا که {{Glossary("RTP")}} این اطلاعات را شامل نمی‌شود، مسیرهای (tracks) مرتبط با یک {{domxref("RTCPeerConnection")}} در [WebRTC](/en-US/docs/Web/API/WebRTC_API) هرگز این ویژگی را شامل نخواهند شد.

## مقدار

یک رشته که مقدار آن یک شناسه یکتای مبدأ برای منبع مسیر است. این شناسه در چندین نشست مرورگر برای همان مبدأ معتبر است و تضمین می‌شود که برای همه مبدأهای دیگر متفاوت باشد، بنابراین می‌توانید با خیال راحت از آن برای درخواست استفاده از همان منبع در چندین نشست استفاده کنید، برای مثال.

مقدار واقعی رشته، با این حال، توسط منبع مسیر تعیین می‌شود و هیچ تضمینی برای شکل آن وجود ندارد، اگرچه مشخصات (specification) توصیه می‌کند که یک GUID باشد.

از آنجا که یک جفت‌سازی یک‌به‌یک بین شناسه و هر منبع وجود دارد، همه مسیرهای با منبع یکسان، شناسه یکسانی را برای هر مبدأ معین به اشتراک می‌گذارند، بنابراین {{domxref("MediaStreamTrack.getCapabilities()")}} همیشه دقیقاً یک مقدار برای `deviceId` بازمی‌گرداند. این امر شناسه دستگاه را برای هر تغییری در قیدها هنگام فراخوانی {{domxref("MediaStreamTrack.applyConstraints()")}} بی‌فایده می‌سازد.

> [!NOTE]
> یک استثنا از قاعده اینکه شناسه‌های دستگاه در نشست‌های مرورگر یکسان هستند: حالت مرور خصوصی (private browsing) از شناسه متفاوتی استفاده می‌کند و آن را در هر نشست مرور تغییر می‌دهد.

## مثال‌ها

مثال [Constraint exerciser](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints#example_constraint_exerciser) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [رابط برنامه‌نویسی Media Capture and Streams](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [قابلیت‌ها، قیدها و تنظیمات](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaTrackSettings.groupId")}}
- {{domxref("MediaTrackConstraints.deviceId")}}
- {{domxref("MediaTrackSettings")}}