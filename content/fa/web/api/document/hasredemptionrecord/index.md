---
title: "Document: hasRedemptionRecord() method"
---

---
title: "Document: hasRedemptionRecord() method"
short-title: hasRedemptionRecord()
slug: Web/API/Document/hasRedemptionRecord
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.Document.hasRedemptionRecord
---

{{APIRef("Storage Access API")}}{{SeeCompatTable}}

متد **`hasRedemptionRecord()`** از رابط {{domxref("Document")}} یک promise برمی‌گرداند که با یک مقدار بولی (boolean) تحقق می‌یابد و نشان می‌دهد که آیا مرورگر یک [redemption record](/en-US/docs/Web/API/Private_State_Token_API/Using#redeeming_tokens) (سابقهٔ بازخرید) متعلق به یک صادرکنندهٔ خاص دارد یا خیر.

## نحو (Syntax)

```js-nolint
hasRedemptionRecord(issuer)
```

### پارامترها

- `issuer`
  - : یک رشته (string) که URL سرور صادرکننده را نمایش می‌دهد.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک مقدار بولی resolve می‌شود و نشان می‌دهد که آیا مرورگر یک redemption record ذخیره‌شده دارد که از سرور صادرکنندهٔ مشخص‌شده منشأ گرفته است.

### استثناها

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر {{domxref("Document")}} فعلی هنوز فعال (active) نباشد، پرتاب می‌شود.
- `NotAllowedError` {{domxref("DOMException")}}
  - : اگر {{domxref("Document")}} فعلی در یک بافت امن (secure context) بارگذاری نشده باشد، پرتاب می‌شود.
- `TypeError` {{domxref("DOMException")}}
  - : اگر `issuer` یک URL معتبر نباشد، پرتاب می‌شود.

## مثال‌ها

```js
const hasRR = await Document.hasRedemptionRecord(`issuer.example`);
if (hasRR) {
  await fetch("some-resource.example", {
    method: "POST",
    privateToken: {
      version: 1,
      operation: "send-redemption-record",
      issuers: ["https://issuer.example"],
    },
  });
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Private State Token API](/en-US/docs/Web/API/Private_State_Token_API)