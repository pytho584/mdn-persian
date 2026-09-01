---
title: "HTMLOptionElement: Option() constructor"
short-title: Option()
slug: Web/API/HTMLOptionElement/Option
page-type: web-api-constructor
browser-compat: api.HTMLOptionElement.Option
---

{{APIRef("HTML DOM")}}

سازندهٔ **`Option()`** یک {{domxref("HTMLOptionElement")}} جدید می‌سازد.

## نحو (Syntax)

```js-nolint
new Option()
new Option(text)
new Option(text, value)
new Option(text, value, defaultSelected)
new Option(text, value, defaultSelected, selected)
```

### پارامترها

- `text` {{optional_inline}}
  - : رشته‌ای که محتوای عنصر را نشان می‌دهد، یعنی متنی که نمایش داده می‌شود. اگر مشخص نشود، مقدار پیش‌فرض `""` (رشتهٔ خالی) استفاده می‌شود.
- `value` {{optional_inline}}
  - : رشته‌ای که مقدار {{domxref("HTMLOptionElement")}} را نشان می‌دهد، یعنی ویژگی value معادل {{htmlelement("option")}}. اگر مشخص نشود، مقدار `text` به‌عنوان مقدار استفاده می‌شود، مثلاً برای مقدار عنصر {{htmlelement("select")}} مرتبط وقتی فرم به سرور ارسال می‌شود.
- `defaultSelected` {{optional_inline}}
  - : مقداری `true` یا `false` که ویژگی [`selected`](/en-US/docs/Web/HTML/Reference/Elements/option#selected) را تنظیم می‌کند، یعنی این {{htmlelement("option")}} به‌عنوان مقدار پیش‌فرض در عنصر {{htmlelement("select")}} هنگام بارگذاری اولیهٔ صفحه انتخاب می‌شود. اگر مشخص نشود، مقدار پیش‌فرض `false` استفاده می‌شود. توجه کنید که مقدار `true` باعث نمی‌شود گزینه در حالتی که از قبل انتخاب نشده است، انتخاب شود.
- `selected` {{optional_inline}}
  - : مقداری `true` یا `false` که وضعیت انتخاب گزینه را تنظیم می‌کند؛ پیش‌فرض `false` است (انتخاب‌نشده). اگر حذف شود، حتی اگر آرگومان `defaultSelected` برابر `true` باشد، گزینه انتخاب نمی‌شود.

## مثال‌ها

### فقط افزودن گزینه‌های جدید

```js
/* فرض کنید HTML زیر را داریم
<select id='s'>

</select>
*/

const s = document.getElementById("s");
const options = [Four, Five, Six];

options.forEach((element, key) => {
  s[key] = new Option(element, key);
});
```

### افزودن گزینه‌ها با پارامترهای مختلف

```html
<select id="s"></select>
```

```js
const s = document.getElementById("s");
const options = ["zero", "one", "two"];

options.forEach((element, key) => {
  if (element === "zero") {
    s[key] = new Option(element, s.options.length, false, false);
  }
  if (element === "one") {
    s[key] = new Option(element, s.options.length, true, false); // ویژگی "selected" را اضافه می‌کند
  }
  if (element === "two") {
    s[key] = new Option(element, s.options.length, false, true); // در واقع در دید کاربر انتخاب می‌شود
  }
});
```

نتیجه:

```html
<select id="s">
  <option value="0">zero</option>
  <option value="1" selected>one</option>
  <option value="2">two</option>
  <!-- کاربر «two» را به‌عنوان انتخاب‌شده می‌بیند -->
</select>
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}