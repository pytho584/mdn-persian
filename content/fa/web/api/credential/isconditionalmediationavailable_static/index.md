---
title: "Credential: isConditionalMediationAvailable() static method"
---

---
title: "Credential: isConditionalMediationAvailable() static method"
short-title: isConditionalMediationAvailable()
slug: Web/API/Credential/isConditionalMediationAvailable_static
page-type: web-api-static-method
browser-compat: api.Credential.isConditionalMediationAvailable_static
---

{{APIRef("Web Authentication API")}}{{securecontext_header}}

متد ایستای **`isConditionalMediationAvailable()`** از رابط {{domxref("Credential")}} یک {{jsxref("Promise")}} برمی‌گرداند که به `false` resolve می‌شود.

زیرکلاس‌های {{domxref("Credential")}} در صورت پشتیبانی از میانجی‌گری شرطی (conditional mediation)، این متد را بازنویسی می‌کنند. برای مثال، به {{domxref("PublicKeyCredential.isConditionalMediationAvailable_static", "PublicKeyCredential.isConditionalMediationAvailable()")}} مراجعه کنید.

## سینتکس

```js-nolint
Credential.isConditionalMediationAvailable()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به `false` resolve می‌شود.

## مثال‌ها

```js
await Credential.isConditionalMediationAvailable(); // false
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}