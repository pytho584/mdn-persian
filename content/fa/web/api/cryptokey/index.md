---
title: CryptoKey
slug: Web/API/CryptoKey
page-type: web-api-interface
browser-compat: api.CryptoKey
---

{{APIRef("Web Crypto API")}}{{SecureContext_header}}{{AvailableInWorkers}}

رابط **`CryptoKey`** از [Web Crypto API](/en-US/docs/Web/API/Web_Crypto_API) یک {{glossary("key")}} رمزنگاری را نشان می‌دهد که از یکی از متدهای {{domxref("SubtleCrypto")}} یعنی {{domxref("SubtleCrypto.generateKey", "generateKey()")}}، {{domxref("SubtleCrypto.deriveKey", "deriveKey()")}}، {{domxref("SubtleCrypto.importKey", "importKey()")}} یا {{domxref("SubtleCrypto.unwrapKey", "unwrapKey()")}} به دست می‌آید.

به دلایل امنیتی، رابط `CryptoKey` فقط در یک [زمینه امن](/en-US/docs/Web/Security/Defenses/Secure_Contexts) قابل استفاده است.

## ویژگی‌های نمونه

- {{domxref("CryptoKey.type")}} {{ReadOnlyInline}}
  - : نوع کلیدی که شیء نشان می‌دهد. می‌تواند یکی از مقادیر `"secret"`، `"private"` یا `"public"` باشد.

- {{domxref("CryptoKey.extractable")}} {{ReadOnlyInline}}
  - : یک مقدار بولی که نشان می‌دهد آیا کلید می‌تواند با استفاده از [`SubtleCrypto.exportKey()`](/en-US/docs/Web/API/SubtleCrypto/exportKey) یا [`SubtleCrypto.wrapKey()`](/en-US/docs/Web/API/SubtleCrypto/wrapKey) استخراج شود یا خیر.

- {{domxref("CryptoKey.algorithm")}} {{ReadOnlyInline}}
  - : یک شیء که الگوریتمی را که این کلید می‌تواند برای آن استفاده شود و هر پارامتر اضافی مرتبط را توصیف می‌کند.

- {{domxref("CryptoKey.usages")}} {{ReadOnlyInline}}
  - : یک {{jsxref("Array")}} از رشته‌ها که نشان می‌دهد چه عملیاتی با کلید می‌توان انجام داد. مقادیر ممکن برای عناصر آرایه عبارتند از `"encrypt"`، `"decrypt"`، `"sign"`، `"verify"`، `"deriveKey"`، `"deriveBits"`، `"wrapKey"` و `"unwrapKey"`.

## مثال‌ها

مثال‌های متدهای `SubtleCrypto` اغلب از اشیاء `CryptoKey` استفاده می‌کنند. برای مثال:

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

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [Web Crypto API](/en-US/docs/Web/API/Web_Crypto_API)
- [امنیت وب](/en-US/docs/Web/Security)
- [حریم خصوصی، مجوزها و امنیت اطلاعات](/en-US/docs/Web/Privacy)
- {{domxref("Crypto")}} و {{domxref("Crypto.subtle")}}