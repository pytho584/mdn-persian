---
title: "HTMLElement: dragend event"
short-title: dragend
slug: Web/API/HTMLElement/dragend_event
page-type: web-api-event
browser-compat: api.HTMLElement.dragend_event
---

{{APIRef("HTML Drag and Drop API")}}

رویداد `dragend` زمانی فعال می‌شود که یک عملیات کشیدن (drag) پایان می‌یابد (با رها کردن دکمه ماوس یا فشار دادن کلید Escape).

این رویداد قابل لغو (cancelable) است و ممکن است تا اشیاء {{domxref("Document")}} و {{domxref("Window")}} بالا بیاید.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("dragend", (event) => { })

ondragend = (event) => { }
```

## نوع رویداد

یک {{domxref("DragEvent")}}. از {{domxref("Event")}} به ارث برده است.

{{InheritanceDiagram("DragEvent")}}

## مثال‌ها

### بازنشانی شفافیت در پایان کشیدن (dragend)

در این مثال، یک عنصر قابل کشیدن داخل یک ظرف داریم. سعی کنید عنصر را بگیرید، بکشید و سپس رها کنید.

ما عنصر را در حین کشیدن نیمه‌شفاف می‌کنیم و به رویداد `dragend` گوش می‌دهیم تا شفافیت آن را هنگام رها شدن بازنشانی کنیم.

برای یک مثال کامل از کشیدن و رها کردن (drag and drop)، به صفحه رویداد [`drag`](/en-US/docs/Web/API/HTMLElement/drag_event) مراجعه کنید.

#### HTML

```html
<div id="container">
  <div id="draggable" draggable="true">This div is draggable</div>
</div>
<div class="dropzone"></div>
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

#container {
  width: 200px;
  height: 20px;
  background: blueviolet;
  padding: 10px;
}

.dragging {
  opacity: 0.5;
}
```

#### JavaScript

```js
const source = document.getElementById("draggable");
source.addEventListener("dragstart", (event) => {
  // make it half transparent
  event.target.classList.add("dragging");
});

source.addEventListener("dragend", (event) => {
  // reset the transparency
  event.target.classList.remove("dragging");
});
```

#### نتیجه

{{EmbedLiveSample('Resetting opacity on drag end')}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- سایر رویدادهای کشیدن و رها کردن:
  - {{domxref("HTMLElement/drag_event", "drag")}}
  - {{domxref("HTMLElement/dragstart_event", "dragstart")}}
  - {{domxref("HTMLElement/dragover_event", "dragover")}}
  - {{domxref("HTMLElement/dragenter_event", "dragenter")}}
  - {{domxref("HTMLElement/dragleave_event", "dragleave")}}
  - {{domxref("HTMLElement/drop_event", "drop")}}