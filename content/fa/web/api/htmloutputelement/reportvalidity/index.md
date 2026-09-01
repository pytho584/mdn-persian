---
title: "HTMLOutputElement: reportValidity() method"
short-title: reportValidity()
slug: Web/API/HTMLOutputElement/reportValidity
page-type: web-api-instance-method
browser-compat: api.HTMLOutputElement.reportValidity
---

{{APIRef("HTML DOM")}}

متد **`reportValidity()`** در واسط {{domxref("HTMLOutputElement")}} همان مراحل بررسی اعتبار را انجام می‌دهد که متد {{domxref("HTMLOutputElement.checkValidity", "checkValidity()")}} انجام می‌دهد. این متد همیشه `true` برمی‌گرداند، زیرا عناصر {{HTMLElement("output")}} هرگز نامزد [اعتبارسنجی محدودیت](/en-US/docs/Web/HTML/Guides/Constraint_validation) نیستند.

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

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("HTMLOutputElement.checkValidity()")}}
- {{HTMLElement("output")}}
- {{HTMLElement("form")}}
- [آموزش: اعتبارسنجی فرم سمت کلاینت](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت](/en-US/docs/Web/HTML/Guides/Constraint_validation)