---
title: "HTMLObjectElement: reportValidity() method"
short-title: reportValidity()
slug: Web/API/HTMLObjectElement/reportValidity
page-type: web-api-instance-method
browser-compat: api.HTMLObjectElement.reportValidity
---

{{APIRef("HTML DOM")}}

متد **`reportValidity()`** در رابط {{domxref("HTMLObjectElement")}} همان مراحل بررسی اعتبار متد {{domxref("HTMLObjectElement.checkValidity", "checkValidity()")}} را انجام می‌دهد. این متد همیشه `true` برمی‌گرداند، زیرا عناصر {{HTMLElement("object")}} هرگز کاندیدای [اعتبارسنجی محدودیت](/en-US/docs/Web/HTML/Guides/Constraint_validation) نیستند.

## نحو

```js-nolint
reportValidity()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک مقدار بولی، `true`.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLObjectElement.checkValidity()")}}
- {{HTMLElement("object")}}
- {{HTMLElement("form")}}
- [یادگیری: اعتبارسنجی فرم سمت کاربر](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت](/en-US/docs/Web/HTML/Guides/Constraint_validation)