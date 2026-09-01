---
title: "Document: releaseCapture() method"
short-title: releaseCapture()
slug: Web/API/Document/releaseCapture
page-type: web-api-instance-method
status:
  - non-standard
browser-compat: api.Document.releaseCapture
---

{{ApiRef("DOM")}}{{Non-standard_header}}

متد **`releaseCapture()`** اگر در حال حاضر بر روی یک عنصر در این سند، گرفتن ماوس فعال شده باشد، آن را آزاد می‌کند. پس از آزاد شدن گرفتن ماوس، رویدادهای ماوس دیگر همه به عنصری که گرفتن روی آن فعال شده بود هدایت نخواهند شد.

فعال کردن گرفتن ماوس بر روی یک عنصر با فراخوانی {{domxref("element.setCapture()")}} انجام می‌شود.

## نحو

```js-nolint
releaseCapture()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

برای مثال به [example](/en-US/docs/Web/API/Element/setCapture#examples) مربوط به {{domxref("element.setCapture()")}} مراجعه کنید.

## مشخصات

بخشی از هیچ مشخصاتی نیست.

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("element.setCapture()")}}