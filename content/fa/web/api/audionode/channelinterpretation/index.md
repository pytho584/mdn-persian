---
title: "AudioNode: channelInterpretation property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioNode/channelInterpretation"
short-title: channelInterpretation
slug: Web/API/AudioNode/channelInterpretation
page-type: web-api-instance-property
browser-compat: api.AudioNode.channelInterpretation
translated_by: "n8n + AI"
---

{{ APIRef("Web Audio API") }}

ویژگی **`channelInterpretation`** از رابط {{domxref("AudioNode")}} یک مقدار شمارشی را نشان می‌دهد که نحوه نگاشت کانال‌های ورودی به کانال‌های خروجی را هنگامی که تعداد ورودی‌ها/خروجی‌ها متفاوت است، توصیف می‌کند. به عنوان مثال، این تنظیم مشخص می‌کند که چگونه یک ورودی مونو به خروجی استریو یا 5.1 کاناله up-mix می‌شود، یا چگونه یک ورودی چهار کاناله به خروجی استریو یا مونو down-mix می‌شود.

این ویژگی دو گزینه دارد: `speakers` و `discrete`. این موارد در [مفاهیم پایه پشت Web Audio API > up-mixing و down-mixing](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#up-mixing_and_down-mixing) مستند شده‌اند.

## مقدار

مقادیر در [مفاهیم پایه پشت Web Audio API > up-mixing و down-mixing](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#up-mixing_and_down-mixing) مستند شده‌اند.

به طور خلاصه:

- `speakers`
  - : از مجموعه‌ای از نگاشت‌های «استاندارد» برای ترکیب‌های تنظیمات رایج بلندگوهای ورودی و خروجی (مونو، استریو، چهارکاناله، 5.1) استفاده می‌کند. به عنوان مثال، با این تنظیم، یک ورودی کانال مونو به هر دو کانال خروجی استریو خروجی می‌دهد.
- `discrete`
  - : کانال‌های ورودی به ترتیب به کانال‌های خروجی نگاشت می‌شوند. اگر تعداد ورودی‌ها بیشتر از خروجی‌ها باشد، ورودی‌های اضافی حذف می‌شوند؛ اگر تعداد کمتر باشد، خروجی‌های استفاده نشده ساکت هستند.

## مثال‌ها

```js
const audioCtx = new AudioContext();

const oscillator = audioCtx.createOscillator();
const gainNode = audioCtx.createGain();

oscillator.connect(gainNode);
gainNode.connect(audioCtx.destination);

oscillator.channelInterpretation = "discrete";
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)