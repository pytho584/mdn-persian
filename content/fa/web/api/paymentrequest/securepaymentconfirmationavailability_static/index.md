---
title: "PaymentRequest: securePaymentConfirmationAvailability() static method"
short-title: securePaymentConfirmationAvailability()
slug: Web/API/PaymentRequest/securePaymentConfirmationAvailability_static
page-type: web-api-static-method
status:
  - experimental
browser-compat: api.PaymentRequest.securePaymentConfirmationAvailability_static
---

{{securecontext_header}}{{APIRef("Payment Request API")}}{{SeeCompatTable}}

متد ایستای **`securePaymentConfirmationAvailability()`** در رابط {{domxref("PaymentRequest")}} نشان می‌دهد که آیا قابلیت [تأیید پرداخت امن](/en-US/docs/Web/API/Payment_Request_API/Using_secure_payment_confirmation) (SPC) در دسترس است یا خیر.

## نحو (Syntax)

```js-nolint
securePaymentConfirmationAvailability()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک مقدار شمارشی (enumerated value) resolved می‌شود و نشان می‌دهد که آیا SPC در دسترس است و اگر نیست، دلیل عدم دسترسی چیست.

مقادیر احتمالی عبارتند از:

- `available`
  - : SPC در فریم فراخوان (calling frame) در دسترس است. این تضمین نمی‌کند که یک [اعتبارنامه سازگار با SPC](/en-US/docs/Web/API/Payment_Request_API/Using_secure_payment_confirmation#creating_a_credential) برای احراز هویت موجود باشد.
- `unavailable-unknown-reason`
  - : SPC در فریم فراخوان به دلیلی نامشخص در دسترس نیست. مرورگر ممکن است این نتیجه را به جای یک دلیل دقیق‌تر بازگرداند تا از حریم خصوصی کاربر محافظت کند.
- `unavailable-feature-not-enabled`
  - : SPC در فریم فراخوان در دسترس نیست، زیرا فعال نشده است.
- `unavailable-no-permission-policy`
  - : SPC در فریم فراخوان در دسترس نیست، زیرا توسط [سیاست مجوز (Permissions Policy)](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) [`payment`](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy/payment) مسدود شده است.
- `unavailable-no-user-verifying-platform-authenticator`
  - : SPC در فریم فراخوان در دسترس نیست، زیرا هیچ احراز هویت‌کننده پلتفرمی تأییدکننده کاربر (user-verifying platform authenticator) در دسترس نیست (برای تشخیص این اطلاعات می‌توان از {{domxref("PublicKeyCredential.isUserVerifyingPlatformAuthenticatorAvailable()")}} نیز استفاده کرد).

## مثال‌ها

```js
async function spcSupport() {
  const support = await PaymentRequest.securePaymentConfirmationAvailability();
  if (support === "available") {
    // Commence SPC payment flow
  } else {
    // Fallback to traditional flows
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از تأیید پرداخت امن](/en-US/docs/Web/API/Payment_Request_API/Using_secure_payment_confirmation)