---
title: "PaymentRequestEvent: changePaymentMethod() method"
short-title: changePaymentMethod()
slug: Web/API/PaymentRequestEvent/changePaymentMethod
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.PaymentRequestEvent.changePaymentMethod
---

{{APIRef("Web-Based Payment Handler API")}}{{SeeCompatTable}}{{AvailableInWorkers("service")}}

متد **`changePaymentMethod()`** از رابط {{domxref("PaymentRequestEvent")}} توسط پردازنده پرداخت برای دریافت جمع مبلغ به‌روزرسانی‌شده، با توجه به جزئیاتی مانند آدرس صورت‌حسابِ روش پرداخت، استفاده می‌شود.

هنگامی که این متد فراخوانی می‌شود، یک رویداد {{domxref("PaymentMethodChangeEvent")}} شلیک می‌شود.

## نحو

```js-nolint
changePaymentMethod(methodName)
changePaymentMethod(methodName, methodDetails)
```

### پارامترها

- `methodName`
  - : نام روش پرداختی که قرار است استفاده شود.
- `methodDetails` {{optional_inline}}
  - : یک شیء حاوی جزئیات مخصوص روش پرداخت که در حال به‌روزرسانی هستند.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یک شیء `PaymentRequestDetailsUpdate` حل می‌شود. این شیء شامل ویژگی‌های زیر است:

- `error`
  - : رشته‌ای که توضیح می‌دهد چرا روش پرداخت انتخاب‌شده توسط کاربر قابل استفاده نیست.
- `total`
  - : جمع مبلغ به‌روزرسانی‌شده بر اساس روش پرداخت تغییر یافته. جمع مبلغ ممکن است تغییر کند، برای مثال، به این دلیل که آدرس صورت‌حساب روش پرداختی که کاربر انتخاب کرده است، مالیات فروش قابل اعمال را تغییر می‌دهد.
- `modifiers`
  - : یک {{jsxref("Array")}} از اشیاء `PaymentDetailsModifier` که ویژگی‌های آن‌ها در {{domxref("PaymentRequestEvent.modifiers")}} توضیح داده شده است.
- `paymentMethodErrors`
  - : شیئی حاوی خطاهای اعتبارسنجی برای روش پرداخت، در صورت وجود.

## مثال‌ها

مثال زیر یک قطعه کد ساده را نشان می‌دهد که می‌توان از آن در یک سرویس‌کارگر (Service Worker) برای ارسال اعلان تغییر روش پرداخت به پنجرهٔ اصلی پردازنده پرداخت استفاده کرد. برای یک نمونه کامل آزمایش، به [پردازنده پرداخت برای آزمایش رویداد تغییر روش پرداخت](https://rsolomakhin.github.io/pr/apps/pmc/) مراجعه کنید.

```js
function notifyPaymentMethodChanged(e) {
  e.changePaymentMethod("someMethod")
    .then((paymentMethodChangeResponse) => {
      paymentHandlerWindow.postMessage(paymentMethodChangeResponse);
    })
    .catch((error) => {
      sendMessage({ error: error.message });
    });
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [نمای کلی برنامه‌های پرداخت مبتنی بر وب](https://web.dev/articles/web-based-payment-apps-overview)
- [راه‌اندازی یک روش پرداخت](https://web.dev/articles/setting-up-a-payment-method)
- [چرخهٔ عمر یک تراکنش پرداخت](https://web.dev/articles/life-of-a-payment-transaction)
- [استفاده از Payment Request API](/en-US/docs/Web/API/Payment_Request_API/Using_the_Payment_Request_API)
- [مفاهیم پردازش پرداخت](/en-US/docs/Web/API/Payment_Request_API/Concepts)