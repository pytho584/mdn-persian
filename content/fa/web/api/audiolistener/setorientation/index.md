---
title: "AudioListener: setOrientation() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioListener/setOrientation"
translated_by: "n8n + AI"
---

---
title: "AudioListener: setOrientation() method"
short-title: setOrientation()
slug: Web/API/AudioListener/setOrientation
page-type: web-api-instance-method
status:
  - deprecated
browser-compat: api.AudioListener.setOrientation
---

{{ APIRef("Web Audio API") }}{{deprecated_header}}

متد `setOrientation()` از رابط {{ domxref("AudioListener") }} جهت‌گیری شنونده را تعریف می‌کند.

این شامل دو بردار جهت است:

- _بردار جلو_، که توسط سه پارامتر بدون واحد `x`، `y` و `z` تعریف می‌شود، جهت چهره‌ی شنونده را توصیف می‌کند، یعنی جهتی که بینی فرد به سمت آن اشاره می‌کند. مقدار پیش‌فرض بردار جلو `(0, 0, -1)` است.
- _بردار بالا_، که توسط سه پارامتر بدون واحد `xUp`، `yUp` و `zUp` تعریف می‌شود، جهت بالای سر شنونده را توصیف می‌کند. مقدار پیش‌فرض بردار بالا `(0, 1, 0)` است.

این دو بردار باید با زاویه ۹۰ درجه از هم جدا شوند — به عبارت تحلیل خطی، آن‌ها باید بر یکدیگر عمود باشند.

## نحو

```js-nolint
setOrientation(x, y, z, xUp, yUp, zUp)
```

### پارامترها

- `x`
  - : مقدار x بردار جلو شنونده.
- `y`
  - : مقدار y بردار جلو شنونده.
- `z`
  - : مقدار z بردار جلو شنونده.
- `xUp`
  - : مقدار x بردار بالای شنونده.
- `yUp`
  - : مقدار y بردار بالای شنونده.
- `zUp`
  - : مقدار z بردار بالای شنونده.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

برای دیدن کد مثال، [`BaseAudioContext.createPanner()`](/en-US/docs/Web/API/BaseAudioContext/createPanner#examples) را ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)