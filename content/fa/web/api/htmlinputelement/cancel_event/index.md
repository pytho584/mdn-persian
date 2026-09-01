---
title: "HTMLInputElement: cancel event"
short-title: cancel
slug: Web/API/HTMLInputElement/cancel_event
page-type: web-api-event
browser-compat: api.HTMLInputElement.cancel_event
---

{{APIRef("HTML DOM")}}

رویداد **`cancel`** روی یک عنصر {{HTMLElement("input")}} زمانی رخ می‌دهد که کاربر گفتگوی انتخاب فایل را از طریق کلید <kbd>Esc</kbd> یا دکمهٔ «انصراف» (cancel) ببندد، و همچنین وقتی کاربر همان فایل‌هایی را که قبلاً برای `type="file"` انتخاب شده بود دوباره انتخاب کند.

این رویداد قابل لغو (cancelable) نیست، اما می‌تواند حباب (bubble) شود.

## نحو (Syntax)

برای استفاده، نام رویداد را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به کار ببرید، یا یک ویژگی کنترل‌کنندهٔ رویداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("cancel", (event) => { })

oncancel = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

### لغو کردن یک عنصر ورودی

#### HTML

```html
<label for="file">یک فایل انتخاب کنید. یا نکنید.</label>
<input type="file" id="file" name="file" />

<div id="result"></div>
```

```css hidden
div {
  margin-bottom: 10px;
}
```

#### JavaScript

```js
const elem = document.getElementById("file");

const result = document.getElementById("result");

elem.addEventListener("cancel", () => {
  result.textContent = "لغو شد.";
});

elem.addEventListener("change", () => {
  if (elem.files.length === 1) {
    result.textContent = "فایل انتخاب شد.";
  }
});
```

#### نتیجه

{{ EmbedLiveSample('Canceling an input element', '100%', '100px') }}

انتخابگر فایل را باز کنید، سپس گفتگوی انتخاب را با کلید Escape یا دکمهٔ «انصراف» ببندید. هر دوی این کارها باعث می‌شوند رویداد `cancel` رخ دهد. همچنین، سعی کنید یک فایل محلی از دستگاه خود انتخاب کنید؛ سپس دوباره پنجرهٔ انتخاب فایل را باز کنید و همان فایل را دوباره انتخاب کنید. این نیز باعث رخ دادن رویداد `cancel` می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- عنصر HTML {{HTMLElement("input")}}