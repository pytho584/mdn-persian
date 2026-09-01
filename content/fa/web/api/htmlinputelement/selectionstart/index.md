---
title: "HTMLInputElement: selectionStart property"
short-title: selectionStart
slug: Web/API/HTMLInputElement/selectionStart
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.selectionStart
---

{{ApiRef("HTML DOM")}}

ویژگی **`selectionStart`** در واسط {{domxref("HTMLInputElement")}} عددی است که اندیس شروع متن انتخاب‌شده را نشان می‌دهد. وقتی چیزی انتخاب نشده باشد، موقعیت مکان‌نمای ورودی متن (caret) را درون عنصر `<input>` برمی‌گرداند.

> [!NOTE]
> طبق [مشخصات فرم‌های WHATWG](https://html.spec.whatwg.org/multipage/forms.html#concept-input-apply)، ویژگی `selectionStart` فقط برای ورودی‌هایی از انواع text، search، URL، tel و password کاربرد دارد. در سایر انواع ورودی، خواندن `selectionStart` مقدار `null` برمی‌گرداند و تنظیم آن خطای `InvalidStateError` ایجاد می‌کند.

اگر `selectionStart` بزرگ‌تر از `selectionEnd` باشد، هر دو به‌عنوان مقدار `selectionEnd` در نظر گرفته می‌شوند.

## مقدار

یک عدد نامنفی.

## مثال‌ها

### HTML

```html
<!-- use selectionStart on non text input element -->
<label for="color">selectionStart property on type=color</label>
<input id="color" type="color" />

<!-- use selectionStart on text input element -->
<fieldset>
  <legend>selectionStart property on type=text</legend>
  <label for="statement">Select 'mdn' word from the text : </label>
  <input
    type="text"
    id="statement"
    value="The mdn is a documentation repository." />
  <button id="statement-btn">Select mdn text</button>
</fieldset>
```

### جاوااسکریپت

```js
const inputElement = document.getElementById("statement");
const statementBtn = document.getElementById("statement-btn");
const colorStart = document.getElementById("color");

statementBtn.addEventListener("click", () => {
  inputElement.selectionStart = 4;
  inputElement.selectionEnd = 7;
  inputElement.focus();
});

// open browser console to verify output
console.log(colorStart.selectionStart); // Output : null
```

### نتیجه

{{EmbedLiveSample("Examples")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی {{domxref("HTMLTextAreaElement.selectionStart")}}
- ویژگی {{domxref("HTMLInputElement.selectionEnd")}}
- روش {{domxref("HTMLInputElement.setSelectionRange")}}