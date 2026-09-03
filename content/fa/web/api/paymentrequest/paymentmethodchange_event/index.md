---
title: "PaymentRequest: paymentmethodchange event"
short-title: paymentmethodchange
slug: Web/API/PaymentRequest/paymentmethodchange_event
page-type: web-api-event
browser-compat: api.PaymentRequest.paymentmethodchange_event
---

{{securecontext_header}}{{APIRef("Payment Request API")}}

رویداد **`paymentmethodchange`** توسط [Payment Request API](/en-US/docs/Web/API/Payment_Request_API) به یک شیء {{domxref("PaymentRequest")}} تحویل داده می‌شود هنگامی که کاربر روش پرداخت را درون یک پردازشگر پرداخت مشخص تغییر می‌دهد.

برای مثال، اگر کاربر در حساب [Apple Pay](https://www.apple.com/apple-pay/) خود از یک کارت اعتباری به کارت دیگری تغییر وضعیت دهد، یک رویداد `paymentmethodchange` برای اطلاع‌رسانی درباره‌ی این تغییر فعال می‌شود.

این رویداد قابل لغو (cancelable) نیست و منتشر (bubble) نمی‌شود.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی event handler تنظیم کنید.

```js-nolint
addEventListener("paymentmethodchange", (event) => { })

onpaymentmethodchange = (event) => { }
```

## نوع رویداد

یک {{domxref("PaymentMethodChangeEvent")}} که از {{domxref("Event")}} ارث‌بری می‌کند.

{{InheritanceDiagram("PaymentMethodChangeEvent")}}

## مثال‌ها

بیایید یک مثال را بررسی کنیم. این کد یک {{domxref("PaymentRequest")}} جدید ایجاد می‌کند، یک handler برای رویداد `paymentmethodchange` با فراخوانی {{domxref("EventTarget.addEventListener", "addEventListener()")}} درخواست اضافه می‌کند، و سپس {{domxref("PaymentRequest.show", "show()")}} را فراخوانی می‌کند تا رابط پرداخت را به کاربر نمایش دهد.

این کد وجود یک متد به نام `detailsForTransaction()` را فرض می‌گیرد که شیئی را برمی‌گرداند که می‌تواند به عنوان آرگومان [`details`](/en-US/docs/Web/API/PaymentRequest/PaymentRequest#details) به سازنده‌ی `PaymentRequest` ارسال شود.

```js
const paymentRequest = new PaymentRequest(
  paymentMethods,
  detailsForTransaction(),
);

paymentRequest.addEventListener("paymentmethodchange", handlePaymentChange);

paymentRequest
  .show()
  .then((response) => response.complete("success"))
  .catch((err) => console.error(`Error handling payment request: ${err}`));
```

خود تابع handler رویداد، یعنی `handlePaymentChange()`، به این صورت است:

```js
handlePaymentChange = (event) => {
  const detailsUpdate = {};

  if (event.methodName === "https://apple.com/apple-pay") {
    const serviceFeeInfo = calculateServiceFee(event.methodDetails);
    Object.assign(detailsUpdate, serviceFeeInfo);
  }

  event.updateWith(detailsUpdate);
};
```

این کد با بررسی ویژگی {{domxref("PaymentMethodChangeEvent.methodName", "methodName")}} رویداد شروع می‌شود. اگر این ویژگی نشان دهد که کاربر در حال استفاده از Apple Pay است، {{domxref("PaymentMethodChangeEvent.methodDetails", "methodDetails")}} را به تابعی به نام `calculateServiceFee()` ارسال می‌کنیم. این تابع (که می‌توانیم ایجاد کنیم) اطلاعات مربوط به تراکنش، مانند کارت اعتباری زیربنایی که برای سرویس‌دهی به درخواست Apple Pay استفاده می‌شود، را دریافت می‌کند و شیئی را محاسبه و برمی‌گرداند که تغییرات مورد نیاز برای اعمال به {{domxref("PaymentRequest")}} را مشخص می‌کند تا هرگونه هزینه سرویس که روش پرداخت ممکن است نیاز داشته باشد، اضافه شود.

پیش از بازگشت handler رویداد، متد {{domxref("PaymentRequestUpdateEvent.updateWith()", "updateWith()")}} رویداد را فراخوانی می‌کند تا تغییرات را در درخواست ادغام کند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Payment Request API](/en-US/docs/Web/API/Payment_Request_API)
- [استفاده از Payment Request API](/en-US/docs/Web/API/Payment_Request_API/Using_the_Payment_Request_API)
- رویداد {{domxref("PaymentRequest.merchantvalidation_event", "merchantvalidation")}}
- رویداد {{domxref("PaymentRequest.shippingaddresschange_event", "shippingaddresschange")}}
- رویداد {{domxref("PaymentRequest.shippingoptionchange_event", "shippingoptionchange")}}