```
---
title: "PublicKeyCredential: getClientExtensionResults() method"
short-title: getClientExtensionResults()
slug: Web/API/PublicKeyCredential/getClientExtensionResults
page-type: web-api-instance-method
browser-compat: api.PublicKeyCredential.getClientExtensionResults
---

{{APIRef("Web Authentication API")}}{{securecontext_header}}

متد **`getClientExtensionResults()`** از رابط {{domxref("PublicKeyCredential")}} یک شیء برمی‌گرداند که در آن، شناسهٔ هر افزونهٔ درخواست‌شده در هنگام ایجاد یا احراز هویت اعتبارنامه، به نتیجهٔ پردازش آن افزونه توسط عامل کاربر نگاشت می‌شود.

در هنگام ایجاد یا دریافت یک `PublicKeyCredential` (به ترتیب از طریق {{domxref("CredentialsContainer.create()","navigator.credentials.create()")}} و {{domxref("CredentialsContainer.get()","navigator.credentials.get()")}})، امکان درخواست پردازش «سفارشی» توسط کلاینت برای افزونه‌های مختلف وجود دارد؛ این افزونه‌ها در ویژگی `extensions` گزینهٔ `publicKey` مشخص می‌شوند. اطلاعات بیشتر دربارهٔ نحوهٔ درخواست افزونه‌های مختلف را می‌توانید در [افزونه‌های Web Authentication](/en-US/docs/Web/API/Web_Authentication_API/WebAuthn_extensions) بیابید.

> [!NOTE]
> `getClientExtensionResults()` فقط نتایج حاصل از افزونه‌هایی را برمی‌گرداند که توسط عامل کاربر (کلاینت) پردازش شده‌اند. نتایج افزونه‌های پردازش‌شده توسط اثباتگر (authenticator) را می‌توانید در [داده‌های authenticator](/en-US/docs/Web/API/Web_Authentication_API/Authenticator_data) موجود در {{domxref("AuthenticatorAssertionResponse.authenticatorData")}} بیابید.

## نحو

```js-nolint
getClientExtensionResults()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک شیء که در هر ورودی آن، رشته شناسه یک افزونه به‌عنوان کلید و خروجی پردازش آن افزونه توسط کلاینت به‌عنوان مقدار قرار می‌گیرد.

### استثناها

- `SecurityError` {{domxref("DOMException")}}
  - : دامنهٔ RP (Relying Party) معتبر نیست.

## نمونه‌ها

```js
const publicKey = {
  // Here are the extension "inputs"
  extensions: {
    appid: "https://accounts.example.com",
  },
  allowCredentials: {
    id: "fgrt46jfgd...",
    transports: ["usb", "nfc"],
    type: "public-key",
  },
  challenge: new Uint8Array(16) /* from the server */,
};

navigator.credentials
  .get({ publicKey })
  .then((publicKeyCred) => {
    const myResults = publicKeyCred.getClientExtensionResults();
    // myResults will contain the output of processing the "appid" extension
  })
  .catch((err) => {
    console.error(err);
  });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

> [!NOTE]
> افزونه‌ها اختیاری هستند و مرورگرهای مختلف ممکن است افزونه‌های متفاوتی را شناسایی کنند. پردازش افزونه‌ها برای کلاینت همیشه اختیاری است: اگر مرورگری افزونه‌ای معین را نشناسد، صرفاً آن را نادیده می‌گیرد. برای اطلاع از اینکه کدام افزونه‌ها توسط کدام مرورگرها پشتیبانی می‌شوند، به [افزونه‌های Web Authentication](/en-US/docs/Web/API/Web_Authentication_API/WebAuthn_extensions) مراجعه کنید.

## همچنین ببینید

- [فهرست افزونه‌های تعریف‌شدهٔ فعلی](https://w3c.github.io/webauthn/#sctn-defined-extensions)
- {{domxref("AuthenticatorAssertionResponse.authenticatorData")}} که حاوی نتیجهٔ پردازش افزونه‌ها توسط اثباتگر (authenticator) است.
```