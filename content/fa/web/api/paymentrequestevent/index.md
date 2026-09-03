---
title: PaymentRequestEvent
slug: Web/API/PaymentRequestEvent
page-type: web-api-interface
status:
  - experimental
browser-compat: api.PaymentRequestEvent
---

{{SeeCompatTable}}{{APIRef("Web-Based Payment Handler API")}}{{AvailableInWorkers("service")}}

رابط **`PaymentRequestEvent`** از {{domxref("Web-based Payment Handler API", "", "", "nocode")}}، شیءای است که هنگام ایجاد یک {{domxref("PaymentRequest")}} به پردازنده‌ی پرداخت ارسال می‌شود.

{{InheritanceDiagram}}

## سازنده

- {{domxref("PaymentRequestEvent.PaymentRequestEvent","PaymentRequestEvent()")}} {{Experimental_Inline}}
  - : یک نمونه‌ی جدید از شیء `PaymentRequestEvent` ایجاد می‌کند.

## ویژگی‌های نمونه

- {{domxref("PaymentRequestEvent.methodData","methodData")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : آرایه‌ای از اشیاء شامل شناسه‌های روش پرداخت برای روش‌های پرداختی که وب‌سایت می‌پذیرد، و همچنین داده‌های اختصاصی مرتبط با هر روش پرداخت را برمی‌گرداند.
- {{domxref("PaymentRequestEvent.modifiers","modifiers")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : آرایه‌ای از اشیاء شامل تغییرات اعمال‌شده در جزئیات پرداخت را برمی‌گرداند.
- {{domxref("PaymentRequestEvent.paymentRequestId","paymentRequestId")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : شناسه‌ی شیء {{domxref("PaymentRequest")}} را برمی‌گرداند.
- {{domxref("PaymentRequestEvent.paymentRequestOrigin","paymentRequestOrigin")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : مبدأ (origin) ای را برمی‌گرداند که شیء {{domxref("PaymentRequest")}} در آن مقداردهی اولیه شده است.
- {{domxref("PaymentRequestEvent.topOrigin","topOrigin")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : مبدأ سطح بالا (top-level origin) را برمی‌گرداند که شیء {{domxref("PaymentRequest")}} در آن مقداردهی اولیه شده است.
- {{domxref("PaymentRequestEvent.total","total")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : مبلغ کل درخواست‌شده برای پرداخت را برمی‌گرداند.

## متدهای نمونه

- {{domxref("PaymentRequestEvent.changePaymentMethod","changePaymentMethod()")}} {{Experimental_Inline}}
  - : با در نظر گرفتن جزئیات روش پرداخت، مبلغ کل به‌روزرسانی‌شده را دریافت می‌کند.
- {{domxref("PaymentRequestEvent.openWindow","openWindow()")}} {{Experimental_Inline}}
  - : URL داده‌شده را در یک پنجره‌ی جدید باز می‌کند، فقط و فقط اگر URL داده‌شده با مبدأ صفحه‌ی فراخوان‌کننده یکسان باشد. این متد یک {{jsxref("Promise")}} برمی‌گرداند که با ارجاعی به {{domxref("WindowClient")}} حل می‌شود.
- {{domxref("PaymentRequestEvent.respondWith","respondWith()")}} {{Experimental_Inline}}
  - : از مدیریت پیش‌فرض رویداد جلوگیری می‌کند و به شما امکان می‌دهد خودتان یک {{jsxref("Promise")}} برای یک شیء {{domxref("PaymentResponse")}} فراهم کنید.

## مثال‌ها

هنگامی که متد {{domxref("PaymentRequest.show()")}} فراخوانی می‌شود، یک رویداد {{domxref("ServiceWorkerGlobalScope.paymentrequest_event", "paymentrequest")}} روی سرویس‌ورکر اپلیکیشن پرداخت پرتاب می‌شود. به این رویداد درون سرویس‌ورکر اپلیکیشن پرداخت گوش داده می‌شود تا مرحله‌ی بعدی فرایند پرداخت آغاز شود.

```js
let paymentRequestEvent;
let resolver;
let client;

// `self` is the global object in service worker
self.addEventListener("paymentrequest", async (e) => {
  if (paymentRequestEvent) {
    // If there's an ongoing payment transaction, reject it.
    resolver.reject();
  }
  // Preserve the event for future use
  paymentRequestEvent = e;

  // …
});
```

هنگامی که یک رویداد `paymentrequest` دریافت می‌شود، اپلیکیشن پرداخت می‌تواند با فراخوانی {{domxref("PaymentRequestEvent.openWindow()")}} پنجره‌ی پردازنده‌ی پرداخت را باز کند. این پنجره، رابطی از اپلیکیشن پرداخت را به مشتریان نمایش می‌دهد که در آن می‌توانند احراز هویت کنند، آدرس و گزینه‌های حمل‌ونقل را انتخاب کنند و پرداخت را تأیید نمایند.

هنگامی که پرداخت پردازش شد، از {{domxref("PaymentRequestEvent.respondWith()")}} برای بازگرداندن نتیجه‌ی پرداخت به وب‌سایت فروشنده استفاده می‌شود.

برای جزئیات بیشتر درباره‌ی این مرحله، [دریافت رویداد درخواست پرداخت از فروشنده](https://web.dev/articles/orchestrating-payment-transactions#receive-payment-request-event) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [مروری بر اپلیکیشن‌های پرداخت مبتنی بر وب](https://web.dev/articles/web-based-payment-apps-overview)
- [راه‌اندازی یک روش پرداخت](https://web.dev/articles/setting-up-a-payment-method)
- [چرخه‌ی حیات یک تراکنش پرداخت](https://web.dev/articles/life-of-a-payment-transaction)
- [استفاده از Payment Request API](/en-US/docs/Web/API/Payment_Request_API/Using_the_Payment_Request_API)
- [مفاهیم پردازش پرداخت](/en-US/docs/Web/API/Payment_Request_API/Concepts)