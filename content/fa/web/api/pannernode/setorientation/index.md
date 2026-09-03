---
title: "PannerNode: setOrientation() method"
short-title: setOrientation()
slug: Web/API/PannerNode/setOrientation
page-type: web-api-instance-method
status:
  - deprecated
browser-compat: api.PannerNode.setOrientation
---

{{APIRef("Web Audio API")}}{{Deprecated_Header}}

> [!NOTE]
> جایگزین پیشنهادی برای این متد منسوخ‌شده، تنظیم مستقیم ویژگی‌های [`orientationX`](/en-US/docs/Web/API/PannerNode/orientationX)، [`orientationY`](/en-US/docs/Web/API/PannerNode/orientationY) و [`orientationZ`](/en-US/docs/Web/API/PannerNode/orientationZ) است.

متد `setOrientation()` از رابط {{ domxref("PannerNode") }} جهت پخش منبع صوتی را تعریف می‌کند.

اگر صدا بسیار جهتی باشد — که توسط سه ویژگی مربوط به مخروط، یعنی {{domxref("PannerNode.coneInnerAngle")}}، {{domxref("PannerNode.coneOuterAngle")}} و {{domxref("PannerNode.coneOuterGain")}} کنترل می‌شود — این موضوع می‌تواند تأثیر زیادی داشته باشد. در چنین حالتی، صدایی که در جهت مخالف شنونده پخش شود ممکن است بسیار آرام یا حتی کاملاً بی‌صدا باشد.

سه پارامتر `x`، `y` و `z` بدون واحد هستند و یک بردار جهت در فضای سه‌بعدی را با استفاده از دستگاه مختصات دکارتی راست‌گرد توصیف می‌کنند. مقدار پیش‌فرض بردار جهت `(1, 0, 0)` است.

## Syntax

```js-nolint
setOrientation(x, y, z)
```

### Parameters

- `x`
  - : مقدار x بردار جهت panner در فضای سه‌بعدی.
- `y`
  - : مقدار y بردار جهت panner در فضای سه‌بعدی.
- `z`
  - : مقدار z بردار جهت panner در فضای سه‌بعدی.

### Return value

هیچ ({{jsxref("undefined")}}).

## Examples

برای کد نمونه، [`BaseAudioContext.createPanner()`](/en-US/docs/Web/API/BaseAudioContext/createPanner#examples) را ببینید.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)