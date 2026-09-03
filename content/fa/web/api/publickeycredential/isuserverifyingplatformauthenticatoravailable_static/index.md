---
title: "PublicKeyCredential: isUserVerifyingPlatformAuthenticatorAvailable() static method"
short-title: isUserVerifyingPlatformAuthenticatorAvailable()
slug: Web/API/PublicKeyCredential/isUserVerifyingPlatformAuthenticatorAvailable_static
page-type: web-api-static-method
browser-compat: api.PublicKeyCredential.isUserVerifyingPlatformAuthenticatorAvailable_static
---

{{APIRef("Web Authentication API")}}{{securecontext_header}}

متد استاتیک **`isUserVerifyingPlatformAuthenticatorAvailable()`** از اینترفیس {{domxref("PublicKeyCredential")}} یک {{jsxref("Promise")}} برمی‌گرداند که اگر یک احراز هویت‌کنندهٔ پلتفرمیِ تأییدکنندهٔ کاربر موجود باشد، با مقدار `true` resolve می‌شود.

احراز هویت‌کنندهٔ پلتفرمیِ تأییدکنندهٔ کاربر، نوعی {{glossary("multi-factor authentication", "multi-factor authenticator")}} است که بخشی از دستگاه کلاینت محسوب می‌شود (و معمولاً جداشدنی نیست) و برای شناسایی کاربر، به انجام عملی از سوی او نیاز دارد. نمونه‌های رایج این احراز هویت‌کننده‌ها عبارت‌اند از:

- Touch ID یا Face ID (در macOS و iOS)
- Windows Hello (در Windows)
- باز کردن قفل دستگاه (اثر انگشت، چهره، PIN و غیره) در Android

> [!NOTE]
> این متد فقط در زمینه‌های سطح بالا (top-level contexts) قابل استفاده است و برای مثال در یک {{HTMLElement("iframe")}} در دسترس نخواهد بود.

## سینتکس

```js-nolint
PublicKeyCredential.isUserVerifyingPlatformAuthenticatorAvailable()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به یک مقدار بولی resolve می‌شود و نشان می‌دهد آیا احراز هویت‌کنندهٔ پلتفرمیِ تأییدکنندهٔ کاربر موجود است یا نه.

> [!NOTE]
> در نسخه‌های پیشین مشخصات (specification)، این مقدار بولی همچنین رضایت کاربر برای افشای وجودِ چنین احراز هویت‌کننده‌ای را منتقل می‌کرد.

### استثناها

{{jsxref("Promise")}} برگشتی ممکن است با مقادیر زیر رد (reject) شود:

- `SecurityError` {{domxref("DOMException")}}
  - : دامنهٔ RP (Relying Party) معتبر نیست.

## نمونه‌ها

```js
PublicKeyCredential.isUserVerifyingPlatformAuthenticatorAvailable()
  .then((available) => {
    if (available) {
      // We can proceed with the creation of a PublicKeyCredential
      // with this authenticator
    } else {
      // Use another kind of authenticator or a classical login/password
      // workflow
    }
  })
  .catch((err) => {
    // Something went wrong
    console.error(err);
  });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Windows Hello](https://learn.microsoft.com/en-us/windows-hardware/design/device-experiences/windows-hello)
- [Web Authentication و Windows Hello — راهنمای MSDN](https://learn.microsoft.com/en-us/archive/microsoft-edge/legacy/developer/) و به‌ویژه [ملاحظات ویژه دربارهٔ `isUserVerifyingPlatformAuthenticator()`](https://learn.microsoft.com/en-us/archive/microsoft-edge/legacy/developer/#special-considerations-for-windows-hello)