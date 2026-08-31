---
title: "AudioWorkletProcessor: process() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioWorkletProcessor/process"
translated_by: "n8n + AI"
---

---
title: "AudioWorkletProcessor: process() method"
short-title: process()
slug: Web/API/AudioWorkletProcessor/process
page-type: web-api-instance-method
spec-urls: https://webaudio.github.io/web-audio-api/#process
---

{{APIRef("Web Audio API")}}

متد **`process()`** از کلاس مشتق‌شده از {{domxref("AudioWorkletProcessor")}}، الگوریتم پردازش صوتی را برای worklet پردازنده صوتی پیاده‌سازی می‌کند.

اگرچه این متد بخشی از رابط {{domxref("AudioWorkletProcessor")}} نیست، هر پیاده‌سازی از `AudioWorkletProcessor` باید یک متد `process()` ارائه دهد.

این متد به‌صورت همزمان از رشته رندر صوتی، برای هر بلوک از صدا (که به عنوان یک کوانتوم رندر نیز شناخته می‌شود) که از طریق {{domxref("AudioWorkletNode")}} متناظر پردازنده هدایت می‌شود، فراخوانی می‌شود. به عبارت دیگر، هر بار که یک بلوک جدید از صدا آماده دستکاری توسط پردازنده شما است، تابع `process()` شما برای انجام این کار فراخوانی می‌شود.

> [!NOTE]
> در حال حاضر، بلوک‌های داده صوتی همیشه 128 فریم طول دارند—یعنی برای هر یک از کانال‌های ورودی، شامل 128 نمونه ممیز شناور 32 بیتی هستند. با این حال، برنامه‌هایی برای بازبینی مشخصات وجود دارد تا امکان تغییر اندازه بلوک‌های صوتی بسته به شرایط فراهم شود (به عنوان مثال، اگر سخت‌افزار صوتی یا استفاده از CPU با اندازه‌های بلوک بزرگ‌تر کارآمدتر باشد). بنابراین، شما _همیشه باید اندازه آرایه نمونه را بررسی کنید_ و اندازه خاصی را فرض نکنید.
>
> این اندازه حتی ممکن است در طول زمان تغییر کند، بنابراین نباید فقط به بلوک اول نگاه کنید و فرض کنید که بافرهای نمونه همیشه یک اندازه خواهند بود.

## نحو

```js-nolint
process(inputs, outputs, parameters)
```

### پارامترها

- `inputs`
  - : آرایه‌ای از _ورودی‌های_ متصل به گره، که هر آیتم آن به نوبه خود آرایه‌ای از _کانال‌ها_ است. هر _کانال_ یک {{jsxref("Float32Array")}} شامل 128 نمونه است. به عنوان مثال، `inputs[n][m][i]` به _n_-امین ورودی، _m_-امین کانال آن ورودی، و _i_-امین نمونه آن کانال دسترسی خواهد داشت.

    هر مقدار نمونه در محدوده `[-1 .. 1]` است.

    تعداد _ورودی‌ها_ و بنابراین طول آن آرایه در زمان ساخت گره ثابت است (به {{domxref("AudioWorkletNode")}} مراجعه کنید). اگر هیچ گره فعالی به _n_-امین ورودی گره متصل نباشد، `inputs[n]` یک آرایه خالی خواهد بود (صفر کانال ورودی در دسترس است).

    تعداد _کانال‌ها_ در هر ورودی ممکن است بسته به ویژگی‌های {{domxref("AudioNode.channelCount", "channelCount")}} و {{domxref("AudioNode.channelCountMode", "channelCountMode")}} متفاوت باشد.

- `outputs`
  - : آرایه‌ای از _خروجی‌ها_ که از نظر ساختار مشابه پارامتر `inputs` است. قرار است در طول اجرای متد `process()` پر شود. هر یک از کانال‌های خروجی به طور پیش‌فرض با صفر پر شده است—پردازنده سکوت را خروجی می‌دهد مگر اینکه آرایه‌های خروجی اصلاح شوند.
- `parameters`
  - : یک شیء حاوی کلیدهای رشته‌ای و مقادیر {{jsxref("Float32Array")}}. برای هر {{domxref("AudioParam")}} سفارشی که با استفاده از getter {{domxref("AudioWorkletProcessor.parameterDescriptors", "parameterDescriptors")}} تعریف شده است، کلید در شیء یک `name` از آن {{domxref("AudioParam")}} است و مقدار یک {{jsxref("Float32Array")}} است. مقادیر آرایه با در نظر گرفتن رویدادهای automation زمان‌بندی‌شده محاسبه می‌شوند.

    اگر نرخ automation پارامتر [`"a-rate"`](/en-US/docs/Web/API/AudioParam#a-rate) باشد، آرایه شامل 128 مقدار خواهد بود—یک مقدار برای هر فریم در بلوک صوتی فعلی. اگر در طول زمان نمایش‌داده‌شده توسط بلوک فعلی هیچ automation اتفاق نیفتد، آرایه ممکن است به جای 128 مقدار یکسان، یک مقدار واحد داشته باشد که برای کل بلوک ثابت است.

    اگر نرخ automation [`"k-rate"`](/en-US/docs/Web/API/AudioParam#k-rate) باشد، آرایه شامل یک مقدار واحد خواهد بود که برای هر یک از 128 فریم استفاده می‌شود.

### مقدار بازگشتی

یک مقدار بولی که نشان می‌دهد آیا {{domxref("AudioWorkletNode")}} حتی اگر منطق داخلی {{Glossary("user agent", "عامل کاربر")}} در غیر این صورت تصمیم بگیرد که خاموش کردن گره امن است، فعال بماند یا خیر.

مقدار بازگشتی به پردازنده شما اجازه می‌دهد بر سیاست طول عمر {{domxref("AudioWorkletProcessor")}} و گره‌ای که مالک آن است تأثیر بگذارد. اگر ترکیب مقدار بازگشتی و وضعیت گره باعث شود مرورگر تصمیم بگیرد گره را متوقف کند، `process()` دوباره فراخوانی نخواهد شد.

بازگرداندن `true` Web Audio API را مجبور می‌کند گره را زنده نگه دارد، در حالی که بازگرداندن `false` به مرورگر اجازه می‌دهد گره را خاتمه دهد اگر نه داده صوتی جدید تولید می‌کند و نه از طریق ورودی‌های خود داده‌ای که در حال پردازش است دریافت می‌کند.

3 نوع رایج گره صوتی عبارتند از:

1. منبع خروجی. یک {{domxref("AudioWorkletProcessor")}} که چنین گره‌ای را پیاده‌سازی می‌کند باید تا زمانی که خروجی تولید می‌کند، `true` را از متد `process` بازگرداند. به محض اینکه مشخص شد دیگر خروجی تولید نخواهد کرد، متد باید `false` بازگرداند. به عنوان مثال، {{domxref("AudioBufferSourceNode")}} را در نظر بگیرید—پردازنده پشت چنین گره‌ای باید در حالی که بافر در حال پخش است `true` را از متد `process` بازگرداند و وقتی پخش بافر به پایان رسید شروع به بازگرداندن `false` کند (هیچ راهی برای فراخوانی `play` روی همان {{domxref("AudioBufferSourceNode")}} دوباره وجود ندارد).
2. گره‌ای که ورودی خود را تبدیل می‌کند. پردازنده‌ای که چنین گره‌ای را پیاده‌سازی می‌کند باید `false` را از متد `process` بازگرداند تا وجود گره‌های ورودی فعال و ارجاعات به گره تعیین کند که آیا می‌توان آن را garbage-collect کرد. نمونه‌ای از گره با این رفتار {{domxref("GainNode")}} است. به محض اینکه هیچ ورودی متصل و ارجاع حفظ‌شده‌ای وجود نداشته باشد، بهره دیگر نمی‌تواند روی چیزی اعمال شود، بنابراین می‌توان آن را با خیال راحت garbage-collect کرد.
3. گره‌ای که ورودی خود را تبدیل می‌کند، اما دارای به اصطلاح _tail-time_ است—این بدان معنی است که برای مدتی حتی پس از قطع شدن یا غیرفعال شدن ورودی‌هایش (تولید صفر کانال) خروجی تولید می‌کند. پردازنده‌ای که چنین گره‌ای را پیاده‌سازی می‌کند باید در طول دوره _tail-time_، از همان لحظه‌ای که ورودی‌های حاوی صفر کانال پیدا می‌شوند، `true` را از متد `process` بازگرداند. نمونه‌ای از چنین گره‌ای {{domxref("DelayNode")}} است—دارای _tail-time_ برابر با ویژگی {{domxref("DelayNode.delayTime", "delayTime")}} خود است.

> [!NOTE]
> نبود دستور `return` به این معنی است که متد `undefined` بازمی‌گرداند، و چون این یک مقدار falsy است، مانند بازگرداندن `false` است. حذف یک دستور `return` صریح ممکن است مشکلاتی ایجاد کند که به سختی قابل تشخیص باشند.

### استثناها

از آنجا که متد `process()` توسط کاربر پیاده‌سازی می‌شود، می‌تواند هر چیزی پرتاب کند. اگر یک خطای uncaught پرتاب شود، گره یک رویداد {{domxref("AudioWorkletNode.processorerror_event", "processorerror")}} منتشر می‌کند و برای بقیه عمر خود سکوت را خروجی می‌دهد.

## مثال‌ها

در این مثال ما یک `AudioWorkletProcessor` ایجاد می‌کنیم که صدای سفید (white noise) را به اولین خروجی خود خروجی می‌دهد. بهره را می‌توان با پارامتر `customGain` کنترل کرد.

```js
class WhiteNoiseProcessor extends AudioWorkletProcessor {
  process(inputs, outputs, parameters) {
    // take the first output
    const output = outputs[0];
    // fill each channel with random values multiplied by gain
    output.forEach((channel) => {
      for (let i = 0; i < channel.length; i++) {
        // generate random value for each sample
        // Math.random range is [0; 1); we need [-1; 1]
        // this won't include exact 1 but is fine for now for simplicity
        channel[i] =
          (Math.random() * 2 - 1) *
          // the array can contain 1 or 128 values
          // depending on if the automation is present
          // and if the automation rate is k-rate or a-rate
          (parameters["customGain"].length > 1
            ? parameters["customGain"][i]
            : parameters["customGain"][0]);
      }
    });
    // as this is a source node which generates its own output,
    // we return true so it won't accidentally get garbage-collected
    // if we don't have any references to it in the main thread
    return true;
  }
  // define the customGain parameter used in process method
  static get parameterDescriptors() {
    return [
      {
        name: "customGain",
        defaultValue: 1,
        minValue: 0,
        maxValue: 1,
        automationRate: "a-rate",
      },
    ];
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

این یک متد ارائه‌شده توسط مرورگرها نیست، بلکه یک متد callback است که باید در کد کلاینت نوشته شود.

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)