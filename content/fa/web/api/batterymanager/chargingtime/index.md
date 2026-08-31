---
title: "BatteryManager: chargingTime property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BatteryManager/chargingTime"
translated_by: "n8n + AI"
---

---
title: "BatteryManager: chargingTime property"
short-title: chargingTime
slug: Web/API/BatteryManager/chargingTime
page-type: web-api-instance-property
browser-compat: api.BatteryManager.chargingTime
---

{{ApiRef("Battery API")}}{{securecontext_header}}

خاصیت فقط‌خواندنی **`chargingTime`** از رابط {{domxref("BatteryManager")}} مدت زمانی را بر حسب ثانیه نشان می‌دهد که تا شارژ کامل باتری باقی مانده است، یا اگر باتری قبلاً کاملاً شارژ شده باشد یا عامل کاربر نتواند اطلاعات وضعیت باتری را گزارش دهد، مقدار `0` برمی‌گرداند.
اگر باتری در حال تخلیه باشد، مقدار آن {{jsxref("Infinity")}} است.
وقتی مقدار آن تغییر کند، رویداد {{domxref("BatteryManager/chargingtimechange_event", "chargingtimechange")}} فعال می‌شود.

> [!NOTE]
> حتی اگر زمان برگردانده‌شده تا ثانیه دقیق باشد،
> مرورگرها آن را به بازه‌های بزرگ‌تر گرد می‌کنند
> (معمولاً به نزدیک‌ترین ۱۵ دقیقه) به دلایل حفظ حریم خصوصی.

## مقدار

یک عدد.

## مثال‌ها

### HTML

```html
<div id="chargingTime">(charging time unknown)</div>
```

### JavaScript

```js
navigator.getBattery().then((battery) => {
  const time = battery.chargingTime;

  document.querySelector("#chargingTime").textContent =
    `Time to fully charge the battery: ${time}s`;
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