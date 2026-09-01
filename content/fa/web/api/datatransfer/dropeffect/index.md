---
title: "DataTransfer: dropEffect property"
short-title: dropEffect
slug: Web/API/DataTransfer/dropEffect
page-type: web-api-instance-property
browser-compat: api.DataTransfer.dropEffect
---

{{APIRef("HTML Drag and Drop API")}}

ویژگی **`DataTransfer.dropEffect`** بازخوردی (معمولاً بصری) را که کاربر در جریان عملیات کشیدن و رها کردن (drag and drop) دریافت می‌کند، کنترل می‌کند. این ویژگی بر نشانگر ماوسی که هنگام کشیدن نمایش داده می‌شود تأثیر می‌گذارد. برای مثال، وقتی کاربر روی عنصر مقصدِ رها کردن قرار می‌گیرد، نشانگر مرورگر ممکن است نشان دهد که چه نوع عملیاتی قرار است انجام شود.

هنگامی که شیء {{domxref("DataTransfer")}} ساخته می‌شود، `dropEffect` روی یک مقدار رشته‌ای تنظیم می‌شود. با خواندن (get) این ویژگی، مقدار فعلی آن بازگردانده می‌شود. هنگام تنظیم (set)، اگر مقدار جدید یکی از مقادیر فهرست‌شده در ادامه باشد، مقدار فعلی ویژگی به مقدار جدید تغییر می‌کند و سایر مقادیر نادیده گرفته می‌شوند.

برای رویدادهای {{domxref("HTMLElement/dragenter_event", "dragenter")}} و {{domxref("HTMLElement/dragover_event", "dragover")}}، `dropEffect` بر اساس عملی که کاربر درخواست می‌کند مقداردهی اولیه می‌شود. نحوه تعیین این مقدار به پلتفرم بستگی دارد، اما معمولاً کاربر می‌تواند با فشردن کلیدهای اصلاح‌گر (modifier keys) مانند کلید alt، عملیات موردنظر را تنظیم کند. در کنترل‌کننده‌های رویداد {{domxref("HTMLElement/dragenter_event", "dragenter")}} و {{domxref("HTMLElement/dragover_event", "dragover")}}، اگر عملی غیر از آنچه کاربر درخواست کرده موردنظر باشد، باید `dropEffect` تغییر کند.

برای رویدادهای {{domxref("HTMLElement/drop_event", "drop")}} و {{domxref("HTMLElement/dragend_event", "dragend")}}، `dropEffect` روی عملیاتی که موردنظر بوده است تنظیم می‌شود؛ که همان مقدار `dropEffect` بعد از آخرین رویداد {{domxref("HTMLElement/dragenter_event", "dragenter")}} یا {{domxref("HTMLElement/dragover_event", "dragover")}} است. برای مثال، در رویداد {{domxref("HTMLElement/dragend_event", "dragend")}}، اگر dropEffect موردنظر «move» باشد، داده‌های کشیده‌شده باید از مبدأ حذف شوند.

## Value

یک رشته که اثر عملیات کشیدن را نشان می‌دهد. مقادیر ممکن عبارت‌اند از:

- `copy`
  - : یک کپی از آیتم مبدأ در مکان جدید ساخته می‌شود.
- `move`
  - : یک آیتم به مکان جدید منتقل می‌شود.
- `link`
  - : یک پیوند به مبدأ در مکان جدید برقرار می‌شود.
- `none`
  - : آیتم را نمی‌توان رها کرد.

اختصاص دادن هر مقدار دیگری به `dropEffect` تأثیری ندارد و مقدار قبلی حفظ می‌شود.

## Example

این مثال کاربرد ویژگی‌های `dropEffect` و {{domxref("DataTransfer.effectAllowed","effectAllowed")}} را نشان می‌دهد.

### HTML

```html
<div>
  <p id="source" draggable="true">
    Select this element, drag it to the Drop Zone and then release the selection
    to move the element.
  </p>
</div>
<div id="target">Drop Zone</div>
```

### CSS

```css
div {
  margin: 0em;
  padding: 2em;
}

#source {
  color: blue;
  border: 1px solid black;
}

#target {
  border: 1px solid black;
}
```

### JavaScript

```js
const source = document.getElementById("source");
const target = document.getElementById("target");

source.addEventListener("dragstart", (ev) => {
  console.log(
    `dragStart: dropEffect = ${ev.dataTransfer.dropEffect} ; effectAllowed = ${ev.dataTransfer.effectAllowed}`,
  );

  // Add this element's id to the drag payload so the drop handler will
  // know which element to add to its tree
  ev.dataTransfer.setData("text", ev.target.id);
  ev.dataTransfer.effectAllowed = "move";
});

target.addEventListener("drop", (ev) => {
  console.log(
    `drop: dropEffect = ${ev.dataTransfer.dropEffect} ; effectAllowed = ${ev.dataTransfer.effectAllowed}`,
  );
  ev.preventDefault();

  // Get the id of the target and add the moved element to the target's DOM
  const data = ev.dataTransfer.getData("text");
  ev.target.appendChild(document.getElementById(data));
});

target.addEventListener("dragover", (ev) => {
  console.log(
    `dragOver: dropEffect = ${ev.dataTransfer.dropEffect} ; effectAllowed = ${ev.dataTransfer.effectAllowed}`,
  );
  ev.preventDefault();
  // Set the dropEffect to move
  ev.dataTransfer.dropEffect = "move";
});
```

{{EmbedLiveSample('Example', 300, 250)}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Drag and drop](/en-US/docs/Web/API/HTML_Drag_and_Drop_API)
- [Drag Operations](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_operations)
- [Working with the drag data store](/en-US/docs/Web/API/HTML_Drag_and_Drop_API/Drag_data_store)