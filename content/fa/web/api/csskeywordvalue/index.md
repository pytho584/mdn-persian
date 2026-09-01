---
title: CSSKeywordValue
slug: Web/API/CSSKeywordValue
page-type: web-api-interface
browser-compat: api.CSSKeywordValue
---

{{APIRef("CSS Typed Object Model API")}} {{AvailableInWorkers}}

رابط **`CSSKeywordValue`** از [API مدل شیء تایپ‌شده CSS](/en-US/docs/Web/API/CSS_Typed_OM_API) نشان‌دهندهٔ مقدار یک کلمه کلیدی یا شناسهٔ دیگر CSS است.

نام نمونهٔ این رابط یک {{Glossary("stringifier")}} (رشته‌ساز) است، بنابراین وقتی در هر جایی که یک رشته انتظار می‌رود استفاده شود، مقدار `CSSKeyword.value` را برمی‌گرداند.

{{InheritanceDiagram}}

## سازنده

- {{domxref("CSSKeywordValue.CSSKeywordValue", "CSSKeywordValue()")}}
  - : یک شیء `CSSKeywordValue` جدید می‌سازد.

## ویژگی‌های نمونه

- {{domxref('CSSKeywordValue.value')}}
  - : یک رشته که مقدار `CSSKeywordValue` را نشان می‌دهد.

## روش‌های نمونه

_همچنین روش‌هایی را از رابط والد خود، {{DOMxRef("CSSStyleValue")}}، به ارث می‌برد._

## مثال‌ها

### کاربرد پایه

این مثال ویژگی CSS {{cssxref('display')}} را با استفاده از `CSSKeywordValue` برای تعریف مقدار، روی `initial` تنظیم می‌کند.

#### HTML

HTML یک عنصر تعریف می‌کند که مقدار کلمه کلیدی `display` را روی آن تنظیم می‌کنیم، یک عنصر {{htmlelement("hr")}}، یک دکمه که برای تنظیم مقدار کلمه کلیدی `display` استفاده می‌شود، و یک دکمه «بازنشانی» برای بازنشانی مثال.

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

CSS ابتدا عنصر را روی `flex` تنظیم می‌کند که آن را مجبور به نمایش تمام‌عرض می‌کند، و یک حاشیه توپر با padding و margin به آن می‌دهد.

```css
#myElement {
  display: flex;
  border: solid;
  padding: 10px;
  margin: 5px;
}
```

#### JavaScript

کد ابتدا یک اشاره‌گر به دکمه «تنظیم initial» می‌گیرد و یک شنونده برای مدیریت رویداد کلیک هنگام فشار دادن آن اضافه می‌کند.

شنونده سپس استایل‌های درون‌خطی عنصر را با استفاده از {{domxref(Element.attributeStyleMap)}} می‌گیرد و ویژگی `display` را با یک `CSSKeywordValue` تازه ساخته شده تنظیم می‌کند. سپس مقدار آن کلمه کلیدی را در کنسول ثبت می‌کند.

```js
const setInitialButton = document.querySelector("#set-initial");

setInitialButton.addEventListener("click", () => {
  const myElementInlineStyles =
    document.getElementById("myElement").attributeStyleMap;
  myElementInlineStyles.set("display", new CSSKeywordValue("initial"));
  console.log(`display: ${myElementInlineStyles.get("display").value}`);
});
```

توجه داشته باشید که نمی‌توانیم مقدار استایل‌های درون‌خطی را قبل از فشار دادن دکمه ثبت کنیم، زیرا هیچ استایلی وجود ندارد.

```js hidden
const resetButton = document.querySelector("#reset");
resetButton.addEventListener("click", () => {
  window.location.reload(true);
});
```

#### نتیجه

روی عنصر کلیک راست کنید و [بازرس ابزار توسعه‌دهنده](https://firefox-source-docs.mozilla.org/devtools-user/page_inspector/how_to/select_an_element/index.html) را برای بازرسی استایل‌های آن باز کنید. باید ببینید که `display: flex` روی `#myElement` تنظیم شده است. دکمه «تنظیم initial» را فشار دهید تا استایل درون‌خطی `display` را روی `"initial"` تنظیم کنید. باید تغییر استایل‌ها را در بازرس ببینید، و عنصر نیز کمی کوچک می‌شود زیرا `flex` غیرفعال می‌شود.

{{EmbedLiveSample("Basic usage", 120, 150)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref('CSSImageValue')}}
- {{domxref('CSSNumericValue')}}
- {{domxref('CSSPositionValue')}}
- {{domxref('CSSTransformValue')}}
- {{domxref('CSSUnparsedValue')}}