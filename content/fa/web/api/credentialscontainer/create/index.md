---
title: "CredentialsContainer: create() method"
short-title: create()
slug: Web/API/CredentialsContainer/create
page-type: web-api-instance-method
browser-compat: api.CredentialsContainer.create
---

{{APIRef("Credential Management API")}}{{SecureContext_Header}}

متد **`create()`** از رابط {{domxref("CredentialsContainer")}} یک {{glossary("credential", "اعتبارنامه")}} جدید ایجاد می‌کند که می‌تواند ذخیره شود و بعداً با استفاده از متد {{domxref("CredentialsContainer.get", "navigator.credentials.get()")}} بازیابی شود. سپس اعتبارنامه بازیابی‌شده می‌تواند توسط یک وب‌سایت برای احراز هویت کاربر استفاده شود.

این متد از سه نوع اعتبارنامه مختلف پشتیبانی می‌کند:

- یک اعتبارنامه رمز عبور، که به کاربر امکان می‌دهد با استفاده از رمز عبور وارد شود.
- یک اعتبارنامه فدرال، که به کاربر امکان می‌دهد با استفاده از یک ارائه‌دهنده هویت فدرال وارد شود.
- یک اعتبارنامه کلید عمومی، که به کاربر امکان می‌دهد با یک احرازکننده مانند یک دستگاه خواننده بیومتریک تعبیه‌شده در سکو یا یک توکن سخت‌افزاری قابل جابه‌جایی وارد شود.

توجه داشته باشید که [Federated Credential Management API (FedCM)](/en-US/docs/Web/API/FedCM_API) جایگزین نوع اعتبارنامه فدرال شده است.

## Syntax

```js-nolint
create()
create(options)
```

### Parameters

- `options` {{optional_inline}}
  - : یک شیء که شامل گزینه‌هایی برای شیء `Credentials` درخواستی جدید است. می‌تواند شامل ویژگی‌های زیر باشد:
    - `signal` {{optional_inline}}
      - : یک نمونه از شیء {{domxref("AbortSignal")}} که امکان لغو یک عملیات `create()` در حال انجام را فراهم می‌کند. یک عملیات لغو شده ممکن است به طور عادی کامل شود (به طور کلی اگر لغو پس از اتمام عملیات دریافت شده باشد) یا با یک `AbortError` {{domxref("DOMException")}} رد شود.

    هر یک از ویژگی‌های زیر نشان‌دهنده یک _نوع اعتبارنامه_ در حال ایجاد است. فقط یکی از آنها باید مشخص شود:
    - `federated` {{optional_inline}}
      - : یک شیء {{domxref("FederatedCredentialInit")}} که شامل الزامات ایجاد یک اعتبارنامه ارائه‌دهنده هویت فدرال است.
    - `password` {{optional_inline}}
      - : یک شیء {{domxref("PasswordCredentialInit")}} که شامل الزامات ایجاد یک اعتبارنامه رمز عبور است.
    - `publicKey` {{optional_inline}}
      - : یک شیء {{domxref("PublicKeyCredentialCreationOptions")}} که شامل الزامات ایجاد یک اعتبارنامه کلید عمومی است. باعث می‌شود فراخوانی `create()` از عامل کاربر بخواهد که اعتبارنامه جدیدی را از طریق یک احرازکننده ایجاد کند - یا برای ثبت یک حساب جدید یا برای مرتبط کردن یک جفت کلید نامتقارن جدید با یک حساب موجود.

        > [!NOTE]
        > استفاده از `create()` با پارامتر `publicKey` ممکن است توسط یک {{HTTPHeader("Permissions-Policy/publickey-credentials-create","publickey-credentials-create")}} [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) تنظیم شده در سرور شما مسدود شود.

### Return value

یک {{jsxref("Promise")}} که با یکی از موارد زیر حل می‌شود:

- یک {{domxref("FederatedCredential")}}، اگر نوع اعتبارنامه `federated` بود.
- یک {{domxref("PasswordCredential")}}، اگر نوع اعتبارنامه `password` بود.
- یک {{domxref("PublicKeyCredential")}}، اگر نوع اعتبارنامه `publicKey` بود.

اگر هیچ شیء اعتبارنامه‌ای نتواند ایجاد شود، پرامیس با `null` حل می‌شود.

### Exceptions

- {{jsxref("TypeError")}}
  - : در مورد درخواست ایجاد {{domxref("PasswordCredential")}}، `id`، `origin` یا `password` ارائه نشده‌اند (خالی هستند).
- `NotAllowedError` {{domxref("DOMException")}}
  - : دلایل احتمالی عبارتند از:
    - استفاده توسط یک {{HTTPHeader("Permissions-Policy/publickey-credentials-create","publickey-credentials-create")}} [Permissions Policy](/en-US/docs/Web/HTTP/Guides/Permissions_Policy) مسدود شده است.
    - تابع در یک مبدأ متقابل فراخوانی می‌شود اما ویژگی [`allow`](/en-US/docs/Web/HTML/Reference/Elements/iframe#allow) iframe خط مشی {{HTTPHeader("Permissions-Policy/publickey-credentials-create","publickey-credentials-create")}} مناسب را تنظیم نکرده است.
    - تابع در یک مبدأ متقابل فراخوانی می‌شود و `<iframe>` فاقد {{glossary("transient activation", "فعالیت گذرا")}} است.
    - تابع سعی در ایجاد یک [اعتبارنامه قابل کشف](/en-US/docs/Web/API/Web_Authentication_API#discoverable_and_non-discoverable_credentials) دارد ([`residentKey`](/en-US/docs/Web/API/PublicKeyCredentialCreationOptions#residentkey) در گزینه {{domxref("PublicKeyCredentialCreationOptions")}} فراخوانی `create()` روی `required` تنظیم شده است)، اما کاربر یک احرازکننده ندارد که از اعتبارنامه‌های قابل کشف پشتیبانی کند.
- `AbortError` {{domxref("DOMException")}}
  - : عملیات لغو شد.

## Examples

### Creating a password credential

این مثال یک اعتبارنامه رمز عبور از یک شیء {{domxref("PasswordCredentialInit")}} ایجاد می‌کند.

```js
const credInit = {
  id: "serpent1234", // "username" in a typical username/password pair
  name: "Serpentina", // display name for credential
  origin: "https://example.org",
  password: "the last visible dog",
};

const makeCredential = document.querySelector("#make-credential");

makeCredential.addEventListener("click", async () => {
  const cred = await navigator.credentials.create({
    password: credInit,
  });
  console.log(cred.name);
  // Serpentina
  console.log(cred.id);
  // serpent1234
  console.log(cred.password);
  // the last visible dog
});
```

### Creating a federated credential

این مثال یک اعتبارنامه فدرال از یک شیء {{domxref("FederatedCredentialInit")}} ایجاد می‌کند.

```js
const credInit = {
  id: "1234",
  name: "Serpentina",
  origin: "https://example.org",
  protocol: "openidconnect",
  provider: "https://provider.example.org",
};

const makeCredential = document.querySelector("#make-credential");

makeCredential.addEventListener("click", async () => {
  const cred = await navigator.credentials.create({
    federated: credInit,
  });
  console.log(cred.name);
  console.log(cred.provider);
});
```

### Creating a public key credential

این مثال یک اعتبارنامه کلید عمومی از یک شیء {{domxref("PublicKeyCredentialCreationOptions")}} ایجاد می‌کند.

```js
const publicKey = {
  challenge: challengeFromServer,
  rp: { id: "acme.com", name: "ACME Corporation" },
  user: {
    id: new Uint8Array([79, 252, 83, 72, 214, 7, 89, 26]),
    name: "jamiedoe",
    displayName: "Jamie Doe",
  },
  pubKeyCredParams: [{ type: "public-key", alg: -7 }],
};

const publicKeyCredential = await navigator.credentials.create({ publicKey });
```

فراخوانی `create()`، در صورت موفقیت، یک پرامیس برمی‌گرداند که با یک نمونه از شیء {{domxref("PublicKeyCredential")}} حل می‌شود که نمایانگر یک اعتبارنامه کلید عمومی است که می‌تواند بعداً برای احراز هویت کاربر از طریق یک فراخوانی WebAuthn {{domxref("CredentialsContainer.get()", "get()")}} استفاده شود. ویژگی {{domxref("PublicKeyCredential.response")}} آن شامل یک شیء {{domxref("AuthenticatorAttestationResponse")}} است که دسترسی به چندین قطعه اطلاعات مفید از جمله داده‌های احرازکننده، کلید عمومی، مکانیسم‌های انتقال و موارد دیگر را فراهم می‌کند.

```js
navigator.credentials.create({ publicKey }).then((publicKeyCredential) => {
  const response = publicKeyCredential.response;

  // Access attestationObject ArrayBuffer
  const attestationObj = response.attestationObject;

  // Access client JSON
  const clientJSON = response.clientDataJSON;

  // Return authenticator data ArrayBuffer
  const authenticatorData = response.getAuthenticatorData();

  // Return public key ArrayBuffer
  const pk = response.getPublicKey();

  // Return public key algorithm identifier
  const pkAlgo = response.getPublicKeyAlgorithm();

  // Return permissible transports array
  const transports = response.getTransports();
});
```

برخی از این داده‌ها باید برای عملیات‌های احراز هویت آینده علیه این اعتبارنامه در سرور ذخیره شوند - به عنوان مثال کلید عمومی، الگوریتم استفاده شده و مجوزهای حمل و نقل.

> [!NOTE]
> برای اطلاعات بیشتر در مورد نحوه عملکرد جریان کلی، به [Creating a key pair and registering a user](/en-US/docs/Web/API/Web_Authentication_API#creating_a_key_pair_and_registering_a_user) مراجعه کنید.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}