---
title: "HTMLButtonElement: formAction property"
short-title: formAction
slug: Web/API/HTMLButtonElement/formAction
page-type: web-api-instance-property
browser-compat: api.HTMLButtonElement.formAction
---

{{APIRef("HTML DOM")}}

ویژگی **`formAction`** در رابط {{domxref("HTMLButtonElement")}}، URL برنامه‌ای است که هنگام ارسال فرمِ متعلق به این کنترل، روی سرور اجرا می‌شود. این ویژگی منعکس‌کنندهٔ مقدار ویژگی [`formaction`](/en-US/docs/Web/HTML/Reference/Elements/button#formaction) عنصر `<button>` است.

این مقدار، اگر فرم از طریق دکمه ارسال شود، ویژگی {{domxref("HTMLFormElement.action", "action")}} رابط {{domxref("HTMLFormElement")}} را بازنویسی می‌کند. این ویژگی قابل خواندن یا تنظیم است.

## مقدار

یک رشته (string). آدرس URL برای ارسال فرم.

## مثال‌ها

```js
btnEl.formAction = "/cgi-bin/publish";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLButtonElement.formEnctype")}}
- {{domxref("HTMLButtonElement.formMethod")}}
- {{domxref("HTMLButtonElement.formNoValidate")}}
- {{domxref("HTMLButtonElement.formTarget")}}
- [Sending form data](/en-US/docs/Learn_web_development/Extensions/Forms/Sending_and_retrieving_form_data)