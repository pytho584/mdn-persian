---
title: "ImageDecoder: decode() method"
short-title: decode()
slug: Web/API/ImageDecoder/decode
page-type: web-api-instance-method
browser-compat: api.ImageDecoder.decode
---

{{securecontext_header}}{{APIRef("WebCodecs API")}}{{AvailableInWorkers("window_and_dedicated")}}

متد **`decode()`** از رابط {{domxref("ImageDecoder")}} یک پیام کنترلی را برای رمزگشایی فریم یک تصویر در صف قرار می‌دهد.

## نحو (Syntax)

```js-nolint
decode()
decode(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : یک شیء حاوی اعضای زیر:
    - `frameIndex` {{optional_inline}}
      - : یک عدد صحیح که نشان‌دهنده‌ی ایندکس فریم برای رمزگشایی است. مقدار پیش‌فرض `0` (اولین فریم) است.
    - `completeFramesOnly` {{optional_inline}}
      - : یک {{jsxref("Boolean")}} که مقدار پیش‌فرض آن `true` است.
        اگر `true` باشد، {{jsxref("Promise")}} برگشتی از متد تنها زمانی resolve می‌شود که تصویر به طور کامل رمزگشایی شود.
        اگر `false` باشد، متد یک Promise جدید برمی‌گرداند که ممکن است با یک تصویر رمزگشایی‌شده‌ی جزئی resolve شود.
        این متد می‌تواند تا زمانی که `result.complete` برابر `true` شود، به صورت مکرر فراخوانی شود و هر مرحله تصویری با سطح جزئیات بعدی موجود ارائه دهد.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک شیء حاوی اعضای زیر resolve می‌شود:

- `image`
  - : یک {{domxref("VideoFrame")}} حاوی تصویر رمزگشایی‌شده.
- `complete`
  - : یک {{jsxref("Boolean")}} که اگر `true` باشد نشان می‌دهد `image` شامل خروجی نهایی با جزئیات کامل است.

### استثناها (Exceptions)

در صورت بروز خطا، promise با استثنای زیر resolve می‌شود:

- `InvalidStateError` {{domxref("DOMException")}}
  - : در صورت برقراری هر یک از شرایط زیر بازگردانده می‌شود:
    - `close` برابر `true` باشد، یعنی متد {{domxref("ImageDecoder.close()","close()")}} قبلاً فراخوانی شده است.
    - فریم درخواستی وجود نداشته باشد.

## مثال‌ها

### رمزگشایی همزمان یک فریم کامل تصویر

مثال زیر فریم دوم (در ایندکس `1`) را رمزگشایی کرده و {{domxref("VideoFrame")}} حاصل را در کنسول چاپ می‌کند.

```js
let result = await imageDecoder.decode({ frameIndex: 1 });
console.log(result.image);
```

### رمزگشایی جزئی یک فریم تصویر progressive

مثال زیر فریم اول را مکرراً رمزگشایی می‌کند تا زمانی که کامل شود:

```js
let complete = false;
while (!complete) {
  // The promise returned by `decode()` will only resolve when a new
  // level of detail is available or the frame is complete. I.e.,
  // calling `decode()` in a loop like this won't needlessly spin.
  let result = await imageDecoder.decode({ completeFramesOnly: false });

  // Do something with `result.image`.

  complete = result.complete;
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}