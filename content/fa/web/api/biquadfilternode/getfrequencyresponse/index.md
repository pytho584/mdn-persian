---
title: "BiquadFilterNode: getFrequencyResponse() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BiquadFilterNode/getFrequencyResponse"
translated_by: "n8n + AI"
---

---
title: "BiquadFilterNode: getFrequencyResponse() method"
short-title: getFrequencyResponse()
slug: Web/API/BiquadFilterNode/getFrequencyResponse
page-type: web-api-instance-method
browser-compat: api.BiquadFilterNode.getFrequencyResponse
---

{{ APIRef("Web Audio API") }}

متد `getFrequencyResponse()` از رابط {{ domxref("BiquadFilterNode")}} تنظیمات الگوریتم فیلتر فعلی را می‌گیرد و پاسخ فرکانسی را برای فرکانس‌های مشخص‌شده در یک آرایه معین از فرکانس‌ها محاسبه می‌کند.

دو آرایه خروجی، `magResponseOutput` و
`phaseResponseOutput`، باید قبل از فراخوانی این متد ایجاد شده باشند؛ آن‌ها
باید هم‌اندازه با آرایه مقادیر فرکانس ورودی
(`frequencyArray`) باشند.

## نحو

```js-nolint
getFrequencyResponse(frequencyArray, magResponseOutput, phaseResponseOutput)
```

### پارامترها

- `frequencyArray`
  - : یک {{jsxref("Float32Array")}} شامل آرایه‌ای از فرکانس‌ها، بر حسب هرتز،
    که می‌خواهید فیلتر کنید.
- `magResponseOutput`
  - : یک {{jsxref("Float32Array")}} برای دریافت اندازه‌های محاسبه‌شده پاسخ فرکانسی
    برای هر مقدار فرکانس در `frequencyArray`. برای هر
    فرکانس در `frequencyArray` که مقدار آن خارج از محدوده 0.0 تا
    `sampleRate`/2 باشد (که در آن {{domxref("BaseAudioContext/sampleRate", "sampleRate")}}
    نرخ نمونه‌برداری {{domxref("AudioContext")}} است)، مقدار متناظر در
    این آرایه {{jsxref("NaN")}} است. این مقادیر بدون واحد هستند.
- `phaseResponseOutput`
  - : یک {{jsxref("Float32Array")}} برای دریافت مقادیر پاسخ فاز محاسبه‌شده بر حسب
    رادیان برای هر مقدار فرکانس در `frequencyArray` ورودی. برای هر
    فرکانس در `frequencyArray` که مقدار آن خارج از محدوده 0.0 تا
    `sampleRate`/2 باشد (که در آن {{domxref("BaseAudioContext/sampleRate", "sampleRate")}}
    نرخ نمونه‌برداری {{domxref("AudioContext")}} است)، مقدار متناظر در
    این آرایه {{jsxref("NaN")}} است.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `InvalidAccessError`
  - : سه آرایه ارائه‌شده همگی طول یکسانی ندارند.

## مثال‌ها

در مثال زیر ما از یک فیلتر بایکواد روی یک جریان رسانه‌ای استفاده می‌کنیم (برای نسخه کامل،
دموی [stream-source-buffer](https://mdn.github.io/webaudio-examples/stream-source-buffer/) ما را ببینید، یا [متن منبع را بخوانید](https://github.com/mdn/webaudio-examples/blob/main/stream-source-buffer/index.html).) به عنوان بخشی از این دمو، پاسخ فرکانسی این فیلتر بایکواد را برای پنج فرکانس نمونه می‌گیریم. ابتدا {{jsxref("Float32Array")}}های مورد نیاز را ایجاد می‌کنیم، یکی شامل فرکانس‌های ورودی، و دو تا برای دریافت مقادیر خروجی اندازه و فاز:

```js
const myFrequencyArray = new Float32Array(5);
myFrequencyArray[0] = 1000;
myFrequencyArray[1] = 2000;
myFrequencyArray[2] = 3000;
myFrequencyArray[3] = 4000;
myFrequencyArray[4] = 5000;

const magResponseOutput = new Float32Array(5);
const phaseResponseOutput = new Float32Array(5);
```

سپس یک عنصر {{ htmlelement("ul") }} در HTML خود ایجاد می‌کنیم تا نتایج را در خود جای دهد،
و یک ارجاع به آن را در جاوااسکریپت خود می‌گیریم:

```html
<p>پاسخ فرکانسی فیلتر بایکواد برای:</p>
<ul class="freq-response-output"></ul>
```

```js
const freqResponseOutput = document.querySelector(".freq-response-output");
```

در نهایت، پس از ایجاد فیلتر بایکواد، از `getFrequencyResponse()`
برای تولید داده‌های پاسخ استفاده کرده و آن‌ها را در آرایه‌های خود قرار می‌دهیم، سپس هر مجموعه داده را پیمایش کرده
و آن‌ها را به صورت یک لیست قابل خواندن در پایین صفحه خروجی می‌دهیم:

```js
const biquadFilter = audioCtx.createBiquadFilter();
biquadFilter.type = "lowshelf";
biquadFilter.frequency.value = 1000;
biquadFilter.gain.value = range.value;

// …

function calcFrequencyResponse() {
  biquadFilter.getFrequencyResponse(
    myFrequencyArray,
    magResponseOutput,
    phaseResponseOutput,
  );

  for (let i = 0; i <= myFrequencyArray.length - 1; i++) {
    const listItem = document.createElement("li");
    listItem.textContent = `: اندازه ${magResponseOutput[i]}، فاز ${phaseResponseOutput[i]} رادیان.`;
    listItem.insertBefore(
      document.createElement("strong"),
      listItem.firstChild,
    ).textContent = `${myFrequencyArray[i]}Hz`;
    freqResponseOutput.appendChild(listItem);
  }
}

calcFrequencyResponse();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)