---
title: "Document: hasPrivateToken() method"
---

---
title: "Document: hasPrivateToken() method"
short-title: hasPrivateToken()
slug: Web/API/Document/hasPrivateToken
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.Document.hasPrivateToken
---

{{APIRef("Storage Access API")}}{{SeeCompatTable}}

متد **`hasPrivateToken()`** از رابط {{domxref("Document")}} یک وعده (Promise) برمی‌گرداند که با یک مقدار بولی (boolean) انجام می‌شود و نشان می‌دهد که آیا مرورگر یک [private state token](/en-US/docs/Web/API/Private_State_Token_API) از یک سرور صادرکننده خاص ذخیره کرده است یا خیر.

## Syntax

```js-nolint
hasPrivateToken(issuer)
```

### پارامترها

- `issuer`
  - : یک رشته (string) که نشانی اینترنتی (URL) سرور صادرکننده را نشان می‌دهد.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک مقدار بولی (boolean) حل می‌شود و نشان می‌دهد که آیا مرورگر یک private state token از سرور صادرکننده مشخص شده ذخیره کرده است یا خیر.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر {{domxref("Document")}} فعلی هنوز فعال نباشد، پرتاب می‌شود.
- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر یکی از شرایط زیر برقرار باشد، پرتاب می‌شود:
    - {{domxref("Document")}} فعلی در یک [secure context (زمینه امن)](/en-US/docs/Glossary/Secure_Context) بارگذاری نشده باشد.
    - حداکثر تعداد صادرکنندگان به ازای هر [origin (مبدا)](/en-US/docs/Glossary/Origin) سطح بالا (دو) بیش از حد مجاز شده باشد.
- `TypeError` {{domxref("DOMException")}}
  - : اگر `issuer` یک URL معتبر نباشد، پرتاب می‌شود.

## مثال‌ها

```js
const hasToken = await Document.hasPrivateToken(`issuer.example`);
if (!hasToken) {
  await fetch(
    "https://issuer.example/.well-known/private-state-token/issuance",
    {
      method: "POST",
      privateToken: {
        version: 1,
        operation: "token-request",
      },
    },
  );
}
```

## مشخصات فنی

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Private State Token API](/en-US/docs/Web/API/Private_State_Token_API)