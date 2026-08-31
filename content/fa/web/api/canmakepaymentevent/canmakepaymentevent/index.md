---
title: "CanMakePaymentEvent: CanMakePaymentEvent() constructor"
source: "https://developer.mozilla.org/en-US/docs/Web/API/CanMakePaymentEvent/CanMakePaymentEvent"
translated_by: "n8n + AI"
---

---
title: "CanMakePaymentEvent: CanMakePaymentEvent() constructor"
short-title: CanMakePaymentEvent()
slug: Web/API/CanMakePaymentEvent/CanMakePaymentEvent
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.CanMakePaymentEvent.CanMakePaymentEvent
---

{{APIRef("Web-Based Payment Handler API")}}{{SeeCompatTable}}{{AvailableInWorkers("service")}}

**`CanMakePaymentEvent()`** سازنده، یک نمونه جدید از شی {{domxref("CanMakePaymentEvent")}} ایجاد می‌کند.

## نحو (Syntax)

```js-nolint
new CanMakePaymentEvent(type)
```

### پارامترها

- `type`
  - : یک رشته است که نوع رویداد را نشان می‌دهد. در مورد `CanMakePaymentEvent` این مقدار همیشه `canmakepayment` است.

## مثال‌ها

یک توسعه‌دهنده از این سازنده به صورت دستی استفاده نمی‌کند. یک شیء جدید `CanMakePaymentEvent` زمانی ساخته می‌شود که یک هندلر در نتیجهٔ رویداد {{domxref("ServiceWorkerGlobalScope.canmakepayment_event", "canmakepayment")}} فراخوانی شود.

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

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Web-based Payment Handler API", "", "", "nocode")}}
- [بررسی اجمالی برنامه‌های پرداخت مبتنی بر وب](https://web.dev/articles/web-based-payment-apps-overview)
- [راه‌اندازی یک روش پرداخت](https://web.dev/articles/setting-up-a-payment-method)
- [چرخه حیات یک تراکنش پرداخت](https://web.dev/articles/life-of-a-payment-transaction)
- [استفاده از Payment Request API](/en-US/docs/Web/API/Payment_Request_API/Using_the_Payment_Request_API)
- [مفاهیم پردازش پرداخت](/en-US/docs/Web/API/Payment_Request_API/Concepts)