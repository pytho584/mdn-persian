---
title: "HTMLFormElement: reportValidity() method"
short-title: reportValidity()
slug: Web/API/HTMLFormElement/reportValidity
page-type: web-api-instance-method
browser-compat: api.HTMLFormElement.reportValidity
---

{{APIRef("HTML DOM")}}

متد **`reportValidity()`** از رابط {{domxref("HTMLFormElement")}} همان مراحل بررسی اعتبار را که متد {{domxref("HTMLFormElement.checkValidity", "checkValidity()")}} انجام می‌دهد، اجرا می‌کند. علاوه بر این، برای هر رویداد {{domxref("HTMLElement/invalid_event", "invalid")}} که شلیک شده و لغو نشده باشد، مرورگر مشکل را به کاربر نمایش می‌دهد.

## Syntax

```js-nolint
reportValidity()
```

### Parameters

هیچکدام.

### Return value

اگر مقادیر کنترل‌های مرتبط هیچ مشکل اعتباری نداشته باشند، `true` و در غیر این صورت `false` بازمی‌گرداند.

## Example

```js
document.forms["my-form"].addEventListener("submit", () => {
  document.forms["my-form"].reportValidity();
});
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("HTMLFormElement.checkValidity()")}}
- {{HTMLElement("form")}}
- [یادگیری: اعتبارسنجی فرم در سمت کاربر](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation)