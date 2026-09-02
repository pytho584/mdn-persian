---
title: "MouseEvent: clientY property"
slug: Web/API/MouseEvent/clientY
page-type: web-api-instance-property
browser-compat: api.MouseEvent.clientY
---

{{APIRef("Pointer Events")}}

خاصیت فقط‑خواندنی **`clientY`** در رابط {{domxref("MouseEvent")}} مختصات عمودی رویداد را درون {{glossary("viewport")}} (نمای دید) برنامه ارائه می‌دهد (در مقابل مختصات درون صفحه).

برای مثال، کلیک روی لبه بالایی نمای دید همیشه به رویداد ماوسی با مقدار `clientY` برابر `0` منجر می‌شود، صرف‌نظر از اینکه صفحه به صورت عمودی اسکرول شده باشد یا نه.

## مقدار

یک مقدار اعشاری از نوع `double` بر حسب پیکسل.

## مثال‌ها

این مثال مختصات ماوس شما را هر بار که رویداد {{domxref("Element/mousemove_event", "mousemove")}} را فعال می‌کنید نمایش می‌دهد.

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

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{ domxref("MouseEvent") }}
- {{domxref("MouseEvent.clientX","clientX")}}
- {{domxref("MouseEvent.screenX","screenX")}} / {{domxref("MouseEvent.screenY","screenY")}}
- [سیستم‌های مختصات](/en-US/docs/Web/API/CSSOM_view_API/Coordinate_systems)