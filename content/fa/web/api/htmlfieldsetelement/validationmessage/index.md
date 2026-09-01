```yaml
---
title: "HTMLFieldSetElement: validationMessage property"
short-title: validationMessage
slug: Web/API/HTMLFieldSetElement/validationMessage
page-type: web-api-instance-property
browser-compat: api.HTMLFieldSetElement.validationMessage
---

{{APIRef("HTML DOM")}}

خاصیت فقط‌خواندنی **`validationMessage`** از رابط {{domxref("HTMLFieldSetElement")}} یک رشته را برمی‌گرداند که یک پیام محلی‌سازی‌شده را نشان می‌دهد و محدودیت‌های اعتبارسنجی را که کنترل {{htmlelement("fieldset")}} آن‌ها را برآورده نمی‌کند (در صورت وجود) توصیف می‌کند. این رشته خالی است زیرا عناصر `<fieldset>` کاندیدای اعتبارسنجی محدودیت نیستند ({{domxref("HTMLFieldSetElement.willValidate")}} برابر با `false` است).

## Value

رشته خالی، `""`;

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{HTMLelement("fieldset")}}
- {{domxref("HTMLFieldSetElement")}}
- {{domxref("HTMLFieldSetElement.willValidate")}}
- {{domxref("HTMLFieldSetElement.validity")}}
- {{domxref("HTMLFieldSetElement.checkValidity()")}}
- {{domxref("HTMLFieldSetElement.reportValidity()")}}
- {{domxref("HTMLFieldSetElement.setCustomValidity()")}}
- [Learn: Client-side form validation](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [Guide: Constraint validation](/en-US/docs/Web/HTML/Guides/Constraint_validation)
- CSS {{cssxref(":valid")}} and {{cssxref(":invalid")}} pseudo-classes
```