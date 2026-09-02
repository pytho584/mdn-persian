---
title: "HTMLTextAreaElement: checkValidity() method"
---

---
title: "HTMLTextAreaElement: checkValidity() method"
short-title: checkValidity()
slug: Web/API/HTMLTextAreaElement/checkValidity
page-type: web-api-instance-method
browser-compat: api.HTMLTextAreaElement.checkValidity
---

{{APIRef("HTML DOM")}}

متد **`checkValidity()`** از رابط {{domxref("HTMLTextAreaElement")}} یک مقدار بولی برمی‌گرداند که نشان می‌دهد آیا عنصر با هر یک از قوانین [اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation) اعمال‌شده روی آن مطابقت دارد یا نه. اگر نتیجه `false` باشد، این متد همچنین یک رویداد {{domxref("HTMLElement/invalid_event", "invalid")}} روی عنصر برمی‌انگیزد. از آنجا که رفتار پیش‌فرض مرورگر برای `checkValidity()` وجود ندارد، لغو کردن این رویداد `invalid` هیچ تأثیری ندارد.

> [!NOTE]
> یک عنصر HTML {{htmlelement("textarea")}} که {{domxref("HTMLTextAreaElement.validationMessage", "validationMessage")}} آن غیر null باشد، نامعتبر در نظر گرفته می‌شود، با شبه‌کلاس CSS {{cssxref(":invalid")}} مطابقت می‌کند، و باعث می‌شود `checkValidity()` مقدار `false` برگرداند. از متد {{domxref("HTMLTextAreaElement.setCustomValidity()")}} استفاده کنید تا {{domxref("HTMLTextAreaElement.validationMessage")}} را روی رشتهٔ خالی تنظیم کنید و وضعیت {{domxref("HTMLTextAreaElement.validity", "validity")}} را معتبر کنید.

## سینتکس

```js-nolint
checkValidity()
```

### پارامترها

هیچ.

### مقدار بازگشتی

اگر مقدار عنصر هیچ مشکل اعتباری نداشته باشد، `true` برمی‌گرداند؛ در غیر این صورت، `false` برمی‌گرداند.

## مثال‌ها

در مثال زیر، فراخوانی `checkValidity()` مقدار `true` یا `false` را برمی‌گرداند.

```js
const element = document.getElementById("myTextArea");
console.log(element.checkValidity());
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLTextAreaElement.reportValidity()")}}
- {{HTMLElement("textarea")}}
- {{HTMLElement("form")}}
- [یادگیری: اعتبارسنجی فرم در سمت کلاینت](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [راهنما: اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation)
- شبه‌کلاس‌های CSS {{cssxref(":valid")}} و {{cssxref(":invalid")}}