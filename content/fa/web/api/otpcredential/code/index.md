---
title: "OTPCredential: code property"
short-title: code
slug: Web/API/OTPCredential/code
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.OTPCredential.code
---

{{SecureContext_Header}}{{APIRef("WebOTP API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`code`** در رابط {{domxref("OTPCredential")}} شامل رمز یک‌بارمصرف (OTP) است.

## مقدار

رشته‌ای (string) شامل OTP.

## مثال‌ها

کد زیر وقتی یک پیامک می‌رسد، فرایند مجوز مرورگر را فعال می‌کند. اگر مجوز داده شود، پرامیس با یک شیء `OTPCredential` resolve می‌شود. مقدار `code` موجود در آن سپس به‌عنوان مقدار یک عنصر فرم {{htmlelement("input")}} تنظیم شده و فرم ارسال می‌شود.

```js
navigator.credentials
  .get({
    otp: { transport: ["sms"] },
    signal: ac.signal,
  })
  .then((otp) => {
    input.value = otp.code;
    if (form) form.submit();
  })
  .catch((err) => {
    console.error(err);
  });
```

> [!NOTE]
> برای توضیح کامل کد، به صفحهٔ اصلی {{domxref('WebOTP API','','',' ')}} مراجعه کنید. همچنین می‌توانید [این کد را به‌عنوان بخشی از یک دموی کامل و قابل اجرا](https://chrome.dev/web-otp-demo/) ببینید.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}