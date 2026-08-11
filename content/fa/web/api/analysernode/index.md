---
title: "AnalyserNode"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AnalyserNode"
translated_by: "n8n + AI"
---

رابط **`AnalyserNode`** یک نود است که امکان تحلیل بلادرنگ فرکانس و حوزهٔ زمان را فراهم می‌کند. این نود از نوع {{domxref("AudioNode")}} است و جریان صدا را بدون تغییر از ورودی به خروجی منتقل می‌کند، اما به شما امکان می‌دهد داده‌های تولیدشده را بگیرید، پردازش کنید و از آن‌ها برای ساخت تصویرسازی‌های صوتی استفاده کنید.

یک `AnalyserNode` دقیقاً یک ورودی و یک خروجی دارد. این نود حتی اگر خروجی آن متصل نباشد نیز کار می‌کند.

![بدون تغییر در جریان صدا، این نود امکان دریافت داده‌های فرکانسی و حوزهٔ زمانی مرتبط با آن را با استفاده از FFT فراهم می‌کند.](fttaudiodata_en.svg)

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">تعداد ورودی‌ها</th>
      <td><code>1</code></td>
    </tr>
    <tr>
      <th scope="row">تعداد خروجی‌ها</th>
      <td><code>1</code> (می‌تواند متصل نباشد)</td>
    </tr>
    <tr>
      <th scope="row">حالت تعداد کانال</th>
      <td><code>"max"</code></td>
    </tr>
    <tr>
      <th scope="row">تعداد کانال</th>
      <td><code>2</code></td>
    </tr>
    <tr>
      <th scope="row">تفسیر کانال</th>
      <td><code>"speakers"</code></td>
    </tr>
  </tbody>
</table>

## سازنده

- {{domxref("AnalyserNode.AnalyserNode", "AnalyserNode()")}}
  - : یک نمونهٔ جدید از شیء `AnalyserNode` می‌سازد.

## ویژگی‌های نمونه

_ویژگی‌ها را از والد خود، {{domxref("AudioNode")}}، به ارث می‌برد._

- {{domxref("AnalyserNode.fftSize")}}
  - : یک عدد صحیح بدون علامت که اندازهٔ FFT ([Fast Fourier Transform](https://en.wikipedia.org/wiki/Fast_Fourier_transform)) را برای تعیین حوزهٔ فرکانس مشخص می‌کند.
- {{domxref("AnalyserNode.frequencyBinCount")}} {{ReadOnlyInline}}
  - : یک عدد صحیح بدون علامت برابر با نصف اندازهٔ FFT. این مقدار معمولاً برابر با تعداد داده‌هایی است که برای تصویرسازی در دسترس خواهید داشت.
- {{domxref("AnalyserNode.minDecibels")}}
  - : یک عدد اعشاری که حداقل مقدار توان در بازهٔ مقیاس‌بندی داده‌های تحلیل FFT را برای تبدیل به مقادیر بایت بدون علامت مشخص می‌کند — در واقع، حداقل مقدار بازهٔ نتایج هنگام استفاده از `getByteFrequencyData()` را تعیین می‌کند.
- {{domxref("AnalyserNode.maxDecibels")}}
  - : یک عدد اعشاری که حداکثر مقدار توان در بازهٔ مقیاس‌بندی داده‌های تحلیل FFT را برای تبدیل به مقادیر بایت بدون علامت مشخص می‌کند — در واقع، حداکثر مقدار بازهٔ نتایج هنگام استفاده از `getByteFrequencyData()` را تعیین می‌کند.
- {{domxref("AnalyserNode.smoothingTimeConstant")}}
  - : یک عدد اعشاری که ثابت میانگین‌گیری با آخرین frame تحلیل را مشخص می‌کند — در واقع، باعث می‌شود تغییر مقادیر در طول زمان نرم‌تر شود.

## متدهای نمونه

_متدها را از والد خود، {{domxref("AudioNode")}}، به ارث می‌برد._

- {{domxref("AnalyserNode.getFloatFrequencyData()")}}
  - : داده‌های فرکانسی جاری را در آرایهٔ {{jsxref("Float32Array")}} که به آن پاس داده می‌شود کپی می‌کند.
- {{domxref("AnalyserNode.getByteFrequencyData()")}}
  - : داده‌های فرکانسی جاری را در آرایهٔ {{jsxref("Uint8Array")}} (آرایهٔ بایت بدون علامت) که به آن پاس داده می‌شود کپی می‌کند.
- {{domxref("AnalyserNode.getFloatTimeDomainData()")}}
  - : شکل موج جاری یا داده‌های حوزهٔ زمان را در آرایهٔ {{jsxref("Float32Array")}} که به آن پاس داده می‌شود کپی می‌کند.
- {{domxref("AnalyserNode.getByteTimeDomainData()")}}
  - : شکل موج جاری یا داده‌های حوزهٔ زمان را در آرایهٔ {{jsxref("Uint8Array")}} (آرایهٔ بایت بدون علامت) که به آن پاس داده می‌شود کپی می‌کند.

## مثال‌ها

> [!NOTE]
> برای اطلاعات بیشتر دربارهٔ ساخت تصویرسازی‌های صوتی، راهنمای [Visualizations with Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Visualizations_with_Web_Audio_API) را ببینید.

### استفادهٔ پایه

مثال زیر روش پایه‌ای استفاده از `AudioContext` را برای ساخت یک `AnalyserNode` نشان می‌دهد، سپس از `requestAnimationFrame` و عنصر `<canvas>` برای دریافت مکرر داده‌های حوزه زمان و رسم خروجی شبیه به اسیلوسکوپ از ورودی صوتی جاری استفاده می‌کند.
برای مثال‌ها و اطلاعات کاربردی کامل‌تر، نسخه نمایشی [Voice-change-O-matic](https://mdn.github.io/webaudio-examples/voice-change-o-matic/) را ببینید (کد مربوطه در [خطوط ۱۰۸ تا ۱۹۳ فایل app.js](https://github.com/mdn/webaudio-examples/blob/main/voice-change-o-matic/scripts/app.js#L108-L193) قرار دارد).

```js
const audioCtx = new AudioContext();

// …

const analyser = audioCtx.createAnalyser();
analyser.fftSize = 2048;

const bufferLength = analyser.frequencyBinCount;
const dataArray = new Uint8Array(bufferLength);
analyser.getByteTimeDomainData(dataArray);

// Connect the source to be analyzed
source.connect(analyser);

// Get a canvas defined with ID "oscilloscope"
const canvas = document.getElementById("oscilloscope");
const canvasCtx = canvas.getContext("2d");

// draw an oscilloscope of the current audio source

function draw() {
  requestAnimationFrame(draw);

  analyser.getByteTimeDomainData(dataArray);

  canvasCtx.fillStyle = "rgb(200 200 200)";
  canvasCtx.fillRect(0, 0, canvas.width, canvas.height);

  canvasCtx.lineWidth = 2;
  canvasCtx.strokeStyle = "rgb(0 0 0)";

  canvasCtx.beginPath();

  const sliceWidth = (canvas.width * 1.0) / bufferLength;
  let x = 0;

  for (let i = 0; i < bufferLength; i++) {
    const v = dataArray[i] / 128.0;
    const y = (v * canvas.height) / 2;

    if (i === 0) {
      canvasCtx.moveTo(x, y);
    } else {
      canvasCtx.lineTo(x, y);
    }

    x += sliceWidth;
  }

  canvasCtx.lineTo(canvas.width, canvas.height / 2);
  canvasCtx.stroke();
}

draw();
```

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)