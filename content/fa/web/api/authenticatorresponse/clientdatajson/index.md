---
title: "AuthenticatorResponse: clientDataJSON property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AuthenticatorResponse/clientDataJSON"
translated_by: "n8n + AI"
---

---
title: "AuthenticatorResponse: clientDataJSON property"
short-title: clientDataJSON
slug: Web/API/AuthenticatorResponse/clientDataJSON
page-type: web-api-instance-property
browser-compat: api.AuthenticatorResponse.clientDataJSON
---

{{APIRef("Web Authentication API")}}{{securecontext_header}}

ویژگی **`clientDataJSON`** در رابط {{domxref("AuthenticatorResponse")}} یک رشته [JSON](/en-US/docs/Learn_web_development/Core/Scripting/JSON) را در یک {{jsxref("ArrayBuffer")}} ذخیره می‌کند که داده‌های کلاینت ارسال‌شده به {{domxref("CredentialsContainer.create()", "navigator.credentials.create()")}} یا {{domxref("CredentialsContainer.get()", "navigator.credentials.get()")}} را نشان می‌دهد. این ویژگی فقط بر روی یکی از اشیاء فرزند `AuthenticatorResponse` قابل دسترسی است، به‌طور خاص {{domxref("AuthenticatorAttestationResponse")}} یا {{domxref("AuthenticatorAssertionResponse")}}.

## مقدار

یک {{jsxref("ArrayBuffer")}}.

## ویژگی‌های نمونه

پس از اینکه شیء `clientDataJSON` از یک `ArrayBuffer` به یک شیء جاوااسکریپت تبدیل شود، دارای ویژگی‌های زیر خواهد بود:

- `challenge`
  - : نسخه‌ی کدگذاری‌شده‌ی [base64url](/en-US/docs/Glossary/Base64) از چالش رمزنگاری ارسال‌شده از سرور طرف اعتماد. مقدار اصلی به‌عنوان گزینه‌ی `challenge` در {{domxref("CredentialsContainer.get()")}} یا {{domxref("CredentialsContainer.create()")}} ارسال می‌شود.

- `crossOrigin` {{optional_inline}}
  - : یک مقدار بولین. اگر روی `true` تنظیم شود، به این معنی است که زمینه‌ی فراخوانی یک {{htmlelement("iframe")}} است که با فریم‌های بالادستی خود هم‌مبدأ نیست.

- `origin`
  - : مبدأ کاملاً واجد شرایط (fully qualified) طرف اعتماد که توسط کلاینت/مرورگر به احرازهویت‌کننده (authenticator) داده شده است. باید انتظار داشته باشیم که _شناسه‌ی طرف اعتماد_ پسوندی از این مقدار باشد.

- `tokenBinding` {{optional_inline}} {{deprecated_inline}}
  - : یک شیء که وضعیت [پروتکل اتصال توکن (token binding)](https://datatracker.ietf.org/doc/html/rfc8471) را برای ارتباط با طرف اعتماد توصیف می‌کند. این شیء دارای دو ویژگی است:
    - `status`: یک رشته که یا `"supported"` است، که نشان می‌دهد کلاینت از اتصال توکن پشتیبانی می‌کند اما با طرف اعتماد مذاکره نکرده است، یا `"present"` زمانی که اتصال توکن قبلاً استفاده شده است.
    - `id`: یک رشته که [base64url](/en-US/docs/Glossary/Base64) شناسه‌ی اتصال توکن (token binding ID) استفاده‌شده برای ارتباط است.

    اگر این ویژگی وجود نداشته باشد، نشان می‌دهد که کلاینت از اتصال توکن پشتیبانی نمی‌کند.

    > [!NOTE]
    > `tokenBinding` از سطح 3 (Level 3) مشخصات (spec) منسوخ شده است، اما این فیلد محفوظ است تا برای هدف دیگری استفاده نشود.

- `topOrigin` {{optional_inline}}
  - : شامل مبدأ کاملاً واجد شرایط سطح بالای طرف اعتماد است. فقط اگر `crossOrigin` برابر با `true` باشد تنظیم می‌شود.

- `type`
  - : یک رشته که یا `"webauthn.get"` است زمانی که یک اعتبارنامه‌ی موجود بازیابی می‌شود، یا `"webauthn.create"` زمانی که یک اعتبارنامه‌ی جدید ایجاد می‌شود.

## مثال‌ها

```js
function arrayBufferToStr(buf) {
  return String.fromCharCode.apply(null, new Uint8Array(buf));
}

// pk is a PublicKeyCredential that is the result of a create() or get() Promise
const clientDataStr = arrayBufferToStr(pk.response.clientDataJSON);
const clientDataObj = JSON.parse(clientDataStr);

console.log(clientDataObj.type); // "webauthn.create" or "webauthn.get"
console.log(clientDataObj.challenge); // base64 encoded String containing the original challenge
console.log(clientDataObj.origin); // the window.origin
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}