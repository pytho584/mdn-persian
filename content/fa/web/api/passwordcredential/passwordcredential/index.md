---
title: "PasswordCredential: PasswordCredential() constructor"
---

---
title: "PasswordCredential: PasswordCredential() constructor"
short-title: PasswordCredential()
slug: Web/API/PasswordCredential/PasswordCredential
page-type: web-api-constructor
status:
  - experimental
browser-compat: api.PasswordCredential.PasswordCredential
---

{{APIRef("Credential Management API")}}{{SeeCompatTable}}{{SecureContext_Header}}

سازنده **`PasswordCredential()`** یک شیء {{domxref("PasswordCredential")}} جدید ایجاد می‌کند.

## Syntax

```js-nolint
new PasswordCredential(data)
new PasswordCredential(form)
```

### پارامترها

یکی از موارد زیر:

- `data`
  - : یک شیء با ویژگی‌های زیر:
    - `iconURL` {{optional_inline}}
      - : یک رشته که نشان‌دهنده URL یک آیکون یا آواتار است که باید با این اعتبارنامه (credential) مرتبط شود.
    - `id`
      - : یک رشته که بخش نام کاربری (username) از ترکیب نام کاربری/رمز عبور را نشان می‌دهد.
    - `name` {{optional_inline}}
      - : یک رشته که یک نام قابل فهم برای انسان را نشان می‌دهد که با این اعتبارنامه مرتبط است و برای کمک به کاربر در انتخاب این اعتبارنامه در یک رابط کاربری طراحی شده است.
    - `origin`
      - : یک رشته که خاستگاه (origin) اعتبارنامه را نشان می‌دهد. اشیاء {{domxref("PasswordCredential")}} به خاستگاه وابسته هستند، به این معنی که فقط در همان خاستگاه مشخص‌شده قابل استفاده خواهند بود.
    - `password`
      - : یک رشته که رمز عبور اعتبارنامه را نشان می‌دهد.

- `form`
  - : یک ارجاع به یک {{domxref("HTMLFormElement")}} با فیلدهای ورودی مناسب. فرم باید حداقل شامل یک id و یک password باشد. همچنین ممکن است به یک توکن CSRF نیاز داشته باشد.

### استثناها

- {{jsxref("TypeError")}}
  - : اگر یکی از گزینه‌های `id`، `origin` یا `password` خالی باشد، پرتاب می‌شود.

## مثال‌ها

این مثال نحوه تنظیم یک {{domxref("HTMLFormElement")}} برای دریافت داده‌هایی را نشان می‌دهد که از آن برای ایجاد یک شیء {{domxref("PasswordCredential")}} استفاده خواهیم کرد.

با عنصر فرم شروع می‌کنیم.

```html
<form id="form" method="post">
  <label for="id">Username:</label>
  <input type="text" name="id" autocomplete="username" />
  <label for="password">Password:</label>
  <input type="password" name="password" autocomplete="current-password" />
  <input type="hidden" name="csrf_token" value="*****" />
</form>
```

سپس یک ارجاع به این عنصر فرم گرفته و با استفاده از آن یک شیء {{domxref("PasswordCredential")}} ایجاد می‌کنیم و آن را در سیستم رمز عبور مرورگر ذخیره می‌کنیم.

```js
const form = document.querySelector("#form");
const creds = new PasswordCredential(form);
// Store the credentials.
navigator.credentials.store(creds).then((creds) => {
  // Do something with the credentials if you need to.
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}