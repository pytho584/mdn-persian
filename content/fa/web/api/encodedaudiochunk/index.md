---
title: "EncodedAudioChunk"
---

---
title: EncodedAudioChunk
slug: Web/API/EncodedAudioChunk
page-type: web-api-interface
browser-compat: api.EncodedAudioChunk
---

{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

رابطِ **`EncodedAudioChunk`** از {{domxref('WebCodecs API','','',' ')}} یک قطعه از داده‌های صوتی رمزگذاری‌شده را نمایش می‌دهد.

## سازنده

- {{domxref("EncodedAudioChunk.EncodedAudioChunk", "EncodedAudioChunk()")}}
  - : یک شیء `EncodedAudioChunk` جدید می‌سازد.

## ویژگی‌های نمونه

- {{domxref("EncodedAudioChunk.type")}} {{ReadOnlyInline}}
  - : یک رشته برمی‌گرداند که نشان می‌دهد این قطعه از داده، یک قطعه کلیدی (key chunk) است یا نه.
- {{domxref("EncodedAudioChunk.timestamp")}} {{ReadOnlyInline}}
  - : یک عدد صحیح برمی‌گرداند که برچسب زمانی (timestamp) صوت را بر حسب میکروثانیه نشان می‌دهد.
- {{domxref("EncodedAudioChunk.duration")}} {{ReadOnlyInline}}
  - : یک عدد صحیح برمی‌گرداند که مدت‌زمان صوت را بر حسب میکروثانیه نشان می‌دهد.
- {{domxref("EncodedAudioChunk.byteLength")}} {{ReadOnlyInline}}
  - : یک عدد صحیح برمی‌گرداند که طول صوت را بر حسب بایت نشان می‌دهد.

## روش‌های نمونه

- {{domxref("EncodedAudioChunk.copyTo()")}}
  - : داده‌های صوتی رمزگذاری‌شده را کپی می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}