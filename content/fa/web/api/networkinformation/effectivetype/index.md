---
title: "NetworkInformation: effectiveType property"
short-title: effectiveType
slug: Web/API/NetworkInformation/effectiveType
page-type: web-api-instance-property
browser-compat: api.NetworkInformation.effectiveType
---

{{APIRef("Network Information API")}} {{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`effectiveType`** از رابط {{domxref("NetworkInformation")}} نوع مؤثر اتصال را برمی‌گرداند؛ یعنی یکی از مقادیر `slow-2g`، `2g`، `3g` یا `4g`. این مقدار با استفاده از ترکیبی از مقادیرِ زمان رفت‌وبرگشت (round-trip time) و سرعت دانلود (downlink) که اخیراً مشاهده شده‌اند تعیین می‌شود.

## مقدار

یک رشته (string) که یکی از مقادیر `slow-2g`، `2g`، `3g` یا `4g` است.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [نوع اتصال مؤثر](/en-US/docs/Glossary/Effective_connection_type)
- {{HTTPHeader("ECT")}}