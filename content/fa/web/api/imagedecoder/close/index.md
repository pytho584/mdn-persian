---
title: "ImageDecoder: close() method"
short-title: close()
slug: Web/API/ImageDecoder/close
page-type: web-api-instance-method
browser-compat: api.ImageDecoder.close
---

{{securecontext_header}}{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

متد **`close()`** از اینترفیس {{domxref("ImageDecoder")}} همه‌ٔ کارهای معلق را پایان می‌دهد و منابع سیستم را آزاد می‌کند.

## سینتکس

```js-nolint
close()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

مثال زیر، `ImageDecoder` را می‌بندد.

```js
imageDecoder.close();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}