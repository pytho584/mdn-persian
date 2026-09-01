---
title: "HTMLMediaElement: fastSeek() method"
short-title: fastSeek()
slug: Web/API/HTMLMediaElement/fastSeek
page-type: web-api-instance-method
browser-compat: api.HTMLMediaElement.fastSeek
---

{{APIRef("HTML DOM")}}

متد **`HTMLMediaElement.fastSeek()`** به‌سرعت رسانه را به زمان جدید می‌برد و در این مسیر دقت را قربانی می‌کند.

> [!NOTE]
> اگر به پیمایش با دقت نیاز دارید، باید [`HTMLMediaElement.currentTime`](/en-US/docs/Web/API/HTMLMediaElement/currentTime)
> را تنظیم کنید.

## Syntax

```js-nolint
fastSeek(time)
```

### Parameters

- `time`
  - : یک عدد اعشاری (double).

### Return value

هیچ ({{jsxref("undefined")}}).

## Examples

این مثال، ویدیو را به‌سرعت به موقعیت ۲۰ ثانیه‌ای می‌برد:

```js
let myVideo = document.getElementById("myVideoElement");

myVideo.fastSeek(20);
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [HTMLMediaElement.currentTime](/en-US/docs/Web/API/HTMLMediaElement/currentTime) برای پیمایش بدون کاهش دقت
