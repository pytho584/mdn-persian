---
title: "HIDDevice: close() method"
short-title: close()
slug: Web/API/HIDDevice/close
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.HIDDevice.close
---

{{securecontext_header}}{{APIRef("WebHID API")}}{{SeeCompatTable}}{{AvailableInWorkers("window_and_worker_except_shared")}}

متد **`close()`** از رابط {{domxref("HIDDevice")}} اتصال به دستگاه HID را می‌بندد.

## Syntax

```js-nolint
close()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که پس از بسته شدن اتصال با مقدار `undefined` حل می‌شود.

## مثال‌ها

در مثال زیر، پس از ارسال و دریافت تمام داده‌ها، دستگاه HID را می‌بندیم.

```js
await device.close();
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}