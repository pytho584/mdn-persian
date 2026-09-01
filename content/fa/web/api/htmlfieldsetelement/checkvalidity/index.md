---
title: "HTMLFieldSetElement: checkValidity() method"
---

---
title: "HTMLFieldSetElement: checkValidity() method"
short-title: checkValidity()
slug: Web/API/HTMLFieldSetElement/checkValidity
page-type: web-api-instance-method
browser-compat: api.HTMLFieldSetElement.checkValidity
---

{{APIRef("HTML DOM")}}

متد **`checkValidity()`** از رابط {{domxref("HTMLFieldSetElement")}} بررسی می‌کند که آیا عنصر معتبر است، اما همیشه `true` برمی‌گرداند، زیرا عناصر {{HTMLElement("fieldset")}} هرگز کاندیدای [اعتبارسنجی محدودیت](/en-US/docs/Web/HTML/Guides/Constraint_validation) نیستند.

> [!NOTE]
> شبه‌کلاس‌های CSS {{cssxref(":valid")}} و {{cssxref(":invalid")}} به عناصر `<fieldset>` بر اساس اعتبار کنترل‌های فرمِ فرزندِ آن اعمال می‌شوند، نه خودِ عنصر `<fieldset>`.

## نحو

```js-nolint
checkValidity()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک مقدار بولین، `true`.

## مثال‌ها

در مثال زیر، فراخوانی `checkValidity()` مقدار `true` را برمی‌گرداند.

```js
const element = document.getElementById("myFieldSet");
console.log(element.checkValidity());
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLFieldSetElement.reportValidity()")}}
- {{HTMLElement("fieldset")}}
- {{HTMLElement("form")}}
- [یادگیری: اعتبارسنجی فرم در سمت کلاینت](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت](/en-US/docs/Web/HTML/Guides/Constraint_validation)