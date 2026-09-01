---
title: "HTMLInputElement: validationMessage property"
---

---
title: "HTMLInputElement: validationMessage property"
short-title: validationMessage
slug: Web/API/HTMLInputElement/validationMessage
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.validationMessage
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`validationMessage`** از رابط {{domxref("HTMLInputElement")}} رشته‌ای را برمی‌گرداند که نمایانگر یک پیام محلی‌سازی‌شده است و محدودیت‌های اعتبارسنجی‌ای را توصیف می‌کند که کنترل {{htmlelement("input")}} آن‌ها را برآورده نمی‌کند (در صورت وجود).

اگر عنصر `<input>` کاندیدای اعتبارسنجی محدودیت نباشد (یعنی {{domxref("HTMLInputElement.willValidate")}} برابر با `false` باشد)، یا محدودیت‌های خود را برآورده کند، مقدار این ویژگی، رشتهٔ خالی (`""`) خواهد بود.

اگر عنصر کاندیدای اعتبارسنجی محدودیت باشد (`willValidate` برابر با `true` باشد) و محدودیت‌ها برآورده نشوند (ویژگی `valid` آبجکت {{domxref("HTMLInputElement.validity")}} برابر با `false` باشد)، مقدار این ویژگی، همان پیام خطایی است که در هنگام اعتبارسنجی به کاربر نمایش داده می‌شود.

## مقدار

یک رشته.

## مثال

```js
const input = document.getElementById("myInput");
const errorMessage = input.validationMessage;
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{HTMLelement("input")}}
- {{domxref("HTMLInputElement")}}
- {{domxref("HTMLInputElement.willValidate")}}
- {{domxref("HTMLInputElement.validity")}}
- {{domxref("HTMLInputElement.checkValidity()")}}
- {{domxref("HTMLInputElement.reportValidity()")}}
- {{domxref("HTMLInputElement.setCustomValidity()")}}
- [یادگیری: اعتبارسنجی فرم سمت کلاینت](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت](/en-US/docs/Web/HTML/Guides/Constraint_validation)
- شبه‌کلاس‌های CSS {{cssxref(":valid")}} و {{cssxref(":invalid")}}