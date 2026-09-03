---
title: "PaymentResponse: shippingAddress property"
short-title: shippingAddress
slug: Web/API/PaymentResponse/shippingAddress
page-type: web-api-instance-property
browser-compat: api.PaymentResponse.shippingAddress
---

{{securecontext_header}}{{APIRef("Payment Request API")}}

ویژگی فقط‌خواندنی **`shippingAddress`** در رابط `PaymentRequest` یک شیء {{domxref('PaymentAddress')}} شامل آدرس ارسال ارائه‌شده توسط کاربر را برمی‌گرداند.

## مقدار

یک شیء {{domxref("PaymentAddress")}} که جزئیات آدرس ارسال ارائه‌شده توسط کاربر را فراهم می‌کند.

## مثال‌ها

به‌طور معمول، عامل کاربر (user agent) ویژگی `shippingAddress` را برای شما پر می‌کند. می‌توانید با تنظیم `options.requestShipping` به `true` هنگام فراخوانی سازندهٔ {{domxref('PaymentRequest.paymentRequest','PaymentRequest')}} این کار را فعال کنید.

در مثال زیر، هزینهٔ ارسال بسته به منطقهٔ جغرافیایی متفاوت است. وقتی رویداد {{domxref('PaymentRequest.shippingaddresschange_event', 'shippingaddresschange')}} رخ دهد و دریافت شود، تابع `updateDetails()` فراخوانی می‌شود تا جزئیات `PaymentRequest` را با استفاده از `shippingAddress` به‌روزرسانی کند و هزینهٔ ارسال صحیح را تنظیم نماید.

```js
// Initialization of PaymentRequest arguments are excerpted for brevity.

const payment = new PaymentRequest(supportedInstruments, details, options);

request.addEventListener("shippingaddresschange", (evt) => {
  evt.updateWith(
    new Promise((resolve) => {
      updateDetails(details, request.shippingAddress, resolve);
    }),
  );
});

payment
  .show()
  .then((paymentResponse) => {
    // Processing of paymentResponse excerpted for the same of brevity.
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

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}