---
title: "PublicKeyCredential: signalCurrentUserDetails() static method"
short-title: signalCurrentUserDetails()
slug: Web/API/PublicKeyCredential/signalCurrentUserDetails_static
page-type: web-api-static-method
browser-compat: api.PublicKeyCredential.signalCurrentUserDetails_static
---

{{APIRef("Web Authentication API")}}{{securecontext_header}}

متد ایستای **`signalCurrentUserDetails()``** در رابط {{domxref("PublicKeyCredential")}} به اصالت‌سنج (authenticator) اعلام می‌کند که یک کاربر خاص، نام کاربری و/یا نام نمایشی خود را در سرور [طرف وابسته (relying party)](https://en.wikipedia.org/wiki/Relying_party) (RP) به‌روزرسانی کرده است.

این کار به اصالت‌سنج اجازه می‌دهد تا جزئیات حساب کاربری را به‌روزرسانی کند و مطمئن شود که با اطلاعات نگهداری‌شده در RP همگام می‌ماند. این متد فقط باید زمانی استفاده شود که کاربر فعلی احراز هویت شده است — پس از ورود به سیستم، یا زمانی که ابرداده‌های مرتبط با اعتبارنامه‌های خود را در برنامه وب RP تغییر می‌دهد.

## نحو (Syntax)

```js-nolint
signalCurrentUserDetails(options)
```

### پارامترها

- `options`
  - : یک شیء که اطلاعات به‌روزرسانی‌شده کاربر را نمایش می‌دهد و شامل ویژگی‌های زیر است:
    - `displayName`
      - : یک رشته که [`displayName`](/en-US/docs/Web/API/PublicKeyCredentialCreationOptions#displayname) به‌روزرسانی‌شده کاربر را نشان می‌دهد.
    - `name`
      - : یک رشته که [`name`](/en-US/docs/Web/API/PublicKeyCredentialCreationOptions#name_2) به‌روزرسانی‌شده کاربر را نشان می‌دهد.
    - `rpId`
      - : یک رشته که [`id` مربوط به RP](/en-US/docs/Web/API/PublicKeyCredentialCreationOptions#id_2) ارسال‌کنندهٔ سیگنال را نشان می‌دهد.
    - `userId`
      - : یک رشته کدگذاری‌شده base64url که [`id` کاربر](/en-US/docs/Web/API/PublicKeyCredentialCreationOptions#id_3) مرتبط با اعتبارنامه‌ها را نشان می‌دهد.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به {{jsxref("undefined")}} باز می‌شود.

### استثناها

این پرامیسی با استثناهای زیر رد می‌شود:

- `SecurityError` {{domxref("DOMException")}}
  - : دامنهٔ RP معتبر نیست.
- `TypeError` {{domxref("DOMException")}}
  - : `credentialId` یک رشتهٔ معتبر کدگذاری‌شده base64url نیست.

## توضیحات

این امکان وجود دارد که اطلاعات ذخیره‌شده در اصالت‌سنج کاربر دربارهٔ یک [اعتبارنامهٔ قابل‌کشف (discoverable credential)](/en-US/docs/Web/API/Web_Authentication_API#discoverable_and_non-discoverable_credentials) (برای مثال، یک [گذرواژه کلید (passkey)](/en-US/docs/Web/Security/Authentication/Passkeys)) از سرور خارج از همگام‌سازی شود. این اتفاق می‌تواند زمانی رخ دهد که کاربر نام کاربری یا نام نمایشی خود را در برنامهٔ وب RP به‌روزرسانی کند اما اصالت‌سنج را به‌روزرسانی نکند.

دفعهٔ بعد که کاربر بخواهد با یک اعتبارنامهٔ قابل‌کشف وارد شود، همچنان اعتبارنامه با نام کاربری/نام نمایشی قدیمی در رابط کاربری مربوطه به او نمایش داده می‌شود که می‌تواند تجربهٔ کاربری گیج‌کننده‌ای ایجاد کند.

برای جلوگیری از این مشکل، `signalCurrentUserDetails()` باید در برنامهٔ وب RP هر بار که کاربر جزئیات حساب کاربری خود را به‌روزرسانی می‌کند یا وارد سیستم می‌شود، فراخوانی شود تا به اصالت‌سنج اعلام کند که اطلاعات کاربر به‌روزرسانی شده است. نحوهٔ مدیریت این اطلاعات به عهدهٔ اصالت‌سنج است، اما انتظار می‌رود که اطلاعات کاربر خود را با به‌روزرسانی ارائه‌شده همگام کند.

## مثال‌ها

### اعلام جزئیات فعلی کاربر

در این مثال، متد `signalCurrentUserDetail()` را فراخوانی می‌کنیم و جزئیات اعتبارنامه‌ای را که کاربر به‌تازگی در RP ویرایش کرده است به آن ارسال می‌کنیم. در نتیجه، اصالت‌سنج باید نسخهٔ خود از اعتبارنامه را به‌روزرسانی کند تا با RP همگام بماند.

```js
if (PublicKeyCredential.signalCurrentUserDetails) {
  await PublicKeyCredential.signalCurrentUserDetails({
    rpId: "example.com",
    userId: "M2YPl-KGnA8", // base64url-encoded user ID
    name: "a.new.email.address@example.com", // username
    displayName: "Maria Sanchez",
  });
} else {
  // Encourage the user to update their details in the authenticator
}
```

برای مثال‌های کد بیشتر، به [Keep passkeys consistent with credentials on your server with the Signal API](https://developer.chrome.com/docs/identity/webauthn-signal-api) در developer.chrome.com (2024) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("PublicKeyCredential.signalAllAcceptedCredentials_static", "PublicKeyCredential.signalAllAcceptedCredentials()")}}
- {{domxref("PublicKeyCredential.signalUnknownCredential_static", "PublicKeyCredential.signalUnknownCredential()")}}
- [Keep passkeys consistent with credentials on your server with the Signal API](https://developer.chrome.com/docs/identity/webauthn-signal-api) در developer.chrome.com (2024)