---
title: "HTMLInputElement: value property"
short-title: value
slug: Web/API/HTMLInputElement/value
page-type: web-api-instance-property
browser-compat: api.HTMLInputElement.value
---

{{ APIRef("HTML DOM") }}

ویژگی **`value`** در رابط {{DOMxRef("HTMLInputElement")}} مقدار کنونی عنصر {{htmlelement("input")}} را به‌صورت یک رشته نمایش می‌دهد.

این ویژگی را می‌توان به‌طور مستقیم نیز تنظیم کرد، برای مثال برای تعیین یک مقدار پیش‌فرض بر اساس یک شرط.

## Value

یک رشته که مقدار پیش‌فرض عنصر {{htmlelement("input")}} را مشخص می‌کند.

## Examples

### بازیابی مقدار یک ورودی متنی

در این مثال، لاگ مقدار کنونی را هنگام وارد کردن داده توسط کاربر در ورودی نمایش می‌دهد.

#### HTML

ما یک {{htmlelement("input")}} و یک {{htmlelement("label")}} مرتبط را همراه با یک ظرف {{htmlelement("pre")}} برای خروجی قرار داده‌ایم.

```html
<label for="given-name">Your name:</label>

<input name="given-name" id="given-name" />

<pre id="log"></pre>
```

#### JavaScript

مقدار {{domxref("HTMLElement.innerText", "innerText")}} عنصر `<pre>` به مقدار کنونی `<input>` به‌روزرسانی می‌شود هر زمان که رویداد {{domxref("Element/keyup_event", "keyup")}} رخ دهد.

```js
const logElement = document.getElementById("log");
const inputElement = document.getElementById("given-name");

inputElement.addEventListener("keyup", () => {
  logElement.innerText = `Name: ${inputElement.value}`;
});
```

```css hidden
#log {
  height: 20px;
  padding: 0.5rem;
  background-color: #ededed;
}
```

#### نتایج

{{EmbedLiveSample("Retrieving a text input's value", "", 100)}}

### بازیابی مقدار رنگ

این مثال نشان می‌دهد که ویژگی `value` با یک `<input>` از نوع {{HTMLElement("input/color", "color")}} چگونه کار می‌کند.

#### HTML

ما یک `<input>` از نوع `color` قرار داده‌ایم:

```html
<label for="color">Pick a color:</label>

<input name="color" id="color" type="color" />

<pre id="log"></pre>
```

#### JavaScript

مقدار {{domxref("HTMLElement.innerText", "innerText")}} عنصر `<pre>` با مقدار رنگ پیش‌فرض (`#000000`) به‌روزرسانی می‌شود و سپس هر بار که رویداد {{domxref("HTMLElement/change_event", "change")}} رخ دهد، دوباره به‌روزرسانی می‌شود.

```js
const logElement = document.getElementById("log");
const inputElement = document.getElementById("color");

logElement.innerText = `Color: ${inputElement.value}`;

inputElement.addEventListener("change", () => {
  logElement.innerText = `Color: ${inputElement.value}`;
});
```

```css hidden
#log {
  height: 20px;
  padding: 0.5rem;
  background-color: #ededed;
}
```

#### نتایج

{{EmbedLiveSample("Retrieving a color value", "", 100)}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## جستارهای وابسته

- {{HTMLElement("input")}}
- {{DOMXref("HTMLInputElement.valueAsDate")}}
- {{DOMXref("HTMLInputElement.valueAsNumber")}}