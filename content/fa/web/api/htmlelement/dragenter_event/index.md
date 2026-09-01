---
title: "HTMLElement: dragenter event"
short-title: dragenter
slug: Web/API/HTMLElement/dragenter_event
page-type: web-api-event
browser-compat: api.HTMLElement.dragenter_event
---

{{APIRef("HTML Drag and Drop API")}}

رویداد `dragenter` وقتی شلیک می‌شود که یک عنصر کشیدنی یا انتخاب متنی، وارد یک مقصد رهاسازی معتبر شود. شیء موردنظر، _انتخاب مستقیم کاربر_ است (عنصری که کاربر مستقیماً به‌عنوان مقصد رهاسازی تعیین کرده) یا عنصر {{HTMLElement("body")}}.

این رویداد قابل لغو است (cancelable) و ممکن است به سمت اشیاء {{domxref("Document")}} و {{domxref("Window")}} انتشار یابد.

## سینتکس

برای استفاده از نام این رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}}، یا به‌عنوان یک ویژگی مدیریت‌کننده رویداد، به شکل زیر عمل کنید:

```js-nolint
addEventListener("dragenter", (event) => { })

ondragenter = (event) => { }
```

## نوع رویداد

یک {{domxref("DragEvent")}}. از {{domxref("Event")}} به ارث می‌رسد.

{{InheritanceDiagram("DragEvent")}}

## مثال‌ها

### استایل‌دهی به مناطق رهاسازی هنگام dragenter

در این مثال، یک عنصر کشیدنی داخل یک ظرف داریم. سعی کنید عنصر را بگیرید، آن را روی ظرف دیگر بکشید و رها کنید.

ما به رویداد `dragenter` گوش می‌دهیم تا وقتی عنصر کشیدنی روی ظرف دیگر قرار دارد، به آن ظرف پس‌زمینه‌ای بنفش بدهیم و این‌طور نشان دهیم که عنصر کشیدنی می‌تواند روی آن ظرف رها شود.

البته در این مثال ناقص، رهاسازی را پیاده‌سازی نکرده‌ایم: برای یک مثال کامل از کشیدن و رها کردن، صفحه رویداد [`drag`](/en-US/docs/Web/API/HTMLElement/drag_event) را ببینید.

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

.dropzone.dragover {
  background-color: purple;
}
```

#### JavaScript

```js
const target = document.getElementById("drop-target");
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
```

#### نتیجه

{{EmbedLiveSample('Styling drop zones on dragenter')}}

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
  - {{domxref("HTMLElement/dragleave_event", "dragleave")}}
  - {{domxref("HTMLElement/drop_event", "drop")}}