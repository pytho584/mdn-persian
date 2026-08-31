---
title: "AudioNode: disconnect() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioNode/disconnect"
translated_by: "n8n + AI"
---

---
title: "AudioNode: disconnect() method"
short-title: disconnect()
slug: Web/API/AudioNode/disconnect
page-type: web-api-instance-method
browser-compat: api.AudioNode.disconnect
---

{{ APIRef("Web Audio API") }}

متد **`disconnect()`** از رابط {{ domxref("AudioNode") }} به شما امکان می‌دهد یک یا چند گره را از گره‌ای که متد روی آن فراخوانی می‌شود جدا کنید.

## سینتکس

```js-nolint
disconnect()
disconnect(output)
disconnect(destination)
disconnect(destination, output)
disconnect(destination, output, input)
```

### پارامترها

نسخه‌های مختلفی از متد `disconnect()` وجود دارند که ترکیب‌های متفاوتی از پارامترها را می‌پذیرند تا مشخص کنند کدام گره‌ها قطع شوند. اگر پارامتری ارائه نشود، همه اتصالات خروجی قطع می‌شوند.

- `destination` {{optional_inline}}
  - : یک {{domxref("AudioNode")}} یا {{domxref("AudioParam")}} که گره یا گره‌هایی را که باید از آن‌ها قطع شود مشخص می‌کند. اگر این مقدار یک `AudioNode` باشد، اتصال به یک گره قطع می‌شود و پارامترهای اختیاری دیگر (`output` و/یا `input`) بیشتر مشخص می‌کنند که کدام ورودی‌ها و/یا خروجی‌ها باید قطع شوند. اگر این مقدار یک `AudioParam` باشد، اتصال به آن `AudioParam` خاتمه می‌یابد و سهم گره در آن پارامتر محاسبه‌شده پس از اعمال تغییر، از آن پس صفر می‌شود.
- `output` {{optional_inline}}
  - : یک شاخص که مشخص می‌کند کدام خروجی از `AudioNode` فعلی باید قطع شود. شماره‌های شاخص بر اساس تعداد کانال‌های خروجی تعریف می‌شوند (برای جزئیات بیشتر به [کانال‌های صوتی](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#audio_channels) مراجعه کنید).
- `input` {{optional_inline}}
  - : یک شاخص که مشخص می‌کند کدام ورودی از `AudioNode` مقصد مشخص‌شده باید قطع شود. شماره‌های شاخص بر اساس تعداد کانال‌های ورودی تعریف می‌شوند (برای جزئیات بیشتر به [کانال‌های صوتی](/en-US/docs/Web/API/Web_Audio_API/Basic_concepts_behind_Web_Audio_API#audio_channels) مراجعه کنید). اگر `destination` یک `AudioParam` باشد، قابل اعمال نیست.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `IndexSizeError` {{domxref("DOMException")}}
  - : اگر مقدار مشخص‌شده برای `input` یا `output` نامعتبر باشد، به گره‌ای اشاره کند که وجود ندارد یا خارج از محدوده مجاز باشد، پرتاب می‌شود.
- `InvalidAccessError` {{domxref("DOMException")}}
  - : اگر گره‌ای که `disconnect()` روی آن فراخوانی شده است به گره `destination` مشخص‌شده متصل نباشد، پرتاب می‌شود.

## مثال‌ها

```js
const audioCtx = new AudioContext();

const oscillator = audioCtx.createOscillator();
const gainNode = audioCtx.createGain();

oscillator.connect(gainNode);
gainNode.connect(audioCtx.destination);

gainNode.disconnect();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)