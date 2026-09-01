---
title: "HTMLSelectElement: validationMessage property"
---

---
title: "HTMLSelectElement: validationMessage property"
short-title: validationMessage
slug: Web/API/HTMLSelectElement/validationMessage
page-type: web-api-instance-property
browser-compat: api.HTMLSelectElement.validationMessage
---

{{APIRef("HTML DOM")}}

ویژگی فقط-خواندنی **`validationMessage`** از رابط {{domxref("HTMLSelectElement")}} رشته‌ای را برمی‌گرداند که یک پیام محلی‌سازی‌شده را نشان می‌دهد و محدودیت‌های اعتبارسنجی‌ای را توصیف می‌کند که کنترل {{htmlelement("select")}} (در صورت وجود) آن‌ها را برآورده نمی‌کند. اگر کنترل کاندیدای اعتبارسنجی محدودیت نباشد ({{domxref("HTMLSelectElement.willValidate")}} برابر با `false` باشد) یا محدودیت‌های خود را برآورده کند، این رشته خالی است.

اگر عنصر `<select>` کاندیدای اعتبارسنجی محدودیت باشد (`willValidate` برابر با `true` باشد) و محدودیت‌ها برآورده نشوند (ویژگی `valid` شیء {{domxref("HTMLSelectElement.validity")}} برابر با `false` باشد)، آنگاه مقدار، پیام خطایی است که در طول اعتبارسنجی به کاربر نمایش داده می‌شود.

## مقدار

یک رشته.

## مثال

```js
const select = document.getElementById("mySelect");
const errorMessage = select.validationMessage;
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLelement("select")}}
- {{domxref("HTMLSelectElement")}}
- {{domxref("HTMLSelectElement.willValidate")}}
- {{domxref("HTMLSelectElement.validity")}}
- {{domxref("HTMLSelectElement.checkValidity()")}}
- {{domxref("HTMLSelectElement.reportValidity()")}}
- {{domxref("HTMLSelectElement.setCustomValidity()")}}
- [یادگیری: اعتبارسنجی فرم در سمت کلاینت](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت](/en-US/docs/Web/HTML/Guides/Constraint_validation)
- شبه‌کلاس‌های CSS {{cssxref(":valid")}} و {{cssxref(":invalid")}}