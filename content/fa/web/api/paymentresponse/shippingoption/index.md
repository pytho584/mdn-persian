---
title: "PaymentResponse: shippingOption property"
short-title: shippingOption
slug: Web/API/PaymentResponse/shippingOption
page-type: web-api-instance-property
browser-compat: api.PaymentResponse.shippingOption
---

{{securecontext_header}}{{APIRef("Payment Request API")}}

ویژگی فقط‌خواندنی **`shippingOption`** از رابط `PaymentRequest`، شناسه (ID) گزینه‌ی حمل‌ونقل انتخاب‌شده توسط کاربر را برمی‌گرداند. این گزینه فقط زمانی وجود دارد که گزینه‌ی `requestShipping` در شیء `options` که به سازنده‌ی {{domxref('PaymentRequest.PaymentRequest','PaymentRequest')}} ارسال شده است، روی `true` تنظیم شده باشد.

## مقدار

یک رشته.

## مثال‌ها

در مثال زیر، رویداد {{domxref('PaymentRequest.shippingoptionchange_event', 'shippingoptionchange')}} فراخوانی می‌شود. این رویداد تابع `updateDetails()` را برای جابجایی بین روش‌های حمل‌ونقل «standard» و «express» صدا می‌زند.

```js
// مقداردهی اولیه آرگومان‌های PaymentRequest برای اختصار حذف شده است.
const payment = new PaymentRequest(supportedInstruments, details, options);

request.addEventListener("shippingoptionchange", (evt) => {
  evt.updateWith(
    new Promise((resolve, reject) => {
      updateDetails(details, request.shippingOption, resolve, reject);
    }),
  );
});

payment
  .show()
  .then((paymentResponse) => {
    // پردازش paymentResponse برای اختصار حذف شده است.
  })
  .catch((err) => {
    console.error("اوه، اتفاق بدی افتاد", err.message);
  });

function updateDetails(details, shippingOption, resolve, reject) {
  let selectedShippingOption;
  let otherShippingOption;
  if (shippingOption === "standard") {
    selectedShippingOption = details.shippingOptions[0];
    otherShippingOption = details.shippingOptions[1];
    details.total.amount.value = "55.00";
  } else if (shippingOption === "express") {
    selectedShippingOption = details.shippingOptions[1];
    otherShippingOption = details.shippingOptions[0];
    details.total.amount.value = "67.00";
  } else {
    reject(`گزینه‌ی حمل‌ونقل ناشناخته '${shippingOption}'`);
    return;
  }
  selectedShippingOption.selected = true;
  otherShippingOption.selected = false;
  details.displayItems.splice(2, 1, selectedShippingOption);
  resolve(details);
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}