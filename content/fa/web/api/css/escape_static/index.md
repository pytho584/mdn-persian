---
title: "CSS: escape() static method"
---

---
title: "CSS: escape() static method"
short-title: escape()
slug: Web/API/CSS/escape_static
page-type: web-api-static-method
browser-compat: api.CSS.escape_static
---

{{APIRef("CSSOM")}}

متد ایستای **`CSS.escape()`** رشته‌ای را برمی‌گرداند که شامل رشتهٔ escape شدهٔ ارسال‌شده به‌عنوان پارامتر است؛ این متد بیشتر برای استفاده به‌عنوان بخشی از یک انتخابگر CSS به کار می‌رود.

## سینتکس

```js-nolint
CSS.escape(str)
```

### پارامترها

- `str`
  - : رشته‌ای که باید escape شود.

### مقدار بازگشتی

رشتهٔ escape شده.

## مثال‌ها

### نتایج پایه

<!-- Note: the {} need to be triple-escaped, once for Yari -->

```js-nolint
CSS.escape(".foo#bar"); // "\\.foo\\#bar"
CSS.escape("()[]{}"); // "\\(\\)\\[\\]\\\{\\\}"
CSS.escape('--a'); // "--a"
CSS.escape(0); // "\\30 ", the Unicode code point of '0' is 30
CSS.escape('\0'); // "\ufffd", the Unicode REPLACEMENT CHARACTER
```

### استفاده‌ها در زمینه

برای escape کردن یک رشته برای استفاده به‌عنوان بخشی از یک انتخابگر، می‌توان از متد `escape()` استفاده کرد:

```js
const element = document.querySelector(`#${CSS.escape(id)} > img`);
```

متد `escape()` همچنین می‌تواند برای escape کردن رشته‌ها استفاده شود، هرچند کاراکترهایی را escape می‌کند که لزوماً نیازی به escape شدن ندارند:

```js
const element = document.querySelector(`a[href="#${CSS.escape(fragment)}"]`);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رابط {{DOMxRef("CSS")}} که این متد ایستا در آن قرار دارد.
- [A polyfill for the CSS.escape](https://github.com/mathiasbynens/CSS.escape/blob/master/css.escape.js)