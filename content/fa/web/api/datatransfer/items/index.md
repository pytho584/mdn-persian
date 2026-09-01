---
title: "DataTransfer: items property"
short-title: items
slug: Web/API/DataTransfer/items
page-type: web-api-instance-property
browser-compat: api.DataTransfer.items
---

{{APIRef("HTML Drag and Drop API")}}

خاصیت فقط‌خواندنی `items` در واسط {{domxref("DataTransfer")}} یک {{domxref("DataTransferItemList","لیست")}} از {{domxref("DataTransferItem","آیتم‌های انتقال داده", "", "nocode")}} در یک عملیات کشیدن است. این لیست به ازای هر آیتم در عملیات یک مورد دارد و اگر عملیات هیچ آیتمی نداشته باشد، لیست خالی خواهد بود.

## مقدار

یک شیء {{domxref("DataTransferItemList")}} حاوی اشیاء {{domxref("DataTransferItem")}} که نشان‌دهندهٔ آیتم‌های در حال کشیده شدن در یک عملیات کشیدن هستند، به ازای هر شیء در حال کشیده شدن یک آیتم در لیست. اگر عملیات کشیدن داده‌ای نداشته باشد، لیست خالی است.

## نمونه‌ها

### ثبت آیتم‌های کشیده شده

این مثال از `items` برای ثبت اطلاعات مربوط به آیتم‌های کشیده شده استفاده می‌کند.

#### HTML

```html
<ul>
  <li id="source1" draggable="true">Drag Item 1 to the Drop Zone</li>
  <li id="source2" draggable="true">Drag Item 2 to the Drop Zone</li>
</ul>
<div id="target">Drop Zone</div>

<button id="reset">Reset</button>
```

#### CSS

```css
div {
  margin: 0em;
  padding: 2em;
}

#target {
  border: 1px solid black;
}
```

#### JavaScript

```js
function dragstartHandler(ev) {
  console.log(`dragstart: target.id = ${ev.target.id}`);
  // Add this element's id to the drag payload so the drop handler will
  // know which element to add to its tree
  ev.dataTransfer.setData("text/plain", ev.target.id);
  ev.dataTransfer.effectAllowed = "move";
}

function dropHandler(ev) {
  ev.preventDefault();
  // Get the id of the target and add the moved element to the target's DOM
  const data = ev.dataTransfer.getData("text");
  ev.target.appendChild(document.getElementById(data));
  // Print each item's "kind" and "type"
  if (ev.dataTransfer.items) {
    for (const item of ev.dataTransfer.items) {
      console.log(`kind = ${item.kind}, type = ${item.type}`);
    }
  }
}

function dragoverHandler(ev) {
  ev.preventDefault();
  // Set the dropEffect to move
  ev.dataTransfer.dropEffect = "move";
}

const source1 = document.querySelector("#source1");
const source2 = document.querySelector("#source2");
const target = document.querySelector("#target");

source1.addEventListener("dragstart", dragstartHandler);
source2.addEventListener("dragstart", dragstartHandler);
target.addEventListener("dragover", dragoverHandler);
target.addEventListener("drop", dropHandler);

const reset = document.querySelector("#reset");
reset.addEventListener("click", () => document.location.reload());
```

#### نتیجه

{{EmbedLiveSample("Logging dragged items", 0, 400)}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## جستارهای وابسته

- [کشیدن و رها کردن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API)
- [عملیات کشیدن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_operations)
- [کار با ذخیره‌گاه داده‌ی کشیدن](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_data_store)