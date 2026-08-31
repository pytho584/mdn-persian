---
title: "CanMakePaymentEvent"
source: "https://developer.mozilla.org/en-US/docs/Web/API/CanMakePaymentEvent"
translated_by: "n8n + AI"
---

---
title: CanMakePaymentEvent
slug: Web/API/CanMakePaymentEvent
page-type: web-api-interface
status:
  - experimental
browser-compat: api.CanMakePaymentEvent
---

{{APIRef("Web-Based Payment Handler API")}}{{SeeCompatTable}}{{AvailableInWorkers("service")}}

رابط **`CanMakePaymentEvent`** از {{domxref("Web-based Payment Handler API", "", "", "nocode")}}، شیء رویداد برای رویداد {{domxref("ServiceWorkerGlobalScope.canmakepayment_event", "canmakepayment")}} است که در سرویس‌ورکر یک برنامه پرداخت برای بررسی آمادگی آن برای مدیریت یک پرداخت، فعال می‌شود. به طور خاص، زمانی که وب‌سایت فروشنده سازنده {{domxref("PaymentRequest.PaymentRequest", "PaymentRequest()")}} را فراخوانی می‌کند، این رویداد فعال می‌شود.

{{InheritanceDiagram}}

## سازنده

- {{domxref("CanMakePaymentEvent.CanMakePaymentEvent", "CanMakePaymentEvent()")}} {{Experimental_Inline}}
  - یک نمونه جدید از شیء `CanMakePaymentEvent` ایجاد می‌کند.

## روش‌های نمونه

- {{domxref("CanMakePaymentEvent.respondWith", "respondWith()")}} {{Experimental_Inline}}
  - سرویس‌ورکر را قادر می‌سازد تا به طور مناسب پاسخ دهد تا نشان دهد آیا آماده پردازش پرداخت‌ها است یا خیر.

## مثال‌ها

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

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Web-based Payment Handler API", "", "", "nocode")}}
- [Web-based payment apps overview](https://web.dev/articles/web-based-payment-apps-overview)
- [Setting up a payment method](https://web.dev/articles/setting-up-a-payment-method)
- [Life of a payment transaction](https://web.dev/articles/life-of-a-payment-transaction)
- [Using the Payment Request API](/en-US/docs/Web/API/Payment_Request_API/Using_the_Payment_Request_API)
- [Payment processing concepts](/en-US/docs/Web/API/Payment_Request_API/Concepts)