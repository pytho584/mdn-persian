---
title: "BatteryManager: charging property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BatteryManager/charging"
translated_by: "n8n + AI"
---

---
title: "BatteryManager: charging property"
short-title: charging
slug: Web/API/BatteryManager/charging
page-type: web-api-instance-property
browser-compat: api.BatteryManager.charging
---

{{ApiRef("Battery API")}}{{securecontext_header}}

ویژگی فقط‌خواندنی **`charging`** در رابط {{domxref("BatteryManager")}} یک مقدار بولی است که نشان می‌دهد آیا باتری دستگاه در حال شارژ است یا خیر. وقتی مقدار آن تغییر کند، رویداد {{domxref("BatteryManager/chargingchange_event", "chargingchange")}} رخ می‌دهد.

اگر باتری در حال شارژ باشد یا عامل کاربر نتواند اطلاعات وضعیت باتری را گزارش کند، این مقدار `true` است. در غیر این صورت، `false` است.

## مقدار

یک مقدار بولی.

## مثال‌ها

### HTML

```html
<div id="charging">(charging state unknown)</div>
```

### JavaScript

```js
navigator.getBattery().then((battery) => {
  const charging = battery.charging;

  document.querySelector("#charging").textContent = charging;
});
```

{{ EmbedLiveSample('Examples', '100%', 30) }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("BatteryManager")}}
- {{domxref("Navigator.getBattery()")}}