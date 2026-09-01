---
title: "HTMLObjectElement: checkValidity() method"
short-title: checkValidity()
slug: Web/API/HTMLObjectElement/checkValidity
page-type: web-api-instance-method
browser-compat: api.HTMLObjectElement.checkValidity
---

{{APIRef("HTML DOM")}}

متد **`checkValidity()`** در رابط {{domxref("HTMLObjectElement")}} بررسی می‌کند که آیا عنصر معتبر است یا نه، اما همیشه `true` برمی‌گرداند، زیرا عناصر {{HTMLElement("object")}} هرگز کاندیدای [اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation) نیستند.

## نحو (Syntax)

```js-nolint
checkValidity()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

یک مقدار بولی، `true`.

## مثال‌ها

در مثال زیر، فراخوانی `checkValidity()` مقدار `true` را برمی‌گرداند.

```js
const element = document.getElementById("myObjectElement");
console.log(element.checkValidity());
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLObjectElement.reportValidity()")}}
- {{HTMLElement("object")}}
- {{HTMLElement("form")}}
- [یادگیری: اعتبارسنجی فرم در سمت کلاینت](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation)
```