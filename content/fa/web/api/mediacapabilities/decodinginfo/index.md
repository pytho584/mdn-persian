---
title: "MediaCapabilities: decodingInfo() method"
short-title: decodingInfo()
slug: Web/API/MediaCapabilities/decodingInfo
page-type: web-api-instance-method
browser-compat: api.MediaCapabilities.decodingInfo
---

{{APIRef("Media Capabilities API")}}{{AvailableInWorkers}}

متد **`decodingInfo()`** از رابط {{domxref("MediaCapabilities")}} یک قول برمی‌گرداند که با اطلاعاتی درباره اینکه عامل کاربر (user agent) چقدر خوب می‌تواند رسانه‌ای با یک پیکربندی مشخص را رمزگشایی/نمایش دهد، fulfil می‌شود.

شیء resolved شامل سه ویژگی بولی `supported`، `smooth` و `powerefficient` است که نشان می‌دهد آیا رمزگشایی رسانه توصیف‌شده پشتیبانی می‌شود، و اگر بله، آیا رمزگشایی روان و کم‌مصرف خواهد بود.

این متد همچنین می‌تواند برای تست قابلیت‌های عامل کاربر برای رمزگشایی رسانه‌ای که با یک سیستم کلید (key system) رمزگذاری شده است استفاده شود، اما فقط زمانی که در رشته اصلی (main thread) و در یک زمینه امن (secure context) فراخوانی شود.
اگر پیکربندی ارسال‌شده در ویژگی `configuration.keySystemConfiguration` برای رمزگشایی داده‌ها پشتیبانی شود، قول resolved همچنین شامل یک شیء {{domxref("MediaKeySystemAccess")}} خواهد بود که می‌تواند برای ایجاد یک شیء {{domxref("MediaKeys")}} برای راه‌اندازی پخش رمزگذاری‌شده استفاده شود.

> **یادداشت:** فراخوانی `decodingInfo()` با این ویژگی ممکن است اثرات قابل مشاهده برای کاربر داشته باشد، مانند درخواست مجوز برای دسترسی به یک یا چند منبع سیستم.
> بنابراین، این تابع فقط زمانی باید فراخوانی شود که برنامه آماده ایجاد و استفاده از یک شیء `MediaKeys` با پیکربندی ارائه‌شده باشد.

## نحو

```js-nolint
decodingInfo(configuration)
```

### پارامترها

- `configuration`
  - : یک شیء با یک ویژگی `type`، _یا_ یک ویژگی `video` یا `audio` حاوی یک پیکربندی از نوع مناسب، و به صورت اختیاری یک `keySystemConfiguration` هنگام رمزگشایی رسانه‌ای که با یک سیستم کلید رمزگذاری شده است: <!-- MediaDecodingConfiguration در مشخصات -->
    - `type`
      - : نوع رسانه‌ای که در حال تست است. یکی از سه مقدار زیر را می‌گیرد:
        - `file`
          - : نمایانگر یک پیکربندی است که برای پخش یک فایل ساده در نظر گرفته شده است.
        - `media-source`
          - : نمایانگر یک پیکربندی است که برای پخش یک {{domxref("MediaSource")}} در نظر گرفته شده است.
        - `webrtc`
          - : نمایانگر یک پیکربندی است که قرار است با استفاده از {{domxref("RTCPeerConnection")}} دریافت شود (زمانی که `keySystemConfiguration` تنظیم شده باشد مجاز نیست).

    - `video`
      - : شیء پیکربندی برای یک منبع رسانه ویدئویی.
        دارای ویژگی‌های زیر است: <!-- VideoConfiguration در مشخصات -->
        - `contentType`
          - : رشته‌ای حاوی یک نوع MIME ویدئویی معتبر، و (به صورت اختیاری) یک پارامتر [`codecs`](/en-US/docs/Web/Media/Guides/Formats/codecs_parameter).
        - `width`
          - : عرض ویدئو.
        - `height`
          - : ارتفاع ویدئو.
        - `bitrate`
          - : تعداد بیت‌هایی که برای رمزگذاری یک ثانیه از فایل ویدئویی استفاده شده است.
        - `framerate`
          - : تعداد فریم‌هایی که یک ثانیه از پخش ویدئو را تشکیل می‌دهند.

    - `audio`
      - : شیء پیکربندی برای یک منبع رسانه صوتی.
        دارای ویژگی‌های زیر است: <!-- AudioConfiguration در مشخصات -->
        - `contentType`
          - : رشته‌ای حاوی یک نوع MIME صوتی معتبر، و (به صورت اختیاری) یک پارامتر [`codecs`](/en-US/docs/Web/Media/Guides/Formats/codecs_parameter).
        - `channels`
          - : تعداد کانال‌های استفاده‌شده توسط track صوتی.
        - `bitrate`
          - : تعداد بیت‌هایی که برای رمزگذاری یک ثانیه از فایل صوتی استفاده شده است.
        - `samplerate`
          - : تعداد نمونه‌های صوتی که یک ثانیه از فایل صوتی را تشکیل می‌دهند.

    - `keySystemConfiguration` {{optional_inline}}
      - : شیءای که پیکربندی سیستم کلید برای رسانه رمزگذاری‌شده را مشخص می‌کند.

        > **یادداشت:** [`Navigator.requestMediaKeySystemAccess()`](/en-US/docs/Web/API/Navigator/requestMediaKeySystemAccess) در آرگومان `supportedConfigurations` خود آرایه‌هایی از برخی از انواع داده‌های مشابه می‌گیرد.

        اگر مشخص شود، [`type`](#type) باید `media-source` یا `file` باشد (نه `webrtc`).
        دارای ویژگی‌های زیر است: <!-- MediaCapabilitiesKeySystemConfiguration در مشخصات -->
        - `keySystem`
          - : رشته‌ای که سیستم کلید رسانه را شناسایی می‌کند.
            به عنوان مثال `org.w3.clearkey` یا `com.widevine.alpha`.

        - `initDataType` {{optional_inline}}
          - : رشته‌ای که نام نوع داده قالب داده‌های مقداردهی اولیه را نشان می‌دهد، مانند `"cenc"`، `"keyids"` و `"webm"`.
            نام‌های مجاز در [ثبت قالب داده‌های مقداردهی اولیه الحاقات رسانه رمزگذاری‌شده](https://w3c.github.io/encrypted-media/format-registry/initdata/) تعریف شده‌اند.

        - `distinctiveIdentifier` {{optional_inline}}
          - : رشته‌ای که نشان می‌دهد آیا پیاده‌سازی ممکن است از "شناسه‌های متمایز" (یا شناسه‌های دائمی متمایز) برای هر عملیات مرتبط با هر شیء ایجاد شده از این پیکربندی استفاده کند.
            مقادیر مجاز عبارتند از:
            - `required`
              - : شیء برگشتی باید از این ویژگی پشتیبانی کند.
            - `optional`
              - : شیء برگشتی ممکن است از این ویژگی پشتیبانی کند.
                این مقدار پیش‌فرض است.
            - `not-allowed`
              - : شیء برگشتی نباید از این ویژگی پشتیبانی یا استفاده کند.

        - `persistentState` {{optional_inline}}
          - : رشته‌ای که نشان می‌دهد آیا شیء برگشتی باید بتواند داده‌های جلسه یا هر نوع وضعیت دیگری را ذخیره کند.
            مقادیر مجاز عبارتند از:
            - `required`
              - : شیء برگشتی باید از این ویژگی پشتیبانی کند.
            - `optional`
              - : شیء برگشتی ممکن است از این ویژگی پشتیبانی کند.
                این مقدار پیش‌فرض است.
            - `not-allowed`
              - : شیء برگشتی نباید از این ویژگی پشتیبانی یا استفاده کند.
                فقط جلسات "موقت" (temporary) زمانی که وضعیت پایدار مجاز نیست می‌توانند ایجاد شوند.

        - `sessionTypes` {{optional_inline}}
          - : آرایه‌ای از رشته‌ها که انواع جلساتی را که باید پشتیبانی شوند نشان می‌دهد.
            مقادیر مجاز شامل:
            - `temporary`
              - : جلسه‌ای که مجوز، کلید(ها) و رکورد یا داده‌های مرتبط با جلسه در آن ذخیره نمی‌شوند.
                برنامه نیازی به مدیریت چنین ذخیره‌سازی ندارد.
                پیاده‌سازی‌ها باید از این گزینه پشتیبانی کنند و این گزینه پیش‌فرض است.
            - `persistent-license`
              - : جلسه‌ای که مجوز (و احتمالاً سایر داده‌های مرتبط با جلسه) در آن ذخیره خواهد شد.
                یک رکورد از مجوز و کلیدهای مرتبط حتی اگر مجوز از بین برود باقی می‌ماند، و تأییدی ارائه می‌دهد که مجوز و کلید(های) موجود در آن دیگر توسط مشتری قابل استفاده نیستند.

        - `audio` {{optional_inline}}
          - : پیکربندی track سیستم کلید صوتی مرتبط با [`audio` configuration](#audio) بالا.
            اگر تنظیم شود، [`audio` configuration](#audio) نیز باید تنظیم شود.
            - `encryptionScheme`
              - : طرح رمزگذاری مرتبط با نوع محتوا، مانند `cenc`، `cbcs`، `cbcs-1-9`.
                این مقدار باید توسط یک برنامه تنظیم شود (پیش‌فرض `null` است، که نشان می‌دهد هر طرح رمزگذاری ممکن است استفاده شود).
            - `robustness`
              - : سطح استحکام مرتبط با نوع محتوا.
                رشته خالی نشان می‌دهد که هر توانایی برای رمزگشایی و رمزگشایی نوع محتوا قابل قبول است.

        - `video` {{optional_inline}}
          - : پیکربندی track سیستم کلید ویدئویی مرتبط با [`video` configuration](#video) بالا.
            اگر تنظیم شود، [`video` configuration](#video) نیز باید تنظیم شود.
            - `encryptionScheme`
              - : طرح رمزگذاری مرتبط با نوع محتوا، مانند `cenc`، `cbcs`، `cbcs-1-9`.
                این مقدار باید توسط یک برنامه تنظیم شود (پیش‌فرض `null` است، که نشان می‌دهد هر طرح رمزگذاری ممکن است استفاده شود).
            - `robustness`
              - : سطح استحکام مرتبط با نوع محتوا.
                رشته خالی نشان می‌دهد که هر توانایی برای رمزگشایی و رمزگشایی نوع محتوا قابل قبول است.

### مقدار بازگشتی

یک {{jsxref('Promise')}} که با یک شیء حاوی ویژگی‌های زیر fulfil می‌شود:

- `supported`
  - : `true` اگر محتوای رسانه اصلاً قابل رمزگشایی باشد. در غیر این صورت `false` است.
- `smooth`
  - : `true` اگر پخش رسانه بتواند با نرخ فریم مشخص‌شده در پیکربندی بدون نیاز به انداختن فریم‌ها پخش شود. در غیر این صورت `false` است.
- `powerEfficient`
  - : `true` اگر پخش رسانه کم‌مصرف باشد. در غیر این صورت `false` است.
- `keySystemAccess`
  - : یک {{domxref("MediaKeySystemAccess")}} که می‌تواند برای ایجاد یک شیء {{domxref("MediaKeys")}} برای راه‌اندازی پخش رمزگذاری‌شده استفاده شود، یا اگر رمزگشایی با پیکربندی ارائه‌شده پشتیبانی نشود `null` است.

مرورگرها یک پیکربندی رسانه پشتیبانی‌شده را به عنوان `smooth` و `powerEfficient` گزارش می‌دهند تا زمانی که آمار روی این دستگاه ثبت شود.
همه کدک‌های صوتی پشتیبانی‌شده `powerEfficient` را به عنوان `true` گزارش می‌دهند.

### استثناها

- {{jsxref("TypeError")}}
  - : اگر `configuration` ارسال‌شده به متد `decodingInfo()` نامعتبر باشد، چه به دلیل اینکه نوع آن ویدئو یا صوتی نیست، `contentType` یک نوع MIME کدک معتبر نیست، پیکربندی رمزگشایی رسانه یک مقدار معتبر برای `type` (file، media-source یا webrtc) نیست، یا هر خطای دیگری در پیکربندی رسانه ارسال‌شده به متد، از جمله حذف هر مقدار، پرتاب می‌شود.

- `InvalidStateError` {{domxref("DOMException")}}
  - : متد در یک worker زمانی که [`configuration.keySystemConfiguration`](#keysystemconfiguration) تعریف شده است فراخوانی شود.

- `SecurityError` {{domxref("DOMException")}}
  - : متد خارج از یک زمینه امن و زمانی که [`configuration.keySystemConfiguration`](#keysystemconfiguration) تعریف شده است فراخوانی شود.

## نکات استفاده

### مقایسه با Navigator.requestMediaKeySystemAccess()

`decodingInfo()` و متد {{domxref("Navigator.requestMediaKeySystemAccess()")}} از [API الحاقات رسانه رمزگذاری‌شده](/en-US/docs/Web/API/Encrypted_Media_Extensions_API) رویکردهای اساساً متفاوتی را برای انتخاب یک پیکربندی برای رمزگشایی رسانه رمزگذاری‌شده منعکس می‌کنند.

پارامتر پیکربندی برای `Navigator.requestMediaKeySystemAccess()` یک آرایه از پیکربندی‌های ممکن می‌گیرد و به سیستم اجازه می‌دهد تا پیکربندی‌ای را که مناسب می‌داند انتخاب کند.

در مقابل، `decodingInfo()` یک پیکربندی را در یک زمان می‌گیرد.
انتظار می‌رود که فراخواننده `decodingInfo()` را چندین بار اجرا کند، از پیکربندی‌های ترجیحی‌تر شروع کرده و به محض یافتن پیکربندی‌ای که نیازهای برنامه برای روان بودن، کم‌مصرف بودن یا هر دو را برآورده می‌کند، متوقف شود.
به عبارت دیگر، تصمیم انتخاب به فراخواننده واگذار می‌شود.

## مثال‌ها

### دریافت اطلاعات رمزگشایی برای فایل‌های رسانه رمزگذاری‌نشده

این مثال نحوه ایجاد یک پیکربندی رسانه برای یک فایل صوتی و سپس استفاده از آن در `MediaCapabilities.decodingInfo()` را نشان می‌دهد.

```css hidden
#log {
  height: 100px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

```html hidden
<pre id="log"></pre>
```

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

```js
// Create media configuration to be tested
const audioConfig = {
  type: "file", // or 'media-source' or 'webrtc'
  audio: {
    contentType: "audio/ogg; codecs=vorbis", // valid content type
    channels: 2, // audio channels used by the track
    bitrate: 132700, // number of bits used to encode 1s of audio
    samplerate: 5200, // number of audio samples making up that 1s.
  },
};

// check support and performance
navigator.mediaCapabilities.decodingInfo(audioConfig).then((result) => {
  if (result.supported) {
    log(
      `The audio configuration is supported${result.smooth ? ", smooth" : ", not smooth"}${result.powerEfficient ? ", power efficient" : ", not power efficient"}.`,
    );
  } else {
    log("The audio configuration is not supported");
  }
});
```

به طور مشابه، کد زیر پیکربندی برای یک فایل ویدئویی را نشان می‌دهد.

```js
const videoConfig = {
  type: "file",
  video: {
    contentType: "video/webm;codecs=vp8", // valid content type
    width: 800, // width of the video
    height: 600, // height of the video
    bitrate: 10000, // number of bits used to encode 1s of video
    framerate: 30, // number of frames making up that 1s.
  },
};

// check support and performance
navigator.mediaCapabilities.decodingInfo(videoConfig).then((result) => {
  if (result.supported) {
    log(
      `The video configuration is supported${result.smooth ? ", smooth" : ", not smooth"}${result.powerEfficient ? ", power efficient" : ", not power efficient"}.`,
    );
  } else {
    log("The video configuration is not supported");
  }
});
```

{{EmbedLiveSample("Getting decoding information for unencrypted media files")}}

### دریافت اطلاعات رمزگشایی برای رسانه رمزگذاری‌شده

این مثال نحوه استفاده از `decodingInfo()` برای انتخاب یک پیکربندی رسانه برای محتوای رمزگذاری‌شده را نشان می‌دهد.

مانند مثال قبلی یک پیکربندی رسانه تعریف می‌کنیم، اما این بار از نوع `media-source` (به جای `file`) استفاده می‌کنیم و محتوای صوتی و ویدئویی را مشخص می‌کنیم.
همچنین یک `keySystemConfiguration` ساده مشخص می‌کنیم.

```css hidden
#log {
  height: 100px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

```html hidden
<pre id="log"></pre>
```

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

```js
const encryptedMediaConfig = {
  type: "media-source", // or 'file'
  audio: {
    contentType: "audio/webm; codecs=opus",
    channels: 2, // audio channels used by the track
    bitrate: 132700, // number of bits used to encode 1s of audio
    samplerate: 48000, // number of audio samples making up that 1s.
  },
  video: {
    contentType: 'video/webm; codecs="vp09.00.10.08"',
    width: 800, // width of the video
    height: 600, // height of the video
    bitrate: 10000, // number of bits used to encode 1s of video
    framerate: 30, // number of frames making up that 1s.
  },
  keySystemConfiguration: {
    keySystem: "org.w3.clearkey",
    initDataType: "webm",
    distinctiveIdentifier: "required",
  },
};
```

در مثال قبلی از [زنجیره‌سازی قول‌ها](/en-US/docs/Web/JavaScript/Guide/Using_promises#chaining) برای انتظار برای نتیجه استفاده کردیم.
در اینجا ما انتخاب کرده‌ایم که از [`async` و `await`](/en-US/docs/Learn_web_development/Extensions/Async_JS/Promises#async_and_await) برای انتظار برای نتیجه استفاده کنیم و سپس آن را ثبت کنیم.

```js
getDecodingInfo(encryptedMediaConfig);

async function getDecodingInfo(mediaConfig) {
  const result = await navigator.mediaCapabilities.decodingInfo(mediaConfig);
  console.log(result);
  if (!result.supported) {
    log("This encrypted media configuration is not supported.");
    return;
  }

  // keySystemAccess is returned if decoding encrypted media is supported
  // This can be used to decrypt and playback the media
  if (!result.keySystemAccess) {
    log("Encrypted media support is not available.");
    return;
  }

  log(
    `The encrypted media configuration is supported${result.smooth ? ", smooth" : ", not smooth"}${result.powerEfficient ? ", power efficient" : ", not power efficient"}.`,
  );
}
```

خروجی ثبت شده در زیر نشان داده شده است.

{{EmbedLiveSample("Getting decoding information for encrypted media")}}

### پیمایش در اطلاعات رمزگشایی برای رسانه رمزگذاری‌شده

مثال قبلی نشان داد که چگونه می‌توانید از `decodingInfo()` برای دریافت اطلاعات فقط برای یک پیکربندی استفاده کنید.
در واقعیت، این متد معمولاً به صورت تکراری با تعدادی پیکربندی فراخوانی می‌شود و اولین پیکربندی پشتیبانی‌شده‌ای که معیارهای برنامه برای پخش روان یا کم‌مصرف را برآورده می‌کند انتخاب می‌کند.
نحوه کار این روش در زیر توضیح داده شده است.

با فرض اینکه از قبل یک `Array` از پیکربندی‌های رسانه به نام `orderedMediaConfigs` داریم که به ترتیب از بیشترین به کمترین مطلوب مرتب شده‌اند، می‌توانیم از [`Array.prototype.map()`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map) برای فراخوانی `decodingInfo()` برای هر پیکربندی استفاده کنیم و آرایه‌ای حاوی تمام اشیاء {{jsxref("Promise")}} برگشتی بدست آوریم.

```js
const capabilitiesPromises = orderedMediaConfigs.map((mediaConfig) =>
  navigator.mediaCapabilities.decodingInfo(mediaConfig),
);
```

سپس از یک [حلقه `for await...of`](/en-US/docs/Web/JavaScript/Reference/Statements/for-await...of) برای پیمایش قول‌ها در حین resolve شدن استفاده می‌کنیم.
در حلقه، آخرین پیکربندی پشتیبانی‌شده را در `nonSmoothConfig` ذخیره می‌کنیم و به محض یافتن یک پیکربندی روان، از حلقه خارج می‌شویم و این را به عنوان `bestConfig` خود تنظیم می‌کنیم.

```js
// Assume this app wants a supported && smooth config.
let bestConfig = null;
let nonSmoothConfig = null;
for await (const mediaCapabilityInfo of capabilitiesPromises) {
  if (!mediaCapabilityInfo.supported) continue;

  if (!mediaCapabilityInfo.smooth) {
    nonSmoothConfig = mediaCapabilityInfo;
    continue;
  }

  bestConfig = mediaCapabilityInfo;
  break;
}
```

اگر یک پیکربندی روان و پشتیبانی‌شده در حین حلقه پیدا کردیم (`bestConfig`)، از آن برای [ایجاد کلیدهای رسانه](/en-US/docs/Web/API/MediaKeySystemAccess/createMediaKeys) و رمزگشایی رسانه استفاده می‌کنیم.
اگر هیچ پیکربندی روانی کشف نکردیم، ممکن است به جای آن از `nonSmoothConfig` برای رمزگشایی رسانه استفاده کنیم.
این آخرین پیکربندی پشتیبانی‌شده‌ای خواهد بود که پیدا شده است، که به دلیل نحوه مرتب‌سازی `orderedMediaConfigs` اصلی، باید پیکربندی با کمترین نرخ فریم باشد.

```js
let keys = null;
if (bestConfig) {
  keys = await bestConfig.keySystemAccess.createMediaKeys();
  // … use keys to decode media using best config
} else if (nonSmoothConfig) {
  console.log(
    "No smooth configs found. Using lowest resolution configuration!",
  );
  keys = await nonSmoothConfig.keySystemAccess.createMediaKeys();
  // … use keys to decode media using lowest framerate config
} else {
  console.log("No supported configs!");
  // Fail!
}
```

اگر هیچ پیکربندی پشتیبانی‌شده‌ای وجود نداشته باشد، چاره‌ای جز شکست و اطلاع‌رسانی به کاربر نداریم.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("MediaCapabilities.encodingInfo()")}}
- {{domxref("HTMLMediaElement.canPlayType()")}} برای file
- {{domxref("MediaSource.isTypeSupported_static", "MediaSource.isTypeSupported()")}} برای media-source
- {{domxref("Navigator.requestMediaKeySystemAccess()")}}