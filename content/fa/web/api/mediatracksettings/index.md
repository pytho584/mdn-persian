---
title: MediaTrackSettings
slug: Web/API/MediaTrackSettings
page-type: web-api-interface
spec-urls:
  - https://w3c.github.io/mediacapture-main/#media-track-settings
  - https://w3c.github.io/mediacapture-screen-share/#extensions-to-mediatracksettings
---

{{APIRef("Media Capture and Streams")}}

دیکشنری **`MediaTrackSettings`** برای بازگرداندن مقادیر فعلی تنظیم‌شده برای هر یک از تنظیمات یک {{domxref("MediaStreamTrack")}} استفاده می‌شود. این مقادیر تا حد امکان به هر محدودیتی که قبلاً با استفاده از یک شیء {{domxref("MediaTrackConstraints")}} توصیف و با استفاده از {{domxref("MediaStreamTrack.applyConstraints", "applyConstraints()")}} تنظیم شده‌اند، پایبند خواهند بود و برای هر ویژگی که محدودیت‌های آن تغییر نکرده‌اند یا محدودیت‌های سفارشی آن‌ها قابل تطبیق نبوده‌اند، به محدودیت‌های پیش‌فرض پایبند خواهند بود.

برای آشنایی بیشتر با نحوه کار محدودیت‌ها و تنظیمات، به [قابلیت‌ها، محدودیت‌ها و تنظیمات](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints) مراجعه کنید.

## ویژگی‌های نمونه

برخی یا همه موارد زیر در این شیء گنجانده خواهند شد، یا به این دلیل که مرورگر از آن‌ها پشتیبانی نمی‌کند یا به دلیل اینکه در زمینه مورد نظر در دسترس نیستند. برای مثال، چون {{Glossary("RTP")}} برخی از این مقادیر را در طول مذاکره یک اتصال WebRTC فراهم نمی‌کند، یک ترک مرتبط با یک {{domxref("RTCPeerConnection")}} شامل مقادیر خاصی مانند {{domxref("MediaTrackSettings.facingMode", "facingMode")}} یا {{domxref("MediaTrackSettings.groupId", "groupId")}} نخواهد بود.

### ویژگی‌های نمونه برای همه ترک‌های رسانه‌ای

- {{domxref("MediaTrackSettings.deviceId", "deviceId")}}
  - : یک رشته که مقدار فعلی ویژگی {{domxref("MediaTrackConstraints.deviceId", "deviceId")}} را نشان می‌دهد. شناسه دستگاه یک رشته یکتا وابسته به origin است که منبع ترک را مشخص می‌کند؛ این مقدار معمولاً یک [GUID](https://en.wikipedia.org/wiki/Universally_unique_identifier) است. این مقدار به منبع داده ترک اختصاص دارد و برای تنظیم محدودیت‌ها قابل استفاده نیست؛ با این حال، می‌توان هنگام فراخوانی {{domxref("MediaDevices.getUserMedia()")}} از آن برای انتخاب اولیه رسانه استفاده کرد.
- {{domxref("MediaTrackSettings.groupId", "groupId")}}
  - : یک رشته که مقدار فعلی ویژگی {{domxref("MediaTrackConstraints.groupId", "groupId")}} را نشان می‌دهد. شناسه گروه یک رشته یکتای مخصوص نشست مرورگر (browsing session) است که گروه منبع ترک را مشخص می‌کند. دو دستگاه (که با {{domxref("MediaTrackSettings.deviceId", "deviceId")}} شناسایی می‌شوند) اگر از یک دستگاه فیزیکی باشند، بخشی از یک گروه در نظر گرفته می‌شوند. برای مثال، دستگاه‌های ورودی و خروجی صوتی برای بلندگو و میکروفون تعبیه‌شده در یک تلفن، شناسه گروه یکسانی دارند، زیرا بخشی از یک دستگاه فیزیکی واحد هستند. با این حال، میکروفون یک هدست شناسه متفاوتی خواهد داشت. این مقدار به منبع داده ترک اختصاص دارد و برای تنظیم محدودیت‌ها قابل استفاده نیست؛ با این حال، می‌توان هنگام فراخوانی {{domxref("MediaDevices.getUserMedia()")}} از آن برای انتخاب اولیه رسانه استفاده کرد.

### ویژگی‌های نمونه ترک‌های صوتی

- {{domxref("MediaTrackSettings.autoGainControl", "autoGainControl")}}
  - : یک مقدار بولین که مقدار فعلی ویژگی {{domxref("MediaTrackConstraints.autoGainControl", "autoGainControl")}} را نشان می‌دهد؛ اگر کنترل خودکار بهره (automatic gain control) فعال باشد `true` است و در غیر این صورت `false`.
- {{domxref("MediaTrackSettings.channelCount", "channelCount")}}
  - : یک مقدار صحیح بلند (long integer) که مقدار فعلی ویژگی {{domxref("MediaTrackConstraints.channelCount", "channelCount")}} را نشان می‌دهد و تعداد کانال‌های صوتی موجود در ترک را مشخص می‌کند (بنابراین نشان می‌دهد در هر فریم صوتی چند نمونه صوتی وجود دارد). این مقدار برای مونو ۱، برای استریو ۲ و به همین ترتیب است.
- {{domxref("MediaTrackSettings.echoCancellation", "echoCancellation")}}
  - : یک مقدار بولین که مقدار فعلی ویژگی {{domxref("MediaTrackConstraints.echoCancellation", "echoCancellation")}} را نشان می‌دهد؛ اگر حذف پژواک (echo cancellation) فعال باشد `true` و در غیر این صورت `false` را مشخص می‌کند.
- {{domxref("MediaTrackSettings.latency", "latency")}}
  - : یک مقدار ممیز شناور با دقت دوبرابر (double-precision floating point) که مقدار فعلی ویژگی {{domxref("MediaTrackConstraints.latency", "latency")}} را نشان می‌دهد و تأخیر صوتی را بر حسب ثانیه مشخص می‌کند. تأخیر (latency) مدت زمانی است که بین شروع پردازش صدا و در دسترس قرار گرفتن داده‌ها برای مرحله بعدی در فرایند استفاده از صدا سپری می‌شود. این مقدار یک مقدار هدف است؛ تأخیر واقعی ممکن است بنا به دلایل مختلف تا حدی متفاوت باشد.
- {{domxref("MediaTrackSettings.noiseSuppression", "noiseSuppression")}}
  - : یک مقدار بولین که مقدار فعلی ویژگی {{domxref("MediaTrackConstraints.noiseSuppression", "noiseSuppression")}} را نشان می‌دهد: اگر حذف نویز (noise suppression) فعال باشد `true` و در غیر این صورت `false` است.
- {{domxref("MediaTrackSettings.restrictOwnAudio", "restrictOwnAudio")}}
  - : یک مقدار بولین که مقدار فعلی ویژگی {{domxref("MediaTrackConstraints.restrictOwnAudio", "restrictOwnAudio")}} را نشان می‌دهد: اگر مرورگر تلاش کند صدای سیستمی را که از تب در حال ضبط در طول ضبط صفحه منشأ می‌گیرد فیلتر کند، `true` و در غیر این صورت `false` است.
- {{domxref("MediaTrackSettings.sampleRate", "sampleRate")}}
  - : یک مقدار صحیح بلند که مقدار فعلی ویژگی {{domxref("MediaTrackConstraints.sampleRate", "sampleRate")}} را نشان می‌دهد و نرخ نمونه‌برداری داده‌های صوتی را بر حسب نمونه بر ثانیه مشخص می‌کند. برای مثال، صدای استاندارد با کیفیت CD نرخ نمونه‌برداری ۴۱٬۰۰۰ نمونه بر ثانیه دارد.
- {{domxref("MediaTrackSettings.sampleSize", "sampleSize")}}
  - : یک مقدار صحیح بلند که مقدار فعلی ویژگی {{domxref("MediaTrackConstraints.sampleSize", "sampleSize")}} را نشان می‌دهد و اندازه خطی هر نمونه صوتی را بر حسب بیت مشخص می‌کند. برای مثال، صدای با کیفیت CD شانزده‌بیتی است، بنابراین در آن حالت این مقدار ۱۶ خواهد بود.
- {{domxref("MediaTrackSettings.suppressLocalAudioPlayback", "suppressLocalAudioPlayback")}}
  - : کنترل می‌کند که آیا صدای در حال پخش در یک تب، هنگام ضبط آن تب، همچنان از بلندگوهای محلی کاربر پخش خواهد شد یا خیر.
- {{domxref("MediaTrackSettings.volume", "volume")}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : یک مقدار ممیز شناور با دقت دوبرابر که مقدار فعلی ویژگی {{domxref("MediaTrackConstraints.volume", "volume")}} را نشان می‌دهد و سطح بلندی صدای ترک را مشخص می‌کند. این مقدار بین 0.0 (سکوت) تا 1.0 (حداکثر بلندی صدای پشتیبانی‌شده) خواهد بود.

### ویژگی‌های نمونه ترک‌های ویدئویی

- {{domxref("MediaTrackSettings.aspectRatio", "aspectRatio")}}
  - : یک مقدار ممیز شناور با دقت دوبرابر که مقدار فعلی ویژگی {{domxref("MediaTrackConstraints.aspectRatio", "aspectRatio")}} را نشان می‌دهد و دقیقاً تا ۱۰ رقم اعشار مشخص شده است. این مقدار عرض تصویر بر حسب پیکسل تقسیم بر ارتفاع آن بر حسب پیکسل است. مقادیر رایج عبارت‌اند از: 1.3333333333 (برای نسبت تصویر «استاندارد» تلویزیون کلاسیک 4:3، که در رایانه‌های لوحی مانند iPad اپل نیز استفاده می‌شود)، 1.7777777778 (برای نسبت تصویر عریض با کیفیت بالا 16:9) و 1.6 (برای نسبت تصویر 16:10 که در میان رایانه‌ها و رایانه‌های لوحی عریض رایج است).
- {{domxref("MediaTrackSettings.facingMode", "facingMode")}}
  - : یک رشته که مقدار فعلی ویژگی {{domxref("MediaTrackConstraints.facingMode", "facingMode")}} را نشان می‌دهد و جهتی که دوربین به آن رو است را مشخص می‌کند. مقدار یکی از موارد زیر خواهد بود:
    - `"user"`
      - : دوربینی که به سمت کاربر است (معمولاً به عنوان «دوربین سلفی» شناخته می‌شود)، که برای عکس سلفی و تماس تصویری استفاده می‌شود.
    - `"environment"`
      - : دوربینی که رو به محیط و دور از کاربر است (زمانی که کاربر به صفحه نمایش نگاه می‌کند). این معمولاً باکیفیت‌ترین دوربین دستگاه است و برای عکاسی عمومی استفاده می‌شود.
    - `"left"`
      - : دوربینی که به سمت محیط سمت چپ کاربر است.
    - `"right"`
      - : دوربینی که به سمت محیط سمت راست کاربر است.
- {{domxref("MediaTrackSettings.frameRate", "frameRate")}}
  - : یک مقدار ممیز شناور با دقت دوبرابر که مقدار فعلی ویژگی {{domxref("MediaTrackConstraints.frameRate", "frameRate")}} را نشان می‌دهد و مشخص می‌کند که ترک چند فریم ویدئو در هر ثانیه دارد. اگر به هر دلیلی نتوان این مقدار را تعیین کرد، مقدار با نرخ همگام‌سازی عمودی دستگاهی که عامل کاربر (user agent) روی آن در حال اجرا است مطابقت خواهد داشت.
- {{domxref("MediaTrackSettings.height", "height")}}
  - : یک مقدار صحیح بلند که مقدار فعلی ویژگی {{domxref("MediaTrackConstraints.height", "height")}} را نشان می‌دهد و ارتفاع داده ویدئویی ترک را بر حسب پیکسل مشخص می‌کند.
- {{domxref("MediaTrackSettings.width", "width")}}
  - : یک مقدار صحیح بلند که مقدار فعلی ویژگی {{domxref("MediaTrackSettings.width", "width")}} را نشان می‌دهد و عرض داده ویدئویی ترک را بر حسب پیکسل مشخص می‌کند.
- {{domxref("MediaTrackSettings.resizeMode", "resizeMode")}}
  - : یک رشته که مقدار فعلی ویژگی {{domxref("MediaTrackConstraints.resizeMode", "resizeMode")}} را نشان می‌دهد و حالتی را مشخص می‌کند که عامل کاربر برای به دست آوردن وضوح ترک استفاده می‌کند. مقدار یکی از موارد زیر خواهد بود:
    - `"none"`
      - : ترک وضوحی را دارد که دوربین، درایور آن یا سیستم‌عامل ارائه می‌دهد.
    - `"crop-and-scale"`
      - : وضوح ترک ممکن است نتیجه استفاده عامل کاربر از برش (cropping) یا کاهش مقیاس از وضوح بالاتر دوربین باشد.

### ویژگی‌های نمونه ترک‌های صفحه اشتراک‌گذاری‌شده

ترک‌هایی که شامل ویدئوی اشتراک‌گذاری‌شده از صفحه کاربر هستند (صرف‌نظر از اینکه داده صفحه از کل صفحه یا بخشی از صفحه، مانند یک پنجره یا تب، می‌آید) عموماً مانند ترک‌های ویدئویی در نظر گرفته می‌شوند، با این استثنا که از تنظیمات اضافه زیر نیز پشتیبانی می‌کنند:

- {{domxref("MediaTrackSettings.cursor", "cursor")}}
  - : یک رشته که نشان می‌دهد آیا نشانگر ماوس در جریان تولیدشده گنجانده شده است یا خیر و تحت چه شرایطی. مقادیر ممکن عبارت‌اند از:
    - `always`
      - : ماوس همیشه در محتوای ویدئویی {domxref("MediaStream")، قابل مشاهده است، مگر اینکه ماوس به بیرون از ناحیه محتوا حرکت کرده باشد.
    - `motion`
      - : نشانگر ماوس همیشه در ویدئو گنجانده می‌شود اگر در حال حرکت باشد، و برای مدت کوتاهی پس از توقف حرکت نیز گنجانده می‌شود.
    - `never`
      - : نشانگر ماوس هرگز در ویدئوی اشتراک‌گذاری‌شده گنجانده نمی‌شود.
- {{domxref("MediaTrackSettings.displaySurface", "displaySurface")}}
  - : یک رشته که نوع منبع موجود در ترک را مشخص می‌کند؛ یکی از موارد زیر:
    - `browser`
      - : جریان شامل محتویات یک تب مرورگر است که توسط کاربر انتخاب شده است.
    - `monitor`
      - : ترک ویدئویی جریان شامل کل محتویات یک یا چند صفحه از صفحه‌های کاربر است.
    - `window`
      - : جریان شامل یک پنجره واحد است که توسط کاربر برای اشتراک‌گذاری انتخاب شده است.
- {{domxref("MediaTrackSettings.logicalSurface", "logicalSurface")}}
  - : یک مقدار بولین که اگر `true` باشد، نشان می‌دهد ویدئوی موجود در ترک ویدئویی جریان شامل یک زمینه رندر پس‌زمینه (background rendering context) است، نه یک زمینه قابل مشاهده برای کاربر. اگر ویدئوی در حال ضبط از یک منبع پیش‌زمینه (قابل مشاهده برای کاربر) می‌آید، این مقدار `false` است.
- {{domxref("MediaTrackSettings.screenPixelRatio", "screenPixelRatio")}}
  - : عددی که نسبت اندازه فیزیکی یک پیکسل در سطح نمایش ضبط‌شده (که با وضوح فیزیکی آن نمایش داده می‌شود) به اندازه منطقی یک پیکسل CSS در صفحه در حال ضبط (که با وضوح منطقی آن نمایش داده می‌شود) را نشان می‌دهد. نمی‌توان از آن به عنوان محدودیت یا قابلیت استفاده کرد.

## مشخصات

{{Specifications}}

## همچنین ببینید

- {{domxref("MediaDevices.getUserMedia()")}}
- {{domxref("MediaDevices.getDisplayMedia()")}}
- {{domxref("MediaStreamTrack.getConstraints()")}}
- {{domxref("MediaStreamTrack.applyConstraints()")}}
- {{domxref("MediaStreamTrack.getSettings()")}}