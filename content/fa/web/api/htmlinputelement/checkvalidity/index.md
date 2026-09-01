---
title: "HTMLInputElement: checkValidity() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/HTMLInputElement/checkValidity"
---

---
title: "HTMLInputElement: checkValidity() method"
short-title: checkValidity()
slug: Web/API/HTMLInputElement/checkValidity
page-type: web-api-instance-method
browser-compat: api.HTMLInputElement.checkValidity
---

{{APIRef("HTML DOM")}}

متد **`checkValidity()`** در رابط {{domxref("HTMLInputElement")}} یک مقدار بولی (boolean) برمی‌گرداند که نشان می‌دهد آیا عنصر، تمام [قوانین اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation) اعمال‌شده بر روی خود را برآورده می‌کند یا خیر. اگر مقدار `false` باشد، این متد همچنین یک رویداد {{domxref("HTMLElement/invalid_event", "invalid")}} روی عنصر فعال می‌کند. از آنجا که `checkValidity()` رفتار پیش‌فرضی در مرورگر ندارد، لغو (cancel) کردن این رویداد `invalid` هیچ تأثیری ندارد.

> [!NOTE]
> یک عنصر HTML {{htmlelement("input")}} با {{domxref("HTMLInputElement.validationMessage", "validationMessage")}} غیر خالی، نامعتبر در نظر گرفته می‌شود، با شبه‌کلاس CSS {{cssxref(":invalid")}} مطابقت خواهد داشت و باعث می‌شود `checkValidity()` مقدار `false` برگرداند. از متد {{domxref("HTMLInputElement.setCustomValidity()")}} برای تنظیم {{domxref("HTMLInputElement.validationMessage")}} روی رشته خالی استفاده کنید تا وضعیت {{domxref("HTMLInputElement.validity", "validity")}} معتبر باشد.

## Syntax

```js-nolint
checkValidity()
```

### Parameters

هیچ.

### Return value

اگر مقدار عنصر هیچ مشکل اعتبارسنجی نداشته باشد `true` و در غیر این صورت `false` برمی‌گرداند.

## Examples

### HTML

ما یک فرم شامل یک فیلد عددی اجباری و دو دکمه قرار می‌دهیم: یکی برای بررسی فرم و دیگری برای ارسال آن.

```html
<form action="#" method="post">
  <p>
    <label for="age">Your (21 to 65) </label>
    <input type="number" name="age" required id="age" min="21" max="65" />
  </p>
  <p>
    <button type="submit">Submit</button>
    <button type="button" id="check">checkValidity()</button>
  </p>
  <p id="log"></p>
</form>
```

### JavaScript

```js
const output = document.querySelector("#log");
const checkButton = document.querySelector("#check");
const ageInput = document.querySelector("#age");

ageInput.addEventListener("invalid", () => {
  console.log("Invalid event fired.");
});

checkButton.addEventListener("click", () => {
  const checkVal = ageInput.checkValidity();
  output.innerHTML = `checkValidity returned: ${checkVal}`;
});
```

### Results

{{EmbedLiveSample("Examples", "100%", 220)}}

وقتی مقدار `false` باشد، اگر مقدار ورودی خالی، کمتر از 21، بیشتر از 65، یا به هر شکل دیگری نامعتبر باشد، رویداد `invalid` در کنسول ثبت (log) می‌شود. برای گزارش خطا به کاربر، به جای آن از {{domxref("HTMLInputElement.reportValidity()")}} استفاده کنید.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("HTMLInputElement.reportValidity()")}}
- {{HTMLElement("input")}}
- {{HTMLElement("form")}}
- [Learn: Client-side form validation](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- [Guide: Constraint validation](/en-US/docs/Web/HTML/Guides/Constraint_validation)
- شبه‌کلاس‌های CSS {{cssxref(":valid")}} و {{cssxref(":invalid")}}