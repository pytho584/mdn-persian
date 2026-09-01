---
title: "HTMLButtonElement: checkValidity() method"
---

---
title: "HTMLButtonElement: checkValidity() method"
short-title: checkValidity()
slug: Web/API/HTMLButtonElement/checkValidity
page-type: web-api-instance-method
browser-compat: api.HTMLButtonElement.checkValidity
---

{{APIRef("HTML DOM")}}

متد **`checkValidity()`** در رابط {{domxref("HTMLButtonElement")}} یک مقدار بولین برمی‌گرداند که نشان می‌دهد آیا عنصر هر یک از قوانین [constraint validation](/en-US/docs/Web/HTML/Guides/Constraint_validation) اعمال‌شده بر آن را برآورده می‌کند یا نه. اگر نتیجه `false` باشد، این متد همچنین یک رویداد {{domxref("HTMLElement/invalid_event", "invalid")}} روی عنصر صادر می‌کند. از آنجا که رفتار پیش‌فرض مرورگر برای `checkValidity()` وجود ندارد، لغو کردن این رویداد `invalid` هیچ اثری ندارد. اگر {{domxref("HTMLButtonElement/type", "type")}} عنصر {{HTMLElement("button")}} برابر `"button"` یا `"reset"` باشد، این متد همیشه `true` برمی‌گرداند، زیرا چنین دکمه‌هایی هرگز نامزد [constraint validation](/en-US/docs/Web/HTML/Guides/Constraint_validation) نیستند.

> [!NOTE]
> یک عنصر HTML {{htmlelement("button")}} از نوع `"submit"` که {{domxref("HTMLButtonElement.validationMessage", "validationMessage")}} آن نال (null) نباشد، نامعتبر در نظر گرفته می‌شود، با شبه‌کلاس CSS {{cssxref(":invalid")}} مطابقت می‌یابد و باعث می‌شود `checkValidity()` مقدار `false` برگرداند. از متد {{domxref("HTMLButtonElement.setCustomValidity()")}} استفاده کنید تا {{domxref("HTMLButtonElement.validationMessage")}} را روی رشتهٔ خالی تنظیم کنید و وضعیت {{domxref("HTMLButtonElement.validity", "validity")}} را معتبر کنید.

## Syntax

```js-nolint
checkValidity()
```

### Parameters

هیچ.

### Return value

اگر مقدار عنصر هیچ مشکل اعتباری نداشته باشد، `true` و در غیر این صورت `false` برمی‌گرداند.

## Examples

در مثال زیر، فراخوانی `checkValidity()` مقدار `true` یا `false` برمی‌گرداند.

```js
const element = document.getElementById("myButton");
console.log(element.checkValidity());
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("HTMLButtonElement.reportValidity()")}}
- {{HTMLElement("button")}}
- {{HTMLElement("form")}}
- [Learn: Client-side form validation](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [Guide: Constraint validation](/en-US/docs/Web/HTML/Guides/Constraint_validation)
- شبه‌کلاس‌های CSS {{cssxref(":valid")}} و {{cssxref(":invalid")}}