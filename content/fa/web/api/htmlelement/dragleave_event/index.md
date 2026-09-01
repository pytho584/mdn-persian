---
title: "HTMLElement: dragleave event"
short-title: dragleave
slug: Web/API/HTMLElement/dragleave_event
page-type: web-api-event
browser-compat: api.HTMLElement.dragleave_event
---

{{APIRef("HTML Drag and Drop API")}}

رویداد `dragleave` زمانی رخ می‌دهد که یک عنصر یا انتخابِ متنیِ در حال کشیدن، یک هدف رهاسازی معتبر را ترک کند.

این رویداد قابل لغو (cancelable) نیست و ممکن است تا اشیاء {{domxref("Document")}} و {{domxref("Window")}} بالا برود (bubble).

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("dragleave", (event) => { })

ondragleave = (event) => { }
```

## نوع رویداد

یک {{domxref("DragEvent")}} که از {{domxref("Event")}} به ارث می‌رسد.

{{InheritanceDiagram("DragEvent")}}

## مثال‌ها

### بازنشانی استایل‌های ناحیه رهاسازی هنگام خروج

در این مثال، یک عنصر قابل کشیدن داخل یک ظرف (container) داریم. سعی کنید عنصر را بگیرید، آن را روی ظرف دیگر بکشید و رها کنید.

وقتی عنصر قابل کشیدن روی ظرف دیگر قرار می‌گیرد، به آن ظرف یک پس‌زمینه بنفش می‌دهیم تا نشان دهیم که عنصر می‌تواند روی آن رها شود. به رویداد `dragleave` گوش می‌دهیم تا وقتی عنصر قابل کشیدن از ظرف خارج می‌شود، پس‌زمینه ظرف به حالت اول بازگردد.

البته در این مثال جزئی، قابلیت رهاسازی پیاده‌سازی نشده است: برای یک مثال کامل از کشیدن و رها کردن، به صفحه رویداد [`drag`](/en-US/docs/Web/API/HTMLElement/drag_event) مراجعه کنید.

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

{{EmbedLiveSample('Resetting drop zone styles on dragleave')}}

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
  - {{domxref("HTMLElement/drop_event", "drop")}}