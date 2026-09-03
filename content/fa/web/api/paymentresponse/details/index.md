---
title: "PaymentResponse: details property"
short-title: details
slug: Web/API/PaymentResponse/details
page-type: web-api-instance-property
browser-compat: api.PaymentResponse.details
---

{{securecontext_header}}{{APIRef("Payment Request API")}}

ویژگی فقط خواندنی **`details`** از رابط {{domxref("PaymentResponse")}} یک شیء قابل سریال‌سازی به JSON برمی‌گرداند که یک پیام مختص روش پرداخت را ارائه می‌دهد که توسط فروشنده برای پردازش تراکنش و تعیین موفقیت انتقال وجه استفاده می‌شود.

## مقدار

یک شیء. این داده‌ها توسط برنامه پرداختی که درخواست پرداخت را برآورده می‌کند، بازگردانده می‌شوند. توسعه‌دهندگان باید با شخص یا نهادی که URL را کنترل می‌کند، برای شکل مورد انتظار شیء `details` مشورت کنند.

## مثال‌ها

مثال زیر جزئیات را از شیء {{domxref('PaymentResponse')}} به قولی که از {{domxref('PaymentRequest.show()')}} برگردانده شده است، استخراج می‌کند. در یک پیاده‌سازی واقعی، این داده‌ها سپس به سرور پرداخت ارسال می‌شوند.

```js
payment.show().then((paymentResponse) => {
  const paymentData = {
    // payment method string
    method: paymentResponse.methodName,
    // payment details as you requested
    details: paymentResponse.details,
    // shipping address information
    address: toDict(paymentResponse.shippingAddress),
  };
  // Send information to the server
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}