---
title: "AnalyserNode: getByteTimeDomainData() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/AnalyserNode/getByteTimeDomainData"
translated_by: "n8n + AI"
---

 ## `getByteTimeDomainData()`

متد `getByteTimeDomainData()` در رابط `AnalyserNode`، داده‌های waveform فعلی — یا همان داده‌های time-domain — را در یک `Uint8Array` که به آن پاس داده شده، کپی می‌کند.

اگر اندازهٔ آرایه از `fftSize` کوچک‌تر باشد، داده‌های اضافی حذف می‌شوند. اگر بزرگ‌تر باشد، خانه‌های اضافی آن نادیده گرفته می‌شوند.

## Syntax

```js-nolint
getByteTimeDomainData(array)
```

### Parameters

- `array`
  - : `Uint8Array`ای که داده‌های time-domain در آن کپی می‌شود.
    اگر اندازهٔ این آرایه از `fftSize` کوچک‌تر باشد، داده‌های اضافی حذف می‌شوند. اگر بزرگ‌تر باشد، خانه‌های اضافی آرایه نادیده گرفته می‌شوند.

### Return value

هیچ (`undefined`).

## Examples

در مثال زیر، با استفاده از `AudioContext` یک `AnalyserNode` ساخته می‌شود؛ سپس با کمک `requestAnimationFrame` و `<canvas>`، داده‌های time-domain به‌طور مداوم خوانده شده و خروجی به‌صورت یک اسیلوسکوپ (oscilloscope) برای ورودی صوتی فعلی رسم می‌شود.

برای مثال‌های کاربردی کامل‌تر، [نمونهٔ Voice-change-O-matic](https://github.com/mdn/webaudio-examples/tree/main/voice-change-o-matic) را ببینید. ([بخش مرتبط در app.js](https://github.com/mdn/webaudio-examples/blob/main/voice-change-o-matic/scripts/app.js#L108-L193))

```js
const audioCtx = new AudioContext();
const analyser = audioCtx.createAnalyser();

// …

analyser.fftSize = 2048;
const bufferLength = analyser.fftSize;
const dataArray = new Uint8Array(bufferLength);
analyser.getByteTimeDomainData(dataArray);

// draw an oscilloscope of the current audio source
function draw() {
  drawVisual = requestAnimationFrame(draw);
  analyser.getByteTimeDomainData(dataArray);

  canvasCtx.fillStyle = "rgb(200 200 200)";
  canvasCtx.fillRect(0, 0, WIDTH, HEIGHT);

  canvasCtx.lineWidth = 2;
  canvasCtx.strokeStyle = "rgb(0 0 0)";

  const sliceWidth = (WIDTH * 1.0) / bufferLength;
  let x = 0;

  canvasCtx.beginPath();
  for (let i = 0; i < bufferLength; i++) {
    const v = dataArray[i] / 128.0;
    const y = (v * HEIGHT) / 2;

    if (i === 0) {
      canvasCtx.moveTo(x, y);
    } else {
      canvasCtx.lineTo(x, y);
    }

    x += sliceWidth;
  }

  canvasCtx.lineTo(WIDTH, HEIGHT / 2);
  canvasCtx.stroke();
}

draw();
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Using the Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)

Wait, I need to remove the template macros like {{Specifications}}, {{Compat}}, and also check if I should keep the See also link. The instruction says: remove template macros. Links and URLs should not be translated but can be kept. The front-matter is removed.

However, the See also link text "Using the Web Audio API" is text. Should I translate it? The instruction says: "هرگز بلوک‌های کد، نام تگ‌ها، خواص CSS، نام متدها/توابع، مقادیر کد، لینک‌ها و URLها را ترجمه نکن". It says don't translate links and URLs. Does it mean the anchor text? Or just the URL? Usually, in these tasks, the link URL is kept as is, and the anchor text can be translated if it's descriptive. But the instruction is a bit ambiguous. Let's look again: "لینک‌ها و URLها را ترجمه نکن". This likely means don't translate the URL, and perhaps keep the link text as is if it's a technical term? No, it says "links and URLs". To be safe, I should translate the anchor text because it's part of the explanatory text, but keep the URL unchanged.

Wait, rule 2: "هرگز بلوک‌های کد، نام تگ‌ها، خواص CSS، نام متدها/توابع، مقادیر کد، لینک‌ها و URLها را ترجمه نکن". This is a strong command. It might mean the actual hyperlink text should not be translated either? But that would look weird in Persian text. However, looking at the instruction: "فقط متن توضیحی را بازنویسی کن". Link anchor text is explanatory text. I think the safest interpretation is: keep the URL path intact, but translate the anchor text if it helps readability. But the instruction explicitly groups "links" with URLs and code values. Maybe it means don't mess with the markdown link syntax. Let me reconsider.

Actually, in many MDN translation tasks, the link text is translated but the href is kept. The instruction "لینک‌ها و URLها را ترجمه نکن" probably means "do not translate the URLs and the link targets". But to be absolutely safe and avoid violating the rule, I will translate the link text if it's natural, but keep the URL. However, if the instruction is interpreted strictly, maybe I should keep the link text as well.

Let me look at the Persian instruction again: "هرگز ... لینک‌ها و URLها را ترجمه نکن". If I keep the English link text "Using the Web Audio API", it's an English sentence in the middle of Persian text. That's common in many MDN translations, but the instruction asks for natural Persian. I think translating the anchor text and keeping the URL is the correct approach. But I'll consider keeping the English link text if it's a title of a page that might be recognized. However, the instruction says "links... should not be translated". This could mean the markdown links `[text](url)` should be preserved as-is? No, that would be strange because the text is in English.

Let's think about the template macros. {{Specifications}} and {{Compat}} must be removed? The instruction says: "ماکروهای قالب مثل {{CSSRef}} یا {{EmbedInteractiveExample(...)}} را حذف کن." So yes, I should remove {{Specifications}} and {{Compat}}. What about the See also section? It's just a link.

So final structure:

Title: I should probably provide a title. The front-matter had title.