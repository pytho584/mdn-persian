---
title: "PaymentManager: enableDelegations() method"
---

---
title: "PaymentManager: enableDelegations() method"
short-title: enableDelegations()
slug: Web/API/PaymentManager/enableDelegations
page-type: web-api-instance-method
status:
  - experimental
browser-compat: api.PaymentManager.enableDelegations
---

{{APIRef("Web-Based Payment Handler API")}}{{SeeCompatTable}}{{SecureContext_Header}}

متد **`enableDelegations()`** از رابط {{domxref("PaymentManager")}} مسئولیت ارائه بخش‌های مختلف اطلاعات پرداخت مورد نیاز را به اپلیکیشن پرداخت واگذار می‌کند، به جای اینکه آن را از مرورگر (مثلاً از طریق تکمیل خودکار) جمع‌آوری کند.

به عنوان مثال، اگر گزینه `requestShipping` در شیء options هنگام فراخوانی سازنده {{domxref("PaymentRequest.PaymentRequest", "PaymentRequest()")}} روی `true` تنظیم شده باشد، یک آدرس حمل و نقل بازگردانده می‌شود.

- اگر `enableDelegations()` برای واگذاری `shippingAddress` استفاده شده باشد، آن آدرس از اپلیکیشن پرداخت می‌آید.
- در غیر این صورت، از تکمیل خودکار مرورگر می‌آید.

## Syntax

```js-nolint
enableDelegations(delegations)
```

### Parameters

- `delegations` {{optional_inline}}
  - : آرایه‌ای شامل یک یا چند مقدار شمارشی که اطلاعات پرداختی را که می‌خواهید به اپلیکیشن پرداخت واگذار کنید، مشخص می‌کند. مقادیر ممکن عبارتند از:
    - `payerEmail`
      - : اپلیکیشن پرداخت ایمیل پرداخت‌کننده را هر زمان که نیاز باشد، ارائه می‌دهد.
    - `payerName`
      - : اپلیکیشن پرداخت نام پرداخت‌کننده را هر زمان که نیاز باشد، ارائه می‌دهد.
    - `payerPhone`
      - : اپلیکیشن پرداخت شماره تلفن پرداخت‌کننده را هر زمان که نیاز باشد، ارائه می‌دهد.
    - `shippingAddress`
      - : اپلیکیشن پرداخت آدرس حمل و نقل را هر زمان که نیاز باشد، ارائه می‌دهد.

### Return value

یک {{jsxref("Promise")}} که با مقدار `undefined` حل می‌شود.

## Examples

```js
navigator.serviceWorker.register("serviceworker.js").then((registration) => {
  registration.paymentManager.userHint = "Card number should be 16 digits";

  registration.paymentManager
    .enableDelegations(["shippingAddress", "payerName"])
    .then(() => {
      // …
    });

  // …
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("Web-based Payment Handler API", "", "", "nocode")}}
- [Web-based payment apps overview](https://web.dev/articles/web-based-payment-apps-overview)
- [Setting up a payment method](https://web.dev/articles/setting-up-a-payment-method)
- [Life of a payment transaction](https://web.dev/articles/life-of-a-payment-transaction)
- [Using the Payment Request API](/en-US/docs/Web/API/Payment_Request_API/Using_the_Payment_Request_API)
- [Payment processing concepts](/en-US/docs/Web/API/Payment_Request_API/Concepts)