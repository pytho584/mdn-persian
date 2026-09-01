---
title: "DOMImplementation: hasFeature() method"
short-title: hasFeature()
slug: Web/API/DOMImplementation/hasFeature
page-type: web-api-instance-method
status:
  - deprecated
browser-compat: api.DOMImplementation.hasFeature
---

{{ApiRef("DOM")}}{{Deprecated_Header}}

متد **`DOMImplementation.hasFeature()`** یک علامت بولی (boolean) برمی‌گرداند که نشان می‌دهد آیا یک ویژگی خاص پشتیبانی می‌شود یا خیر. این متد منسوخ شده است و مرورگرهای مدرن در همه موارد `true` برمی‌گردانند.

پیاده‌سازی‌های مختلف تا حد زیادی در نوع ویژگی‌هایی که گزارش می‌دادند اختلاف داشتند. آخرین نسخه مشخصات (spec) تصمیم گرفت که این متد را مجبور کند همیشه `true` برگرداند، جایی که قابلیت مورد نظر دقیق و در حال استفاده بود.

## نحو

```js-nolint
hasFeature(feature, version)
```

### پارامترها

- `feature`
  - : رشته‌ای که نام ویژگی را نشان می‌دهد.
- `version`
  - : رشته‌ای که نسخه مشخصات تعریف‌کننده ویژگی را نشان می‌دهد.

### مقدار بازگشتی

یک مقدار بولی `true`.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{domxref("DOMImplementation")}} که این متد به آن تعلق دارد.