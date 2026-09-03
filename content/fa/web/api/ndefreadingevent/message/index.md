---
title: "NDEFReadingEvent: message property"
short-title: message
slug: Web/API/NDEFReadingEvent/message
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.NDEFReadingEvent.message
---

{{APIRef("Web NFC API")}}{{securecontext_header}}{{SeeCompatTable}}

ویژگی **`message`** از رابط {{domxref("NDEFReadingEvent")}} یک شیء {{DOMxRef("NDEFMessage")}} شامل پیام دریافت‌شده را برمی‌گرداند.

## مقدار

یک شیء {{domxref("NDEFMessage")}}.

## مثال‌ها

این مثال نحوه ایجاد یک تابع کمکی را نشان می‌دهد که یک تگ را می‌خواند و سپس polling را متوقف می‌کند و با حذف کارهای غیرضروری، عمر باتری را حفظ می‌کند. این مثال به راحتی می‌تواند برای زمان‌بندی پس از مدت مشخصی (به میلی‌ثانیه) گسترش یابد.

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