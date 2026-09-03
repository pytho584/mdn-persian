---
title: "OTPCredential"
---

---
title: OTPCredential
slug: Web/API/OTPCredential
page-type: web-api-interface
status:
  - experimental
browser-compat: api.OTPCredential
---

{{APIRef("WebOTP API")}}{{SecureContext_Header}}{{SeeCompatTable}}

رابط **`OTPCredential`** متعلق به {{domxref('WebOTP API','','',' ')}} زمانی بازگردانده می‌شود که یک فراخوانی {{domxref("CredentialsContainer.get", "navigator.credentials.get()")}} از نوع WebOTP (یعنی فراخوانی‌ای که با گزینهٔ `otp` انجام شده باشد) با موفقیت انجام شود. این رابط شامل یک ویژگی `code` است که رمز یکبارمصرف (OTP) بازیابی‌شده را در خود نگه می‌دارد.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_این رابط همچنین ویژگی‌هایی را از {{domxref("Credential")}} به ارث می‌برد._

- {{domxref("OTPCredential.code")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : رمز یکبارمصرف (OTP).

## روش‌های نمونه

هیچ‌کدام.

## مثال‌ها

کد زیر، هنگام رسیدن یک پیامک، فرایند درخواست مجوز مرورگر را فعال می‌کند. اگر مجوز صادر شود، پرامیس (Promise) با یک شیء `OTPCredential` حل می‌شود. سپس مقدار `code` موجود، به‌عنوان مقدار یک عنصر فرم {{htmlelement("input")}} تنظیم می‌شود و فرم ارسال می‌گردد.

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
> برای توضیح کامل کد، به صفحهٔ اصلی {{domxref('WebOTP API','','',' ')}} مراجعه کنید. همچنین می‌توانید [این کد را به‌عنوان بخشی از یک نسخهٔ نمایشی کامل و عملی](https://chrome.dev/web-otp-demo/) مشاهده کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}