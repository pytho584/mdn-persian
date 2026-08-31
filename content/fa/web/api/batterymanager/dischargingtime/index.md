---
title: "BatteryManager: dischargingTime property"
short-title: dischargingTime
slug: Web/API/BatteryManager/dischargingTime
page-type: web-api-instance-property
browser-compat: api.BatteryManager.dischargingTime
source: "https://developer.mozilla.org/en-US/docs/Web/API/BatteryManager/dischargingTime"
translated_by: "n8n + AI"
---

{{ApiRef("Battery API")}}{{securecontext_header}}

ویژگی فقط‌خواندنی **`dischargingTime`** از رابط {{domxref("BatteryManager")}} مدت زمان باقی‌مانده تا تخلیه کامل باتری را بر حسب ثانیه نشان می‌دهد، یا {{jsxref("Infinity")}} اگر باتری در حال شارژ باشد به جای تخلیه، یا اگر عامل کاربر نتواند اطلاعات وضعیت باتری را گزارش دهد. هنگامی که مقدار آن تغییر کند، رویداد {{domxref("BatteryManager/dischargingtimechange_event", "dischargingtimechange")}} فعال می‌شود.

> [!NOTE]
> حتی اگر زمان برگشتی تا ثانیه دقیق باشد، مرورگرها آن را به یک بازه بزرگتر (معمولاً نزدیک‌ترین ۱۵ دقیقه) به دلایل حریم خصوصی گرد می‌کنند.

## مقدار

یک عدد.

## مثال‌ها

### HTML

```html
<div id="dischargingTime">(discharging time unknown)</div>
```

### JavaScript

```js
navigator.getBattery().then((battery) => {
  const time = battery.dischargingTime;

  document.querySelector("#dischargingTime").textContent =
    `Remaining time to fully discharge the battery: ${time}s`;
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