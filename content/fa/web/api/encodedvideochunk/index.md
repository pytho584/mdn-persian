---
title: "EncodedVideoChunk"
source: "https://developer.mozilla.org/en-US/docs/Web/API/EncodedVideoChunk"
---

---
title: EncodedVideoChunk
slug: Web/API/EncodedVideoChunk
page-type: web-api-interface
browser-compat: api.EncodedVideoChunk
---

{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

رابط **`EncodedVideoChunk`** در {{domxref('WebCodecs API','','',' ')}} یک تکه از داده‌های ویدیویی کدگذاری‌شده را نمایش می‌دهد.

## سازنده

- {{domxref("EncodedVideoChunk.EncodedVideoChunk", "EncodedVideoChunk()")}}
  - : یک شیء `EncodedVideoChunk` جدید ایجاد می‌کند.

## ویژگی‌های نمونه

- {{domxref("EncodedVideoChunk.type")}} {{ReadOnlyInline}}
  - : رشته‌ای را برمی‌گرداند که نشان می‌دهد آیا این تکه داده یک تکه کلیدی (key chunk) است یا خیر.
- {{domxref("EncodedVideoChunk.timestamp")}} {{ReadOnlyInline}}
  - : یک عدد صحیح را برمی‌گرداند که برچسب زمانی ویدیو را بر حسب میکروثانیه نشان می‌دهد.
- {{domxref("EncodedVideoChunk.duration")}} {{ReadOnlyInline}}
  - : یک عدد صحیح را برمی‌گرداند که مدت‌زمان ویدیو را بر حسب میکروثانیه نشان می‌دهد.
- {{domxref("EncodedVideoChunk.byteLength")}} {{ReadOnlyInline}}
  - : یک عدد صحیح را برمی‌گرداند که طول ویدیو را بر حسب بایت نشان می‌دهد.

## روش‌های نمونه

- {{domxref("EncodedVideoChunk.copyTo()")}}
  - : داده‌های ویدیویی کدگذاری‌شده را کپی می‌کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}