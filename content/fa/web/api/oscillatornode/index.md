---
title: OscillatorNode
slug: Web/API/OscillatorNode
page-type: web-api-interface
browser-compat: api.OscillatorNode
---

{{APIRef("Web Audio API")}}

رابطِ **`OscillatorNode`** یک شکل موج تناوبی مانند موج سینوسی را نمایش می‌دهد. این یک ماژول پردازش صوتی از نوع {{domxref("AudioScheduledSourceNode")}} است که باعث تولید فرکانس مشخصی از یک موج مفروض می‌شود — در واقع، یک تُنِ ثابت.

{{InheritanceDiagram}}

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">تعداد ورودی‌ها</th>
      <td><code>0</code></td>
    </tr>
    <tr>
      <th scope="row">تعداد خروجی‌ها</th>
      <td><code>1</code></td>
    </tr>
    <tr>
      <th scope="row">حالت تعداد کانال‌ها</th>
      <td><code>max</code></td>
    </tr>
    <tr>
      <th scope="row">تعداد کانال‌ها</th>
      <td><code>2</code> (در حالت شمارش پیش‌فرض استفاده نمی‌شود)</td>
    </tr>
    <tr>
      <th scope="row">تفسیر کانال‌ها</th>
      <td><code>speakers</code></td>
    </tr>
  </tbody>
</table>

## سازنده

- {{domxref("OscillatorNode.OscillatorNode", "OscillatorNode()")}}
  - : یک نمونهٔ جدید از شیء `OscillatorNode` می‌سازد و به‌صورت اختیاری شیئی را می‌پذیرد که مقادیر پیش‌فرض [ویژگی‌های گره](#instance_properties) را مشخص می‌کند. به‌عنوان جایگزین، می‌توانید از متد کارخانه‌ای {{domxref("BaseAudioContext.createOscillator()")}} استفاده کنید؛ به [ایجاد یک AudioNode](/en-US/docs/Web/API/AudioNode#creating_an_audionode) مراجعه کنید.

## ویژگی‌های نمونه

_همچنین ویژگی‌های والد خود، {{domxref("AudioScheduledSourceNode")}} را به ارث می‌برد._

- {{domxref("OscillatorNode.frequency")}}
  - : یک {{domxref("AudioParam")}} از نوع [a-rate](/en-US/docs/Web/API/AudioParam#a-rate) که فرکانس نوسان را بر حسب هرتز نشان می‌دهد (اگرچه `AudioParam` بازگشتی فقط‌خواندنی است، مقداری که نشان می‌دهد قابل تغییر است). مقدار پیش‌فرض ۴۴۰ هرتز است (نت استاندارد A میانی).
- {{domxref("OscillatorNode.detune")}}
  - : یک {{domxref("AudioParam")}} از نوع [a-rate](/en-US/docs/Web/API/AudioParam#a-rate) که میزان انحراف کوک (detune) نوسان را بر حسب سنت نشان می‌دهد (اگرچه `AudioParam` بازگشتی فقط‌خواندنی است، مقداری که نشان می‌دهد قابل تغییر است). مقدار پیش‌فرض ۰ است.
- {{domxref("OscillatorNode.type")}}
  - : رشته‌ای که شکل موجِ مورد استفاده برای پخش را مشخص می‌کند؛ این رشته می‌تواند یکی از چند مقدار استاندارد باشد، یا `custom` برای استفاده از {{domxref("PeriodicWave")}} به‌منظور توصیف یک شکل موج سفارشی. موج‌های مختلف تُن‌های متفاوتی تولید می‌کنند. مقادیر استاندارد عبارت‌اند از `"sine"`، `"square"`، `"sawtooth"`، `"triangle"` و `"custom"`. مقدار پیش‌فرض `"sine"` است.

## متدهای نمونه

_همچنین متدهای والد خود، {{domxref("AudioScheduledSourceNode")}} را به ارث می‌برد._

- {{domxref("OscillatorNode.setPeriodicWave()")}}
  - : یک {{domxref("PeriodicWave")}} تنظیم می‌کند که شکل موج تناوبی مورد استفاده به‌جای یکی از شکل‌های موج استاندارد را توصیف می‌کند؛ فراخواندن این متد، `type` را به `custom` تنظیم می‌کند.
- {{domxref("AudioScheduledSourceNode.start()")}}
  - : زمان دقیق شروع پخش تُن را مشخص می‌کند.
- {{domxref("AudioScheduledSourceNode.stop()")}}
  - : زمان توقف پخش تُن را مشخص می‌کند.

## رویدادها

_همچنین رویدادهای والد خود، {{domxref("AudioScheduledSourceNode")}} را به ارث می‌برد._

## مثال‌ها

### استفاده از OscillatorNode

مثال زیر کاربرد پایهٔ {{domxref("AudioContext")}} را برای ساخت یک گره نوسان‌ساز و شروع پخش یک تُن با آن نشان می‌دهد. برای یک مثال کاربردی، به [دموی Violent Theremin](https://mdn.github.io/webaudio-examples/violent-theremin/) مراجعه کنید ([کد مربوطه را در app.js](https://github.com/mdn/webaudio-examples/blob/main/violent-theremin/scripts/app.js) ببینید).

```js
// create web audio api context
const audioCtx = new AudioContext();

// create Oscillator node
const oscillator = audioCtx.createOscillator();

oscillator.type = "square";
oscillator.frequency.setValueAtTime(440, audioCtx.currentTime); // value in hertz
oscillator.connect(audioCtx.destination);
oscillator.start();
```

### انواع مختلف گره‌های نوسان‌ساز

چهار [نوع](/en-US/docs/Web/API/OscillatorNode/type) داخلیِ نوسان‌ساز عبارت‌اند از `sine`، `square`، `triangle` و `sawtooth`. این‌ها شکل موجِ تولیدشده توسط یک نوسان‌ساز هستند. نکتهٔ جالب: این‌ها شکل موج‌های پیش‌فرض برای بیشتر سینث‌سایزرها هستند، زیرا موج‌هایی هستند که تولید الکترونیکی آن‌ها آسان است. این مثال، شکل موج انواع مختلف را در فرکانس‌های متفاوت به‌صورت تصویری نشان می‌دهد.

```html
<div class="controls">
  <label for="type-select">
    Oscillator type
    <select id="type-select">
      <option>sine</option>
      <option>square</option>
      <option>triangle</option>
      <option>sawtooth</option>
    </select>
  </label>

  <label for="freq-range">
    Frequency
    <input
      type="range"
      min="100"
      max="800"
      step="10"
      value="250"
      id="freq-range" />
  </label>
  <button data-playing="init" id="play-button">Play</button>
</div>

<canvas id="wave-graph"></canvas>
```

```css hidden
.controls {
  display: flex;
  gap: 1rem;
  margin: 1rem 0;
  align-items: center;
}

#wave-graph {
  width: 500px;
  height: 300px;
  border: 4px solid var(--pink);
}
```

کد در دو بخش ارائه شده است: در بخش نخست، امور مربوط به صدا را راه‌اندازی می‌کنیم.

```js
const typeSelect = document.getElementById("type-select");
const frequencyControl = document.getElementById("freq-range");
const playButton = document.getElementById("play-button");

const audioCtx = new AudioContext();
const osc = new OscillatorNode(audioCtx, {
  type: typeSelect.value,
  frequency: frequencyControl.valueAsNumber,
});
// Rather than creating a new oscillator for every start and stop
// which you would do in an audio application, we are just going
// to mute/un-mute for demo purposes - this means we need a gain node
const gain = new GainNode(audioCtx);
const analyser = new AnalyserNode(audioCtx, {
  fftSize: 1024,
  smoothingTimeConstant: 0.8,
});
osc.connect(gain).connect(analyser).connect(audioCtx.destination);

typeSelect.addEventListener("change", () => {
  osc.type = typeSelect.value;
});

frequencyControl.addEventListener("input", () => {
  osc.frequency.value = frequencyControl.valueAsNumber;
});

playButton.addEventListener("click", () => {
  if (audioCtx.state === "suspended") {
    audioCtx.resume();
  }

  if (playButton.dataset.playing === "init") {
    osc.start(audioCtx.currentTime);
    playButton.dataset.playing = "true";
    playButton.innerText = "Pause";
  } else if (playButton.dataset.playing === "false") {
    gain.gain.linearRampToValueAtTime(1, audioCtx.currentTime + 0.2);
    playButton.dataset.playing = "true";
    playButton.innerText = "Pause";
  } else if (playButton.dataset.playing === "true") {
    gain.gain.linearRampToValueAtTime(0.0001, audioCtx.currentTime + 0.2);
    playButton.dataset.playing = "false";
    playButton.innerText = "Play";
  }
});
```

در بخش دوم نیز با استفاده از {{domxref("AnalyserNode")}} که در بالا ساختیم، شکل موج را روی یک canvas رسم می‌کنیم.

```js
const dpr = window.devicePixelRatio;
const w = 500 * dpr;
const h = 300 * dpr;
const canvasEl = document.getElementById("wave-graph");
canvasEl.width = w;
canvasEl.height = h;
const canvasCtx = canvasEl.getContext("2d");

const bufferLength = analyser.frequencyBinCount;
const dataArray = new Uint8Array(bufferLength);
analyser.getByteTimeDomainData(dataArray);

// draw an oscilloscope of the current oscillator
function draw() {
  analyser.getByteTimeDomainData(dataArray);

  canvasCtx.fillStyle = "white";
  canvasCtx.fillRect(0, 0, w, h);

  canvasCtx.lineWidth = 4.0;
  canvasCtx.strokeStyle = "black";
  canvasCtx.beginPath();

  const sliceWidth = (w * 1.0) / bufferLength;
  let x = 0;

  for (let i = 0; i < bufferLength; i++) {
    const v = dataArray[i] / 128.0;
    const y = (v * h) / 2;
    if (i === 0) {
      canvasCtx.moveTo(x, y);
    } else {
      canvasCtx.lineTo(x, y);
    }
    x += sliceWidth;
  }

  canvasCtx.lineTo(w, h / 2);
  canvasCtx.stroke();

  requestAnimationFrame(draw);
}

draw();
```

> [!WARNING]
> این مثال سروصدا تولید می‌کند!

{{EmbedLiveSample("Different oscillator node types", "", 500)}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از Web Audio API](/en-US/docs/Web/API/Web_Audio_API/Using_Web_Audio_API)