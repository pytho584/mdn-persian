---
title: "PaymentRequest: merchantvalidation event"
short-title: merchantvalidation
slug: Web/API/PaymentRequest/merchantvalidation_event
page-type: web-api-event
status:
  - deprecated
  - non-standard
browser-compat: api.PaymentRequest.merchantvalidation_event
---

{{APIRef("Payment Request API")}}{{SecureContext_Header}}{{Deprecated_Header}}{{non-standard_header}}

رویدادهای **`merchantvalidation`** توسط [Payment Request API](/en-US/docs/Web/API/Payment_Request_API) به یک شیء {{domxref("PaymentRequest")}} تحویل داده می‌شوند، زمانی که یک پردازشگر پرداخت نیاز دارد که فروشنده‌ای که درخواست خرید را داده است، خود را به عنوان مجاز برای استفاده از آن پردازشگر پرداخت اعتبارسنجی کند.

با نحوه عملکرد فرآیند [merchant validation](/en-US/docs/Web/API/Payment_Request_API/Concepts#merchant_validation) آشنا شوید.

این رویداد قابل لغو نیست و bubble نمی‌کند.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک خاصیت event handler تنظیم کنید.

```js-nolint
addEventListener("merchantvalidation", (event) => { })

onmerchantvalidation = (event) => { }
```

## نوع رویداد

یک {{domxref("MerchantValidationEvent")}}. از {{domxref("Event")}} ارث‌بری می‌کند.

{{InheritanceDiagram("MerchantValidationEvent")}}

## مثال‌ها

در این مثال، یک event handler برای رویداد `merchantvalidation` تنظیم شده است. این handler از {{domxref("Window/fetch", "fetch()")}} برای ارسال درخواست به سرور خود با یک آرگومان از URL اعتبارسنجی روش پرداخت استفاده می‌کند که از خاصیت {{domxref("MerchantValidationEvent.validationURL", "validationURL")}} رویداد به دست آمده است. سرور فروشنده باید بر اساس مستندات روش پرداخت به URL اعتبارسنجی دسترسی پیدا کند. معمولاً یک کلاینت نباید به URL اعتبارسنجی دسترسی داشته باشد.

```js
request.addEventListener("merchantvalidation", (event) => {
  event.complete(async () => {
    const merchantServerUrl = `${
      window.location.origin
    }/validate?url=${encodeURIComponent(event.validationURL)}`;
    // دریافت داده‌های اعتبارسنجی و تکمیل اعتبارسنجی
    return await fetch(merchantServerUrl).then((response) => response.text());
  }, false);
});

const response = await request.show();
```

نحوه مدیریت اعتبارسنجی توسط سرور فروشنده به پیاده‌سازی سرور و مستندات روش پرداخت بستگی دارد. محتوای تحویل داده شده توسط سرور اعتبارسنجی به سرور فروشنده ارسال می‌شود و سپس از handler fulfillment فراخوانی `fetch()` به متد {{domxref("MerchantValidationEvent.complete", "complete()")}} روی رویداد بازگردانده می‌شود. این پاسخ به پردازشگر پرداخت اطلاع می‌دهد که آیا فروشنده اعتبارسنجی شده است یا خیر.

همچنین می‌توانید از خاصیت event handler `onmerchantvalidation` برای تنظیم handler این رویداد استفاده کنید:

```js
request.onmerchantvalidation = (event) => {
  event.complete(async () => {
    const merchantServerUrl = `${
      window.location.origin
    }/validate?url=${encodeURIComponent(event.validationURL)}`;
    // دریافت داده‌های اعتبارسنجی و تکمیل اعتبارسنجی
    return await fetch(merchantServerUrl).then((response) => response.text());
  });
};

const response = await request.show();
```

برای اطلاعات بیشتر، به [Merchant validation](/en-US/docs/Web/API/Payment_Request_API/Concepts#merchant_validation) مراجعه کنید.

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [Payment Request API](/en-US/docs/Web/API/Payment_Request_API)
- [Using the Payment Request API](/en-US/docs/Web/API/Payment_Request_API/Using_the_Payment_Request_API)
- خاصیت event handler `onmerchantvalidation`
- [Merchant validation](/en-US/docs/Web/API/Payment_Request_API/Concepts#merchant_validation)
- رویداد {{domxref("PaymentRequest.paymentmethodchange_event", "paymentmethodchange")}}
- رویداد {{domxref("PaymentRequest.shippingaddresschange_event", "shippingaddresschange")}}
- رویداد {{domxref("PaymentRequest.shippingoptionchange_event", "shippingoptionchange")}}