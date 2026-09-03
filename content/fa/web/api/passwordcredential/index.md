---
title: PasswordCredential
slug: Web/API/PasswordCredential
page-type: web-api-interface
status:
  - experimental
browser-compat: api.PasswordCredential
---

{{SeeCompatTable}}{{APIRef("Credential Management API")}}{{securecontext_header}}

رابط **`PasswordCredential`** از [API مدیریت اعتبارنامه](/en-US/docs/Web/API/Credential_Management_API) اطلاعات مربوط به یک جفت نام کاربری/گذرواژه را فراهم می‌کند. در مرورگرهای پشتیبان، نمونه‌ای از این کلاس می‌تواند در عضو `credential` آبجکت `init` برای {{domxref("Window/fetch", "fetch()")}} سراسری ارسال شود.

> [!NOTE]
> این رابط به زمینه‌های سطح بالا محدود است و نمی‌توان آن را از یک {{HTMLElement("iframe")}} استفاده کرد.

{{InheritanceDiagram}}

## سازنده

- {{domxref("PasswordCredential.PasswordCredential()","PasswordCredential()")}} {{Experimental_Inline}}
  - : یک شیء `PasswordCredential` جدید می‌سازد.

## ویژگی‌های نمونه

_ویژگی‌هایی را از ancestor خود، {{domxref("Credential")}} به ارث می‌برد._

- {{domxref("PasswordCredential.iconURL")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : رشته‌ای شامل یک URL که به تصویری برای یک آیکن اشاره می‌کند. این تصویر برای نمایش در انتخابگر اعتبارنامه در نظر گرفته شده است. URL باید بدون احراز هویت قابل دسترسی باشد.
- {{domxref("PasswordCredential.name")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : رشته‌ای قابل خواندن برای انسان که نام عمومی را برای نمایش در انتخابگر اعتبارنامه فراهم می‌کند.
- {{domxref("PasswordCredential.password")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : رشته‌ای شامل گذرواژه اعتبارنامه.

## روش‌های نمونه

هیچ.

## مثال‌ها

```js
const cred = new PasswordCredential({
  id,
  password,
  name,
  iconURL,
});

navigator.credentials.store(cred).then(() => {
  // Do something else.
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}