---
title: "AudioBuffer: copyFromChannel() method"
short-title: copyFromChannel()
slug: Web/API/AudioBuffer/copyFromChannel
page-type: web-api-instance-method
browser-compat: api.AudioBuffer.copyFromChannel
translated_by: "n8n + AI"
---

{{APIRef("Web Audio API")}}

متد **`copyFromChannel()`** از رابط {{domxref("AudioBuffer")}} داده‌های نمونه صوتی را از کانال مشخص‌شده در `AudioBuffer` به یک {{jsxref("Float32Array")}} مشخص کپی می‌کند.

## نحو (Syntax)

```js-nolint
copyFromChannel(destination, channelNumber, startInChannel)
```

### پارامترها

- `destination`
  - : یک {{jsxref("Float32Array")}} که نمونه‌های کانال به آن کپی می‌شوند.
- `channelNumber`
  - : شماره کانال `AudioBuffer` فعلی که داده‌های کانال از آن کپی می‌شود.
- `startInChannel` {{optional_inline}}
  - : یک آفست اختیاری در بافر کانال مبدأ که کپی نمونه‌ها از آنجا آغاز می‌شود. اگر مشخص نشود، به‌طور پیش‌فرض مقدار 0 (آغاز بافر) در نظر گرفته می‌شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها (Exceptions)

- `indexSizeError`
  - : یکی از پارامترهای ورودی مقداری خارج از محدوده مجاز دارد:
    - مقدار `channelNumber` شماره کانالی را مشخص می‌کند که وجود ندارد (یعنی بزرگ‌تر یا مساوی مقدار {{domxref("AudioBuffer.numberOfChannels", "numberOfChannels")}} در کانال است).
    - مقدار `startInChannel` خارج از محدوده فعلی نمونه‌هایی است که در بافر مبدأ وجود دارند؛ یعنی بزرگ‌تر از {{domxref("AudioBuffer.length", "length")}} فعلی آن است.

## مثال‌ها

این مثال یک بافر صوتی جدید ایجاد می‌کند و سپس نمونه‌ها را از کانال دیگری به آن کپی می‌کند.

```js
const myArrayBuffer = audioCtx.createBuffer(2, frameCount, audioCtx.sampleRate);
const anotherArray = new Float32Array(length);
myArrayBuffer.copyFromChannel(anotherArray, 1, 0);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)