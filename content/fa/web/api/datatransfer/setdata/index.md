---
title: "DataTransfer: setData() method"
short-title: setData()
slug: Web/API/DataTransfer/setData
page-type: web-api-instance-method
browser-compat: api.DataTransfer.setData
---

{{APIRef("HTML Drag and Drop API")}}

متد **`DataTransfer.setData()`** دادهٔ عملیات درگ را با داده و نوع مشخص‌شده تنظیم می‌کند. اگر داده‌ای برای نوع مشخص‌شده وجود نداشته باشد، در انتهای ذخیره‌گاه دادهٔ درگ اضافه می‌شود، به‌طوری که آخرین مورد در فهرست {{domxref("DataTransfer.types","types")}} نوع جدید خواهد بود. اگر داده‌ای برای نوع مشخص‌شده از قبل وجود داشته باشد، دادهٔ موجود در همان موقعیت جایگزین می‌شود. به عبارت دیگر، ترتیب فهرست {{domxref("DataTransfer.types","types")}} هنگام جایگزینی داده‌های همان نوع تغییر نمی‌کند.

نمونه‌هایی از انواع داده عبارت‌اند از `text/plain` و `text/uri-list`.

## نحو

```js-nolint
setData(format, data)
```

### پارامترها

- `format`
  - : یک رشته که نوع دادهٔ درگ مورد نظر برای افزودن به {{domxref("DataTransfer")}} را نشان می‌دهد.
- `data`
  - : یک رشته که دادهٔ مورد نظر برای افزودن به {{domxref("DataTransfer")}} را نشان می‌دهد.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

### کشیدن یک عنصر

در این مثال می‌توانیم یک عنصر {{HTMLElement("p")}} را به داخل یک عنصر هدف {{HTMLElement("div")}} بکشیم.

- در مدیریت‌کنندهٔ رویداد `dragstart`، از `setData()` برای افزودن `id` عنصر `<p>` به شیء {{domxref("DataTransfer")}} استفاده می‌کنیم.
- در مدیریت‌کنندهٔ رویداد `drop`، `id` را بازیابی کرده و از آن برای انتقال عنصر `<p>` به داخل هدف استفاده می‌کنیم.

#### HTML

```html
<div>
  <p id="source" draggable="true">
    Select this element, drag it to the drop zone and then release the selection
    to move the element.
  </p>
</div>
<div id="target">Drop Zone</div>

<button id="reset">Reset example</button>
```

#### CSS

```css
div {
  margin: 0.5em 0;
  padding: 2em;
}

#target,
#source {
  border: 1px solid black;
  padding: 0.5rem;
}

.dragging {
  background-color: pink;
}
```

#### JavaScript

```js
const source = document.querySelector("#source");
source.addEventListener("dragstart", (ev) => {
  console.log("dragStart");
  // Change the source element's background color
  // to show that drag has started
  ev.currentTarget.classList.add("dragging");
  // Clear the drag data cache (for all formats/types)
  ev.dataTransfer.clearData();
  // Set the drag's format and data.
  // Use the event target's id for the data
  ev.dataTransfer.setData("text/plain", ev.target.id);
});
source.addEventListener("dragend", (ev) =>
  ev.target.classList.remove("dragging"),
);

const target = document.querySelector("#target");
target.addEventListener("dragover", (ev) => {
  console.log("dragOver");
  ev.preventDefault();
});
target.addEventListener("drop", (ev) => {
  console.log("Drop");
  ev.preventDefault();
  // Get the data, which is the id of the source element
  const data = ev.dataTransfer.getData("text");
  const source = document.getElementById(data);
  ev.target.appendChild(source);
});

const reset = document.querySelector("#reset");
reset.addEventListener("click", () => document.location.reload());
```

#### نتیجه

{{EmbedLiveSample("Dragging an element", "", 250)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [کشیدن و رها کردن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API)
- [عملیات درگ](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_operations)
- [کار با ذخیره‌گاه دادهٔ درگ](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_data_store)