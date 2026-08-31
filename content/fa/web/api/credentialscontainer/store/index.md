---
title: "CredentialsContainer: store() method"
short-title: store()
slug: Web/API/CredentialsContainer/store
page-type: web-api-instance-method
browser-compat: api.CredentialsContainer.store
---

{{APIRef("Credential Management API")}}{{SecureContext_Header}}

متد **`store()`** از رابط {{domxref("CredentialsContainer")}} مجموعه‌ای از اعتبارنامه‌ها را برای کاربر درون یک نمونه {{domxref("Credential")}} ذخیره می‌کند و آن را در قالب یک {{jsxref("Promise")}} برمی‌گرداند.

> [!NOTE]
> این متد به زمینه‌های سطح بالا (top-level contexts) محدود است. فراخوانی آن درون یک عنصر
> `<iframe>` بدون اثر انجام می‌شود.

## Syntax

```js-nolint
store(credentials)
```

### Parameters

- `credentials`
  - : یک نمونه معتبر از {{domxref("Credential")}}.

### Return value

یک {{jsxref("Promise")}} که به `undefined` resolve می‌شود.

### Exceptions

- `NotAllowedError` {{domxref("DOMException")}}
  - : زمانی پرتاب می‌شود که اعتبارنامه‌ای از همان نوع اعتبارنامه فعلی در حال عملیات وجود داشته باشد.

## Examples

### ذخیره اعتبارنامه رمز عبور در احراز هویت موفق

این کد پس از ثبت‌نام یا ورود کاربر و تأیید صحت اعتبارنامه توسط سرور اجرا می‌شود.

```js
// Check if the browser supports password credentials (and the Credential Management API)
if ("PasswordCredential" in window) {
  let credential = new PasswordCredential({
    id: "example-username",
    name: "Carina Anand", // In case of a login, the name comes from the server.
    password: "correct horse battery staple",
  });

  navigator.credentials.store(credential).then(
    () => {
      console.info("Credential stored in the user agent's credential manager.");
    },
    (err) => {
      console.error("Error while storing the credential: ", err);
    },
  );
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}