---
title: "MouseEvent: movementX property"
short-title: movementX
slug: Web/API/MouseEvent/movementX
page-type: web-api-instance-property
browser-compat: api.MouseEvent.movementX
---

{{APIRef("Pointer Lock API")}}

ویژگی فقط‌خواندنی **`movementX`** از رابط {{domxref("MouseEvent")}}، تفاوت در مختصهٔ X ماوس (یا اشاره‌گر) را بین رویداد حرکتِ داده‌شده و رویداد حرکتِ قبلیِ همان نوع برمی‌گرداند.

به عبارت دیگر، مقدار این ویژگی به این صورت محاسبه می‌شود: `currentEvent.movementX = currentEvent.screenX - previousEvent.screenX`. مقدار این ویژگی برای همهٔ رویدادها به‌جز {{domxref("Element/mousemove_event", "mousemove")}}، {{domxref("Element/pointermove_event", "pointermove")}} و {{domxref("Element/pointerrawupdate_event", "pointerrawupdate")}} صفر است.

> [!WARNING]
> مرورگرها [برای `movementX` و `screenX` واحدهای متفاوتی با آنچه در مشخصات تعریف شده](https://github.com/w3c/pointerlock/issues/42) استفاده می‌کنند.
> بسته به مرورگر و سیستم‌عامل، واحدهای `movementX` می‌توانند پیکسل فیزیکی، پیکسل منطقی یا پیکسل CSS باشند. بهتر است از ویژگی‌های حرکت استفاده نکنید و به‌جای آن، اختلاف بین مقادیر فعلی رویداد ({{domxref("MouseEvent.screenX", "screenX")}}، {{domxref("MouseEvent.screenY", "screenY")}}) و مقادیر قبلی رویداد را محاسبه کنید.

## Value

یک عدد. برای هر {{domxref("MouseEvent")}} غیر از `mousemove` و هر {{domxref("PointerEvent")}} غیر از `pointermove` یا `pointerrawupdate`، همیشه صفر است.

## Examples

### Log mouse movement for `mousemove` events

این مثال میزان حرکت ماوس را با استفاده از `movementX` و {{domxref("MouseEvent.movementY", "movementY")}} ثبت می‌کند.

#### HTML

```html
<p id="log">Move your mouse around.</p>
```

#### JavaScript

```js
const log = document.getElementById("log");

function logMovement(event) {
  log.insertAdjacentHTML(
    "afterbegin",
    `movement: ${event.movementX}, ${event.movementY}<br>`,
  );
  while (log.childNodes.length > 128) log.lastChild.remove();
}

document.addEventListener("mousemove", logMovement);
```

#### Result

{{EmbedLiveSample("### Log mouse movement for `mousemove` events")}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("MouseEvent.movementY")}}
- {{domxref("MouseEvent")}}
- [Pointer Lock](/en-US/docs/Web/API/Pointer_Lock_API)