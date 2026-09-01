---
title: "Event: type property"
short-title: type
slug: Web/API/Event/type
page-type: web-api-instance-property
browser-compat: api.Event.type
---

{{APIRef("DOM")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`type`** از رابط {{domxref("Event")}} رشته‌ای شامل نوع رویداد را برمی‌گرداند. این مقدار هنگام ساخته‌شدن رویداد تنظیم می‌شود و نامی است که معمولاً برای ارجاع به رویداد خاص استفاده می‌شود، مانند `click`، `load` یا `error`.

## مقدار

رشته‌ای که نوع {{domxref("Event")}} را شامل می‌شود.

## مثال

این مثال، نوع رویداد را هر بار که یک کلید صفحه‌کلید را فشار دهید یا دکمه‌ای از ماوس را کلیک کنید، ثبت می‌کند.

### HTML

```html
<p>Press any key or click the mouse to get the event type.</p>
<p id="log"></p>
```

### JavaScript

```js
function getEventType(event) {
  const log = document.getElementById("log");
  log.innerText = `${event.type}\n${log.innerText}`;
}

// Keyboard events
document.addEventListener("keydown", getEventType); // first
document.addEventListener("keypress", getEventType); // second
document.addEventListener("keyup", getEventType); // third

// Mouse events
document.addEventListener("mousedown", getEventType); // first
document.addEventListener("mouseup", getEventType); // second
document.addEventListener("click", getEventType); // third
```

### نتیجه

{{EmbedLiveSample('Example')}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{ domxref("EventTarget.addEventListener()") }}
- {{ domxref("EventTarget.removeEventListener()") }}