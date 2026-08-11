---
title: "minlength HTML attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/minlength"
translated_by: "n8n + AI"
---

ویژگی **`minlength`** حداقل [طول رشته](/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/length) را تعیین می‌کند که کاربر می‌تواند در یک `<input>` یا `<textarea>` وارد کند. این ویژگی باید یک مقدار صحیح (integer) برابر با ۰ یا بیشتر باشد.

طول بر حسب واحدهای کد UTF-16 (UTF-16 code units) سنجیده می‌شود، که اغلب اما نه همیشه با تعداد کاراکترها برابر است. اگر `minlength` مشخص نشود یا مقدار نامعتبری داشته باشد، ورودی هیچ حداقل طولی نخواهد داشت. این مقدار باید کمتر یا مساوی مقدار [maxlength](/en-US/docs/Web/HTML/Reference/Attributes/maxlength) باشد؛ در غیر این صورت مقدار ورودی هرگز معتبر نخواهد بود، چون برآوردن هر دو شرط غیرممکن است.

اگر طول مقدار متنی فیلد کمتر از `minlength` (بر اساس واحدهای کد UTF-16) باشد، ورودی در اعتبارسنجی محدودیت‌ها (constraint validation) ناموفق خواهد بود و `validityState.tooShort` مقدار `true` را برمی‌گرداند. اعتبارسنجی محدودیت‌ها فقط زمانی اعمال می‌شود که کاربر مقدار را تغییر داده باشد. پس از شکست در ارسال، برخی مرورگرها پیام خطایی نشان می‌دهند که حداقل طول لازم و طول فعلی را مشخص می‌کند.

`minlength` به معنای [`required`](/en-US/docs/Web/HTML/Reference/Attributes/required) نیست؛ ورودی تنها زمانی قانون `minlength` را نقض می‌کند که کاربر مقداری وارد کرده باشد. اگر یک ورودی `required` نباشد، حتی با وجود `minlength` می‌توان رشتهٔ خالی ارسال کرد.

```html interactive-example
<label for="name">Product name:</label>
<input
  id="name"
  name="name"
  type="text"
  value="Shampoo"
  minlength="3"
  maxlength="20"
  required />

<label for="description">Product description:</label>
<textarea
  id="description"
  name="description"
  minlength="10"
  maxlength="40"
  required></textarea>
```

```css interactive-example
label {
  display: block;
  margin-top: 1em;
}

input:valid,
textarea:valid {
  background-color: palegreen;
}
```

## مثال‌ها

با افزودن `minlength="5"`، مقدار باید یا خالی باشد یا پنج کاراکتر یا بیشتر داشته باشد تا معتبر باشد.

```html
<label for="fruit">Enter a fruit name that is at least 5 letters long</label>
<input type="text" minlength="5" id="fruit" />
```

می‌توانیم از شبه‌کلاس‌ها (pseudoclasses) برای استایل‌دهی به عنصر بر اساس معتبر بودن مقدار استفاده کنیم. مقدار تا زمانی معتبر است که یا null (خالی) باشد یا پنج کاراکتر یا بیشتر داشته باشد. _Lime_ نامعتبر است و _lemon_ معتبر.

```css
input {
  border: 2px solid currentColor;
}
input:invalid {
  border: 2px dashed red;
}
input:invalid:focus {
  background-image: linear-gradient(pink, lightgreen);
}
```

## همچنین ببینید

- [`maxlength`](/en-US/docs/Web/HTML/Reference/Attributes/maxlength)
- [`size`](/en-US/docs/Web/HTML/Reference/Attributes/size)
- [`pattern`](/en-US/docs/Web/HTML/Reference/Attributes/pattern)
- [اعتبارسنجی محدودیت‌ها](/en-US/docs/Web/HTML/Guides/Constraint_validation)
- [اعتبارسنجی فرم](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
- `<input>`