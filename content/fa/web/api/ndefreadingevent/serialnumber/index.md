---
title: "NDEFReadingEvent: serialNumber property"
short-title: serialNumber
slug: Web/API/NDEFReadingEvent/serialNumber
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.NDEFReadingEvent.serialNumber
---

{{APIRef("Web NFC API")}}{{securecontext_header}}{{SeeCompatTable}}

ویژگی **`serialNumber`** از واسط {{domxref("NDEFReadingEvent")}}، شمارهٔ سریال دستگاهی را بازمی‌گرداند که برای جلوگیری از برخورد (anti-collision) و شناسایی استفاده می‌شود؛ یا اگر شمارهٔ سریالی در دسترس نباشد، یک رشتهٔ خالی بازگردانده می‌شود.

## مقدار

یک رشته (string) شامل شمارهٔ سریال دستگاه.

## مثال‌ها

این مثال نشان می‌دهد که چگونه می‌توان یک تابع کمکی نوشت که یک برچسب (tag) را می‌خواند و سپس جست‌وجوی پیوسته (polling) را متوقف می‌کند تا با حذف کارهای غیرضروری، عمر باتری حفظ شود. این مثال را به‌سادگی می‌توان گسترش داد تا پس از مدت زمان مشخصی بر حسب میلی‌ثانیه منقضی شود (timeout).

```js
const ndefReader = new NDEFReader();

function read() {
  return new Promise((resolve, reject) => {
    const controller = new AbortController();
    controller.signal.onabort = reject;
    ndefReader.addEventListener(
      "reading",
      (event) => {
        controller.abort();
        resolve(event);
      },
      { once: true },
    );
    ndefReader.scan({ signal: controller.signal }).catch((err) => reject(err));
  });
}

read().then(({ serialNumber }) => {
  console.log(serialNumber);
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}