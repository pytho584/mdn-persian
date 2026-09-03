---
title: Payment Request API
slug: Web/API/Payment_Request_API
page-type: web-api-overview
browser-compat: api.PaymentRequest
---

{{DefaultAPISidebar("Payment Request API")}}{{securecontext_header}}

**Payment Request API** تجربهٔ کاربری یکپارچه‌ای برای فروشندگان و کاربران فراهم می‌کند. این API روش جدیدی برای پرداخت نیست؛ بلکه راهی است که کاربران بتوانند روش پرداخت موردنظر خود را انتخاب کرده و آن اطلاعات را در اختیار فروشنده قرار دهند.

## مفاهیم و کاربرد

بسیاری از مشکلات مربوط به رها شدن سبد خرید آنلاین ریشه در فرم‌های تسویه‌حساب دارند؛ فرم‌هایی که پر کردن آن‌ها دشوار و زمان‌بر است و اغلب تکمیل آن‌ها به چندین مرحله نیاز دارد. **Payment Request API** برای کاهش مراحل لازم جهت تکمیل پرداخت آنلاین طراحی شده و به‌طور بالقوه می‌تواند فرم‌های تسویه‌حساب را کاملاً حذف کند. هدف این است که با ذخیره‌سازی اطلاعات کاربر در برنامه‌های پرداخت و ارسال آن به فروشنده، فرایند تسویه‌حساب در دسترس‌تر شود و امید است دیگر به فرم HTML نیازی نباشد.

برای درخواست پرداخت، صفحهٔ وب در واکنش به اقدام کاربری که پرداخت را آغاز می‌کند — مانند کلیک روی دکمهٔ «خرید» — یک شیء {{domxref("PaymentRequest")}} می‌سازد. `PaymentRequest` به صفحهٔ وب اجازه می‌دهد تا در حالی که کاربر برای تکمیل تراکنش اطلاعات لازم را وارد می‌کند، با عامل کاربر (user agent) تبادل اطلاعات کند.

راهنمای کاملی را در [استفاده از Payment Request API](/en-US/docs/Web/API/Payment_Request_API/Using_the_Payment_Request_API) ببینید.

> [!NOTE]
> این API در عناصر {{htmlelement("iframe")}} که مبدأ متفاوتی با صفحهٔ والد دارند (cross-origin) تنها زمانی در دسترس است که ویژگی [`allowpaymentrequest`](/en-US/docs/Web/HTML/Reference/Elements/iframe#allowpaymentrequest) روی آن‌ها تنظیم شده باشد.

## رابط‌ها

- {{domxref('PaymentAddress')}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : شیئی که اطلاعات نشانی را نگهداری می‌کند؛ برای نمونه برای نشانی صورت‌حساب و نشانی حمل‌ونقل استفاده می‌شود.
- {{domxref('PaymentRequest')}}
  - : شیئی که API لازم برای ایجاد و مدیریت رابط پرداختِ {{Glossary("user agent", "user agent's")}} را فراهم می‌کند.
- {{domxref('PaymentRequestUpdateEvent')}}
  - : به صفحهٔ وب اجازه می‌دهد جزئیات درخواست پرداخت را در پاسخ به اقدام کاربر به‌روزرسانی کند.
- {{domxref('PaymentMethodChangeEvent')}}
  - : نمایانگر تغییر ابزار پرداخت توسط کاربر است (برای نمونه، جابه‌جایی از یک روش پرداخت به روش دیگر).
- {{domxref('PaymentResponse')}}
  - : شیئی که پس از انتخاب روش پرداخت توسط کاربر و پذیرفته‌شدن درخواست پرداخت بازگردانده می‌شود.
- {{domxref('MerchantValidationEvent')}} {{Deprecated_Inline}}
  - : نمایانگر شرایطی است که مرورگر از فروشنده (وب‌سایت) می‌خواهد تأیید کند که برای استفاده از یک پردازندهٔ پرداخت خاص مجاز است (برای نمونه، به‌عنوان دارندهٔ مجوز استفاده از Apple Pay ثبت شده باشد).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Payment Request API](/en-US/docs/Web/API/Payment_Request_API/Using_the_Payment_Request_API)
- [مفاهیم پردازش پرداخت](/en-US/docs/Web/API/Payment_Request_API/Concepts)
- [معرفی Payment Request API برای Apple Pay](https://webkit.org/blog/8182/introducing-the-payment-request-api-for-apple-pay/)
- [آموزش Google Pay API PaymentRequest](https://developers.google.com/pay/api/web/guides/paymentrequest/tutorial)
- [راهنمای یکپارچه‌سازی پرداخت وب در Samsung Pay](https://developer.samsung.com/internet/android/web-payments-integration-guide.html)
- [پرسش‌های متداول W3C درباره Payment Request API](https://github.com/w3c/payment-request-info/wiki/FAQ)
- دستور Permissions Policy {{httpheader("Permissions-Policy/payment", "payment")}}