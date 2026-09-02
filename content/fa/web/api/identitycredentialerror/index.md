---
title: IdentityCredentialError
slug: Web/API/IdentityCredentialError
page-type: web-api-interface
browser-compat: api.IdentityCredentialError
---

{{APIRef("FedCM API")}}{{SecureContext_Header}}{{SeeCompatTable}}

رابط **`IdentityCredentialError`** از {{domxref("FedCM API", "FedCM API", "", "nocode")}} یک خطای احراز هویت را توصیف می‌کند که نشان می‌دهد عامل کاربر پس از درخواست کاربر برای استفاده از یک حساب فدرال، یک تأیید هویت دریافت نکرده است. این می‌تواند مثلاً به دلیل غیرمجاز بودن مشتری یا در دسترس نبودن موقت سرور رخ دهد.

مرورگرها می‌توانند از این نوع خطا برای نمایش پیام خطا در رابط کاربری استفاده کنند.

{{InheritanceDiagram}}

## سازنده

- {{domxref("IdentityCredentialError.IdentityCredentialError", "IdentityCredentialError()")}} {{experimental_inline}}
  - : یک نمونه جدید از شیء `IdentityCredentialError` ایجاد می‌کند.

## ویژگی‌های نمونه

_علاوه بر ویژگی‌های زیر، `IdentityCredentialError` ویژگی‌ها را از والد خود، {{DOMxRef("DOMException")}}، به ارث می‌برد._

- {{domxref("IdentityCredentialError.error", "error")}} {{Experimental_Inline}} {{ReadOnlyInline}}
  - : یک رشته. این می‌تواند یکی از مقادیر ذکر شده در [فهرست خطاهای مشخص شده OAuth 2.0](https://datatracker.ietf.org/doc/html/rfc6749#section-4.1.2.1) یا یک رشته دلخواه باشد.
- {{domxref("IdentityCredentialError.url", "url")}} {{Experimental_Inline}} {{ReadOnlyInline}}
  - : یک URL که به اطلاعات قابل خواندن توسط انسان درباره خطا اشاره می‌کند تا به کاربران نمایش داده شود، مانند نحوه رفع خطا یا تماس با خدمات مشتری.

## مثال‌ها

```js
try {
  const cred = await navigator.credentials.get({
    identity: {
      providers: [
        {
          configURL: "https://idp.example/manifest.json",
          clientId: "1234",
        },
      ],
    },
  });
} catch (e) {
  const error = e.error;
  const url = e.url;
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CredentialsContainer.get()")}}
- [پاسخ‌های خطای تأیید هویت](/en-US/docs/Web/API/FedCM_API/IDP_integration#id_assertion_error_responses)