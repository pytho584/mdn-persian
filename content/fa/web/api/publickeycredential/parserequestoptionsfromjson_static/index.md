---
title: "PublicKeyCredential: parseRequestOptionsFromJSON() static method"
short-title: parseRequestOptionsFromJSON()
slug: Web/API/PublicKeyCredential/parseRequestOptionsFromJSON_static
page-type: web-api-static-method
browser-compat: api.PublicKeyCredential.parseRequestOptionsFromJSON_static
---

{{APIRef("Web Authentication API")}}{{securecontext_header}}

متد ایستای **`parseRequestOptionsFromJSON()`** از رابط {{domxref("PublicKeyCredential")}} یک {{glossary("JSON type representation")}} را به یک نمونه از {{domxref("PublicKeyCredentialRequestOptions")}} تبدیل می‌کند.

این متد یک تابع کمکی برای تبدیل اطلاعات ارائه‌شده توسط سرور طرف اتکا (relying party) به برنامه وب است تا بتواند یک اعتبارنامه (credential) موجود را درخواست کند.

## نحو

```js-nolint
PublicKeyCredential.parseRequestOptionsFromJSON(options)
```

### پارامترها

- `options`
  - : شیئی با همان ساختار یک نمونه {{domxref("PublicKeyCredentialRequestOptions")}}، اما به جای ویژگی‌های بافر (buffer) از رشته‌های [base64url](/en-US/docs/Glossary/Base64) استفاده شده است.

### مقدار بازگشتی

یک نمونه از {{domxref("PublicKeyCredentialRequestOptions")}}.

### استثناها

- `EncodingError` {{domxref("DOMException")}}
  - : اگر هر بخشی از شیء `options` نتواند به یک نمونه {{domxref("PublicKeyCredentialRequestOptions")}} تبدیل شود، پرتاب می‌شود.
- `SecurityError` {{domxref("DOMException")}}
  - : دامنه طرف اتکا (RP) معتبر نیست.

## توضیحات

فرایند Web Authentication برای [احراز هویت یک کاربر (از قبل ثبت‌نام‌شده)](/en-US/docs/Web/API/Web_Authentication_API#authenticating_a_user) شامل این است که سرور طرف اتکا اطلاعات لازم برای یافتن یک اعتبارنامه موجود را به برنامه وب ارسال کند؛ از جمله جزئیاتی درباره هویت کاربر، طرف اتکا، یک «چالش» (challenge) و به‌صورت اختیاری محل جستجوی اعتبارنامه: برای مثال در یک احرازکننده داخلی دستگاه، یا در یک احرازکننده خارجی متصل از طریق USB، BLE و غیره.

برنامه وب این اطلاعات را برای یافتن اعتبارنامه به یک احرازکننده منتقل می‌کند؛ بدین منظور تابع [`navigator.credentials.get()`](/en-US/docs/Web/API/CredentialsContainer/get) را با آرگومانی فراخوانی می‌کند که داده‌های ارائه‌شده توسط سرور را به‌صورت یک نمونه {{domxref("PublicKeyCredentialRequestOptions")}} در بر دارد.

این مشخصات تعیین نمی‌کند که اطلاعات لازم برای درخواست یک اعتبارنامه چگونه ارسال شود. رویکردی مناسب این است که سرور اطلاعات را در یک {{glossary("JSON type representation")}} از نمونه {{domxref("PublicKeyCredentialRequestOptions")}} بسته‌بندی کند؛ بازنمایی‌ای که ساختار آن را منعکس می‌کند، اما ویژگی‌های بافر مانند `challenge` را به‌صورت رشته‌های [base64url](/en-US/docs/Glossary/Base64) کدگذاری می‌کند. این شیء را می‌توان به یک رشته [JSON](/en-US/docs/Glossary/JSON) سریال کرد، به برنامه وب فرستاد، از حالت سریال خارج کرد و سپس با استفاده از **`parseRequestOptionsFromJSON()`** به یک نمونه {{domxref("PublicKeyCredentialRequestOptions")}} تبدیل کرد.

## مثال‌ها

هنگام اعطای مجوز به یک کاربر از قبل ثبت‌نام‌شده، سرور طرف اتکا اطلاعات مربوط به اعتبارنامه‌های درخواستی، طرف اتکا و یک چالش را در اختیار برنامه وب قرار می‌دهد. کد زیر این اطلاعات را به شکلی که در [پارامتر `options`](#options) در بالا توصیف شده تعریف می‌کند:

```js
const requestCredentialOptionsJSON = {
  challenge: new Uint8Array([139, 66, 181, 87, 7, 203 /* … */]),
  rpId: "acme.com",
  allowCredentials: [
    {
      type: "public-key",
      id: new Uint8Array([64, 66, 25, 78, 168, 226, 174 /* … */]),
    },
  ],
  userVerification: "required",
};
```

از آنجا که این شیء فقط از انواع داده JSON استفاده می‌کند، می‌توان آن را با [`JSON.stringify()`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify) به JSON سریال کرد و به برنامه وب فرستاد.

```js
JSON.stringify(requestCredentialOptionsJSON);
```

برنامه وب می‌تواند رشته JSON را دوباره به یک شیء `requestCredentialOptionsJSON` غیرسریال کند (در اینجا نشان داده نشده است). متد **`parseRequestOptionsFromJSON()`** برای تبدیل آن شیء به شکلی که بتوان در `navigator.credentials.get()` استفاده کرد به کار می‌رود:

```js
// Convert options to form used by get()
const publicKey = PublicKeyCredential.parseRequestOptionsFromJSON(
  requestCredentialOptionsJSON, // JSON-type representation
);

navigator.credentials
  .get({ publicKey })
  .then((returnedCredentialInfo) => {
    // Handle the returned credential information here.
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

- [Web Authentication API](/en-US/docs/Web/API/Web_Authentication_API)
- {{domxref("PublicKeyCredential.parseCreationOptionsFromJSON_static", "PublicKeyCredential.parseCreationOptionsFromJSON()")}}