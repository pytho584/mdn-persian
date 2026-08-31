---
title: "CryptoKeyPair"
---

---
title: CryptoKeyPair
slug: Web/API/CryptoKeyPair
page-type: web-api-interface
spec-urls: https://w3c.github.io/webcrypto/#keypair
---

{{APIRef("Web Crypto API")}}

دیکشنری **`CryptoKeyPair`** از [Web Crypto API](/en-US/docs/Web/API/Web_Crypto_API) یک جفت کلید برای الگوریتم رمزنگاری نامتقارن (که به آن الگوریتم کلید عمومی نیز گفته می‌شود) را نشان می‌دهد.

یک شیء `CryptoKeyPair` را می‌توان با استفاده از {{domxref("SubtleCrypto.generateKey()")}} به دست آورد، زمانی که الگوریتم انتخاب‌شده یکی از الگوریتم‌های نامتقارن باشد: RSASSA-PKCS1-v1_5، RSA-PSS، RSA-OAEP، ECDSA یا ECDH.

این شیء شامل دو ویژگی است که هر دو از نوع [`CryptoKey`](/en-US/docs/Web/API/CryptoKey) هستند: یک ویژگی `privateKey` که شامل کلید خصوصی است و یک ویژگی `publicKey` که شامل کلید عمومی است.

## ویژگی‌های نمونه

- `CryptoKeyPair.privateKey`
  - : یک شیء [`CryptoKey`](/en-US/docs/Web/API/CryptoKey) که نشان‌دهنده کلید خصوصی است. برای الگوریتم‌های رمزنگاری و رمزگشایی، از این کلید برای رمزگشایی استفاده می‌شود. برای الگوریتم‌های امضا و تأیید، از آن برای امضا کردن استفاده می‌شود.
- `CryptoKeyPair.publicKey`
  - : یک شیء [`CryptoKey`](/en-US/docs/Web/API/CryptoKey) که نشان‌دهنده کلید عمومی است. برای الگوریتم‌های رمزنگاری و رمزگشایی، از این کلید برای رمزنگاری استفاده می‌شود. برای الگوریتم‌های امضا و تأیید، از آن برای تأیید امضاها استفاده می‌شود.

## نمونه‌ها

نمونه‌های مربوط به متدهای `SubtleCrypto` معمولاً از اشیاء `CryptoKeyPair` استفاده می‌کنند. برای مثال:

- [`SubtleCrypto.generateKey()`](/en-US/docs/Web/API/SubtleCrypto/generateKey)
- [`SubtleCrypto.deriveKey()`](/en-US/docs/Web/API/SubtleCrypto/deriveKey)
- [`SubtleCrypto.importKey()`](/en-US/docs/Web/API/SubtleCrypto/importKey)
- [`SubtleCrypto.exportKey()`](/en-US/docs/Web/API/SubtleCrypto/exportKey)
- [`SubtleCrypto.wrapKey()`](/en-US/docs/Web/API/SubtleCrypto/wrapKey)
- [`SubtleCrypto.unwrapKey()`](/en-US/docs/Web/API/SubtleCrypto/unwrapKey)
- [`SubtleCrypto.encrypt()`](/en-US/docs/Web/API/SubtleCrypto/encrypt)
- [`SubtleCrypto.decrypt()`](/en-US/docs/Web/API/SubtleCrypto/decrypt)
- [`SubtleCrypto.sign()`](/en-US/docs/Web/API/SubtleCrypto/sign)
- [`SubtleCrypto.verify()`](/en-US/docs/Web/API/SubtleCrypto/verify)

## مشخصات

{{Specifications}}

## همچنین ببینید

- {{domxref("SubtleCrypto.generateKey")}}.
- {{domxref("SubtleCrypto.sign")}} و {{domxref("SubtleCrypto.verify")}}.
- {{domxref("SubtleCrypto.encrypt")}} و {{domxref("SubtleCrypto.decrypt")}}.