---
title: "HTMLSelectElement: value property"
short-title: value
slug: Web/API/HTMLSelectElement/value
page-type: web-api-instance-property
browser-compat: api.HTMLSelectElement.value
---

{{ APIRef("HTML DOM") }}

ویژگی **`HTMLSelectElement.value`** شامل مقدار اولین عنصر {{htmlelement("option")}} انتخاب‌شده‌ای است که با این عنصر {{htmlelement("select")}} مرتبط است.

این ویژگی را می‌توان به‌طور مستقیم نیز مقداردهی کرد؛ برای مثال، برای تنظیم یک مقدار پیش‌فرض بر اساس یک شرط.

## Value

مقدار این ویژگی یک رشته (string) است که مقدار اولین عنصر {{htmlelement("option")}} انتخاب‌شده در این عنصر {{htmlelement("select")}} را در بر می‌گیرد؛ اگر هیچ گزینه‌ای انتخاب نشده باشد، رشتهٔ خالی است.

## Examples

### Retrieving the selected value

```html
<label for="bird-select">Choose a bird:</label>

<select name="birds" id="bird-select">
  <option value="">--Please choose an option--</option>
  <option value="Scarlet ibis">Scarlet ibis</option>
  <option value="Marabou stork">Marabou stork</option>
  <option value="Roseate spoonbill">Roseate spoonbill</option>
</select>

<pre id="log"></pre>
```

```js
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = text;
}

const select = document.querySelector("#bird-select");
select.addEventListener("change", () => {
  log(`Selection: ${select.value}`);
});
```

```css hidden
#log {
  height: 20px;
  padding: 0.5rem;
  border: 1px solid black;
}
```

{{EmbedLiveSample("Retrieving the selected value")}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- عنصر HTML {{HTMLElement("select")}} که این رابط را پیاده‌سازی می‌کند.