---
title: "MediaKeySession: close() method"
short-title: close()
slug: Web/API/MediaKeySession/close
page-type: web-api-instance-method
browser-compat: api.MediaKeySession.close
---

{{APIRef("Encrypted Media Extensions")}}{{SecureContext_Header}}

متد `close()` از رابط {{domxref('MediaKeySession')}} اعلام می‌کند که دیگر به نشست رسانه‌ای فعلی نیازی نیست و ماژول رمزگشایی محتوا باید هر منبع مرتبط با این شیء را آزاد کرده و آن را ببندد. سپس یک {{jsxref('Promise')}} برمی‌گرداند.

## Syntax

```js-nolint
close()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref('Promise')}}.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}