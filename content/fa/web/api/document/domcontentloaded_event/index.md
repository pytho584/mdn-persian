---
title: "Document: DOMContentLoaded event"
---

---
title: "Document: DOMContentLoaded event"
short-title: DOMContentLoaded
slug: Web/API/Document/DOMContentLoaded_event
page-type: web-api-event
browser-compat: api.Document.DOMContentLoaded_event
---

{{APIRef("DOM")}}

رویداد **`DOMContentLoaded`** زمانی رخ می‌دهد که سند HTML به‌طور کامل تجزیه شده باشد و همهٔ اسکریپت‌های معوق ([`<script defer src="…">`](/en-US/docs/Web/HTML/Reference/Elements/script#defer) و [`<script type="module">`](/en-US/docs/Web/HTML/Reference/Elements/script#module)) دانلود و اجرا شده باشند. این رویداد منتظر پایان بارگذاری چیزهای دیگری مانند تصاویر، زیرفریم‌ها و اسکریپت‌های ناهمگام (async) نمی‌ماند.

`DOMContentLoaded` منتظر بارگذاری برگه‌های سبک (stylesheet) نمی‌ماند؛ با این حال، اسکریپت‌های معوق _منتظر_ برگه‌های سبک می‌مانند و رویداد `DOMContentLoaded` پس از اسکریپت‌های معوق در صف قرار می‌گیرد. همچنین، اسکریپت‌هایی که معوق یا ناهمگام نیستند (مثلاً `<script>`) منتظر می‌مانند تا برگه‌های سبکی که قبلاً تجزیه شده‌اند بارگذاری شوند.

رویداد دیگری به نام {{domxref("Window/load_event", "load")}} باید فقط برای تشخیص بارگذاری کامل صفحه استفاده شود. استفاده از `load` در جایی که `DOMContentLoaded` مناسب‌تر است، اشتباهی رایج است.

معمولاً برای جلوگیری از اجرای اسکریپت پیش از آنکه DOM موردنظر آن به‌طور کامل ساخته شود، می‌توانید اسکریپت را در انتهای بدنهٔ سند، بلافاصله پیش از تگ پایانی `</body>` قرار دهید، بدون اینکه آن را در یک شنوندهٔ رویداد (event listener) بپیچید.

این رویداد قابل‌لغو نیست.

## نحو

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید.

```js-nolint
addEventListener("DOMContentLoaded", (event) => { })
```

> [!NOTE]
> برای این رویداد هیچ ویژگی کنترل‌کنندهٔ رویداد (event handler) به نام `onDOMContentLoaded` وجود ندارد.

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

### استفادهٔ پایه

```js
document.addEventListener("DOMContentLoaded", (event) => {
  console.log("DOM fully loaded and parsed");
});
```

### به تأخیر انداختن DOMContentLoaded

```html
<script>
  document.addEventListener("DOMContentLoaded", (event) => {
    console.log("DOM fully loaded and parsed");
  });

  for (let i = 0; i < 1_000_000_000; i++);
  // This synchronous script is going to delay parsing of the DOM,
  // so the DOMContentLoaded event is going to launch later.
</script>
```

### بررسی اینکه آیا بارگذاری از قبل کامل شده است

گاهی ممکن است اسکریپت شما پس از آن اجرا شود که رویداد `DOMContentLoaded` قبلاً رخ داده است. این معمولاً زمانی اتفاق می‌افتد که اسکریپت به‌صورت ناهمگام اجرا شود. سناریوهای رایج عبارت‌اند از:

- ماژولی که پس از بارگذاری سند، به‌صورت پویا (dynamically) وارد شده است.
- اسکریپتی که از طریق `<script async>` گنجانده شده است.
- اسکریپتی که به‌صورت پویا به صفحه تزریق می‌شود.
- کدی که پس از یک عملیات ناهمگام، مانند `await fetch(...)`، از سر گرفته می‌شود، از جمله پس از یک `await` سطح بالا در یک ماژول.

در این موارد، پیش از افزودن شنوندهٔ `DOMContentLoaded` باید `readyState` سند را بررسی کنید؛ در غیر این صورت ممکن است منطق راه‌اندازی (setup) شما اصلاً اجرا نشود. برای اسکریپت‌های همگام (بدون `async`) که از قبل در نشانه‌گذاری اولیه (initial markup) وجود دارند، این وضعیت رخ نمی‌دهد؛ سند پیش از فعال کردن `DOMContentLoaded` منتظر اجرای اسکریپت می‌ماند، بنابراین همیشه مطمئن هستید که منطق راه‌اندازیِ داخل شنونده اجرا خواهد شد.

اسکریپت زیر را به‌تنهایی در نظر بگیرید:

```js
function doSomething() {
  console.info("DOM loaded");
}

if (document.readyState === "loading") {
  // Loading hasn't finished yet
  document.addEventListener("DOMContentLoaded", doSomething);
} else {
  // `DOMContentLoaded` has already fired
  doSomething();
}
```

اسکریپت نمی‌تواند روش گنجانده‌شدن خود در HTML را تعیین کند. اگر از طریق `<script async>` گنجانده شده باشد یا به‌صورت پویا تزریق شود، تا زمانی که اجرا شود، رویداد `DOMContentLoaded` قبلاً رخ داده است. برای اطمینان از اینکه `doSomething()` همیشه هنگام بارگذاری اسکریپت اجرا می‌شود، به دو مسیر نیاز داریم: یکی که اگر سند از قبل بارگذاری شده است، بلافاصله `doSomething` را اجرا کند، و دیگری که پس از بارگذاری سند، `doSomething` را اجرا کند.

> [!NOTE]
> در اینجا هیچ شرایط رقابتی (race condition) وجود ندارد — ممکن نیست سند بین بررسی `if` و فراخوانی `addEventListener()` بارگذاری شود. جاوااسکریپت از معناشناسی «اجرا تا پایان» (run-to-completion) پیروی می‌کند؛ یعنی اگر سند در یک تیک مشخص از حلقهٔ رویداد (event loop) در حال بارگذاری باشد، تا چرخهٔ بعدی نمی‌تواند بارگذاری‌شده شود، و در آن زمان هندلر `doSomething` از قبل متصل شده و فعال خواهد شد.

> [!NOTE]
> `document.readyState` پس از اتمام کار تجزیه‌گر HTML و پیش از اجرای اسکریپت‌های دارای `defer` یا `type="module"` روی `"interactive"` تنظیم می‌شود. رویداد `DOMContentLoaded` پس از اجرای این اسکریپت‌ها، اما پیش از اجرای اسکریپت‌های دارای `async` فعال می‌شود. `document.readyState` پس از اجرای اسکریپت‌های ناهمگام روی `"complete"` تنظیم می‌شود. این بدان معناست که در طول اجرای اسکریپت‌های معوق و ماژولی، `document.readyState` برابر `"interactive"` است، اما همچنان می‌توان شنونده‌های `DOMContentLoaded` را متصل کرد و آن‌ها طبق روال عادی فعال خواهند شد. در عمل، اجرای کمی زودترِ `doSomething()` اشکالی ندارد، مگر اینکه به وضعیت سراسری (global state)ای وابسته باشد که توسط سایر اسکریپت‌های معوق/ماژولی راه‌اندازی شده است.

### مثال زنده

#### HTML

```html
<div class="controls">
  <button id="reload" type="button">Reload</button>
</div>

<div class="event-log">
  <label for="eventLog">Event log:</label>
  <textarea
    readonly
    class="event-log-contents"
    rows="8"
    cols="30"
    id="eventLog"></textarea>
</div>
```

```css hidden
body {
  display: grid;
  grid-template-areas: "control log";
}

.controls {
  grid-area: control;
  display: flex;
  align-items: center;
  justify-content: center;
}

.event-log {
  grid-area: log;
}

.event-log-contents {
  resize: none;
}

label,
button {
  display: block;
}

#reload {
  height: 2rem;
}
```

#### JavaScript

```js
const log = document.querySelector(".event-log-contents");
const reload = document.querySelector("#reload");

reload.addEventListener("click", () => {
  log.textContent = "";
  setTimeout(() => {
    window.location.reload(true);
  }, 200);
});

window.addEventListener("load", (event) => {
  log.textContent += "load\n";
});

document.addEventListener("readystatechange", (event) => {
  log.textContent += `readystate: ${document.readyState}\n`;
});

document.addEventListener("DOMContentLoaded", (event) => {
  log.textContent += "DOMContentLoaded\n";
});
```

#### نتیجه

{{ EmbedLiveSample('Live_example', '100%', '160px') }}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- رویدادهای مرتبط: {{domxref("Window/load_event", "load")}}، {{domxref("Document/readystatechange_event", "readystatechange")}}، {{domxref("Window/beforeunload_event", "beforeunload")}}، {{domxref("Window/unload_event", "unload")}}