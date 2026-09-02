---
title: "HTMLTextAreaElement: willValidate property"
short-title: willValidate
slug: Web/API/HTMLTextAreaElement/willValidate
page-type: web-api-instance-property
browser-compat: api.HTMLTextAreaElement.willValidate
---

{{APIRef("HTML DOM")}}

خاصیت فقط-خواندنی **`willValidate`** از واسط {{domxref("HTMLTextAreaElement")}} مشخص می‌کند که آیا عنصر {{htmlelement("textarea")}} یک کاندید برای [constraint validation](/en-US/docs/Web/HTML/Guides/Constraint_validation) است یا خیر. این مقدار `false` است اگر هر شرایطی آن را از اعتبارسنجی محدودیتی منع کند، مانند زمانی که ویژگی {{domxref("HTMLTextAreaElement.disabled", "disabled")}} یا {{domxref("HTMLTextAreaElement.readOnly", "readOnly")}} آن `true` باشد.

## Value

یک مقدار بولی.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("HTMLTextAreaElement.checkValidity()")}}
- {{HTMLElement("textarea")}}
- {{HTMLElement("form")}}
- [Learn: Client-side form validation](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [Guide: Constraint validation](/en-US/docs/Web/HTML/Guides/Constraint_validation)