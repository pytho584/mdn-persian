---
title: "PannerNode: distanceModel property"
short-title: distanceModel
slug: Web/API/PannerNode/distanceModel
page-type: web-api-instance-property
browser-compat: api.PannerNode.distanceModel
---

{{ APIRef("Web Audio API") }}

ویژگی `distanceModel` از رابط {{ domxref("PannerNode") }} یک مقدار شمارشی است که تعیین می‌کند از کدام الگوریتم برای کاهش بلندی صدای منبع صوتی هنگام دور شدن از شنونده استفاده شود.

مقادیر ممکن عبارتند از:

- `linear`: یک _مدل فاصله خطی_ که بهرهٔ ناشی از فاصله را طبق رابطهٔ زیر محاسبه می‌کند:
  `1 - rolloffFactor * (distance - refDistance) / (maxDistance - refDistance)`
- `inverse`: یک _مدل فاصله معکوس_ که بهرهٔ ناشی از فاصله را طبق رابطهٔ زیر محاسبه می‌کند:
  `refDistance / (refDistance + rolloffFactor * (Math.max(distance, refDistance) - refDistance))`
- `exponential`: یک _مدل فاصله نمایی_ که بهرهٔ ناشی از فاصله را طبق رابطهٔ زیر محاسبه می‌کند:
  `pow((Math.max(distance, refDistance) / refDistance, -rolloffFactor)`.

مقدار پیش‌فرض `distanceModel`، `inverse` است.

## Value

یک enum — برای جزئیات بیشتر به [`DistanceModelType`](https://webaudio.github.io/web-audio-api/#idl-def-DistanceModelType) مراجعه کنید.

## Examples

برای کد نمونه، [`BaseAudioContext.createPanner()`](/en-US/docs/Web/API/BaseAudioContext/createPanner#examples) را ببینید.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- [مبانی فضاسازی صوتی Web Audio](/en-US/docs/Web/API/Web_Audio_API/Web_audio_spatialization_basics)