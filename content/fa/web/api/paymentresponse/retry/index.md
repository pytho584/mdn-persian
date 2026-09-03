---
title: "PaymentResponse: retry() method"
short-title: retry()
slug: Web/API/PaymentResponse/retry
page-type: web-api-instance-method
browser-compat: api.PaymentResponse.retry
---

{{securecontext_header}}{{APIRef("Payment Request API")}}

در رابط {{domxref("PaymentResponse")}}، متد **`retry()`** این امکان را فراهم می‌کند که پس از بروز خطا در هنگام پردازش، از کاربر بخواهید پرداخت را دوباره انجام دهد.

این کار به برنامه شما اجازه می‌دهد تا موقعیت‌هایی مانند آدرس حمل‌ونقل نامعتبر یا کارت اعتباری ردشده را به‌شکلی مناسب مدیریت کند.

## Syntax

```js-nolint
retry(errorFields)
```

### Parameters

- `errorFields`
  - : یک شیء با ویژگی‌های زیر:
    - `error` {{optional_inline}}
      - : توضیحی کلی درباره خطای پرداخت که کاربر ممکن است با تلاش مجدد برای پرداخت بتواند آن را برطرف کند، احتمالاً پس از اصلاح اشتباهات در اطلاعات پرداخت. می‌توان `error` را به تنهایی برای ارائه یک پیام خطای عمومی ارائه کرد، یا همراه با سایر ویژگی‌ها به‌عنوان نمای کلی استفاده کرد در حالی که مقادیر سایر ویژگی‌ها کاربر را به خطاهای موجود در فیلدهای خاص فرم پرداخت راهنمایی می‌کند.
    - `paymentMethod` {{optional_inline}}
      - : هرگونه خطای مختص روش پرداخت که ممکن است رخ داده باشد. محتوای این شیء بسته به روش پرداخت استفاده‌شده متفاوت خواهد بود.

### Return value

یک {{jsxref("Promise")}} که وقتی پرداخت با موفقیت انجام شود، resolve می‌شود. اگر پرداخت دوباره ناموفق باشد، این وعده (promise) با یک مقدار استثنای مناسب reject می‌شود.

معمولاً از این متد به این صورت استفاده می‌کنید که ابتدا {{domxref("PaymentRequest.show", "show()")}} را فراخوانی می‌کنید و سپس یک حلقه یا تابع بازگشتی می‌سازید که {{domxref("PaymentResponse")}} را از نظر خطا یا دلایل دیگر برای تلاش مجدد درخواست پرداخت بررسی می‌کند. اگر نیاز به تلاش مجدد باشد، حلقه `retry()` را صدا می‌زند و سپس برای بررسی پاسخ وقتی که برسد، به ابتدای حلقه بازمی‌گردد. حلقه تنها زمانی خارج می‌شود که کاربر درخواست پرداخت را لغو کند یا درخواست با موفقیت انجام شود.

برای مشاهده یک مثال کامل، بخش [example](#examples) را ببینید، اما مفهوم اصلی به‌صورت خلاصه به این شکل است:

1. یک {{domxref("PaymentRequest")}} جدید بسازید
   (`new` {{domxref("PaymentRequest.PaymentRequest", "PaymentRequest()")}})
2. درخواست پرداخت را نمایش دهید ({{domxref("PaymentRequest.show()")}})
3. اگر `show()` با موفقیت resolve شود، {{domxref("PaymentResponse")}} برگشتی، پرداخت درخواستی و گزینه‌های انتخاب‌شده توسط کاربر را توصیف می‌کند. مراحل زیر را ادامه دهید:
   1. پاسخ برگشتی را اعتبارسنجی کنید؛ اگر هر فیلدی مقدار نامطلوبی داشت، متد {{domxref("PaymentResponse.complete", "complete()")}} پاسخ را با مقدار `"fail"` فراخوانی کنید تا شکست را نشان دهد.
   2. اگر داده‌های پاسخ معتبر و قابل قبول هستند،
      `complete("success")` را فراخوانی کنید تا پرداخت نهایی شود و پردازش انجام شود.

4. اگر `show()` reject شود، درخواست پرداخت ناموفق بوده است، معمولاً به این دلیل که یک درخواست پرداخت در حال پردازش وجود دارد، یا {{Glossary("user agent")}} از هیچ‌کدام از روش‌های پرداخت مشخص‌شده پشتیبانی نمی‌کند، یا به دلیل یک مشکل امنیتی.
   برای جزئیات بیشتر به [فهرست استثناها](/en-US/docs/Web/API/PaymentRequest/show#exceptions) برای `show()` مراجعه کنید.
   `complete("fail")` را فراخوانی کنید تا درخواست پرداخت بسته شود.

```js
async function handlePayment() {
  const payRequest = new PaymentRequest(methodData, details, options);

  try {
    let payResponse = await payRequest.show();

    while (validate(payResponse)) {
      /* let the user edit the payment information,
         wait until they submit */
      await response.retry();
    }
    await payResponse.complete("success");
  } catch (err) {
    /* handle the exception */
  }
}
```

## Examples

```js
async function doPaymentRequest() {
  const request = new PaymentRequest(methodData, details, options);
  const response = await request.show();
  await recursiveValidate(request, response);
  await response.complete("success");
}

// Keep validating until the data looks good!
async function recursiveValidate(request, response) {
  const promisesToFixThings = [];
  const errors = await validate(request, response);
  if (!errors) {
    return;
  }
  if (errors.shippingAddress) {
    // "shippingaddresschange" fired at request object
    const promise = fixField(
      request,
      "shippingaddresschange",
      shippingValidator,
    );
    promisesToFixThings.push(promise);
  }
  if (errors.payer) {
    // "payerdetailchange" fired at response object
    const promise = fixField(response, "payerdetailchange", payerValidator);
    promisesToFixThings.push(promise);
  }
  await Promise.all([response.retry(errors), ...promisesToFixThings]);
  await recursiveValidate(request, response);
}

function fixField(requestOrResponse, event, validator) {
  return new Promise((resolve) => {
    // Browser keeps calling this until promise resolves.
    requestOrResponse.addEventListener(event, async function listener(ev) {
      const promiseToValidate = validator(requestOrResponse);
      ev.updateWith(promiseToValidate);
      const errors = await promiseToValidate;
      if (!errors) {
        // yay! fixed!
        event.removeEventListener(event, listener);
        resolve();
      }
    });
  });
}

doPaymentRequest();
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("PaymentResponse")}} interface.