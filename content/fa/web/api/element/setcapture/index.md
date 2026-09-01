---
title: "Element: setCapture() method"
---

---
title: "Element: setCapture() method"
short-title: setCapture()
slug: Web/API/Element/setCapture
page-type: web-api-instance-method
status:
  - deprecated
  - non-standard
browser-compat: api.Element.setCapture
---

{{Deprecated_Header}}{{non-standard_header}}{{ APIRef("DOM") }}

این متد را در هنگام مدیریت رویداد `mousedown` فراخوانی کنید تا تمام رویدادهای ماوس به این عنصر هدایت شوند تا زمانی که دکمه ماوس رها شود یا {{domxref("document.releaseCapture()")}} فراخوانی شود.

> [!WARNING]
> این رابط هیچ‌گاه پشتیبانی بین‌مرورگری چندانی نداشته است؛ احتمالاً به دنبال {{domxref("element.setPointerCapture")}} از API رویدادهای اشاره‌گر (Pointer Events) هستید.

## سینتکس

```js-nolint
setCapture(retargetToElement)
```

### پارامترها

- `retargetToElement`
  - : اگر `true` باشد، همه رویدادها مستقیماً به این عنصر هدایت می‌شوند؛ اگر `false` باشد، رویدادها می‌توانند بر روی فرزندان این عنصر نیز رخ دهند.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

در این مثال، مختصات فعلی ماوس، در حالی که پس از کلیک‌کردن و نگه‌داشتن روی یک عنصر، ماوس را حرکت می‌دهید، رسم می‌شود.

```html
<p>This is an example of how to use mouse capture on elements in Gecko 2.0.</p>
<p><a id="myButton" href="#">Test Me</a></p>
<div id="output">No events yet</div>
```

```css
#myButton {
  border: solid black 1px;
  color: black;
  padding: 2px;
  box-shadow: black 2px 2px;
}
```

```js
function mouseDown(e) {
  e.target.setCapture();
  e.target.addEventListener("mousemove", mouseMoved);
}

function mouseUp(e) {
  e.target.removeEventListener("mousemove", mouseMoved);
}

function mouseMoved(e) {
  const output = document.getElementById("output");
  output.textContent = `Position: ${e.clientX}, ${e.clientY}`;
}

const btn = document.getElementById("myButton");
if (btn.setCapture) {
  btn.addEventListener("mousedown", mouseDown);
  btn.addEventListener("mouseup", mouseUp);
} else {
  document.getElementById("output").textContent =
    "Sorry, there appears to be no setCapture support on this browser";
}
```

[مشاهده مثال‌های زنده](https://mdn.dev/archives/media/samples/domref/mousecapture.html)

## یادداشت‌ها

بسته به چیدمان عناصر دیگر، ممکن است عنصر کاملاً به بالا یا پایین اسکرول نشود.

## مشخصات

بخشی از هیچ مشخصاتی نیست.

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{ domxref("document.releaseCapture()") }}
- {{domxref("element.setPointerCapture")}}