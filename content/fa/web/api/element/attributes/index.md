---
title: "Element: attributes property"
short-title: attributes
slug: Web/API/Element/attributes
page-type: web-api-instance-property
browser-compat: api.Element.attributes
---

{{ APIRef("DOM") }}

ویژگی **`Element.attributes`** یک مجموعهٔ زنده (live collection) از تمام گره‌های ویژگی (attribute nodes) ثبت‌شده روی گرهٔ مشخص‌شده را بازمی‌گرداند. این ویژگی یک {{domxref("NamedNodeMap")}} است، نه یک `Array`، بنابراین هیچ‌یک از متدهای {{jsxref("Array")}} را ندارد و ایندکس گره‌های {{domxref("Attr")}} ممکن است در مرورگرهای مختلف متفاوت باشد. به بیان دقیق‌تر، `attributes` یک جفت‌کلید/مقدار از رشته‌هاست که هر اطلاعات مربوط به آن ویژگی را نشان می‌دهد.

## مقدار

یک شیء {{domxref("NamedNodeMap")}}.

## مثال‌ها

### مثال‌های پایه

```js
// دریافت اولین عنصر <p> در سند
const paragraph = document.querySelector("p");
const attributes = paragraph.attributes;
```

### شمارش ویژگی‌های عنصر

می‌توانید ویژگی‌های یک عنصر را با استفاده از [`for...of`](/en-US/docs/Web/JavaScript/Reference/Statements/for...of) شمارش کنید. مثال زیر گره‌های ویژگی عنصر را در سند با شناسه «paragraph» مرور می‌کند و مقدار هر ویژگی را چاپ می‌کند.

```html
<p id="paragraph" class="green" contenteditable>Sample Paragraph</p>
<input type="button" value="Show paragraph attribute name and value" />
<pre id="result"></pre>
```

```css
.green {
  color: green;
}
```

```js
const paragraph = document.getElementById("paragraph");
const result = document.getElementById("result");
const btn = document.querySelector("input[type='button']");

btn.addEventListener("click", () => {
  // First, let's verify that the paragraph has some attributes
  if (paragraph.hasAttributes()) {
    let output = "Attributes of first paragraph:\n";
    for (const attr of paragraph.attributes) {
      output += `${attr.name} -> ${attr.value}\n`;
    }
    result.textContent = output;
  } else {
    result.textContent = "No attributes to show";
  }
});
```

{{EmbedLiveSample('enumerating_elements_attributes', 100, 300)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("NamedNodeMap")}}، رابط شیء بازگشتی
- ملاحظات سازگاری بین مرورگرها: در [quirksmode](https://quirksmode.org/dom/core/#attributes)