---
title: "PaymentResponse: payerdetailchange event"
short-title: payerdetailchange
slug: Web/API/PaymentResponse/payerdetailchange_event
page-type: web-api-event
browser-compat: api.PaymentResponse.payerdetailchange_event
---

{{APIRef("Payment Request API")}}{{SecureContext_Header}}

رویداد **`payerdetailchange`** توسط [Payment Request API](/en-US/docs/Web/API/Payment_Request_API) به یک شیء {{domxref("PaymentResponse")}} زمانی که کاربر اطلاعات شخصی خود را در هنگام پر کردن فرم درخواست پرداخت تغییر می‌دهد، فرستاده می‌شود. این اتفاق می‌تواند زمانی رخ دهد که پرداخت‌کننده در حال تلاش مجدد برای ارسال جزئیات خود پس از تشخیص یک خطا است.

مدیریت‌کننده رویداد برای `payerdetailchange` باید هر مقدار در فرم که تغییر کرده است را بررسی کند و اطمینان حاصل کند که مقادیر معتبر هستند. اگر هرکدام نامعتبر بود، باید پیام‌های خطای مناسب پیکربندی شود و متد {{domxref("PaymentResponse.retry", "retry()")}} روی {{domxref("PaymentResponse")}} فراخوانی شود تا از کاربر بخواهد ورودی‌های نامعتبر را تصحیح کند.

این رویداد قابل لغو نیست و bubble نمی‌کند.

## Syntax

Use the event name in methods like {{domxref("EventTarget.addEventListener", "addEventListener()")}}, or set an event handler property.

```js-nolint
addEventListener("payerdetailchange", (event) => { })

onpayerdetailchange = (event) => { }
```

## Event type

یک {{domxref("PaymentRequestUpdateEvent")}}. از {{domxref("Event")}} ارث‌بری می‌کند.

{{InheritanceDiagram("PaymentRequestUpdateEvent")}}

## Examples

در مثال زیر، `onpayerdetailchange` برای تنظیم یک شنونده برای رویداد `payerdetailchange` به منظور اعتبارسنجی اطلاعات وارد شده توسط کاربر استفاده شده است و درخواست می‌کند که هرگونه اشتباه تصحیح شود.

```js
// Options for PaymentRequest(), indicating that shipping address,
// payer email address, name, and phone number all be collected.

const options = {
  requestShipping: true,
  requestPayerEmail: true,
  requestPayerName: true,
  requestPayerPhone: true,
};
const request = new PaymentRequest(methods, details, options);
const response = request.show();

// Get the data from the response

let {
  payerName: oldPayerName,
  payerEmail: oldPayerEmail,
  payerPhone: oldPayerPhone,
} = response;

// Set up a handler for payerdetailchange events, to
// request corrections as needed.

response.onpayerdetailchange = async (ev) => {
  const promisesToValidate = [];
  const { payerName, payerEmail, payerPhone } = response;

  // Validate each value which changed by calling a function
  // that validates each type of data, returning a promise which
  // resolves if the data is valid.

  if (oldPayerName !== payerName) {
    promisesToValidate.push(validateName(payerName));
    oldPayerName = payerName;
  }
  if (oldPayerEmail !== payerEmail) {
    promisesToValidate.push(validateEmail(payerEmail));
    oldPayerEmail = payerEmail;
  }
  if (oldPayerPhone !== payerPhone) {
    promisesToValidate.push(validatePhone(payerPhone));
    oldPayerPhone = payerPhone;
  }

  // As each validation promise resolves, add the results of the
  // validation to the errors list

  const errors = await Promise.all(promisesToValidate).then((results) =>
    results.reduce((errors, result) => Object.assign(errors, result)),
  );

  // If we found any errors, wait for them to be corrected

  if (Object.getOwnPropertyNames(errors).length) {
    await response.retry(errors);
  } else {
    // We have a good payment; send the data to the server
    await fetch("/pay-for-things/", { method: "POST", body: response.json() });
    response.complete("success");
  }
};

await response.retry({
  payer: {
    email: "invalid domain.",
    phone: "invalid number.",
  },
});
```

### addEventListener equivalent

همچنین می‌توانید مدیریت‌کننده رویداد را با استفاده از متد `addEventListener()` تنظیم کنید:

```js
response.addEventListener("payerdetailchange", async (ev) => {
  // …
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Payment Request API](/en-US/docs/Web/API/Payment_Request_API)
- [Using the Payment Request API](/en-US/docs/Web/API/Payment_Request_API/Using_the_Payment_Request_API)
- {{domxref("PaymentResponse")}}
- [`paymentmethodchange`](/en-US/docs/Web/API/PaymentRequest/paymentmethodchange_event)
- [`shippingaddresschange`](/en-US/docs/Web/API/PaymentRequest/shippingaddresschange_event)
- [`shippingoptionchange`](/en-US/docs/Web/API/PaymentRequest/shippingoptionchange_event)