---
title: "OscillatorNode: setPeriodicWave() method"
short-title: setPeriodicWave()
slug: Web/API/OscillatorNode/setPeriodicWave
page-type: web-api-instance-method
browser-compat: api.OscillatorNode.setPeriodicWave
---

{{ APIRef("Web Audio API") }}

متد **`setPeriodicWave()`** در رابط {{domxref("OscillatorNode")}} برای اشاره به یک {{domxref("PeriodicWave")}} استفاده می‌شود که شکل موج دوره‌ای را تعریف می‌کند و هنگامی که {{domxref("OscillatorNode.type", "type")}} برابر با `custom` باشد، برای شکل‌دهی به خروجی نوسان‌ساز به کار می‌رود.

## نحو (Syntax)

```js-nolint
setPeriodicWave(wave)
```

### پارامترها

- `wave`
  - : یک شیء {{domxref("PeriodicWave")}} که نشان‌دهندهٔ شکل موج مورد استفاده برای شکل خروجی نوسان‌ساز است.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

مثال زیر کاربرد سادهٔ `createPeriodicWave()` را نشان می‌دهد و یک موج سینوسی را از یک موج دوره‌ای بازسازی می‌کند.

```js
const real = new Float32Array(2);
const imag = new Float32Array(2);
const ac = new AudioContext();
const osc = ac.createOscillator();

real[0] = 0;
imag[0] = 0;
real[1] = 1;
imag[1] = 0;

const wave = ac.createPeriodicWave(real, imag);

osc.setPeriodicWave(wave);

osc.connect(ac.destination);

osc.start();
osc.stop(2);
```

این کار درست است، زیرا صدایی که فقط شامل یک تون اصلی (fundamental tone) باشد، ذاتاً یک موج سینوسی است.

در اینجا، یک {{domxref("PeriodicWave")}} با دو مقدار ایجاد می‌کنیم. مقدار اول، آفست DC است؛ یعنی مقداری که نوسان‌ساز از آن شروع می‌شود. صفر در اینجا مناسب است، زیرا می‌خواهیم منحنی را از وسط بازهٔ \[-1.0; 1.0] شروع کنیم.

مقدار دوم و مقادیر بعدی، مؤلفه‌های سینوسی و کسینوسی هستند. می‌توانید آن را به‌عنوان نتیجهٔ تبدیل فوریه در نظر بگیرید، جایی که از مقادیر حوزهٔ زمان، مقادیر حوزهٔ فرکانس به دست می‌آورید. در اینجا، با `createPeriodicWave()` فرکانس‌ها را مشخص می‌کنید و مرورگر یک تبدیل فوریهٔ معکوس انجام می‌دهد تا بافری در حوزهٔ زمان برای فرکانس نوسان‌ساز به دست آورد. در این مثال، ما فقط یک مؤلفه را با حجم کامل (1.0) روی تون اصلی تنظیم کرده‌ایم، بنابراین یک موج سینوسی به دست می‌آید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- [AudioContext.createPeriodicWave](/en-US/docs/Web/API/BaseAudioContext/createPeriodicWave)