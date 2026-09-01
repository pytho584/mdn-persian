---
title: "HTMLFormElement: reset event"
---

---
title: "HTMLFormElement: reset event"
short-title: reset
slug: Web/API/HTMLFormElement/reset_event
page-type: web-api-event
browser-compat: api.HTMLFormElement.reset_event
---

{{APIRef("HTML DOM")}}

رویداد **`reset`** زمانی رخ می‌دهد که یک {{HTMLElement("form")}} بازنشانی می‌شود.

## نحو

از نام رویداد در متدهایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی handler رویداد تنظیم کنید.

```js-nolint
addEventListener("reset", (event) => { })

onreset = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

این مثال از {{domxref("EventTarget.addEventListener()")}} برای گوش دادن به بازنشانی فرم استفاده می‌کند و {{domxref("Event.timeStamp")}} فعلی را هر بار که این اتفاق می‌افتد، ثبت می‌کند.

### HTML

```html
<form id="form">
  <label>Test field: <input type="text" /></label>
  <br /><br />
  <button type="reset">Reset form</button>
</form>
<p id="log"></p>
```

### JavaScript

```js
const form = document.getElementById("form");
const log = document.getElementById("log");

function logReset(event) {
  log.textContent = `Form reset! Timestamp: ${event.timeStamp}`;
}

form.addEventListener("reset", logReset);
```

### نتیجه

{{EmbedLiveSample("Examples")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- عنصر HTML {{HTMLElement("form")}}