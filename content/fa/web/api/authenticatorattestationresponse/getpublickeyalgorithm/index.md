---
title: "AuthenticatorAttestationResponse: getPublicKeyAlgorithm() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AuthenticatorAttestationResponse/getPublicKeyAlgorithm"
translated_by: "n8n + AI"
---

---
title: "AuthenticatorAttestationResponse: getPublicKeyAlgorithm() method"
short-title: getPublicKeyAlgorithm()
slug: Web/API/AuthenticatorAttestationResponse/getPublicKeyAlgorithm
page-type: web-api-instance-method
browser-compat: api.AuthenticatorAttestationResponse.getPublicKeyAlgorithm
---

{{APIRef("Web Authentication API")}}{{securecontext_header}}

متد **`getPublicKeyAlgorithm()`** از رابط {{domxref("AuthenticatorAttestationResponse")}} عددی را برمی‌گرداند که برابر با [شناسه الگوریتم COSE](https://www.iana.org/assignments/cose/cose.xhtml#algorithms) است و الگوریتم رمزنگاری استفاده‌شده برای اعتبارنامه جدید را نشان می‌دهد.

این یک تابع کمکی است که برای دسترسی آسان به نوع الگوریتم ایجاد شده است. این اطلاعات باید ذخیره شود تا عملیات احراز هویت آینده (به عنوان مثال، با استفاده از {{domxref("CredentialsContainer.get()","navigator.credentials.get()")}}) تأیید شود.

## نحو

```js-nolint
getPublicKeyAlgorithm()
```

### پارامترها

هیچ.

### مقدار بازگشتی

عددی که برابر با [شناسه الگوریتم COSE](https://www.iana.org/assignments/cose/cose.xhtml#algorithms) است و الگوریتم رمزنگاری استفاده‌شده برای اعتبارنامه جدید را نشان می‌دهد.

## مثال‌ها

برای یک مثال دقیق، [ایجاد یک اعتبارنامه کلید عمومی](/en-US/docs/Web/API/CredentialsContainer/create#creating_a_public_key_credential) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}