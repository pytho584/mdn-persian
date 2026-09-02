---
title: "MerchantValidationEvent: validationURL property"
short-title: validationURL
slug: Web/API/MerchantValidationEvent/validationURL
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.MerchantValidationEvent.validationURL
---

{{APIRef("Payment Request API")}}{{Deprecated_Header}}{{SecureContext_Header}}{{non-standard_header}}

ویژگی {{domxref("MerchantValidationEvent")}} با نام **`validationURL`** یک رشتهٔ فقط‌خواندنی است که نشانی اینترنتی (URL) موردنیاز برای دریافت داده‌های مخصوصِ پردازندهٔ پرداخت جهت تأیید فروشنده (merchant) را فراهم می‌کند.

این داده‌ها باید به متد {{domxref("MerchantValidationEvent.complete", "complete()")}} ارسال شوند تا عامل کاربر (user agent) بتواند تراکنش را کامل کند.

## مقدار

یک رشتهٔ فقط‌خواندنی که URL لازم برای بارگذاری داده‌های مخصوصِ پردازندهٔ پرداخت را مشخص می‌کند؛ داده‌هایی که برای تکمیل فرایند تأیید فروشنده ضروری هستند. پس از بارگذاری، این داده‌ها باید — به‌طور مستقیم یا از طریق یک promise — به {{domxref("MerchantValidationEvent.complete", "complete()")}} ارسال شوند.

برای آشنایی بیشتر با این فرایند، به [تأیید فروشنده](/en-US/docs/Web/API/Payment_Request_API/Concepts#merchant_validation) مراجعه کنید.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Payment Request API](/en-US/docs/Web/API/Payment_Request_API)
- [استفاده از Payment Request API](/en-US/docs/Web/API/Payment_Request_API/Using_the_Payment_Request_API)
- [مفاهیم پردازش پرداخت](/en-US/docs/Web/API/Payment_Request_API/Concepts)