---
title: "IdentityCredentialError: url property"
short-title: url
slug: Web/API/IdentityCredentialError/url
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.IdentityCredentialError.url
---

{{APIRef("FedCM API")}}{{AvailableInWorkers}}{{SeeCompatTable}}

خاصیت فقط-خواندنی **`url`** از رابط {{domxref("IdentityCredentialError")}}، نشانی اینترنتی (URL) است که به اطلاعات قابل‌فهم برای انسان درباره خطا اشاره می‌کند تا به کاربران نمایش داده شود، مانند نحوه رفع خطا یا تماس با پشتیبانی مشتریان.

## مقدار

یک رشته (string) که نشانی اینترنتی برای اطلاعات بیشتر درباره خطا را نشان می‌دهد.

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

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("CredentialsContainer.get()")}}
- [پاسخ‌های خطای تأیید هویت (ID assertion error responses)](/en-US/docs/Web/API/FedCM_API/IDP_integration#id_assertion_error_responses)