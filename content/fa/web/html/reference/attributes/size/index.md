---
title: "size HTML attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/size"
translated_by: "n8n + AI"
---

ویژگی (attribute) **`size`** عرض عنصر `<input>` و ارتفاع عنصر `<select>` را تعیین می‌کند. برای یک عنصر `input`، این ویژگی تعداد کاراکترهایی را مشخص می‌کند که user agent به کاربر اجازه می‌دهد هنگام ویرایش مقدار ببیند. برای عنصر `select`، تعداد گزینه‌هایی را که باید به کاربر نمایش داده شوند، معین می‌کند. این مقدار باید یک عدد صحیح نامنفی و بزرگ‌تر از صفر باشد.

اگر `size` مشخص نشود یا مقدار نامعتبری داده شود، عنصر `input` اندازه‌ی اعلام‌شده‌ای نخواهد داشت و عرض پیش‌فرض کنترل فرم بر اساس user agent خواهد بود. اگر CSS با propertyهایی که روی عرض تأثیر می‌گذارند، همان عنصر را هدف بگیرد، CSS اولویت دارد.

ویژگی `size` هیچ تأثیری بر اعتبارسنجی محدودیت‌ها (constraint validation) ندارد.

```html interactive-example
<label for="firstName">First Name:</label>
<input id="firstName" name="firstName" type="text" size="10" />

<label for="lastName">Last Name:</label>
<input id="lastName" name="lastName" type="text" size="20" />

<label for="fruit">Favorite fruit:</label>
<select id="fruit" name="fruit" size="2">
  <option>Orange</option>
  <option>Banana</option>
  <option>Apple</option>
</select>
```

```css interactive-example
label {
  display: block;
  margin-top: 1rem;
}
```

## مثال‌ها

با افزودن `size` به برخی تایپ‌های input، می‌توان عرض ورودی را کنترل کرد. افزودن `size` به یک select ارتفاع آن را تغییر می‌دهد و مشخص می‌کند در حالت بسته، چند گزینه قابل مشاهده باشد.

```html
<label for="fruit">Enter a fruit</label>
<input type="text" size="15" id="fruit" />
<label for="vegetable">Enter a vegetable</label>
<input type="text" id="vegetable" />

<select name="fruits" size="5">
  <option>banana</option>
  <option>cherry</option>
  <option>strawberry</option>
  <option>durian</option>
  <option>blueberry</option>
</select>

<select name="vegetables" size="5">
  <option>carrot</option>
  <option>cucumber</option>
  <option>cauliflower</option>
  <option>celery</option>
  <option>collard greens</option>
</select>
```

## مشخصات

## سازگاری مرورگر

## همچنین ببینید

- [`maxlength`](/en-US/docs/Web/HTML/Reference/Attributes/maxlength)
- [`minlength`](/en-US/docs/Web/HTML/Reference/Attributes/minlength)
- [`pattern`](/en-US/docs/Web/HTML/Reference/Attributes/pattern)