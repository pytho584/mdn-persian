---
title: "AudioContext: close() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AudioContext/close"
translated_by: "n8n + AI"
---

---
title: "AudioContext: close() method"
short-title: close()
slug: Web/API/AudioContext/close
page-type: web-api-instance-method
browser-compat: api.AudioContext.close
---

{{ APIRef("Web Audio API") }}

متد `close()` از رابط {{ domxref("AudioContext") }}، زمینه صوتی را می‌بندد و هر گونه منابع صوتی سیستمی را که از آن‌ها استفاده می‌کند، آزاد می‌کند.

این تابع به‌طور خودکار تمام اشیاء ساخته‌شده توسط `AudioContext` را آزاد نمی‌کند، مگر اینکه ارجاع‌های دیگری نیز آزاد شده باشند؛ با این حال، تمام منابع صوتی سیستمی را که ممکن است از ایجاد و استفاده از `AudioContext`های اضافی جلوگیری کنند، به‌اجبار آزاد می‌کند، پیشروی زمان صوتی در زمینه صوتی را معلق می‌کند و پردازش داده‌های صوتی را متوقف می‌کند. {{jsxref("Promise")}} بازگردانده‌شده زمانی حل می‌شود که تمام منابع مسدودکننده ایجاد `AudioContext` آزاد شده باشند. اگر این متد روی یک {{domxref("OfflineAudioContext")}} فراخوانی شود، یک استثنای `INVALID_STATE_ERR` پرتاب می‌کند.

## نحو

```js-nolint
close()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک {{jsxref("Promise")}} که با {{jsxref('undefined')}} حل می‌شود.

## مثال‌ها

قطعه کد زیر از [دموی وضعیت‌های AudioContext](https://github.com/mdn/webaudio-examples/blob/main/audiocontext-states/index.html) گرفته شده است ([اجرای زنده آن را ببینید](https://mdn.github.io/webaudio-examples/audiocontext-states/).) وقتی دکمه توقف کلیک شود، `close()` فراخوانی می‌شود. وقتی Promise حل شود، مثال به حالت آغازین خود بازنشانی می‌شود.

```js
stopBtn.onclick = () => {
  audioCtx.close().then(() => {
    startBtn.removeAttribute("disabled");
    susResBtn.setAttribute("disabled", "disabled");
    stopBtn.setAttribute("disabled", "disabled");
  });
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)
- [Web Audio API](/en-US/docs/Web/API/Web_Audio_API)