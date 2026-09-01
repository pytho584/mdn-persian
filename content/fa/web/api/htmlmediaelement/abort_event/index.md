---
title: "HTMLMediaElement: abort event"
short-title: abort
slug: Web/API/HTMLMediaElement/abort_event
page-type: web-api-event
browser-compat: api.HTMLMediaElement.abort_event
---

{{APIRef("HTML DOM")}}

رویداد **`abort`** زمانی پرتاب می‌شود که بارگذاری منبع رسانه پیش از تکمیل‌شدن متوقف شود، اما نه در نتیجهٔ بروز خطا.
این کار معمولاً با حذف ویژگی `src` یا تنظیم آن به رشتهٔ خالی (`""`) و سپس فراخوانی `load()` انجام می‌شود.

این رویداد قابل لغو نیست و bubble نمی‌شود.

## Syntax

برای استفاده از نام رویداد، می‌توانید آن را در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} به کار ببرید، یا یک ویژگی مدیریت رویداد (event handler property) تنظیم کنید.

```js-nolint
addEventListener("abort", (event) => { })

onabort = (event) => { }
```

## Event type

یک {{domxref("Event")}} عمومی.

## Examples

مثال زیر نشان می‌دهد که چگونه می‌توان بارگذاری یک ویدیو را لغو کرد.
با فشردن دکمه، بارگذاری منبع ویدیو شروع می‌شود.
پس از یک وقفهٔ کوتاه، با حذف ویژگی `src` و فراخوانی متد `load()` بارگذاری لغو می‌شود.
اگر در زمان فراخوانی `load()` منبع ویدیو همچنان در حال بارگذاری باشد، رویداد `abort` پرتاب می‌شود.

### Abort loading a media resource

#### HTML

```html
<video controls width="250"></video>

<button id="loadAndAbort">Load and abort video</button>

<pre id="log"></pre>
```

#### CSS

```css
video,
button,
pre {
  display: block;
  margin-block: 1rem;
}
```

#### JavaScript

```js
const video = document.querySelector("video");
const loadAndAbortButton = document.querySelector("#loadAndAbort");
const log = document.querySelector("#log");

video.addEventListener("abort", () => {
  log.textContent += "Video loading aborted\n";
});

loadAndAbortButton.addEventListener("click", () => {
  log.textContent = "Loading video...\n";

  video.src = `/shared-assets/videos/flower.webm?nocache=${Date.now()}`;
  video.load();

  setTimeout(() => {
    video.removeAttribute("src");
    video.load();
  }, 50);
});
```

#### Result

{{EmbedLiveSample("Abort_loading_a_media_resource", "100%", 300)}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("HTMLAudioElement")}}
- {{domxref("HTMLVideoElement")}}
- {{HTMLElement("audio")}}
- {{HTMLElement("video")}}