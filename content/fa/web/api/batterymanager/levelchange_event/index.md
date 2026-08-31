---
title: "BatteryManager: levelchange event"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BatteryManager/levelchange_event"
translated_by: "n8n + AI"
---

---
title: "BatteryManager: levelchange event"
short-title: levelchange
slug: Web/API/BatteryManager/levelchange_event
page-type: web-api-event
browser-compat: api.BatteryManager.levelchange_event
---

{{ApiRef("Battery API")}}{{securecontext_header}}

رویداد **`levelchange`** از رابط {{domxref("BatteryManager")}} زمانی که ویژگی {{domxref("BatteryManager.level", "level")}} باتری به‌روزرسانی می‌شود، فعال می‌گردد.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت‌کننده رویداد تنظیم نمایید.

```js-nolint
addEventListener("levelchange", (event) => { })

onlevelchange = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال

### HTML

```html
<div id="level">(battery level unknown)</div>
<div id="stateBattery">(charging state unknown)</div>
```

### JavaScript

```js
navigator.getBattery().then((battery) => {
  battery.onlevelchange = () => {
    document.querySelector("#level").textContent = battery.level;

    if (battery.charging) {
      document.querySelector("#stateBattery").textContent = `Charging time: ${
        battery.chargingTime / 60
      }`;
    } else {
      document.querySelector("#stateBattery").textContent =
        `Discharging time: ${battery.dischargingTime / 60}`;
    }
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