---
title: "PaymentRequestEvent: topOrigin property"
---

---
title: "PaymentRequestEvent: topOrigin property"
short-title: topOrigin
slug: Web/API/PaymentRequestEvent/topOrigin
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PaymentRequestEvent.topOrigin
---

{{SeeCompatTable}}{{APIRef("Web-Based Payment Handler API")}}{{AvailableInWorkers("service")}}

ویژگی فقط‌خواندنی **`topOrigin`** از رابط {{domxref("PaymentRequestEvent")}}، مبدأ (origin) سطح‌بالای دریافت‌کنندهٔ پرداخت را بازمی‌گرداند؛ جایی که شیء {{domxref("PaymentRequest")}} مقداردهی اولیه شده است.

## مقدار

یک رشته (string).

## مثال‌ها

```js
self.addEventListener("paymentrequest", (e) => {
  console.log(e.topOrigin);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [مروری بر اپلیکیشن‌های پرداخت مبتنی بر وب](https://web.dev/articles/web-based-payment-apps-overview)
- [راه‌اندازی یک روش پرداخت](https://web.dev/articles/setting-up-a-payment-method)
- [چرخهٔ حیات یک تراکنش پرداخت](https://web.dev/articles/life-of-a-payment-transaction)
- [استفاده از Payment Request API](/en-US/docs/Web/API/Payment_Request_API/Using_the_Payment_Request_API)
- [مفاهیم پردازش پرداخت](/en-US/docs/Web/API/Payment_Request_API/Concepts)