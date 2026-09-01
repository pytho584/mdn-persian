```
---
title: "ElementInternals: setFormValue() method"
short-title: setFormValue()
slug: Web/API/ElementInternals/setFormValue
page-type: web-api-instance-method
browser-compat: api.ElementInternals.setFormValue
---

{{APIRef("Web Components")}}

متد **`setFormValue()`** از رابط {{domxref("ElementInternals")}}، مقدار ارسالی و حالت عنصر را تنظیم می‌کند و این موارد را به عامل کاربر منتقل می‌کند.

## سینتکس

```js-nolint
setFormValue(value)
setFormValue(value, state)
```

### پارامترها

- `value`
  - : یک {{domxref("File")}}، یک رشته یا یک {{domxref("FormData")}} به‌عنوان مقداری که باید به سرور ارسال شود.
- `state` {{optional_inline}}
  - : یک {{domxref("File")}}، یک رشته یا یک {{domxref("FormData")}} که ورودی انجام‌شده توسط کاربر را نشان می‌دهد. این امکان را به برنامه می‌دهد تا در صورت نیاز، اطلاعات ارسال‌شده توسط کاربر را به همان شکلی که کاربر ارائه کرده است دوباره نمایش دهد.

> [!NOTE]
> به‌طور کلی، `state` برای انتقال اطلاعاتی استفاده می‌شود که توسط کاربر تعیین شده است، حال آنکه `value` برای ارسال به سرور، پس از پاکسازی (sanitization) مناسب است.
> برای مثال، اگر یک عنصر سفارشی از کاربر بخواهد تاریخی را وارد کند، ممکن است کاربر «3/15/2019» را وارد کند.
> این مقدار، `state` خواهد بود.
> سرور یک قالب تاریخ مانند `2019-03-15` را انتظار دارد؛ تاریخی که در این قالب باشد به‌عنوان `value` ارسال می‌شود.

### مقدار بازگشتی

undefined.

### استثناها

- `NotSupportedError` {{domxref("DOMException")}}
  - : اگر عنصر ویژگی `formAssociated` خود را روی `true` تنظیم نکرده باشد، این خطا پرتاب می‌شود.

## مثال‌ها

در مثال زیر، یک عنصر سفارشی چک‌باکس مقدار `on` را به‌عنوان مقداری برای ارسال به سرور و `checked` را به‌عنوان state تنظیم می‌کند.

```js
this.internals_.setFormValue("on", "checked");
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
```