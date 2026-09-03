---
title: "PaymentRequestEvent: paymentRequestOrigin property"
short-title: paymentRequestOrigin
slug: Web/API/PaymentRequestEvent/paymentRequestOrigin
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PaymentRequestEvent.paymentRequestOrigin
---

{{SeeCompatTable}}{{APIRef("Web-Based Payment Handler API")}}{{AvailableInWorkers("service")}}

ویژگی فقط‌خواندنی **`paymentRequestOrigin`** از رابط {{domxref("PaymentRequestEvent")}}، مبدأ (origin)ای را برمی‌گرداند که شیء {{domxref("PaymentRequest")}} در آن مقداردهی اولیه شده است.

## مقدار

یک رشته (string).

## مثال‌ها

```js
self.addEventListener("paymentrequest", (e) => {
  console.log(e.paymentRequestOrigin);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [مروری بر برنامه‌های پرداخت مبتنی بر وب](https://web.dev/articles/web-based-payment-apps-overview)
- [راه‌اندازی یک روش پرداخت](https://web.dev/articles/setting-up-a-payment-method)
- [چرخه‌ی یک تراکنش پرداخت](https://web.dev/articles/life-of-a-payment-transaction)
- [استفاده از Payment Request API](/en-US/docs/Web/API/Payment_Request_API/Using_the_Payment_Request_API)
- [مفاهیم پردازش پرداخت](/en-US/docs/Web/API/Payment_Request_API/Concepts)