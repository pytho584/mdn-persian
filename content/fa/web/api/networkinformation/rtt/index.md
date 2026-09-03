---
title: "NetworkInformation: rtt property"
---

---
title: "NetworkInformation: rtt property"
short-title: rtt
slug: Web/API/NetworkInformation/rtt
page-type: web-api-instance-property
browser-compat: api.NetworkInformation.rtt
---

{{apiref("Network Information API")}} {{AvailableInWorkers}}

خاصیت فقطخواندنی **`rtt`** در رابط {{domxref("NetworkInformation")}} زمان رفتوبرگشت مؤثر تخمینی اتصال فعلی را برمی‌گرداند که به نزدیک‌ترین مضرب ۲۵ میلی‌ثانیه گرد شده است. این مقدار بر اساس اندازه‌گیری‌های اخیر RTT در لایه کاربردی (application layer) روی اتصال‌هایی که اخیراً فعال بوده‌اند محاسبه می‌شود و اتصال‌هایی که به فضای آدرس خصوصی برقرار شده‌اند را شامل نمی‌شود. اگر داده اندازه‌گیری اخیری در دسترس نباشد، این مقدار بر اساس ویژگی‌های فناوری اتصال زیرین تعیین می‌شود.

## مقدار

یک عدد.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{HTTPHeader("RTT")}}