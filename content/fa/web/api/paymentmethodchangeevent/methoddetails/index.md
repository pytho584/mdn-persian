---
title: "PaymentMethodChangeEvent: methodDetails property"
short-title: methodDetails
slug: Web/API/PaymentMethodChangeEvent/methodDetails
page-type: web-api-instance-property
browser-compat: api.PaymentMethodChangeEvent.methodDetails
---

{{securecontext_header}}{{APIRef("Payment Request API")}}

خاصیت فقط خواندنی **`methodDetails`** از رابط {{domxref("PaymentMethodChangeEvent")}} یک شیء است که شامل هر داده‌ای است که پردازشگر پرداخت ممکن است برای توصیف تغییری که کاربر در روش پرداخت خود ایجاد کرده است، ارائه دهد. اگر جزئیاتی در دسترس نباشد، مقدار `null` است.

## مقدار

یک شیء شامل هر داده‌ای که برای توصیف تغییرات ایجاد شده در روش پرداخت لازم است. محتوا بسته به روش پرداخت واقعی انتخاب شده متفاوت است، بنابراین ابتدا باید به خاصیت {{domxref("PaymentMethodChangeEvent.methodName", "methodName")}} مراجعه کنید و سپس `methodDetails` را تفسیر کنید.

مقدار پیش‌فرض `null` است، که نشان می‌دهد هیچ جزئیات اضافی در دسترس نیست.

## مثال‌ها

این مثال از رویداد {{domxref("PaymentRequest.paymentmethodchange_event", "paymentmethodchange")}} برای نظارت بر تغییرات روش پرداخت انتخاب شده برای Apple Pay استفاده می‌کند تا در صورت انتخاب کارت ویزا به عنوان روش پرداخت، تخفیف محاسبه شود.

```js
request.onpaymentmethodchange = (ev) => {
  const { type: cardType } = ev.methodDetails;
  const newStuff = {};
  if (ev.methodName === "https://apple.com/apple-pay") {
    switch (cardType) {
      case "visa": {
        // do Apple Pay specific handling for Visa card…
        // methodDetails contains the card information
        const discount = calculateDiscount(ev.methodDetails);
        Object.assign(newStuff, discount);
        break;
      }
    }
  }
  // finally…
  ev.updateWith(newStuff);
};
const response = await request.show();
```

توجه کنید که خاصیت `methodDetails` توسط تابع `calculateDiscount()` برای محاسبه هرگونه تخفیف پرداخت استفاده می‌شود، سپس {{domxref("PaymentRequestUpdateEvent.updateWith", "updateWith()")}} فراخوانی می‌شود تا رویداد را با به‌روزرسانی محاسبه‌شده به‌روز کند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}