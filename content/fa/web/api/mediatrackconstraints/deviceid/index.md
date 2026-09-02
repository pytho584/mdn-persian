```
---
title: "MediaTrackConstraints: deviceId property"
short-title: deviceId
slug: Web/API/MediaTrackConstraints/deviceId
page-type: web-api-instance-property
browser-compat: api.MediaStreamTrack.applyConstraints.deviceId_constraint
---

{{APIRef("Media Capture and Streams")}}

ویژگی **`deviceId`** از فرهنگ لغت {{domxref("MediaTrackConstraints")}} یک [`ConstrainDOMString`](/en-US/docs/Web/API/MediaTrackConstraints#constraindomstring) است که محدودیت‌های درخواستی یا اجباری اعمال‌شده بر روی مقدار ویژگی قابل‌محدودیت {{domxref("MediaTrackSettings.deviceId", "deviceId")}} را توصیف می‌کند.

در صورت نیاز، می‌توانید با بررسی مقدار {{domxref("MediaTrackSupportedConstraints.deviceId")}} که توسط فراخوانی {{domxref("MediaDevices.getSupportedConstraints()")}} بازگردانده می‌شود، تعیین کنید که آیا این محدودیت پشتیبانی می‌شود یا خیر. با این حال، معمولاً این کار ضروری نیست زیرا مرورگرها هر محدودیتی را که با آن آشنا نباشند نادیده می‌گیرند.

از آنجایی که {{Glossary("RTP")}} این اطلاعات را شامل نمی‌شود، ردگیری‌های (tracks) مرتبط با یک {{domxref("RTCPeerConnection")}} [WebRTC](/en-US/docs/Web/API/WebRTC_API) هرگز این ویژگی را شامل نخواهند شد.

## مقدار

یک شیء مبتنی بر [`ConstrainDOMString`](/en-US/docs/Web/API/MediaTrackConstraints#constraindomstring) که یک یا چند شناسه دستگاه قابل قبول، ایده‌آل و/یا دقیق (اجباری) را مشخص می‌کند که به عنوان منبع محتوای رسانه‌ای قابل قبول هستند.

شناسه‌های دستگاه برای یک مبدأ (origin) معین منحصربه‌فرد هستند و تضمین می‌شود که در جلسات مرور (browsing sessions) روی همان مبدأ یکسان باشند. با این حال، مقدار `deviceId` توسط منبع محتوای ردگیری (track) تعیین می‌شود و هیچ فرمت خاصی توسط مشخصات اجباری نشده است (اگرچه نوعی GUID توصیه می‌شود). این بدان معناست که یک ردگیری معین تنها یک مقدار برای `deviceId` هنگام فراخوانی {{domxref("MediaStreamTrack.getCapabilities", "getCapabilities()")}} بازمی‌گرداند.

به همین دلیل، هنگام فراخوانی {{domxref("MediaStreamTrack.applyConstraints()")}} استفاده‌ای برای شناسه دستگاه وجود ندارد، زیرا تنها یک مقدار ممکن وجود دارد؛ با این حال، می‌توانید یک `deviceId` را ثبت کنید و از آن برای اطمینان از دریافت منبع یکسان در فراخوانی‌های متعدد به {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}} استفاده کنید.

> [!NOTE]
> استثنایی بر قاعده‌ای که می‌گوید شناسه‌های دستگاه در جلسات مرور یکسان هستند: حالت مرور خصوصی (private browsing) از یک شناسه متفاوت استفاده می‌کند و آن را در هر جلسه مرور تغییر می‌دهد.

## مثال‌ها

برای مثال، [Constraint exerciser](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints#example_constraint_exerciser) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [قابلیت‌ها، محدودیت‌ها و تنظیمات](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints)
- {{domxref("MediaTrackConstraints")}}
- {{domxref("MediaDevices.getSupportedConstraints()")}}
- {{domxref("MediaTrackSupportedConstraints")}}
- {{domxref("MediaStreamTrack")}}
```