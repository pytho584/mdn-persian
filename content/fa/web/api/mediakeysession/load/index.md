---
title: "MediaKeySession: load() method"
short-title: load()
slug: Web/API/MediaKeySession/load
page-type: web-api-instance-method
browser-compat: api.MediaKeySession.load
---

{{APIRef("Encrypted Media Extensions")}}{{SecureContext_Header}}

متد `load()` در رابط {{domxref('MediaKeySession')}} یک {{jsxref('Promise')}} برمی‌گرداند که پس از بارگذاری داده‌ها برای یک شیء جلسه مشخص، به یک مقدار بولی (boolean) resolve می‌شود.

## نحو (Syntax)

```js-nolint
load(sessionId)
```

### پارامترها

- `sessionId`
  - : یک رشته منحصربه‌فرد که توسط ماژول توصیف محتوا (content description module) برای شیء رسانه‌ای فعلی و کلیدها یا مجوزهای مرتبط با آن تولید می‌شود.

### مقدار بازگشتی

یک {{jsxref('Promise')}} که به یک مقدار بولی resolve می‌شود و نشان می‌دهد که بارگذاری موفق بوده یا ناموفق.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
