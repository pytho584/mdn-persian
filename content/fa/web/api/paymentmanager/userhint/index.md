---
title: "PaymentManager: userHint property"
short-title: userHint
slug: Web/API/PaymentManager/userHint
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PaymentManager.userHint
---

{{APIRef("Web-Based Payment Handler API")}}{{SeeCompatTable}}{{SecureContext_Header}}

ویژگی **`userHint`** از رابط {{domxref("PaymentManager")}} یک راهنما (Hint) برای مرورگر فراهم می‌کند تا در کنار نام و نماد برنامه‌ی پرداخت در رابط کاربری Web-based Payment Handler نمایش داده شود.

## مقدار

یک رشته (String).

## نمونه‌ها

```js
navigator.serviceWorker.register("serviceworker.js").then((registration) => {
  registration.paymentManager.userHint = "شماره کارت باید ۱۶ رقم باشد";

  registration.paymentManager
    .enableDelegations(["shippingAddress", "payerName"])
    .then(() => {
      // …
    });

  // …
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Web-based Payment Handler API", "", "", "nocode")}}
- [مروری بر برنامه‌های پرداخت مبتنی بر وب](https://web.dev/articles/web-based-payment-apps-overview)
- [راه‌اندازی یک روش پرداخت](https://web.dev/articles/setting-up-a-payment-method)
- [چرخه‌ی یک تراکنش پرداخت](https://web.dev/articles/life-of-a-payment-transaction)
- [استفاده از Payment Request API](/en-US/docs/Web/API/Payment_Request_API/Using_the_Payment_Request_API)
- [مفاهیم پردازش پرداخت](/en-US/docs/Web/API/Payment_Request_API/Concepts)