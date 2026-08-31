---
title: "BaseAudioContext: createPeriodicWave() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BaseAudioContext/createPeriodicWave"
translated_by: "n8n + AI"
---

---
title: "BaseAudioContext: createPeriodicWave() method"
short-title: createPeriodicWave()
slug: Web/API/BaseAudioContext/createPeriodicWave
page-type: web-api-instance-method
browser-compat: api.BaseAudioContext.createPeriodicWave
---

{{ APIRef("Web Audio API") }}

متد `createPeriodicWave()` از رابط {{ domxref("BaseAudioContext") }} برای ایجاد یک {{domxref("PeriodicWave")}} استفاده می‌شود. این موج برای تعریف یک شکل‌موج متناوب استفاده می‌شود که می‌تواند برای شکل‌دهی به خروجی یک {{ domxref("OscillatorNode") }} به کار رود.

## نحو

```js-nolint
createPeriodicWave(real, imag)
createPeriodicWave(real, imag, constraints)
```

### پارامترها

- `real`
  - آرایه‌ای از عبارت‌های کسینوسی (به طور سنتی عبارت‌های A).
- `imag`
  - آرایه‌ای از عبارت‌های سینوسی (به طور سنتی عبارت‌های B).

آرایه‌های `real` و `imag` باید طول یکسانی داشته باشند، در غیر این صورت یک خطا پرتاب می‌شود.

- `constraints` {{optional_inline}}
  - یک شیء دیکشنری که مشخص می‌کند آیا نرمال‌سازی باید غیرفعال شود یا خیر. اگر مشخص نشود، نرمال‌سازی به طور پیش‌فرض فعال است. این شیء یک ویژگی دارد:
    - `disableNormalization`
      - اگر روی `true` تنظیم شود، نرمال‌سازی برای موج متناوب غیرفعال می‌شود. مقدار پیش‌فرض `false` است.

> [!NOTE]
> اگر نرمال‌سازی انجام شود، موج حاصل حداکثر مقدار قله مطلق ۱ را خواهد داشت.

### مقدار بازگشتی

یک {{domxref("PeriodicWave")}}.

## مثال‌ها

مثال زیر کاربرد ساده `createPeriodicWave()` را برای ایجاد یک شیء {{domxref("PeriodicWave")}} حاوی یک موج سینوسی ساده نشان می‌دهد.

```js
const real = new Float32Array(2);
const imag = new Float32Array(2);
const ac = new AudioContext();
const osc = ac.createOscillator();

real[0] = 0;
imag[0] = 0;
real[1] = 1;
imag[1] = 0;

const wave = ac.createPeriodicWave(real, imag, { disableNormalization: true });

osc.setPeriodicWave(wave);

osc.connect(ac.destination);

osc.start();
osc.stop(2);
```

این کار می‌کند زیرا صدایی که فقط یک تُن بنیادی دارد، بنا به تعریف یک موج سینوسی است.

در اینجا، یک `PeriodicWave` با دو مقدار ایجاد می‌کنیم. مقدار اول، آفست DC است، یعنی مقداری که نوسانگر از آن شروع می‌شود. مقدار `0` در اینجا مناسب است، زیرا منحنی را از وسط بازه `[-1.0; 1.0]` شروع می‌کند. مقدار دوم و مقادیر بعدی، مؤلفه‌های سینوسی و کسینوسی هستند، مشابه نتیجه تبدیل فوریه که مقادیر حوزه زمان را به مقادیر حوزه فرکانس تبدیل می‌کند. در اینجا، با `createPeriodicWave()`، فرکانس‌ها را مشخص می‌کنید و مرورگر یک تبدیل فوریه معکوس انجام می‌دهد تا یک بافر حوزه زمان برای فرکانس نوسانگر به دست آورد. در این مثال، فقط یک مؤلفه را با حجم کامل (`1.0`) روی تُن بنیادی تنظیم می‌کنیم، بنابراین یک موج سینوسی به دست می‌آوریم. به خاطر داشته باشید که تُن بنیادی با فرکانس نوسانگر (که به طور پیش‌فرض `440 Hz` است) مطابقت دارد. بنابراین، تغییر فرکانس نوسانگر به طور مؤثر فرکانس این موج متناوب را نیز همراه با آن تغییر می‌دهد.

ضرایب تبدیل فوریه باید به ترتیب _صعودی_ داده شوند (یعنی، <math><semantics><mrow><mrow><mo>(</mo><mrow><mi>a</mi><mo>+</mo><mi>b</mi><mi>i</mi></mrow><mo>)</mo></mrow><msup><mi>e</mi><mi>i</mi></msup><mo>,</mo><mrow><mo>(</mo><mrow><mi>c</mi><mo>+</mo><mi>d</mi><mi>i</mi></mrow><mo>)</mo></mrow><msup><mi>e</mi><mrow><mn>2</mn><mi>i</mi></mrow></msup><mo>,</mo><mrow><mo>(</mo><mrow><mi>f</mi><mo>+</mo><mi>g</mi><mi>i</mi></mrow><mo>)</mo></mrow><msup><mi>e</mi><mrow><mn>3</mn><mi>i</mi></mrow></msup></mrow><annotation encoding="TeX">\left(a+bi\right)e^{i} , \left(c+di\right)e^{2i} ,\left(f+gi\right)e^{3i} </annotation></semantics></math> و غیره) و می‌توانند مثبت یا منفی باشند. یک راه ساده برای به دست آوردن دستی این ضرایب (اگرچه بهترین راه نیست) استفاده از ماشین‌حساب نموداری است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)