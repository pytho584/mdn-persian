```
---
title: "MouseEvent: clientX property"
---

---
title: "MouseEvent: clientX property"
short-title: clientX
slug: Web/API/MouseEvent/clientX
page-type: web-api-instance-property
browser-compat: api.MouseEvent.clientX
---

{{APIRef("Pointer Events")}}

خاصیت فقط‌خواندنی **`clientX`** از رابط {{domxref("MouseEvent")}} مختصات افقی رویداد را درون {{glossary("viewport")}} برنامه (و نه مختصات درون صفحه) فراهم می‌کند.

برای مثال، کلیک کردن روی لبه‌ی چپ viewport همیشه منجر به یک رویداد ماوس با مقدار `clientX` برابر `0` می‌شود، صرف‌نظر از اینکه صفحه به صورت افقی اسکرول شده باشد یا نه.

## مقدار

یک عدد اعشاری از نوع `double` بر حسب پیکسل.

## مثال‌ها

این مثال مختصات ماوس شما را هر بار که رویداد {{domxref("Element/mousemove_event", "mousemove")}} را فعال می‌کنید، نمایش می‌دهد.

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
- {{domxref("MouseEvent.clientY","clientY")}}
- {{domxref("MouseEvent.screenX","screenX")}} / {{domxref("MouseEvent.screenY","screenY")}}
- [سیستم‌های مختصات](/en-US/docs/Web/API/CSSOM_view_API/Coordinate_systems)
```