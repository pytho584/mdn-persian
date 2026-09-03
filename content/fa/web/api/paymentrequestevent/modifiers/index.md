---
title: "PaymentRequestEvent: modifiers property"
short-title: modifiers
slug: Web/API/PaymentRequestEvent/modifiers
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.PaymentRequestEvent.modifiers
---

{{SeeCompatTable}}{{APIRef("Web-Based Payment Handler API")}}{{AvailableInWorkers("service")}}

ویژگی فقط‌خواندنی **`modifiers`** در رابط {{domxref("PaymentRequestEvent")}} یک {{jsxref("Array")}} از اشیاء `PaymentDetailsModifier` برمی‌گرداند که شامل اصلاح‌کننده‌هایی برای جزئیات پرداخت هستند.

## مقدار

آرایه‌ای از اشیاء حاوی اصلاح‌کننده‌ها برای جزئیات پرداخت است. این اشیاء شامل ویژگی‌های زیر هستند:

- `supportedMethods`
  - : یک شناسه‌ی روش پرداخت. اعضای این شیء فقط در صورتی روی پرداخت اعمال می‌شوند که کاربر این روش پرداخت را انتخاب کند.
- `total`
  - : یک شیء `PaymentItem` شامل ویژگی‌های زیر:
    - `label`
      - : رشته‌ای شامل توضیح قابل‌خواندن برای انسان درباره‌ی این مورد که ممکن است به کاربر نمایش داده شود.
    - `amount`
      - : یک شیء `PaymentCurrencyAmount` (رجوع کنید به [`total` > Value](/en-US/docs/Web/API/PaymentRequestEvent/total#value)).
    - `pending`
      - : یک مقدار بولی. وقتی `true` باشد یعنی عضو `amount` نهایی نیست. این مورد معمولاً برای نمایش اقلامی مانند هزینه‌ی حمل‌ونقل یا مالیات استفاده می‌شود که به انتخاب آدرس حمل یا گزینه‌ی حمل بستگی دارند.
- `additionalDisplayItems`
  - : آرایه‌ای از اشیاء `PaymentItem` که اقلام نمایشی اضافی را برای درج در جزئیات پرداخت فراهم می‌کنند. این عضو معمولاً برای افزودن یک ردیف تخفیف یا هزینه‌ی اضافه استفاده می‌شود که دلیل مبلغ کل متفاوت برای روش پرداخت انتخاب‌شده را نشان می‌دهد و عامل کاربر (user agent) ممکن است آن را نمایش دهد.
- `data`
  - : شیءئی که اطلاعات اختیاری موردنیاز روش‌های پرداخت پشتیبانی‌شده را فراهم می‌کند. اگر ارائه شود، به‌صورت JSON سریال‌سازی خواهد شد.

## مثال‌ها

```js
self.addEventListener("paymentrequest", (e) => {
  console.log(e.modifiers);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [مروری بر برنامه‌های پرداخت مبتنی بر وب](https://web.dev/articles/web-based-payment-apps-overview)
- [راه‌اندازی یک روش پرداخت](https://web.dev/articles/setting-up-a-payment-method)
- [مراحل یک تراکنش پرداخت](https://web.dev/articles/life-of-a-payment-transaction)
- [استفاده از Payment Request API](/en-US/docs/Web/API/Payment_Request_API/Using_the_Payment_Request_API)
- [مفاهیم پردازش پرداخت](/en-US/docs/Web/API/Payment_Request_API/Concepts)