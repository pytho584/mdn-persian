---
title: "AudioBufferSourceNode: AudioBufferSourceNode() constructor"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioBufferSourceNode/AudioBufferSourceNode"
translated_by: "n8n + AI"
---

---
title: "AudioBufferSourceNode: AudioBufferSourceNode() constructor"
short-title: AudioBufferSourceNode()
slug: Web/API/AudioBufferSourceNode/AudioBufferSourceNode
page-type: web-api-constructor
browser-compat: api.AudioBufferSourceNode.AudioBufferSourceNode
---

{{APIRef("Web Audio API")}}

سازنده **`AudioBufferSourceNode()`** یک نمونه شیء جدید {{domxref("AudioBufferSourceNode")}} ایجاد می‌کند.

## نحو

```js-nolint
new AudioBufferSourceNode(context, options)
```

### پارامترها

- `context`
  - : ارجاعی به یک {{domxref("AudioContext")}}.
- `options` {{optional_inline}}
  - : گزینه‌ها به شرح زیر هستند:
    - `buffer`
      - : نمونه‌ای از {{domxref("AudioBuffer")}} که قرار است پخش شود.
    - `detune`
      - : مقداری بر حسب سنت برای تغییر سرعت رندر جریان صوتی. محدوده اسمی آن (∞- تا ∞+) است. مقدار پیش‌فرض `0` می‌باشد.
    - `loop`
      - : یک مقدار بولی که نشان می‌دهد آیا صدا به صورت حلقه پخش شود یا خیر. مقدار پیش‌فرض `false` است. اگر حلقه به صورت پویا در حین پخش تغییر کند، مقدار جدید در بلوک پردازش بعدی صدا اعمال می‌شود.
    - `loopEnd`
      - : یک مقدار اختیاری بر حسب ثانیه که مشخص می‌کند حلقه کجا باید پایان یابد اگر ویژگی `loop` برابر `true` باشد. مقدار پیش‌فرض `0` است. مقدار آن از محتوای حلقه مستثنی است. فریم‌های نمونه‌ای که حلقه را تشکیل می‌دهند، از مقادیر `loopStart` تا `loopEnd`-(1/`sampleRate`) اجرا می‌شوند. منطقی است که این مقدار را بین 0 و مدت زمان بافر تنظیم کنید. اگر `loopEnd` کمتر از 0 باشد، حلقه در 0 پایان می‌یابد. اگر `loopEnd` بیشتر از مدت زمان بافر باشد، حلقه در انتهای بافر پایان می‌یابد. این ویژگی با ضرب در نرخ نمونه بافر و گرد کردن به نزدیک‌ترین مقدار صحیح، به یک افست فریم نمونه دقیق در داخل بافر تبدیل می‌شود. بنابراین رفتار آن مستقل از مقدار پارامتر `playbackRate` است.
    - `loopStart`
      - : یک مقدار اختیاری بر حسب ثانیه که مشخص می‌کند حلقه کجا باید شروع شود اگر ویژگی `loop` برابر `true` باشد. مقدار پیش‌فرض `0` است. منطقی است که این مقدار را بین 0 و مدت زمان بافر تنظیم کنید. اگر `loopStart` کمتر از 0 باشد، حلقه از 0 شروع می‌شود. اگر `loopStart` بیشتر از مدت زمان بافر باشد، حلقه از انتهای بافر شروع می‌شود. این ویژگی با ضرب در نرخ نمونه بافر و گرد کردن به نزدیک‌ترین مقدار صحیح، به یک افست فریم نمونه دقیق در داخل بافر تبدیل می‌شود. بنابراین رفتار آن مستقل از مقدار پارامتر `playbackRate` است.
    - `playbackRate`
      - : سرعت رندر جریان صوتی. مقدار پیش‌فرض آن `1` است. این پارامتر از نوع k-rate است. این یک پارامتر ترکیبی با `detune` است. محدوده اسمی آن (∞- تا ∞+) می‌باشد.
    - `channelCount`
      - : یک عدد صحیح است که برای تعیین تعداد کانال‌ها هنگام [بالا-آمیختن و پایین-آمیختن](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#up-mixing_and_down-mixing) اتصالات به هر ورودی گره استفاده می‌شود. (برای اطلاعات بیشتر به {{domxref("AudioNode.channelCount")}} مراجعه کنید.) کاربرد و تعریف دقیق آن به مقدار `channelCountMode` بستگی دارد.
    - `channelCountMode`
      - : یک مقدار شمارشی است که نحوه تطبیق کانال‌ها بین ورودی‌ها و خروجی‌های گره را توصیف می‌کند. (برای اطلاعات بیشتر از جمله مقادیر پیش‌فرض به {{domxref("AudioNode.channelCountMode")}} مراجعه کنید.)
    - `channelInterpretation`
      - : یک مقدار شمارشی است که معنای کانال‌ها را توصیف می‌کند. این تفسیر نحوه انجام [بالا-آمیختن و پایین-آمیختن](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#up-mixing_and_down-mixing) صدا را تعیین می‌کند. مقادیر ممکن `"speakers"` یا `"discrete"` هستند. (برای اطلاعات بیشتر از جمله مقادیر پیش‌فرض به {{domxref("AudioNode.channelCountMode")}} مراجعه کنید.)

### مقدار بازگشتی

یک نمونه شیء جدید از {{domxref("AudioBufferSourceNode")}}.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}