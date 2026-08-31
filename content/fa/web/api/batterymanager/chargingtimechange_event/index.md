---
title: "BatteryManager: chargingtimechange event"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BatteryManager/chargingtimechange_event"
translated_by: "n8n + AI"
short-title: chargingtimechange
slug: Web/API/BatteryManager/chargingtimechange_event
page-type: web-api-event
browser-compat: api.BatteryManager.chargingtimechange_event
---

{{ApiRef("Battery API")}}{{securecontext_header}}

رویداد **`chargingtimechange`** از رابط {{domxref("BatteryManager")}} زمانی رخ می‌دهد که ویژگی {{domxref("BatteryManager.chargingTime", "chargingTime")}} باتری به‌روز می‌شود.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("chargingtimechange", (event) => { })

onchargingtimechange = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال

### HTML

```html
<div id="level">(میزان باتری نامشخص)</div>
<div id="chargingTime">(زمان شارژ نامشخص)</div>
```

### JavaScript

```js
navigator.getBattery().then((battery) => {
  battery.onchargingtimechange = () => {
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