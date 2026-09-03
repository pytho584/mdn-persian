---
title: "PaymentRequestEvent: PaymentRequestEvent() constructor"
short-title: PaymentRequestEvent()
slug: Web/API/PaymentRequestEvent/PaymentRequestEvent
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.PaymentRequestEvent.PaymentRequestEvent
---

{{APIRef("Web-Based Payment Handler API")}}{{SeeCompatTable}}{{AvailableInWorkers("service")}}

سازنده **`PaymentRequestEvent()`** یک نمونه جدید از شی {{domxref("PaymentRequestEvent")}} می‌سازد.

## Syntax

```js-nolint
new PaymentRequestEvent(type)
new PaymentRequestEvent(type, options)
```

### پارامترها

- `type`
  - : یک رشته شامل نام رویداد. این مقدار به حروف بزرگ و کوچک حساس است و مرورگرها آن را به `paymentrequest` تنظیم می‌کنند.
- `options` {{optional_inline}}
  - : یک شی که علاوه بر ویژگی‌های تعریف‌شده در {{domxref("ExtendableEvent/ExtendableEvent", "ExtendableEvent()")}}، می‌تواند ویژگی‌های زیر را داشته باشد:
    - `methodData`
      - : آرایه‌ای از اشیاء `PaymentMethodData` (به [`methodData` > مقدار](/en-US/docs/Web/API/PaymentRequestEvent/methodData#value) مراجعه کنید) که شامل شناسه‌های روش پرداخت برای روش‌های پرداخت پذیرفته‌شده توسط وب‌سایت و هر داده مرتبط با روش پرداخت خاص است.
    - `modifiers`
      - : آرایه‌ای از اشیاء حاوی تغییرات در جزئیات پرداخت.
    - `paymentRequestId`
      - : شناسه شی {{domxref("PaymentRequest")}}.
    - `paymentRequestOrigin`
      - : مبدأ (origin) جایی که شی {{domxref("PaymentRequest")}} مقداردهی اولیه شده است.
    - `topOrigin`
      - : مبدأ سطح بالایی که شی {{domxref("PaymentRequest")}} در آن مقداردهی اولیه شده است.
    - `total`
      - : کل مبلغ درخواست‌شده برای پرداخت.

### مقدار بازگشتی

یک شی جدید {{domxref("PaymentRequestEvent")}}.

## مثال‌ها

یک توسعه‌دهنده معمولاً از این سازنده به صورت دستی استفاده نمی‌کند. یک شی `PaymentRequestEvent` جدید وقتی ساخته می‌شود که یک handler در نتیجه فعال شدن رویداد {{domxref("ServiceWorkerGlobalScope.paymentrequest_event", "paymentrequest")}} فراخوانی شود.

```js
self.addEventListener("paymentrequest", (e) => {
  // …
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [مروری بر برنامه‌های پرداخت مبتنی بر وب](https://web.dev/articles/web-based-payment-apps-overview)
- [تنظیم یک روش پرداخت](https://web.dev/articles/setting-up-a-payment-method)
- [زندگی یک تراکنش پرداخت](https://web.dev/articles/life-of-a-payment-transaction)
- [استفاده از Payment Request API](/en-US/docs/Web/API/Payment_Request_API/Using_the_Payment_Request_API)
- [مفاهیم پردازش پرداخت](/en-US/docs/Web/API/Payment_Request_API/Concepts)