---
title: "IIRFilterNode: getFrequencyResponse() method"
short-title: getFrequencyResponse()
slug: Web/API/IIRFilterNode/getFrequencyResponse
page-type: web-api-instance-method
browser-compat: api.IIRFilterNode.getFrequencyResponse
---

{{ APIRef("Web Audio API") }}

متد `getFrequencyResponse()` از رابط {{ domxref("IIRFilterNode") }} تنظیمات فعلی الگوریتم فیلتر را گرفته و پاسخ فرکانسی را برای فرکانس‌های مشخص‌شده در یک آرایه‌ی فرکانسی معین محاسبه می‌کند.

دو آرایه‌ی خروجی، `magResponseOutput` و `phaseResponseOutput`، باید پیش از فراخوانی این متد ساخته شده باشند؛ اندازه‌ی آن‌ها باید با آرایه‌ی مقادیر فرکانس ورودی (`frequencyArray`) یکسان باشد.

## سینتکس

```js-nolint
getFrequencyResponse(frequencyArray, magResponseOutput, phaseResponseOutput)
```

### پارامترها

- `frequencyArray`
  - : یک {{jsxref("Float32Array")}} شامل آرایه‌ای از فرکانس‌ها بر حسب هرتز که می‌خواهید فیلتر کنید.
- `magResponseOutput`
  - : یک {{jsxref("Float32Array")}} برای دریافت بزرگی‌های محاسبه‌شده‌ی پاسخ فرکانسی برای هر مقدار فرکانس در `frequencyArray`.
- `phaseResponseOutput`
  - : یک {{jsxref("Float32Array")}} برای دریافت مقادیر پاسخ فاز محاسبه‌شده بر حسب رادیان برای هر مقدار فرکانس در `frequencyArray` ورودی.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر طول هر سه آرایه‌ی ارائه‌شده یکسان نباشد، این خطا پرتاب می‌شود.

## مثال‌ها

در مثال زیر، از یک فیلتر IIR روی یک جریان رسانه‌ای استفاده می‌کنیم (برای مشاهده‌ی کامل دمو، [دموی stream-source-buffer](https://mdn.github.io/webaudio-examples/stream-source-buffer/) را به‌صورت زنده ببینید یا [کد منبع آن را بخوانید](https://github.com/mdn/webaudio-examples/blob/main/stream-source-buffer/index.html)). به‌عنوان بخشی از این دمو، پاسخ فرکانسی این فیلتر IIR را برای پنج فرکانس نمونه به دست می‌آوریم. ابتدا اشیاء {{jsxref("Float32Array")}} موردنیاز را می‌سازیم؛ یکی شامل فرکانس‌های ورودی و دو تای دیگر برای دریافت مقادیر خروجی بزرگی و فاز:

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

سپس یک عنصر {{ htmlelement("ul") }} در HTML خود برای نمایش نتایج ایجاد می‌کنیم و ارجاع آن را در جاوااسکریپت می‌گیریم:

```html
<p>IIR filter frequency response for:</p>
<ul class="freq-response-output"></ul>
```

```js
const freqResponseOutput = document.querySelector(".freq-response-output");
```

در نهایت، پس از ایجاد فیلتر، از `getFrequencyResponse()` برای تولید داده‌های پاسخ استفاده می‌کنیم و آن‌ها را در آرایه‌هایمان قرار می‌دهیم؛ سپس هر مجموعه داده را پیمایش کرده و به‌صورت فهرستی قابل‌خواندن در انتهای صفحه نمایش می‌دهیم:

```js
const feedforwardCoefficients = [0.1, 0.2, 0.3, 0.4, 0.5];
const feedbackCoefficients = [0.5, 0.4, 0.3, 0.2, 0.1];

const iirFilter = audioCtx.createIIRFilter(
  feedforwardCoefficients,
  feedbackCoefficients,
);

// …

function calcFrequencyResponse() {
  iirFilter.getFrequencyResponse(
    myFrequencyArray,
    magResponseOutput,
    phaseResponseOutput,
  );

  for (let i = 0; i < myFrequencyArray.length; i++) {
    const listItem = document.createElement("li");
    listItem.textContent = `${myFrequencyArray[i]}Hz: Magnitude ${magResponseOutput[i]}, Phase ${phaseResponseOutput[i]} radians.`;
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
- {{domxref("IIRFilterNode")}}
- {{domxref("AudioNode")}}