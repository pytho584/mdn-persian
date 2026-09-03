---
title: Payment processing concepts
slug: Web/API/Payment_Request_API/Concepts
page-type: guide
spec-urls:
  - https://w3c.github.io/payment-request/
  - https://w3c.github.io/payment-method-id/
---

{{DefaultAPISidebar("Payment Request API")}}

رابط برنامه‌نویسی درخواست پرداخت ([Payment Request API](/en-US/docs/Web/API/Payment_Request_API)) پردازش پرداخت در یک وب‌سایت یا برنامه را آسان می‌کند. در این مقاله، نگاهی می‌اندازیم به اینکه این API چگونه کار می‌کند و هر یک از اجزای آن چه کاری انجام می‌دهد.

## اصطلاحات

پیش از پرداختن به جزئیات نحوه عملکرد API، لازم است با چند مفهوم آشنا شوید.

- payee (or merchant)
  - : فروشنده — شخص یا سازمان — که وب‌سایت یا برنامه‌اش می‌خواهد از طریق Payment Request API پول دریافت کند.
- payer
  - : شخص یا سازمانی که با استفاده از یک وب‌سایت یا برنامه خرید می‌کند. پرداخت‌کننده طبق الزام روش پرداخت، احراز هویت می‌کند و سپس پرداخت را مجاز می‌کند.
- payment method
  - : ابزاری که پرداخت با استفاده از آن انجام می‌شود، مانند کارت اعتباری یا سرویس پرداخت آنلاین.
- payment method provider
  - : سازمانی که فناوری لازم برای انجام پرداخت با یک روش پرداخت معین را فراهم می‌کند. برای مثال، هنگام پرداخت با کارت اعتباری، سرویس پردازش کارت اعتباری، ارائه‌دهنده روش پرداخت است.
- payment handler
  - : پیاده‌سازی کدهای لازم برای ارتباط با یک ارائه‌دهنده روش پرداخت خاص به‌منظور پردازش پرداخت‌ها.

برخی از پردازنده‌های پرداخت از **merchant validation** (تأیید هویت فروشنده) استفاده می‌کنند؛ فرآیندی که در آن هویت فروشنده به نحوی اعتبارسنجی می‌شود، معمولاً با استفاده از نوعی پاسخ رمزنگاری مانند کلید عمومی. فروشندگان تأییدشده مجاز به ارتباط با یک پردازنده پرداخت هستند.

## شناسه‌های روش پرداخت

پردازنده‌های پرداخت با **شناسه‌های روش پرداخت** (payment method identifiers) شناسایی می‌شوند؛ رشته‌هایی که به‌صورت یکتا پردازنده پرداخت را مشخص می‌کنند. این شناسه‌ها می‌توانند یکی از شناسه‌های استانداردشده پردازنده پرداخت باشند یا یک URL که سرویس پردازش پرداخت هم برای شناسایی خود و هم برای مدیریت پرداخت‌ها از آن استفاده می‌کند.

### شناسه‌های استاندارد روش پرداخت

شناسه‌های استاندارد روش پرداخت، شناسه‌هایی هستند که در [payment method registry](https://w3c.github.io/payment-method-id/#registry) فهرست شده‌اند.

- `secure-payment-confirmation`
  - : روش [Secure Payment Confirmation](https://w3c.github.io/secure-payment-confirmation/) را شناسایی می‌کند. داده‌های درخواست پرداخت برای این روش توسط دیکشنری {{domxref("SecurePaymentConfirmationRequest")}} تعریف می‌شود. برای اطلاعات بیشتر، [Using Secure Payment Confirmation](/en-US/docs/Web/API/Payment_Request_API/Using_secure_payment_confirmation) را ببینید.

- `basic-card`
  - : این شناسه روش پرداخت برای تسهیل پرداخت‌های مبتنی بر کارت در وب از طریق Payment Request API در نظر گرفته شده بود. **گروه [Web Payments Working Group](https://www.w3.org/groups/wg/payments) این روش پرداخت را منسوخ (deprecated) اعلام کرده است.**

### شناسه‌های روش پرداخت مبتنی بر URL

این شناسه‌ها معمولاً توسط ارائه‌دهندگان سرویس پرداخت هنگام راه‌اندازی (onboarding) یا یکپارچه‌سازی ارائه می‌شوند و بسته به ویژگی‌های سرویس، نسخه API و فناوری ارتباطی ممکن است بسیار متفاوت باشند. توسعه‌دهندگان معمولاً این شناسه‌ها را مستقیماً از مستندات ارائه‌دهنده سرویس پرداخت انتخابی خود دریافت می‌کنند، نه اینکه به‌طور مستقل آن‌ها را کشف کنند.

- `https://apple.com/apple-pay`
  - : پرداخت‌ها با استفاده از سرویس [Apple Pay](https://www.apple.com/apple-pay/) انجام می‌شوند. این روش پرداخت عمدتاً در Safari روی دستگاه‌های سازگار اپل پشتیبانی می‌شود.
- `https://google.com/pay`
  - : پرداخت‌ها توسط [Google Pay](https://pay.google.com/payments/home/) پردازش می‌شوند. پشتیبانی از آن به مرورگرهایی بستگی دارد که Payment Handler API را پیاده‌سازی می‌کنند (در حال حاضر عمدتاً مرورگرهای مبتنی بر Chromium).

## وظایف یک پردازنده پرداخت

یک {{Glossary("user agent")}} ممکن است پشتیبانی داخلی برای برخی از انواع پرداخت‌ها فراهم کند. علاوه بر این، می‌توان از [Payment Handler API](https://w3c.github.io/web-based-payment-handler/) برای ایجاد پشتیبانی از ارائه‌دهندگان روش پرداخت اضافی در مرورگرهایی که از آن پشتیبانی می‌کنند استفاده کرد. در هر صورت، پردازنده پرداخت مسئول موارد زیر است:

1. **اطمینان از اینکه پرداخت امکان‌پذیر است.** شرایطی که پرداخت را ممکن می‌کنند بسته به روش پرداخت و درخواست پرداخت کاربر متفاوت است؛ برای مثال، اگر کاربر بخواهد با کارت اعتباری‌ای پرداخت کند که توسط فروشنده پذیرفته نشده است، پرداخت امکان‌پذیر نیست.
2. **اگر پردازنده پرداخت از merchant validation پشتیبانی می‌کند، به درخواست‌های تأیید هویت فروشنده از سمت user agent پاسخ دهد.** برای جزئیات به [Merchant validation](#merchant_validation) مراجعه کنید.
3. **تأیید اینکه اطلاعات ارائه‌شده توسط کاربر به یک تراکنش معتبر منجر می‌شود.** این امر منجر به ایجاد و بازگرداندن یک شیء خاص روش پرداخت می‌شود که حاوی اطلاعات لازم برای مدیریت تراکنش است.

## Merchant validation

برخی از پردازنده‌های پرداخت از _merchant validation_ (تأیید هویت فروشنده) استفاده می‌کنند؛ فرآیندی که در آن هویت فروشنده به نحوی اعتبارسنجی می‌شود، معمولاً با استفاده از نوعی چالش رمزنگاری. اگر فروشنده با موفقیت تأیید نشود، اجازه استفاده از پردازنده پرداخت را ندارد.

فناوری دقیق تأیید هویت به پردازنده پرداخت بستگی دارد و merchant validation کاملاً اختیاری است. در نهایت، تنها کاری که وب‌سایت یا برنامه مسئول آن است، دریافت کلید تأیید هویت فروشنده و ارسال آن به متد {{domxref("MerchantValidationEvent.complete", "complete()")}} رویداد است.

```js
paymentRequest.onmerchantvalidation = (event) => {
  event.complete(fetchValidationData(event.validationURL));
};
```

در این مثال، `fetchValidationData()` تابعی است که اطلاعات شناسایی خاص پردازنده پرداخت را از آدرس داده‌شده توسط `validationURL` بارگذاری می‌کند. توجه داشته باشید که این تابع باید از طریق سرور فروشنده عمل کند، زیرا معمولاً کلاینت به خودِ URL تأیید هویت دسترسی ندارد.

سپس با ارسال این داده‌ها (یا یک {{jsxref("Promise")}} که به داده‌های بارگذاری‌شده resolve می‌شود) به پردازنده پرداخت از طریق `complete()`، پردازنده پرداخت می‌تواند از داده‌های بازیابی‌شده و هر الگوریتم و داده‌های دیگری که پشتیبانی می‌کند استفاده کند تا تأیید کند که فروشنده می‌تواند از پردازنده پرداخت استفاده کند.

بنابراین، توجه به این نکته مهم است که {{Glossary("user agent")}} هرگز رویداد {{domxref("PaymentRequest.merchantvalidation_event", "merchantvalidation")}} را ارسال نمی‌کند، مگر اینکه خود user agent یک پردازنده پرداخت پیاده‌سازی کرده باشد. برای مثال، Safari پشتیبانی یکپارچه‌ای از Apple Pay دارد؛ بنابراین پردازنده پرداخت Apple Pay با ارسال `merchantvalidation` به کلاینت و دستور دریافت داده‌های تأیید هویت سرور و تحویل آن به پردازنده پرداخت از طریق فراخوانی `complete()`، مطمئن می‌شود که Apple Pay می‌تواند برای پرداخت به فروشنده استفاده شود.

## مشخصات

{{Specifications}}

## همچنین ببینید

- [Payment Request API](/en-US/docs/Web/API/Payment_Request_API)
- [Using the Payment Request API](/en-US/docs/Web/API/Payment_Request_API/Using_the_Payment_Request_API)
- [Introducing the Payment Request API for Apple Pay](https://webkit.org/blog/8182/introducing-the-payment-request-api-for-apple-pay/)
- [Google Pay API PaymentRequest Tutorial](https://developers.google.com/pay/api/web/guides/paymentrequest/tutorial)
- [Android Payment Apps Developers Guide](https://web.dev/articles/android-payment-apps-developers-guide)
- [Samsung Internet Web Payments Integration Guide](https://developer.samsung.com/internet/android/web-payments-integration-guide.html)