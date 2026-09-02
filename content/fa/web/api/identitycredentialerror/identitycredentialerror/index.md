---
title: "IdentityCredentialError: IdentityCredentialError() constructor"
---

---
title: "IdentityCredentialError: IdentityCredentialError() constructor"
short-title: IdentityCredentialError()
slug: Web/API/IdentityCredentialError/IdentityCredentialError
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.IdentityCredentialError.IdentityCredentialError
---

{{APIRef("Fetch API")}}{{AvailableInWorkers}}{{SeeCompatTable}}

سازندهی **`IdentityCredentialError()`** یک شیء جدید {{domxref("IdentityCredentialError")}} ایجاد میکند.

## سینتکس

```js-nolint
new IdentityCredentialError()
new IdentityCredentialError(message)
new IdentityCredentialError(message, options)
```

### پارامترها

- `message`
  - : شرحی از خطا. اگر موجود نباشد، رشتهی خالی `''` استفاده میشود.
- `options` {{optional_inline}}
  - : یک شیء که میتواند ویژگیهای زیر را داشته باشد:
    - `error` {{optional_inline}}
      - : یک رشته. این میتواند یکی از مقادیر موجود در [فهرست خطاهای مشخصشدهی OAuth 2.0](https://datatracker.ietf.org/doc/html/rfc6749#section-4.1.2.1) یا یک رشتهی دلخواه باشد.
    - `url` {{optional_inline}}
      - : یک URL که به اطلاعات قابلخواندن برای انسان دربارهی خطا اشاره میکند تا به کاربران نمایش داده شود، مانند نحوهی رفع خطا یا تماس با پشتیبانی مشتری.

## مثالها

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
- [پاسخهای خطای تأیید هویت](/en-US/docs/Web/API/FedCM_API/IDP_integration#id_assertion_error_responses)