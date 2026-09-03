---
title: "PaymentRequest: canMakePayment() method"
short-title: canMakePayment()
slug: Web/API/PaymentRequest/canMakePayment
page-type: web-api-instance-method
browser-compat: api.PaymentRequest.canMakePayment
---

{{securecontext_header}}{{APIRef("Payment Request API")}}

متد **`canMakePayment()`** از {{domxref("PaymentRequest")}} تعیین می‌کند که آیا درخواست به‌گونه‌ای پیکربندی شده است که با حداقل یکی از روش‌های پرداخت پشتیبانی‌شده توسط {{Glossary("user agent")}} سازگار باشد یا خیر.

می‌توانید این متد را قبل از فراخوانی {{domxref("PaymentRequest.show", "show()")}} صدا بزنید تا در زمانی که مرورگر کاربر قادر به مدیریت هیچ‌یک از روش‌های پرداخت پذیرفته‌شده شما نیست، تجربه کاربری روان‌تری ارائه دهید.

به‌عنوان مثال، می‌توانید `canMakePayment()` را فراخوانی کنید تا مشخص شود آیا مرورگر به کاربر امکان پرداخت از طریق Payment Request API را می‌دهد یا خیر؛ اگر این‌گونه نبود، می‌توانید به روش پرداخت دیگری بازگردید، یا فهرستی از روش‌هایی که توسط Payment Request API پشتیبانی نمی‌شوند ارائه دهید (یا حتی دستورالعمل‌هایی برای پرداخت از طریق پست یا تلفن ارائه کنید).

## نحو (Syntax)

```js-nolint
canMakePayment()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که به یک مقدار بولین تبدیل می‌شود و اگر user agent از هر یک از روش‌های پرداختی که هنگام نمونه‌سازی درخواست با استفاده از سازنده {{domxref('PaymentRequest.PaymentRequest()','PaymentRequest')}} ارائه شده‌اند پشتیبانی کند، به `true` resolve می‌شود. اگر پرداخت قابل پردازش نباشد، پرامیز مقدار `false` دریافت می‌کند.

> [!NOTE]
> اگر این متد را بیش از حد فراخوانی کنید، مرورگر ممکن است پرامیز بازگشتی را با یک `DOMException` رد کند.

## مثال‌ها

در مثال زیر که [برگرفته از یک دمو](https://rsolomakhin.github.io/samples/paymentrequest/can-make-payment/) است، یک شیء `PaymentRequest` به‌صورت ناهمگام برای هر دو Apple Pay و Example Pay ساخته می‌شود. فراخوانی `canMakePayment()` در تشخیص ویژگی (feature detection) قرار گرفته و بسته به نتیجه `Promise`، یک تابع بازخورد مناسب فراخوانی می‌شود.

```js
async function initPaymentRequest() {
  const details = {
    total: {
      label: "Total",
      amount: {
        currency: "USD",
        value: "0.00",
      },
    },
  };

  const supportsApplePay = new PaymentRequest(
    [{ supportedMethods: "https://apple.com/apple-pay" }],
    details,
  ).canMakePayment();

  // Supports Apple Pay?
  if (await supportsApplePay) {
    // show Apple Pay logo, for instance
    return;
  }

  // Otherwise, let's see if we can use Example Pay
  const supportsExamplePay = await new PaymentRequest(
    [{ supportedMethods: "https://example.com/pay" }],
    details,
  ).canMakePayment();

  if (supportsExamplePay) {
    // show Example Pay support
    return;
  }

  // Otherwise, make payments using HTML form element
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref('PaymentRequest.show','PaymentRequest.show()')}}