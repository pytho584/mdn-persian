---
title: "HTMLElement: focus() method"
short-title: focus()
slug: Web/API/HTMLElement/focus
page-type: web-api-instance-method
browser-compat: api.HTMLElement.focus
---

{{ APIRef("HTML DOM") }}

متد **`HTMLElement.focus()`** فوکوس (تمرکز) را روی عنصر مشخص‌شده قرار می‌دهد، در صورتی که بتوان روی آن فوکوس کرد. عنصر فوکوس‌شده عنصری است که به طور پیش‌فرض رویدادهای صفحه‌کلید و رویدادهای مشابه را دریافت می‌کند.

به طور پیش‌فرض، مرورگر پس از فوکوس کردن، عنصر را به درون نمای دید اسکرول می‌کند و ممکن است نشانه‌ای بصری از عنصر فوکوس‌شده (معمولاً با نمایش یک «حلقه فوکوس» در اطراف عنصر) ارائه دهد. گزینه‌های پارامتر برای غیرفعال کردن اسکرول پیش‌فرض و اجبار نمایش نشانه بصری روی عناصر فراهم شده است.

## نحو (Syntax)

```js-nolint
focus()
focus(options)
```

### پارامترها

- `options` {{optional_inline}}
  - : یک شیء اختیاری برای کنترل جنبه‌های فرایند فوکوس. این شیء ممکن است شامل ویژگی‌های زیر باشد:
    - `preventScroll` {{optional_inline}}
      - : یک مقدار بولین که نشان می‌دهد آیا مرورگر باید سند را اسکرول کند تا عنصر تازه فوکوس‌شده را در معرض دید قرار دهد یا خیر. مقدار `false` برای `preventScroll` (پیش‌فرض) به این معنی است که مرورگر پس از فوکوس کردن، عنصر را در معرض دید اسکرول می‌کند. اگر `preventScroll` برابر `true` تنظیم شود، هیچ اسکرولی رخ نخواهد داد.
    - `focusVisible` {{optional_inline}} {{experimental_inline}}
      - : یک مقدار بولین که باید برای اجبار نمایش نشانه بصری فوکوس روی `true`، یا برای جلوگیری از آن روی `false` تنظیم شود. اگر این ویژگی مشخص نشود، مرورگر در صورت تشخیص اینکه این کار باعث بهبود دسترسی برای کاربران می‌شود، نشانه بصری را نمایش می‌دهد.

### مقدار بازگشتی

هیچکدام ({{jsxref("undefined")}}).

## مثال‌ها

### فوکوس روی یک فیلد متنی

این مثال از یک دکمه برای تنظیم فوکوس روی یک فیلد متنی استفاده می‌کند.

#### HTML

```html
<input id="myTextField" value="Text field." />
<button id="focusButton">Click to set focus on the text field</button>
```

#### JavaScript

کد زیر یک کنترل‌کننده رویداد برای تنظیم فوکوس روی فیلد متنی هنگام فشار دادن دکمه اضافه می‌کند. توجه داشته باشید که اکثر مرورگرها به طور خودکار نشانه بصری (یک «حلقه فوکوس») برای یک فیلد متنی فوکوس‌شده اضافه می‌کنند، بنابراین کد `focusVisible` را روی `true` تنظیم نمی‌کند.

```js
document.getElementById("focusButton").addEventListener("click", () => {
  document.getElementById("myTextField").focus();
});
```

#### نتیجه

دکمه را انتخاب کنید تا فوکوس روی فیلد متنی تنظیم شود.

{{ EmbedLiveSample('Focus_on_a_text_field') }}

### فوکوس روی یک دکمه

این مثال نشان می‌دهد که چگونه می‌توانید روی یک عنصر دکمه فوکوس تنظیم کنید.

#### HTML

ابتدا سه دکمه تعریف می‌کنیم. هر دو دکمه وسط و راست، فوکوس را روی دکمه سمت چپ تنظیم می‌کنند. دکمه سمت راست همچنین `focusVisible` را مشخص می‌کند.

```html
<button id="myButton">Button</button>
<button id="focusButton">Click to set focus on "Button"</button>
<button id="focusButtonVisibleIndication">
  Click to set focus and focusVisible on "Button"
</button>
```

#### JavaScript

کد زیر کنترل‌کننده‌هایی برای رویدادهای کلیک روی دکمه‌های وسط و راست تنظیم می‌کند.

```js
document.getElementById("focusButton").addEventListener("click", () => {
  document.getElementById("myButton").focus();
});

document
  .getElementById("focusButtonVisibleIndication")
  .addEventListener("click", () => {
    document.getElementById("myButton").focus({ focusVisible: true });
  });
```

#### نتیجه

دکمه وسط یا دکمه سمت راست را انتخاب کنید تا فوکوس روی دکمه سمت چپ تنظیم شود.

مرورگرها معمولاً هنگام تنظیم برنامه‌ریزی‌شده فوکوس روی عناصر دکمه، نشانه بصری فوکوس را نشان نمی‌دهند، بنابراین اثر انتخاب دکمه وسط ممکن است واضح نباشد. با این حال، اگر گزینه `focusVisible` در مرورگر شما پشتیبانی شود، باید تغییر فوکوس روی دکمه سمت چپ را هنگام انتخاب دکمه سمت راست مشاهده کنید.

{{ EmbedLiveSample('Focus_on_a_button') }}

### فوکوس با و بدون اسکرول

این مثال اثر تنظیم فوکوس با گزینه [`preventScroll`](#preventscroll) را روی `true` و `false` (پیش‌فرض) نشان می‌دهد.

#### HTML

HTML دو دکمه را تعریف می‌کند که برای تنظیم فوکوس روی یک دکمه سوم که خارج از صفحه است استفاده می‌شوند.

```html
<button id="focus_scroll">Click to set focus on off-screen button</button>
<button id="focus_no_scroll">
  Click to set focus on offscreen button without scrolling
</button>

<div id="container">
  <button id="myButton">Button</button>
</div>
```

```css hidden
#myButton {
  margin-top: 500px; /* دکمه را خارج از صفحه قرار می‌دهد */
}
```

#### JavaScript

این کد یک کنترل‌کننده رویداد کلیک روی دکمه‌های اول و دوم برای تنظیم فوکوس روی آخرین دکمه تنظیم می‌کند. توجه داشته باشید که کنترل‌کننده اول گزینه `preventScroll` را مشخص نمی‌کند، بنابراین اسکرول به عنصر فوکوس‌شده فعال خواهد بود.

```js
document.getElementById("focus_scroll").addEventListener("click", () => {
  document.getElementById("myButton").focus(); // پیش‌فرض: {preventScroll:false}
});

document.getElementById("focus_no_scroll").addEventListener("click", () => {
  document.getElementById("myButton").focus({ preventScroll: true });
});
```

#### نتیجه

دکمه اول را انتخاب کنید تا فوکوس تنظیم شود و به دکمه خارج از صفحه اسکرول شود. انتخاب دکمه دوم فوکوس را تنظیم می‌کند، اما اسکرول غیرفعال است.

{{ EmbedLiveSample('Focus with and without scrolling') }}

## مشخصات

{{Specifications}}

## یادداشت‌ها

- اگر `HTMLElement.focus()` را از یک کنترل‌کننده رویداد mousedown فراخوانی می‌کنید، باید `event.preventDefault()` را فراخوانی کنید تا از خروج فوکوس از `HTMLElement` جلوگیری شود.
- رفتار فوکوس در رابطه با ویژگی‌های مختلف HTML مانند [`tabindex`](/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex) یا {{Glossary("shadow tree", "shadow dom")}}، که پیش‌تر به طور کامل مشخص نشده بودند، در اکتبر 2019 به‌روزرسانی شدند. برای اطلاعات بیشتر به [وبلاگ WHATWG](https://blog.whatwg.org/focusing-on-focus) مراجعه کنید.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLElement.blur")}} برای حذف فوکوس از یک عنصر.
- {{domxref("document.activeElement")}} برای دانستن اینکه کدام عنصر در حال حاضر فوکوس شده است.