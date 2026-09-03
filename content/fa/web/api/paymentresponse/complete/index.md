---
title: "PaymentResponse: complete() method"
short-title: complete()
slug: Web/API/PaymentResponse/complete
page-type: web-api-instance-method
browser-compat: api.PaymentResponse.complete
---

{{securecontext_header}}{{APIRef("Payment Request API")}}

متد **`complete()`** از {{domxref("PaymentRequest")}} در [Payment Request API](/en-US/docs/Web/API/Payment_Request_API) به {{Glossary("user agent")}} اطلاع می‌دهد که تعامل کاربر به پایان رسیده است و باعث می‌شود هر رابط کاربری باقی‌مانده بسته شود.

این متد باید پس از پذیرش درخواست پرداخت توسط کاربر و پس از resolve شدن {{jsxref("Promise")}} برگشتی از متد {{domxref('PaymentRequest.show()')}} فراخوانی شود.

## نحو

```js-nolint
complete()
complete(result)
```

### پارامترها

- `result` {{optional_inline}}
  - : رشته‌ای که وضعیت عملیات پرداخت را در زمان اتمام نشان می‌دهد. باید یکی از مقادیر زیر باشد:
    - `success`
      - : پرداخت با موفقیت پردازش شد. user agent ممکن است نوعی نشانه «پرداخت موفق» را به کاربر نمایش دهد یا ندهد.
    - `fail`
      - : پرداخت با موفقیت پردازش نشد. بسته به طراحی user agent، ممکن است شکست به کاربر اعلام شود یا نشود.
    - `unknown`
      - : وضعیت موفقیت یا شکست تراکنش ناشناخته یا نامربوط است و user agent نباید هیچ اعلانی نمایش دهد، حتی اگر به طور معمول نمایش دهد. _این مقدار پیش‌فرض است._

    > [!NOTE]
    > در نسخه‌های قدیمی‌تر مشخصات، رشته خالی `""` به جای `unknown` برای نشان دادن اتمام بدون وضعیت نتیجه مشخص استفاده می‌شد. برای جزئیات به بخش [سازگاری مرورگر](#browser_compatibility) در زیر مراجعه کنید.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که پس از بسته شدن کامل رابط پرداخت، بدون هیچ مقداری resolve می‌شود. اگر خطایی رخ دهد، promise به جای آن reject می‌شود و یکی از استثناهای ذکرشده در زیر را برمی‌گرداند.

### استثناها

- `AbortError` {{domxref("DOMException")}}
  - : اگر سندی که درخواست پرداخت در آن انجام می‌شود در حین نمایش رابط کاربری غیرفعال شده باشد، برگردانده می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر پرداخت قبلاً کامل شده باشد، یا اگر `complete()` در حالی فراخوانی شود که درخواست تلاش مجدد برای پرداخت در انتظار است، برگردانده می‌شود. نمی‌توانید پس از درخواست تلاش مجدد برای پرداخت، آن را به عنوان کامل در نظر بگیرید.

## مثال‌ها

مثال زیر اطلاعات پرداخت را با استفاده از [Fetch API](/en-US/docs/Web/API/Fetch_API) به یک سرور امن ارسال می‌کند. این مثال `complete()` را با پاسخی متناسب با وضعیت پاسخ فراخوانی می‌کند.

```js
// Initialization of PaymentRequest arguments are excerpted for the
//   sake of brevity.
const payment = new PaymentRequest(supportedInstruments, details, options);

payment
  .show()
  .then((paymentResponse) => {
    const fetchOptions = {
      method: "POST",
      credentials: include,
      body: JSON.stringify(paymentResponse),
    };
    const serverPaymentRequest = new Request("secure/payment/endpoint");
    fetch(serverPaymentRequest, fetchOptions)
      .then((response) => {
        if (response.status < 400) {
          paymentResponse.complete("success");
        } else {
          paymentResponse.complete("fail");
        }
      })
      .catch((reason) => {
        paymentResponse.complete("fail");
      });
  })
  .catch((err) => {
    console.error("Uh oh, something bad happened", err.message);
  });
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}