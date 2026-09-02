---
title: "IdentityCredentialError: error property"
short-title: error
slug: Web/API/IdentityCredentialError/error
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.IdentityCredentialError.error
---

{{APIRef("FedCM API")}}{{AvailableInWorkers}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`error`** در رابط {{domxref("IdentityCredentialError")}} یا یکی از مقادیر فهرست‌شده در [فهرست خطاهای مشخص‌شده در OAuth 2.0](https://datatracker.ietf.org/doc/html/rfc6749#section-4.1.2.1) است یا یک رشتهٔ دلخواه که اطلاعات بیشتری دربارهٔ خطا می‌دهد.

## مقدار

یکی از مقادیر فهرست‌شده در [فهرست خطاهای مشخص‌شده در OAuth 2.0](https://datatracker.ietf.org/doc/html/rfc6749#section-4.1.2.1) یا یک رشتهٔ دلخواه.

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