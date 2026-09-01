---
title: "HTMLTableColElement: span property"
short-title: span
slug: Web/API/HTMLTableColElement/span
page-type: web-api-instance-property
browser-compat: api.HTMLTableColElement.span
---

{{ APIRef("HTML DOM") }}

ویژگی **`span`** از رابط {{domxref("HTMLTableColElement")}} تعداد ستون‌هایی را که این عنصر {{htmlelement("col")}} یا {{htmlelement("colgroup")}} باید بپوشاند، مشخص می‌کند. این ویژگی به ستون اجازه می‌دهد فضای چندین ستون از جدول را اشغال کند. این ویژگی منعکس‌کنندهٔ ویژگی [`span`](/en-US/docs/Web/HTML/Reference/Elements/col#span) است.

## مقدار

یک عدد مثبت که تعداد ستون‌ها را نشان می‌دهد.

> [!NOTE]
> هنگام تنظیم یک مقدار جدید، مقدار به نزدیک‌ترین عدد کاملاً مثبت (تا ۱۰۰۰) _محدود_ می‌شود.

## مثال‌ها

این مثال دو دکمه برای تغییر پوشش ستون اولین سلول بدنه ارائه می‌دهد.

### HTML

```html
<table>
  <colgroup>
    <col />
    <col span="2" class="multiColumn" />
  </colgroup>
  <thead>
    <tr>
      <th></th>
      <th scope="col">C1</th>
      <th scope="col">C2</th>
      <th scope="col">C3</th>
      <th scope="col">C4</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Row 1</th>
      <td>cell</td>
      <td>cell</td>
      <td>cell</td>
      <td>cell</td>
    </tr>
  </tbody>
</table>
<button id="increase">Increase column span</button>
<button id="decrease">Decrease column span</button>
<div>The first &lt;col&gt; spans <output>2</output> actual column(s).</div>
```

```css hidden
table {
  border-collapse: collapse;
}

th,
td,
table {
  border: 1px solid black;
}

button {
  margin: 1em 1em 1em 0;
}
```

### CSS

```css
.multiColumn {
  background-color: #d7d9f2;
}
```

### JavaScript

```js
// Obtain relevant interface elements
const col = document.querySelectorAll("col")[1];
const output = document.querySelectorAll("output")[0];

const increaseButton = document.getElementById("increase");
const decreaseButton = document.getElementById("decrease");

increaseButton.addEventListener("click", () => {
  col.span += 1;

  // Update the display
  output.textContent = col.span;
});

decreaseButton.addEventListener("click", () => {
  col.span -= 1;

  // Update the display
  output.textContent = col.span;
});
```

### نتیجه

{{EmbedLiveSample("Examples", "100%", 175)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLTableCellElement.colSpan")}}