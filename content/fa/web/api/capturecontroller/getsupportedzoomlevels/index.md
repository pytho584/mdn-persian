---
title: "CaptureController: getSupportedZoomLevels() method"
short-title: getSupportedZoomLevels()
slug: Web/API/CaptureController/getSupportedZoomLevels
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.CaptureController.getSupportedZoomLevels
---

{{APIRef("Screen Capture API")}}{{SeeCompatTable}}{{SecureContext_Header}}

در رابط {{domxref("CaptureController")}}، متد **`getSupportedZoomLevels()`** سطوح بزرگ‌نمایی متفاوتی را که سطح نمایش ضبط‌شده از آن‌ها پشتیبانی می‌کند، برمی‌گرداند.

## Syntax

```js-nolint
getSupportedZoomLevels()
```

### Parameters

هیچ.

### Return value

یک آرایه از اعداد که سطوح بزرگ‌نمایی متفاوتی را نشان می‌دهد که سطح نمایش ضبط‌شده از آن‌ها پشتیبانی می‌کند.

### Exceptions

- `InvalidStateError` {{domxref("DOMException")}}
  - : جریان {{domxref("MediaStream")}} که توسط فراخوانی اولیه {{domxref("MediaDevices.getDisplayMedia()")}} بازگردانده شده است، دیگر در حال ضبط نیست؛ برای مثال به این دلیل که روی اشیاء {{domxref("MediaStreamTrack")}} مرتبط، متد {{domxref("MediaStreamTrack.stop", "stop()")}} فراخوانی شده است.

- `NotSupportedError` {{domxref("DOMException")}}
  - : نوع سطحی که در حال ضبط است، یک برگه مرورگر (browser tab) نیست.

## Examples

### Basic `getSupportedZoomLevels()` usage

در نسخه نمایشی زنده ما، که در [استفاده از API کنترل سطح ضبط‌شده](/en-US/docs/Web/API/Screen_Capture_API/Captured_Surface_Control) نشان داده شده است، با اجرای `getSupportedZoomLevels()` سطوح بزرگ‌نمایی پشتیبانی‌شده سطح نمایش ضبط‌شده را به دست می‌آوریم و آرایه حاصل را در متغیری به نام `zoomLevels` ذخیره می‌کنیم:

```js
const zoomLevels = controller.getSupportedZoomLevels();
```

این آرایه بعداً در تابعی به نام `updateZoomButtonState()` استفاده می‌شود. مسئله‌ای که این کار حل می‌کند این است که اگر تلاش کنید به پایین‌تر از حداقل سطح بزرگ‌نمایی پشتیبانی‌شده کوچک‌نمایی کنید یا به بالاتر از حداکثر سطح بزرگ‌نمایی پشتیبانی‌شده بزرگ‌نمایی کنید، {{domxref("CaptureController.decreaseZoomLevel", "decreaseZoomLevel()")}}/{{domxref("CaptureController.increaseZoomLevel", "increaseZoomLevel()")}} یک `InvalidStateError` {{domxref("DOMException")}} پرتاب خواهد کرد.

> [!NOTE]
> معمولاً بهترین روش این است که `decreaseZoomLevel()` و `increaseZoomLevel()` را از داخل یک بلوک [`try...catch`](/en-US/docs/Web/JavaScript/Reference/Statements/try...catch) فراخوانی کنید، زیرا ممکن است سطح بزرگ‌نمایی به‌صورت ناهمگام (asynchronous) توسط موجودیتی غیر از برنامه تغییر کند که می‌تواند منجر به پرتاب خطا شود. برای مثال، کاربر ممکن است مستقیماً با سطح ضبط‌شده تعامل کند تا بزرگ‌نمایی یا کوچک‌نمایی کند.

تابع `updateZoomButtonState()` با اطمینان از فعال بودن هر دو دکمه «کوچک‌نمایی» (Zoom out) و «بزرگ‌نمایی» (Zoom in) از این مشکل جلوگیری می‌کند. سپس دو بررسی انجام می‌دهد:

- اگر سطح بزرگ‌نمایی فعلی برابر با حداقل سطح بزرگ‌نمایی پشتیبانی‌شده باشد (که در اولین مقدار آرایه `zoomLevels` ذخیره شده است)، دکمه «کوچک‌نمایی» را غیرفعال می‌کنیم تا کاربر نتواند بیشتر کوچک‌نمایی کند.
- اگر سطح بزرگ‌نمایی فعلی برابر با حداکثر سطح بزرگ‌نمایی پشتیبانی‌شده باشد (که در آخرین مقدار آرایه `zoomLevels` ذخیره شده است)، دکمه «بزرگ‌نمایی» را غیرفعال می‌کنیم تا کاربر نتواند بیشتر بزرگ‌نمایی کند.

```js
function updateZoomButtonState() {
  decBtn.disabled = false;
  incBtn.disabled = false;
  if (controller.zoomLevel === zoomLevels[0]) {
    decBtn.disabled = true;
  } else if (controller.zoomLevel === zoomLevels[zoomLevels.length - 1]) {
    incBtn.disabled = true;
  }
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Screen Capture API](/en-US/docs/Web/API/Screen_Capture_API)
- {{domxref("MediaDevices.getDisplayMedia()")}}
- [استفاده از API کنترل سطح ضبط‌شده](/en-US/docs/Web/API/Screen_Capture_API/Captured_Surface_Control)