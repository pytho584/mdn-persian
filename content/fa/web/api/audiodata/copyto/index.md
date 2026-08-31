---
title: "AudioData: copyTo() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioData/copyTo"
translated_by: "n8n + AI"
---

---
title: "AudioData: copyTo() method"
short-title: copyTo()
slug: Web/API/AudioData/copyTo
page-type: web-api-instance-method
browser-compat: api.AudioData.copyTo
---

{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

متد **`copyTo()`** از رابط {{domxref("AudioData")}} یک پلن از یک شیء `AudioData` را در یک بافر مقصد کپی می‌کند.

## سینتکس

```js-nolint
copyTo(destination, options)
```

### پارامترها

- `destination`
  - : یک {{jsxref("ArrayBuffer")}}، یک {{jsxref("TypedArray")}} یا یک {{jsxref("DataView")}} که پلن به آن کپی می‌شود.
- `options`
  - : یک شیء که شامل موارد زیر است:
    - `planeIndex`
      - : شاخص پلنی که باید از آن کپی شود.
    - `frameOffset` {{optional_inline}}
      - : یک عدد صحیح که افست اولین فریمی که در داخل پلن کپی می‌شود را مشخص می‌کند. پیش‌فرض `0` است.
    - `frameCount` {{optional_inline}}
      - : یک عدد صحیح که تعداد فریم‌های قابل کپی را مشخص می‌کند. اگر حذف شود، همه فریم‌ها از `frameOffset` تا انتهای پلن کپی می‌شوند.
    - `format` {{optional_inline}}
      - : یک رشته که فرمت صوتی را مشخص می‌کند که نمونه‌های مبدأ هنگام کپی شدن به مقصد، به آن تبدیل شوند.
        این می‌تواند هر یک از مقادیر `"u8"`, `"s16"`, `"s32"`, `"f32"`, `"u8-planar"`, `"s16-planar"`, `"s32-planar"` و `"f32-planar"` باشد (برای اطلاعات بیشتر به {{domxref("AudioData.format")}} مراجعه کنید).
        توجه داشته باشید که `"f32-planar"` باید پشتیبانی شود.
        اگر حذف شود، نمونه‌ها در قالب خود `AudioData` کپی می‌شوند.

### مقدار بازگشتی

تعریف‌نشده.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر شیء `AudioData` [انتقال یافته](/en-US/docs/Web/API/Web_Workers_API/Transferable_objects) باشد، پرتاب می‌شود.
- {{jsxref("RangeError")}}
  - : اگر یکی از شرایط زیر برقرار باشد، پرتاب می‌شود:
    - طول نمونه از طول مقصد بیشتر باشد.
    - فرمت شیء `AudioData` یک فرمت پلانار را توصیف کند، اما `options.planeIndex` خارج از تعداد پلن‌های موجود باشد.
    - فرمت شیء `AudioData` یک فرمت درهم‌تنیده (interleaved) را توصیف کند، اما `options.planeIndex` بزرگ‌تر از `0` باشد.
- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر [`format`](#format) مشخص‌شده برای تبدیل داده‌ها پشتیبانی نشود، پرتاب می‌شود.

## مثال‌ها

مثال زیر پلن در شاخص `1` را در یک بافر مقصد کپی می‌کند.

```js
AudioData.copyTo(AudioBuffer, { planeIndex: 1 });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}