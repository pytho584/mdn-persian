---
title: "PaymentRequest"
---

---
title: PaymentRequest
slug: Web/API/PaymentRequest
page-type: web-api-interface
browser-compat: api.PaymentRequest
---

{{APIRef("Payment Request API")}}{{SecureContext_Header}}

رابط **`PaymentRequest`** در [Payment Request API](/en-US/docs/Web/API/Payment_Request_API) نقطهٔ دسترسی اصلی به این API است و به محتوای وب و برنامه‌ها اجازه می‌دهد تا از طرف مالک سایت یا ناشر برنامه، پرداخت‌هایی را از کاربر نهایی دریافت کنند.

{{InheritanceDiagram}}

## سازنده

- {{domxref('PaymentRequest.PaymentRequest()','PaymentRequest()')}}
  - : یک شیء `PaymentRequest` جدید ایجاد می‌کند.

## ویژگی‌های نمونه

- {{domxref('PaymentRequest.id')}} {{ReadOnlyInline}}
  - : یک شناسهٔ یکتا برای یک `PaymentRequest` خاص که می‌تواند از طریق `details.id` تنظیم شود. اگر تنظیم نشده باشد، به‌طور پیش‌فرض یک UUID خواهد بود.
- {{domxref('PaymentRequest.shippingAddress')}} {{ReadOnlyInline}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : اگر از طریق گزینه‌های پرداخت درخواست شده باشد، آدرس حمل‌ونقل انتخابی کاربر را برای محاسبهٔ هزینهٔ ارسال برمی‌گرداند. این ویژگی فقط زمانی مقداردهی می‌شود که سازنده با پرچم `requestShipping` برابر با `true` فراخوانده شود. همچنین، در برخی مرورگرها، تا زمانی که کاربر آمادگی خود را برای تکمیل تراکنش اعلام نکند (یعنی دکمه «پرداخت» را فشار ندهد)، بخش‌هایی از آدرس به دلایل حریم خصوصی پنهان می‌شوند.
- {{domxref('PaymentRequest.shippingOption')}} {{ReadOnlyInline}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : شناسهٔ گزینهٔ حمل‌ونقل انتخاب‌شده را برمی‌گرداند. این ویژگی فقط زمانی مقداردهی می‌شود که سازنده با پرچم `requestShipping` برابر با `true` فراخوانده شود.
- {{domxref('PaymentRequest.shippingType')}} {{ReadOnlyInline}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : نوع حمل‌ونقل مورد استفاده برای انجام تراکنش را برمی‌گرداند. این مقدار می‌تواند یکی از `shipping`، `delivery`، `pickup` یا در صورت عدم ارائهٔ مقدار در سازنده، `null` باشد.

## روش‌های ایستا

- {{domxref('PaymentRequest.securePaymentConfirmationAvailability_static', 'PaymentRequest.securePaymentConfirmationAvailability()')}} {{experimental_inline}}
  - : نشان می‌دهد که آیا قابلیت [تأیید امن پرداخت](/en-US/docs/Web/API/Payment_Request_API/Using_secure_payment_confirmation) در دسترس است یا خیر.

## روش‌های نمونه

- {{domxref('PaymentRequest.canMakePayment()')}}
  - : نشان می‌دهد که آیا شیء `PaymentRequest` می‌تواند قبل از فراخوانی `show()` پرداختی انجام دهد یا خیر.
- {{domxref('PaymentRequest.show()')}}
  - : باعث می‌شود عامل کاربر (user agent) تعامل کاربر برای درخواست پرداخت را آغاز کند.
- {{domxref('PaymentRequest.abort()')}}
  - : باعث می‌شود عامل کاربر به درخواست پرداخت پایان دهد و هر رابط کاربری که ممکن است نمایش داده شده باشد را حذف کند.

## رویدادها

- {{domxref("PaymentRequest.merchantvalidation_event", "merchantvalidation")}} {{Deprecated_Inline}} {{non-standard_inline}}
  - : با برخی از پردازشگرهای پرداخت (مانند Apple Pay)، این رویداد برای مدیریت رویداد {{domxref("PaymentRequest.merchantvalidation_event", "merchantvalidation")}} فراخوانی می‌شود. این رویداد زمانی ارسال می‌شود که عامل کاربر نیاز دارد فروشنده تأیید کند که فروشنده یا ارائه‌دهندهٔ درخواست‌کنندهٔ پرداخت معتبر است.
- {{domxref("PaymentRequest.paymentmethodchange_event", "paymentmethodchange")}}
  - : با برخی از پردازشگرهای پرداخت (مانند Apple Pay)، هر زمان که کاربر ابزار پرداخت را تغییر دهد، مانند تغییر از کارت اعتباری به کارت نقدی، ارسال می‌شود.
- {{domxref("PaymentRequest.shippingaddresschange_event", "shippingaddresschange")}}{{Deprecated_Inline}} {{Non-standard_Inline}}
  - : هر زمان که کاربر آدرس حمل‌ونقل خود را تغییر دهد، ارسال می‌شود.
- {{domxref("PaymentRequest.shippingoptionchange_event", "shippingoptionchange")}} {{Deprecated_Inline}} {{Non-standard_Inline}}
  - : هر زمان که کاربر گزینهٔ حمل‌ونقل را تغییر دهد، ارسال می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}