---
title: "PublicKeyCredential: signalUnknownCredential() static method"
short-title: signalUnknownCredential()
slug: Web/API/PublicKeyCredential/signalUnknownCredential_static
page-type: web-api-static-method
browser-compat: api.PublicKeyCredential.signalUnknownCredential_static
---

{{APIRef("Web Authentication API")}}{{securecontext_header}}

متد استاتیک **`signalUnknownCredential()`** در رابط {{domxref("PublicKeyCredential")}} به اصالت‌سنج (authenticator) اطلاع می‌دهد که [شناسهٔ اعتبارنامه](/en-US/docs/Web/API/PublicKeyCredentialRequestOptions#id) توسط سرورِ [طرف اتکا](https://en.wikipedia.org/wiki/Relying_party) (relying party یا به‌اختصار RP) شناسایی نشده است.

این کار به اصالت‌سنج امکان می‌دهد اعتبارنامه‌هایی را که طرف اتکا مجاز نمی‌داند حذف کند؛ مانند اعتبارنامه‌های حساب‌های حذف‌شده، یا حساب‌هایی که روی اصالت‌سنج ساخته و ذخیره شده‌اند اما اطلاعاتشان به‌درستی روی سرور به‌روزرسانی نشده است.

معمولاً این متد پس از آن فراخوانی می‌شود که ورود کاربر به دلیل در دسترس نبودن اطلاعات حساب برای طرف اتکا ناموفق بوده است. از آنجا که این متد اطلاعات حساسی را افشا نمی‌کند، حتی وقتی کاربرِ فعلی احراز هویت نشده باشد نیز می‌توان از آن استفاده کرد.

## سینتکس

```js-nolint
signalUnknownCredential(options)
```

### پارامترها

- `options`
  - : شیئی که نمایانگر اعتبارنامهٔ شناسایی‌نشده است و ویژگی‌های زیر را دارد:
    - `credentialId`
      - : رشته‌ای کدگذاری‌شده با base64url که [`id` همان اعتبارنامه‌ای که ناشناخته مانده](/en-US/docs/Web/API/PublicKeyCredentialRequestOptions#id) را نشان می‌دهد.
    - `rpId`
      - : رشته‌ای که [`id` طرف اتکا](/en-US/docs/Web/API/PublicKeyCredentialCreationOptions#id_2) را نشان می‌دهد؛ همان طرف اتکایی که این سیگنال را ارسال کرده است.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با {{jsxref("undefined")}} resolve می‌شود.

### استثناها

این Promise با استثناهای زیر رد (reject) می‌شود:

- `SecurityError` {{domxref("DOMException")}}
  - : دامنهٔ طرف اتکا (RP) معتبر نیست.
- `TypeError` {{domxref("DOMException")}}
  - : مقدار `credentialId` یک رشتهٔ معتبر کدگذاری‌شده با base64url نیست.

## توضیحات

ممکن است اطلاعات مربوط به یک [اعتبارنامهٔ قابل‌کشف (discoverable credential)](/en-US/docs/Web/API/Web_Authentication_API#discoverable_and_non-discoverable_credentials) که روی اصالت‌سنج کاربر ذخیره شده است (مثلاً یک [passkey](/en-US/docs/Web/Security/Authentication/Passkeys)) با اطلاعات سمت سرور هماهنگ نباشد. این اتفاق معمولاً وقتی رخ می‌دهد که کاربر یک اعتبارنامه را از برنامهٔ وبِ طرف اتکا حذف می‌کند، بدون آنکه اصالت‌سنج را به‌روزرسانی کند.

وقتی کاربر می‌خواهد با استفاده از اعتبارنامه‌های قابل‌کشف وارد شود، فهرستی از اعتبارنامه‌های موجود روی اصالت‌سنج برای انتخاب به او نمایش داده می‌شود و اعتبارنامهٔ انتخاب‌شده برای ورود به برنامهٔ وبِ طرف اتکا بازگردانده می‌شود. اگر کاربر اعتبارنامه‌ای را انتخاب کند که از سرورِ طرف اتکا حذف شده باشد، آن اعتبارنامه شناسایی نمی‌شود و ورود با شکست مواجه می‌شود. این تجربه‌ای گیج‌کننده برای کاربر است؛ کاربر انتظار دارد فقط اعتبارنامه‌هایی به او پیشنهاد شود که ورود با آن‌ها موفق خواهد بود.

برای کاهش این مشکل، هر بار که ورود مبتنی بر اعتبارنامهٔ قابل‌کشف ناموفق می‌ماند، باید `signalUnknownCredential()` را در برنامهٔ وبِ طرف اتکا فراخوانی کرد تا به اصالت‌سنج اطلاع داده شود که شناسهٔ آن اعتبارنامه شناسایی نشده است.

اینکه اصالت‌سنج این اطلاعات را چگونه پردازش کند به خودش بستگی دارد؛ اما انتظار می‌رود اعتبارنامهٔ مربوطه را حذف کند تا دیگر ناهماهنگی میان داده‌های ذخیره‌شده روی اصالت‌سنج و داده‌های طرف اتکا وجود نداشته باشد.

علاوه بر این، `signalUnknownCredential()` ممکن است در شرایطی هم فراخوانی شود که یک برنامهٔ وب می‌تواند اعتبارنامهٔ قابل‌کشفی روی اصالت‌سنج بسازد اما به هر دلیلی امکان بارگذاری (upload) اطلاعات آن اعتبارنامه روی سرور را ندارد.

`signalUnknownCredential()` حتی وقتی کاربرِ فعلی احراز هویت نشده باشد نیز قابل فراخوانی است، زیرا این متد اطلاعات حساسی را افشا نمی‌کند.

## مثال‌ها

### اعلام یک اعتبارنامهٔ ناشناخته

در این مثال، تلاش برای ورود با استفاده از اعتبارنامه‌های قابل‌کشف از طریق یک فراخوانی [`get()`](/en-US/docs/Web/API/CredentialsContainer/get) انجام می‌شود. اعتبارنامه با موفقیت بازگردانده می‌شود و شناسهٔ اعتبارنامه و بار داده (payload) در ثابت‌ها ذخیره می‌شوند.

سپس بار داده با یک درخواست [`fetch()`](/en-US/docs/Web/API/Window/fetch) برای ورود کاربر به سرورِ طرف اتکا ارسال می‌شود؛ اما درخواست با پاسخ {{httpstatus("404")}} شکست می‌خورد، زیرا طرف اتکا آن کاربر را نمی‌شناسد (مثلاً به این دلیل که آن اعتبارنامه قبلاً از سمت طرف اتکا حذف شده است).

در نتیجه، متد `signalUnknownCredential()` را فراخوانی می‌کنیم و `rpId` و شناسهٔ اعتبارنامه را به آن پاس می‌دهیم تا به اصالت‌سنج اطلاع دهیم که این اعتبارنامه برای طرف اتکا ناشناخته است. انتظار می‌رود اصالت‌سنج سپس آن اعتبارنامه را حذف کند تا مشکل مشابهی دوباره رخ ندهد.

```js
const credential = await navigator.credentials.get({
  challenge: new Uint8Array([139, 66, 181, 87, 7, 203 /* … */]),
  rpId: "example.com",
  allowCredentials: [],
  // Empty allowCredentials list means only discoverable
  // credentials are presented to the user
});

// Retrieve base64url-encoded credential ID,
// such as "vI0qOggiE3OT01ZRWBYz5l4MEgU0c7PmAA"
const credID = credential.id;
// Retrieve payload to send to the RP server
const payload = credential.toJSON();

const result = await fetch("/login", {
  // fetch() options, will include the payload in the request body
});

// Detect authentication failure due to lack of the credential
if (result.status === 404) {
  if (PublicKeyCredential.signalUnknownCredential) {
    await PublicKeyCredential.signalUnknownCredential({
      rpId: "example.com",
      credentialId: credID,
    });
  } else {
    // Encourage the user to delete the credential from the authenticator
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("PublicKeyCredential.signalAllAcceptedCredentials_static", "PublicKeyCredential.signalAllAcceptedCredentials()")}}
- {{domxref("PublicKeyCredential.signalCurrentUserDetails_static", "PublicKeyCredential.signalCurrentUserDetails()")}}
- [با Signal API، passkeyها را با اعتبارنامه‌های روی سرور خود هماهنگ نگه دارید](https://developer.chrome.com/docs/identity/webauthn-signal-api) در developer.chrome.com (2024)