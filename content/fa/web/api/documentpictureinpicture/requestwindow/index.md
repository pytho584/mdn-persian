---
title: "DocumentPictureInPicture: requestWindow() method"
short-title: requestWindow()
slug: Web/API/DocumentPictureInPicture/requestWindow
page-type: web-api-instance-method
browser-compat: api.DocumentPictureInPicture.requestWindow
---

{{APIRef("Document Picture-in-Picture API")}}{{SecureContext_Header}}

متد **`requestWindow()`** از رابط {{domxref("DocumentPictureInPicture")}} پنجرهٔ Picture-in-Picture را برای بافت مرور اصلی (main browsing context) فعلی باز می‌کند. این متد یک {{jsxref("Promise")}} برمی‌گرداند که با یک نمونهٔ {{domxref("Window")}} که نمایانگر بافت مرور داخل پنجرهٔ Picture-in-Picture است، برآورده می‌شود.

متد `requestWindow()` به [فعال‌سازی گذرا](/en-US/docs/Glossary/Transient_activation) نیاز دارد؛ یعنی باید در پاسخ به یک اقدام کاربر مانند کلیک ماوس یا فشردن دکمه فراخوانی شود.

## Syntax

```js-nolint
requestWindow()
requestWindow(options)
```

### Parameters

- `options` {{optional_inline}}
  - : یک شیء گزینه‌ها که شامل ویژگی‌های زیر است:
    - `disallowReturnToOpener` {{optional_inline}}
      - : یک مقدار بولی. وقتی روی `true` تنظیم شود، این گزینه به مرورگر اشاره می‌کند که نباید کنترل رابط کاربری‌ای را نمایش دهد که به کاربر امکان بازگشت به تب مبدأ و بستن پنجرهٔ Picture-in-Picture را بدهد. پیش‌فرض `false` است.

        برای مثال، در پیاده‌سازی کروم از این قابلیت، کنترل رابط کاربری ارائه‌شده یک دکمهٔ «بازگشت به تب» در نوار بالای پنجرهٔ Picture-in-Picture است:

        ![پنجرهٔ مرورگر حاوی یک پخش‌کنندهٔ ویدیوی تعبیه‌شده و چند دکمهٔ کنترل، که دکمهٔ «بازگشت به تب» در نوار بالا با یک کادر قرمز مشخص شده است](back-to-tab-button.png)

    - `height` {{optional_inline}}
      - : یک عدد نامنفی که ارتفاع viewport پنجرهٔ Picture-in-Picture را بر حسب پیکسل تعیین می‌کند. پیش‌فرض `0` است.
    - `preferInitialWindowPlacement` {{optional_inline}}
      - : یک مقدار بولی که پیش‌فرض آن `false` است. وقتی روی `true` تنظیم شود، باعث می‌شود پنجرهٔ Picture-in-Picture همیشه زمانی که بسته و دوباره باز می‌شود، در همان موقعیت و اندازه‌ای ظاهر شود که ابتدا باز شده بود. در مقابل، اگر `preferInitialWindowPlacement` برابر `false` باشد، اندازه و موقعیت پنجرهٔ Picture-in-Picture هنگام بستن و بازگشایی به خاطر سپرده می‌شود — مثلاً در همان موقعیت و اندازهٔ قبلی که کاربر تنظیم کرده است، دوباره باز می‌شود.

    - `width` {{optional_inline}}
      - : یک عدد نامنفی که عرض viewport پنجرهٔ Picture-in-Picture را بر حسب پیکسل تعیین می‌کند. پیش‌فرض `0` است.

> [!NOTE]
> اگر یکی از `height` یا `width` مشخص شده باشد، دیگری نیز باید مشخص شود، در غیر این صورت خطا پرتاب می‌شود. اگر هر دو مقدار مشخص نشده باشند، صفر تعیین شده باشند، یا بیش از حد بزرگ تنظیم شده باشند، مرورگر مقادیر را برای ارائهٔ تجربهٔ کاربری معقول، به‌طور مناسب محدود (clamp) یا نادیده می‌گیرد. اندازهٔ نهایی محدودشده به پیاده‌سازی، اندازهٔ نمایشگر و عوامل دیگر بستگی دارد.

### Return value

یک {{jsxref("Promise")}} که با یک نمونهٔ شیء {{domxref("Window")}} برآورده می‌شود؛ این شیء نمایانگر بافت مرور داخل پنجرهٔ Picture-in-Picture است.

### Exceptions

- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر API به‌طور صریح غیرفعال شده باشد (مثلاً از طریق تنظیمات مرورگر) پرتاب می‌شود.
- `NotAllowedError` {{domxref("DOMException")}}
  - : در موارد زیر پرتاب می‌شود:
    - `requestWindow()` از یک شیء `window` سطح بالا (top-level) فراخوانی نشود.
    - `requestWindow()` از شیء `window` پنجرهٔ Picture-in-Picture فراخوانی شود (یعنی {{domxref("DocumentPictureInPicture.window")}}).
    - `requestWindow()` بدون {{Glossary("Transient_activation", "transient activation")}} فراخوانی شود.
- `RangeError` {{domxref("DOMException")}}
  - : اگر فقط یکی از `height` و `width` تنظیم شود، یا اگر `height` و `width` با مقادیر منفی تنظیم شوند، پرتاب می‌شود.

## Examples

```js
const videoPlayer = document.getElementById("player");

// …

// Open a Picture-in-Picture window with all options set
const pipWindow = await window.documentPictureInPicture.requestWindow({
  width: videoPlayer.clientWidth,
  height: videoPlayer.clientHeight,
  disallowReturnToOpener: true,
  preferInitialWindowPlacement: true,
});

// …
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("Document Picture-in-Picture API", "Document Picture-in-Picture API", "", "nocode")}}
- [استفاده از Document Picture-in-Picture API](/en-US/docs/Web/API/Document_Picture-in-Picture_API/Using)