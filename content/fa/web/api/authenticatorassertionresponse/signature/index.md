---
title: "AuthenticatorAssertionResponse: signature property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AuthenticatorAssertionResponse/signature"
translated_by: "n8n + AI"
---

---
title: "AuthenticatorAssertionResponse: signature property"
short-title: signature
slug: Web/API/AuthenticatorAssertionResponse/signature
page-type: web-api-instance-property
browser-compat: api.AuthenticatorAssertionResponse.signature
---

{{APIRef("Web Authentication API")}}{{securecontext_header}}

ویژگی فقط‌خواندنی **`signature`** از رابط {{domxref("AuthenticatorAssertionResponse")}} یک شیء {{jsxref("ArrayBuffer")}} است که امضای احرازکننده برای هر دو {{domxref("AuthenticatorAssertionResponse.authenticatorData")}} و یک هش SHA-256 از داده‌های کلاینت ({{domxref("AuthenticatorResponse.clientDataJSON","AuthenticatorAssertionResponse.clientDataJSON")}}) است.

این امضا به‌عنوان بخشی از پاسخ، برای بررسی به سرور ارسال می‌شود. این امضا ثابت می‌کند که احرازکننده دارای کلید خصوصی‌ای است که برای تولید اعتبارنامه استفاده شده است.

## مقدار

یک شیء {{jsxref("ArrayBuffer")}} که امضای احرازکننده (با استفاده از کلید خصوصی آن) برای هر دو {{domxref("AuthenticatorAssertionResponse.authenticatorData")}} و یک هش SHA-256 از داده‌های کلاینت (چالش، مبدأ و غیره) است که از {{domxref("AuthenticatorResponse.clientDataJSON","AuthenticatorAssertionResponse.clientDataJSON")}} در دسترس است.

## مثال‌ها

برای یک مثال مفصل، [Retrieving a public key credential](/en-US/docs/Web/API/CredentialsContainer/get#retrieving_a_public_key_credential) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}