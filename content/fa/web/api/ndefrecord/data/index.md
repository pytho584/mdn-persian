---
title: "NDEFRecord: data property"
short-title: data
slug: Web/API/NDEFRecord/data
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.NDEFRecord.data
---

{{SecureContext_Header}}{{SeeCompatTable}}{{APIRef("Web NFC API")}}

خاصیت **`data`** از رابط {{DOMxRef("NDEFRecord")}} یک {{jsxref("DataView")}} شامل بایت‌های خام بارِ مفید رکورد را برمی‌گرداند.

## مقدار

یک {{jsxref("DataView")}} که شامل داده‌های بارِ مفید رمزگذاری‌شدهٔ رکورد است.

## نمونه‌ها

مثال زیر در میان رکوردهای یک شیء {{domxref("NDEFMessage")}} که از {{domxref("NDEFReadingEvent.message")}} گرفته شده است، پیمایش می‌کند. پس از انتخاب یک رکورد بر اساس {{domxref("NDEFRecord.mediaType", "mediaType")}} آن، آنچه در خاصیت `data` ذخیره شده است را رمزگشایی می‌کند.

```js
const ndef = new NDEFReader();
await ndef.scan();
ndef.onreading = (event) => {
  const decoder = new TextDecoder();
  for (const record of event.message.records) {
    if (record.mediaType === "application/json") {
      const json = JSON.parse(decoder.decode(record.data));
      const article = /^[aeio]/i.test(json.title) ? "an" : "a";
      console.log(`${json.name} is ${article} ${json.title}`);
    }
  }
};
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}