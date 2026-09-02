---
title: "ImageDecoder: reset() method"
short-title: reset()
slug: Web/API/ImageDecoder/reset
page-type: web-api-instance-method
browser-compat: api.ImageDecoder.reset
---

{{securecontext_header}}{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

متد **`reset()`** از رابط {{domxref("ImageDecoder")}} تمام عملیات‌های `decode()` در انتظار را لغو می‌کند و تمام promises (وعده‌های) در انتظار را رد می‌کند. تمام حالت‌های دیگر بدون تغییر باقی می‌مانند. پس از `reset()` همچنان می‌توان متدهای کلاس را فراخوانی کرد. برای مثال، فراخوانی `decode()` پس از `reset()` مجاز است.

## نحو (Syntax)

```js-nolint
reset()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

مثال زیر `ImageDecoder` را بازنشانی می‌کند.

```js
for (let i = 0; i < imageDecoder.tracks.selectedTrack.frameCount; ++i)
  imageDecoder.decode({ frameIndex: i }).catch(console.log);
imageDecoder.reset();
imageDecoder.decode({ frameIndex: 0 }).then(console.log);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}