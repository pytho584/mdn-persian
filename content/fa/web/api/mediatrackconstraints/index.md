---
title: MediaTrackConstraints
slug: Web/API/MediaTrackConstraints
page-type: web-api-interface
spec-urls:
  - https://w3c.github.io/mediacapture-main/#dom-mediatrackconstraints
  - https://w3c.github.io/mediacapture-screen-share/#extensions-to-mediatrackconstraintset
---

{{APIRef("Media Capture and Streams")}}

دیکشنری **`MediaTrackConstraints`** برای توصیف مجموعه‌ای از قابلیت‌های رسانه و مقدار یا مقادیری که هر یک می‌توانند داشته باشند، استفاده می‌شود.

یک دیکشنری محدودیت‌ها به متد {{domxref("MediaStreamTrack.applyConstraints", "applyConstraints()")}} از رابط {{domxref("MediaStreamTrack")}} ارسال می‌شود تا به اسکریپت اجازه دهد مجموعه‌ای از مقادیر یا بازه‌های دقیق (الزامی) و/یا مقادیر یا بازه‌های ترجیحی را برای ترک (track) تعیین کند.

آخرین مجموعه محدودیت‌های سفارشی درخواست‌شده را می‌توان با فراخوانی {{domxref("MediaStreamTrack.getConstraints", "getConstraints()")}} دریافت کرد.

اشیاء از این نوع همچنین می‌توانند به موارد زیر ارسال شوند:

- متد {{domxref("MediaDevices.getUserMedia()")}} برای مشخص کردن محدودیت‌ها روی جریان رسانه‌ای که از سخت‌افزاری مانند دوربین یا میکروفون درخواست می‌شود.
- متد {{domxref("MediaDevices.getDisplayMedia()")}} برای مشخص کردن محدودیت‌ها روی جریان رسانه‌ای که از ضبط صفحه یا پنجره درخواست می‌شود.

## محدودیت‌ها

انواع زیر برای مشخص کردن یک محدودیت برای یک ویژگی استفاده می‌شوند. آن‌ها به شما اجازه می‌دهند یک یا چند مقدار `exact` تعیین کنید که یکی از آن‌ها باید مقدار پارامتر باشد، یا مجموعه‌ای از مقادیر `ideal` که در صورت امکان باید استفاده شوند. همچنین می‌توانید یک مقدار واحد (یا آرایه‌ای از مقادیر) مشخص کنید که عامل کاربر (user agent) پس از اعمال همه محدودیت‌های سخت‌گیرانه‌تر، بهترین تلاش خود را برای مطابقت با آن انجام دهد.

برای آشنایی بیشتر با نحوه کار محدودیت‌ها، به [قابلیت‌ها، محدودیت‌ها و تنظیمات](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints) مراجعه کنید.

> [!NOTE]
> مقادیر `min` و `exact` در محدودیت‌های استفاده‌شده در فراخوانی‌های {{domxref("MediaDevices.getDisplayMedia()")}} مجاز نیستند — آن‌ها یک `TypeError` تولید می‌کنند — اما در محدودیت‌های استفاده‌شده در فراخوانی‌های {{domxref("MediaStreamTrack.applyConstraints()")}} مجاز هستند.

### ConstrainBoolean

نوع محدودیت `ConstrainBoolean` برای مشخص کردن محدودیت برای ویژگی‌ای استفاده می‌شود که مقدار آن یک مقدار بولی (Boolean) است. مقدار آن می‌تواند یک بولی (`true` یا `false`) یا یک شیء شامل ویژگی‌های زیر باشد:

- `exact`
  - : یک بولی که باید مقدار آن ویژگی باشد. اگر ویژگی نتواند به این مقدار تنظیم شود، تطبیق ناموفق خواهد بود.
- `ideal`
  - : یک بولی که مقدار ایده‌آل برای ویژگی را مشخص می‌کند. در صورت امکان این مقدار استفاده می‌شود، اما اگر ممکن نباشد، عامل کاربر نزدیک‌ترین تطبیق ممکن را استفاده خواهد کرد.

### ConstrainBooleanOrDOMString

نوع محدودیت `ConstrainBooleanOrDOMString` برای مشخص کردن محدودیت برای ویژگی‌ای استفاده می‌شود که مقدار آن یک مقدار بولی یا رشته‌ای است. این نوع می‌تواند مقادیری را که در بخش‌های [`ConstrainBoolean`](#constrainboolean) و [`ConstrainDOMString`](#constraindomstring) مشخص شده‌اند بپذیرد.

### ConstrainDouble

نوع محدودیت `ConstrainDouble` برای مشخص کردن محدودیت برای ویژگی‌ای استفاده می‌شود که مقدار آن یک عدد اعشاری با دقت دوگانه (double-precision floating-point) است. مقدار آن می‌تواند یک عدد یا یک شیء شامل ویژگی‌های زیر باشد:

- `max`
  - : یک عدد اعشاری که بزرگ‌ترین مقدار مجاز ویژگی توصیف‌شده را مشخص می‌کند. اگر مقدار نتواند برابر یا کمتر از این مقدار بماند، تطبیق ناموفق خواهد بود.
- `min`
  - : یک عدد اعشاری که کوچک‌ترین مقدار مجاز ویژگی توصیف‌شده را مشخص می‌کند. اگر مقدار نتواند برابر یا بیشتر از این مقدار بماند، تطبیق ناموفق خواهد بود.
- `exact`
  - : یک عدد اعشاری که مقدار مشخص و الزامی را تعیین می‌کند که ویژگی برای قابل قبول بودن باید داشته باشد.
- `ideal`
  - : یک عدد اعشاری که مقدار ایده‌آل برای ویژگی را مشخص می‌کند. در صورت امکان این مقدار استفاده می‌شود، اما اگر ممکن نباشد، عامل کاربر نزدیک‌ترین تطبیق ممکن را استفاده خواهد کرد.

### ConstrainDOMString

نوع محدودیت `ConstrainDOMString` برای مشخص کردن محدودیت برای ویژگی‌ای استفاده می‌شود که مقدار آن یک رشته است. مقدار آن می‌تواند یک رشته، آرایه‌ای از رشته‌ها، یا یک شیء شامل ویژگی‌های زیر باشد:

- `exact`
  - : یک رشته یا آرایه‌ای از رشته‌ها که یکی از آن‌ها باید مقدار ویژگی باشد. اگر ویژگی نتواند به یکی از مقادیر فهرست‌شده تنظیم شود، تطبیق ناموفق خواهد بود.
- `ideal`
  - : یک رشته یا آرایه‌ای از رشته‌ها که مقادیر ایده‌آل را برای ویژگی مشخص می‌کند. در صورت امکان یکی از مقادیر فهرست‌شده استفاده خواهد شد، اما اگر ممکن نباشد، عامل کاربر نزدیک‌ترین تطبیق ممکن را استفاده خواهد کرد.

### ConstrainULong

نوع محدودیت `ConstrainULong` برای مشخص کردن محدودیت برای ویژگی‌ای استفاده می‌شود که مقدار آن یک عدد صحیح است. مقدار آن می‌تواند یک عدد یا یک شیء شامل ویژگی‌های زیر باشد:

- `max`
  - : یک عدد صحیح که بزرگ‌ترین مقدار مجاز ویژگی توصیف‌شده را مشخص می‌کند. اگر مقدار نتواند برابر یا کمتر از این مقدار بماند، تطبیق ناموفق خواهد بود.
- `min`
  - : یک عدد صحیح که کوچک‌ترین مقدار مجاز ویژگی توصیف‌شده را مشخص می‌کند. اگر مقدار نتواند برابر یا بیشتر از این مقدار بماند، تطبیق ناموفق خواهد بود.
- `exact`
  - : یک عدد صحیح که مقدار مشخص و الزامی را تعیین می‌کند که ویژگی برای قابل قبول بودن باید داشته باشد.
- `ideal`
  - : یک عدد صحیح که مقدار ایده‌آل برای ویژگی را مشخص می‌کند. در صورت امکان این مقدار استفاده می‌شود، اما اگر ممکن نباشد، عامل کاربر نزدیک‌ترین تطبیق ممکن را استفاده خواهد کرد.

## ویژگی‌های نمونه

ترکیبی از ویژگی‌های زیر — نه لزوماً همه آن‌ها — روی شیء وجود خواهد داشت. این ممکن است به این دلیل باشد که مرورگر مورد نظر از آن ویژگی پشتیبانی نمی‌کند، یا به این دلیل که آن ویژگی قابل اعمال نیست. برای مثال، از آنجا که {{Glossary("RTP")}} برخی از این مقادیر را در طول مذاکره (negotiation) یک اتصال WebRTC فراهم نمی‌کند، یک ترک مرتبط با {{domxref("RTCPeerConnection")}} شامل برخی مقادیر مانند {{domxref("MediaTrackConstraints.facingMode", "facingMode")}} یا {{domxref("MediaTrackConstraints.groupId", "groupId")}} نخواهد بود.

### ویژگی‌های نمونه مشترک همه ترک‌های رسانه‌ای

- {{domxref("MediaTrackConstraints.deviceId", "deviceId")}}
  - : یک شیء [`ConstrainDOMString`](#constraindomstring) که یک شناسه دستگاه یا آرایه‌ای از شناسه‌های دستگاه قابل قبول و/یا الزامی را مشخص می‌کند.
- {{domxref("MediaTrackConstraints.groupId", "groupId")}}
  - : یک شیء [`ConstrainDOMString`](#constraindomstring) که یک شناسه گروه یا آرایه‌ای از شناسه‌های گروه قابل قبول و/یا الزامی را مشخص می‌کند.

### ویژگی‌های نمونه ترک‌های صوتی

- {{domxref("MediaTrackConstraints.autoGainControl", "autoGainControl")}}
  - : یک شیء [`ConstrainBoolean`](#constrainboolean) که مشخص می‌کند آیا کنترل بهره خودکار (automatic gain control) ترجیح داده می‌شود و/یا الزامی است.
- {{domxref("MediaTrackConstraints.channelCount", "channelCount")}}
  - : یک [`ConstrainULong`](#constrainulong) که تعداد کانال یا بازه تعداد کانال‌های قابل قبول و/یا الزامی را مشخص می‌کند.
- {{domxref("MediaTrackConstraints.echoCancellation", "echoCancellation")}}
  - : یک شیء [`ConstrainBooleanOrDOMString`](#constrainbooleanordomstring) که مشخص می‌کند آیا حذف پژواک (echo cancellation) ترجیح داده می‌شود و/یا الزامی است یا خیر، و در صورت پشتیبانی، چه نوعی.
- {{domxref("MediaTrackConstraints.latency", "latency")}}
  - : یک [`ConstrainDouble`](#constraindouble) که تأخیر (latency) یا بازه تأخیرهای قابل قبول و/یا الزامی را مشخص می‌کند.
- {{domxref("MediaTrackConstraints.noiseSuppression", "noiseSuppression")}}
  - : یک [`ConstrainBoolean`](#constrainboolean) که مشخص می‌کند آیا حذف نویز (noise suppression) ترجیح داده می‌شود و/یا الزامی است.
- {{domxref("MediaTrackConstraints.sampleRate", "sampleRate")}}
  - : یک [`ConstrainULong`](#constrainulong) که نرخ نمونه‌برداری یا بازه نرخ‌های نمونه‌برداری قابل قبول و/یا الزامی را مشخص می‌کند.
- {{domxref("MediaTrackConstraints.sampleSize", "sampleSize")}}
  - : یک [`ConstrainULong`](#constrainulong) که اندازه نمونه یا بازه اندازه‌های نمونه قابل قبول و/یا الزامی را مشخص می‌کند.
- {{domxref("MediaTrackConstraints.volume", "volume")}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : یک [`ConstrainDouble`](#constraindouble) که حجم صدا (volume) یا بازه حجم‌های قابل قبول و/یا الزامی را مشخص می‌کند.

### ویژگی‌های نمونه ترک‌های تصویر

- `whiteBalanceMode`
  - : یک {{jsxref("String")}} که یکی از مقادیر `"none"`، `"manual"`، `"single-shot"` یا `"continuous"` را مشخص می‌کند.
- `exposureMode`
  - : یک {{jsxref("String")}} که یکی از مقادیر `"none"`، `"manual"`، `"single-shot"` یا `"continuous"` را مشخص می‌کند.
- `focusMode`
  - : یک {{jsxref("String")}} که یکی از مقادیر `"none"`، `"manual"`، `"single-shot"` یا `"continuous"` را مشخص می‌کند.
- `pointsOfInterest`
  - : مختصات پیکسلی روی سنسور برای یک یا چند نقطه مورد نظر. این مقدار یا یک شیء به شکل { x:_value_, y:_value_ } است یا آرایه‌ای از چنین اشیائی، که در آن _value_ یک عدد صحیح با دقت دوگانه است.
- `exposureCompensation`
  - : یک [`ConstrainDouble`](#constraindouble) (یک عدد صحیح با دقت دوگانه) که تنظیم گام دیافراگم (f-stop) را تا ±3 مشخص می‌کند.
- `colorTemperature`
  - : یک [`ConstrainDouble`](#constraindouble) (یک عدد صحیح با دقت دوگانه) که دمای رنگ مورد نظر را بر حسب درجه کلوین مشخص می‌کند.
- `iso`
  - : یک [`ConstrainDouble`](#constraindouble) (یک عدد صحیح با دقت دوگانه) که تنظیمات ایزو (iso) مورد نظر را مشخص می‌کند.
- `brightness`
  - : یک [`ConstrainDouble`](#constraindouble) (یک عدد صحیح با دقت دوگانه) که تنظیمات روشنایی مورد نظر را مشخص می‌کند.
- `contrast`
  - : یک [`ConstrainDouble`](#constraindouble) (یک عدد صحیح با دقت دوگانه) که میزان تفاوت بین روشن و تاریک را مشخص می‌کند.
- `saturation`
  - : یک [`ConstrainDouble`](#constraindouble) (یک عدد صحیح با دقت دوگانه) که میزان اشباع رنگ را مشخص می‌کند.
- `sharpness`
  - : یک [`ConstrainDouble`](#constraindouble) (یک عدد صحیح با دقت دوگانه) که شدت لبه‌ها را مشخص می‌کند.
- `focusDistance`
  - : یک [`ConstrainDouble`](#constraindouble) (یک عدد صحیح با دقت دوگانه) که فاصله تا جسم فوکوس‌شده را مشخص می‌کند.
- `zoom`
  - : یک [`ConstrainDouble`](#constraindouble) (یک عدد صحیح با دقت دوگانه) که فاصله کانونی مورد نظر را مشخص می‌کند.
- `torch`
  - : یک مقدار بولی که تعیین می‌کند آیا نور پرکننده (fill light) به‌طور پیوسته روشن است، به این معنی که تا زمانی که ترک فعال است روشن می‌ماند.

### ویژگی‌های نمونه ترک‌های ویدئویی

- {{domxref("MediaTrackConstraints.aspectRatio", "aspectRatio")}}
  - : یک [`ConstrainDouble`](#constraindouble) که نسبت تصویر ({{glossary("aspect ratio")}}) ویدئو یا بازه نسبت‌های تصویر قابل قبول و/یا الزامی را مشخص می‌کند.
- {{domxref("MediaTrackConstraints.facingMode", "facingMode")}}
  - : یک شیء [`ConstrainDOMString`](#constraindomstring) که یک جهت (facing) یا آرایه‌ای از جهت‌ها را که قابل قبول و/یا الزامی هستند مشخص می‌کند.
- {{domxref("MediaTrackConstraints.frameRate", "frameRate")}}
  - : یک [`ConstrainDouble`](#constraindouble) که نرخ فریم یا بازه نرخ‌های فریم قابل قبول و/یا الزامی را مشخص می‌کند.
- {{domxref("MediaTrackConstraints.height", "height")}}
  - : یک [`ConstrainULong`](#constrainulong) که ارتفاع ویدئو یا بازه ارتفاع‌های قابل قبول و/یا الزامی را مشخص می‌کند.
- {{domxref("MediaTrackConstraints.width", "width")}}
  - : یک [`ConstrainULong`](#constrainulong) که عرض ویدئو یا بازه عرض‌های قابل قبول و/یا الزامی را مشخص می‌کند.
- `resizeMode`
  - : یک شیء [`ConstrainDOMString`](#constraindomstring) که یک حالت یا آرایه‌ای از حالت‌ها را مشخص می‌کند که عامل کاربر (UA) می‌تواند برای استخراج وضوح و نرخ فریم یک ترک ویدئویی از آن‌ها استفاده کند. مقادیر مجاز عبارت‌اند از:
    - `crop-and-scale`
      - : عامل کاربر می‌تواند از برش (cropping) و کاهش مقیاس وضوح یا نرخ فریم بر روی خروجی خام سخت‌افزار/سیستم‌عامل استفاده کند تا سایر محدودیت‌ها برآورده شوند. این محدودیت به توسعه‌دهندگان اجازه می‌دهد حتی اگر قالب خاص مشخص‌شده توسط محدودیت‌هایشان به‌صورت بومی توسط سخت‌افزار پشتیبانی نمی‌شود، ویدئوی کم‌وضوح (downscaled) دریافت کنند.
    - `none`
      - : عامل کاربر از وضوح