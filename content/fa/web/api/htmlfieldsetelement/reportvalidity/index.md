---
title: "HTMLFieldSetElement: reportValidity() method"
short-title: reportValidity()
slug: Web/API/HTMLFieldSetElement/reportValidity
page-type: web-api-instance-method
browser-compat: api.HTMLFieldSetElement.reportValidity
---

{{APIRef("HTML DOM")}}

روش **`reportValidity()`** از رابط {{domxref("HTMLFieldSetElement")}} همان مراحل بررسی اعتبار را مانند روش {{domxref("HTMLFieldSetElement.checkValidity", "checkValidity()")}} انجام می‌دهد. این روش همیشه `true` برمی‌گرداند زیرا عناصر {{HTMLElement("fieldset")}} هرگز کاندیدای [اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation) نیستند.

## نحو

```js-nolint
reportValidity()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

یک مقدار بولین، `true`.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLFieldSetElement.checkValidity()")}}
- {{HTMLElement("fieldset")}}
- {{HTMLElement("form")}}
- [یادگیری: اعتبارسنجی فرم سمت کاربر](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation)