---
title: "AuthenticatorAttestationResponse: getPublicKey() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AuthenticatorAttestationResponse/getPublicKey"
translated_by: "n8n + AI"
---

---
title: "AuthenticatorAttestationResponse: getPublicKey() method"
short-title: getPublicKey()
slug: Web/API/AuthenticatorAttestationResponse/getPublicKey
page-type: web-api-instance-method
browser-compat: api.AuthenticatorAttestationResponse.getPublicKey
---

{{APIRef("Web Authentication API")}}{{securecontext_header}}

متد **`getPublicKey()`** از رابط {{domxref("AuthenticatorAttestationResponse")}} یک {{jsxref("ArrayBuffer")}} حاوی `SubjectPublicKeyInfo` DER اعتبارنامه جدید (مشاهده کنید [Subject Public Key Info](https://www.rfc-editor.org/info/rfc5280/#section-4.1.2.7)) را برمی‌گرداند، یا اگر در دسترس نباشد `null` را برمی‌گرداند.

این یک تابع کمکی است که برای دسترسی آسان به کلید عمومی ایجاد شده است. این کلید باید برای تأیید عملیات احراز هویت آینده ذخیره شود (یعنی با استفاده از {{domxref("CredentialsContainer.get()","navigator.credentials.get()")}}).

## نحو

```js-nolint
getPublicKey()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک {{jsxref("ArrayBuffer")}} حاوی `SubjectPublicKeyInfo` DER اعتبارنامه جدید (مشاهده کنید [Subject Public Key Info](https://www.rfc-editor.org/info/rfc5280/#section-4.1.2.7))، یا اگر در دسترس نباشد `null`.

## مثال‌ها

برای یک مثال دقیق، [ایجاد یک اعتبارنامه کلید عمومی](/en-US/docs/Web/API/CredentialsContainer/create#creating_a_public_key_credential) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}