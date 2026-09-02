---
title: "MouseEvent: screenY property"
short-title: screenY
slug: Web/API/MouseEvent/screenY
page-type: web-api-instance-property
browser-compat: api.MouseEvent.screenY
---

{{APIRef("Pointer Events")}}

ویژگی فقط‌خواندنی **`screenY`** در رابط {{domxref("MouseEvent")}} مختصات عمودی (offset) اشاره‌گر ماوس را در [screen coordinates](/en-US/docs/Web/API/CSSOM_view_API/Coordinate_systems#screen) فراهم می‌کند.

## مقدار

یک مقدار اعشاری از نوع `double` بر حسب پیکسل.

نسخه‌های اولیه مشخصات این ویژگی را به صورت یک عدد صحیح (integer) که به تعداد پیکسل‌ها اشاره می‌کرد تعریف کرده بودند.

## مثال‌ها

این مثال مختصات ماوس شما را هر بار که رویداد {{domxref("Element/mousemove_event", "mousemove")}} را راه‌اندازی می‌کنید نمایش می‌دهد.

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

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{ domxref("MouseEvent") }}
- {{ domxref("MouseEvent.screenX","screenX") }}
- {{ domxref("MouseEvent.clientX","clientX") }} / {{ domxref("MouseEvent.clientY", "clientY") }}
- [Coordinate systems](/en-US/docs/Web/API/CSSOM_view_API/Coordinate_systems)