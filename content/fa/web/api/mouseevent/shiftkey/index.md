---
title: "MouseEvent: shiftKey property"
---

---
title: "MouseEvent: shiftKey property"
short-title: shiftKey
slug: Web/API/MouseEvent/shiftKey
page-type: web-api-instance-property
browser-compat: api.MouseEvent.shiftKey
---

{{APIRef("Pointer Events")}}

ویژگی فقط‌خواندنی **`MouseEvent.shiftKey`** یک مقدار بولی است که نشان می‌دهد آیا کلید <kbd>shift</kbd> هنگام رخداد یک رویداد ماوس فشرده شده بود یا خیر.

## مقدار

یک مقدار بولی، که در آن `true` نشان‌دهندهٔ فشرده‌شدن کلید و `false` نشان‌دهندهٔ _فشرده‌نشدن_ کلید است.

## مثال‌ها

این مثال ویژگی `shiftKey` را هنگام فعال‌سازی رویداد {{domxref("Element/click_event", "click")}} ثبت می‌کند.

### HTML

```html
<p>Click anywhere to test the <code>shiftKey</code> property.</p>
<p id="log"></p>
```

### JavaScript

```js
let log = document.querySelector("#log");
document.addEventListener("click", logKey);

function logKey(e) {
  log.textContent = `The shift key is pressed: ${e.shiftKey}`;
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