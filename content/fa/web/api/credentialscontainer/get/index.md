---
title: "CredentialsContainer: get() method"
---

---
title: "CredentialsContainer: get() method"
short-title: get()
slug: Web/API/CredentialsContainer/get
page-type: web-api-instance-method
browser-compat: api.CredentialsContainer.get

{{APIRef("Credential Management API")}}{{SecureContext_Header}}

متد **`get()`** از رابط {{domxref("CredentialsContainer")}} یک {{jsxref("Promise")}} برمی‌گرداند که با یک {{glossary("credential")}} واحد (اعتبارنامه) حل می‌شود؛ سپس می‌توان از این اعتبارنامه برای احراز هویت کاربر در یک وب‌سایت استفاده کرد.

این متد یک آرگومان اختیاری `options` می‌پذیرد که می‌تواند شامل موارد زیر باشد:

- ویژگی `mediation` که نشان می‌دهد کاربر چگونه و آیا باید در عملیات مشارکت کند. این ویژگی برای مثال مشخص می‌کند که آیا سایت می‌تواند با استفاده از یک اعتبارنامه ذخیره‌شده، کاربر را به‌صورت بی‌صدا (بدون دخالت کاربر) وارد سیستم کند یا خیر.
- ویژگی `signal` که امکان لغو عملیات را با استفاده از {{domxref("AbortController")}} فراهم می‌کند.
- یک یا چند ویژگی — `password`، `federated`، `identity`، `otp`، `publicKey` — که [انواع اعتبارنامه](/en-US/docs/Web/API/Credential_Management_API/Credential_types) درخواستی را مشخص می‌کنند. در صورت تنظیم، مقادیر این ویژگی‌ها شامل پارامترهایی است که مرورگر برای یافتن اعتبارنامه مناسب از نوع درخواستی به آن‌ها نیاز دارد.

این API همیشه با یک اعتبارنامه واحد یا `null` حل می‌شود. اگر چندین اعتبارنامه در دسترس باشد و دخالت کاربر مجاز باشد، مرورگر از کاربر می‌خواهد یک اعتبارنامه را انتخاب کند.

## نحو

```js-nolint
get()
get(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : شیئی که شامل گزینه‌های درخواست است. می‌تواند ویژگی‌های زیر را داشته باشد:
    - `mediation` {{optional_inline}}
      - : رشته‌ای که نشان می‌دهد کاربر چگونه در بازیابی اعتبارنامه مشارکت دارد. مقدار می‌تواند یکی از موارد زیر باشد:
        - `"conditional"`
          - : اعتبارنامه‌های کشف‌شده در یک کادر محاوره‌ای غیرحالتمند (non-modal) به‌همراه نشانه‌ای از مبدأ درخواست‌دهنده اعتبارنامه به کاربر نمایش داده می‌شوند. در عمل، این به معنای تکمیل خودکار اعتبارنامه‌های موجود است؛ برای جزئیات بیشتر درباره نحوه استفاده از آن، [رابط کاربری تکمیل خودکار (Autofill UI)](/en-US/docs/Web/API/Web_Authentication_API#autofill_ui) را ببینید.

        - `"optional"`
          - : اگر بتوان برای یک عملیات مشخص بدون دخالت کاربر اعتبارنامه را تحویل داد، این کار انجام می‌شود و ورود مجدد خودکار بدون دخالت کاربر ممکن می‌شود. اگر دخالت کاربر لازم باشد، عامل کاربر از کاربر می‌خواهد احراز هویت کند. این مقدار برای موقعیت‌هایی در نظر گرفته شده است که اطمینان معقولی دارید کاربر با دیدن کادر محاوره‌ای ورود، شگفت‌زده یا سردرگم نمی‌شود — مثلاً در سایتی که کاربران را به‌طور خودکار وارد سیستم نمی‌کند، وقتی کاربر به‌تازگی دکمه «ورود / ثبت‌نام» را کلیک کرده است.

        - `"required"`
          - : همیشه از کاربر خواسته می‌شود احراز هویت کند. این مقدار برای موقعیت‌هایی در نظر گرفته شده است که می‌خواهید احراز هویت کاربر را اجباری کنید — مثلاً وقتی می‌خواهید کاربر هنگام انجام یک عملیات حساس (مانند تأیید پرداخت با کارت اعتباری) دوباره احراز هویت کند، یا هنگام تغییر کاربر.

        - `"silent"`
          - : از کاربر خواسته نمی‌شود احراز هویت کند. عامل کاربر به‌طور خودکار کاربر را دوباره احراز هویت کرده و در صورت امکان وارد سیستم می‌کند. اگر رضایت لازم باشد، پرامیس با `null` حل می‌شود. این مقدار برای موقعیت‌هایی در نظر گرفته شده است که می‌خواهید هنگام بازدید کاربر از یک برنامه وب، در صورت امکان به‌طور خودکار او را وارد کنید؛ اما اگر این امکان وجود نداشت، نمی‌خواهید یک کادر محاوره‌ای ورود گیج‌کننده به او نمایش دهید. در عوض، باید منتظر بمانید تا کاربر صریحاً دکمه «ورود / ثبت‌نام» را کلیک کند.

        مقدار پیش‌فرض `"optional"` است.

        > [!NOTE]
        > در مورد یک درخواست [احراز هویت فدرال (FedCM API)](/en-US/docs/Web/API/FedCM_API)، مقدار `mediation` برابر با `optional` یا `silent` ممکن است منجر به تلاش برای [بازاحراز هویت خودکار](/en-US/docs/Web/API/FedCM_API/RP_sign-in#auto-reauthentication) شود. این که چنین اتفاقی افتاده است یا نه، از طریق پارامتر [`is_auto_selected`](/en-US/docs/Web/API/FedCM_API/IDP_integration#is_auto_selected) که هنگام اعتبارسنجی به `id_assertion_endpoint` ارائه‌دهنده هویت (IdP) ارسال می‌شود، به IdP اطلاع داده می‌شود و از طریق ویژگی {{domxref("IdentityCredential.isAutoSelected")}} به طرف معتمد (RP) منتقل می‌شود. این موضوع برای ارزیابی عملکرد، الزامات امنیتی (IdP ممکن است بخواهد درخواست‌های بازاحراز هویت خودکار را رد کند و همیشه به دخالت کاربر نیاز داشته باشد) و تجربه کاربری عمومی (یک IdP یا RP ممکن است بخواهد تجربه کاربری متفاوتی برای ورود خودکار و غیرخودکار ارائه دهد) مفید است.

    - `signal` {{optional_inline}}
      - : یک نمونه از شیء {{domxref("AbortSignal")}} که امکان لغو یک عملیات در حال انجام `get()` را فراهم می‌کند. یک عملیات لغوشده ممکن است به‌طور عادی کامل شود (معمولاً اگر لغو پس از پایان عملیات دریافت شده باشد) یا با دلیل سیگنال رد شود (که به‌طور پیش‌فرض یک {{domxref("DOMException")}} از نوع `AbortError` است، یا اگر هنگام فراخوانی {{domxref("AbortController.abort", "abort()")}} مقدار سفارشی ارائه شده باشد، همان مقدار سفارشی است).

    - `password` {{optional_inline}}
      - : این گزینه از مرورگر می‌خواهد یک [رمز عبور](/en-US/docs/Web/API/Credential_Management_API/Credential_types#passwords) ذخیره‌شده را به‌عنوان یک شیء {{domxref("PasswordCredential")}} بازیابی کند. مقدار آن یک مقدار بولی است.

    - `identity` {{optional_inline}}
      - : این گزینه از مرورگر می‌خواهد با استفاده از [Federated Credential Management API](/en-US/docs/Web/API/FedCM_API)، یک [اعتبارنامه هویت فدرال](/en-US/docs/Web/API/Credential_Management_API/Credential_types#federated_identity_credentials) را به‌عنوان یک شیء {{domxref("IdentityCredential")}} بازیابی کند.

        مقدار این گزینه یک شیء {{domxref("IdentityCredentialRequestOptions")}} است که شامل جزئیات ارائه‌دهندگان هویت خاصی است که وب‌سایت می‌خواهد از آن‌ها استفاده کند.

    - `federated` {{optional_inline}}
      - : این گزینه از مرورگر می‌خواهد یک [اعتبارنامه هویت فدرال](/en-US/docs/Web/API/Credential_Management_API/Credential_types#federated_identity_credentials) را به‌عنوان یک شیء {{domxref("FederatedCredential")}} بازیابی کند. این رابط اکنون منسوخ شده است و توسعه‌دهندگان باید در صورت وجود، ترجیح دهند از گزینه `identity` استفاده کنند.

        مقدار این گزینه یک شیء با ویژگی‌های زیر است:
        - `protocols`
          - : آرایه‌ای از رشته‌ها که پروتکل‌های ارائه‌دهندگان هویت فدرال اعتبارنامه‌های درخواستی را نشان می‌دهد (مثلاً `"openidconnect"`).
        - `providers`
          - : آرایه‌ای از رشته‌ها که ارائه‌دهندگان هویت فدرال اعتبارنامه‌ها را نشان می‌دهد (مثلاً `"https://www.facebook.com"` یا `"https://accounts.google.com"`).

    - `otp` {{optional_inline}}
      - : این گزینه از مرورگر می‌خواهد یک [رمز یکبارمصرف (OTP)](/en-US/docs/Web/API/Credential_Management_API/Credential_types#one-time_passwords) را به‌عنوان یک شیء {{domxref("OTPCredential")}} بازیابی کند.

        مقدار این گزینه آرایه‌ای از رشته‌ها است که فقط می‌تواند حاوی مقدار رشته‌ای `"sms"` باشد.

    - `publicKey` {{optional_inline}}
      - : این گزینه از مرورگر می‌خواهد یک [تأییده‌ای که با Web Authentication API امضا شده است](/en-US/docs/Web/API/Credential_Management_API/Credential_types#web_authentication_assertions) را به‌عنوان یک {{domxref("PublicKeyCredential")}} بازیابی کند.

        مقدار این گزینه یک شیء {{domxref("PublicKeyCredentialRequestOptions")}} است.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با یکی از زیرکلاس‌های زیر از {{domxref("Credential")}} حل می‌شود:

- {{domxref("PasswordCredential")}}
- {{domxref("IdentityCredential")}}
- {{domxref("FederatedCredential")}}
- {{domxref("OTPCredential")}}
- {{domxref("PublicKeyCredential")}}

اگر [mediation شرطی](#mediation) در فراخوانی `get()` مشخص شده باشد، رابط کاربری مرورگر نمایش داده می‌شود و پرامیس تا زمانی که کاربر یک حساب کاربری را از میان پیشنهادهای تکمیل خودکار موجود برای ورود انتخاب کند، در حالت معلق (pending) باقی می‌ماند:

- اگر کاربر سپس ژستی خارج از کادر محاوره‌ای رابط کاربری مرورگر انجام دهد، آن کادر بدون اینکه پرامیس حل یا رد شود و بدون ایجاد شرایط خطای قابل مشاهده برای کاربر بسته می‌شود.
- اگر کاربر یک اعتبارنامه را انتخاب کند، {{domxref("PublicKeyCredential")}} مربوطه به فراخواننده بازگردانده می‌شود.

اگر نتوان یک اعتبارنامه واحد را به‌طور بدون ابهام به دست آورد، پرامیس با `null` حل می‌شود.

### استثناها

- `AbortError` {{domxref("DOMException")}}
  - : درخواست با فراخوانی متد {{domxref("AbortController.abort", "abort()")}} از {{domxref("AbortController")}} مرتبط با گزینه [`signal`](#signal) این متد لغو شد. توجه داشته باشید که اگر فراخواننده `abort()` یک آرگومان `reason` ارائه کرده باشد، `get()` به‌جای یک استثنای `AbortController`، با مقدار `reason` رد می‌شود.

- `TimeoutError` {{domxref("DOMException")}}
  - : درخواست به دلیل یک وقفه زمانی تعیین‌شده با {{domxref("AbortSignal.timeout_static", "AbortSignal.timeout()")}} به‌طور خودکار لغو شد.

- {{domxref("IdentityCredentialError")}}
  - : هنگام درخواست یک {{domxref("IdentityCredential")}}، درخواست به [endpoint تأیید هویت](/en-US/docs/Web/API/FedCM_API/IDP_integration#the_id_assertion_endpoint) نمی‌تواند احراز هویت را اعتبارسنجی کند و با یک پاسخ خطا حاوی اطلاعاتی درباره دلیل آن رد می‌شود.

- `NetworkError` {{domxref("DOMException")}}
  - : هنگام درخواست یک {{domxref("IdentityCredential")}}، {{glossary("identity provider")}} (IdP) ظرف ۶۰ ثانیه پاسخ نداد، اعتبارنامه‌های ارائه‌شده معتبر / یافت نشدند، یا وضعیت ورود مرورگر برای IdP روی `"logged-out"` تنظیم شده است (برای اطلاعات بیشتر درباره وضعیت ورود FedCM، به [به‌روزرسانی وضعیت ورود با استفاده از Login Status API](/en-US/docs/Web/API/FedCM_API/IDP_integration#update_login_status_using_the_login_status_api) مراجعه کنید). در حالت اخیر، ممکن است در رد کردن درخواست تأخیری وجود داشته باشد تا از افشای وضعیت ورود IdP به RP جلوگیری شود.

- `NotAllowedError` {{domxref("DOMException")}}
  - : در یکی از شرایط زیر صادر می‌شود:
    - کاربر درخواست را لغو کرد.

    - استفاده از این API توسط یکی از [خط‌مشی‌های مجوز (Permissions Policy)](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) زیر مسدود شده است:
      - {{HTTPHeader("Permissions-Policy/identity-credentials-get","identity-credentials-get")}}
      - {{HTTPHeader("Permissions-Policy/publickey-credentials-get","publickey-credentials-get")}}
      - {{HTTPHeader("Permissions-Policy/otp-credentials","otp-credentials")}}

    - مبدأ فراخواننده یک [مبدأ ناشفاف (opaque origin)](/en-US/docs/Web/HTTP/Reference/Headers/Origin#null) است.

- `SecurityError` {{domxref("DOMException")}}
  - : دامنه فراخواننده یک دامنه معتبر نیست.

## مثال‌ها

### بازیابی یک اعتبارنامه هویت فدرال

طرف‌های معتمد (Relying parties) می‌توانند `get()` را با گزینه `identity` فراخوانی کنند تا از کاربران بخواهند با استفاده از فدراسیون هویت، از طریق یک ارائه‌دهنده هویت (IdP) وارد طرف معتمد شوند. یک درخواست معمولی به این شکل است:

```js
async function signIn() {
  const identityCredential = await navigator.credentials.get({
    identity: {
      providers: [
        {
          configURL: "https://accounts.idp.example/config.json",
          clientId: "********",
          params: {/* IdP-specific parameters */},
        },
      ],
    },
  });
}
```

برای جزئیات بیشتر درباره نحوه عملکرد این کار، به [Federated Credential Management (FedCM) API](/en-US/docs/Web/API/FedCM_API) مراجعه کنید. این فراخوانی جریان ورود به سیستم را که در [جریان ورود FedCM](/en-US/docs/Web/API/FedCM_API/RP_sign-in#fedcm_sign-in_flow) توضیح داده شده است آغاز می‌کند.

یک فراخوانی مشابه که شامل افزونه‌های `context` و `loginHint` است به این شکل خواهد بود:

```js
async function signIn() {
  const identityCredential = await navigator.credentials.get({
    identity: {
      context: "signup",
      providers: [
        {
          configURL: "https://accounts.idp.example/config.json",
          clientId: "********",
          params: {/* IdP-specific parameters */},
          loginHint: "user1@example.com",
        },
      ],
    },
  });
}
```

اگر IdP نتواند درخواست ارسال‌شده به [endpoint تأیید هویت](/en-US/docs/Web/API/FedCM_API/IDP_integration#the_id_assertion_endpoint) را اعتبارسنجی کند، پرامیس بازگشتی از `CredentialsContainer.get()` را رد می‌کند:

```js
async function signIn() {
  try {
    const identityCredential = await navigator.credentials.get({
      identity: {
        providers: [
          {
            configURL: "https://accounts.idp.example/config.json",
            clientId: "********",
            params: {/* IdP-specific parameters */},
          },
        ],
      },
    });
  } catch (e) {
    // Handle the error in some way, for example provide information
    // to help the user succeed in a future sign-in attempt
