---
title: "HTMLFormElement: checkValidity() method"
short-title: checkValidity()
slug: Web/API/HTMLFormElement/checkValidity
page-type: web-api-instance-method
browser-compat: api.HTMLFormElement.checkValidity
---

{{APIRef("HTML DOM")}}

متد **`checkValidity()`** از رابط {{domxref("HTMLFormElement")}} یک مقدار بولی (boolean) برمی‌گرداند که نشان می‌دهد آیا همهٔ کنترل‌های مرتبط، قوانین [اعتبارسنجی محدودیت](/en-US/docs/Web/HTML/Guides/Constraint_validation) اعمال‌شده بر آنها را رعایت می‌کنند یا خیر. این متد همچنین یک رویداد {{domxref("HTMLElement/invalid_event", "invalid")}} روی هر عنصر نامعتبر (invalid) فعال می‌کند، اما روی خود عنصر فرم این کار را انجام نمی‌دهد. از آنجا که هیچ رفتار پیش‌فرض مرورگر برای `checkValidity()` وجود ندارد، لغو (cancel) کردن این رویداد `invalid` هیچ تأثیری نخواهد داشت.

> [!NOTE]
> شبه‌کلاس‌های CSS {{cssxref(":valid")}} و {{cssxref(":invalid")}} بر اساس اعتبار کنترل‌های فرم متعلق به عنصر `<form>` روی آن اعمال می‌شوند، نه بر اساس اعتبار خود عنصر `<form>`.

## نحو (Syntax)

```js-nolint
checkValidity()
```

### پارامترها

هیچکدام.

### مقدار بازگشتی

اگر مقادیر کنترل‌های مرتبط هیچ مشکل اعتبارسنجی نداشته باشند `true` و در غیر این صورت `false` برمی‌گرداند.

## مثال‌ها

در مثال زیر، فراخوانی `checkValidity()` بسته به شرایط `true` یا `false` برمی‌گرداند.

```js
const element = document.getElementById("myForm");
console.log(element.checkValidity());
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLFormElement.reportValidity()")}}
- {{HTMLElement("form")}}
- [یادگیری: اعتبارسنجی فرم در سمت کلاینت](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت](/en-US/docs/Web/HTML/Guides/Constraint_validation)