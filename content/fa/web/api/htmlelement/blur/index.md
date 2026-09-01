---
title: "HTMLElement: blur() method"
short-title: blur()
slug: Web/API/HTMLElement/blur
page-type: web-api-instance-method
browser-compat: api.HTMLElement.blur
---

{{APIRef("HTML DOM")}}

متد **`HTMLElement.blur()`** فوکوس صفحه‌کلید را از عنصر جاری حذف می‌کند.

## نحو (Syntax)

```js-nolint
blur()
```

### پارامترها

هیچ‌کدام.

### مقدار برگشتی

هیچ‌کدام ({{jsxref("undefined")}}).

## مثال‌ها

### حذف فوکوس از یک ورودی متنی

#### HTML

```html
<input type="text" id="sampleText" value="Sample Text" /><br /><br />
<button type="button">برای دریافت فوکوس کلیک کنید</button>
```

#### JavaScript

```js
const textField = document.getElementById("sampleText");
const button = document.querySelector("button");

function focusInput() {
  textField.focus();

  // ورودی پس از ۳ ثانیه فوکوس خود را از دست می‌دهد
  setTimeout(() => {
    textField.blur();
  }, 3000);
}

button.addEventListener("click", focusInput);
```

#### نتیجه

{{ EmbedLiveSample('Remove_focus_from_a_text_input') }}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLElement.focus")}}