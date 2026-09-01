---
title: "HTMLOutputElement: checkValidity() method"
---

---
title: "HTMLOutputElement: checkValidity() method"
short-title: checkValidity()
slug: Web/API/HTMLOutputElement/checkValidity
page-type: web-api-instance-method
browser-compat: api.HTMLOutputElement.checkValidity
---

{{APIRef("HTML DOM")}}

متد **`checkValidity()`** در رابط {{domxref("HTMLOutputElement")}} بررسی می‌کند که آیا عنصر معتبر است یا خیر، اما همیشه `true` برمی‌گرداند، زیرا عناصر {{HTMLElement("output")}} هرگز برای [اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation) در نظر گرفته نمی‌شوند.

## نحو

```js-nolint
checkValidity()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک مقدار بولین، `true`.

## مثال‌ها

در مثال زیر، فراخوانی `checkValidity()` مقدار `true` برمی‌گرداند.

```js
const element = document.getElementById("myOutput");
console.log(element.checkValidity());
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLOutputElement.reportValidity()")}}
- {{HTMLElement("output")}}
- {{HTMLElement("form")}}
- [یادگیری: اعتبارسنجی فرم سمت کلاینت](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation)