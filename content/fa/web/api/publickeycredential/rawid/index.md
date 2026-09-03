---
title: "PublicKeyCredential: rawId property"
short-title: rawId
slug: Web/API/PublicKeyCredential/rawId
page-type: web-api-instance-property
browser-compat: api.PublicKeyCredential.rawId
---

{{APIRef("Web Authentication API")}}{{securecontext_header}}

ویژگی فقط-خواندنی **`rawId`** از رابط {{domxref("PublicKeyCredential")}} یک شیء {{jsxref("ArrayBuffer")}} است که شامل شناسهٔ اعتبارنامه‌ها می‌باشد.

ویژگی {{domxref("PublicKeyCredential.id")}} نسخه‌ای [کدگذاری‌شده با base64url](/en-US/docs/Glossary/Base64) از این شناسه است.

> [!NOTE]
> این ویژگی فقط در زمینه‌های سطح بالا قابل استفاده است و برای مثال در یک {{HTMLElement("iframe")}} در دسترس نخواهد بود.

## مقدار

یک {{jsxref("ArrayBuffer")}} که شامل شناسهٔ اعتبارنامه‌ها است. انتظار می‌رود که این شناسه در سطح جهانی یکتا باشد و برای `PublicKeyCredential` فعلی و {{domxref("AuthenticatorAssertionResponse")}} مرتبط با آن تعیین شده است.

## مثال‌ها

```js
const options = {
  challenge: new Uint8Array(26) /* from the server */,
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
  .create({ publicKey: options })
  .then((pubKeyCredential) => {
    const rawId = pubKeyCredential.rawId;
    // Do something with rawId
  })
  .catch((err) => {
    // Deal with any error
  });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}