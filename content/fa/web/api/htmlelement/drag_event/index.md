---
title: "HTMLElement: drag event"
short-title: drag
slug: Web/API/HTMLElement/drag_event
page-type: web-api-event
browser-compat: api.HTMLElement.drag_event
---

{{APIRef("HTML Drag and Drop API")}}

رویداد `drag` هر چند صد میلی‌ثانیه یک بار، زمانی که کاربر یک عنصر یا متن انتخاب‌شده را می‌کشد، رخ می‌دهد.

این رویداد قابل‌لغو است و ممکن است به سمت بالا تا اشیاء {{domxref("Document")}} و {{domxref("Window")}} انتشار یابد.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("drag", (event) => { })

ondrag = (event) => { }
```

## نوع رویداد

یک {{domxref("DragEvent")}}. از {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("DragEvent")}}

## مثال‌ها

### مثال کشیدن و رها کردن

#### HTML

```html
<div class="dropzone">
  <div id="draggable" draggable="true">This div is draggable</div>
</div>
<div class="dropzone" id="drop-target"></div>
```

#### CSS

```css
body {
  /* Prevent the user selecting text in the example */
  user-select: none;
}

#draggable {
  text-align: center;
  background: white;
}

.dropzone {
  width: 200px;
  height: 20px;
  background: blueviolet;
  margin: 10px;
  padding: 10px;
}

.dropzone.dragover {
  background-color: purple;
}

.dragging {
  opacity: 0.5;
}
```

#### JavaScript

```js
let dragged;

/* events fired on the draggable target */
const source = document.getElementById("draggable");
source.addEventListener("drag", (event) => {
  console.log("dragging");
});

source.addEventListener("dragstart", (event) => {
  // store a ref. on the dragged elem
  dragged = event.target;
  // make it half transparent
  event.target.classList.add("dragging");
});

source.addEventListener("dragend", (event) => {
  // reset the transparency
  event.target.classList.remove("dragging");
});

/* events fired on the drop targets */
const target = document.getElementById("drop-target");
target.addEventListener("dragover", (event) => {
  // prevent default to allow drop
  event.preventDefault();
});

target.addEventListener("dragenter", (event) => {
  // highlight potential drop target when the draggable element enters it
  if (event.target.classList.contains("dropzone")) {
    event.target.classList.add("dragover");
  }
});

target.addEventListener("dragleave", (event) => {
  // reset background of potential drop target when the draggable element leaves it
  if (event.target.classList.contains("dropzone")) {
    event.target.classList.remove("dragover");
  }
});

target.addEventListener("drop", (event) => {
  // prevent default action (open as link for some elements)
  event.preventDefault();
  // move dragged element to the selected drop target
  if (event.target.classList.contains("dropzone")) {
    event.target.classList.remove("dragover");
    event.target.appendChild(dragged);
  }
});
```

#### نتیجه

{{EmbedLiveSample('Drag and drop example')}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLElement/dragstart_event", "dragstart")}}
- {{domxref("HTMLElement/dragend_event", "dragend")}}
- {{domxref("HTMLElement/dragover_event", "dragover")}}
- {{domxref("HTMLElement/dragenter_event", "dragenter")}}
- {{domxref("HTMLElement/dragleave_event", "dragleave")}}
- {{domxref("HTMLElement/drop_event", "drop")}}