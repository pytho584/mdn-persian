```
---
title: PublicKeyCredential
slug: Web/API/PublicKeyCredential
page-type: web-api-interface
browser-compat: api.PublicKeyCredential
---

{{APIRef("Web Authentication API")}}{{securecontext_header}}

رابط **`PublicKeyCredential`** اطلاعاتی درباره یک جفت‌کلید عمومی/خصوصی فراهم می‌کند؛ این جفت‌کلید یک اعتبارنامه برای ورود به یک سرویس با استفاده از کلیدهای نامتقارنی است که در برابر فیشینگ و نشت داده‌ها مقاوم هستند و به‌جای رمز عبور استفاده می‌شوند. این رابط از {{domxref("Credential")}} به ارث می‌رسد و بخشی از افزونه [Web Authentication API](/en-US/docs/Web/API/Web_Authentication_API) برای [Credential Management API](/en-US/docs/Web/API/Credential_Management_API) است.

{{InheritanceDiagram}}

> [!NOTE]
> این API به زمینه‌های سطح بالا محدود است. استفاده از آن درون عنصر {{HTMLElement("iframe")}} هیچ اثری نخواهد داشت.

## ویژگی‌های نمونه

- {{domxref("PublicKeyCredential.authenticatorAttachment")}} {{ReadOnlyInline}}
  - : رشته‌ای که سازوکار اتصال پیاده‌سازی WebAuthn به authenticator را در لحظه تکمیل فراخوانی مرتبط {{domxref("CredentialsContainer.create()","navigator.credentials.create()")}} یا {{domxref("CredentialsContainer.get()","navigator.credentials.get()")}} نشان می‌دهد.

- {{domxref("PublicKeyCredential.id")}} {{ReadOnlyInline}}
  - : از {{domxref("Credential")}} به ارث رسیده و برای نمایش به‌صورت [کدگذاری base64url](/en-US/docs/Glossary/Base64) از {{domxref("PublicKeyCredential.rawId")}} بازنویسی شده است.

- {{domxref("PublicKeyCredential.rawId")}} {{ReadOnlyInline}}
  - : یک {{jsxref("ArrayBuffer")}} که شناسه یکتای سراسری این `PublicKeyCredential` را نگه می‌دارد. از این شناسه می‌توان برای جست‌وجوی اعتبارنامه‌ها در فراخوانی‌های آینده {{domxref("CredentialsContainer.get()","navigator.credentials.get()")}} استفاده کرد.

- {{domxref("PublicKeyCredential.response")}} {{ReadOnlyInline}}
  - : نمونه‌ای از یک شیء {{domxref("AuthenticatorResponse")}} است. اگر `PublicKeyCredential` حاصل یک فراخوانی {{domxref("CredentialsContainer.create()","navigator.credentials.create()")}} باشد، نوع آن {{domxref("AuthenticatorAttestationResponse")}} خواهد بود و اگر حاصل فراخوانی {{domxref("CredentialsContainer.get()","navigator.credentials.get()")}} باشد، نوع آن {{domxref("AuthenticatorAssertionResponse")}} است.

- `PublicKeyCredential.type` {{ReadOnlyInline}}
  - : از {{domxref("Credential")}} به ارث رسیده است. برای نمونه‌های `PublicKeyCredential` همیشه برابر با `public-key` است.

## متدهای استاتیک

- {{domxref("PublicKeyCredential.getClientCapabilities_static", "PublicKeyCredential.getClientCapabilities()")}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند که با یک شیء resolve می‌شود و می‌توان از آن برای بررسی اینکه آیا قابلیت‌ها و [افزونه‌های](/en-US/docs/Web/API/Web_Authentication_API/WebAuthn_extensions) خاص WebAuthn پشتیبانی می‌شوند یا نه استفاده کرد.

- {{domxref("PublicKeyCredential.isConditionalMediationAvailable_static", "PublicKeyCredential.isConditionalMediationAvailable()")}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند که اگر میانجی‌گری شرطی (conditional mediation) در دسترس باشد، به `true` resolve می‌شود.

- {{domxref("PublicKeyCredential.isUserVerifyingPlatformAuthenticatorAvailable_static", "PublicKeyCredential.isUserVerifyingPlatformAuthenticatorAvailable()")}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند که اگر یک authenticator متصل به پلتفرم قادر به _تأیید هویت_ کاربر باشد، به `true` resolve می‌شود.

- {{domxref("PublicKeyCredential.parseCreationOptionsFromJSON_static", "PublicKeyCredential.parseCreationOptionsFromJSON()")}}
  - : یک متد کمکی برای تبدیل داده‌های ثبت اعتبارنامه ارسال‌شده از سمت سرور هنگام [ثبت‌نام کاربر با اعتبارنامه‌ها](/en-US/docs/Web/API/Web_Authentication_API#creating_a_key_pair_and_registering_a_user) است.

- {{domxref("PublicKeyCredential.parseRequestOptionsFromJSON_static", "PublicKeyCredential.parseRequestOptionsFromJSON()")}}
  - : یک متد کمکی برای تبدیل داده‌های درخواست اعتبارنامه ارسال‌شده از سمت سرور هنگام [احراز هویت یک کاربر (ثبت‌شده)](/en-US/docs/Web/API/Web_Authentication_API#authenticating_a_user) است.

- {{domxref("PublicKeyCredential.signalAllAcceptedCredentials_static", "PublicKeyCredential.signalAllAcceptedCredentials()")}}
  - : همه [شناسه‌های اعتبارنامه](/en-US/docs/Web/API/PublicKeyCredentialRequestOptions#id) معتبری را که سرور [طرف اتکا](https://en.wikipedia.org/wiki/Relying_party) هنوز برای یک کاربر خاص نگه می‌دارد، به authenticator اعلام می‌کند.

- {{domxref("PublicKeyCredential.signalCurrentUserDetails_static", "PublicKeyCredential.signalCurrentUserDetails()")}}
  - : به authenticator اعلام می‌کند که یک کاربر مشخص، نام کاربری و/یا نام نمایشی خود را به‌روزرسانی کرده است.

- {{domxref("PublicKeyCredential.signalUnknownCredential_static", "PublicKeyCredential.signalUnknownCredential()")}}
  - : به authenticator اعلام می‌کند که یک [شناسه اعتبارنامه](/en-US/docs/Web/API/PublicKeyCredentialRequestOptions#id) توسط سرور [طرف اتکا](https://en.wikipedia.org/wiki/Relying_party) شناسایی نشده است؛ برای مثال به این دلیل که حذف شده است.

## متدهای نمونه

- {{domxref("PublicKeyCredential.getClientExtensionResults()")}}
  - : اگر افزونه‌ای درخواست شده باشد، این متد نتیجه پردازش آن افزونه‌ها را برمی‌گرداند.

- {{domxref("PublicKeyCredential.toJSON()")}}
  - : یک متد کمکی برای ایجاد یک نمایش رشته JSON از یک `PublicKeyCredential` به منظور ارسال به سرور هنگام [ثبت‌نام کاربر با اعتبارنامه‌ها](/en-US/docs/Web/API/Web_Authentication_API#creating_a_key_pair_and_registering_a_user) و [احراز هویت یک کاربر ثبت‌شده](/en-US/docs/Web/API/Web_Authentication_API#authenticating_a_user) است.

## مثال‌ها

### ایجاد یک نمونه جدید از PublicKeyCredential

در اینجا، از {{domxref("CredentialsContainer.create()","navigator.credentials.create()")}} برای تولید یک اعتبارنامه جدید استفاده می‌کنیم.

```js
const createCredentialOptions = {
  publicKey: {
    challenge: new Uint8Array([
      21, 31, 105 /* 29 more random bytes generated by the server */,
    ]),
    rp: {
      name: "Example CORP",
      id: "login.example.com",
    },
    user: {
      id: new Uint8Array(16),
      name: "canand@example.com",
      displayName: "Carina Anand",
    },
    pubKeyCredParams: [
      {
        type: "public-key",
        alg: -7,
      },
    ],
  },
};

navigator.credentials
  .create(createCredentialOptions)
  .then((newCredentialInfo) => {
    const response = newCredentialInfo.response;
    const clientExtensionsResults =
      newCredentialInfo.getClientExtensionResults();
  })
  .catch((err) => {
    console.error(err);
  });
```

### دریافت یک نمونه موجود از PublicKeyCredential

در اینجا، با استفاده از {{domxref("CredentialsContainer.get()","navigator.credentials.get()")}} یک اعتبارنامه موجود را از authenticator دریافت می‌کنیم.

```js
const requestCredentialOptions = {
  publicKey: {
    challenge: new Uint8Array([/* bytes sent from the server */]),
  },
};

navigator.credentials
  .get(requestCredentialOptions)
  .then((credentialInfoAssertion) => {
    // send assertion response back to the server
    // to proceed with the control of the credential
  })
  .catch((err) => {
    console.error(err);
  });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط والد {{domxref("Credential")}}
```