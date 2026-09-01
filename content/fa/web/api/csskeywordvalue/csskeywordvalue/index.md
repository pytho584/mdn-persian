---
title: "CSSKeywordValue: CSSKeywordValue() constructor"
short-title: CSSKeywordValue()
slug: Web/API/CSSKeywordValue/CSSKeywordValue
page-type: web-api-constructor
browser-compat: api.CSSKeywordValue.CSSKeywordValue
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

سازندهی **`CSSKeywordValue()`** یک شیء جدید از {{domxref("CSSKeywordValue")}} می‌سازد که یک کلیدواژه یا شناسه‌ی دیگر CSS را نمایش می‌دهد.

## سینتکس

```js-nolint
new CSSKeywordValue(value)
```

### پارامترها

- `value`
  - : یک {{jsxref('String')}} که برای تنظیم {{domxref("CSSKeywordValue.value")}} استفاده می‌شود.

### استثناها

- {{jsxref("TypeError")}}
  - : اگر پارامتر `value` مشخص نشده باشد، یا اگر یک رشته‌ی خالی باشد، پرتاب می‌شود.

## نمونه‌ها

### استفاده‌ی پایه

این مثال ویژگی CSS {{cssxref('display')}} را روی `initial` تنظیم می‌کند و یک `CSSKeywordValue` برای این کلیدواژه می‌سازد.

#### HTML

در HTML زیر، یک عنصر تعریف شده است که مقدار کلیدواژه‌ی `display` را روی آن تنظیم می‌کنیم؛ یک عنصر {{htmlelement("hr")}}، یک دکمه که برای تنظیم مقدار کلیدواژه‌ی `display` استفاده می‌شود، و یک دکمه‌ی «بازنشانی» برای بازگردانی مثال.

```html
<div id="myElement">
  Check the developer tools to see the log in the console and to inspect this
  div's style attributes.
</div>
<hr />
<button id="set-initial" type="button">Set initial</button>
<button id="reset" type="button">Reset</button>
```

#### CSS

CSS در ابتدا عنصر را روی `flex` تنظیم می‌کند که باعث می‌شود به‌صورت تمام‌عرض نمایش داده شود و یک حاشیه‌ی توپر به‌همراه padding و margin به آن می‌دهد.

```css
#myElement {
  display: flex;
  border: solid;
  padding: 10px;
  margin: 5px;
}
```

#### جاوااسکریپت

کد ابتدا به دکمه‌ی «Set initial» دسترسی پیدا می‌کند و یک شنونده به آن اضافه می‌کند تا رویداد کلیک هنگام فشرده‌شدن دکمه مدیریت شود.

شنونده سپس استایل‌های درون‌خطی عنصر را با استفاده از {{domxref("Element.attributeStyleMap")}} دریافت می‌کند و ویژگی `display` را با یک `CSSKeywordValue` تازه‌ساخته‌شده تنظیم می‌نماید. سپس مقدار آن کلیدواژه را در کنسول ثبت می‌کند.

```js
const setInitialButton = document.querySelector("#set-initial");

setInitialButton.addEventListener("click", () => {
  const myElementInlineStyles =
    document.getElementById("myElement").attributeStyleMap;
  myElementInlineStyles.set("display", new CSSKeywordValue("initial"));
  console.log(`display: ${myElementInlineStyles.get("display").value}`);
});
```

توجه داشته باشید که نمی‌توانیم مقدار استایل‌های درون‌خطی را قبل از فشردن دکمه ثبت کنیم، چون چنین استایلی وجود ندارد.

```js hidden
const resetButton = document.querySelector("#reset");
resetButton.addEventListener("click", () => {
  window.location.reload(true);
});
```

#### نتیجه

روی عنصر کلیک راست کنید و [بازرس ابزار توسعه‌دهنده](https://firefox-source-docs.mozilla.org/devtools-user/page_inspector/how_to/select_an_element/index.html) را باز کنید تا استایل‌های آن را بررسی نمایید. باید ببینید که `display: flex` روی `#myElement` تنظیم شده است. دکمه‌ی «Set initial» را فشار دهید تا استایل درون‌خطیِ `display` برابر با `"initial"` تنظیم شود. در بازرس شاهد تغییر استایل‌ها خواهید بود؛ همچنین عنصر کمی جمع می‌شود، چون `flex` غیرفعال می‌گردد.

{{EmbedLiveSample("Basic usage", 120, 150)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}