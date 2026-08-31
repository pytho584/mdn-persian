---
title: "CryptoKey: type property"
short-title: type
slug: Web/API/CryptoKey/type
page-type: web-api-instance-property
browser-compat: api.CryptoKey.type
---

{{APIRef("Web Crypto API")}}{{SecureContext_Header}}{{AvailableInWorkers}}

خاصیت فقط‌خواندنی **`type`** در رابط {{DOMxRef("CryptoKey")}} مشخص می‌کند که شیء نمایانگر چه نوع کلیدی است. این خاصیت می‌تواند مقادیر زیر را داشته باشد:

- `"secret"`: این کلید، یک کلید محرمانه برای استفاده با یک {{Glossary("Symmetric-key cryptography", "الگوریتم متقارن")}} است.
- `"private"`: این کلید، نیمه خصوصی یک [`CryptoKeyPair`](/en-US/docs/Web/API/CryptoKeyPair) متعلق به یک {{Glossary("Public-key cryptography", "الگوریتم نامتقارن")}} است.
- `"public"`: این کلید، نیمه عمومی یک [`CryptoKeyPair`](/en-US/docs/Web/API/CryptoKeyPair) متعلق به یک {{Glossary("Public-key cryptography", "الگوریتم نامتقارن")}} است.

## مقدار

یکی از رشته‌های زیر: `"secret"`، `"private"` یا `"public"`.

## مثال‌ها

این تابع یک پیام را با استفاده از {{domxref("SubtleCrypto.verify()")}} و یک کلید عمومی که به عنوان پارامتر داده شده است، تأیید می‌کند. اگر کلید از نوع عمومی نباشد، تابع همیشه `"invalid"` برمی‌گرداند، زیرا چنین تأییدی ذاتاً ناامن است.

```js
async function verifyMessage(publicKey) {
  const signatureValue = document.querySelector(
    ".rsassa-pkcs1 .signature-value",
  );
  signatureValue.classList.remove("valid", "invalid");

  let result = false; // By default, it is invalid

  if (publicKey.type === "public") {
    const encoded = getMessageEncoding();
    result = await window.crypto.subtle.verify(
      "RSASSA-PKCS1-v1_5",
      publicKey,
      signature,
      encoded,
    );
  }

  signatureValue.classList.add(result ? "valid" : "invalid");
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}