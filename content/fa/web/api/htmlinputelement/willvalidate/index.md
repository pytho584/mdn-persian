---
title: "HTMLInputElement: willValidate property"
short-title: willValidate
slug: Web/API/HTMLInputElement/willValidate
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.willValidate
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`willValidate`** در رابط {{domxref("HTMLInputElement")}} مشخص می‌کند که آیا عنصر {{htmlelement("input")}} کاندیدای [constraint validation](/en-US/docs/Web/HTML/Guides/Constraint_validation) (اعتبارسنجی محدودیت‌ها) است یا نه. اگر هر شرایطی آن را از اعتبارسنجی محدودیت‌ها بازدارد، مقدار این ویژگی `false` است؛ از جمله:

- {{domxref("HTMLInputElement.type", "type")}} آن یکی از مقادیر `hidden`، `reset` یا `button` باشد؛
- یک جد (ancestor) از نوع {{HTMLElement("datalist")}} داشته باشد؛
- خاصیت {{domxref("HTMLInputElement.disabled", "disabled")}} آن برابر `true` باشد.

## مقدار

یک مقدار بولین.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLInputElement.checkValidity()")}}
- {{HTMLElement("input")}}
- {{HTMLElement("form")}}
- [Learn: Client-side form validation](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [Guide: Constraint validation](/en-US/docs/Web/HTML/Guides/Constraint_validation)