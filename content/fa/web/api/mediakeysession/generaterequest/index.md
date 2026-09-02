---
title: "MediaKeySession: generateRequest() method"
short-title: generateRequest()
slug: Web/API/MediaKeySession/generateRequest
page-type: web-api-instance-method
browser-compat: api.MediaKeySession.generateRequest
---

{{APIRef("Encrypted Media Extensions")}}{{SecureContext_Header}}

متد `generateRequest()` از رابط {{domxref('MediaKeySession')}} یک {{jsxref('Promise')}} را پس از تولید درخواست مجوز بر اساس داده‌های مقداردهی اولیه برمی‌گرداند.

## نحو (Syntax)

```js-nolint
generateRequest(initDataType, initData)
```

### پارامترها

- `initDataType`
  - : رشته‌ای که قالب پارامتر `initData` را مشخص می‌کند. این مقدار باید یکی از موارد زیر باشد:
    - `"cenc"`: پارامتر `initData` از قالب [`"cenc"`](https://w3c.github.io/encrypted-media/format-registry/initdata/cenc.html) استفاده می‌کند.
    - `"keyids"`: پارامتر `initData` از قالب [`"keyids"`](https://w3c.github.io/encrypted-media/format-registry/initdata/keyids.html) استفاده می‌کند.
    - `"webm"`: پارامتر `initData` از قالب [`"webm"`](https://w3c.github.io/encrypted-media/format-registry/initdata/webm.html) استفاده می‌کند.
- `initData`
  - : داده‌های مقداردهی اولیه برای درخواست، در قالبی که توسط `initDataType` مشخص شده است. این مقدار نمونه‌ای از هر یک از انواع زیر است:
    - {{jsxref("ArrayBuffer")}}
    - {{jsxref("DataView")}}
    - {{jsxref("TypedArray")}}

### مقدار بازگشتی

یک {{jsxref('Promise')}}.

### استثناها (Exceptions)

- {{jsxref("TypeError")}}
  - : اگر `initDataType` یک رشتهٔ خالی باشد، یا `initData` یک آرایهٔ خالی باشد، یا `initData` ارائه‌شده طبق `initDataType` مشخص‌شده معتبر نباشد، پرتاب می‌شود.
- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر پیاده‌سازی سیستم کلید (Key System) مرتبط با شیء `MediaKeySession` از `initDataType` ارائه‌شده پشتیبانی نکند، یا داده‌های مقداردهی اولیهٔ پاک‌سازی‌شده خالی باشند، یا داده‌های مقداردهی اولیهٔ پاک‌سازی‌شده توسط ماژول رمزگشایی محتوا (CDM) پشتیبانی نشوند، پرتاب می‌شود.
- {{domxref("QuotaExceededError")}}
  - : اگر عملیات به دلیل کمبود منابع در عامل کاربر (user agent) یا CDM با شکست مواجه شود، پرتاب می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر شیء `MediaKeySession` در وضعیت `closing` یا `closed` باشد، یا اگر قبلاً مقداردهی اولیه شده باشد، پرتاب می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}