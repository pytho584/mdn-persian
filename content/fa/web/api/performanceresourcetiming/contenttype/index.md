---
title: "PerformanceResourceTiming: contentType property"
short-title: contentType
slug: Web/API/PerformanceResourceTiming/contentType
page-type: web-api-instance-property
browser-compat: api.PerformanceResourceTiming.contentType
---

{{APIRef("Performance API")}}{{AvailableInWorkers}}

خاصیت فقط‌خواندنی **`contentType`** در رابط {{domxref("PerformanceResourceTiming")}} رشته‌ای است که نوع محتوای منبع واکشی‌شده را نشان می‌دهد و به شکل {{glossary("MIME type")}} و زیرنوع (subtype) که با یک اسلش (/) از هم جدا شده‌اند، قالب‌بندی می‌شود.

نوع محتوا نسخه‌ای «حداقلی‌شده» و «استانداردشده» از نوع MIME است که از هدر HTTP {{httpheader("Content-Type")}} ارسال‌شده در پاسخ واکشی منبع استخراج می‌شود.
برای جاوااسکریپت، JSON، SVG و XML، نوع MIME با یک رشتهٔ نمایندهٔ نوع/زیرنوع MIME جایگزین می‌شود.
سایر انواع پشتیبانی‌شده توسط مرورگر با رشتهٔ نوع/زیرنوع MIME موجود در هدر نمایش داده می‌شوند (سایر اطلاعات موجود در هدر کنار گذاشته می‌شوند).

## مقدار

رشته‌ای که «جوهره» نوع MIME محتوا را نشان می‌دهد.
این مقدار می‌تواند یکی از موارد زیر باشد:

- `text/javascript`
  - : محتوای جاوااسکریپت.
- `application/json`
  - : محتوای JSON.
- `image/svg+xml`
  - : محتوای SVG.
- `application/xml`
  - : محتوای XML (به غیر از SVG).
- نوع/زیرنوع MIME
  - : هر نوع/زیرنوع MIME دیگری که توسط عامل کاربر پشتیبانی می‌شود.
- `""` (رشتهٔ خالی)
  - : برای انواع MIME که توسط مرورگر پشتیبانی نمی‌شوند، یا اگر واکشی منبع به دلیل بررسی‌های [CORS](/en-US/docs/Web/HTTP/Guides/CORS) ناموفق بوده باشد، بازگردانده می‌شود.

## مثال‌ها

### فیلتر کردن منابع

از خاصیت `contentType` می‌توان برای دریافت فقط ورودی‌های خاص زمان‌بندی منبع استفاده کرد؛ برای مثال، فقط ورودی‌های مربوط به اسکریپت‌ها.

مثال زیر از یک {{domxref("PerformanceObserver")}} برای اطلاع‌یافتن از ورودی‌های جدید `resource` هنگام ثبت‌شدن در زمان‌خط مرورگر استفاده می‌کند.
از گزینهٔ `buffered` برای دسترسی به ورودی‌های مربوط به قبل از ایجاد observer استفاده شده است.

```js
const observer = new PerformanceObserver((list) => {
  const javascriptResources = list
    .getEntries()
    .filter((entry) => entry.contentType === "text/javascript");
  console.log(javascriptResources);
});

observer.observe({ type: "resource", buffered: true });
```

مثال زیر از {{domxref("Performance.getEntriesByType()")}} استفاده می‌کند که فقط ورودی‌های performance از نوع `resource` موجود در زمان‌خط مرورگر را هنگام فراخوانی متد نشان می‌دهد.

```js
const scripts = performance
  .getEntriesByType("resource")
  .filter((entry) => entry.contentType === "text/javascript");
console.log(scripts);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}