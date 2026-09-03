---
title: "PaymentRequest: shippingoptionchange event"
short-title: shippingoptionchange
slug: Web/API/PaymentRequest/shippingoptionchange_event
page-type: web-api-event
status:
  - deprecated
  - non-standard
browser-compat: api.PaymentRequest.shippingoptionchange_event
---

{{APIRef("Payment Request API")}}{{SecureContext_Header}}{{Deprecated_Header}}{{Non-standard_Header}}

برای درخواست‌های پرداختی که اطلاعات حمل‌ونقل را درخواست می‌کنند و گزینه‌های حمل‌ونقل ارائه می‌دهند، رویداد **`shippingoptionchange`** هر زمان که کاربر یک گزینه حمل‌ونقل را از فهرست گزینه‌های موجود انتخاب کند، به {{domxref("PaymentRequest")}} ارسال می‌شود.

رشته‌ای که گزینه حمل‌ونقل انتخاب‌شدهٔ فعلی را مشخص می‌کند، در ویژگی {{domxref("PaymentRequest.shippingOption", "shippingOption")}} قابل دسترسی است.

این رویداد قابل لغو نیست و منتشر نمی‌شود (bubble نمی‌کند).

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("shippingoptionchange", (event) => { })

onshippingoptionchange = (event) => { }
```

## نوع رویداد

یک {{domxref("PaymentRequestUpdateEvent")}}. از {{domxref("Event")}} ارث‌بری می‌کند.

{{InheritanceDiagram("PaymentRequestUpdateEvent")}}

## مثال‌ها

این قطعه کد یک کنترل‌کننده برای رویداد `shippingoptionchange` تنظیم می‌کند. کد، هزینهٔ کل پرداخت را بر اساس گزینهٔ حمل‌ونقل انتخاب‌شده دوباره محاسبه می‌کند. به‌عنوان مثال، اگر سه گزینه وجود داشته باشد (مانند «حمل‌ونقل رایگان زمینی»، «هوایی دو روزه» و «روز بعد»)، هر بار که کاربر یکی از این گزینه‌ها را انتخاب کند، این کنترل‌کننده رویداد فراخوانی می‌شود تا کل را بر اساس گزینهٔ حمل‌ونقل تغییر یافته دوباره محاسبه کند.

```js
paymentRequest.addEventListener("shippingoptionchange", (event) => {
  const value = calculateNewTotal(paymentRequest.shippingOption);
  const total = {
    currency: "EUR",
    label: "Total due",
    value,
  };
  event.updateWith({ total });
});
```

پس از فراخوانی یک تابع سفارشی به نام `calculateNewTotal()` برای محاسبهٔ مجموع به‌روزرسانی‌شده بر اساس گزینهٔ حمل‌ونقل تازه انتخاب‌شده که توسط {{domxref("PaymentRequest.shippingOption", "shippingOption")}} مشخص شده است. مجموع تجدید نظر شده با فراخوانی روش {{domxref("PaymentRequestUpdateEvent.updateWith", "updateWith()")}} رویداد به درخواست پرداخت بازگردانده می‌شود.

همچنین می‌توانید یک کنترل‌کننده رویداد برای `shippingoptionchange` با استفاده از ویژگی کنترل‌کننده رویداد متناظر آن، یعنی `onshippingoptionchange` ایجاد کنید:

```js
paymentRequest.onshippingoptionchange = (event) => {
  const value = calculateNewTotal(paymentRequest.shippingOption);
  const total = {
    currency: "EUR",
    label: "Total due",
    value,
  };
  event.updateWith({ total });
};
```

## سازگاری با مرورگر

{{Compat}}