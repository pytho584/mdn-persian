---
title: MerchantValidationEvent
slug: Web/API/MerchantValidationEvent
page-type: web-api-interface
status:
  - deprecated
  - non-standard
browser-compat: api.MerchantValidationEvent
---

{{APIRef("Payment Request API")}}{{Deprecated_Header}}{{SecureContext_Header}}{{non-standard_header}}

رابطهٔ **`MerchantValidationEvent`** در [Payment Request API](/en-US/docs/Web/API/Payment_Request_API) به فروشنده امکان می‌دهد تا تأیید کند که مجاز به استفاده از یک پرداخت‌یار خاص (payment handler) است.

دربارهٔ [تأیید فروشنده (merchant validation)](/en-US/docs/Web/API/Payment_Request_API/Concepts#merchant_validation) بیشتر بیاموزید.

## سازنده (Constructor)

- {{domxref("MerchantValidationEvent.MerchantValidationEvent()","MerchantValidationEvent()")}} {{Deprecated_Inline}} {{non-standard_inline}}
  - : یک شیء جدید `MerchantValidationEvent` می‌سازد که رویداد {{domxref("PaymentRequest.merchantvalidation_event", "merchantvalidation")}} را توصیف می‌کند؛ این رویداد به پرداخت‌یار ارسال می‌شود تا از آن بخواهد فروشنده را تأیید کند.

## ویژگی‌های نمونه (Instance properties)

- {{domxref("MerchantValidationEvent.methodName")}} {{Deprecated_Inline}} {{non-standard_inline}}
  - : یک رشته که شناسهٔ یکتای روش پرداخت را برای پرداخت‌یاری که نیاز به تأیید دارد فراهم می‌کند. این مقدار می‌تواند یکی از رشته‌های شناسهٔ استاندارد روش پرداخت باشد یا یک URL که هم پرداخت‌یار را شناسایی می‌کند و هم درخواست‌های مربوط به آن را مدیریت می‌کند، مانند `https://apple.com/apple-pay`.
- {{domxref("MerchantValidationEvent.validationURL")}} {{Deprecated_Inline}} {{non-standard_inline}}
  - : یک رشته که URL ای را مشخص می‌کند که سایت یا برنامه می‌تواند اطلاعات تأیید مخصوص پرداخت‌یار را از آن دریافت کند. پس از دریافت این داده‌ها، داده (یا یک promise که به دادهٔ تأیید حل می‌شود) باید به {{domxref("MerchantValidationEvent.complete", "complete()")}} ارسال شود تا تأیید شود که درخواست پرداخت از یک فروشندهٔ مجاز صادر شده است.

## روش‌های نمونه (Instance methods)

- {{domxref("MerchantValidationEvent.complete()")}} {{Deprecated_Inline}} {{non-standard_inline}}
  - : داده‌های دریافت‌شده از URL مشخص‌شده توسط {{domxref("MerchantValidationEvent.validationURL", "validationURL")}} را به `complete()` ارسال کنید تا فرایند تأیید برای {{domxref("PaymentRequest")}} تکمیل شود.

## سازگاری مرورگر

{{Compat}}