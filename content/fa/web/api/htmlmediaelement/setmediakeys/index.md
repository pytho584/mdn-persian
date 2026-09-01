---
title: "HTMLMediaElement: setMediaKeys() method"
short-title: setMediaKeys()
slug: Web/API/HTMLMediaElement/setMediaKeys
page-type: web-api-instance-method
browser-compat: api.HTMLMediaElement.setMediaKeys
---

{{APIRef("HTML DOM")}}{{SecureContext_Header}}

متد **`setMediaKeys()`** در رابط {{domxref("HTMLMediaElement")}}، شیء {{domxref("MediaKeys")}} را تنظیم می‌کند که برای رمزگشایی رسانه در حین پخش استفاده خواهد شد.

این متد یک {{jsxref("Promise")}} برمی‌گرداند که در صورت تنظیم موفق کلیدهای جدید، fulfilled می‌شود و در صورت عدم امکان تنظیم کلیدها، rejected می‌شود.

## Syntax

```js-nolint
setMediaKeys(mediaKeys)
```

### Parameters

- `mediaKeys`
  - : یک شیء {{domxref("MediaKeys")}} که {{domxref("HTMLMediaElement")}} می‌تواند برای رمزگشایی داده‌های رسانه در حین پخش از آن استفاده کند.

### Return value

یک {{jsxref("Promise")}} که با {{jsxref('undefined')}} fulfilled می‌شود.

### Exceptions

پرامیسی که برگردانده می‌شود ممکن است با یک خطا rejected شود:

- `InvalidStateError` {{domxref("DOMException")}}
  - : کلیدهای رسانه قبلاً در حال اتصال هستند، یا امکان حذف کلیدهای قبلی در زمان فعلی وجود ندارد (مثلاً به این دلیل که پیاده‌سازی خاص، حذف را در حین پخش مجاز نمی‌کند).
- {{domxref("QuotaExceededError")}}
  - : کلیدهای ارسال‌شده قبلاً توسط عنصر دیگری استفاده می‌شوند، یا مرورگر به دلایل دیگر قادر به استفاده از آن با این عنصر نیست.
- `NotSupportedError` {{domxref("DOMException")}}
  - : کلیدهای رسانه‌ای که در حال حاضر با رسانه مرتبط هستند نمی‌توانند از آن جدا شوند، زیرا این کار توسط CDM یا مرورگر پشتیبانی نمی‌شود.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}