---
title: "BatteryManager: chargingchange event"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BatteryManager/chargingchange_event"
translated_by: "n8n + AI"
---

---
title: "BatteryManager: chargingchange event"
short-title: chargingchange
slug: Web/API/BatteryManager/chargingchange_event
page-type: web-api-event
browser-compat: api.BatteryManager.chargingchange_event
---

{{ApiRef("Battery API")}}{{securecontext_header}}

**`chargingchange`** رویداد رابط {{domxref("BatteryManager")}} زمانی فعال می‌شود که ویژگی {{domxref("BatteryManager.charging", "charging")}} باتری به‌روزرسانی شود.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت رویداد تنظیم کنید.

```js-nolint
addEventListener("chargingchange", (event) => { })

onchargingchange = (event) => { }
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
  battery.onchargingchange = () => {
    document.querySelector("#level").textContent = battery.level;
    document.querySelector("#chargingTime").textContent = battery.chargingTime;
  };
});
```

{{ EmbedLiveSample('Example', '100%', 40) }}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("BatteryManager")}}
- {{domxref("Navigator.getBattery()")}}