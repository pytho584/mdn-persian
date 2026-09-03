---
title: "PaymentResponse"
slug: Web/API/PaymentResponse
page-type: web-api-interface
browser-compat: api.PaymentResponse
---

{{SecureContext_Header}}{{APIRef("Payment Request API")}}

رابط **`PaymentResponse`** از [Payment Request API](/en-US/docs/Web/API/Payment_Request_API) پس از آن که کاربر یک روش پرداخت را انتخاب کرد و درخواست پرداخت را تأیید کرد، بازگردانده می‌شود.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref('PaymentResponse.details')}} {{ReadOnlyInline}}
  - : یک شیء قابل سریال‌سازی به JSON بازمی‌گرداند که یک پیام خاص روش پرداخت را ارائه می‌دهد و توسط فروشنده برای پردازش تراکنش و تعیین موفقیت انتقال وجه استفاده می‌شود. محتویات این شیء به روش پرداخت مورد استفاده بستگی دارد. توسعه‌دهندگان باید با شخصی که URL را کنترل می‌کند، برای شکل مورد انتظار شیء جزئیات مشورت کنند.
- {{domxref('PaymentResponse.methodName')}} {{ReadOnlyInline}}
  - : شناسه روش پرداخت برای روش پرداختی که کاربر انتخاب کرده است را بازمی‌گرداند، به عنوان مثال Visa، Mastercard، PayPal و غیره.
- {{domxref('PaymentResponse.payerEmail')}} {{ReadOnlyInline}}
  - : آدرس ایمیلی که کاربر ارائه داده است را بازمی‌گرداند. این گزینه تنها زمانی وجود دارد که گزینه `requestPayerEmail` در پارامتر `options` سازنده {{domxref('PaymentRequest.PaymentRequest','PaymentRequest()')}} برابر با `true` تنظیم شده باشد.
- {{domxref('PaymentResponse.payerName')}} {{ReadOnlyInline}}
  - : نامی که کاربر ارائه داده است را بازمی‌گرداند. این گزینه تنها زمانی وجود دارد که گزینه `requestPayerName` در پارامتر `options` سازنده {{domxref('PaymentRequest.PaymentRequest','PaymentRequest()')}} برابر با `true` تنظیم شده باشد.
- {{domxref('PaymentResponse.payerPhone')}} {{ReadOnlyInline}}
  - : شماره تلفنی که کاربر ارائه داده است را بازمی‌گرداند. این گزینه تنها زمانی وجود دارد که گزینه `requestPayerPhone` در پارامتر `options` سازنده {{domxref('PaymentRequest.PaymentRequest','PaymentRequest()')}} برابر با `true` تنظیم شده باشد.
- {{domxref('PaymentResponse.requestId')}} {{ReadOnlyInline}}
  - : شناسه {{domxref('PaymentRequest')}} که پاسخ فعلی را تولید کرده است بازمی‌گرداند. این همان مقداری است که در سازنده {{domxref('PaymentRequest.PaymentRequest','PaymentRequest()')}} توسط `details.id` ارائه شده است.
- {{domxref('PaymentResponse.shippingAddress')}} {{ReadOnlyInline}}
  - : آدرس حمل و نقلی که کاربر ارائه داده است را بازمی‌گرداند. این گزینه تنها زمانی وجود دارد که گزینه `requestShipping` در پارامتر `options` سازنده {{domxref('PaymentRequest.PaymentRequest','PaymentRequest()')}} برابر با `true` تنظیم شده باشد.
- {{domxref('PaymentResponse.shippingOption')}} {{ReadOnlyInline}}
  - : ویژگی ID گزینه حمل و نقلی که کاربر انتخاب کرده است را بازمی‌گرداند. این گزینه تنها زمانی وجود دارد که گزینه `requestShipping` در پارامتر `options` سازنده {{domxref('PaymentRequest.PaymentRequest','PaymentRequest()')}} برابر با `true` تنظیم شده باشد.

## روش‌های نمونه

- {{domxref('PaymentResponse.retry()')}}
  - : اگر مشکلی در داده‌های پاسخ پرداخت وجود داشته باشد (و خطا قابل بازیابی باشد)، این روش به فروشنده اجازه می‌دهد از کاربر بخواهد پرداخت را دوباره امتحان کند. این روش یک شیء به عنوان آرگومان می‌گیرد که برای اطلاع دقیق کاربر از مشکل موجود در پاسخ پرداخت استفاده می‌شود تا بتواند سعی در رفع مشکلات کند.
- {{domxref('PaymentResponse.complete()')}}
  - : به عامل کاربر اطلاع می‌دهد که تعامل کاربر به پایان رسیده است. این کار باعث بسته شدن هر رابط کاربری باقی‌مانده می‌شود. این روش فقط پس از حل شدن Promise بازگردانده شده توسط روش {{domxref('PaymentRequest.show()')}} باید فراخوانی شود.
- {{domxref("PaymentResponse.toJSON()")}}
  - : یک [شیء JSON](/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON) بازمی‌گرداند که نمایانگر این شیء `PaymentResponse` است.

## رویدادها

به این رویداد با استفاده از [`addEventListener()`](/en-US/docs/Web/API/EventTarget/addEventListener) یا با اختصاص یک شنونده رویداد به ویژگی `oneventname` این رابط گوش دهید.

- [`payerdetailchange`](/en-US/docs/Web/API/PaymentResponse/payerdetailchange_event)
  - : در طول یک تلاش مجدد زمانی که کاربر تغییراتی در اطلاعات شخصی خود هنگام پر کردن فرم درخواست پرداخت ایجاد می‌کند، فعال می‌شود. به توسعه‌دهنده اجازه می‌دهد هر داده کاربر درخواست شده (مانند شماره تلفن یا آدرس ایمیل) را در صورت تغییر، دوباره اعتبارسنجی کند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}