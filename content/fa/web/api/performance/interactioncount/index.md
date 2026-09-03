---
title: "Performance: interactionCount property"
short-title: interactionCount
slug: Web/API/Performance/interactionCount
page-type: web-api-instance-property
browser-compat: api.Performance.interactionCount
---

{{APIRef("Performance API")}}

خصوصیت فقط‑خواندنی `performance.interactionCount` تعداد تعامل‌های واقعی کاربر را که از زمان بارگذاری صفحه رخ داده‌اند، نشان می‌دهد.

فقط تعامل‌های گسسته‌ای که دارای {{domxref("PerformanceEventTiming.interactionId", "interactionId")}} هستند — مانند کلیک‌ها و رویدادهای کلید — شمارش می‌شوند. سایر تعامل‌ها، مانند تعامل‌های اسکرول، مستثنی هستند.

این ویژگی هنگام محاسبه {{Glossary("Interaction_to_next_paint", "Interaction to Next Paint (INP)")}} مفید است، و به طور خاص برای حذف داده‌های پرت (outliers) در صفحات طولانی‌مدت کاربرد دارد. INP درصد نود و هشتم تعامل‌های یک صفحه را در نظر می‌گیرد و بنابراین از هر ۵۰ تعامل، یک تعامل را به عنوان «داده پرت» که منعکس‌کننده پاسخ‌گویی کلی صفحه نیست، حذف می‌کند.

## Value

یک عدد که در ابتدا `0` است و با هر تعامل گسسته که توسط {{domxref("PerformanceEventTiming")}} اندازه‌گیری می‌شود و یک {{domxref("PerformanceEventTiming.interactionId", "interactionId")}} به آن اختصاص می‌یابد، به میزان `1` افزایش می‌یابد.

## Examples

### بررسی تعداد تعامل‌ها برای محاسبه دقیق INP

برای صفحات با تعداد زیادی تعامل، می‌توانید INP را پس از حذف ۱ داده پرت از هر ۵۰ داده، با استفاده از الگوی زیر دوباره محاسبه کنید:

```js
if (performance.interactionCount >= 50) {
  recalculateINP(); // Actual calculation is complex and is not shown here
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("PerformanceEventTiming")}}
- {{domxref("PerformanceEventTiming.interactionId")}}
- {{Glossary("Interaction_to_next_paint", "Interaction to Next Paint (INP)")}}