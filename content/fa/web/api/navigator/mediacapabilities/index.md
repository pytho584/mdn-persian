---
title: "Navigator: mediaCapabilities property"
short-title: mediaCapabilities
slug: Web/API/Navigator/mediaCapabilities
page-type: web-api-instance-property
browser-compat: api.Navigator.mediaCapabilities
---

{{APIRef("Media Capabilities API")}}

ویژگی فقط خواندنی **`mediaCapabilities`** از رابط {{domxref("Navigator")}} به یک شیء {{domxref("MediaCapabilities")}} اشاره می‌کند که می‌تواند اطلاعاتی درباره قابلیت‌های رمزگشایی و رمزگذاری برای یک فرمت رسانه و قابلیت‌های خروجی مشخص ارائه دهد.

## مقدار

یک شیء {{domxref("MediaCapabilities")}}.

## مثال‌ها

```js
navigator.mediaCapabilities
  .decodingInfo({
    type: "file",
    audio: {
      contentType: "audio/mp3",
      channels: 2,
      bitrate: 132700,
      samplerate: 5200,
    },
  })
  .then((result) => {
    console.log(
      `This configuration is ${result.supported ? "" : "not "}supported,`,
    );
    console.log(`${result.smooth ? "" : "not "}smooth, and`);
    console.log(`${result.powerEfficient ? "" : "not "}power efficient.`);
  });
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [Media Capabilities API](/en-US/docs/Web/API/Media_Capabilities_API)
- {{domxref("Navigator")}}