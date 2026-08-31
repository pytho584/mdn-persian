---
title: "AudioDestinationNode"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioDestinationNode"
translated_by: "n8n + AI"
---

---
title: AudioDestinationNode
slug: Web/API/AudioDestinationNode
page-type: web-api-interface
browser-compat: api.AudioDestinationNode
---

{{APIRef("Web Audio API")}}

رابط `AudioDestinationNode` نمایانگر مقصد نهایی یک گراف صوتی در یک زمینه (context) معین است — معمولاً بلندگوهای دستگاه شما. همچنین می‌تواند گره‌ای باشد که هنگام استفاده با `OfflineAudioContext` داده‌های صوتی را «ضبط» می‌کند.

`AudioDestinationNode` خروجی ندارد (زیرا خودش خروجی است و هیچ `AudioNode` دیگری نمی‌تواند بعد از آن در گراف صوتی متصل شود) و یک ورودی دارد. تعداد کانال‌های ورودی باید بین `0` و مقدار `maxChannelCount` باشد، در غیر این صورت استثنا ایجاد می‌شود.

برای دریافت `AudioDestinationNode` یک `AudioContext` معین، می‌توانید از ویژگی {{domxref("BaseAudioContext/destination", "AudioContext.destination")}} استفاده کنید.

{{InheritanceDiagram}}

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">Number of inputs</th>
      <td><code>1</code></td>
    </tr>
    <tr>
      <th scope="row">Number of outputs</th>
      <td><code>0</code></td>
    </tr>
    <tr>
      <th scope="row">Channel count mode</th>
      <td><code>"explicit"</code></td>
    </tr>
    <tr>
      <th scope="row">Channel count</th>
      <td><code>2</code></td>
    </tr>
    <tr>
      <th scope="row">Channel interpretation</th>
      <td><code>"speakers"</code></td>
    </tr>
  </tbody>
</table>

## ویژگی‌های نمونه

ویژگی‌های والد خود، {{domxref("AudioNode")}} را به ارث می‌برد.

- {{domxref("AudioDestinationNode.maxChannelCount")}}
  - : یک `unsigned long` که حداکثر تعداد کانال‌هایی را که دستگاه فیزیکی می‌تواند مدیریت کند، تعریف می‌کند.

## روش‌های نمونه

روش خاصی ندارد؛ روش‌های والد خود، {{domxref("AudioNode")}} را به ارث می‌برد.

## مثال

برای استفاده از `AudioDestinationNode` هیچ راه‌اندازی پیچیده‌ای لازم نیست — به‌طور پیش‌فرض، این گره خروجی سیستم کاربر (مثلاً بلندگوهایش) را نمایندگی می‌کند، بنابراین می‌توانید تنها با چند خط کد آن را در داخل گراف صوتی وصل کنید:

```js
const audioCtx = new AudioContext();
const source = audioCtx.createMediaElementSource(myMediaElement);
source.connect(gainNode);
gainNode.connect(audioCtx.destination);
```

برای مشاهده پیاده‌سازی کامل‌تر، یکی از مثال‌های Web Audio مازندرانی MDN را بررسی کنید، مانند [Voice-change-o-matic](https://mdn.github.io/webaudio-examples/voice-change-o-matic/) یا [Violent Theremin](https://github.com/mdn/webaudio-examples/tree/main/violent-theremin).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)