---
title: "MerchantValidationEvent: MerchantValidationEvent() constructor"
short-title: MerchantValidationEvent()
slug: Web/API/MerchantValidationEvent/MerchantValidationEvent
page-type: web-api-constructor
status:
  - deprecated
  - non-standard
browser-compat: api.MerchantValidationEvent.MerchantValidationEvent
---

{{APIRef("Payment Request API")}}{{deprecated_header}}{{securecontext_header}}{{non-standard_header}}

سازندهٔ **`MerchantValidationEvent()`** یک شیء جدید {{domxref("MerchantValidationEvent")}} می‌سازد. معمولاً نیازی به ساخت این رویدادها به‌صورت دستی ندارید؛ در عوض، فقط رویداد {{domxref("PaymentRequest.merchantvalidation_event", "merchantvalidation")}} را مدیریت کنید.

## Syntax

```js-nolint
new MerchantValidationEvent(type)
new MerchantValidationEvent(type, options)
```

### Parameters

- `type`
  - : رشته‌ای شامل نام رویداد. این مقدار به بزرگی و کوچکی حروف حساس است و مرورگرها همیشه آن را روی `merchantvalidation` قرار می‌دهند.
- `options` {{optional_inline}}
  - : شیءای که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، می‌تواند ویژگی‌های زیر را داشته باشد:
    - `methodName` {{optional_inline}}
      - : رشته‌ای شامل شناسهٔ روش پرداخت برای پردازندهٔ پرداختی که در حال استفاده است. به‌طور پیش‌فرض رشته‌ای خالی است.
    - `validationURL` {{optional_inline}}
      - : نشانی اینترنتی (URL) که اطلاعات تأیید ویژهٔ پردازندهٔ پرداخت برای اعتبارسنجی فروشنده از آن دریافت می‌شود. به‌طور پیش‌فرض رشته‌ای خالی است.

### Return value

یک شیء جدید {{domxref("MerchantValidationEvent")}} که اطلاعات لازم را برای تحویل به کد سمت کلاینت فراهم می‌کند تا با فراخوانی {{domxref("MerchantValidationEvent.complete", "complete()")}} به {{Glossary("user agent")}} ارائه شود.

### Exceptions

- {{jsxref("TypeError")}}
  - : اگر رشتهٔ مشخص‌شده به‌عنوان `validationURL` نتواند به‌عنوان یک URL تجزیه شود، پرتاب می‌شود.
- {{jsxref("RangeError")}}
  - : اگر `methodName` مشخص‌شده با هیچ فروشندهٔ شناخته‌شده و پشتیبانی‌شده‌ای مطابقت نداشته باشد یا یک شناسهٔ استاندارد و خوش‌فرم روش پرداخت نباشد، پرتاب می‌شود.

## Specifications

_این ویژگی منسوخ شده است و بخشی از هیچ مشخصاتی نیست._

## Browser compatibility

{{Compat}}

## See also

- [Payment Request API](/en-US/docs/Web/API/Payment_Request_API)
- [استفاده از Payment Request API](/en-US/docs/Web/API/Payment_Request_API/Using_the_Payment_Request_API)
- [مفاهیم پردازش پرداخت](/en-US/docs/Web/API/Payment_Request_API/Concepts)