---
title: "AuthenticatorAttestationResponse: getAuthenticatorData() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AuthenticatorAttestationResponse/getAuthenticatorData"
translated_by: "n8n + AI"
---

---
title: "AuthenticatorAttestationResponse: getAuthenticatorData() method"
short-title: getAuthenticatorData()
slug: Web/API/AuthenticatorAttestationResponse/getAuthenticatorData
page-type: web-api-instance-method
browser-compat: api.AuthenticatorAttestationResponse.getAuthenticatorData
---

{{APIRef("Web Authentication API")}}{{securecontext_header}}

متد **`getAuthenticatorData()`** از رابط {{domxref("AuthenticatorAttestationResponse")}} یک {{jsxref("ArrayBuffer")}} حاوی داده‌های احراز هویت موجود در ویژگی {{domxref("AuthenticatorAttestationResponse.attestationObject")}} را برمی‌گرداند.

این یک تابع کمکی است که برای دسترسی آسان به داده‌های احراز هویت بدون نیاز به نوشتن کد تجزیه اضافی برای استخراج آن از `attestationObject` ایجاد شده است.

## Syntax

```js-nolint
getAuthenticatorData()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("ArrayBuffer")}} با {{jsxref("ArrayBuffer.byteLength", "byteLength")}} حداقل ۳۷ بایت، که شامل ساختار داده توضیح داده شده در [Authenticator data](/en-US/docs/Web/API/Web_Authentication_API/Authenticator_data) است.

این معادل داده‌های احراز هویت موجود در ویژگی {{domxref("AuthenticatorAttestationResponse.attestationObject")}} خواهد بود.

## مثال‌ها

برای یک مثال کامل، [ایجاد یک اعتبارنامه کلید عمومی](/en-US/docs/Web/API/CredentialsContainer/create#creating_a_public_key_credential) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}