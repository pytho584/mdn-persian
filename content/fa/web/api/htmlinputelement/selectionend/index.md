---
title: "HTMLInputElement: selectionEnd property"
short-title: selectionEnd
slug: Web/API/HTMLInputElement/selectionEnd
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.selectionEnd
---

{{ApiRef("HTML DOM")}}

ویژگی **`selectionEnd`** از رابط {{domxref("HTMLInputElement")}} یک عدد است که نمایانگر اندیس پایانی متن انتخاب‌شده می‌باشد. به عبارت دیگر، این ویژگی اندیس کاراکتری را نشان می‌دهد که **بلافاصله پس از** انتخاب قرار دارد. همچنین، هنگامی که هیچ متنی انتخاب نشده باشد، این ویژگی افست (offset) کاراکتری را برمی‌گرداند که بلافاصله پس از موقعیت فعلی مکان‌نما (cursor) درون متن ورودی قرار دارد.

> [!NOTE]
> طبق [مشخصات فرم‌های WHATWG](https://html.spec.whatwg.org/multipage/forms.html#concept-input-apply) ویژگی `selectionEnd` تنها برای ورودی‌هایی از نوع text، search، URL، tel و password اعمال می‌شود. در مرورگرهای مدرن، تنظیم این ویژگی برای سایر انواع ورودی باعث بروز استثنا (exception) می‌شود. همچنین، دسترسی به `selectionEnd` در عناصر ورودی غیرمتنی مقدار `null` را برمی‌گرداند.

اگر مقدار `selectionEnd` کمتر از `selectionStart` باشد، هر دو به‌عنوان مقدار `selectionEnd` در نظر گرفته می‌شوند.

## مقدار

یک عدد غیرمنفی.

## مثال‌ها

### HTML

```html
<!-- استفاده از selectionEnd روی عنصر ورودی غیرمتنی -->
<label for="color">ویژگی selectionStart روی نوع color</label>
<input id="color" type="color" />

<!-- استفاده از selectionEnd روی عنصر ورودی متنی -->
<fieldset>
  <legend>ویژگی selectionEnd روی نوع text</legend>
  <label for="pin">کد PIN را وارد کنید</label>
  <input type="text" id="pin" value="کد PIN غیرممکن: 102-12-145" />
  <button id="pin-btn" type="button">تصحیح PIN</button>
</fieldset>
```

### JavaScript

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

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی {{domxref("HTMLTextAreaElement.selectionEnd")}}
- ویژگی {{domxref("HTMLInputElement.selectionStart")}}
- متد {{domxref("HTMLInputElement.setSelectionRange")}}