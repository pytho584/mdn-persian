---
title: "PublicKeyCredential: toJSON() method"
short-title: toJSON()
slug: Web/API/PublicKeyCredential/toJSON
page-type: web-api-instance-method
browser-compat: api.PublicKeyCredential.toJSON
---

{{APIRef("Web Authentication API")}}{{securecontext_header}}

متد **`toJSON()`** از واسط {{domxref("PublicKeyCredential")}} یک {{glossary("JSON type representation")}} از یک {{domxref("PublicKeyCredential")}} را برمی‌گرداند.

ویژگی‌های شیء بازگشتی بستگی به این دارد که آن اعتبارنامه (credential) هنگام [ایجاد جفت‌کلید و ثبت‌نام کاربر](/en-US/docs/Web/API/Web_Authentication_API#creating_a_key_pair_and_registering_a_user) توسط [`navigator.credentials.create()`](/en-US/docs/Web/API/CredentialsContainer/create) بازگردانده شده باشد یا هنگام [احراز هویت کاربر](/en-US/docs/Web/API/Web_Authentication_API#authenticating_a_user) توسط [`navigator.credentials.get()`](/en-US/docs/Web/API/CredentialsContainer/get).

هنگامی که کد برنامهٔ وب برای ارسال یک {{domxref("PublicKeyCredential")}} به سرورِ طرفِ معتمد (relying party) هنگام ثبت‌نام یا احراز هویت، آن را سریال‌سازی می‌کند، این متد به‌صورت خودکار در پاسخ به [`JSON.stringify()`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify) فراخوانی می‌شود. این متد برای فراخوانی مستقیم از کد برنامهٔ وب در نظر گرفته نشده است.

## سینتکس

```js-nolint
toJSON()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{glossary("JSON type representation")}} از یک شیء [`PublicKeyCredential`](/en-US/docs/Web/API/PublicKeyCredential).

ویژگی‌های موجود به این بستگی دارند که اعتبارنامه هنگام ثبت‌نام توسط [`navigator.credentials.create()`](/en-US/docs/Web/API/CredentialsContainer/create) بازگردانده شده باشد یا هنگام احراز هویت کاربر توسط [`navigator.credentials.get()`](/en-US/docs/Web/API/CredentialsContainer/get). مقادیر و انواع ویژگی‌های موجود مانند [`PublicKeyCredential`](/en-US/docs/Web/API/PublicKeyCredential) هستند، با این تفاوت که به‌جای ویژگی‌های بافر (buffer) از رشته‌های کدگذاری‌شده با [base64url](/en-US/docs/Glossary/Base64) استفاده می‌شود.

ویژگی‌های شیء عبارت‌اند از:

- `id`
  - : مقداری که توسط {{domxref("PublicKeyCredential.id")}} بازگردانده می‌شود.
- `rawId`
  - : نسخهٔ کدگذاری‌شده با [base64url](/en-US/docs/Glossary/Base64) از {{domxref("PublicKeyCredential.rawId")}}.
- `authenticatorAttachment` {{optional_inline}}
  - : مقداری که توسط {{domxref("PublicKeyCredential.authenticatorAttachment")}} بازگردانده می‌شود.
- `type`
  - : رشتهٔ `"public-key"`.
- `clientExtensionResults`
  - : آرایه‌ای شامل نسخه‌های کدگذاری‌شده با [base64url](/en-US/docs/Glossary/Base64) از مقادیری که توسط {{domxref("PublicKeyCredential.getClientExtensionResults()")}} بازگردانده شده‌اند.
- `response`
  - : شیء موجود در ویژگی `response` بستگی دارد به اینکه اعتبارنامه‌ها پس از یک عملیات ثبت‌نام یا یک عملیات احراز هویت بازگردانده شده باشند.
    - هنگام ثبت‌نام یک کاربر جدید، `response` یک {{glossary("JSON type representation")}} از {{domxref("AuthenticatorAttestationResponse")}} خواهد بود که در آن مقادیر بافر با [base64url](/en-US/docs/Glossary/Base64) کدگذاری شده‌اند.

    - هنگام احراز هویت یک کاربر، مقدار بازگشتی نسخه‌ای از {{glossary("JSON type representation")}} مربوط به {{domxref("AuthenticatorAssertionResponse")}} خواهد بود که در آن مقادیر بافر با [base64url](/en-US/docs/Glossary/Base64) کدگذاری شده‌اند.

### استثناها

- `SecurityError` {{domxref("DOMException")}}
  - : دامنهٔ طرف معتمد (RP) نامعتبر است.

## مثال‌ها

هنگام ثبت‌نام یک کاربر جدید، سرورِ طرف معتمد (relying party) اطلاعاتی دربارهٔ اعتبارنامه‌های مورد انتظار در اختیار برنامهٔ وب قرار می‌دهد. برنامهٔ وب، [`navigator.credentials.create()`](/en-US/docs/Web/API/CredentialsContainer/create) را با اطلاعات دریافتی (`createCredentialOptions` در زیر) فراخوانی می‌کند؛ این فراخوانی یک Promise برمی‌گرداند که با اعتبارنامهٔ جدید (یک {{domxref("PublicKeyCredential")}}) برآورده می‌شود.

```js
const newCredentialInfo = await navigator.credentials.create({
  createCredentialOptions,
});
```

سپس برنامهٔ وب، اعتبارنامهٔ بازگشتی را با استفاده از `JSON.stringify()` سریال‌سازی می‌کند (که به نوبهٔ خود `toJSON()` را فراخوانی می‌کند) و آن را دوباره برای سرور ارسال می‌کند.

```js
const registrationURL = "https://example.com/registration";
const apiRegOptsResp = await fetch(registrationURL, {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify(newCredentialInfo), // Calls newCredentialInfo.toJSON
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Web Authentication API](/en-US/docs/Web/API/Web_Authentication_API)
- {{domxref("PublicKeyCredential.parseCreationOptionsFromJSON_static", "PublicKeyCredential.parseCreationOptionsFromJSON()")}}
- {{domxref("PublicKeyCredential.parseRequestOptionsFromJSON_static", "PublicKeyCredential.parseRequestOptionsFromJSON()")}}