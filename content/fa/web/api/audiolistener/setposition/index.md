---
title: "AudioListener: setPosition() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioListener/setPosition"
translated_by: "n8n + AI"
---

---
title: "AudioListener: setPosition() method"
short-title: setPosition()
slug: Web/API/AudioListener/setPosition
page-type: web-api-instance-method
status:
  - deprecated
browser-compat: api.AudioListener.setPosition
---

{{ APIRef("Web Audio API") }} {{deprecated_header}}

متد `setPosition()` از رابط {{ domxref("AudioListener") }} موقعیت شنونده را تعریف می‌کند.

سه پارامتر `x`، `y` و `z` بدون واحد هستند و موقعیت شنونده را در فضای سه‌بعدی بر اساس دستگاه مختصات دکارتی راست‌گرد توصیف می‌کنند. اشیاء {{domxref("PannerNode")}} از این موقعیت نسبت به منابع صوتی فردی برای فضایی‌سازی استفاده می‌کنند.

مقدار پیش‌فرض بردار موقعیت `(0, 0, 0)` است.

> [!NOTE]
> از آنجایی که این متد منسوخ شده است، به جای آن از سه ویژگی {{domxref("AudioListener.positionX", "positionX")}}، {{domxref("AudioListener.positionY", "positionY")}} و {{domxref("AudioListener.positionZ", "positionZ")}} استفاده کنید.

## Syntax

```js-nolint
setPosition(x, y, z)
```

### Parameters

- `x`
  - : موقعیت x شنونده در فضای سه‌بعدی.
- `y`
  - : موقعیت y شنونده در فضای سه‌بعدی.
- `z`
  - : موقعیت z شنونده در فضای سه‌بعدی.

### Return value

هیچ ({{jsxref("undefined")}}).

## Examples

برای کد مثال، [`BaseAudioContext.createPanner()`](/en-US/docs/Web/API/BaseAudioContext/createPanner#examples) را ببینید.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)