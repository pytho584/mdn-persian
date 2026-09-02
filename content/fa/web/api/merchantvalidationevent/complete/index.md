---
title: "MerchantValidationEvent: complete() method"
short-title: complete()
slug: Web/API/MerchantValidationEvent/complete
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.MerchantValidationEvent.complete
---

{{APIRef("Payment Request API")}}{{Deprecated_Header}}{{SecureContext_Header}}{{non-standard_header}}

متد **`complete()`** از {{domxref("MerchantValidationEvent")}} اطلاعات مخصوص فروشنده را که قبلاً از {{domxref("MerchantValidationEvent.validationURL", "validationURL")}} دریافت شده است، می‌گیرد و از آن برای تأیید اعتبار فروشنده استفاده می‌کند.

تنها کاری که باید انجام دهید این است که از کنترل‌کننده رویداد {{domxref("PaymentRequest.merchantvalidation_event", "merchantvalidation")}} خود، تابع `complete()` را با داده‌هایی که از `validationURL` دریافت کرده‌اید فراخوانی کنید.

## Syntax

```js-nolint
complete(validationData)
complete(merchantSessionPromise)
```

### Parameters

- `validationData` یا `merchantSessionPromise`
  - : یک شیء حاوی داده‌های لازم برای تکمیل فرآیند تأیید اعتبار فروشنده، یا یک {{jsxref("Promise")}} که به داده‌های تأیید اعتبار resolve می‌شود.

### Return value

هیچ‌کدام ({{jsxref("undefined")}}).

### Exceptions

این استثنا ممکن است به کنترل‌کننده rejection پرامیس ارسال شود:

- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر رویداد مستقیماً از عامل کاربر (user agent) نیامده باشد، بلکه توسط کد دیگری ارسال شده باشد، بازگردانده می‌شود. همچنین اگر در حال حاضر درخواست پرداخت دیگری در حال پردازش باشد، درخواست پرداخت فعلی به کاربر نمایش داده نشود، یا اطلاعات پرداخت در حال به‌روزرسانی باشد.

## Examples

در این مثال، کد سمت کلاینت مورد نیاز برای پشتیبانی از تأیید اعتبار فروشنده برای یک درخواست پرداخت به نام `payRequest` را مشاهده می‌کنیم:

```js
payRequest.onmerchantvalidation = (event) => {
  const validationDataPromise = getValidationData(event.validationURL);
  event.complete(validationDataPromise);
};

function getValidationData(url) {
  // Retrieve the validation data from the URL
  // …
}
```

این کد یک کنترل‌کننده برای رویداد {{domxref("PaymentRequest.merchantvalidation_event", "merchantvalidation")}} تنظیم می‌کند. کنترل‌کننده رویداد تابعی به نام `getValidationData()` را فراخوانی می‌کند که داده‌ها را از URL تأیید اعتبار دریافت می‌کند و سپس آن داده‌ها (یا یک پرامیس برای تحویل داده‌ها) را به `complete()` منتقل می‌کند.

## Browser compatibility

{{Compat}}

## See also

- [Payment Request API](/en-US/docs/Web/API/Payment_Request_API)
- [Using the Payment Request API](/en-US/docs/Web/API/Payment_Request_API/Using_the_Payment_Request_API)
- [Payment processing concepts](/en-US/docs/Web/API/Payment_Request_API/Concepts)