---
title: "BaseAudioContext: statechange event"
source: "https://developer.mozilla.org/en-US/docs/Web/API/BaseAudioContext/statechange_event"
translated_by: "n8n + AI"
---

title: "BaseAudioContext: statechange event"
short-title: statechange
slug: Web/API/BaseAudioContext/statechange_event
page-type: web-api-event
browser-compat: api.BaseAudioContext.statechange_event

{{APIRef("Web Audio API")}}

یک رویداد `statechange` بر روی یک شیء {{DOMxRef("BaseAudioContext")}} هنگامی که عضو {{domxref("BaseAudioContext.state", "state")}} آن تغییر می‌کند، شلیک می‌شود.

## Syntax

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("statechange", (event) => { })

onstatechange = (event) => { }
```

## Event type

یک {{domxref("Event")}} عمومی.

## Examples

قطعه کد زیر از [نمونه وضعیت‌های AudioContext](https://github.com/mdn/webaudio-examples) ما گرفته شده است ([اجرای زنده آن را ببینید](https://mdn.github.io/webaudio-examples/audiocontext-states/)). کنترل‌کننده `onstatechange` برای ثبت {{domxref("BaseAudioContext.state", "state")}} فعلی در کنسول هر بار که تغییر می‌کند استفاده می‌شود.

```js
audioCtx.onstatechange = () => {
  console.log(audioCtx.state);
};
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)