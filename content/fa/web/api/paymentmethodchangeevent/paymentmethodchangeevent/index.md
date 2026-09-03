---
title: "PaymentMethodChangeEvent: PaymentMethodChangeEvent() سازنده"
short-title: PaymentMethodChangeEvent()
slug: Web/API/PaymentMethodChangeEvent/PaymentMethodChangeEvent
page-type: web-api-constructor
browser-compat: api.PaymentMethodChangeEvent.PaymentMethodChangeEvent
---

{{securecontext_header}}{{APIRef("Payment Request API")}}

سازنده **`PaymentMethodChangeEvent()`** یک شیء {{domxref("PaymentMethodChangeEvent")}} جدید می‌سازد که جزئیات مربوط به رویداد {{domxref("PaymentRequest.paymentmethodchange_event", "paymentmethodchange")}} را فراهم می‌کند.

## نحو (Syntax)

```js-nolint
new PaymentMethodChangeEvent(type)
new PaymentMethodChangeEvent(type, options)
```

### پارامترها

- `type`
  - : یک رشته شامل نام رویداد. این مقدار به حروف بزرگ و کوچک حساس است و مرورگرها آن را روی `paymentmethodchange` تنظیم می‌کنند.
- `options` {{optional_inline}}
  - : یک شیء که _علاوه بر ویژگی‌های تعریف‌شده در {{domxref("Event/Event", "Event()")}}_، می‌تواند ویژگی‌های زیر را داشته باشد:
    - `methodName` {{optional_inline}}
      - : رشته‌ای شامل شناسه روش پرداخت برای پردازنده پرداختی که در حال استفاده است. به‌طور پیش‌فرض این رشته خالی است.
    - `methodDetails` {{optional_inline}}
      - : یک شیء که اطلاعات خاص روش پرداخت را فراهم می‌کند و تغییرات اعمال‌شده به پرداخت را توصیف می‌کند، یا اگر اطلاعات اضافی در دسترس یا مورد نیاز نباشد، `null` است. به‌طور پیش‌فرض این مقدار `null` است.

### مقدار بازگشتی

یک شیء {{domxref("PaymentMethodChangeEvent")}} جدید که تغییری در گزینه‌های مشخص‌شده برای روش پرداخت داده‌شده در ویژگی `methodName` را توصیف می‌کند.

نوع ویژگی `methodDetails` به روش پرداخت بستگی دارد. برای مثال، اگر `methodName` برابر با `https://example.com/pay` باشد، که نشان می‌دهد روش پرداخت Example Pay برای تأیید استفاده می‌شود، شکل `methodDetails` توسط آن روش پرداخت تعریف می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Payment Request API](/en-US/docs/Web/API/Payment_Request_API)
- [استفاده از Payment Request API](/en-US/docs/Web/API/Payment_Request_API/Using_the_Payment_Request_API)
- [مفاهیم پردازش پرداخت](/en-US/docs/Web/API/Payment_Request_API/Concepts)