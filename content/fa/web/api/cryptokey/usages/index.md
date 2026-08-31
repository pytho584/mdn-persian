---
title: "CryptoKey: usages property"
---

---
title: "CryptoKey: usages property"
short-title: usages
slug: Web/API/CryptoKey/usages
page-type: web-api-instance-property
browser-compat: api.CryptoKey.usages
---

{{APIRef("Web Crypto API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`usages`** در رابط {{DOMxRef("CryptoKey")}} نشان می‌دهد که با کلید چه کارهایی می‌توان انجام داد.

## مقدار

یک {{jsxref("Array")}} از رشته‌ها از فهرست زیر:

- `"encrypt"`: از کلید می‌توان برای [رمزگذاری](/en-US/docs/Web/API/SubtleCrypto/encrypt) پیام‌ها استفاده کرد.
- `"decrypt"`: از کلید می‌توان برای [رمزگشایی](/en-US/docs/Web/API/SubtleCrypto/decrypt) پیام‌ها استفاده کرد.
- `"sign"`: از کلید می‌توان برای [امضای](/en-US/docs/Web/API/SubtleCrypto/sign) پیام‌ها استفاده کرد.
- `"verify"`: از کلید می‌توان برای [تأیید](/en-US/docs/Web/API/SubtleCrypto/verify) امضاها استفاده کرد.
- `"deriveKey"`: از کلید می‌توان در [استخراج یک کلید جدید](/en-US/docs/Web/API/SubtleCrypto/deriveKey) استفاده کرد.
- `"deriveBits"`: از کلید می‌توان در [استخراج بیت‌ها](/en-US/docs/Web/API/SubtleCrypto/deriveBits) استفاده کرد.
- `"wrapKey"`: از کلید می‌توان برای [دورپیچی یک کلید](/en-US/docs/Web/API/SubtleCrypto/wrapKey) استفاده کرد.
- `"unwrapKey"`: از کلید می‌توان برای [باز کردن دورپیچی یک کلید](/en-US/docs/Web/API/SubtleCrypto/unwrapKey) استفاده کرد.

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
    `The following usages are reported for this key: ${key.usages.toString()}`,
  ),
);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}