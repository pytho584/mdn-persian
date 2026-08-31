---
title: "BaseAudioContext"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BaseAudioContext"
translated_by: "n8n + AI"
slug: Web/API/BaseAudioContext
page-type: web-api-interface
browser-compat: api.BaseAudioContext
---

{{APIRef("Web Audio API")}}

رابط `BaseAudioContext` از [Web Audio API](/en-US/docs/Web/API/Web_Audio_API) به عنوان یک تعریف پایه برای گراف‌های پردازش صوتی آنلاین و آفلاین عمل می‌کند که به ترتیب توسط {{domxref("AudioContext")}} و {{domxref("OfflineAudioContext")}} نمایش داده می‌شوند. شما مستقیماً از `BaseAudioContext` استفاده نمی‌کنید – بلکه از ویژگی‌های آن از طریق یکی از این دو رابط ارث‌برنده استفاده می‌کنید.

یک `BaseAudioContext` می‌تواند هدف رویدادها باشد، بنابراین رابط {{domxref("EventTarget")}} را پیاده‌سازی می‌کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("BaseAudioContext.audioWorklet")}} {{ReadOnlyInline}} {{securecontext_inline}}
  - : شیء {{domxref("AudioWorklet")}} را برمی‌گرداند که می‌تواند برای ایجاد و مدیریت {{domxref("AudioNode")}}هایی استفاده شود که در آن‌ها کد جاوااسکریپت پیاده‌ساز رابط {{domxref("AudioWorkletProcessor")}} در پس‌زمینه برای پردازش داده‌های صوتی اجرا می‌شود.
- {{domxref("BaseAudioContext.currentTime")}} {{ReadOnlyInline}}
  - : یک عدد اعشاری double را برمی‌گرداند که نشان‌دهنده زمان سخت‌افزاری همواره در حال افزایش (برحسب ثانیه) برای زمان‌بندی است. این مقدار از `0` شروع می‌شود.
- {{domxref("BaseAudioContext.destination")}} {{ReadOnlyInline}}
  - : یک {{domxref("AudioDestinationNode")}} را برمی‌گرداند که مقصد نهایی تمام صداها در زمینه را نشان می‌دهد. می‌توان آن را به عنوان دستگاه رندر صدا در نظر گرفت.
- {{domxref("BaseAudioContext.listener")}} {{ReadOnlyInline}}
  - : شیء {{domxref("AudioListener")}} را برمی‌گرداند که برای فضایی‌سازی سه‌بعدی استفاده می‌شود.
- {{domxref("BaseAudioContext.sampleRate")}} {{ReadOnlyInline}}
  - : یک عدد اعشاری float را برمی‌گرداند که نشان‌دهنده نرخ نمونه‌برداری (برحسب نمونه در ثانیه) است که توسط همه گره‌ها در این زمینه استفاده می‌شود. نرخ نمونه‌برداری یک {{domxref("AudioContext")}} قابل تغییر نیست.
- {{domxref("BaseAudioContext.state")}} {{ReadOnlyInline}}
  - : وضعیت فعلی `AudioContext` را برمی‌گرداند.

## روش‌های نمونه

_همچنین روش‌هایی از رابط_ {{domxref("EventTarget")}} _را پیاده‌سازی می‌کند._

- {{domxref("BaseAudioContext.createAnalyser()")}}
  - : یک {{domxref("AnalyserNode")}} ایجاد می‌کند که می‌تواند برای نمایش داده‌های زمانی و فرکانسی صدا و مثلاً برای ایجاد تجسم‌های داده استفاده شود.
- {{domxref("BaseAudioContext.createBiquadFilter()")}}
  - : یک {{domxref("BiquadFilterNode")}} ایجاد می‌کند که یک فیلتر مرتبه دوم را نشان می‌دهد و می‌تواند به عنوان چندین نوع فیلتر رایج مختلف پیکربندی شود: بالاگذر، پایین‌گذر، میان‌گذر و غیره.
- {{domxref("BaseAudioContext.createBuffer()")}}
  - : یک شیء جدید و خالی از {{ domxref("AudioBuffer") }} ایجاد می‌کند که سپس می‌تواند با داده پر شود و از طریق یک {{ domxref("AudioBufferSourceNode") }} پخش شود.
- {{domxref("BaseAudioContext.createBufferSource()")}}
  - : یک {{domxref("AudioBufferSourceNode")}} ایجاد می‌کند که می‌تواند برای پخش و دستکاری داده‌های صوتی موجود در یک شیء {{ domxref("AudioBuffer") }} استفاده شود. {{ domxref("AudioBuffer") }}ها با استفاده از {{domxref("BaseAudioContext/createBuffer", "AudioContext.createBuffer()")}} ایجاد می‌شوند یا توسط {{domxref("BaseAudioContext/decodeAudioData", "AudioContext.decodeAudioData()")}} هنگامی که یک آهنگ صوتی را با موفقیت رمزگشایی می‌کند، بازگردانده می‌شوند.
- {{domxref("BaseAudioContext.createConstantSource()")}}
  - : یک شیء {{domxref("ConstantSourceNode")}} ایجاد می‌کند که یک منبع صوتی است که به طور پیوسته یک سیگنال صوتی مونو (یک کاناله) خروجی می‌دهد که همه نمونه‌های آن مقدار یکسانی دارند.
- {{domxref("BaseAudioContext.createChannelMerger()")}}
  - : یک {{domxref("ChannelMergerNode")}} ایجاد می‌کند که برای ترکیب کانال‌های چند جریان صوتی به یک جریان صوتی واحد استفاده می‌شود.
- {{domxref("BaseAudioContext.createChannelSplitter()")}}
  - : یک {{domxref("ChannelSplitterNode")}} ایجاد می‌کند که برای دسترسی به کانال‌های جداگانه یک جریان صوتی و پردازش جداگانه آن‌ها استفاده می‌شود.
- {{domxref("BaseAudioContext.createConvolver()")}}
  - : یک {{domxref("ConvolverNode")}} ایجاد می‌کند که می‌تواند برای اعمال اثرات کانولوشن به گراف صوتی شما، مثلاً یک اثر طنین، استفاده شود.
- {{domxref("BaseAudioContext.createDelay()")}}
  - : یک {{domxref("DelayNode")}} ایجاد می‌کند که برای تأخیر سیگنال صوتی ورودی به میزان معینی استفاده می‌شود. این گره همچنین برای ایجاد حلقه‌های بازخورد در یک گراف Web Audio API مفید است.
- {{domxref("BaseAudioContext.createDynamicsCompressor()")}}
  - : یک {{domxref("DynamicsCompressorNode")}} ایجاد می‌کند که می‌تواند برای اعمال فشرده‌سازی آکوستیک به یک سیگنال صوتی استفاده شود.
- {{domxref("BaseAudioContext.createGain()")}}
  - : یک {{domxref("GainNode")}} ایجاد می‌کند که می‌تواند برای کنترل حجم کلی گراف صوتی استفاده شود.
- {{domxref("BaseAudioContext.createIIRFilter()")}}
  - : یک {{domxref("IIRFilterNode")}} ایجاد می‌کند که یک فیلتر مرتبه دوم را نشان می‌دهد و می‌تواند به عنوان چندین نوع فیلتر رایج مختلف پیکربندی شود.
- {{domxref("BaseAudioContext.createOscillator()")}}
  - : یک {{domxref("OscillatorNode")}} ایجاد می‌کند، یک منبع که یک شکل موج دوره‌ای را نشان می‌دهد. اساساً یک تُن تولید می‌کند.
- {{domxref("BaseAudioContext.createPanner()")}}
  - : یک {{domxref("PannerNode")}} ایجاد می‌کند که برای فضایی‌سازی یک جریان صوتی ورودی در فضای سه‌بعدی استفاده می‌شود.
- {{domxref("BaseAudioContext.createPeriodicWave()")}}
  - : یک {{domxref("PeriodicWave")}} ایجاد می‌کند که برای تعریف یک شکل موج دوره‌ای استفاده می‌شود و می‌تواند برای تعیین خروجی یک {{ domxref("OscillatorNode") }} استفاده شود.
- {{domxref("BaseAudioContext.createScriptProcessor()")}} {{deprecated_inline}}
  - : یک {{domxref("ScriptProcessorNode")}} ایجاد می‌کند که می‌تواند برای پردازش مستقیم صدا از طریق جاوااسکریپت استفاده شود.
- {{domxref("BaseAudioContext.createStereoPanner()")}}
  - : یک {{domxref("StereoPannerNode")}} ایجاد می‌کند که می‌تواند برای اعمال پنینگ استریو به یک منبع صوتی استفاده شود.
- {{domxref("BaseAudioContext.createWaveShaper()")}}
  - : یک {{domxref("WaveShaperNode")}} ایجاد می‌کند که برای پیاده‌سازی اثرات اعوجاج غیرخطی استفاده می‌شود.
- {{domxref("BaseAudioContext.decodeAudioData()")}}
  - : داده‌های فایل صوتی موجود در یک {{jsxref("ArrayBuffer")}} را به صورت ناهمزمان رمزگشایی می‌کند. در این حالت، `ArrayBuffer` معمولاً از ویژگی `response` یک {{domxref("XMLHttpRequest")}} پس از تنظیم `responseType` به `arraybuffer` بارگذاری می‌شود. این روش فقط روی فایل‌های کامل کار می‌کند، نه قطعات فایل‌های صوتی.

## رویدادها

- {{domxref("BaseAudioContext.statechange_event", "statechange")}}
  - : هنگامی که وضعیت `AudioContext` به دلیل فراخوانی یکی از روش‌های تغییر وضعیت ({{domxref("AudioContext.suspend")}}، {{domxref("AudioContext.resume")}} یا {{domxref("AudioContext.close")}}) تغییر می‌کند، فعال می‌شود.

## مثال‌ها

```js
const audioContext = new AudioContext();

const oscillatorNode = audioContext.createOscillator();
const gainNode = audioContext.createGain();
const finish = audioContext.destination;
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- {{domxref("AudioContext")}}
- {{domxref("OfflineAudioContext")}}