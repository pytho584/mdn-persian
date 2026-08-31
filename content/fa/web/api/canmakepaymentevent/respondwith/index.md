---
title: "CanMakePaymentEvent: respondWith() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/CanMakePaymentEvent/respondWith"
translated_by: "n8n + AI"
---

---
title: "CanMakePaymentEvent: respondWith() method"
short-title: respondWith()
slug: Web/API/CanMakePaymentEvent/respondWith
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.CanMakePaymentEvent.respondWith
---

{{APIRef("Web-Based Payment Handler API")}}{{SeeCompatTable}}{{AvailableInWorkers("service")}}

متد **`respondWith()`** از رابط {{domxref("CanMakePaymentEvent")}} به سرویس‌ورکر اجازه می‌دهد تا به‌طور مناسب پاسخ دهد و سیگنال دهد که آیا آماده رسیدگی به پرداخت‌ها است یا نه.

## Syntax

```js-nolint
respondWith(response)
```

### Parameters

- `response`
  - : یک {{jsxref("Promise")}} که با یک مقدار بولین resolve می‌شود تا سیگنال دهد که آیا برای رسیدگی به درخواست پرداخت آماده است: (`true`) یا آماده نیست (`false`).

### Return value

هیچ‌کدام (`undefined`).

## Examples

```js
self.addEventListener("canmakepayment", (e) => {
  e.respondWith(
    new Promise((resolve, reject) => {
      someAppSpecificLogic()
        .then((result) => {
          resolve(result);
        })
        .catch((error) => {
          reject(error);
        });
    }),
  );
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("Web-based Payment Handler API", "", "", "nocode")}}
- [Web-based payment apps overview](https://web.dev/articles/web-based-payment-apps-overview)
- [Setting up a payment method](https://web.dev/articles/setting-up-a-payment-method)
- [Life of a payment transaction](https://web.dev/articles/life-of-a-payment-transaction)
- [Using the Payment Request API](/en-US/docs/Web/API/Payment_Request_API/Using_the_Payment_Request_API)
- [Payment processing concepts](/en-US/docs/Web/API/Payment_Request_API/Concepts)