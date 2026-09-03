---
title: Using Secure Payment Confirmation
slug: Web/API/Payment_Request_API/Using_secure_payment_confirmation
page-type: guide
spec-urls:
  - https://w3c.github.io/payment-request/
  - https://w3c.github.io/payment-method-id/
  - https://w3c.github.io/webauthn/
---

{{DefaultAPISidebar("Payment Request API")}}

Secure Payment Confirmation (SPC) که از طریق Payment Request API در دسترس است، سازوکاری برای احراز هویت قوی مشتری هنگام پرداخت فراهم می‌کند و بدین ترتیب از کلاهبرداری در پرداخت‌های آنلاین جلوگیری می‌کند.

## نمای کلی

برای جلوگیری از کلاهبرداری در پرداخت‌های آنلاین، معمولاً هویت صاحب حساب احراز می‌شود. احراز هویت قوی خطر کلاهبرداری را کاهش می‌دهد، اما احتمالِ رها شدن سبد خرید را به دلیل اصطکاکِ ایجادشده در فرایند خرید افزایش می‌دهد.

بنابراین بانک‌ها، فروشندگان، ارائه‌دهندگان خدمات پرداخت و سایر فعالانِ زیست‌بوم پرداخت هنگام انتخاب نوع و قدرت احراز هویت برای هر تراکنش، عوامل متعددی را در نظر می‌گیرند؛ از جمله مبلغ تراکنش، اقلام خریداری‌شده، سابقه پرداخت کاربر، اینکه در صورت کلاهبرداری کدام طرف مسئولیت خسارت را بر عهده می‌گیرد، و الزامات قانونی (مانند الزامات [دستورالعمل دوم خدمات پرداخت اروپا](<https://en.wikipedia.org/wiki/Payment_Services_Directive#Revised_Directive_on_Payment_Services_(PSD2)>) درباره احراز هویت قوی مشتری و ارائهٔ شواهد رضایت کاربر).

برای احراز هویت قوی، معمولاً چند سازوکار به‌صورت ترکیبی استفاده می‌شود؛ از جمله گذرواژه، کدهای یک‌بارمصرف پیامکی، اپلیکیشن‌های موبایل و Web Authentication. هر یک از این‌ها مزایا و معایب خود را دارند. برای مثال، کدهای یک‌بارمصرف پیامکی اکنون برای کاربران آشنا هستند اما ممکن است مشکلات کاربری (مانند در دسترس نبودن دستگاه موردنظر) و آسیب‌پذیری‌های امنیتی به همراه داشته باشند. Web Authentication امنیت بهتری ارائه می‌دهد و در تمام مرورگرهای اصلی و تمام گوشی‌ها و رایانه‌های مدرن در دسترس است. با وجود این، Web Authentication به‌تنهایی شواهدی مبنی بر رضایت کاربر برای انجام پرداخت فراهم نمی‌کند.

SPC برای فعال‌سازیِ احراز هویت قوی مشتری (SCA) به شکلی ساده و روان در انواع سیستم‌های پرداخت طراحی شده است و شواهد رمزنگاری‌شده‌ای فراهم می‌کند که نشان می‌دهد کاربر با شرایط تراکنش موافقت کرده است. وقتی این API فراخوانی می‌شود، مرورگر عناصر تراکنش را در یک کادر محاوره‌ای نشان می‌دهد: نام فروشنده، ابزار پرداخت و مبلغ و واحد پول. برای نمونه، کادر محاوره‌ای تراکنش مرورگر Chrome (نسخه M118) برای SPC به این شکل است:

![Chrome M118 transaction dialog for SPC](chrome-tx-dialog.png)

با انتخاب «Verify» یک فرایند Web Authentication شروع می‌شود. وقتی کاربر با موفقیت احراز هویت می‌کند (مثلاً با استفاده از ابزارهای زیست‌سنجی تلفن یا لپ‌تاپ خود)، مرورگر داده‌های نمایش‌داده‌شده در کادر محاوره‌ای را به ابزار احراز هویت (authenticator) می‌فرستد. ابزار احراز هویت آن داده‌ها را امضا می‌کند و آن‌ها را به‌عنوان بخشی از تأییدیه Web Authentication (assertion) حاصل، به مرورگر برمی‌گرداند. سپس این تأییدیه برای اعتبارسنجی به طرف اتکا (Relying Party) ارسال می‌شود. چون مرورگر داده‌های نمایش‌داده‌شده را مستقیماً در اختیار ابزار احراز هویت قرار می‌دهد (بدون آنکه هیچ کد جاوااسکریپتی بتواند آن داده‌ها را تغییر دهد)، طرف اتکا می‌تواند با اطمینان بالایی مطمئن باشد که کاربر با داده‌های تراکنشِ نمایش‌داده‌شده موافقت کرده است.

به این ترتیب، SPC بر پایه Web Authentication ساخته شده است تا سایَت‌ها بتوانند احراز هویت قویِ بدون‌اصطکاک انجام دهند و شواهدی از رضایت کاربر فراهم کنند. SPC به‌طور معمول به‌عنوان بخشی از چارچوب احراز هویتِ یک سیستم پرداخت مشخص به کار می‌رود. برای مثال، SPC هم در EMV® 3-D Secure نسخهٔ 2.3.1 و هم در EMV® Secure Remote Commerce نسخهٔ 1.3 پشتیبانی می‌شود، اما طوری طراحی شده است که با طیف گسترده‌ای از انواع پرداخت، از جمله پرداخت‌های «push» مانند انتقال مستقیم اعتباری و پرداخت‌های کیف پول، سازگار باشد.

## روش درخواست پرداخت

Secure Payment Confirmation از قابلیت‌های زیربنایی Payment Request API بهره می‌گیرد. شناسهٔ استانداردِ روش پرداختِ مورد استفاده برای Secure Payment Confirmation، [`"secure-payment-confirmation"`](/en-US/docs/Web/API/Payment_Request_API/Concepts#secure-payment-confirmation) است.

## افزونهٔ Web Authentication

Secure Payment Confirmation یک [افزونهٔ Web Authentication](/en-US/docs/Web/API/Web_Authentication_API/WebAuthn_extensions) به نام [`payment`](/en-US/docs/Web/API/Web_Authentication_API/WebAuthn_extensions#payment) تعریف می‌کند که سه قابلیت ویژهٔ پرداخت را به Web Authentication سنتی اضافه می‌کند:

1. وقتی طرف اتکا استفاده از آن را فعال کند، به نهادهایی غیر از طرف اتکا اجازه می‌دهد با استفاده از اعتبارنامه‌های طرف اتکا، فرایند احراز هویتِ پرداخت را آغاز کنند. SPC فرایند احراز هویت را از اعتبارسنجی نتایج احراز هویت جدا می‌کند. این کار به فروشندگان (یا ارائه‌دهندگان خدمات پرداختِ آن‌ها در یک iframe با مبدأ متفاوت) اجازه می‌دهد کنترل تجربهٔ کاربری احراز هویت را در دست بگیرند، بدون اینکه کاربر را از طریق تغییر مسیر (redirect) به وب‌سایت یا اپلیکیشن موبایل دیگری منتقل کنند. اگر طرف اتکا مثلاً بانک باشد، این ویژگی به فروشنده اجازه می‌دهد تجربه کاربری احراز هویت را مدیریت کند، در حالی که بانک همچنان می‌تواند نتایج احراز هویت را اعتبارسنجی کند. ارتباط بین طرف‌ها (برای تبادل اعتبارنامه‌ها و نتایج احراز هویت) معمولاً از طریق زیرساخت‌های خاصِ همان سیستم پرداخت، مانند EMV® 3-D Secure، انجام می‌شود.
2. تضمین می‌کند که عامل کاربر (User Agent) به‌شکل مناسبی به کاربر اطلاع دهد که در حال احراز هویتِ یک تراکنش است و جزئیات آن تراکنش چیست. سپس این جزئیات در تأییدیه‌ای که ابزار احراز هویت امضا کرده است گنجانده می‌شوند.
3. اجازه می‌دهد navigator.credentials.create در یک iframe با مبدأ متفاوت فراخوانی شود، به شرطی که خط‌مشی مجوزِ «payment» روی آن iframe تنظیم شده باشد.
   توجه: این قابلیت اکنون بخشی از WebAuthn Level 3 است و در آنجا در عوض از خط‌مشی مجوزِ «publickey-credential-create» استفاده می‌شود. به توسعه‌دهندگان توصیه می‌شود هرجا در دسترس بود از آن استفاده کنند، نه از مجوزِ «payment» مخصوص SPC.

## مثال‌ها

### ایجاد یک اعتبارنامه

ایجاد یک اعتبارنامه در Secure Payment Confirmation با همان فراخوانی {{domxref("CredentialsContainer.create()", "navigator.credentials.create()")}} در Web Authentication انجام می‌شود، با این تفاوت که افزونهٔ `payment` نیز مشخص شده است.

```js
const publicKey = {
  challenge: Uint8Array.from(randomStringFromServer, (c) => c.charCodeAt(0)),
  rp: {
    name: "Fancy Bank",
  },
  user: {
    // Assuming that userId is ASCII-only
    id: Uint8Array.from(userId, (c) => c.charCodeAt(0)),
    name: "jane.doe@example.org",
    displayName: "Jane Doe",
  },
  pubKeyCredParams: [
    {
      type: "public-key",
      alg: -7, // "ES256"
    },
    {
      type: "public-key",
      alg: -257, // "RS256"
    },
  ],
  authenticatorSelection: {
    userVerification: "required",
    residentKey: "required",
    authenticatorAttachment: "platform",
  },
  timeout: 60000, // 1 minute
  extensions: {
    payment: {
      isPayment: true,
    },
  },
};
navigator.credentials
  .create({ publicKey })
  .then((newCredentialInfo) => {
    // Send new credential info to server for verification and registration.
  })
  .catch((err) => {
    // No acceptable authenticator or user refused consent. Handle appropriately.
  });
```

### ایجاد یک اعتبارنامه در iframe با مبدأ متفاوت

SPC اجازه می‌دهد اعتبارنامه‌ای در یک iframe با مبدأ متفاوت ایجاد شود (مثلاً اگر `merchant.com` یک iframe از `bank.com` را درون صفحه خود جا دهد).

در این جریان، به‌عنوان بخشی از یک تراکنش، طرف اتکا (مثلاً بانک) هویت صاحب حساب را از طریق سازوکاری غیر از SPC احراز می‌کند (مثلاً با استفاده از گذرواژهٔ یک‌بارمصرف یا سازوکاری دیگر). سپس طرف اتکا این گزینه را به کاربر پیشنهاد می‌دهد که برای تسهیل تراکنش‌های آینده، یک اعتبارنامهٔ SPC ثبت کند. کاربر نیز آن اعتبارنامهٔ SPC را برای طرف اتکا ثبت می‌کند. برای اینکه این مراحل در بافت فروشنده (بدون تغییر مسیر) انجام شوند، iframe با مبدأ متفاوت باید خط‌مشیِ مجوزِ [`payment`](/en-US/docs/Web/HTTP/Reference/Headers/Permissions-Policy/payment) را تنظیم شده داشته باشد.

```html
<!-- Assume parent origin is merchant.com -->
<!-- Inside this cross-origin iframe, script would be allowed to create a SPC credential for example.org -->
<iframe src="https://example.org" allow="payment"></iframe>
```

### احراز هویت یک پرداخت

یک مبدأ می‌تواند Payment Request API را با روش پرداخت `"secure-payment-confirmation"` فراخوانی کند تا از کاربر بخواهد با استفاده از اعتبارنامهٔ Secure Payment Confirmation که توسط مبدأ دیگری ایجاد شده است، هویت خود را تأیید کند. مرورگر یک رابط کاربری بومی (به‌نام «کادر محاوره‌ای تراکنش») با جزئیات تراکنش نمایش می‌دهد (برای مثال واحد پول، مبلغ و مبدأ دریافت‌کننده).

> [!NOTE]
> طبق Payment Request API، اگر `PaymentRequest` در یک iframe با مبدأ متفاوت استفاده شود (مثلاً اگر `merchant.com` یک iframe از `psp.com` را تعبیه کند و `psp.com` بخواهد از `PaymentRequest` استفاده کند)، آن iframe باید خط‌مشی مجوزِ `payment` را تنظیم شده داشته باشد.

```js
const request = new PaymentRequest(
  [
    {
      supportedMethods: "secure-payment-confirmation",
      data: {
        // List of credential IDs obtained from the Account Provider.
        credentialIds,
        // The challenge is also obtained from the Account Provider.
        challenge: new Uint8Array(randomStringFromServer, (c) =>
          c.charCodeAt(0),
        ),
        instrument: {
          displayName: "Fancy Card ****1234",
          icon: "https://fancybank.com/card-art.png",
        },
        payeeOrigin: "https://merchant.com",
        timeout: 60000, // 1 minute
      },
    },
  ],
  {
    total: {
      label: "Total",
      amount: {
        currency: "USD",
        value: "5.00",
      },
    },
  },
);
try {
  // NOTE: canMakePayment() checks only public information for whether the SPC
  // call is valid. To preserve user privacy, it does not check whether any
  // passed credentials match the current device.
  const canMakePayment = await request.canMakePayment();
  if (!canMakePayment) {
    throw new Error("Cannot make payment");
  }
  const response = await request.show();
  await response.complete("success");
  // response.details is a PublicKeyCredential, with a clientDataJSON that
  // contains the transaction data for verification by the issuing bank.
  // send response.details to the issuing bank for verification
} catch (err) {
  // SPC cannot be used; merchant should fallback to traditional flows
}
```

پیش از شروع فرایند پرداخت، می‌توانید با فراخوانی متد ایستای {{domxref('PaymentRequest.securePaymentConfirmationAvailability_static', 'PaymentRequest.securePaymentConfirmationAvailability()')}} تعیین کنید که آیا SPC در دسترس است یا خیر. برای نمونه:

```js
async function spcSupport() {
  const support = await PaymentRequest.securePaymentConfirmationAvailability();
  if (support === "available") {
    // Commence SPC payment flow
  } else {
    // Fallback to traditional flows
  }
}
```

## مشخصات

{{Specifications}}

## همچنین ببینید

- [Payment Request API](/en-US/docs/Web/API/Payment_Request_API)
- [Payment Method Identifiers](/en-US/docs/Web/API/Payment_Request_API/Concepts#payment_method_identifiers)
- [Web Authentication](/en-US/docs/Web/API/Web_Authentication_API)
- [Secure Payment Confirmation Explainer](https://github.com/w3c/secure-payment-confirmation/blob/main/explainer.md)
- [Secure Payment Confirmation Scope](https://github.com/w3c/secure-payment-confirmation/blob/main/scope.md)
- نمودار کلی [جریان SPC در هنگام یک پرداخت](https://github.com/w3c/wpsig/blob/gh-pages/spc-general.png)
- [Secure Payment Confirmation Test Suite](https://wpt.fyi/results/secure-payment-confirmation?label=master&label=experimental&aligned)
- [Chrome developer documentation for SPC](https://developer.chrome.com/docs/payments/secure-payment-confirmation)
- [EMV® 3-D Secure (version 2.3)](https://www.emvco.com/emv-technologies/3-d-secure/)
- [EMV® Secure Remote Commerce (version 1.3)](https://www.emvco.com/emv-technologies/secure-remote-commerce/)