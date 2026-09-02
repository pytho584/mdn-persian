---
title: "MediaDevices: getDisplayMedia() method"
short-title: getDisplayMedia()
slug: Web/API/MediaDevices/getDisplayMedia
page-type: web-api-instance-method
browser-compat: api.MediaDevices.getDisplayMedia
---

{{APIRef("Screen Capture API")}}{{SecureContext_Header}}

متد **`getDisplayMedia()`** از رابط {{domxref("MediaDevices")}} از کاربر می‌خواهد که محتوای یک نمایشگر یا بخشی از آن (مانند یک پنجره) را به‌عنوان یک {{domxref("MediaStream")}} انتخاب کرده و اجازهٔ ضبط آن را صادر کند.

استریم حاصل را می‌توان با [MediaStream Recording API](/en-US/docs/Web/API/MediaStream_Recording_API) ضبط کرد یا به‌عنوان بخشی از یک نشست [WebRTC](/en-US/docs/Web/API/WebRTC_API) ارسال نمود.

برای جزئیات بیشتر و یک مثال، [استفاده از Screen Capture API](/en-US/docs/Web/API/Screen_Capture_API/Using_Screen_Capture) را ببینید.

## نحو

```js-nolint
getDisplayMedia()
getDisplayMedia(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : شیئی که الزامات مربوط به {{domxref("MediaStream")}} بازگردانده‌شده را مشخص می‌کند.
    گزینه‌های `getDisplayMedia()` همانند [constraintهای](/en-US/docs/Web/API/MediaDevices/getUserMedia#parameters) مربوط به متد {{domxref("MediaDevices.getUserMedia()")}} کار می‌کنند، هرچند در این مورد فقط `audio` و `video` قابل مشخص‌کردن هستند.
    فهرست خصوصیت‌های ممکن برای `getDisplayMedia()` به شرح زیر است:

    - `video` {{optional_inline}}
      - : یک مقدار بولی یا یک نمونه از {{domxref("MediaTrackConstraints")}}؛ مقدار پیش‌فرض `true` است.
        اگر این گزینه حذف شود یا روی `true` تنظیم شود، {{domxref("MediaStream")}} بازگردانده‌شده شامل یک track ویدیویی خواهد بود.
        از آنجا که `getDisplayMedia()` به یک track ویدیویی نیاز دارد، اگر این گزینه روی `false` تنظیم شود، promise با خطای `TypeError` رد خواهد شد.
    - `audio` {{optional_inline}}
      - : یک مقدار بولی یا یک نمونه از {{domxref("MediaTrackConstraints")}}؛ مقدار پیش‌فرض `false` است.
        مقدار `true` نشان می‌دهد که {{domxref("MediaStream")}} بازگردانده‌شده شامل یک track صوتی خواهد بود، به‌شرط آنکه صدا برای سطح نمایش انتخاب‌شده توسط کاربر پشتیبانی و در دسترس باشد.
    - `controller` {{Experimental_Inline}} {{optional_inline}}
      - : یک نمونه شیء {{domxref("CaptureController")}} شامل متدهایی که در صورت گنجاندن، می‌توان از آن‌ها برای دستکاری بیشتر نشست ضبط استفاده کرد.
    - `monitorTypeSurfaces` {{Experimental_Inline}} {{optional_inline}}
      - : یک مقدار شمارشی (enumerated) که مشخص می‌کند آیا مرورگر باید کل صفحه‌ها را در گزینه‌های ضبط صفحه که همراه با گزینه‌های تب و پنجره به کاربر ارائه می‌شود قرار دهد یا نه.
        این گزینه برای محافظت از شرکت‌ها در برابر نشت اطلاعات خصوصی ناشی از خطای کارکنان هنگام استفاده از برنامه‌های کنفرانس ویدیویی در نظر گرفته شده است.
        مقادیر ممکن عبارتند از:
        - `include`: نشان می‌دهد که مرورگر باید گزینه‌های صفحه را شامل شود.
        - `exclude`: نشان می‌دهد که گزینه‌های صفحه باید حذف شوند.

        > [!NOTE]
        > نمی‌توانید `monitorTypeSurfaces: "exclude"` را هم‌زمان با [`displaySurface: "monitor"`](/en-US/docs/Web/API/MediaTrackConstraints/displaySurface) تنظیم کنید، زیرا این دو تنظیم با یکدیگر تناقض دارند.
        > تلاش برای این کار باعث می‌شود فراخوانی `getDisplayMedia()` با خطای `TypeError` شکست بخورد.

    - `preferCurrentTab` {{non-standard_inline}} {{Experimental_Inline}} {{optional_inline}}
      - : یک مقدار بولی؛ مقدار `true` به مرورگر دستور می‌دهد که تب فعلی را به‌عنوان برجسته‌ترین منبع ضبط ارائه دهد، یعنی به‌صورت یک گزینهٔ جداگانه با عنوان «This Tab» در گزینه‌های «Choose what to share» که به کاربر نمایش داده می‌شود.
        این کار مفید است، زیرا بسیاری از انواع برنامه‌ها معمولاً فقط می‌خواهند تب فعلی را به اشتراک بگذارند.
        برای مثال، یک برنامهٔ ارائهٔ اسلاید ممکن است بخواهد به کاربر اجازه دهد تب فعلی را که شامل ارائه است در یک کنفرانس مجازی پخش کند.
    - `selfBrowserSurface` {{Experimental_Inline}} {{optional_inline}}
      - : یک مقدار شمارشی که مشخص می‌کند آیا مرورگر باید به کاربر اجازه دهد تب فعلی را برای ضبط انتخاب کند.
        این کار به جلوگیری از اثر «تالار بی‌پایان آینه‌ها» (infinite hall of mirrors) کمک می‌کند که وقتی یک برنامهٔ کنفرانس ویدیویی به‌طور ناخواسته نمایشگر خودش را به اشتراک می‌گذارد رخ می‌دهد.
        مقادیر ممکن عبارتند از:
        - `include`: نشان می‌دهد که مرورگر باید تب فعلی را در گزینه‌های ارائه‌شده برای ضبط شامل شود.
        - `exclude`: نشان می‌دهد که تب فعلی باید از گزینه‌ها حذف شود.
    - `surfaceSwitching` {{Experimental_Inline}} {{optional_inline}}
      - : یک مقدار شمارشی که مشخص می‌کند آیا مرورگر باید کنترلی نمایش دهد که به کاربر امکان می‌دهد در طول اشتراک‌گذاری صفحه، تب مشترک را به‌صورت پویا تغییر دهد.
        این کار راحت‌تر از آن است که هر بار کاربر بخواهد تب مشترک را تغییر دهد، کل فرایند اشتراک‌گذاری دوباره طی شود.
        مقادیر ممکن عبارتند از:
        - `include`: نشان می‌دهد که مرورگر باید کنترل را شامل شود.
        - `exclude`: نشان می‌دهد که کنترل نباید نمایش داده شود.
    - `systemAudio` {{Experimental_Inline}} {{optional_inline}}
      - : یک مقدار شمارشی که مشخص می‌کند آیا مرورگر باید صدای سیستم را در میان منابع صوتی ممکن ارائه‌شده به کاربر قرار دهد.
        مقادیر ممکن عبارتند از:
        - `include`: نشان می‌دهد که مرورگر باید صدای سیستم را در فهرست گزینه‌ها قرار دهد.
        - `exclude`: نشان می‌دهد که صدای سیستم باید از گزینه‌های نمایش‌داده‌شده حذف شود.
    - `windowAudio` {{Experimental_Inline}} {{optional_inline}}
      - : یک مقدار شمارشی که به مرورگر نشان می‌دهد کاربر هنگام ارائهٔ گزینه‌های اشتراک‌گذاری پنجره، چه گزینهٔ اشتراک‌گذاری صدا دریافت کند. مقادیر ممکن عبارتند از:
        - `exclude`: نشان می‌دهد که هنگام انتخاب گزینهٔ اشتراک‌گذاری پنجره، صدا نباید قابل اشتراک‌گذاری باشد.
        - `window`: نشان می‌دهد که هنگام انتخاب گزینهٔ اشتراک‌گذاری پنجره، فقط صدای منتشرشده از آن پنجره به اشتراک گذاشته شود.
        - `system`: نشان می‌دهد که هنگام انتخاب گزینهٔ اشتراک‌گذاری پنجره، تمام صدای سیستم به اشتراک گذاشته شود.

> [!NOTE]
> برای بیشتر این گزینه‌ها، مقدار پیش‌فرض توسط مشخصات (spec) الزامی نشده است. برای گزینه‌های مستقل که مقدار پیش‌فرض ذکر نشده، بخش [سازگاری مرورگر](#browser_compatibility) را برای مقادیر پیش‌فرض خاص مرورگرها ببینید.

> [!NOTE]
> برای جزئیات بسیار بیشتر دربارهٔ نحوهٔ کار این گزینه‌ها، مقالهٔ [قابلیت‌ها، محدودیت‌ها و تنظیمات](/en-US/docs/Web/API/Media_Capture_and_Streams_API/Constraints) را ببینید.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به یک {{domxref("MediaStream")}} شامل یک track ویدیویی که محتوای آن از ناحیهٔ انتخاب‌شده توسط کاربر از صفحه می‌آید، و همچنین یک track صوتی اختیاری، resolve می‌شود.

> [!NOTE]
> پشتیبانی مرورگر از trackهای صوتی متفاوت است؛ هم از نظر اینکه آیا اصلاً توسط ضبط‌کنندهٔ رسانه پشتیبانی می‌شوند و هم از نظر منابع صوتی پشتیبانی‌شده.
> برای جزئیات مربوط به هر مرورگر، [جدول سازگاری](#browser_compatibility) را بررسی کنید.

### استثناها

- `AbortError` {{domxref("DOMException")}}
  - : اگر خطا یا شکستی رخ دهد که با هیچ‌یک از سایر استثناهای فهرست‌شده در اینجا مطابقت نداشته باشد، پرتاب می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر فراخوانی `getDisplayMedia()` از کدی انجام نشده باشد که در اثر یک {{glossary("transient activation")}} اجرا می‌شود، مانند یک event handler.
    یا اگر زمینهٔ مرورگر کاملاً فعال نباشد یا فوکوس نداشته باشد.
    یا اگر گزینهٔ `controller` قبلاً در ایجاد یک {{domxref("MediaStream")}} دیگر استفاده شده باشد.
- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر اجازهٔ دسترسی به ناحیهٔ صفحه توسط کاربر رد شده باشد، یا نمونهٔ مرورگری کنونی اجازهٔ دسترسی به اشتراک‌گذاری صفحه را نداشته باشد (مثلاً توسط [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy)).
- `NotFoundError` {{domxref("DOMException")}}
  - : اگر هیچ منبعی از ویدیوی صفحه برای ضبط در دسترس نباشد، پرتاب می‌شود.
- `NotReadableError` {{domxref("DOMException")}}
  - : اگر کاربر یک صفحه، پنجره، تب یا منبع دیگری از داده‌های صفحه را انتخاب کرده باشد، اما خطا یا قفلی در سطح سخت‌افزار یا سیستم‌عامل رخ دهد که از اشتراک‌گذاری منبع انتخابی جلوگیری کند، پرتاب می‌شود.
- `OverconstrainedError` {{domxref("DOMException")}}
  - : اگر پس از ایجاد استریم، اعمال هر یک از constraintهای مشخص‌شده به این دلیل که هیچ استریم سازگاری نمی‌توانست تولید شود، شکست بخورد، پرتاب می‌شود.
- {{jsxref("TypeError")}}
  - : اگر `options` مشخص‌شده شامل مقادیری باشد که در هنگام فراخوانی `getDisplayMedia()` مجاز نیستند، مثلاً خصوصیت `video` روی `false` تنظیم شده باشد، یا اگر هر یک از {{domxref("MediaTrackConstraints")}} مشخص‌شده مجاز نباشند، پرتاب می‌شود.
    مقادیر `min` و `exact` در constraintهای مورد استفاده در فراخوانی‌های `getDisplayMedia()` مجاز نیستند.

## امنیت

از آنجا که `getDisplayMedia()` می‌تواند به روش‌های سوءاستفاده‌آمیز استفاده شود، ممکن است منبع نگرانی‌های قابل‌توجهی در زمینهٔ حریم خصوصی و امنیت باشد.
به همین دلیل، مشخصات (specification) اقداماتی را که مرورگرها برای پشتیبانی کامل از `getDisplayMedia()` ملزم به انجام آن‌ها هستند، به‌تفصیل شرح می‌دهد.

- گزینه‌های مشخص‌شده نمی‌توانند برای محدودکردن انتخاب‌های موجود برای کاربر استفاده شوند.
  در عوض، باید پس از انتخاب منبع توسط کاربر اعمال شوند تا خروجی منطبق بر گزینه‌ها تولید شود.
- اجازهٔ آغاز به کار برای استفاده از `getDisplayMedia()` نمی‌تواند برای استفادهٔ مجدد ذخیره شود.
  کاربر باید هر بار برای دریافت اجازه، درخواست را ببیند.
- [فعال‌سازی گذرای کاربر](/en-US/docs/Web/Security/Defenses/User_activation) (transient user activation) الزامی است.
  کاربر باید با صفحه یا یک عنصر رابط کاربری تعامل کند تا این قابلیت کار کند.
- مرورگرها ترغیب می‌شوند که دربارهٔ اشتراک‌گذاری نمایشگرها یا پنجره‌هایی که شامل مرورگر هستند به کاربران هشدار دهند و به‌دقت مراقب محتوای دیگری باشند که ممکن است ضبط شود و به سایر کاربران نمایش داده شود.

## مثال‌ها

در مثال زیر، متدی به نام `startCapture()` ایجاد می‌شود که با دریافت مجموعه‌ای از گزینه‌های مشخص‌شده توسط پارامتر `displayMediaOptions`، ضبط صفحه را آغاز می‌کند.

```js
const displayMediaOptions = {
  video: {
    displaySurface: "browser",
  },
  audio: {
    suppressLocalAudioPlayback: false,
  },
  preferCurrentTab: false,
  selfBrowserSurface: "exclude",
  systemAudio: "include",
  surfaceSwitching: "include",
  monitorTypeSurfaces: "include",
};

async function startCapture(displayMediaOptions) {
  let captureStream;

  try {
    captureStream =
      await navigator.mediaDevices.getDisplayMedia(displayMediaOptions);
  } catch (err) {
    console.error(`Error: ${err}`);
  }
  return captureStream;
}
```

این مثال از {{jsxref("Operators/await", "await")}} استفاده می‌کند تا به‌صورت ناهمزمان منتظر بماند تا `getDisplayMedia()` با یک {{domxref("MediaStream")}} که شامل محتویات نمایشگر مطابق گزینه‌های مشخص‌شده است، resolve شود.
سپس استریم به فراخواننده (caller) بازگردانده می‌شود تا مورد استفاده قرار گیرد؛ شاید برای افزودن به یک تماس WebRTC با استفاده از {{domxref("RTCPeerConnection.addTrack()")}} به منظور افزودن track ویدیویی از استریم.

> [!NOTE]
> دموی [Screen sharing controls](https://chrome.dev/screen-sharing-controls/) پیاده‌سازی کاملی را ارائه می‌دهد که به شما امکان می‌دهد با انتخاب constraintها و گزینه‌های دلخواه `getDisplayMedia()`، ضبط صفحه ایجاد کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Screen Capture API](/en-US/docs/Web/API/Screen_Capture_API)
- [Using the Screen Capture API](/en-US/docs/Web/API/Screen_Capture_API/Using_Screen_Capture)
- [Media Capture and Streams API](/en-US/docs/Web/API/Media_Capture_and_Streams_API)
- [WebRTC API](/en-US/docs/Web/API/WebRTC_API)
- {{domxref("MediaDevices.getUserMedia", "getUserMedia()")}}: ضبط رسانه از دوربین و/یا میکروفون