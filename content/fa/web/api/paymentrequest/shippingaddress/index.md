---
title: "PaymentRequest: shippingAddress property"
short-title: shippingAddress
slug: Web/API/PaymentRequest/shippingAddress
page-type: web-api-instance-property
status:
  - deprecated
  - non-standard
browser-compat: api.PaymentRequest.shippingAddress
---

{{securecontext_header}}{{APIRef("Payment Request API")}}{{Deprecated_header}}{{Non-standard_header}}

ویژگی فقط‌خواندنی **`shippingAddress`** در رابط {{domxref('PaymentRequest')}}، آدرس حمل‌ونقل ارائه‌شده توسط کاربر را بازمی‌گرداند. مقدار پیش‌فرض آن `null` است.

## مقدار

یک شیء {{domxref('PaymentAddress')}} یا `null`.

## مثال‌ها

به‌طور معمول، عامل کاربر (user agent) مقدار ویژگی `shippingAddress` را پر می‌کند. می‌توانید با قرار دادن `options.requestShipping` روی `true` هنگام فراخوانی سازندهٔ `PaymentRequest`، این کار را فعال کنید.

در مثال زیر، هزینهٔ حمل‌ونقل بسته به منطقهٔ جغرافیایی متفاوت است. وقتی رویداد {{domxref('PaymentRequest.shippingaddresschange_event', 'shippingaddresschange')}} صدا زده می‌شود، تابع `updateDetails()` برای به‌روزرسانی جزئیات `PaymentRequest` فراخوانی می‌شود و از `shippingAddress` برای تنظیم هزینهٔ صحیح حمل‌ونقل استفاده می‌کند.

```js
// Initialization of PaymentRequest arguments are excerpted for the sake of
//   brevity.
const payment = new PaymentRequest(supportedInstruments, details, options);

payment.addEventListener("shippingaddresschange", (evt) => {
  evt.updateWith(
    new Promise((resolve) => {
      updateDetails(details, request.shippingAddress, resolve);
    }),
  );
});

payment
  .show()
  .then((paymentResponse) => {
    // Processing of paymentResponse excerpted for brevity.
  })
  .catch((err) => {
    console.error("Uh oh, something bad happened", err.message);
  });

function updateDetails(details, shippingAddress, resolve) {
  if (shippingAddress.country === "US") {
    const shippingOption = {
      id: "",
      label: "",
      amount: { currency: "USD", value: "0.00" },
      selected: true,
    };
    if (shippingAddress.region === "MO") {
      shippingOption.id = "mo";
      shippingOption.label = "Free shipping in Missouri";
      details.total.amount.value = "55.00";
    } else {
      shippingOption.id = "us";
      shippingOption.label = "Standard shipping in US";
      shippingOption.amount.value = "5.00";
      details.total.amount.value = "60.00";
    }
    details.displayItems.splice(2, 1, shippingOption);
    details.shippingOptions = [shippingOption];
  } else {
    delete details.shippingOptions;
  }
  resolve(details);
}
```

## سازگاری مرورگر

{{Compat}}