---
title: "MediaStreamTrack"
slug: Web/API/MediaStreamTrack
page-type: web-api-interface
browser-compat: api.MediaStreamTrack
---

{{APIRef("Media Capture and Streams")}}

رابط **`MediaStreamTrack`** از {{domxref("API ضبط و جریان‌های رسانه", "", "", "nocode")}} یک تک‌رسانه (track) منفرد را درون یک جریان (stream) نشان می‌دهد؛ معمولاً این‌ها تک‌های صوتی یا تصویری هستند، اما انواع دیگر تک‌ها نیز ممکن است وجود داشته باشند.

برخی از عامل‌های کاربر (user agents) این رابط را زیرکلاس‌سازی می‌کنند تا اطلاعات یا قابلیت‌های دقیق‌تری ارائه دهند، مانند {{domxref("CanvasCaptureMediaStreamTrack")}}.

{{InheritanceDiagram}}

## ویژگی‌های نمونه (Instance properties)

علاوه بر ویژگی‌های فهرست‌شده در زیر، `MediaStreamTrack` دارای ویژگی‌های قابل محدودیت (constrainable properties) است که می‌توان با استفاده از {{domxref("MediaStreamTrack.applyConstraints", "applyConstraints()")}} تنظیم کرد و با استفاده از {{domxref("MediaStreamTrack.getConstraints", "getConstraints()")}} و {{domxref("MediaStreamTrack.getSettings", "getSettings()")}} به آن‌ها دسترسی داشت. برای یادگیری نحوه کار صحیح با ویژگی‌های قابل محدودیت، به [Capabilities, constraints, and settings](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints) مراجعه کنید. عدم انجام صحیح این کار باعث می‌شود کد شما ناپایدار باشد.

- {{domxref("MediaStreamTrack.contentHint")}}
  - : یک رشته که ممکن است توسط برنامه وب برای ارائه یک راهنمایی در مورد نوع محتوای تک‌رسانه استفاده شود تا نحوه برخورد مصرف‌کنندگان API با آن را هدایت کند. مقادیر مجاز به مقدار ویژگی {{domxref("MediaStreamTrack.kind")}} بستگی دارند.
- {{domxref("MediaStreamTrack.enabled")}}
  - : یک مقدار بولی که اگر `true` باشد، تک‌رسانه فعال است و اجازه نمایش جریان منبع رسانه را دارد؛ یا `false` اگر غیرفعال باشد و جریان منبع رسانه را نمایش ندهد بلکه سکوت و سیاهی ارائه دهد. اگر تک‌رسانه قطع شده باشد، این مقدار قابل تغییر است اما دیگر تأثیری ندارد.

    > [!NOTE]
    > شما می‌توانید قابلیت استاندارد «سکوت» (mute) را با تنظیم `enabled` به `false` پیاده‌سازی کنید. ویژگی `muted` به وضعیتی اشاره دارد که به دلیل یک مشکل فنی، رسانه‌ای وجود ندارد.

- {{domxref("MediaStreamTrack.id")}} {{ReadOnlyInline}}
  - : یک رشته حاوی شناسه یکتا (GUID) برای تک‌رسانه برمی‌گرداند؛ این شناسه توسط مرورگر تولید می‌شود.
- {{domxref("MediaStreamTrack.kind")}} {{ReadOnlyInline}}
  - : یک رشته برمی‌گرداند که اگر تک‌رسانه صوتی باشد `"audio"` و اگر تصویری باشد `"video"` تنظیم می‌شود. اگر تک‌رسانه از منبع خود جدا شود، این مقدار تغییر نمی‌کند.
- {{domxref("MediaStreamTrack.label")}} {{ReadOnlyInline}}
  - : یک رشته حاوی برچسبی که توسط عامل کاربر تعیین شده و منبع تک‌رسانه را شناسایی می‌کند، مانند `"internal microphone"` برمی‌گرداند. این رشته ممکن است خالی بماند و تا زمانی که هیچ منبعی متصل نشده باشد خالی است. هنگامی که تک‌رسانه از منبع خود جدا می‌شود، برچسب تغییر نمی‌کند.
- {{domxref("MediaStreamTrack.muted")}} {{ReadOnlyInline}}
  - : یک مقدار بولی برمی‌گرداند که نشان می‌دهد آیا تک‌رسانه به دلیل یک مشکل فنی قادر به ارائه داده‌های رسانه‌ای نیست یا خیر.

    > [!NOTE]
    > شما می‌توانید قابلیت استاندارد «سکوت» (mute) را با تنظیم `enabled` به `false` پیاده‌سازی کنید و با بازگرداندن آن به `true`، رسانه را از حالت سکوت خارج کنید.

- {{domxref("MediaStreamTrack.readyState")}} {{ReadOnlyInline}}
  - : یک رشته شمارشی (enumerated string) برمی‌گرداند که وضعیت تک‌رسانه را نشان می‌دهد. این مقدار یکی از موارد زیر خواهد بود:
    - `"live"` که نشان می‌دهد یک ورودی متصل است و به بهترین نحو در تلاش برای ارائه داده‌های بلادرنگ است. در این حالت، خروجی داده را می‌توان با استفاده از ویژگی {{domxref("MediaStreamTrack.enabled", "enabled")}} روشن یا خاموش کرد.
    - `"ended"` که نشان می‌دهد ورودی دیگر داده‌ای ارائه نمی‌دهد و هرگز داده جدیدی ارائه نخواهد داد.

## روش‌های نمونه (Instance methods)

- {{domxref("MediaStreamTrack.applyConstraints()")}}
  - : به برنامه اجازه می‌دهد مقادیر ایده‌آل و/یا محدوده‌های مقادیر قابل قبول را برای هر تعداد از ویژگی‌های قابل محدودیت موجود `MediaStreamTrack` مشخص کند.
- {{domxref("MediaStreamTrack.clone()")}}
  - : یک کپی از `MediaStreamTrack` برمی‌گرداند.
- {{domxref("MediaStreamTrack.getCapabilities()")}}
  - : یک شیء برمی‌گرداند که مقادیر پذیرفته‌شده یا محدوده مقادیر را برای هر ویژگی قابل محدودیت `MediaStreamTrack` مرتبط به تفصیل شرح می‌دهد.
- {{domxref("MediaStreamTrack.getConstraints()")}}
  - : یک شیء {{domxref('MediaTrackConstraints')}} حاوی محدودیت‌های فعلی تنظیم‌شده برای تک‌رسانه برمی‌گرداند؛ مقدار بازگشتی با آخرین محدودیت‌های تنظیم‌شده با استفاده از {{domxref("MediaStreamTrack.applyConstraints", "applyConstraints()")}} مطابقت دارد.
- {{domxref("MediaStreamTrack.getSettings()")}}
  - : یک شیء {{domxref("MediaTrackSettings")}} حاوی مقادیر فعلی هر یک از ویژگی‌های قابل محدودیت `MediaStreamTrack` برمی‌گرداند.
- {{domxref("MediaStreamTrack.stop()")}}
  - : پخش منبع مرتبط با تک‌رسانه را متوقف می‌کند، هم منبع و هم تک‌رسانه از یکدیگر جدا می‌شوند. وضعیت تک‌رسانه به `ended` تنظیم می‌شود.

## رویدادها (Events)

به این رویدادها با استفاده از {{domxref("EventTarget.addEventListener", "addEventListener()")}} یا با اختصاص یک شنونده رویداد به ویژگی `oneventname` این رابط گوش دهید:

- {{domxref("MediaStreamTrack/ended_event", "ended")}}
  - : زمانی ارسال می‌شود که پخش تک‌رسانه به پایان می‌رسد (زمانی که مقدار {{domxref("MediaStreamTrack.readyState", "readyState")}} به `ended` تغییر می‌کند)، به جز زمانی که تک‌رسانه با فراخوانی {{domxref("MediaStreamTrack.stop")}} پایان یافته باشد.
- {{domxref("MediaStreamTrack/mute_event", "mute")}}
  - : به `MediaStreamTrack` ارسال می‌شود زمانی که مقدار ویژگی {{domxref("MediaStreamTrack.muted", "muted")}} به `true` تغییر می‌کند، که نشان می‌دهد تک‌رسانه به طور موقت قادر به ارائه داده نیست (مانند زمانی که شبکه دچار اختلال سرویس است).
- {{domxref("MediaStreamTrack/unmute_event", "unmute")}}
  - : زمانی به تک‌رسانه ارسال می‌شود که داده دوباره در دسترس قرار می‌گیرد و وضعیت `muted` پایان می‌یابد.

## مشخصات (Specifications)

{{Specifications}}

## سازگاری مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید (See also)

- [API ضبط و جریان‌های رسانه (Media Capture and Streams API)](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- {{domxref("MediaStream")}}