---
title: "Multimodal prompts"
---

---
title: Multimodal prompts
slug: Web/API/Prompt_API/Multimodal
page-type: guide
---

{{DefaultAPISidebar("Prompt API")}}

[Prompt API](/en-US/docs/Web/API/Prompt_API) ورودی‌های چندوجهی، از جمله محتوای تصویر و صدا را می‌پذیرد. این مقاله به نحوه کار با ورودی‌های چندوجهی در برنامه شما می‌پردازد.

## تعیین انواع ورودی مورد انتظار

برای اعلام اینکه می‌خواهید در نشست خود از ورودی‌های تصویر و/یا صدا استفاده کنید، باید آن‌ها را در گزینه `expectedInputs` متد {{domxref("LanguageModel.create_static", "create()")}} قرار دهید:

```js
return await LanguageModel.create({
  expectedInputs: [
    { type: "text", languages: ["en"] },
    { type: "image" },
    { type: "audio" },
  ],
  expectedOutputs: [{ type: "text", languages: ["en"] }],
});
```

## ارائه داده‌های ورودی چندوجهی

هنگام ارائه ورودی‌های چندوجهی — برای مثال در یک فراخوانی {{domxref("LanguageModel.prompt", "prompt()")}}، {{domxref("LanguageModel.promptStreaming", "promptStreaming()")}} یا {{domxref("LanguageModel.append", "append()")}}، یا در گزینه [`initialPrompts`](/en-US/docs/Web/API/LanguageModel/create_static#initialprompts) یک فراخوانی `create()` — باید `type` داده صحیح را در شیءهای ورودی خود مشخص کنید و در ویژگی‌های `value` به منبع داده اشاره نمایید.

مثال زیر سه ورودی `user` را در یک فراخوانی `prompt()` ارسال می‌کند — برای هر نوع یک ورودی: `text`، `image` و `audio`.

```js
const response = await session.prompt([
  {
    role: "user",
    content: [
      { type: "text", value: "Describe my image and audio:" },
      { type: "image", value: imgElem },
      { type: "audio", value: audioBuffer },
    ],
  },
]);
```

## چه نوع داده‌هایی پذیرفته می‌شوند؟

Prompt API چندین قالب مختلف برای داده‌های صوتی و تصویری می‌پذیرد:

- صدا:
  - {{domxref("AudioBuffer")}}
  - {{domxref("ArrayBufferView")}}
  - {{jsxref("ArrayBuffer")}}
  - {{domxref("Blob")}}
- تصویر:
  - {{domxref("HTMLImageElement")}}
  - {{domxref("SVGImageElement")}}
  - {{domxref("HTMLVideoElement")}} (از فریم در موقعیت فعلی `<video>` استفاده می‌کند)
  - {{domxref("HTMLCanvasElement")}}
  - {{domxref("ImageBitmap")}}
  - {{domxref("OffscreenCanvas")}}
  - {{domxref("VideoFrame")}}
  - {{domxref("Blob")}}
  - {{domxref("ImageData")}}

## مثال کامل

بیایید به یک مثال چندوجهی نگاه کنیم که به شما امکان می‌دهد یک فایل تصویری محلی را انتخاب کنید و API آن را برای‌تان توصیف کند.

ساختار کلی برنامه بسیار شبیه به نمونه‌های راهنماهای قبلی است. ما تمام کد را به‌طور مشروح مرور نمی‌کنیم؛ در عوض فقط مرتبط‌ترین بخش‌ها را توضیح می‌دهیم. برای بررسی دقیق‌تر کد کامل، دکمه «Play» را در [خروجی زنده نمایش‌داده‌شده](#result) فشار دهید تا کد کامل در MDN Playground باز شود.

### HTML

فایلی که باید توصیف شود با استفاده از عنصر [`<input type="file">`](/en-US/docs/Web/HTML/Reference/Elements/input/file) انتخاب می‌شود. توصیف تصویر توسط API در یک عنصر {{htmlelement("p")}} خروجی داده می‌شود. همچنین یک عنصر {{htmlelement("img")}} برای نمایش تصویر انتخابی اضافه می‌کنیم.

```html live-sample___multimodal
<h1>Prompt API demo</h1>
<p>
  <strong>Focus the demo window, then press a key to start the app</strong>.
  This demo loads an image from your local filesystem, and then uses the Prompt
  API to describe it. First released in Chrome 148.
</p>

<h2>Input</h2>

<section>
  <form>
    <div>
      <label for="url">Choose image from your local files:</label>
      <input type="file" id="inputElem" accept="image/*" />
    </div>
    <button type="submit" id="submit">Submit query</button
    ><button type="button" id="abort">Abort query</button>
  </form>
  <img />
</section>

<h2>Output</h2>

<p class="prompt-output"></p>
```

```css hidden live-sample___multimodal
* {
  box-sizing: border-box;
}

html {
  font-family: "Helvetica", "Arial";
}

body {
  max-width: 600px;
  margin: 0 auto;
}

section {
  display: flex;
  gap: 10px;
}

form {
  flex: 1;
}

img {
  display: block;
  flex: 1;
  max-width: 300px;
  border: 1px solid #999999;
}

form div {
  display: flex;
  flex-direction: column;
  gap: 10px;
  margin-bottom: 20px;
}

input,
.prompt-output {
  padding: 5px;
}

.prompt-output {
  min-height: 150px;
  border: 1px solid black;
  width: 100%;
  display: block;
}

.error {
  color: red;
}

button {
  margin-right: 10px;
}
```

### جاوااسکریپت

ما یک متغیر `session` برای نگهداری نشست خود ایجاد می‌کنیم. از آنجا که استفاده از API به [فعال‌سازی گذرا](/en-US/docs/Glossary/Transient_activation) نیاز دارد، `session` را درون یک کنترل‌کننده رویداد `keydown` در پنجره دمو مقداردهی می‌کنیم. وقتی کاربر دمو را فوکوس می‌کند و کلیدی را فشار می‌دهد، ابتدا بررسی می‌کنیم که آیا API پشتیبانی می‌شود؛ اگر نه، پیامی مبنی بر عدم پشتیبانی چاپ می‌کنیم. اگر پشتیبانی موجود باشد، بررسی می‌کنیم که آیا `session` از قبل مقداری به آن تخصیص داده شده است (نمی‌خواهیم هر بار یک نشست جدید ایجاد کنیم). اگر نه، تابع `init()` را اجرا می‌کنیم.

```js hidden live-sample___multimodal
const form = document.querySelector("form");
const inputElem = document.querySelector("input");
const submitBtn = document.querySelector("#submit");
const abortBtn = document.querySelector("#abort");
abortBtn.disabled = true;
submitBtn.disabled = true;
inputElem.disabled = true;
const promptOutput = document.querySelector(".prompt-output");
const imgElem = document.querySelector("img");
```

```js live-sample___multimodal
let session;
window.addEventListener("keydown", () => {
  if (!("LanguageModel" in window)) {
    promptOutput.innerHTML = `<span class="error">Your browser doesn't support the Prompt API!</span>`;
  } else if (!session) {
    init();
  }
});
```

تابع `init()` با استفاده از تابع سفارشی `getSession()` یک نمونه از `LanguageModel` می‌سازد.

اگر ساخت نمونه موفقیت‌آمیز باشد، نمونه حاصل از `LanguageModel` را به متغیر `session` اختصاص می‌دهیم، یک پیام موفقیت را در `<p>` خروجی چاپ می‌کنیم، `<input>` را فعال می‌کنیم تا بتوان تصویر انتخاب کرد، و شنونده‌های رویداد را برای به‌روزرسانی رابط کاربری هنگام انتخاب یک تصویر جدید در انتخابگر فایل و مدیریت ارسال پرس‌وجوی پرامپت، اختصاص می‌دهیم.

```js live-sample___multimodal
async function init() {
  session = await getSession();
  if (!session) return;
  promptOutput.textContent = `Session created.`;
  inputElem.disabled = false;
  inputElem.addEventListener("change", getImage);
  form.addEventListener("submit", handleSubmission);
}
```

تابع `getSession()` مانند سایر مثال‌ها عمل می‌کند ([`getSession()` در اینجا توضیح داده شده است](/en-US/docs/Web/API/Prompt_API/Using#complete_example:~:text=Now%20we%20define%20the%20getSession%28%29%20function))، با این تفاوت که ما `image` را علاوه بر `text` در گزینه `expectedInputs` خود قرار می‌دهیم:

```js
return await LanguageModel.create({
  expectedInputs: [{ type: "text", languages: ["en"] }, { type: "image" }],
  expectedOutputs: [{ type: "text", languages: ["en"] }],
});
```

تابع `getImage()` ابتدا بررسی می‌کند که آیا فایلی در انتخابگر `<input type="file">` انتخاب شده است. اگر نه، یک خطای مناسب در `<p>` خروجی چاپ می‌کنیم و سپس `return` می‌کنیم. در انتهای بدنه تابع، ویژگی `src` عنصر `<img>` را با یک URL شیء ساخته‌شده از فایل انتخاب‌شده در انتخابگر فایل تنظیم می‌کنیم تا تصویر در رابط کاربری نمایش داده شود.

علاوه بر این، دو شنونده رویداد به `<img>` اضافه می‌کنیم:

- اگر رویداد `error` روی `<img>` رخ دهد، یک خطای مناسب در `<p>` خروجی چاپ می‌کنیم و سپس `return` می‌کنیم.
- اگر رویداد `load` روی `<img>` رخ دهد، یک پیام موفقیت در `<p>` خروجی چاپ می‌کنیم تا به کاربر اطلاع دهیم برنامه برای پرس‌وجو درباره تصویر آماده است، و سپس دکمه ارسال `<button>` را فعال می‌کنیم تا پرس‌وجو ارسال شود.

```js live-sample___multimodal
function getImage() {
  const file = inputElem.files[0];
  if (!file) {
    promptOutput.innerHTML = `<span class="error">No file selected!</span>`;
    return;
  }

  imgElem.addEventListener("error", () => {
    promptOutput.innerHTML = `<span class="error">Image not loaded!</span>`;
    return;
  });

  imgElem.addEventListener("load", () => {
    promptOutput.innerHTML = "Image query ready to submit!";
    submitBtn.disabled = false;
  });

  imgElem.src = URL.createObjectURL(file);
}
```

تابع `handleSubmission()` از همان جریان مثال‌های قبلی برای پرامپت کردن مدل زبانی و دریافت خروجی آن استفاده می‌کند ([توضیح را ببینید](/en-US/docs/Web/API/Prompt_API/Using#complete_example:~:text=Next%2C%20inside%20a%20try%20block%2C%20we)). تفاوت اصلی این است که در ورودی‌های فراخوانی `prompt()`، ابتدا از API می‌خواهیم تصویر را توصیف کند و سپس یک ارجاع به خود عنصر `<img>` به آن می‌دهیم.

```js live-sample___multimodal
async function handleSubmission(e) {
  e.preventDefault();
  try {
    promptOutput.textContent = "...generating response...";
    submitBtn.disabled = true;
    abortBtn.disabled = false;

    const controller = new AbortController();
    abortBtn.addEventListener("click", () => {
      controller.abort("Query aborted by user.");
      submitBtn.disabled = false;
      abortBtn.disabled = true;
    });

    const response = await session.prompt(
      [
        {
          role: "user",
          content: [
            { type: "text", value: "Please describe the following image:" },
            { type: "image", value: imgElem },
          ],
        },
      ],
      {
        signal: controller.signal,
      },
    );

    promptOutput.textContent = response;

    submitBtn.disabled = false;
    abortBtn.disabled = true;
    console.log(`${session.contextUsage}/${session.contextWindow}`);
  } catch (e) {
    promptOutput.innerHTML = `<span class="error">${e}</span>`;
    submitBtn.disabled = true;
    abortBtn.disabled = false;
  }
}
```

```js hidden live-sample___multimodal
async function getSession() {
  const availability = await LanguageModel.availability({
    expectedInputs: [{ type: "text", languages: ["en"] }, { type: "image" }],
    expectedOutputs: [{ type: "text", languages: ["en"] }],
  });
  if (availability === "unavailable") {
    promptOutput.textContent = "Language model not available.";
    return undefined;
  } else if (availability === "available") {
    return await LanguageModel.create({
      expectedInputs: [{ type: "text", languages: ["en"] }, { type: "image" }],
      expectedOutputs: [{ type: "text", languages: ["en"] }],
    });
  } else {
    return await LanguageModel.create({
      expectedInputs: [{ type: "text", languages: ["en"] }, { type: "image" }],
      expectedOutputs: [{ type: "text", languages: ["en"] }],
      monitor(monitor) {
        monitor.addEventListener("downloadprogress", (e) => {
          promptOutput.textContent = `Downloading model data ${Math.floor(e.loaded * 100)}%`;
        });
      },
    });
  }
}
```

### نتیجه

{{EmbedLiveSample("multimodal", , "630px", , , , "language-model", "allow-forms")}}

پنجره دموی تعبیه‌شده را فوکوس کنید و یک کلید از صفحه‌کلید خود را فشار دهید تا برنامه شروع شود؛ سپس با استفاده از انتخابگر فایل یک تصویر انتخاب کنید. پس از بارگیری تصویر، دکمه «Submit query» را فشار دهید. پس از اندکی انتظار، توصیف تصویر توسط API باید در `<p>` خروجی ظاهر شود.

## همچنین ببینید

- [دموی MediaRecorder + Audio Prompt API](https://chrome.dev/web-ai-demos/mediarecorder-audio-prompt/) در chrome.dev (2026)
- [دموی Prompt API با ورودی تصویر](https://chrome.dev/web-ai-demos/canvas-image-prompt/) در chrome.dev (2026)