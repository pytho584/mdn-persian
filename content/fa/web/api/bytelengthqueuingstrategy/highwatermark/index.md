---
title: "ByteLengthQueuingStrategy: highWaterMark property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/ByteLengthQueuingStrategy/highWaterMark"
translated_by: "n8n + AI"
---

---
title: "ByteLengthQueuingStrategy: highWaterMark property"
short-title: highWaterMark
slug: Web/API/ByteLengthQueuingStrategy/highWaterMark
page-type: web-api-instance-property
browser-compat: api.ByteLengthQueuingStrategy.highWaterMark
---

{{APIRef("Streams")}}{{AvailableInWorkers}}

ویژگی فقط‑خواندنی **`ByteLengthQueuingStrategy.highWaterMark`** تعداد کل بایت‌هایی را برمی‌گرداند که می‌توانند در صف داخلی قبل از اعمال [فشار معکوس](/en-US/docs/Web/API/Streams_API/Concepts#backpressure) قرار بگیرند.

> [!NOTE]
> برخلاف [`CountQueuingStrategy()`](/en-US/docs/Web/API/CountQueuingStrategy/CountQueuingStrategy) که در آن ویژگی `highWaterMark` یک شمارش ساده از تعداد تکه‌ها را مشخص می‌کند، در `ByteLengthQueuingStrategy()`، پارامتر `highWaterMark` تعداد _بایت_ را مشخص می‌کند – به طور خاص، با توجه به یک جریان از تکه‌ها، چه تعداد بایت از آن تکه‌ها (به جای شمارش تعداد تکه‌ها) می‌تواند در صف داخلی قبل از اعمال فشار معکوس قرار گیرد.

## مقدار

یک عدد صحیح.

## مثال‌ها

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
console.log(`highWaterMark value: ${queuingStrategy.highWaterMark}$`);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- سازنده {{domxref("ByteLengthQueuingStrategy.ByteLengthQueuingStrategy", "ByteLengthQueuingStrategy()")}}