---
title: "HTMLElement: drop event"
short-title: drop
slug: Web/API/HTMLElement/drop_event
page-type: web-api-event
browser-compat: api.HTMLElement.drop_event
---

{{APIRef("HTML Drag and Drop API")}}

رویداد **`drop`** زمانی رخ می‌دهد که یک عنصر یا انتخاب متنی روی یک مقصد رهاسازی معتبر رها شود. برای اطمینان از اینکه رویداد `drop` همیشه مطابق انتظار رخ می‌دهد، همیشه باید یک فراخوانی [`preventDefault()`](/en-US/docs/Web/API/Event/preventDefault) را در بخشی از کد خود که رویداد [`dragover`](/en-US/docs/Web/API/HTMLElement/dragover_event) را مدیریت می‌کند، قرار دهید.

این رویداد قابل لغو است و ممکن است به سمت اشیاء {{domxref("Document")}} و {{domxref("Window")}} حباب کند.

## سینتکس

نام رویداد را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت رویداد تنظیم کنید.

```js-nolint
addEventListener("drop", (event) => { })

ondrop = (event) => { }
```

## نوع رویداد

یک {{domxref("DragEvent")}}. از {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("DragEvent")}}

## مثال‌ها

### یک مثال ساده از کشیدن و رها کردن

در این مثال، یک عنصر قابل کشیدن درون یک ظرف داریم. سعی کنید عنصر را بگیرید، آن را روی ظرف دیگر بکشید و رها کنید.

در اینجا از سه مدیریت‌کننده رویداد استفاده می‌کنیم:

- در مدیریت‌کننده رویداد `dragstart`، ارجاعی به عنصری که کاربر کشیده است می‌گیریم.
- در مدیریت‌کننده رویداد `dragover` برای ظرف مقصد، تابع `event.preventDefault()` را فراخوانی می‌کنیم که به آن امکان دریافت رویدادهای `drop` را می‌دهد.
- در مدیریت‌کننده رویداد `drop` برای ناحیه رهاسازی، جابجایی عنصر قابل کشیدن از ظرف اصلی به ناحیه رهاسازی را مدیریت می‌کنیم.

برای مثالی کامل‌تر از کشیدن و رها کردن، به صفحه رویداد [`drag`](/en-US/docs/Web/API/HTMLElement/drag_event) مراجعه کنید.

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
  // prevent default action (open as a link for some elements)
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
  - {{domxref("HTMLElement/dragover_event", "dragover")}}
  - {{domxref("HTMLElement/dragenter_event", "dragenter")}}
  - {{domxref("HTMLElement/dragleave_event", "dragleave")}}