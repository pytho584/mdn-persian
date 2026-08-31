---
title: "Battery Status API"
source: "https://developer.mozilla.org/en-US/docs/Web/API/Battery_Status_API"
translated_by: "n8n + AI"
---

---
title: Battery Status API
slug: Web/API/Battery_Status_API
page-type: web-api-overview
browser-compat:
  - api.BatteryManager
  - api.Navigator.getBattery
spec-urls: https://w3c.github.io/battery/
---

{{DefaultAPISidebar("Battery API")}}{{securecontext_header}}

**Battery Status API** که بیشتر با نام **Battery API** شناخته می‌شود، اطلاعاتی دربارهٔ سطح شارژ باتری سیستم فراهم می‌کند و به شما امکان می‌دهد تا با رویدادهایی که هنگام تغییر سطح باتری یا وضعیت شارژ ارسال می‌شوند، مطلع شوید. این قابلیت می‌تواند برای تنظیم مصرف منابع برنامهٔ شما برای کاهش مصرف باتری زمانی که باتری کم است، یا برای ذخیرهٔ تغییرات پیش از اتمام باتری به‌منظور جلوگیری از از دست رفتن داده‌ها استفاده شود.

> [!NOTE]
> این API در [Web Workers](/en-US/docs/Web/API/Web_Workers_API) _در دسترس نیست_ (از طریق {{domxref("WorkerNavigator")}} در معرض قرار نگرفته است).

## رابط‌ها

- {{domxref("BatteryManager")}}
  - : اطلاعاتی دربارهٔ سطح شارژ باتری سیستم فراهم می‌کند.

### توسعه‌هایی برای سایر رابط‌ها

- {{domxref("Navigator.getBattery()")}}
  - : یک {{JSxRef("Promise")}} برمی‌گرداند که با یک {{DOMxRef("BatteryManager")}} resolve می‌شود.

## مثال

در این مثال، تغییرات وضعیت شارژ (چه به برق وصل باشیم و در حال شارژ باشیم یا نه) و همچنین تغییرات سطح باتری و زمان‌بندی را دنبال می‌کنیم. این کار با گوش دادن به رویدادهای {{domxref("BatteryManager.chargingchange_event", "chargingchange")}}، {{domxref("BatteryManager.levelchange_event", "levelchange")}}، {{domxref("BatteryManager.chargingtimechange_event", "chargingtimechange")}} و {{domxref("BatteryManager.dischargingtimechange_event", "dischargingtimechange")}} انجام می‌شود.

```js
navigator.getBattery().then((battery) => {
  function updateAllBatteryInfo() {
    updateChargeInfo();
    updateLevelInfo();
    updateChargingInfo();
    updateDischargingInfo();
  }
  updateAllBatteryInfo();

  battery.addEventListener("chargingchange", () => {
    updateChargeInfo();
  });
  function updateChargeInfo() {
    console.log(`Battery charging? ${battery.charging ? "Yes" : "No"}`);
  }

  battery.addEventListener("levelchange", () => {
    updateLevelInfo();
  });
  function updateLevelInfo() {
    console.log(`Battery level: ${battery.level * 100}%`);
  }

  battery.addEventListener("chargingtimechange", () => {
    updateChargingInfo();
  });
  function updateChargingInfo() {
    console.log(`Battery charging time: ${battery.chargingTime} seconds`);
  }

  battery.addEventListener("dischargingtimechange", () => {
    updateDischargingInfo();
  });
  function updateDischargingInfo() {
    console.log(`Battery discharging time: ${battery.dischargingTime} seconds`);
  }
});
```

همچنین ببینید [the example in the specification](https://w3c.github.io/battery/#examples).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Hacks blog post - Using the Battery API](https://hacks.mozilla.org/2012/02/using-the-battery-api-part-of-webapi/)