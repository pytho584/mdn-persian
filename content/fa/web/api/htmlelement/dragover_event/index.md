---
title: "HTMLElement: dragover event"
short-title: dragover
slug: Web/API/HTMLElement/dragover_event
page-type: web-api-event
browser-compat: api.HTMLElement.dragover_event
---

{{APIRef("HTML Drag and Drop API")}}

رویداد `dragover` زمانی پرتاب می‌شود که یک عنصر یا متن انتخاب‌شده روی یک ناحیهٔ هدف معتبر برای رها کردن کشیده می‌شود (هر چند صد میلی‌ثانیه یک بار).

این رویداد قابل لغو (cancelable) است و می‌تواند به سمت بالا به اشیاء {{domxref("Document")}} و {{domxref("Window")}} منتشر شود.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی handler رویداد تنظیم کنید.

```js-nolint
addEventListener("dragover", (event) => { })

ondragover = (event) => { }
```

## نوع رویداد

یک {{domxref("DragEvent")}}. از {{domxref("Event")}} ارث‌بری می‌کند.

{{InheritanceDiagram("DragEvent")}}

## مثال‌ها

### یک مثال ساده از کشیدن و رها کردن

در این مثال، یک عنصر قابل کشیدن داخل یک ظرف داریم. سعی کنید عنصر را بگیرید، آن را روی ظرف دیگر بکشید و رها کنید.

ما در اینجا از سه handler رویداد استفاده می‌کنیم:

- در handler رویداد `dragstart`، ارجاعی به عنصری که کاربر کشیده است به دست می‌آوریم.
- در handler رویداد `dragover` برای ظرف هدف، با `event.preventDefault()` فراخوانی می‌کنیم که این امکان را می‌دهد تا رویدادهای `drop` دریافت شوند.
- در handler رویداد `drop` برای ناحیهٔ رها کردن، جابجایی عنصر قابل کشیدن از ظرف اصلی به ناحیهٔ رها کردن را مدیریت می‌کنیم.

برای یک مثال کامل از کشیدن و رها کردن، به صفحهٔ رویداد [`drag`](/en-US/docs/Web/API/HTMLElement/drag_event) مراجعه کنید.

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
  /* Prevent the user from selecting text in the example */
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
```

#### JavaScript

```js
let dragged = null;

const source = document.getElementById("draggable");
source.addEventListener("dragstart", (event) => {
  // store a ref. on the dragged elem
  dragged = event.target;
});

const target = document.getElementById("drop-target");
target.addEventListener("dragover", (event) => {
  // prevent default to allow drop
  event.preventDefault();
});

target.addEventListener("drop", (event) => {
  // prevent default action (open as link for some elements)
  event.preventDefault();
  // move dragged element to the selected drop target
  if (event.target.className === "dropzone") {
    dragged.parentNode.removeChild(dragged);
    event.target.appendChild(dragged);
  }
});
```

#### نتیجه

{{EmbedLiveSample('A minimal drag and drop example')}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- سایر رویدادهای کشیدن و رها کردن:
  - {{domxref("HTMLElement/drag_event", "drag")}}
  - {{domxref("HTMLElement/dragstart_event", "dragstart")}}
  - {{domxref("HTMLElement/dragend_event", "dragend")}}
  - {{domxref("HTMLElement/dragenter_event", "dragenter")}}
  - {{domxref("HTMLElement/dragleave_event", "dragleave")}}
  - {{domxref("HTMLElement/drop_event", "drop")}}