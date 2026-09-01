---
title: "HIDDevice: open() method"
short-title: open()
slug: Web/API/HIDDevice/open
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.HIDDevice.open
---

{{securecontext_header}}{{APIRef("WebHID API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_shared")}}

متد **`open()`** در رابط {{domxref("HIDDevice")}} از سیستمعامل درخواست میکند که دستگاه HID را باز کند.

> [!NOTE]
> دستگاه‌های HID به‌صورت خودکار باز نمی‌شوند. بنابراین، یک {{domxref("HIDDevice")}} که توسط {{domxref("HID.requestDevice()")}} بازگردانده شده است، باید پیش از آنکه برای انتقال داده در دسترس قرار گیرد، با این متد باز شود.

## سینتکس

```js-nolint
open()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که پس از باز شدن اتصال، با مقدار `undefined` حل می‌شود.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر اتصال از قبل باز شده باشد پرتاب می‌شود.
- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر تلاش برای باز کردن اتصال به هر دلیلی ناموفق باشد پرتاب می‌شود.

## مثال‌ها

در مثال زیر، قبل از تلاش برای ارسال یا دریافت داده، منتظر باز شدن اتصال HID می‌مانیم.

```js
await device.open();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
