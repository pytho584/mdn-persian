---
title: "PublicKeyCredential: signalAllAcceptedCredentials() static method"
---

---
title: "PublicKeyCredential: signalAllAcceptedCredentials() static method"
short-title: signalAllAcceptedCredentials()
slug: Web/API/PublicKeyCredential/signalAllAcceptedCredentials_static
page-type: web-api-static-method
browser-compat: api.PublicKeyCredential.signalAllAcceptedCredentials_static
---

{{APIRef("Web Authentication API")}}{{securecontext_header}}

متد ایستای **`signalAllAcceptedCredentials()`** از واسط {{domxref("PublicKeyCredential")}} به اصالت‌سنج (authenticator) اعلام می‌کند که همهٔ [شناسه‌های اعتبارنامه](/en-US/docs/Web/API/PublicKeyCredentialRequestOptions#id) معتبری که سرور [طرف اعتماد (relying party)](https://en.wikipedia.org/wiki/Relying_party) (RP) هنوز برای یک کاربر خاص نگه داشته است کدام‌اند.

این کار به اصالت‌سنج اجازه می‌دهد اطلاعات اعتبارنامه‌ها را به‌روزرسانی کند و همهٔ اعتبارنامه‌هایی را که دیگر توسط RP شناسایی نمی‌شوند، مثلاً اعتبارنامه‌های مربوط به حساب‌های حذف‌شده، حذف کند. این متد باید هر بار که کاربر با RP احراز هویت می‌کند فراخوانی شود.

`signalAllAcceptedCredentials()` باید _فقط_ زمانی فراخوانی شود که کاربر فعلی احراز هویت شده است — پس از ثبت‌نام یا ورود، یا زمانی که کاربر یک اعتبارنامه را حذف می‌کند — زیرا این متد اطلاعات حساس متعلق به کاربر را افشا می‌کند.

## Syntax

```js-nolint
signalAllAcceptedCredentials(options)
```

### Parameters

- `options`
  - : یک شیء که نشان‌دهندهٔ اعتبارنامه‌های معتبر است و شامل ویژگی‌های زیر می‌باشد:
    - `allAcceptedCredentialIds`
      - : آرایه‌ای از رشته‌های کدگذاری‌شده با base64url که نشان‌دهندهٔ [`id`های اعتبارنامه‌هایی](/en-US/docs/Web/API/PublicKeyCredentialRequestOptions#id) هستند که هنوز معتبرند.
    - `rpId`
      - : رشته‌ای که [`id` طرف اعتماد](/en-US/docs/Web/API/PublicKeyCredentialCreationOptions#id_2) را که این سیگنال را ارسال کرده نشان می‌دهد.
    - `userId`
      - : رشته‌ای کدگذاری‌شده با base64url که [`id` کاربر](/en-US/docs/Web/API/PublicKeyCredentialCreationOptions#id_3) مرتبط با این اعتبارنامه‌ها را نشان می‌دهد.

### Return value

یک {{jsxref("Promise")}} که با {{jsxref("undefined")}} حل می‌شود.

### Exceptions

این پرامیژ با استثناهای زیر رد می‌شود:

- `SecurityError` {{domxref("DOMException")}}
  - : دامنهٔ RP معتبر نیست.
- `TypeError` {{domxref("DOMException")}}
  - : رشتهٔ `userId` یا هر یک از عناصر `allAcceptedCredentialIds` رشته‌های کدگذاری‌شدهٔ base64url معتبری نیستند.

## Description

ممکن است اطلاعات ذخیره‌شده در اصالت‌سنج کاربر دربارهٔ یک [اعتبارنامهٔ قابل‌کشف](/en-US/docs/Web/API/Web_Authentication_API#discoverable_and_non-discoverable_credentials) (مثلاً یک [passkey](/en-US/docs/Web/Security/Authentication/Passkeys)) با سرور از همگامی خارج شود. این معمولاً زمانی رخ می‌دهد که کاربر بدون به‌روزرسانی اصالت‌سنج، یک اعتبارنامه را از وب‌اپ RP حذف می‌کند.

هنگامی که کاربر می‌خواهد با استفاده از اعتبارنامه‌های قابل‌کشف وارد شود، مجموعه‌ای از اعتبارنامه‌ها از اصالت‌سنج به او نمایش داده می‌شود تا انتخاب کند، و اعتبارنامهٔ انتخاب‌شده برای ورود به وب‌اپ RP بازگردانده می‌شود. اگر کاربر اعتبارنامه‌ای را انتخاب کند که از سرور RP حذف شده است، شناسایی نمی‌شود و ورود ناموفق خواهد بود. این تجربه‌ای گیج‌کننده برای کاربران است، زیرا انتظار دارند فقط اعتبارنامه‌هایی به آن‌ها پیشنهاد شود که باید موفق باشند.

برای کاهش این مشکل، وب‌اپ RP باید هر بار که کاربر یک اعتبارنامه را حذف می‌کند یا وارد می‌شود، `signalAllAcceptedCredentials()` را فراخوانی کند تا به اصالت‌سنج بگوید کدام اعتبارنامه‌ها برای آن کاربر همچنان معتبرند. نحوهٔ برخورد با این اطلاعات به عهدهٔ اصالت‌سنج است، اما انتظار می‌رود که اطلاعات خود را با فهرست اعتبارنامه‌های ارائه‌شده همگام کند. اعتبارنامه‌هایی که در فهرست نیستند باید حذف شوند تا کاربر اعتبارنامه‌هایی را که در رابط ورود وجود ندارند دریافت نکند.

> [!WARNING]
> هنگام فراخوانی `signalAllAcceptedCredentials()` احتیاط کنید — هر اعتبارنامهٔ معتبری که در فهرست گنجانده نشده باشد قرار است از اصالت‌سنج حذف شود، که مانع ورود کاربر با آن اعتبارنامه‌ها خواهد شد. ارسال یک فهرست خالی ممکن است همهٔ اعتبارنامه‌های کاربر را حذف کند. برخی اصالت‌سنج‌ها ممکن است از بازیابی اعتبارنامه‌ها از طریق فراخوانی بعدی `signalAllAcceptedCredentials()` با گنجاندن شناسهٔ اعتبارنامه‌های حذف‌شدهٔ قبلی در فهرست پشتیبانی کنند.

`signalAllAcceptedCredentials()` باید _فقط_ زمانی فراخوانی شود که کاربر فعلی احراز هویت شده است، زیرا اطلاعات حساس متعلق به کاربر را افشا می‌کند. اگر کاربر به دلیل تلاش برای ورود با اعتبارنامه‌ای که در سرور RP وجود ندارد احراز هویت نشده است، در عوض باید {{domxref("PublicKeyCredential.signalUnknownCredential_static", "PublicKeyCredential.signalUnknownCredential()")}} را با آن اعتبارنامهٔ ناشناخته فراخوانی کنید تا اصالت‌سنج بتواند آن را حذف کند. برای مقایسهٔ دقیق‌تر به [روش‌های همگام‌سازی اعتبارنامهٔ قابل‌کشف](/en-US/docs/Web/API/Web_Authentication_API#discoverable_credential_synchronization_methods) مراجعه کنید.

## Examples

### اعلام اعتبارنامه‌های پذیرفته‌شده

در این مثال، متد `signalAllAcceptedCredentials()` را فراخوانی می‌کنیم و جزئیات همهٔ اعتبارنامه‌های متعلق به کاربر، از جمله اعتبارنامه‌ای که همین حالا با آن وارد شده است، را به آن传递 می‌دهیم. در نتیجه، اصالت‌سنج باید نسخهٔ خود از اعتبارنامه‌ها را به‌روزرسانی کند تا با RP همگام بمانند.

```js
if (PublicKeyCredential.signalAllAcceptedCredentials) {
  await PublicKeyCredential.signalAllAcceptedCredentials({
    rpId: "example.com",
    userId: "M2YPl-KGnA8", // شناسهٔ کاربر کدگذاری‌شده با base64url
    allAcceptedCredentialIds: [
      // فهرستی از شناسه‌های اعتبارنامهٔ کدگذاری‌شده با base64url
      "vI0qOggiE3OT01ZRWBYz5l4MEgU0c7PmAA",
      // …
    ],
  });
}
```

برای مثال‌های کد بیشتر، به [Keep passkeys consistent with credentials on your server with the Signal API](https://developer.chrome.com/docs/identity/webauthn-signal-api) در developer.chrome.com (2024) مراجعه کنید.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("PublicKeyCredential.signalCurrentUserDetails_static", "PublicKeyCredential.signalCurrentUserDetails()")}}
- {{domxref("PublicKeyCredential.signalUnknownCredential_static", "PublicKeyCredential.signalUnknownCredential()")}}
- [Keep passkeys consistent with credentials on your server with the Signal API](https://developer.chrome.com/docs/identity/webauthn-signal-api) در developer.chrome.com (2024)