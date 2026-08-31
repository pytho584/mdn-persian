---
title: "AudioContext: suspend() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioContext/suspend"
translated_by: "n8n + AI"
---

---
title: "AudioContext: suspend() method"
short-title: suspend()
slug: Web/API/AudioContext/suspend
page-type: web-api-instance-method
browser-compat: api.AudioContext.suspend
---

{{ APIRef("Web Audio API") }}

متد `suspend()` از رابط {{ domxref("AudioContext") }} پیشروی زمان در زمینه صوتی را معلق می‌کند و به‌طور موقت دسترسی به سخت‌افزار صوتی را متوقف و مصرف CPU/باتری را در این فرآیند کاهش می‌دهد — این زمانی مفید است که بخواهید برنامه‌ای سخت‌افزار صوتی را خاموش کند وقتی برای مدتی از زمینه صوتی استفاده نخواهد کرد.

اگر روی یک {{domxref("OfflineAudioContext")}} فراخوانی شود، این متد باعث پرتاب شدن استثنای `INVALID_STATE_ERR` می‌شود.

## نحو

```js-nolint
suspend()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با {{jsxref('undefined')}} resolve می‌شود. اگر زمینه قبلاً بسته شده باشد، این Promise رد می‌شود.

## مثال‌ها

قطعه کد زیر از [AudioContext states demo](https://github.com/mdn/webaudio-examples/blob/main/audiocontext-states/index.html) ([نسخه زنده را ببینید](https://mdn.github.io/webaudio-examples/audiocontext-states/).) گرفته شده است. وقتی دکمه suspend/resume کلیک می‌شود، {{domxref("BaseAudioContext/state", "AudioContext.state")}} بررسی می‌شود — اگر `running` باشد، `suspend()` فراخوانی می‌شود؛ اگر `suspended` باشد، {{domxref("AudioContext/resume", "resume()")}} فراخوانی می‌شود. در هر حالت، برچسب متنی دکمه پس از resolve شدن Promise به‌طور مناسب به‌روزرسانی می‌شود.

```js
susResBtn.onclick = () => {
  if (audioCtx.state === "running") {
    audioCtx.suspend().then(() => {
      susResBtn.textContent = "Resume context";
    });
  } else if (audioCtx.state === "suspended") {
    audioCtx.resume().then(() => {
      susResBtn.textContent = "Suspend context";
    });
  }
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)