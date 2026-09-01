---
title: "HTMLInputElement: select() method"
short-title: select()
slug: Web/API/HTMLInputElement/select
page-type: web-api-instance-method
browser-compat: api.HTMLInputElement.select
---

{{ APIRef("HTML DOM") }}

متد **`HTMLInputElement.select()`** تمام متن موجود در یک عنصر {{HTMLElement("textarea")}} یا یک عنصر {{HTMLElement("input")}} که شامل فیلد متنی است را انتخاب می‌کند.

## نحو (Syntax)

```js-nolint
select()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

در این مثال، با کلیک روی دکمه، تمام متن داخل عنصر `<input>` انتخاب می‌شود.

### HTML

```html
<input type="text" id="text-box" size="20" value="Hello world!" />
<button>Select text</button>
```

### JavaScript

```js
function selectText() {
  const input = document.getElementById("text-box");
  input.focus();
  input.select();
}

document.querySelector("button").addEventListener("click", selectText);
```

### نتیجه

{{EmbedLiveSample("Examples")}}

## نکات

فراخوانی `element.select()` لزوماً باعث فوکوس کردن ورودی نمی‌شود، بنابراین معمولاً همراه با {{domxref("HTMLElement.focus")}} استفاده می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{ HTMLElement("input") }}
- {{ HTMLElement("textarea") }}
- {{ domxref("HTMLInputElement") }}
- {{ domxref("HTMLInputElement.setSelectionRange") }}