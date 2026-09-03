---
title: "PublicKeyCredential: getClientCapabilities() static method"
short-title: getClientCapabilities()
slug: Web/API/PublicKeyCredential/getClientCapabilities_static
page-type: web-api-static-method
browser-compat: api.PublicKeyCredential.getClientCapabilities_static
---

{{APIRef("Web Authentication API")}}{{securecontext_header}}

متد ایستای **`getClientCapabilities()`** از رابط {{domxref("PublicKeyCredential")}} یک {{jsxref("Promise")}} برمی‌گرداند که با یک شیء resolve می‌شود و می‌توان از آن برای بررسی پشتیبانی یا عدم پشتیبانی از قابلیت‌های خاص کلاینت WebAuthn و [افزونه‌ها](/en-US/docs/Web/API/Web_Authentication_API/WebAuthn_extensions) استفاده کرد.

یک طرف اتکا (relying party یا RP) می‌تواند از این اطلاعات استفاده کند تا رابط‌های کاربری و فرایندهای ورود و ثبت‌نام خود را به‌شکل مناسبی سفارشی کند.

## Syntax

```js-nolint
PublicKeyCredential.getClientCapabilities()
```

### Parameters

هیچ.

### Return value

یک {{jsxref("Promise")}} که به شیءای resolve می‌شود؛ نام ویژگی‌های این شیء رشته‌های قابلیت کلاینت هستند و مقادیر آن‌ها بولین‌هایی هستند که نشان می‌دهند قابلیت یا افزونهٔ مربوطه پشتیبانی می‌شود یا خیر.

رشته‌های قابلیت کلاینت WebAuthn عبارت‌اند از:

- `"conditionalCreate"`
  - : کلاینت قادر به ایجاد [اعتبارنامه‌های قابل‌کشف](/en-US/docs/Web/API/Web_Authentication_API#discoverable_and_non-discoverable_credentials) است.
- `"conditionalGet"`
  - : کلاینت از [میانجیگری شرطی](/en-US/docs/Web/API/Web_Authentication_API#autofill_ui) پشتیبانی می‌کند. این قابلیت معادل این است که [`isConditionalMediationAvailable()`](/en-US/docs/Web/API/PublicKeyCredential/isConditionalMediationAvailable_static) با مقدار `true` resolve شود.
- `"hybridTransport"`
  - : کلاینت استفاده از ترابرد [هیبرید](/en-US/docs/Web/API/AuthenticatorAttestationResponse/getTransports#hybrid) را پشتیبانی می‌کند. این به آن معناست که کلاینت می‌تواند از احرازکننده‌هایی استفاده کند که به بلوتوث، NFC یا USB متکی هستند.
- `"passkeyPlatformAuthenticator"`
  - : کلاینت امکان استفاده از یک احرازکنندهٔ passkey را فراهم می‌کند که از سازوکارهای {{glossary("multi-factor authentication")}} مانند PIN یا بررسی زیست‌سنجی پشتیبانی می‌کند. این احرازکننده می‌تواند بخشی از همان پلتفرم (دستگاه) کلاینت باشد یا از طریق یک ترابرد هیبرید مانند بلوتوث یا USB متصل شود. اعتبارنامه‌ها روی احرازکننده ذخیره می‌شوند. به [راهنمای توسعه‌دهندگان passkey برای طرف‌های اتکا](https://developers.google.com/identity/passkeys/developer-guides) مراجعه کنید.
- `userVerifyingPlatformAuthenticator`
  - : کلاینت یک احرازکنندهٔ پلتفرمی (بخشی از همان دستگاه) دارد که از سازوکارهای {{glossary("multi-factor authentication")}} مانند PIN یا بررسی زیست‌سنجی پشتیبانی می‌کند. اعتبارنامه‌ها ممکن است روی RP یا روی احرازکننده ذخیره شوند.
- `relatedOrigins`
  - : کلاینت از [درخواست‌های مبدأ مرتبط](https://web.dev/articles/webauthn-related-origin-requests) پشتیبانی می‌کند. این کلاینت‌ها اجازه می‌دهند از یک passkey در چندین سایتی که مبدأ یکسانی دارند استفاده شود.
- `signalAllAcceptedCredentials`
  - : کلاینت از متد ایستای [`PublicKeyCredential.signalAllAcceptedCredentials()`](/en-US/docs/Web/API/PublicKeyCredential/signalAllAcceptedCredentials_static) پشتیبانی می‌کند. اگر پشتیبانی نشود، فرایندهای RP باید از کاربر بخواهند که اعتبارنامه‌ها را به‌صورت دستی روی احرازکننده حذف کند.
- `signalCurrentUserDetails`
  - : کلاینت از متد ایستای [`PublicKeyCredential.signalCurrentUserDetails()`](/en-US/docs/Web/API/PublicKeyCredential/signalCurrentUserDetails_static) پشتیبانی می‌کند. اگر پشتیبانی نشود، فرایندهای RP باید از کاربر بخواهند که جزئیات کاربر را به‌صورت دستی روی احرازکننده به‌روزرسانی کند.
- `signalUnknownCredential`
  - : کلاینت از متد ایستای [`PublicKeyCredential.signalUnknownCredential()`](/en-US/docs/Web/API/PublicKeyCredential/signalUnknownCredential_static) پشتیبانی می‌کند. اگر پشتیبانی نشود، فرایندهای RP باید از کاربر بخواهند که اعتبارنامه‌ها را به‌صورت دستی از احرازکننده حذف کند.

رشته‌های مربوط به [افزونه‌های وب](/en-US/docs/Web/API/Web_Authentication_API/WebAuthn_extensions) با افزودن پیشوند `extension:` به [شناسهٔ افزونه](/en-US/docs/Web/API/Web_Authentication_API/WebAuthn_extensions#available_extensions) قالب‌بندی می‌شوند. برای مثال، برای بررسی پشتیبانی از [افزونهٔ `appid`](/en-US/docs/Web/API/Web_Authentication_API/WebAuthn_extensions#appid) می‌توان از کلید `extension:appid` استفاده کرد.

### Exceptions

{{jsxref("Promise")}} بازگشتی ممکن است با مقادیر زیر رد شود:

- `SecurityError` {{domxref("DOMException")}}
  - : دامنهٔ طرف اتکا (RP) معتبر نیست.

## Description

`getClientCapabilities()` به شما امکان می‌دهد بررسی کنید که آیا یک قابلیت یا افزونهٔ مشخص پشتیبانی می‌شود یا خیر و از این اطلاعات برای ارائهٔ تجربهٔ کاربری مناسب استفاده کنید.

برای مثال، پشتیبانی از قابلیت `userVerifyingPlatformAuthenticator` نشان می‌دهد که امکانات زیست‌سنجی مانند حسگر اثر انگشت مجاز هستند. یک برنامهٔ وب می‌تواند در صورت پشتیبانی از این قابلیت، آیکون اثر انگشت نمایش دهد و در غیر این صورت، یک فیلد ورود رمز عبور نشان دهد. اگر ورود با زیست‌سنجی ضروری باشد، برنامه می‌تواند به‌جای آن اطلاع‌رسانی کند که این مرورگر یا دستگاه امکان احراز هویت کاربر را در آن سایت ندارد. به‌طور مشابه، `conditionalGet` نشان می‌دهد که کلاینت هنگام ورود کاربر از میانجیگری شرطی پشتیبانی می‌کند؛ یعنی مرورگر می‌تواند اعتبارنامه‌های قابل‌کشف را در فرم ورود (مثلاً در یک فیلد متنی با تکمیل خودکار یا یک فهرست کشویی) به‌صورت خودکار ارائه دهد و در کنار آن‌ها دکمهٔ ورود را نیز نمایش دهد.

اگر مقدار یک قابلیت در شیء بازگشتی وجود داشته باشد، `true` به این معناست که آن قابلیت در حال حاضر پشتیبانی می‌شود و `false` به این معناست که پشتیبانی نمی‌شود. با این حال، اگر کلید مربوط به یک قابلیت خاص وجود نداشته باشد، نمی‌توان هیچ فرضی دربارهٔ در دسترس بودن ویژگی مرتبط داشت.

برای افزونه‌ها نیز همین قاعده برقرار است. توجه داشته باشید که حتی اگر افزونه‌ای توسط کلاینت پشتیبانی شود، ممکن است یک احرازکنندهٔ خاص از آن افزونه پشتیبانی نکند؛ بنابراین RPها نباید این را تضمینی برای انجام مراحل پردازش سمت احرازکننده برای آن افزونه بدانند. اگر کلید مربوط به یک افزونه وجود نداشته باشد، RP نمی‌تواند فرض کند که مراحل پردازش سمت کلاینت برای آن افزونه توسط این کلاینت انجام می‌شود یا اینکه افزونه به احرازکننده ارسال خواهد شد.

## Examples

### بررسی همهٔ قابلیت‌ها

این مثال نشان می‌دهد که چگونه شیء قابلیت‌ها را دریافت کرده و روی مقادیر آن پیمایش کنید.

```html hidden
<pre id="log"></pre>
```

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

```css hidden
#log {
  height: 230px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

#### JavaScript

ابتدا منتظر `getClientCapabilities()` می‌مانیم تا شیء حاوی قابلیت‌ها را دریافت کنیم. سپس روی شیء پیمایش می‌کنیم و نتیجه را ثبت می‌کنیم (کد ثبت لاگ در اینجا نمایش داده نشده است):

```js
async function checkClientCapabilities() {
  const capabilities = await PublicKeyCredential.getClientCapabilities();

  if (capabilities) {
    log("Client Capabilities:");

    for (const [key, value] of Object.entries(capabilities)) {
      log(` ${key}: ${value}`);
    }
  }
}
```

قبل از فراخوانی تابع، بررسی می‌کنیم که تعریف شده باشد و نتیجه را ثبت می‌کنیم.

```js
// Call the function to check capabilities.
if (PublicKeyCredential.getClientCapabilities) {
  checkClientCapabilities();
} else {
  log(
    "PublicKeyCredential.getClientCapabilities() is not supported on this browser.",
  );
}
```

#### Result

{{EmbedLiveSample("Check all capabilities", "", "280")}}

### بررسی احرازکنندهٔ پلتفرمی تأییدکنندهٔ کاربر

این مثال یک قابلیت مشخص، یعنی `userVerifyingPlatformAuthenticator` را بررسی می‌کند. یک برنامهٔ واقعی ممکن است از نتیجه برای پیکربندی رابط کاربری استفاده کند.

```html hidden
<pre id="log"></pre>
```

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

```css hidden
#log {
  height: 40px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

#### JavaScript

کد شبیه به مثال قبلی است، با این تفاوت که یک قابلیت مشخصِ بازگشتی را بررسی می‌کنیم و برای مدیریت حالتی که `getClientCapabilities()` پشتیبانی نمی‌شود از `try...catch` استفاده می‌کنیم.

```js
checkIsUserVerifyingPlatformAuthenticatorAvailable();

async function checkIsUserVerifyingPlatformAuthenticatorAvailable() {
  try {
    const capabilities = await PublicKeyCredential.getClientCapabilities();

    if (capabilities.userVerifyingPlatformAuthenticator) {
      log("Biometric login supported");
    } else {
      log("Biometric login not supported. Do password.");
    }
  } catch (error) {
    if (error instanceof TypeError) {
      log(
        "PublicKeyCredential.getClientCapabilities() is not supported on this browser.",
      );
    } else {
      log(`Unexpected error: ${error}`);
    }
  }
}
```

توجه کنید که در اینجا نتیجهٔ بررسی را ثبت می‌کنیم. در یک برنامهٔ واقعی، ممکن است رابط کاربری را به‌روزرسانی کنیم تا گزینه‌های مناسب برای تأیید هویت کاربر نمایش داده شود.

#### Result

گزارش زیر یا رشته‌ای را نشان می‌دهد که بیانگر پشتیبانی نشدن این متد است، یا رشته‌ای که مشخص می‌کند ورود با زیست‌سنجی یا رمز عبور پشتیبانی می‌شود.

{{EmbedLiveSample("Test for user verifying platform authenticator", "", "90")}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Web Authentication API](/en-US/docs/Web/API/Web_Authentication_API)