---
title: "HTMLMediaElement: preservesPitch property"
short-title: preservesPitch
slug: Web/API/HTMLMediaElement/preservesPitch
page-type: web-api-instance-property
browser-compat: api.HTMLMediaElement.preservesPitch
---

{{APIRef("HTML DOM")}}

ویژگی **`HTMLMediaElement.preservesPitch`** تعیین می‌کند که آیا مرورگر باید زیر و بمی صدا را برای جبران تغییرات نرخ پخش که از طریق تنظیم {{domxref("HTMLMediaElement.playbackRate")}} ایجاد می‌شوند، تنظیم کند یا نه.

## مقدار

یک مقدار بولی (Boolean) که پیش‌فرض آن `true` است.

## مثال‌ها

### تنظیم ویژگی preservesPitch

در این مثال، یک عنصر {{HTMLElement("audio")}}، یک کنترل لغزنده (range) که نرخ پخش را تنظیم می‌کند، و یک چک‌باکس که `preservesPitch` را تعیین می‌کند، داریم.

ابتدا صدا را پخش کنید، سپس نرخ پخش را تغییر دهید و بعد از آن چک‌باکس را فعال و غیرفعال کنید.

```html
<audio
  controls
  src="https://mdn.github.io/webaudio-examples/audio-basics/outfoxing.mp3"></audio>

<div>
  <label for="rate">Adjust playback rate:</label>
  <input id="rate" type="range" min="0.25" max="3" step="0.05" value="1" />
</div>

<div>
  <label for="pitch">Preserve pitch:</label>
  <input type="checkbox" id="pitch" name="pitch" checked />
</div>
```

```css hidden
div {
  margin: 0.5rem 0;
}
```

```js
const audio = document.querySelector("audio");
document.getElementById("rate").addEventListener("change", (e) => {
  audio.playbackRate = e.target.value;
});
document.getElementById("pitch").addEventListener("change", (e) => {
  audio.preservesPitch = e.target.checked;
});
```

{{EmbedLiveSample("Setting the preservesPitch property")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLMediaElement.playbackRate")}}
- [Web Audio playbackRate explained](/en-US/docs/Web/Media/Guides/Audio_and_video_delivery/WebAudio_playbackRate_explained)