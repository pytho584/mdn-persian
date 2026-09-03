---
title: "PaymentRequestEvent: total property"
short-title: total
slug: Web/API/PaymentRequestEvent/total
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PaymentRequestEvent.total
---

{{SeeCompatTable}}{{APIRef("Web-Based Payment Handler API")}}{{AvailableInWorkers("service")}}

ویژگی فقطخواندنی **`total`** از رابط {{domxref("PaymentRequestEvent")}} یک شیء `PaymentCurrencyAmount` شامل مبلغ کل درخواست‌شده برای پرداخت را برمی‌گرداند.

## مقدار

یک شیء `PaymentCurrencyAmount`. این شیء دارای ویژگی‌های زیر است:

- `currency`
  - : یک رشته شامل کد ارز استاندارد سه‌حرفی [ISO 4217](https://www.iso.org/iso-4217-currency-codes.html) که ارز پرداخت را نشان می‌دهد. مثال‌ها عبارتند از `USD`، `CAN` و `GBP`.
- `value`
  - : یک رشته شامل یک مقدار پولی اعشاری، به‌عنوان مثال `2.55`.

## مثال‌ها

```js
self.addEventListener("paymentrequest", (e) => {
  console.log(e.total);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [نمای کلی برنامه‌های پرداخت مبتنی بر وب](https://web.dev/articles/web-based-payment-apps-overview)
- [راه‌اندازی یک روش پرداخت](https://web.dev/articles/setting-up-a-payment-method)
- [چرخه حیات یک تراکنش پرداخت](https://web.dev/articles/life-of-a-payment-transaction)
- [استفاده از API درخواست پرداخت](/en-US/docs/Web/API/Payment_Request_API/Using_the_Payment_Request_API)
- [مفاهیم پردازش پرداخت](/en-US/docs/Web/API/Payment_Request_API/Concepts)