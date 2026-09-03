---
title: "NetworkInformation: downlinkMax property"
source: "https://developer.mozilla.org/en-US/docs/Web/API/NetworkInformation/downlinkMax"
---

---
title: "NetworkInformation: downlinkMax property"
short-title: downlinkMax
slug: Web/API/NetworkInformation/downlinkMax
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.NetworkInformation.downlinkMax
---

{{APIRef("Network Information API")}}{{SeeCompatTable}} {{AvailableInWorkers}}

خاصیتِ فقط‌خواندنی **`downlinkMax`** از رابط {{domxref("NetworkInformation")}}، حداکثر سرعت دانلود را بر حسب مگابیت بر ثانیه (Mbps) برای فناوری اتصالِ زیرین بازمی‌گرداند.

## مقدار

عددی که حداکثر سرعت دانلود را بر حسب مگابیت بر ثانیه (Mb/s) برای فناوری اتصالِ زیرین نشان می‌دهد.

## مثال‌ها

مثال زیر اتصال را با استفاده از رویداد `change` پایش می‌کند و تغییرات را هنگام وقوع ثبت می‌کند.

```js
function logConnectionType() {
  let connectionType = "not supported";
  let downlinkMax = "not supported";

  if ("connection" in navigator) {
    connectionType = navigator.connection.effectiveType;

    if ("downlinkMax" in navigator.connection) {
      downlinkMax = navigator.connection.downlinkMax;
    }
  }

  console.log(
    `Current connection type: ${connectionType} (downlink max: ${downlinkMax})`,
  );
}

logConnectionType();
navigator.connection.addEventListener("change", logConnectionType);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}