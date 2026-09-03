---
title: Preserving sessions across reloads
short-title: Preserving sessions
slug: Web/API/Prompt_API/Preserving_sessions
page-type: guide
---

{{DefaultAPISidebar("Prompt API")}}

یکی از مشکلات [API Prompt](/en-US/docs/Web/API/Prompt_API) این است که مرورگر اطلاعات نشست را هنگام بارگذاری مجدد صفحه ذخیره نمی‌کند. این موضوع چندان غافلگیرکننده نیست، چون وب به‌صورت پیش‌فرض بدون حالت (stateless) است، اما همچنان یک مشکل محسوب می‌شود. برای بازیابی زمینهٔ نشست پس از بارگذاری مجدد یا راه‌اندازی دوبارهٔ مرورگر، باید سازوکاری برای ذخیرهٔ گفتگو و بازیابی آن با بهره‌گیری از راهکار سمت سرور یا سمت کلاینت پیاده‌سازی کنید.

در این مقاله یاد می‌گیرید چگونه یک نمونهٔ پرسش‌وپاسخ ساده (بسیار شبیه به [مثال کامل](/en-US/docs/Web/API/Prompt_API/Using#complete_example) در نخستین راهنمای Prompt API ما) را پیاده‌سازی کنید که در آن راهکاری برای حفظ نشست با استفاده از [Web Storage](/en-US/docs/Web/API/Web_Storage_API) به‌کار رفته باشد.

> [!NOTE]
> برای بررسی دقیق‌تر کل پایگاه کد، [کد منبع کامل](https://github.com/mdn/dom-examples/tree/main/prompt-api-web-storage) را ببینید.

## رابط کاربری

در HTML این مثال از یک عنصر {{htmlelement("textarea")}} برای وارد کردن دستورها (prompt) و یک عنصر {{htmlelement("p")}} برای نمایش پاسخ‌های API استفاده شده است. همچنین سه عنصر {{htmlelement("button")}} وجود دارد: یکی برای ارسال دستور به API، یکی برای لغو درخواست دستور در حال انجام، و یکی برای پاک کردن تاریخچهٔ نشست ذخیره‌شده.

```html
<h1>Prompt API demo</h1>
<p>
  This demo stores your previous session prompt history using the Web Storage
  API, and provides an option to delete it. First released in Chrome 148.
</p>

<h2>Input</h2>

<form>
  <div>
    <label for="prompt-text">Enter prompt text:</label>
    <textarea id="prompt-text" name="promptText" rows="6"></textarea>
  </div>
  <button type="submit" id="submit">Submit query</button
  ><button type="button" id="abort">Abort query</button>
  <button type="button" id="delete-session">Delete saved prompt history</button>
</form>

<h2>Output</h2>

<p class="prompt-output"></p>
```

برای اختصار، کد CSS را نشان نمی‌دهیم؛ از نظر استایل نکتهٔ قابل بحث چندانی وجود ندارد.

## بازیابی تاریخچهٔ دستورها

هنگامی که صفحه برای نخستین بار بارگذاری می‌شود، باید بررسی کنیم که آیا تاریخچه‌ای از دستورها ذخیره شده است یا نه؛ اگر ذخیره شده باشد، آن را در نشست بارگذاری می‌کنیم.

ابتدا متغیری به نام `promptHistory` تعریف می‌کنیم تا تاریخچهٔ ذخیره‌شده را در آن نگه داریم:

```js
let promptHistory;
```

سپس بررسی می‌کنیم که آیا خاصیتی به نام `promptHistory` در {{domxref("Window.localStorage", "localStorage")}} وجود دارد؛ این همان کلیدی است که تاریخچهٔ دستورها را زیر آن ذخیره می‌کنیم. اگر وجود داشت، آن را با استفاده از {{domxref("Storage.getItem", "getItem()")}} از حافظه برمی‌گردانیم، با {{jsxref("JSON.parse()")}} به یک آرایه تبدیل می‌کنیم و در متغیر ذخیره می‌کنیم. اکنون که تاریخی برای حذف وجود دارد، دکمهٔ حذف `<button>` را نیز فعال می‌کنیم. اگر کلید ذخیره‌شده‌ای به نام `promptHistory` وجود نداشته باشد، متغیر `promptHistory` را با یک آرایهٔ خالی مقداردهی می‌کنیم.

```js
if (localStorage.promptHistory) {
  promptHistory = JSON.parse(localStorage.getItem("promptHistory"));
  deleteBtn.disabled = false;
} else {
  promptHistory = [];
}
```

## افزودن تاریخچهٔ دستورها به نشست

سپس متغیری به نام `session` برای نگهداری نشست می‌سازیم. از آنجا که استفاده از API به [فعال‌سازی گذرا (transient activation)](/en-US/docs/Glossary/Transient_activation) نیاز دارد، مقدار `session` را درون یک event handler از نوع `focus` روی `<textarea>` مقداردهی می‌کنیم. وقتی کاربر روی `<textarea>` تمرکز می‌کند، ابتدا بررسی می‌کنیم که آیا API پشتیبانی می‌شود یا نه؛ اگر پشتیبانی نمی‌شود، پیامی دربارهٔ عدم پشتیبانی نمایش می‌دهیم و زودتر (`return`) از تابع خارج می‌شویم. سپس بررسی می‌کنیم که آیا `session` از قبل مقداری دارد یا نه (نمی‌خواهیم در هر بار تمرکز یک نشست تازه بسازیم). اگر نداشت، تابع `init()` را اجرا می‌کنیم که با تابع سفارشی `getSession()` یک نمونهٔ `LanguageModel` می‌سازد. تاریخچهٔ `promptHistory` را که پیش‌تر تعریف کردیم به `getSession()` می‌دهیم تا هنگام ساخت نشست، تاریخچهٔ ذخیره‌شده به آن افزوده شود.

اگر ساخت نمونه با موفقیت انجام شود، نمونهٔ `LanguageModel` حاصل را در متغیر `session` قرار می‌دهیم، پیام موفقیت را در `<p>` خروجی چاپ می‌کنیم و دکمهٔ ثبت `<button>` را فعال می‌کنیم (حالا که نشست در دسترس است، می‌توانیم شروع به پرس‌وجو از آن کنیم).

```js
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
  session = await getSession(promptHistory);
  promptOutput.textContent = `Session created.`;
  submitBtn.disabled = false;
}
```

حالا به تابع `getSession()` می‌پردازیم. این تابع ابتدا نیازمندی‌های موردنظر خود از مدل را از طریق متد `availability()` بررسی می‌کند تا ببیند آیا مدل در دسترس است یا نه:

- اگر مقدار `unavailable` برگردد، پیام خطای مناسبی در `<p>` خروجی چاپ می‌کنیم.
- اگر مقدار `available` برگردد، با استفاده از متد `create()` نشستی ایجاد می‌کنیم و گزینه‌های مختلفی از جمله `initialPrompts` را به آن می‌فرستیم. مقدار `initialPrompts` را برابر پارامتر تاریخچه (history) که در اختیار تابع است قرار می‌دهیم. این همان چیزی است که به نشست اجازه می‌دهد پس از هر بار بارگذاری صفحه، تاریخچهٔ دستورهای قبلی را به‌عنوان زمینه در اختیار داشته باشد.
- اگر مقدار دیگری برگردد (یعنی `downloadable` یا `downloading`)، همان فراخوانی متد `create()` را اجرا می‌کنیم، اما این بار گزینه‌ای به نام `monitor` را نیز شامل می‌شویم. هر بار که رویداد {{domxref("CreateMonitor.downloadprogress_event", "downloadprogress")}} رخ دهد، این گزینه درصد داده‌های اضافی دانلودشده را در `<p>` خروجی چاپ می‌کند.

```js
async function getSession(history) {
  const availability = await LanguageModel.availability({
    expectedInputs: [{ type: "text", languages: ["en"] }],
    expectedOutputs: [{ type: "text", languages: ["en"] }],
  });
  if (availability === "unavailable") {
    console.log(`Language model not available.`);
    return undefined;
  } else if (availability === "available") {
    return await LanguageModel.create({
      initialPrompts: history,
      expectedInputs: [{ type: "text", languages: ["en"] }],
      expectedOutputs: [{ type: "text", languages: ["en"] }],
    });
  } else {
    return await LanguageModel.create({
      initialPrompts: history,
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

## به‌روزرسانی تاریخچه پس از هر دستور

وقتی فرم ارسال می‌شود، محتوای `<textarea>` در یک فراخوانی {{domxref("LanguageModel.prompt", "prompt()")}} قرار می‌گیرد و نتیجهٔ بازگشتی در `<p>` خروجی نمایش داده می‌شود تا کاربر آن را ببیند.

مهم‌ترین بخش این مثال، روش ذخیره‌سازی تاریخچه برای استفاده‌های بعدی است. توجه کنید که پس از هر عملیات موفق، دو شیء را با استفاده از {{jsxref("Array.push", "push()")}} به آرایهٔ `promptHistory` اضافه می‌کنیم: یکی نشان‌دهندهٔ دستور `user` و دیگری نشان‌دهندهٔ پاسخ `assistant`، آن هم در قالبی که API بتواند آن را تفسیر کند. سپس `promptHistory` به‌روزشده را با {{jsxref("JSON.stringify", "stringify()")}} به رشته تبدیل می‌کنیم و با استفاده از {{domxref("Storage.setItem", "setItem()")}} در آیتم حافظهٔ وب به نام `promptHistory` ذخیره می‌کنیم. در این مرحله دکمهٔ حذف `<button>` را نیز فعال می‌کنیم، چون قطعاً تاریخچه‌ای برای حذف وجود دارد.

```js
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

    const response = await session.prompt(textarea.value, {
      signal: controller.signal,
    });

    promptOutput.textContent = response;

    submitBtn.disabled = false;
    abortBtn.disabled = true;
    console.log(`${session.contextUsage}/${session.contextWindow}`);

    promptHistory.push({ role: "user", content: textarea.value });
    promptHistory.push({ role: "assistant", content: response });
    localStorage.setItem("promptHistory", JSON.stringify(promptHistory));
    deleteBtn.disabled = false;
  } catch (e) {
    promptOutput.innerHTML = `<span class="error">${e}</span>`;
  }
}
```

## اتصال دکمهٔ حذف

هنگامی که دکمهٔ حذف `<button>` کلیک می‌شود، آیتم `promptHistory` را با استفاده از {{domxref("Storage.removeItem", "removeItem()")}} از حافظهٔ محلی حذف می‌کنیم. همچنین صفحه را با استفاده از {{domxref("Location.reload()")}} دوباره بارگذاری می‌کنیم؛ این کار راهی ساده و کم‌هزینه برای جلوگیری از ناسازگاری بین حافظهٔ محلی و نشست مدل است.

```js
deleteBtn.addEventListener("click", () => {
  localStorage.removeItem("promptHistory");
  window.location.reload();
});
```

## نتیجه

برای مشاهدهٔ عملکرد این دمو، [اجرای دمو](https://mdn.github.io/dom-examples/prompt-api-web-storage/) را در یک زبانهٔ جدید باز کنید (همچنین [کد منبع کامل](https://github.com/mdn/dom-examples/tree/main/prompt-api-web-storage) را ببینید). امکان ارائهٔ نسخهٔ کاری این دمو به‌صورت تعبیه‌شده در صفحه وجود نداشت، زیرا MDN تمام داده‌های ذخیره‌شده را پاک می‌کند.

برای نمونه، دستوری مانند "My favorite color is red" ارسال کنید، سپس صفحه را دوباره بارگذاری کنید و دستوری مانند "What is my favorite color?" بفرستید. مدل باید گفتگوی قبلی شما را به خاطر بسپارد.

حالا همین کار را تکرار کنید، اما در این فاصله دکمهٔ «Delete saved prompt history» را فشار دهید. این بار مدل گفتگوی قبلی شما را به خاطر نخواهد آورد.