---
title: "maxlength HTML attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/maxlength"
translated_by: "n8n + AI"
---

ویژگی **`maxlength`** حداکثر [طول رشته](/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/length) را تعیین می‌کند که کاربر می‌تواند در یک `<input>` یا `<textarea>` وارد کند. این ویژگی باید مقدار عدد صحیحی برابر یا بزرگ‌تر از ۰ داشته باشد.

طول بر اساس «واحدهای کد UTF-16» (UTF-16 code units) اندازه‌گیری می‌شود که اغلب — اما نه همیشه — با تعداد کاراکترها برابر است. اگر `maxlength` مشخص نشده باشد یا مقدار نامعتبر داشته باشد، ورودی حداکثر طول نخواهد داشت.

هر مقدار `maxlength` باید بزرگ‌تر یا مساوی مقدار [`minlength`](/en-US/docs/Web/HTML/Reference/Attributes/minlength) باشد، در صورتی که آن مقدار وجود داشته باشد و معتبر باشد. اگر طول مقدار متنی فیلد بیشتر از `maxlength` واحد کد UTF-16 باشد، اعتبارسنجی محدودیت با شکست مواجه می‌شود. اعتبارسنجی محدودیت فقط زمانی اعمال می‌شود که کاربر مقدار را تغییر دهد.

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

## توضیحات

### اعتبارسنجی محدودیت

در حالی که مرورگر معمولاً از ورود متن بیشتر از حد مجاز `maxlength` جلوگیری می‌کند، اگر طول متن بیشتر از حد مجاز شود، خاصیت فقط‌خواندنی `tooLong` از شیء `ValidityState` مقدار `true` خواهد گرفت.

## مثال‌ها

```html
<input type="password" maxlength="4" />
```

## همچنین ببینید

- [`minlength`](/en-US/docs/Web/HTML/Reference/Attributes/minlength)
- [`size`](/en-US/docs/Web/HTML/Reference/Attributes/size)
- [`pattern`](/en-US/docs/Web/HTML/Reference/Attributes/pattern)
- [اعتبارسنجی محدودیت](/en-US/docs/Web/HTML/Guides/Constraint_validation)
- [اعتبارسنجی فرم](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)