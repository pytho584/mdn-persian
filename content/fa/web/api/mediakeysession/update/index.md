---
title: "MediaKeySession: update() method"
short-title: update()
slug: Web/API/MediaKeySession/update
page-type: web-api-instance-method
browser-compat: api.MediaKeySession.update
---

{{APIRef("Encrypted Media Extensions")}}{{SecureContext_Header}}

متد `update()` در رابط {{domxref('MediaKeySession')}} پیام‌ها و مجوزها را به CDM بارگذاری می‌کند و سپس یک {{jsxref('Promise')}} برمی‌گرداند.

## نحو (Syntax)

```js-nolint
update(response)
```

### پارامترها

- `response`
  - : نمونه‌ای که یا یک {{jsxref("ArrayBuffer")}}، یک {{jsxref("TypedArray")}}، یا یک {{jsxref("DataView")}} است.

### مقدار بازگشتی

یک {{jsxref('Promise')}} که به `undefined` برطرف می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}