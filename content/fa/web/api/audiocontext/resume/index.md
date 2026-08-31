---
title: "AudioContext: resume() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioContext/resume"
translated_by: "n8n + AI"
---

---
title: "AudioContext: resume() method"
short-title: resume()
slug: Web/API/AudioContext/resume
page-type: web-api-instance-method
browser-compat: api.AudioContext.resume
---

{{ APIRef("Web Audio API") }}

متد **`resume()`** از رابط {{ domxref("AudioContext") }}، پیشروی زمان را در بافت صوتی که قبلاً معلق شده است، از سر می‌گیرد.

این متد اگر روی {{domxref("OfflineAudioContext")}} فراخوانی شود، باعث پرتاب استثنای `INVALID_STATE_ERR` خواهد شد.

## نحو (Syntax)

```js-nolint
resume()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که وقتی بافت از سر گرفته شود، حل می‌شود. اگر بافت قبلاً بسته شده باشد، پرامیس رد می‌شود.

## مثال‌ها

قطعه زیر از [دموی حالت‌های AudioContext](https://github.com/mdn/webaudio-examples/tree/main/audiocontext-states) گرفته شده است ([مشاهده اجرای زنده](https://mdn.github.io/webaudio-examples/audiocontext-states/)). وقتی دکمه توقف/ازسرگیری کلیک می‌شود، {{domxref("BaseAudioContext/state", "AudioContext.state")}} بررسی می‌شود — اگر `running` باشد، {{domxref("AudioContext.suspend()", "suspend()")}} فراخوانی می‌شود؛ اگر `suspended` باشد، `resume()` فراخوانی می‌شود. در هر حالت، برچسب متنی دکمه پس از حل شدن پرامیس به‌روزرسانی می‌شود.

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