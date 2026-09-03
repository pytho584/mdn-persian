---
title: "PaymentMethodChangeEvent: methodName property"
---

---
title: "PaymentMethodChangeEvent: methodName property"
short-title: methodName
slug: Web/API/PaymentMethodChangeEvent/methodName
page-type: web-api-instance-property
browser-compat: api.PaymentMethodChangeEvent.methodName
---

{{securecontext_header}}{{APIRef("Payment Request API")}}

ویژگی فقط‌خواندنی **`methodName`** در رابط {{domxref("PaymentMethodChangeEvent")}} رشته‌ای است که پردازندهٔ پرداختی را که کاربر در حال حاضر انتخاب کرده است، به‌صورت یکتا شناسایی می‌کند. پردازندهٔ پرداخت می‌تواند یک فناوری پرداخت مانند Apple Pay یا Android Pay باشد و هر پردازندهٔ پرداخت ممکن است از چند روش پرداخت پشتیبانی کند؛ تغییرات روش پرداخت درون پردازندهٔ پرداخت توسط `PaymentMethodChangeEvent` توصیف می‌شوند.

## مقدار

یک رشته است که پردازندهٔ پرداختی را که در حال حاضر انتخاب شده است به‌صورت یکتا شناسایی می‌کند. این مقدار می‌تواند رشته‌ای انتخاب‌شده از فهرست شناسه‌های استانداردشدهٔ روش پرداخت باشد، یا یک URL که سرویس پردازش پرداخت از آن استفاده می‌کند. برای اطلاعات بیشتر، [شناسه‌های روش پرداخت](/en-US/docs/Web/API/Payment_Request_API/Concepts#payment_method_identifiers) را ببینید.

مقدار پیش‌فرض، رشتهٔ خالی `""` است.

## مثال‌ها

این مثال از رویداد {{domxref("PaymentRequest.paymentmethodchange_event", "paymentmethodchange")}} برای نظارت بر تغییرات روش پرداختی که برای Apple Pay انتخاب شده است استفاده می‌کند تا اگر کاربر کارت ویزا (Visa) را به‌عنوان روش پرداخت خود انتخاب کند، تخفیف محاسبه شود.

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

توجه داشته باشید که ویژگی `methodDetails` در تابع `calculateDiscount()` برای محاسبهٔ تخفیف پرداخت استفاده می‌شود و سپس {{domxref("PaymentRequestUpdateEvent.updateWith", "updateWith()")}} فراخوانی می‌شود تا رویداد را با به‌روزرسانیِ محاسبه‌شده به‌روزرسانی کند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}