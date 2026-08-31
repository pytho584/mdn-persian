---
title: "ByteLengthQueuingStrategy: ByteLengthQueuingStrategy() constructor"
source: "https://developer.mozilla.org/en-US/docs/Web/API/ByteLengthQueuingStrategy/ByteLengthQueuingStrategy"
translated_by: "n8n + AI"
---

{{APIRef("Streams")}}{{AvailableInWorkers}}

سازنده **`ByteLengthQueuingStrategy()`** یک نمونه از شیء `ByteLengthQueuingStrategy` ایجاد و بازمی‌گرداند.

## Syntax

```js-nolint
new ByteLengthQueuingStrategy(options)
```

### Parameters

- `options`
  - : یک شیء با ویژگی زیر:
    - `highWaterMark`
      - : تعداد کل بایت‌هایی که می‌توانند در صف داخلی قبل از اعمال فشار برگشتی (backpressure) قرار گیرند.

        بر خلاف [`CountQueuingStrategy()`](/en-US/docs/Web/API/CountQueuingStrategy/CountQueuingStrategy) که در آن `highWaterMark` یک شمارش ساده از تعداد تکه‌ها (chunks) را مشخص می‌کند، در `ByteLengthQueuingStrategy()`، `highWaterMark` یک تعداد _بایت_ را مشخص می‌کند – به طور خاص، با توجه به یک جریان از تکه‌ها، چند بایت از آن تکه‌ها (به جای شمارش تعداد تکه‌ها) می‌توانند قبل از اعمال فشار برگشتی در صف داخلی قرار گیرند.

### Return value

یک نمونه از شیء {{domxref("ByteLengthQueuingStrategy")}}.

### Exceptions

هیچ‌کدام.

## Examples

```js
const queuingStrategy = new ByteLengthQueuingStrategy({
  highWaterMark: 1 * 1024,
});

const readableStream = new ReadableStream(
  {
    start(controller) {
      // …
    },
    pull(controller) {
      // …
    },
    cancel(err) {
      console.log("stream error:", err);
    },
  },
  queuingStrategy,
);

const size = queuingStrategy.size(chunk);
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("ByteLengthQueuingStrategy")}} رابط