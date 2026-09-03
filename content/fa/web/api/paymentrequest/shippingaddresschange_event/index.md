---
title: "PaymentRequest: shippingaddresschange event"
short-title: shippingaddresschange
slug: Web/API/PaymentRequest/shippingaddresschange_event
page-type: web-api-event
status:
  - deprecated
  - non-standard
browser-compat: api.PaymentRequest.shippingaddresschange_event
---

{{APIRef("Payment Request API")}}{{SecureContext_Header}}{{Deprecated_Header}}{{Non-standard_Header}}

رویداد **`shippingaddresschange`** وقتی به شیء {{domxref("PaymentRequest")}} ارسال می‌شود که کاربر یک آدرس حمل‌ونقل را انتخاب کند یا جزئیات آدرس حمل‌ونقل خود را تغییر دهد.

این رویداد قابل لغو (cancelable) نیست و حباب (bubble) نمی‌شود.

## نحو (Syntax)

برای استفاده از نام رویداد می‌توانید از روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی handler رویداد تنظیم کنید.

```js-nolint
addEventListener("shippingaddresschange", (event) => { })

onshippingaddresschange = (event) => { }
```

## نوع رویداد

یک {{domxref("PaymentRequestUpdateEvent")}}. از {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("PaymentRequestUpdateEvent")}}

## نکات استفاده

بسته به مرورگر، ممکن است اطلاعات آدرس حمل‌ونقل به دلایل حفظ حریم خصوصی ویرایش شود. به عبارت دیگر، {{domxref("PaymentAddress")}} که شامل آدرس حمل‌ونقل است ممکن است بخش‌هایی از محتوایش تغییر کند، مبهم شود یا به‌کلی حذف شود تا از شناسایی کاربر بدون رضایت او جلوگیری شود (زیرا اگر کاربر بخواهد محصولی برای او ارسال کنید، به آدرسش نیاز دارید).

## مثال

در این مثال، یک handler برای رویداد `shippingaddresschange` تنظیم شده است تا بررسی کند که آدرس با الزامات تعیین‌شده توسط برنامه وب مطابقت دارد.

```js
const paymentRequest = new PaymentRequest(methodData, details, options);

paymentRequest.addEventListener("shippingaddresschange", (event) => {
  const detailsUpdate = checkAddress(paymentRequest.shippingAddress);
  event.updateWith(detailsUpdate);
});

function checkAddress(theAddress) {
  const detailsUpdate = {};

  // Check the address, return an object with any changes or errors.

  return detailsUpdate;
}
```

همچنین می‌توانید با استفاده از ویژگی handler رویداد `onshippingaddresschange` یک handler برای `shippingaddresschange` تنظیم کنید:

```js
paymentRequest.onshippingaddresschange = (event) => {
  const detailsUpdate = checkAddress(paymentRequest.shippingAddress);
  event.updateWith(detailsUpdate);
};
```

## سازگاری مرورگر

{{Compat}}