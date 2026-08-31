---
title: "BatteryManager: level property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BatteryManager/level"
translated_by: "n8n + AI"
---

---
title: "BatteryManager: level property"
short-title: level
slug: Web/API/BatteryManager/level
page-type: web-api-instance-property
browser-compat: api.BatteryManager.level
---

{{ApiRef("Battery API")}}{{securecontext_header}}

ویژگی فقط‌خواندنی **`level`** در رابط {{domxref("BatteryManager")}}، سطح شارژ فعلی باتری را به صورت عددی بین `0.0` و `1.0` نشان می‌دهد. مقدار `0.0` به این معنی است که باتری خالی است و سیستم در آستانه تعلیق است. مقدار `1.0` به این معنی است که باتری کاملاً پر است یا عامل کاربر قادر به گزارش اطلاعات وضعیت باتری نیست. وقتی مقدار آن تغییر کند، رویداد {{domxref("BatteryManager/levelchange_event", "levelchange")}} فعال می‌شود.

## مثال‌ها

### دریافت سطح باتری

#### HTML

```html
<button id="get-level">Get battery level</button>
<div id="output"></div>
```

#### JavaScript

```js
const getLevel = document.querySelector("#get-level");
const output = document.querySelector("#output");

getLevel.addEventListener("click", async () => {
  if (!navigator.getBattery) {
    output.textContent = "Battery manager is unsupported";
  } else {
    const manager = await navigator.getBattery();
    const level = manager.level;
    output.textContent = `Battery level: ${level}`;
  }
});
```

#### نتیجه

{{ EmbedLiveSample('دریافت سطح باتری') }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("BatteryManager")}}
- {{domxref("Navigator.getBattery()")}}