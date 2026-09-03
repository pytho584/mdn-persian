---
title: "PaymentRequestEvent: methodData property"
short-title: methodData
slug: Web/API/PaymentRequestEvent/methodData
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PaymentRequestEvent.methodData
---

{{SeeCompatTable}}{{APIRef("Web-Based Payment Handler API")}}{{AvailableInWorkers("service")}}

ویژگی فقط‑خواندنی **`methodData`** در رابط {{domxref("PaymentRequestEvent")}} آرایه‌ای از اشیاء `PaymentMethodData` را بازمی‌گرداند که شامل شناسه‌های روش‌های پرداخت پذیرفته‌شده توسط وب‌سایت و هر داده اضافی مختص آن روش‌های پرداخت است.

## مقدار

آرایه‌ای از اشیاء `PaymentMethodData`. هر شیء شامل ویژگی‌های زیر است:

- `supportedMethods`
  - : یک شناسه روش پرداخت برای روش پرداختی که وب‌سایت فروشنده می‌پذیرد.
- `data`
  - : یک شیء که اطلاعات اختیاری مورد نیاز احتمالی روش‌های پرداخت پشتیبانی‌شده را فراهم می‌کند. در صورت ارائه، به صورت JSON سریال‌سازی خواهد شد.

## مثال‌ها

```js
self.addEventListener("paymentrequest", (e) => {
  console.log(e.methodData);
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [مروری بر برنامه‌های پرداخت مبتنی بر وب](https://web.dev/articles/web-based-payment-apps-overview)
- [راه‌اندازی یک روش پرداخت](https://web.dev/articles/setting-up-a-payment-method)
- [چرخه یک تراکنش پرداخت](https://web.dev/articles/life-of-a-payment-transaction)
- [استفاده از Payment Request API](/en-US/docs/Web/API/Payment_Request_API/Using_the_Payment_Request_API)
- [مفاهیم پردازش پرداخت](/en-US/docs/Web/API/Payment_Request_API/Concepts)