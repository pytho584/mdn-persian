---
title: "HTMLSelectElement: checkValidity() method"
short-title: checkValidity()
slug: Web/API/HTMLSelectElement/checkValidity
page-type: web-api-instance-method
browser-compat: api.HTMLSelectElement.checkValidity
---

{{APIRef("HTML DOM")}}

متد **`checkValidity()`** از رابط {{domxref("HTMLSelectElement")}} یک مقدار بولی (boolean) برمی‌گرداند که نشان می‌دهد آیا عنصر مورد نظر با قوانین [اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation) اعمال شده بر روی آن مطابقت دارد یا خیر. اگر مقدار بازگشتی `false` باشد، این متد همچنین یک رویداد {{domxref("HTMLElement/invalid_event", "invalid")}} روی عنصر ایجاد می‌کند. از آنجایی که هیچ رفتار پیش‌فرض مرورگری برای `checkValidity()` وجود ندارد، لغو (cancel) این رویداد `invalid` تأثیری ندارد.

> [!NOTE]
> یک عنصر HTML {{htmlelement("select")}} که {{domxref("HTMLSelectElement.validationMessage", "validationMessage")}} آن غیر null باشد، نامعتبر در نظر گرفته می‌شود، با شبه‌کلاس CSS {{cssxref(":invalid")}} مطابقت می‌کند، و باعث می‌شود `checkValidity()` مقدار `false` برگرداند. از متد {{domxref("HTMLSelectElement.setCustomValidity()")}} برای تنظیم {{domxref("HTMLSelectElement.validationMessage")}} روی رشته خالی استفاده کنید تا وضعیت {{domxref("HTMLSelectElement.validity", "validity")}} به معتبر تنظیم شود.

## نحو (Syntax)

```js-nolint
checkValidity()
```

### پارامترها

هیچ‌کدام.

### مقدار بازگشتی

اگر مقدار عنصر هیچ مشکل اعتباری نداشته باشد `true` و در غیر این صورت `false` برمی‌گرداند.

## مثال‌ها

در مثال زیر، فراخوانی `checkValidity()` یا `true` یا `false` را برمی‌گرداند.

```js
const element = document.getElementById("mySelect");
console.log(element.checkValidity());
```

## مشخصات (Specifications)

{{Specifications}}

## سازگاری مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLSelectElement.reportValidity()")}}
- {{HTMLElement("textarea")}}
- {{HTMLElement("form")}}
- [یادگیری: اعتبارسنجی فرم در سمت کلاینت](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation)
- شبه‌کلاس‌های CSS {{cssxref(":valid")}} و {{cssxref(":invalid")}}