---
title: "PaymentResponse: toJSON() method"
short-title: toJSON()
slug: Web/API/PaymentResponse/toJSON
page-type: web-api-instance-method
browser-compat: api.PaymentResponse.toJSON
---

{{SecureContext_Header}}{{APIRef("Payment Request API")}}

متد **`toJSON()`** از رابط {{domxref("PaymentResponse")}} یک {{Glossary("Serialization","سریالساز")}} است؛ این متد یک نمایش JSON از شیء {{domxref("PaymentResponse")}} برمی‌گرداند.

## Syntax

```js-nolint
toJSON()
```

### Parameters

هیچکدام.

### Return value

یک شیء {{jsxref("JSON")}} که نمایش سریالسازی شده شیء {{domxref("PaymentResponse")}} است.

## Examples

### استفاده از متد toJSON

در این مثال، فراخوانی `paymentResponse.toJSON()` یک نمایش JSON از شیء `PaymentResponse` برمی‌گرداند.

```js
payment.show().then((paymentResponse) => {
  console.log(paymentResponse.toJSON());
});
```

برای دریافت یک رشته JSON، می‌توانید مستقیماً از [`JSON.stringify(paymentResponse)`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify) استفاده کنید؛ این متد به طور خودکار `toJSON()` را فراخوانی می‌کند.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{jsxref("JSON")}}