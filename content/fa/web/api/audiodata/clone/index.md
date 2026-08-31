---
title: "AudioData: clone() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioData/clone"
translated_by: "n8n + AI"
---

---
title: "AudioData: clone() method"
short-title: clone()
slug: Web/API/AudioData/clone
page-type: web-api-instance-method
browser-compat: api.AudioData.clone
---

{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

متد **`clone()`** در رابط {{domxref("AudioData")}} یک شیء `AudioData` جدید ایجاد می‌کند که به همان منبع رسانه‌ای شیء اصلی ارجاع می‌دهد.

## سینتکس

```js-nolint
clone()
```

### پارامترها

هیچ.

### مقدار بازگشتی

شیء {{domxref("AudioData")}} کلون‌شده.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر شیء `AudioData` [انتقال](/en-US/docs/Web/API/Web_Workers_API/Transferable_objects) داده شده باشد، پرتاب می‌شود.

## مثال‌ها

مثال زیر یک کپی از `AudioData` را به‌عنوان `audioData2` کلون می‌کند.

```js
let audioData2 = AudioData.clone();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}