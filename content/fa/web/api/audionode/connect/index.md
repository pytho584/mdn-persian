---
title: "AudioNode: connect() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioNode/connect"
translated_by: "n8n + AI"
---

---
title: "AudioNode: connect() method"
short-title: connect()
slug: Web/API/AudioNode/connect
page-type: web-api-instance-method
browser-compat: api.AudioNode.connect
---

{{ APIRef("Web Audio API") }}

روش `connect()` در رابط {{ domxref("AudioNode") }} به شما امکان می‌دهد یکی از خروجی‌های گره را به یک هدف متصل کنید، که می‌تواند یا یک `AudioNode` دیگر باشد (در نتیجه داده‌های صوتی را به گره مشخص‌شده هدایت می‌کند) یا یک {{domxref("AudioParam")}}، به‌طوری‌که داده‌های خروجی گره به‌طور خودکار برای تغییر مقدار آن پارامتر در طول زمان استفاده شود.

## سینتکس

```js-nolint
connect(destination)
connect(destination, outputIndex)
connect(destination, outputIndex, inputIndex)
```

### پارامترها

- `destination`
  - : مقصدی که به آن متصل می‌شود ({{domxref("AudioNode")}} یا {{domxref("AudioParam")}}).
- `outputIndex` {{optional_inline}}
  - : شاخصی که مشخص می‌کند کدام خروجی از `AudioNode` فعلی به مقصد متصل شود. شماره شاخص‌ها بر اساس تعداد کانال‌های خروجی تعریف می‌شوند (ببینید [Audio channels](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#audio_channels)). اگرچه می‌توانید فقط یک خروجی معین را به یک ورودی معین یک‌بار متصل کنید (تلاش‌های تکراری نادیده گرفته می‌شوند)، می‌توانید با فراخوانی مکرر `connect()` یک خروجی را به چندین ورودی متصل کنید. این امر [fan-out](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#fan-in_and_fan-out) را ممکن می‌سازد. مقدار پیش‌فرض 0 است.
- `inputIndex` {{optional_inline}}
  - : شاخصی که توصیف می‌کند می‌خواهید کدام ورودی از مقصد را به `AudioNode` فعلی متصل کنید؛ پیش‌فرض 0 است. شماره شاخص‌ها بر اساس تعداد کانال‌های ورودی تعریف می‌شوند (ببینید [Audio channels](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#audio_channels)). امکان اتصال یک `AudioNode` به یک `AudioNode` دیگر وجود دارد که به نوبه خود به `AudioNode` اول متصل می‌شود و یک چرخه ایجاد می‌کند.

### مقدار بازگشتی

اگر مقصد یک گره باشد، `connect()` یک ارجاع به شیء {{domxref("AudioNode")}} مقصد برمی‌گرداند و به شما امکان می‌دهد چندین فراخوانی `connect()` را زنجیره کنید. در برخی مرورگرها، پیاده‌سازی‌های قدیمی‌تر این رابط {{jsxref("undefined")}} برمی‌گردانند.

اگر مقصد یک `AudioParam` باشد، `connect()` مقدار `undefined` را برمی‌گرداند.

### استثناها

- `IndexSizeError` {{domxref("DOMException")}}
  - : اگر مقدار مشخص‌شده به‌عنوان `outputIndex` یا `inputIndex` با ورودی یا خروجی موجود مطابقت نداشته باشد، پرتاب می‌شود.
- `InvalidAccessError` {{domxref("DOMException")}}
  - : اگر گره مقصد بخشی از همان زمینه صوتی (audio context) گره مبدأ نباشد، پرتاب می‌شود.
- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر اتصال مشخص‌شده یک چرخه ایجاد کند (که در آن صدا به‌طور مکرر از طریق همان گره‌ها به عقب باز می‌گردد) و هیچ شیء {{domxref("DelayNode")}} در چرخه وجود نداشته باشد تا از گیر کردن شکل موج حاصل در ساخت همان قاب صوتی به‌طور نامحدود جلوگیری کند، پرتاب می‌شود. همچنین اگر پارامتر `inputIndex` در حالی استفاده شود که مقصد یک {{domxref("AudioParam")}} باشد، پرتاب می‌شود.

## مثال‌ها

### اتصال به یک ورودی صوتی

بارزترین کاربرد روش `connect()` هدایت خروجی صوتی از یک گره به ورودی صوتی گره دیگر برای پردازش بیشتر است. به عنوان مثال، ممکن است صدا را از یک {{domxref("MediaElementAudioSourceNode")}} — یعنی صدای یک عنصر رسانه‌ای HTML مانند {{HTMLElement("audio")}} — از طریق یک فیلتر باند گذر که با استفاده از {{domxref("BiquadFilterNode")}} پیاده‌سازی شده است ارسال کنید تا نویز کاهش یابد و سپس صدا را به بلندگوها بفرستید.

این مثال یک نوسان‌ساز (oscillator) ایجاد می‌کند و آن را به یک گره بهره (gain node) متصل می‌کند، به طوری که گره بهره صدای گره نوسان‌ساز را کنترل می‌کند.

```js
const audioCtx = new AudioContext();

const oscillator = audioCtx.createOscillator();
const gainNode = audioCtx.createGain();

oscillator.connect(gainNode);
gainNode.connect(audioCtx.destination);
```

### مثال با AudioParam

در این مثال، مقدار بهره یک {{domxref("GainNode")}} را با استفاده از یک {{domxref("OscillatorNode")}} با فرکانس پایین تغییر خواهیم داد. این تکنیک به عنوان پارامتر کنترل‌شده با _LFO_ شناخته می‌شود.

```js
const audioCtx = new AudioContext();

// create a normal oscillator to make sound
const oscillator = audioCtx.createOscillator();

// create a second oscillator that will be used as an LFO (Low-frequency
// oscillator), and will control a parameter
const lfo = audioCtx.createOscillator();

// set the frequency of the second oscillator to a low number
lfo.frequency.value = 2.0; // 2Hz: two oscillations per second

// create a gain whose gain AudioParam will be controlled by the LFO
const gain = audioCtx.createGain();

// connect the LFO to the gain AudioParam. This means the value of the LFO
// will not produce any audio, but will change the value of the gain instead
lfo.connect(gain.gain);

// connect the oscillator that will produce audio to the gain
oscillator.connect(gain);

// connect the gain to the destination so we hear sound
gain.connect(audioCtx.destination);

// start the oscillator that will produce audio
oscillator.start();

// start the oscillator that will modify the gain value
lfo.start();
```

#### نکات مربوط به AudioParam

امکان اتصال خروجی یک `AudioNode` به بیش از یک {{domxref("AudioParam")}} و همچنین اتصال خروجی بیش از یک AudioNode به یک {{domxref("AudioParam")}} با فراخوانی‌های متعدد `connect()` وجود دارد. بنابراین [Fan-in and fan-out](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#fan-in_and_fan-out) پشتیبانی می‌شوند.

یک {{ domxref("AudioParam") }} داده‌های صوتی رندر شده را از هر خروجی `AudioNode` متصل به خود می‌گیرد و آن را با [down-mixing](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#up-mixing_and_down-mixing) به مونو تبدیل می‌کند (اگر قبلاً مونو نباشد). سپس آن را با هر خروجی مشابه دیگر مخلوط می‌کند و همچنین مقدار پارامتر ذاتی (مقداری که {{ domxref("AudioParam") }} به طور معمول بدون هیچ اتصال صوتی دارد)، از جمله هر تغییر زمانی برنامه‌ریزی‌شده برای پارامتر را در نظر می‌گیرد.

بنابراین، می‌توان محدوده‌ای را که در آن یک {{domxref("AudioParam")}} تغییر می‌کند با تنظیم مقدار {{domxref("AudioParam")}} به فرکانس مرکزی انتخاب کرد و از یک {{domxref("GainNode")}} بین منبع صوتی و {{domxref("AudioParam")}} برای تنظیم محدوده تغییرات {{domxref("AudioParam")}} استفاده کرد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Using the Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)