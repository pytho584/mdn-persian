---
title: "HTMLInputElement: select() method"
short-title: select()
slug: Web/API/HTMLInputElement/select
page-type: web-api-instance-method
browser-compat: api.HTMLInputElement.select
---

{{ APIRef("HTML DOM") }}

**`HTMLInputElement.select()`** روشی است که تمام متن موجود در یک عنصر {{HTMLElement("textarea")}} یا در یک عنصر {{HTMLElement("input")}} حاوی فیلد متنی را انتخاب میکند.

## نحو

```js-nolint
select()
```

### پارامترها

هیچ.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثالها

در این مثال، روی دکمه کلیک کنید تا تمام متن درون عنصر `<input>` انتخاب شود.

### HTML

```html
<input type="text" id="text-box" size="20" value="Hello world!" />
<button>انتخاب متن</button>
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

فراخوانی `element.select()` لزوماً ورودی را فوکوس نمیکند، بنابراین معمولاً همراه با {{domxref("HTMLElement.focus")}} استفاده میشود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{ HTMLElement("input") }}
- {{ HTMLElement("textarea") }}
- {{ domxref("HTMLInputElement") }}
- {{ domxref("HTMLInputElement.setSelectionRange") }}