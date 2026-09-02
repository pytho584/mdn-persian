---
title: "MouseEvent: screenX property"
short-title: screenX
slug: Web/API/MouseEvent/screenX
page-type: web-api-instance-property
browser-compat: api.MouseEvent.screenX
---

{{APIRef("Pointer Events")}}

ویژگی فقط‌خواندنی **`screenX`** از رابط {{domxref("MouseEvent")}} مختصات افقی (offset) نشانگر ماوس را در [مختصات صفحه‌نمایش](/en-US/docs/Web/API/CSSOM_view_API/Coordinate_systems#screen) ارائه می‌دهد.

> [!NOTE]
> در محیط‌های چندنمایشگری، نمایشگرهایی که به‌صورت افقی کنار هم تراز شده‌اند به‌عنوان یک دستگاه واحد در نظر گرفته می‌شوند و بنابراین بازهٔ مقدار `screenX` تا پهنای ترکیبی این نمایشگرها گسترش می‌یابد.

## مقدار

یک مقدار ممیز شناور از نوع `double` بر حسب پیکسل.

نسخه‌های اولیهٔ مشخصات فنی، این ویژگی را به‌صورت یک عدد صحیح تعریف کرده بودند که به تعداد پیکسل‌ها اشاره داشت.

## نمونه‌ها

این مثال، هر بار که رویداد {{domxref("Element/mousemove_event", "mousemove")}} رخ می‌دهد، مختصات ماوس شما را نمایش می‌دهد.

### HTML

```html
<p>Move your mouse to see its position.</p>
<p id="screen-log"></p>
```

### JavaScript

```js
let screenLog = document.querySelector("#screen-log");
document.addEventListener("mousemove", logKey);

function logKey(e) {
  screenLog.innerText = `
    Screen X/Y: ${e.screenX}, ${e.screenY}
    Client X/Y: ${e.clientX}, ${e.clientY}`;
}
```

### نتیجه

{{EmbedLiveSample("Examples")}}

### مسیریابی یک رویداد

هنگامی که رویدادها را روی window، document یا سایر عناصر بزرگ رهگیری می‌کنید، می‌توانید مختصات آن رویداد (مثلاً یک کلیک) را به‌دست آورید و آن را به‌درستی مسیریابی کنید؛ همان‌طور که مثال زیر نشان می‌دهد:

```js
function checkClickMap(e) {
  if (e.screenX < 50) doRedButton();
  if (50 <= e.screenX && e.screenX < 100) doYellowButton();
  if (e.screenX >= 100) doRedButton();
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{ domxref("MouseEvent") }}
- {{ domxref("MouseEvent.screenY","screenY") }}
- {{ domxref("MouseEvent.clientX","clientX") }} / {{ domxref("MouseEvent.clientY", "clientY") }}
- [سیستم‌های مختصات](/en-US/docs/Web/API/CSSOM_view_API/Coordinate_systems)