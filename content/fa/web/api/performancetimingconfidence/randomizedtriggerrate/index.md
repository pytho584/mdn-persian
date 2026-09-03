---
title: "PerformanceTimingConfidence: randomizedTriggerRate property"
short-title: randomizedTriggerRate
slug: Web/API/PerformanceTimingConfidence/randomizedTriggerRate
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PerformanceTimingConfidence.randomizedTriggerRate
---

{{APIRef("Performance API")}}{{SeeCompatTable}}

خاصیت فقط‌خواندنی **`randomizedTriggerRate`** از رابط {{domxref("PerformanceTimingConfidence")}} نشان می‌دهد که هر چند وقت یکبار نویز هنگام نمایش {{domxref("PerformanceTimingConfidence.value")}} اعمال می‌شود.

نویز به داده‌ها اضافه می‌شود تا حریم خصوصی بهبود یابد (به‌طوری که هر آیتم داده کمتر قابل شناسایی باشد). وقتی نویز اضافه می‌شود، یک `value` با اطمینان `low` یا `high` با احتمال برابر برگردانده می‌شود، نه `value` واقعی، تا نتایج مبهم شوند.

## مقدار

یک عدد بین `0` تا `1`، شامل هر دو، که یک مقدار درصدی را نشان می‌دهد. مقدار `0` معادل `0%` است، به این معنی که هرگز نویز اضافه نمی‌شود، در حالی که `1` معادل `100%` است، به این معنی که همیشه نویز اضافه می‌شود.

## مثال‌ها

برای مثال به صفحه اصلی {{domxref("PerformanceTimingConfidence")}} مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("PerformanceTimingConfidence")}}