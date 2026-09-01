```markdown
---
title: "HTMLOutputElement: validationMessage property"
short-title: validationMessage
slug: Web/API/HTMLOutputElement/validationMessage
page-type: web-api-instance-property
browser-compat: api.HTMLOutputElement.validationMessage
---

{{APIRef("HTML DOM")}}

خاصیت فقط-خواندنی **`validationMessage`** از رابط {{domxref("HTMLOutputElement")}} یک رشته برمی‌گرداند که یک پیام بومی‌سازی‌شده را نشان می‌دهد و محدودیت‌های اعتبارسنجی را توصیف می‌کند که کنترل {{htmlelement("output")}} آن‌ها را برآورده نمی‌کند (در صورت وجود). این رشته خالی است زیرا عناصر `<output>` کاندیدایی برای اعتبارسنجی محدودیت‌ها نیستند ({{domxref("HTMLOutputElement.willValidate")}} `false` است).

## مقدار

رشته خالی، `""`؛

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{HTMLelement("output")}}
- {{domxref("HTMLOutputElement")}}
- {{domxref("HTMLOutputElement.willValidate")}}
- {{domxref("HTMLOutputElement.validity")}}
- {{domxref("HTMLOutputElement.checkValidity()")}}
- {{domxref("HTMLOutputElement.reportValidity()")}}
- {{domxref("HTMLOutputElement.setCustomValidity()")}}
- [یادگیری: اعتبارسنجی سمت کلاینت فرم](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation)
- شبه‌کلاس‌های CSS {{cssxref(":valid")}} و {{cssxref(":invalid")}}
```