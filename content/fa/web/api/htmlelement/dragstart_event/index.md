---
title: "HTMLElement: dragstart event"
---

---
title: "HTMLElement: dragstart event"
short-title: dragstart
slug: Web/API/HTMLElement/dragstart_event
page-type: web-api-event
browser-compat: api.HTMLElement.dragstart_event
---

{{APIRef("HTML Drag and Drop API")}}

رویداد `dragstart` زمانی به وقوع می‌پیوندد که کاربر شروع به درگ کردن (کشیدن) یک عنصر یا یک انتخاب متنی می‌کند.

این رویداد قابل لغو (cancelable) است و ممکن است به سمت بالا در اشیاء {{domxref("Document")}} و {{domxref("Window")}} انتشار یابد (bubble).

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("dragstart", (event) => { })

ondragstart = (event) => { }
```

## نوع رویداد

یک {{domxref("DragEvent")}}. از {{domxref("Event")}} به ارث می‌برد.

{{InheritanceDiagram("DragEvent")}}

## مثال‌ها

### تنظیم شفافیت هنگام شروع درگ

در این مثال، یک عنصر قابل درگ داخل یک ظرف (container) داریم. سعی کنید عنصر را بگیرید، آن را درگ کنید و سپس رها کنید.

ما به رویداد `dragstart` گوش می‌دهیم تا عنصر هنگام درگ شدن، نیمه‌شفاف شود.

برای یک مثال کامل از درگ و رها کردن (drag and drop)، به صفحه رویداد [`drag`](/en-US/docs/Web/API/HTMLElement/drag_event) مراجعه کنید.

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

{{EmbedLiveSample('Setting opacity on drag start')}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- سایر رویدادهای درگ و رها کردن:
  - {{domxref("HTMLElement/drag_event", "drag")}}
  - {{domxref("HTMLElement/dragend_event", "dragend")}}
  - {{domxref("HTMLElement/dragover_event", "dragover")}}
  - {{domxref("HTMLElement/dragenter_event", "dragenter")}}
  - {{domxref("HTMLElement/dragleave_event", "dragleave")}}
  - {{domxref("HTMLElement/drop_event", "drop")}}