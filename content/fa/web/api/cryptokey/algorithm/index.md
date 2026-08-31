---
title: "CryptoKey: algorithm property"
short-title: algorithm
slug: Web/API/CryptoKey/algorithm
page-type: web-api-instance-property
browser-compat: api.CryptoKey.algorithm
---

{{APIRef("Web Crypto API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقط-خواندنی **`algorithm`** از رابط {{DOMxRef("CryptoKey")}} یک شیء را برمی‌گرداند که الگوریتم قابل استفاده برای این کلید و هر پارامتر اضافی مرتبط را توصیف می‌کند.

شیء بازگشتی به الگوریتم مورد استفاده برای تولید کلید بستگی دارد.

## مقدار

یک شیء منطبق با:

- [`AesKeyGenParams`](/en-US/docs/Web/API/AesKeyGenParams) اگر الگوریتم یکی از انواع AES باشد.
- [`RsaHashedKeyGenParams`](/en-US/docs/Web/API/RsaHashedKeyGenParams) اگر الگوریتم یکی از انواع RSA باشد.
- [`EcKeyGenParams`](/en-US/docs/Web/API/EcKeyGenParams) اگر الگوریتم یکی از انواع EC باشد.
- [`HmacKeyGenParams`](/en-US/docs/Web/API/HmacKeyGenParams) اگر الگوریتم HMAC باشد.

برای `RsaHashedKeyGenParams` و `HmacKeyGenParams`، ویژگی `hash` همیشه به صورت شیء (با یک ویژگی به نام `name`) است، نه به صورت رشته.

## مثال‌ها

```js
const rawKey = window.crypto.getRandomValues(new Uint8Array(16));

// Import an AES secret key from an ArrayBuffer containing the raw bytes.
// Takes an ArrayBuffer string containing the bytes, and returns a Promise
// that will resolve to a CryptoKey representing the secret key.
function importSecretKey(rawKey) {
  return window.crypto.subtle.importKey("raw", rawKey, "AES-GCM", true, [
    "encrypt",
    "decrypt",
  ]);
}

importSecretKey(rawKey).then((key) =>
  console.log(
    `This key is to be used with the ${key.algorithm.name} algorithm.`,
  ),
);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}