---
title: "HTMLButtonElement: willValidate property"
short-title: willValidate
slug: Web/API/HTMLButtonElement/willValidate
page-type: web-api-instance-property
browser-compat: api.HTMLButtonElement.willValidate
---

{{APIRef("HTML DOM")}}

خاصیت فقط خواندنی **`willValidate`** از رابط {{domxref("HTMLButtonElement")}} نشان می‌دهد که آیا عنصر {{htmlelement("button")}} کاندیدای [اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation) است یا خیر. اگر هر یک از شرایط زیر آن را از اعتبارسنجی محدودیت‌ها منع کند، مقدار آن `false` است:

- {{domxref("HTMLButtonElement.type", "type")}} آن `reset` یا `button` باشد؛
- دارای یک عنصر جد {{HTMLElement("datalist")}} باشد؛
- خاصیت {{domxref("HTMLButtonElement.disabled", "disabled")}} برابر `true` باشد.

## مقدار

یک مقدار بولی.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("HTMLButtonElement.checkValidity()")}}
- {{HTMLElement("button")}}
- {{HTMLElement("form")}}
- [یادگیری: اعتبارسنجی فرم در سمت کلاینت](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation)