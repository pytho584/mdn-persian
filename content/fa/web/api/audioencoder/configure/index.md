---
title: "AudioEncoder: configure() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioEncoder/configure"
translated_by: "n8n + AI"
---

---
title: "AudioEncoder: configure() method"
short-title: configure()
slug: Web/API/AudioEncoder/configure
page-type: web-api-instance-method
browser-compat: api.AudioEncoder.configure
---

{{securecontext_header}}{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

متد **`configure()`** از رابط {{domxref("AudioEncoder")}} یک پیام کنترلی را برای پیکربندی رمزگذار صوتی جهت رمزگذاری تکه‌ها در صف قرار می‌دهد.

## سینتکس

```js-nolint
configure(config)
```

### پارامترها

- `config`
  - : یک شیء دیکشنری شامل اعضای زیر:
    - `codec`
      - : یک رشته حاوی [valid codec string](https://w3c.github.io/webcodecs/codec_registry.html#audio-codec-registry). برای جزئیات ساخت رشته کدک، به ["codecs" parameter](/en-US/docs/Web/Media/Guides/Formats/codecs_parameter#codec_options_by_container) مراجعه کنید.
    - `sampleRate`
      - : یک عدد صحیح که تعداد نمونه‌های فریم در هر ثانیه را نشان می‌دهد.
    - `numberOfChannels`
      - : یک عدد صحیح که تعداد کانال‌های صوتی را نشان می‌دهد.
    - `bitrate` {{optional_inline}}
      - : یک عدد صحیح که نرخ بیت را نشان می‌دهد.
    - `bitrateMode` {{optional_inline}}
      - : یک مقدار شمارشی که حالت نرخ بیت مورد استفاده رمزگذار را تعیین می‌کند. مقادیر ممکن عبارتند از:
        - `"constant"`
          - : رمزگذار صوتی را مجبور می‌کند تا بدون توجه به محتوای صوتی، همان نرخ بیت را حفظ کند. این می‌تواند زمانی مفید باشد که مصرف پهنای باند قابل پیش‌بینی ترجیح داده شود.
        - `"variable"` (پیش‌فرض)
          - : به رمزگذار صوتی اجازه می‌دهد تا نرخ بیت خود را بر اساس محتوای صوتی که در حال رمزگذاری آن است افزایش یا کاهش دهد، تا پهنای باند/حجم باینری حفظ شود، در حالی که همچنان کیفیت هدف حفظ می‌شود. به عنوان مثال، یک رمزگذار ممکن است هنگام رمزگذاری سکوت، نرخ بیت را کاهش دهد و هنگام رمزگذاری گفتار به نرخ بیت کامل بازگردد.

        پیاده‌سازی‌های خاص رمزگذار کدک ممکن است از اصطلاحات کمی متفاوت استفاده کنند (مثلاً CBR در مقابل VBR برای Opus)، اما همه آن‌ها باید به مفهوم کلی نرخ بیت «ثابت» در مقابل «متغیر» نگاشت شوند.

    - `opus` {{optional_inline}}
      - : گزینه‌های پیکربندی کدک مخصوص کدک Opus را مشخص می‌کند. مقدار آن یک شیء `OpusEncoderConfig` است که ویژگی‌های ممکن آن به شرح زیر است:
        - `application` {{optional_inline}}
          - : یک مقدار شمارشی که نوع کاربرد مورد نظر رمزگذار را مشخص می‌کند. مقادیر ممکن عبارتند از:
            - `audio` (پیش‌فرض)
              - : پردازش سیگنال به‌طور وفادارانه نسبت به ورودی اصلی.
            - `lowdelay`
              - : هنگام پردازش سیگنال، با غیرفعال کردن برخی حالت‌های عملیاتی، حداقل تأخیر ممکن رمزگذاری را پیکربندی می‌کند.
            - `voip`
              - : پردازش سیگنال برای بهبود وضوح گفتار.
        - `complexity` {{optional_inline}}
          - : عددی که پیچیدگی محاسباتی رمزگذار را بر اساس جنبه‌های شرح داده شده در بخش [RFC6716, 2.1.5. — Complexity](https://www.rfc-editor.org/info/rfc6716/#section-2.1.5) تعریف می‌کند. محدوده معتبر از 0 تا 10 است که 10 بالاترین پیچیدگی را نشان می‌دهد. اگر مقداری مشخص نشود، مقدار پیش‌فرض به پلتفرم بستگی دارد؛ مشخصات برای پلتفرم‌های موبایل 5 و برای سایر پلتفرم‌ها 9 را توصیه می‌کند.
        - `format` {{optional_inline}}
          - : یک مقدار شمارشی که قالبی را مشخص می‌کند که رمزگذار باید {{domxref("EncodedAudioChunk")}}ها را در آن خروجی دهد. مقادیر ممکن عبارتند از:
            - `opus` (پیش‌فرض)
              - : خروجی `EncodedAudioChunk`ها در قالب Opus. در این حالت، برای رمزگشایی جریان صوتی رمزگذاری‌شده هیچ فراداده‌ای لازم نیست.
            - `ogg`
              - : خروجی `EncodedAudioChunk`ها در قالب Ogg. در این حالت، برای رمزگشایی جریان صوتی رمزگذاری‌شده هیچ فراداده‌ای لازم نیست. در این حالت، فراداده‌های جریان صوتی رمزگذاری‌شده در پیکربندی رمزگشا — از طریق ویژگی [`description`](/en-US/docs/Web/API/AudioDecoder/configure#description) شیء پیکربندی که به {{domxref("AudioDecoder.configure()")}} منتقل می‌شود — ارائه می‌شوند.
        - `frameDuration` {{optional_inline}}
          - : عددی که مدت زمان فریم، به میکروثانیه، `EncodedAudioChunk`های خروجی رمزگذار را تعریف می‌کند. اگر مشخص نشود، `frameDuration` به طور پیش‌فرض `20000` است.
        - `packetlossperc` {{optional_inline}}
          - : عددی که درصد از دست رفتن بسته مورد انتظار رمزگذار را تعریف می‌کند. محدوده معتبر از 0 تا 100 است. اگر مشخص نشود، `packetlossperc` به طور پیش‌فرض `0` است.
        - `signal` {{optional_inline}}
          - : یک مقدار شمارشی که مقدار پیش‌فرض نوع سیگنال صوتی در حال رمزگذاری را مشخص می‌کند. مقادیر ممکن عبارتند از:
            - `auto` (پیش‌فرض)
              - : سیگنال صوتی به عنوان نوع خاصی مشخص نشده است.
            - `music`
              - : سیگنال صوتی موسیقی است.
            - `voice`
              - : سیگنال صوتی صدا یا گفتار است.
        - `usedtx` {{optional_inline}}
          - : یک مقدار بولی که مشخص می‌کند آیا رمزگذار از انتقال ناپیوسته (DTX) استفاده می‌کند یا خیر، که نرخ بیت را در طول سکوت یا نویز پس‌زمینه کاهش می‌دهد. وقتی DTX فعال باشد، فقط یک فریم هر 400 میلی‌ثانیه رمزگذاری می‌شود. اگر مشخص نشود، `usedtx` به طور پیش‌فرض `false` است.
        - `useinbandfec` {{optional_inline}}
          - : یک مقدار بولی که مشخص می‌کند آیا رمزگذار تصحیح خطای پیشرو (FEC) درون‌باند Opus را ارائه می‌کند یا خیر. این باعث می‌شود بسته‌هایی که مشخص شده حاوی اطلاعات گفتاری مهم ادراکی هستند — مانند شروع‌ها یا گذراها — با نرخ بیت پایین‌تر دوباره رمزگذاری شده و به بسته بعدی اضافه شوند. اگر مشخص نشود، `useinbandfec` به طور پیش‌فرض `false` است.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- {{jsxref("TypeError")}}
  - : اگر `config` ارائه‌شده نامعتبر باشد پرتاب می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر {{domxref("AudioEncoder.state","state")}} برابر با `"closed"` باشد پرتاب می‌شود.
- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر `config` ارائه‌شده معتبر باشد اما عامل کاربر نتواند کدکی را ارائه دهد که بتواند این پروفایل را رمزگشایی کند، پرتاب می‌شود.

## مثال‌ها

### مثال پیکربندی پایه

مثال زیر یک {{domxref("AudioEncoder")}} جدید ایجاد می‌کند و آن را با برخی از گزینه‌های موجود پیکربندی می‌کند.

```js
const init = {
  output: handleOutput,
  error(e) {
    console.log(e.message);
  },
};

let config = {
  codec: "mp3",
  sampleRate: 44100,
  numberOfChannels: 2,
  bitrate: 128_000, // 128 kbps
  bitrateMode: "constant",
};

let encoder = new AudioEncoder(init);
encoder.configure(config);
```

### مثال پیکربندی مخصوص Opus

مثال زیر یک {{domxref("AudioEncoder")}} جدید ایجاد می‌کند و آن را با گزینه‌های مخصوص Opus پیکربندی می‌کند.

```js
const init = {
  output: handleOutput,
  error(e) {
    console.log(e.message);
  },
};

let opusConfig = {
  application: "voip",
  complexity: 9,
  signal: "voice",
  usedtx: true,
};

let config = {
  codec: "opus",
  sampleRate: 44100,
  numberOfChannels: 2,
  bitrate: 128_000,
  opus: opusConfig,
};

let encoder = new AudioEncoder(init);
encoder.configure(config);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}