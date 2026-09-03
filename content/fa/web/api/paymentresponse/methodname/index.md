---
title: "PaymentResponse: methodName property"
short-title: methodName
slug: Web/API/PaymentResponse/methodName
page-type: web-api-instance-property
browser-compat: api.PaymentResponse.methodName
---

{{securecontext_header}}{{APIRef("Payment Request API")}}

ویژگی فقط‌خواندنی **`methodName`** از رابط {{domxref("PaymentResponse")}}، رشته‌ای را برمی‌گرداند که پردازشگر پرداختی را که کاربر انتخاب کرده است، به‌طور یکتا شناسایی می‌کند.

این رشته می‌تواند یکی از شناسه‌های استاندارد روش پرداخت باشد یا یک URL که پردازشگر پرداخت برای پردازش مبلغ‌ها از آن استفاده می‌کند.

## مقدار

رشته‌ای که پردازشگر پرداختی را که برای پردازش مبلغ استفاده می‌شود، به‌طور یکتا شناسایی می‌کند. این مقدار می‌تواند یک شناسه استاندارد یا یک URL باشد که پردازشگر پرداخت برای مدیریت مبلغ‌ها از آن استفاده می‌کند. نحوه عملکرد [تأیید فروشنده](/en-US/docs/Web/API/Payment_Request_API/Concepts#merchant_validation) را ببینید.

## مثال‌ها

مثال زیر نام روش پرداخت را از شیء {{domxref('PaymentResponse')}} به پرامیسی که از {{domxref('PaymentRequest.show()')}} برگردانده می‌شود استخراج می‌کند. در یک پیاده‌سازی واقعی، این داده‌ها سپس به سرور پرداخت ارسال می‌شوند.

```js
payment.show().then((paymentResponse) => {
  const paymentData = {
    // رشته روش پرداخت
    method: paymentResponse.methodName,
    // جزئیات پرداخت همان‌طور که درخواست کرده‌اید
    details: paymentResponse.details,
    // اطلاعات آدرس حمل‌ونقل
    address: toDict(paymentResponse.shippingAddress),
  };
  // ارسال اطلاعات به سرور
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
