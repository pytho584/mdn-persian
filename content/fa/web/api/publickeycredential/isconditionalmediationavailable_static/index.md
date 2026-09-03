---
title: "PublicKeyCredential: isConditionalMediationAvailable() static method"
short-title: isConditionalMediationAvailable()
slug: Web/API/PublicKeyCredential/isConditionalMediationAvailable_static
page-type: web-api-static-method
browser-compat: api.PublicKeyCredential.isConditionalMediationAvailable_static
---

{{APIRef("Web Authentication API")}}{{securecontext_header}}

متد ایستای **`isConditionalMediationAvailable()`** از رابط {{domxref("PublicKeyCredential")}} یک {{jsxref("Promise")}} برمی‌گرداند که اگر [میانجیگری شرطی](/en-US/docs/Web/API/Web_Authentication_API#autofill_ui) در دسترس باشد، به `true` resolve می‌شود.

## سینتکس

```js-nolint
PublicKeyCredential.isConditionalMediationAvailable()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک مقدار بولی resolve می‌شود و نشان می‌دهد که آیا میانجیگری شرطی در دسترس است یا نه.

### استثناها

{{jsxref("Promise")}} بازگشتی ممکن است با مقادیر زیر رد شود:

- `SecurityError` {{domxref("DOMException")}}
  - : دامنهٔ RP معتبر نیست.

## مثال‌ها

پیش از فراخوانی یک WebAuthn API شرطی، بررسی کنید که:

- مرورگر از Web Authentication API پشتیبانی می‌کند.
- مرورگر از میانجیگری شرطی پشتیبانی می‌کند.

```js
// Availability of `window.PublicKeyCredential` means WebAuthn is usable.
if (
  window.PublicKeyCredential &&
  PublicKeyCredential.isConditionalMediationAvailable
) {
  // Check if conditional mediation is available.
  const isCMA = await PublicKeyCredential.isConditionalMediationAvailable();
  if (isCMA) {
    // Call WebAuthn authentication
    const publicKeyCredentialRequestOptions = {
      // Server generated challenge
      challenge: challengeFromServer,
      // The same RP ID as used during registration
      rpId: "example.com",
    };

    const credential = await navigator.credentials.get({
      publicKey: publicKeyCredentialRequestOptions,
      signal: abortController.signal,
      // Specify 'conditional' to activate conditional UI
      mediation: "conditional",
    });
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}