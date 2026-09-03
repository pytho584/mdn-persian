---
title: "PublicKeyCredential: id property"
short-title: id
slug: Web/API/PublicKeyCredential/id
page-type: web-api-instance-property
browser-compat: api.PublicKeyCredential.id
---

{{APIRef("Web Authentication API")}}{{securecontext_header}}

ویژگی فقطخواندنی **`id`** در رابط {{domxref("PublicKeyCredential")}} یک رشته است که از {{domxref("Credential")}} به ارث می‌رسد و نمایانگر شناسهٔ نمونهٔ فعلی `PublicKeyCredential` است.

این ویژگی نسخهٔ [کدگذاری‌شده با base64url](/en-US/docs/Glossary/Base64) از {{domxref("PublicKeyCredential.rawId")}} است.

> [!NOTE]
> این ویژگی فقط در زمینه‌های سطح بالا (top-level contexts) قابل استفاده است و برای مثال در یک {{HTMLElement("iframe")}} در دسترس نخواهد بود.

## مقدار

یک رشته که نسخهٔ [کدگذاری‌شده با base64url](/en-US/docs/Glossary/Base64) از {{domxref("PublicKeyCredential.rawId")}} است.

## مثال‌ها

```js
const publicKey = {
  challenge: new Uint8Array(26) /* this actually is given from the server */,
  rp: {
    name: "Example CORP",
    id: "login.example.com",
  },
  user: {
    id: new Uint8Array(26) /* To be changed for each user */,
    name: "canand@example.com",
    displayName: "Carina Anand",
  },
  pubKeyCredParams: [
    {
      type: "public-key",
      alg: -7,
    },
  ],
};

navigator.credentials
  .create({ publicKey })
  .then((newCredentialInfo) => {
    const id = newCredentialInfo.id;
    // Do something with the id

    // send attestation response and client extensions
    // to the server to proceed with the registration
    // of the credential
  })
  .catch((err) => {
    console.error(err);
  });
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Credential.id")}}