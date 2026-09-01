---
title: "HTMLInputElement: formAction property"
---

---
title: "HTMLInputElement: formAction property"
short-title: formAction
slug: Web/API/HTMLInputElement/formAction
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.formAction
---

{{APIRef("HTML DOM")}}

ویژگی **`formAction`** از رابط {{domxref("HTMLInputElement")}}، نشانی (URL) برنامهای است که هنگام ارسال فرمِ متعلق به این کنترل، روی سرور اجرا میشود. این ویژگی مقدار صفت [`formaction`](/en-US/docs/Web/HTML/Reference/Elements/input#formaction) عنصر `<input>` را منعکس میکند.

این ویژگی تنها برای عناصر `<input>` از نوع [`submit`](/en-US/docs/Web/HTML/Reference/Elements/input/submit) و [`image`](/en-US/docs/Web/HTML/Reference/Elements/input/image) معتبر است.

اگر فرم از طریق این ورودی ارسال شود، مقدار این ویژگی، ویژگی {{domxref("HTMLFormElement.action", "action")}} در رابط {{domxref("HTMLFormElement")}} را نادیده می‌گیرد. این ویژگی قابل خواندن و تنظیم است.

## مقدار

یک رشته (string). نشانی URL برای ارسال فرم.

## مثال‌ها

```js
inputElement.formAction = "/cgi-bin/publish";
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLInputElement.formEnctype")}}
- {{domxref("HTMLInputElement.formMethod")}}
- {{domxref("HTMLInputElement.formNoValidate")}}
- {{domxref("HTMLInputElement.formTarget")}}
- [`<input type="submit">`](/en-US/docs/Web/HTML/Reference/Elements/input/submit)
- [`<input type="image">`](/en-US/docs/Web/HTML/Reference/Elements/input/image)
- [ارسال داده‌های فرم](/en-US/docs/Learn_web_development/Extensions/Forms/Sending_and_retrieving_form_data)