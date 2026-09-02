---
title: "HTMLTextAreaElement: validationMessage property"
---

---
title: "HTMLTextAreaElement: validationMessage property"
short-title: validationMessage
slug: Web/API/HTMLTextAreaElement/validationMessage
page-type: web-api-instance-property
browser-compat: api.HTMLTextAreaElement.validationMessage
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`validationMessage`** از رابط {{domxref("HTMLTextAreaElement")}} رشته‌ای را برمی‌گرداند که یک پیام محلی‌سازی‌شده را نشان می‌دهد و محدودیت‌های اعتبارسنجی را توصیف می‌کند که کنترل {{htmlelement("textarea")}} آن‌ها را (در صورت وجود) برآورده نمی‌کند. در صورتی این رشته خالی است که کنترل نامزد اعتبارسنجی محدودیت نباشد ({{domxref("HTMLTextAreaElement.willValidate")}} برابر `false` باشد) یا محدودیت‌های خود را برآورده کند.

اگر عنصر `<textarea>` نامزد اعتبارسنجی محدودیت باشد (`willValidate` برابر `true` باشد) و محدودیت‌ها برآورده نشوند (ویژگی `valid` در شیء {{domxref("HTMLTextAreaElement.validity")}} برابر `false` باشد)، مقدار این ویژگی همان پیام خطایی است که در طول اعتبارسنجی به کاربر نمایش داده می‌شود.

## مقدار

یک رشته.

## مثال

```js
const textarea = document.getElementById("myTextArea");
const errorMessage = textarea.validationMessage;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLelement("textarea")}}
- {{domxref("HTMLTextAreaElement")}}
- {{domxref("HTMLTextAreaElement.willValidate")}}
- {{domxref("HTMLTextAreaElement.validity")}}
- {{domxref("HTMLTextAreaElement.checkValidity()")}}
- {{domxref("HTMLTextAreaElement.reportValidity()")}}
- {{domxref("HTMLTextAreaElement.setCustomValidity()")}}
- [یادگیری: اعتبارسنجی فرم در سمت کلاینت](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت](/en-US/docs/Web/HTML/Guides/Constraint_validation)
- شبه‌کلاس‌های CSS {{cssxref(":valid")}} و {{cssxref(":invalid")}}