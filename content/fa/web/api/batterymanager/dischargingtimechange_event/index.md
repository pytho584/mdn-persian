---
title: "BatteryManager: dischargingtimechange event"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BatteryManager/dischargingtimechange_event"
translated_by: "n8n + AI"
---

---
title: "BatteryManager: dischargingtimechange event"
short-title: dischargingtimechange
slug: Web/API/BatteryManager/dischargingtimechange_event
page-type: web-api-event
browser-compat: api.BatteryManager.dischargingtimechange_event
---

{{ApiRef("Battery API")}}{{securecontext_header}}

رویداد **`dischargingtimechange`** از رابط {{domxref("BatteryManager")}} زمانی رخ می‌دهد که ویژگی {{domxref("BatteryManager.dischargingTime", "dischargingTime")}} باتری به‌روزرسانی شود.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("dischargingtimechange", (event) => { })

ondischargingtimechange = (event) => { }
```

## نوع رویداد

_یک {{domxref("Event")}} عمومی._

## مثال

### HTML

```html
<div id="level">(battery level unknown)</div>
<div id="chargingTime">(charging time unknown)</div>
```

### JavaScript

```js
navigator.getBattery().then((battery) => {
  battery.ondischargingtimechange = () => {
    document.querySelector("#level").textContent = battery.level;
    document.querySelector("#chargingTime").textContent = battery.chargingTime;
  };
});
```

{{ EmbedLiveSample('Example', '100%', 40) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("BatteryManager")}}
- {{domxref("Navigator.getBattery()")}}