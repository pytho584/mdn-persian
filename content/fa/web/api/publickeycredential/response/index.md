---
title: "PublicKeyCredential: response property"
short-title: response
slug: Web/API/PublicKeyCredential/response
page-type: web-api-instance-property
browser-compat: api.PublicKeyCredential.response
---

{{APIRef("Web Authentication API")}}{{securecontext_header}}

ویژگی فقط‌خواندنی **`response`** در رابط {{domxref("PublicKeyCredential")}} یک شیء {{domxref("AuthenticatorResponse")}} است که از سمت authenticator به عامل کاربر (user agent) ارسال می‌شود تا اعتبارنامه‌ها ساخته یا دریافت شوند. اطلاعات موجود در این پاسخ، توسط سرور طرف وابسته (relying party) برای تأیید قانونی‌بودن درخواست استفاده خواهد شد.

یک `AuthenticatorResponse` به یکی از دو شکل زیر است:

- یک {{domxref("AuthenticatorAttestationResponse")}} (زمانی که `PublicKeyCredential` از طریق {{domxref("CredentialsContainer.create()")}} ساخته شده باشد)
- یک {{domxref("AuthenticatorAssertionResponse")}} (زمانی که `PublicKeyCredential` از طریق {{domxref("CredentialsContainer.get()")}} به‌دست آمده باشد).

برای اعتبارسنجی _ساخت_ اعتبارنامه‌ها، سرور طرف وابسته به هر دوی موارد زیر نیاز دارد:

- همین پاسخ
- افزونه‌های کلاینت (که با {{domxref("PublicKeyCredential.getClientExtensionResults()")}} به دست می‌آیند) برای اعتبارسنجی درخواست.

> [!NOTE]
> هنگام اعتبارسنجی دریافت اعتبارنامه‌های موجود، کل شیء `PublicKeyCredential` و افزونه‌های کلاینت برای سرور طرف وابسته لازم هستند.

> [!NOTE]
> این ویژگی فقط در زمینه‌های سطح بالا (top-level contexts) قابل استفاده است و به‌عنوان مثال در یک {{HTMLElement("iframe")}} در دسترس نخواهد بود.

## مقدار

یک شیء {{domxref("AuthenticatorResponse")}} شامل داده‌هایی است که اسکریپت طرف وابسته دریافت می‌کند و باید برای اعتبارسنجی درخواست ساخت یا دریافت، به سرور طرف وابسته ارسال شود. این شیء شامل داده‌هایی از سمت کلاینت ({{domxref("AuthenticatorResponse/clientDataJSON")}}) و داده‌هایی از سمت authenticator است.

## مثال‌ها

```js
const options = {
  challenge: new Uint8Array(16) /* from the server */,
  rp: {
    name: "Example CORP",
    id: "login.example.com",
  },
  user: {
    id: new Uint8Array(16) /* from the server */,
    name: "canand@example.com",
    displayName: "Carina Anand",
  },
  pubKeyCredParams: [
    {
      type: "public-key",
      alg: -7,
    },
  ],
};

navigator.credentials
  .create({ publicKey: options })
  .then((pubKeyCredential) => {
    const response = pubKeyCredential.response;
    const clientExtResults = pubKeyCredential.getClientExtensionResults();
    // Send response and client extensions to the server so that it can validate
    // and create credentials
  })
  .catch((err) => {
    // Deal with any error
  });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}