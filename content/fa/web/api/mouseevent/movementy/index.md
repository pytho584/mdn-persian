---
title: "خاصیت MouseEvent: movementY"
---

---
title: "خاصیت MouseEvent: movementY"
short-title: movementY
slug: Web/API/MouseEvent/movementY
page-type: web-api-instance-property
browser-compat: api.MouseEvent.movementY
---

{{APIRef("Pointer Lock API")}}

خاصیت فقط‌خواندنی **`movementY`** در رابط {{domxref("MouseEvent")}}، تفاوت مختصات Y اشاره‌گر (یا ماوس) را بین رویداد حرکتِ داده‌شده و رویداد حرکتِ قبلی از همان نوع، ارائه می‌دهد.

به بیان دیگر، مقدار این خاصیت به این صورت محاسبه می‌شود: `currentEvent.movementY = currentEvent.screenY - previousEvent.screenY`.
مقدار این خاصیت برای همه رویدادها به‌جز {{domxref("Element/mousemove_event", "mousemove")}}، {{domxref("Element/pointermove_event", "pointermove")}} و {{domxref("Element/pointerrawupdate_event", "pointerrawupdate")}} برابر با صفر است.

> [!WARNING]
> مرورگرها [از واحدهای متفاوتی برای `movementY` و `screenY` استفاده می‌کنند](https://github.com/w3c/pointerlock/issues/42) که با تعریف مشخصات (specification) تفاوت دارد.
> بسته به مرورگر و سیستم عامل، واحدهای `movementY` ممکن است پیکسل فیزیکی، پیکسل منطقی یا پیکسل CSS باشند.
> بهتر است از خاصیت‌های movement استفاده نکنید و به جای آن، تفاضل بین مقادیر جاری ({{domxref("MouseEvent.screenX", "screenX")}}، {{domxref("MouseEvent.screenY", "screenY")}}) و مقادیر قبلی را محاسبه کنید.

## مقدار

یک عدد.
برای هر {{domxref("MouseEvent")}} غیر از `mousemove` و هر {{domxref("PointerEvent")}} غیر از `pointermove` یا `pointerrawupdate`، مقدار همیشه صفر است.

## مثال‌ها

### ثبت حرکت ماوس برای رویدادهای `mousemove`

این مثال میزان حرکت ماوس را با استفاده از {{domxref("MouseEvent.movementX", "movementX")}} و `movementY` ثبت می‌کند.

#### HTML

```html
<p id="log">Move your mouse around inside this element.</p>
```

#### جاوااسکریپت

```js
const log = document.getElementById("log");

function logMovement(event) {
  log.innerText = `movement: ${event.movementX}, ${event.movementY}\n${log.innerText}`;
}

document.addEventListener("mousemove", logMovement);
```

#### نتیجه

{{EmbedLiveSample("ثبت حرکت ماوس برای رویدادهای `mousemove`")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("MouseEvent.movementX")}}
- {{domxref("MouseEvent")}}
- [قفل اشاره‌گر (Pointer Lock)](/en-US/docs/Web/API/Pointer_Lock_API)