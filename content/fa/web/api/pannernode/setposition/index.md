---
title: "PannerNode: setPosition() method"
short-title: setPosition()
slug: Web/API/PannerNode/setPosition
page-type: web-api-instance-method
status:
  - deprecated
browser-compat: api.PannerNode.setPosition
---

{{APIRef("Web Audio API")}}{{Deprecated_Header}}

> [!NOTE]
> جایگزین پیشنهادی برای این متد منسوخ‌شده، تنظیم مستقیم ویژگی‌های [`positionX`](/en-US/docs/Web/API/PannerNode/positionX)، [`positionY`](/en-US/docs/Web/API/PannerNode/positionY) و [`positionZ`](/en-US/docs/Web/API/PannerNode/positionZ) است.

متد `setPosition()` در رابط {{ domxref("PannerNode") }} موقعیت منبع صوتی را نسبت به شنونده تعیین می‌کند؛ شنونده با یک شیء {{domxref("AudioListener")}} نمایش داده می‌شود که در ویژگی {{domxref("BaseAudioContext.listener")}} ذخیره شده است. سه پارامتر `x`، `y` و `z` بدون واحد هستند و موقعیت منبع را در فضای سه‌بعدی با استفاده از دستگاه مختصات دکارتی راستگرد توصیف می‌کنند.

مقدار پیش‌فرض موقعیت در متد `setPosition()` برابر با `(0, 0, 0)` است.

## سینتکس

```js-nolint
setPosition(x, y, z)
```

### پارامترها

- `x`
  - : مختصات x موقعیت panner در فضای سه‌بعدی.
- `y`
  - : مختصات y موقعیت panner در فضای سه‌بعدی.
- `z`
  - : مختصات z موقعیت panner در فضای سه‌بعدی.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

برای مشاهده کد مثال، به [`BaseAudioContext.createPanner()`](/en-US/docs/Web/API/BaseAudioContext/createPanner#examples) مراجعه کنید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)