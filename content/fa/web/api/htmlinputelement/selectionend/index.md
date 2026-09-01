---
title: "HTMLInputElement: selectionEnd property"
short-title: selectionEnd
slug: Web/API/HTMLInputElement/selectionEnd
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.selectionEnd
---

{{ApiRef("HTML DOM")}}

ویژگی **`selectionEnd`** از رابط {{domxref("HTMLInputElement")}} عددی است که اندیس پایان متن انتخاب‌شده را نشان می‌دهد. به بیان دیگر، این ویژگی اندیس نویسه‌ای را نشان می‌دهد که **بلافاصله بعد از** انتخاب قرار دارد. همچنین وقتی هیچ انتخابی وجود ندارد، این ویژگی آفست نویسه‌ای را برمی‌گرداند که بلافاصله بعد از موقعیت فعلی مکان‌نمای ورودی متن قرار دارد.

> [!NOTE]
> بر اساس [مشخصات فرم‌های WHATWG](https://html.spec.whatwg.org/multipage/forms.html#concept-input-apply)، ویژگی `selectionEnd` فقط برای ورودی‌های نوع text، search، URL، tel و password اعمال می‌شود. در مرورگرهای مدرن، تنظیم ویژگی `selectionEnd` روی سایر انواع ورودی، استثنا (exception) پرتاب می‌کند. علاوه بر این، هنگام دسترسی به ویژگی `selectionEnd` روی عناصر ورودی غیرمتنی، این ویژگی مقدار `null` برمی‌گرداند.

اگر `selectionEnd` کوچک‌تر از `selectionStart` باشد، هر دو به‌عنوان مقدار `selectionEnd` در نظر گرفته می‌شوند.

## مقدار

یک عدد نامنفی.

## مثال‌ها

### HTML

```html
<!-- استفاده از selectionEnd روی عنصر ورودی غیرمتنی -->
<label for="color">ویژگی selectionStart روی نوع color</label>
<input id="color" type="color" />

<!-- استفاده از selectionEnd روی عنصر ورودی متنی -->
<fieldset>
  <legend>ویژگی selectionEnd روی نوع text</legend>
  <label for="pin">PIN را وارد کنید</label>
  <input type="text" id="pin" value="impossible PIN: 102-12-145" />
  <button id="pin-btn" type="button">تصحیح PIN</button>
</fieldset>
```

### جاوااسکریپت

```js
const colorEnd = document.getElementById("color");
const text = document.querySelector("#pin");
const pinBtn = document.querySelector("#pin-btn");
const validPinChecker = /^\d{3}-\d{2}-\d{3}/g;
const selectionEnd = text.value.length;
const selectedText = text.value.substring(text.selectionStart, selectionEnd);

pinBtn.addEventListener("click", () => {
  const correctedText = selectedText.replace(validPinChecker, "");
  text.value = correctedText;
});

// برای مشاهده خروجی، کنسول مرورگر را باز کنید
console.log(colorEnd.selectionEnd); // خروجی: null
```

### نتیجه

{{EmbedLiveSample("Examples")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی {{domxref("HTMLTextAreaElement.selectionEnd")}}
- ویژگی {{domxref("HTMLInputElement.selectionStart")}}
- روش {{domxref("HTMLInputElement.setSelectionRange")}}