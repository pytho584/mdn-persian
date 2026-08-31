---
title: Crypto
slug: Web/API/Crypto
page-type: web-api-interface
browser-compat: api.Crypto
---

{{APIRef("Web Crypto API")}}{{AvailableInWorkers}}

رابط `Crypto` نمایانگر ویژگی‌های پایه‌ی رمزنگاری موجود در بافتار فعلی است. این رابط امکان دسترسی به یک مولد اعداد تصادفی امن از نظر رمزنگاری و ابزارهای رمزنگاری پایه را فراهم می‌کند.

`Crypto` در پنجره‌ها از طریق ویژگی {{domxref("Window.crypto")}} و در workerها از طریق ویژگی {{domxref("WorkerGlobalScope.crypto")}} در دسترس است.

## ویژگی‌های نمونه

- {{domxref("Crypto.subtle")}} {{ReadOnlyInline}} {{SecureContext_inline}}
  - : یک شیء {{domxref("SubtleCrypto")}} برمی‌گرداند که دسترسی به ابزارهای رمزنگاری پایه‌ی رایج مانند هش، امضا، رمزگذاری یا رمزگشایی را فراهم می‌کند.

## متدهای نمونه

- {{domxref("Crypto.getRandomValues()")}}
  - : آرایه‌ی {{ jsxref("TypedArray") }} داده‌شده را با مقادیر تصادفی امن از نظر رمزنگاری پر می‌کند.
- {{domxref("Crypto.randomUUID()")}} {{SecureContext_inline}}
  - : یک UUID نسخه‌ی 4 به طول 36 کاراکتر که به‌صورت تصادفی تولید شده است برمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [امنیت وب](/en-US/docs/Web/Security)
- [بافتارهای امن](/en-US/docs/Web/Security/Defenses/Secure_Contexts)
- [ویژگی‌های محدودشده به بافتارهای امن](/en-US/docs/Web/Security/Defenses/Secure_Contexts/features_restricted_to_secure_contexts)
- [امنیت لایه انتقال](/en-US/docs/Web/Security/Defenses/Transport_Layer_Security)
- [Strict-Transport-Security](/en-US/docs/Web/HTTP/Reference/Headers/Strict-Transport-Security)