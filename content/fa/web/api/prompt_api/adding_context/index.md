---
title: Adding context with initial and ongoing prompt inputs
short-title: Adding context
slug: Web/API/Prompt_API/Adding_context
page-type: guide
---

{{DefaultAPISidebar("Prompt API")}}

در [راهنمای اصلی Prompt API](/en-US/docs/Web/API/Prompt_API/Using)، همه چیزهایی را که برای شروع کار با [Prompt API](/en-US/docs/Web/API/Prompt_API) لازم دارید پوشش دادیم. با این حال، آن راهنما فقط ساخت یک اپلیکیشن عمومی هوش مصنوعی برای پرامپت را پوشش می‌دهد. اگر می‌خواهید به اپلیکیشن خود شخصیت‌های گوناگون بدهید، آن را به شیوه‌های متفاوت پاسخ دهید، یا گفتگوهای گذشته را به خاطر بسپارد، باید زمینه (context) بیشتری برایش فراهم کنید. Prompt API برای این کار چند سازوکار مختلف در اختیار شما قرار می‌دهد که در این مقاله به آن‌ها پرداخته می‌شود.

## دستور زبان ورودی prompt

هنگامی که {{domxref("LanguageModel.prompt()")}} فراخوانده می‌شود، یک پارامتر `input` می‌گیرد که حاوی ورودی‌هایی است که باید به آن‌ها پاسخ داده شود:

```js
const response = await session.prompt(inputElem.value);
```

فراخوانی قبلی `prompt()` فقط یک رشته را به‌عنوان پارامتر دریافت می‌کند. این یک شکل کوتاه‌نوشته است که برای وضعیت رایجی ارائه شده که می‌خواهید فقط یک پیام متنی از کاربر به مدل بدهید. می‌توانید این شکل را بسط دهید تا `role` (نقش) شیء `input` را به‌صراحت تعیین کنید:

```js
const response = await session.prompt([
  {
    role: "user",
    content: inputElem.value,
  },
]);
```

سه نوع `role` موجود عبارت‌اند از:

- `user`
  - : ورودی‌هایی که از طرف `user` می‌آیند و API باید به آن‌ها پاسخ دهد.
- `assistant`
  - : ورودی‌هایی که از دید دستیار هوش مصنوعی نوشته می‌شوند و عمدتاً برای فراهم کردن زمینه/تاریخچه گفتگو و شکل‌دهی بیشتر به نحوه پاسخ مدل به کار می‌روند. این‌ها معمولاً برای [حفظ نشست‌ها](/en-US/docs/Web/API/Prompt_API/Preserving_sessions) و [پرامپت‌های چند نمونه‌ای (few-shot)](#few-shot_prompts) استفاده می‌شوند.
- `system`
  - : ورودی‌های سراسری از کل سیستم که به مدل دستورالعمل می‌دهند چگونه پاسخ دهد. اگر یک ورودی `system` وجود داشته باشد، باید در ابتدای ورودی‌های ارائه‌شده بیاید؛ در غیر این صورت، پرامیسی که برگردانده می‌شود با یک استثنا رد (reject) خواهد شد. ورودی‌های `system` معمولاً فقط به‌عنوان [پرامپت‌های اولیه هنگام ایجاد نشست](#providing_initial_prompts_during_session_creation) گنجانده می‌شوند.

### چند ورودی

می‌توانید چند ورودی را در آرایه قرار دهید، برای مثال:

```js
const response = await session.prompt([
  {
    role: "user",
    content: "The following is my favorite color. Do you like it?",
  },
  {
    role: "user",
    content: inputElem.value,
  },
]);
```

این کار مفید است، زیرا می‌توانید زمینه بیشتری برای کمک به مدل در ساختن پاسخ فراهم کنید، در کنار ورودی واقعی که از صفحه گرفته می‌شود و ممکن است فقط یک کلمه باشد.

### مشخص کردن نوع ورودی

به‌طور پیش‌فرض، نوع `input` برابر با `text` است. برای تعیین صریح `type`، می‌توانید شکل قبلی را به معادل کامل و بلندنویسی (longhand) گسترش دهید که به این صورت است:

```js
const response = await session.prompt([
  {
    role: "user",
    content: [
      {
        type: "text",
        value: inputElem.value,
      },
    ],
  },
]);
```

به این شکل نیازی ندارید، مگر اینکه به دستیار ورودی `image` و/یا `audio` بدهید (به [پرامپت‌های چندحالته](/en-US/docs/Web/API/Prompt_API/Multimodal) مراجعه کنید):

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

با این حال، می‌توانید مثال قبلی را با چند ورودی `user` به این شکل بازنویسی کنید؛ در این حالت هر دو پیام در یک شیء ورودی واحد قرار می‌گیرند. شاید این نسخه را برای درک ساده‌تر بیابید:

```js
const response = await session.prompt([
  {
    role: "user",
    content: [
      {
        type: "text",
        value: "The following is my favorite color. Do you like it?",
      },
      { type: "text", value: inputElem.value },
    ],
  },
]);
```

## ارائه پرامپت‌های اولیه هنگام ایجاد نشست

متد {{domxref("LanguageModel.create_static", "create()")}} می‌تواند گزینه [`initialPrompts`](/en-US/docs/Web/API/LanguageModel/create_static#initialprompts) را بپذیرد که شامل آرایه‌ای از پرامپت‌های ورودی است، دقیقاً مانند آرایه ورودی‌هایی که به `prompt()` و سایر متدها داده می‌شود. این امکان را به شما می‌دهد که هنگام ایجاد نشست، مجموعه‌ای اولیه از پرامپت‌ها را به آن بدهید تا مدل بلافاصله زمینه‌ای برای کار داشته باشد.

برای مثال:

```js
const session = await LanguageModel.create({
  initialPrompts: [
    {
      role: "system",
      content: "Respond like a pirate.",
    },
    {
      role: "assistant",
      content: "Avast ye, pirate! I am Redbeard!",
    },
    {
      role: "user",
      content:
        "Yarrrr, matey! Well met. My name is Silas Blacktooth, the scourge of Blackpool!",
    },
  ],
});
```

`initialPrompts` علاوه بر اینکه به مدل می‌گوید چه شخصیتی باید داشته باشد، برای بارگذاری یک گفتگوی ذخیره‌شده قبلی در نشست نیز مفید است، مثلاً پس از بارگذاری مجدد صفحه یا مراجعه بعدی کاربر به اپلیکیشن. به [حفظ نشست‌ها در طول بارگذاری مجدد](/en-US/docs/Web/API/Prompt_API/Preserving_sessions) مراجعه کنید.

> [!NOTE]
> شکل کوتاه‌نوشته متنی که در ابتدای بخش [دستور زبان ورودی prompt](#prompt_input_syntax) بحث شد، نمی‌تواند در گزینه `initialPrompts` در فراخوانی `create()` استفاده شود.

## پرامپت‌های چند نمونه‌ای (few-shot)

پرامپت چند نمونه‌ای (few-shot) مجموعه‌ای از جفت‌ورودی‌های نقش `user` و نقش `assistant` است که به‌عنوان مثال به API داده می‌شود تا نحوه پاسخ به نوع خاصی از ورودی را بیاموزد، پیش از آنکه از آن خواسته شود کاری مشابه را انجام دهد.

مثال زیر نشان می‌دهد که چگونه می‌توان با استفاده از یک پرامپت چند نمونه‌ای، ترجمه فرانسوی را در قالبی مشخص درخواست کرد و نمونه ورودی‌ها و خروجی‌ها را برای نمایش ساختار مورد انتظار ارائه داد.

```js
const session = await LanguageModel.create({
  expectedInputs: [{ type: "text", languages: ["en"] }],
  expectedOutputs: [{ type: "text", languages: ["en", "fr"] }],
  initialPrompts: [
    {
      role: "system",
      content:
        "Translate the user's input to French. Use the output format 'English input: French output'",
    },
    { role: "user", content: "Hello" },
    { role: "assistant", content: "Hello: Bonjour" },
    { role: "user", content: "Goodbye" },
    { role: "assistant", content: "Goodbye: Au revoir" },
    { role: "user", content: "The train is late" },
    {
      role: "assistant",
      content: "The train is late: Le train est en retard",
    },
    { role: "user", content: "My shoes are pink" },
    {
      role: "assistant",
      content: "My shoes are pink: Mes chaussures sont roses",
    },
  ],
});

const result = await session.prompt("Window");
console.log(result); // "Window: Fenêtre"
```

می‌توانید فقط پرامپت اولیه `system` را قرار دهید و مثال همچنان کار کند، اما احتمال اینکه پاسخ‌ها در قالب دلخواه ارائه شوند کمتر است.

## مثالی از ورودی‌های اولیه و چندگانه

بیایید مثالی را ببینیم که از ورودی‌های اولیه و چندگانه برای ایجاد زمینه بیشتر استفاده می‌کند. در این مثال، از کاربر خواسته می‌شود نام خود را وارد کند و API یک بررسی بامزه و غیرجدی از آن ارائه می‌دهد.

از نظر فنی، این مثال بسیار شبیه به [مثال کامل](/en-US/docs/Web/API/Prompt_API/Using#complete_example) در راهنمای قبلی است؛ تنها تفاوت‌های واقعی این است که ورودی کاربر از طریق یک {{htmlelement("input")}} تک‌خطی ارائه می‌شود نه یک {{htmlelement("textarea")}}، و فراخوانی‌های `create()` و `prompt()` متفاوت هستند. بنابراین دوباره کل کد را بررسی نمی‌کنیم. برای بررسی جزئیات بیشتر کد، به توضیحات مقاله قبلی مراجعه کنید و دکمه «Play» را در خروجی زنده نمایش‌داده‌شده فشار دهید تا کد کامل در MDN Playground باز شود.

```html hidden live-sample___rate-my-name
<h1>Prompt API rate my name!</h1>
<p>
  Enter your name (or someone else's name) into the input field and press the
  rate button to have AI review your name. First released in Chrome 148.
</p>

<h2>Input</h2>

<form>
  <div>
    <label for="prompt-text">Enter your name:</label>
    <input id="prompt-text" name="promptText" />
  </div>
  <button type="submit" id="submit">Rate my name!</button
  ><button type="button" id="abort">Abort rating</button>
</form>

<h2>Output</h2>

<p class="prompt-output"></p>
```

```css hidden live-sample___rate-my-name live-sample___excerpt-question live-sample___constraint-example
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

form div {
  display: flex;
  flex-direction: column;
  gap: 10px;
  margin-bottom: 20px;
}

input,
textarea,
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

```js hidden live-sample___rate-my-name
const form = document.querySelector("form");
const inputElem = document.querySelector("input");
const submitBtn = document.querySelector("#submit");
const abortBtn = document.querySelector("#abort");
abortBtn.disabled = true;
submitBtn.disabled = true;
const promptOutput = document.querySelector(".prompt-output");

let session;
inputElem.addEventListener("focus", () => {
  if (!("LanguageModel" in window)) {
    promptOutput.innerHTML = `<span class="error">Your browser doesn't support the Prompt API!</span>`;
    return;
  }

  if (!session) {
    init();
  }
});

async function init() {
  session = await getSession();
  promptOutput.textContent = `Session created.`;
  submitBtn.disabled = false;
}

form.addEventListener("submit", handleSubmission);

async function handleSubmission(e) {
  e.preventDefault();

  if (inputElem.value === "") {
    promptOutput.innerHTML = `<span class="error">No text entered!</span>`;
    return;
  }

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
          content: "What do you think of my name?",
        },
        {
          role: "user",
          content: inputElem.value,
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
  }
}

async function getSession() {
  const availability = await LanguageModel.availability({
    expectedInputs: [{ type: "text", languages: ["en"] }],
    expectedOutputs: [{ type: "text", languages: ["en"] }],
  });
  if (availability === "unavailable") {
    promptOutput.textContent = "Language model not available.";
    return undefined;
  } else if (availability === "available") {
    return await LanguageModel.create({
      expectedInputs: [{ type: "text", languages: ["en"] }],
      expectedOutputs: [{ type: "text", languages: ["en"] }],
      initialPrompts: [
        {
          role: "system",
          content:
            "In each case, respond with a short paragraph that pokes fun at the person's name in a sarcastic manner. Include a rating out of 10 at the end of the paragraph. The response should be cheeky, but not rude or offensive.",
        },
      ],
    });
  } else {
    return await LanguageModel.create({
      expectedInputs: [{ type: "text", languages: ["en"] }],
      expectedOutputs: [{ type: "text", languages: ["en"] }],
      initialPrompts: [
        {
          role: "system",
          content:
            "In each case, respond with a short paragraph that pokes fun at the person's name in a sarcastic manner. Include a rating out of 10 at the end of the paragraph. The response should be cheeky, but not rude or offensive.",
        },
      ],
      monitor(monitor) {
        monitor.addEventListener("downloadprogress", (e) => {
          promptOutput.textContent = `Downloading model data ${Math.floor(e.loaded * 100)}%`;
        });
      },
    });
  }
}
```

### جاوااسکریپت

هنگامی که متد {{domxref("LanguageModel.create_static", "create()")}} برای ایجاد نمونه نشست `LanguageModel` فراخوانده می‌شود، یک گزینه `initialPrompts` به آن می‌دهیم که شامل یک ورودی `system` است تا دقیقاً به مدل بگوید می‌خواهیم به هر پرامپت کاربر چگونه پاسخ دهد:

```js
return await LanguageModel.create({
  expectedInputs: [{ type: "text", languages: ["en"] }],
  expectedOutputs: [{ type: "text", languages: ["en"] }],
  initialPrompts: [
    {
      role: "system",
      content:
        "In each case, respond with a short paragraph that pokes fun at the person's name in a sarcastic manner. Include a rating out of 10 at the end of the paragraph. The response should be cheeky, but not rude or offensive.",
    },
  ],
});
```

وقتی {{domxref("LanguageModel.prompt", "prompt()")}} را روی شیء `session` صدا می‌زنیم، دو شیء ورودی `user` به آن می‌دهیم. اولی مشخص می‌کند که کاربر چه چیزی از API خواسته است، و دومی نام کاربر را که در عنصر `<input>` وارد شده در اختیار API می‌گذارد تا آن را بررسی کند.

```js
const response = await session.prompt(
  [
    {
      role: "user",
      content: "What do you think of my name?",
    },
    {
      role: "user",
      content: inputElem.value,
    },
  ],
  {
    signal: controller.signal,
  },
);
```

### نتیجه

{{EmbedLiveSample("rate-my-name", , "600px", , , , "language-model", "allow-forms")}}

سعی کنید یک نام را در `<input>` وارد کنید و سپس دکمه ثبت (submit) را فشار دهید تا از مدل هوش مصنوعی یک بررسی بامزه درباره آن نام بخواهید.

## افزودن محدودیت‌های پاسخ

هر دو متد `prompt()` و {{domxref("LanguageModel.promptStreaming", "promptStreaming()")}} یک گزینه [`responseConstraint`](/en-US/docs/Web/API/LanguageModel/prompt#responseconstraint) می‌پذیرند که مقدار آن یک شیء [JSON Schema](https://json-schema.org/) است و قالب دقیق مورد انتظار برای پاسخ‌های دستیار را تعریف می‌کند. این کار نتایج کنترل‌شده‌تری نسبت به صرفاً درخواستِ پاسخ به روشی خاص از طریق پرامپت `system` ارائه می‌دهد.

یک schema بسیار ساده می‌تواند پاسخی تعریف کند که فقط شامل یک مقدار بولی باشد:

```js
const schema = {
  type: "boolean",
};
```

برای استفاده از آن، schema را به‌عنوان مقدار گزینه `responseConstraint` قرار می‌دهید:

```js
const response = await session.prompt(
  [
    {
      role: "user",
      content: `Is this a color: ${inputElem.value}?`,
    },
  ],
  {
    responseConstraint: schema,
  },
);
```

در این حالت، محتوای پرامپت را به «Is this a color:» و به‌دنبال آن `value` یک عنصر `<input>` تنظیم می‌کنیم. در نتیجه، API بررسی می‌کند که آیا ورودی کاربر یک رنگ است یا نه و مقدار `true` یا `false` را برمی‌گرداند.

### مثال پیچیده‌تری از محدودیت پاسخ

بیایید مثال پیچیده‌تری را ببینیم تا ایده بهتری از امکانات محدودیت‌های پاسخ به دست آورید. در این مورد، schema مشخص می‌کند که پاسخ API باید به‌صورت JSON ارائه شود که شامل موارد زیر است:

- یک رشته که توصیف خلاصه‌ای را نشان می‌دهد.
- یک آرایه شامل دقیقاً سه رشته که سه نکته تأییدکننده را نشان می‌دهد.

```js
const schema = {
  $schema: "https://json-schema.org/draft/2020-12/schema",
  title: "Description with Three Bullets",
  type: "object",
  properties: {
    description: {
      type: "string",
      description: "A descriptive sentence summarizing the content.",
      minLength: 1,
    },
    bullets: {
      type: "array",
      description: "Exactly three supporting bullet points.",
      items: {
        type: "string",
        minLength: 1,
      },
      minItems: 3,
      maxItems: 3,
    },
  },
  required: ["description", "bullets"],
  additionalProperties: false,
};
```

این، مانند قبل، در گزینه `responseConstraint` فراخوانی `prompt()` قرار می‌گیرد:

```js
const response = await session.prompt(textarea.value, {
  responseConstraint: schema,
});
```

چون پاسخ به‌صورت یک رشته JSON تعیین شده، می‌توانیم آن را به یک شیء تبدیل (parse) کنیم و سپس ویژگی‌های شیء را در پاسخ خود به کار ببریم:

```js
const structuredOutput = JSON.parse(response);

promptOutput.innerHTML = `${structuredOutput.description}<br><br>- ${structuredOutput.bullets[0]}<br>- ${structuredOutput.bullets[1]}<br>- ${structuredOutput.bullets[2]}`;
```

می‌توانید این نسخه نمایشی را در مثال زنده زیر امتحان کنید:

```html hidden live-sample___constraint-example
<h1>Prompt API constraint demo</h1>
<p>
  Type in a subject. The demo uses a JSON schema to constrain the API response
  to a JSON string containing a summary string and an array containing three
  supporting strings. Released in Chrome 148, but trialed since version 137.
</p>

<h2>Input</h2>

<form>
  <div>
    <label for="prompt-text">Enter prompt text:</label>
    <textarea id="prompt-text" name="promptText" rows="6"></textarea>
  </div>
  <button type="submit" id="submit">Submit query</button
  ><button type="button" id="abort">Abort query</button>
</form>

<h2>Output</h2>

<p class="prompt-output"></p>
```

```js hidden live-sample___constraint-example
const form = document.querySelector("form");
const textarea = document.querySelector("textarea");
const submitBtn = document.querySelector("#submit");
const abortBtn = document.querySelector("#abort");
abortBtn.disabled = true;
submitBtn.disabled = true;
const promptOutput = document.querySelector(".prompt-output");

let session;
textarea.addEventListener("focus", () => {
  if (!("LanguageModel" in window)) {
    promptOutput.innerHTML = `<span class="error">Your browser doesn't support the Prompt API!</span>`;
    return;
  }

  if (!session) {
    init();
  }
});

async function init() {
  session = await getSession();
  promptOutput.textContent = `Session created.`;
  submitBtn.disabled = false;
}

form.addEventListener("submit", handleSubmission);

async function handleSubmission(e) {
  e.preventDefault();

  if (textarea.value === "") {
    promptOutput.innerHTML = `<span class="error">No text entered!</span>`;
    return;
  }

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

    const schema = {
      $schema: "https://json-schema.org/draft/2020-12/schema",
      title: "Description with Three Bullets",
      type: "object",
      properties: {
        description: {
          type: "string",
          description: "A descriptive sentence summarizing the content.",
          minLength: 1,
        },
        bullets: {
          type: "array",
          description: "Exactly three supporting bullet points.",
          items: {
            type: "string",
            minLength: 1,
          },
          minItems: 3,
          maxItems: 3,
        },
      },
      required: ["description", "bullets"],
      additionalProperties: false,
    };

    const response = await session.prompt(textarea.value, {
      signal: controller.signal,
      responseConstraint: schema,
    });

    const structuredOutput = JSON.parse(response);

    promptOutput.innerHTML = `${structuredOutput.description}<br><br>- ${structuredOutput.bullets[0]}<br>- ${structuredOutput.bullets[1]}<br>- ${structuredOutput.bullets[2]}`;

    submitBtn.disabled = false;
    abortBtn.disabled = true;
    console.log(`${session.contextUsage}/${session.contextWindow}`);
  } catch (e) {
    promptOutput.innerHTML = `<span class="error">${e}</span>`;
  }
}

async function getSession() {
  const availability = await LanguageModel.availability({
    expectedInputs: [{ type: "text", languages: ["en"] }],
    expectedOutputs: [{ type: "text", languages: ["en"] }],
  });
  if (availability === "unavailable") {
    promptOutput.textContent = "Language model not available.";
    return undefined;
  } else if (availability === "available") {
    return await LanguageModel.create({
      expectedInputs: [{ type: "text", languages: ["en"] }],
      expectedOutputs: [{ type: "text", languages: ["en"] }],
    });
  } else {
    return await LanguageModel.create({
      expectedInputs: [{ type: "text", languages: ["en"] }],
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

{{EmbedLiveSample("constraint-example", , "660px", , , , "language-model", "allow-forms")}}

## افزودن پیام‌های اضافی به زمینه (context)

استنتاج پاسخ برای یک سؤال یا جمله کاربر می‌تواند زمان زیادی طول بکشد، به‌ویژه وقتی API مجبور است با ورودی‌های متنی بزرگ و پیچیده یا ورودی‌های چندحالته کار کند.

برای کاهش تأخیر درک‌شده بین prompt کاربر و پاسخ، ایده خوبی است که پردازش درخواست توسط API را هرچه زودتر شروع کنید — یعنی پیش از ارسال ورودی اصلی توسط کاربر، زمینه مفیدی را فراهم کنید — یا بعد از آن، زمینه بیشتری اضافه کنید.

متد {{domxref("LanguageModel.append()")}} دقیقاً برای فراهم کردن چنین زمینه‌ای وجود دارد؛ این متد ورودی‌های بیشتری برای پردازش به API اضافه می‌کند بدون اینکه پاسخی از مدل تولید کند.

برای مثال، در قطعه کد زیر گزیده‌ای از یک کتاب نسبتاً مشهور را ارائه می‌دهیم. با `append()` آن را به نشست API می‌دهیم و بعد با یک فراخوانی `prompt()` یک سؤال درباره آن می‌پرسیم. مرورگر می‌تواند پردازش گزیده را زودتر شروع کند، در حالی که منتظر است سؤال پرسیده شود.

```js
const excerpt =
  "The face of Elrond was ageless, neither old nor young, though in it was written the memory of many things both glad and sorrowful. His hair was dark as the shadows of twilight, and upon it was set a circlet of silver; his eyes were grey as a clear evening, and in them was a light like the light of stars. Venerable he seemed as a king crowned with many winters, and yet hale as a tried warrior in the fullness of his strength. He was Lord of Rivendell and mighty among both Elves and Men.";

await session.append(excerpt);

// ...

const response = await session.prompt([
  {
    role: "user",
    content: "What book was the last entered text taken from?",
  },
]);
```

### یک مثال از append

بیایید پیاده‌سازی واقعی مثال گزیده متن را که پیش‌تر به آن اشاره شد ببینیم. در اینجا می‌توانید یک بخش از متن را در یک ورودی و یک سؤال درباره آن متن را در ورودی دیگری وارد کنید. پس از ارسال، پاسخ API به سؤال دقیقاً در زمینه متنی که ارائه شده پاسخ خواهد داد.

این مثال مشابه مثال‌های قبلی کار می‌کند، بنابراین همه کد را به‌طور کامل مرور نمی‌کنیم. برای مطالعه کد کامل، دکمه «Play» را در خروجی زنده نمایش‌داده‌شده فشار دهید تا کد کامل در MDN Playground باز شود.

```html hidden live-sample___excerpt-question
<h1>Prompt API excerpt question demo</h1>
<p>
  Enter a passage of text (such as a book excerpt) into the textarea, then enter
  a question about the text into the single-line input. Press the submit button
  to ask your question to the API. First released in Chrome 148.
</p>

<h2>Input</h2>

<form>
  <div>
    <label for="excerpt-text">Enter your text passage:</label>
    <textarea id="excerpt-text" name="excerpt-text" rows="6"></textarea>
  </div>
  <div>
    <label for="question-text">Enter your question:</label>
    <input id="question-text" name="question-text" />
  </div>
  <button type="submit" id="submit">Ask question!</button
  ><button type="button" id="abort">Abort question</button>
</form>

<h2>Output</h2>

<p class="prompt-output"></p>
```

```js hidden live-sample___excerpt-question
const form = document.querySelector("form");
const textareaElem = document.querySelector("textarea");
const inputElem = document.querySelector("input");
const submitBtn = document.querySelector("#submit");
const abortBtn = document.querySelector("#abort");
abortBtn.disabled = true;
submitBtn.disabled = true;
const promptOutput = document.querySelector(".prompt-output");

let session;
textareaElem.addEventListener("focus", () => {
  if (!("LanguageModel" in window)) {
    promptOutput.innerHTML = `<span class="error">Your browser doesn't support the Prompt API!</span>`;
    return;
  }

  if (!session) {
    init();
  }
});

async function init() {
  session = await getSession();
  promptOutput.textContent = `Session created.`;
}

textareaElem.addEventListener("change", appendExcerpt);
form.addEventListener("submit", handleSubmission);

async function appendExcerpt() {
  if (textareaElem.value === "") {
    promptOutput.innerHTML = `<span class="error">No passage entered!</span>`;
    return;
  }
  session.append(textareaElem.value);
  submitBtn.disabled = false;
}

async function handleSubmission(e) {
  e.preventDefault();

  if (inputElem.value === "") {
    promptOutput.innerHTML = `<span class="error">No question entered!</span>`;
    return;
  }

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
          content: "I have a question for you about the provided text.",
        },
        {
          role: "user",
          content: inputElem.value,
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
  }
}

async function getSession() {
  const availability = await LanguageModel.availability({
    expectedInputs: [{ type: "text", languages: ["en"] }],
    expectedOutputs: [{ type: "text", languages: ["en"] }],
  });
  if (availability === "unavailable") {
    promptOutput.textContent = "Language model not available.";
    return undefined;
  } else if (availability === "available") {
    return await LanguageModel.create({
      expectedInputs: [{ type: "text", languages: ["en"] }],
      expectedOutputs: [{ type: "text", languages: ["en"] }],
    });
  } else {
    return await LanguageModel.create({
      expectedInputs: [{ type: "text", languages: ["en"] }],
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

### جاوااسکریپت

در این مثال، گزیده متن در یک `<textarea>` وارد می‌شود. وقتی رویداد `change` عنصر `<textarea>` رخ می‌دهد (یعنی کاربر متنی را در آن وارد کرده و سپس فوکوس را جای دیگری برده است)، تابع `appendExcerpt()` را اجرا می‌کنیم. این تابع بررسی می‌کند که آیا `<textarea>` متنی دارد یا نه. اگر داشته باشد، متن از طریق `append()` به نشست داده می‌شود تا پردازش آغاز شود. در این مرحله، دکمه ثبت فرم را نیز فعال می‌کنیم (قبلاً آن را غیرفعال کرده بودیم تا بدون وارد کردن گزیده متن، امکان ارسال سؤال وجود نداشته باشد).

```js
textareaElem.addEventListener("change", appendExcerpt);

async function appendExcerpt() {
  if (textareaElem.value === "") {
    promptOutput.innerHTML = `<span class="error">No passage entered!</span>`;
    return;
  }
  session.append(textareaElem.value);
  submitBtn.disabled = false;
}
```

سؤال در یک `<input>` متنی وارد می‌شود. وقتی `<form>` شامل آن ورودی ارسال می‌شود (رویداد `submit` رخ می‌دهد)، تابع `handleSubmission()` را اجرا می‌کنیم. مهم‌ترین بخش بدنه این تابع، فراخوانی `prompt()` است. دو ورودی `user` به آن می‌دهیم — یکی اعلام می‌کند که سؤال درباره متن ارائه‌شده خواهد بود (متنی که قبلاً از طریق فراخوانی `append()` داده شده است) و دیگری شامل خود سؤال است که از `value` عنصر `<input>` گرفته می‌شود.

```js
form.addEventListener("submit", handleSubmission);

async function handleSubmission(e) {
  // ...

  const response = await session.prompt(
    [
      {
        role: "user",
        content: "I have a question for you about the provided text.",
      },
      {
        role: "user",
        content: inputElem.value,
      },
    ],
    {
      signal: controller.signal,
    },
  );

  promptOutput.textContent = response;

  // ...
}
```

### نتیجه

{{EmbedLiveSample("excerpt-question", , "730px", , , , "language-model", "allow-forms")}}

سعی کنید یک بخش از متن را در ناحیه متن (textarea) وارد کنید و سؤالی درباره آن بخش را در ورودی تک‌خطی بنویسید و سپس فرم را ارسال کنید.