---
title: PaymentManager
slug: Web/API/PaymentManager
page-type: web-api-interface
status:
  - experimental
browser-compat: api.PaymentManager
---

{{APIRef("Web-Based Payment Handler API")}}{{SeeCompatTable}}{{SecureContext_Header}}

رابط **`PaymentManager`** از {{domxref("Web-based Payment Handler API", "", "", "nocode")}} برای مدیریت جنبه‌های مختلف عملکرد برنامه‌های پرداخت استفاده می‌شود.

دسترسی به این رابط از طریق ویژگی {{domxref("ServiceWorkerRegistration.paymentManager")}} فراهم می‌شود.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("PaymentManager.userHint", "userHint")}} {{Experimental_Inline}}
  - : راهنمایی برای مرورگر فراهم می‌کند تا در کنار نام و نماد برنامه‌ی پرداخت در رابط کاربری Web-based Payment Handler نمایش داده شود.

## روش‌های نمونه

- {{domxref("PaymentManager.enableDelegations", "enableDelegations()")}} {{Experimental_Inline}}
  - : مسئولیت ارائه بخش‌های مختلف اطلاعات پرداخت مورد نیاز را به برنامه‌ی پرداخت واگذار می‌کند، به جای اینکه از مرورگر جمع‌آوری شود (مثلاً از طریق تکمیل خودکار).

## نمونه‌ها

```js
navigator.serviceWorker.register("serviceworker.js").then((registration) => {
  registration.paymentManager.userHint = "Card number should be 16 digits";

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

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Web-based Payment Handler API", "", "", "nocode")}}
- [مروری بر برنامه‌های پرداخت مبتنی بر وب](https://web.dev/articles/web-based-payment-apps-overview)
- [راه‌اندازی یک روش پرداخت](https://web.dev/articles/setting-up-a-payment-method)
- [چرخه‌ی عمر یک تراکنش پرداخت](https://web.dev/articles/life-of-a-payment-transaction)
- [استفاده از Payment Request API](/en-US/docs/Web/API/Payment_Request_API/Using_the_Payment_Request_API)
- [مفاهیم پردازش پرداخت](/en-US/docs/Web/API/Payment_Request_API/Concepts)