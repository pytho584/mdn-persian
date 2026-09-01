---
title: "HTMLSelectElement: reportValidity() method"
short-title: reportValidity()
slug: Web/API/HTMLSelectElement/reportValidity
page-type: web-api-instance-method
browser-compat: api.HTMLSelectElement.reportValidity
---

{{APIRef("HTML DOM")}}

متد **`reportValidity()`** از رابط {{domxref("HTMLSelectElement")}} همان مراحل بررسی اعتبار را انجام می‌دهد که متد {{domxref("HTMLSelectElement.checkValidity", "checkValidity()")}} انجام می‌دهد. علاوه بر این، اگر رویداد {{domxref("HTMLElement/invalid_event", "invalid")}} لغو نشود، مرورگر مشکل را به کاربر نمایش می‌دهد.

## نحو (Syntax)

```js-nolint
reportValidity()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

اگر مقدار عنصر هیچ مشکل اعتباری نداشته باشد، `true` و در غیر این صورت `false` برمی‌گرداند.

## مشخصات (Specifications)

{{Specifications}}

## سازگاری با مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLSelectElement.checkValidity()")}}
- {{HTMLElement("select")}}
- {{HTMLElement("form")}}
- [یادگیری: اعتبارسنجی فرم در سمت کاربر](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation)
- کلاس‌های شبه CSS {{cssxref(":valid")}} و {{cssxref(":invalid")}}