---
title: "Element: setHTMLUnsafe() method"
short-title: setHTMLUnsafe()
slug: Web/API/Element/setHTMLUnsafe
page-type: web-api-instance-method
browser-compat: api.Element.setHTMLUnsafe
---

{{APIRef("DOM")}}

> [!WARNING]
> این متد ورودی خود را به‌عنوان HTML تجزیه و نتیجه را در DOM می‌نویسد.
> به چنین APIهایی [نقاط تزریق](/en-US/docs/Web/API/Trusted_Types_API#concepts_and_usage) گفته می‌شود و اگر ورودی در ابتدا از سوی یک مهاجم باشد، می‌توانند بردار حمله برای [اسکریپت بین‌سایتی (XSS)](/en-US/docs/Web/Security/Attacks/XSS) باشند.
>
> می‌توانید این خطر را با ارسال همیشگی اشیاء `TrustedHTML` به‌جای رشته‌ها و [اعمال Trusted Types](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) کاهش دهید.
> برای اطلاعات بیشتر، [ملاحظات امنیتی](#security_considerations) را ببینید.

> [!NOTE]
> {{domxref("Element.setHTML()")}} تقریباً همیشه باید به‌جای این متد استفاده شود — در مرورگرهایی که از آن پشتیبانی می‌کنند — زیرا همیشه ساختارهای HTML ناامن در برابر XSS را حذف می‌کند.

متد **`setHTMLUnsafe()`** از رابط {{domxref("Element")}} برای تجزیهٔ ورودی HTML به یک {{domxref("DocumentFragment")}} استفاده می‌شود؛ به‌صورت اختیاری، عناصر و ویژگی‌های ناخواسته و همچنین مواردی که به بافتار (context) تعلق ندارند را فیلتر می‌کند و سپس از آن برای جایگزینی زیردرخت (subtree) عنصر در DOM استفاده می‌کند.

## نحو

```js-nolint
setHTMLUnsafe(input)
setHTMLUnsafe(input, options)
```

### پارامترها

- `input`
  - : یک نمونه (instance) از {{domxref("TrustedHTML")}} یا رشته‌ای که HTML موردنظر برای تجزیه را تعریف می‌کند.
- `options` {{optional_inline}}
  - : یک شیء گزینه‌ها با پارامترهای اختیاری زیر:
    - `sanitizer` {{optional_inline}}
      - : یک شیء {{domxref("Sanitizer")}} یا {{domxref("SanitizerConfig")}} که مشخص می‌کند کدام عناصر ورودی مجاز یا حذف شوند.
        این مقدار همچنین می‌تواند رشته‌ای با مقدار `"default"` باشد که یک `Sanitizer` با [پیکربندی پیش‌فرض پاک‌کننده](/en-US/docs/Web/API/HTML_Sanitizer_API/Default_sanitizer_configuration) (امن در برابر XSS) اعمال می‌کند.
        اگر مشخص نشود، هیچ پاک‌کننده‌ای استفاده نمی‌شود.

        توجه داشته باشید که اگر از یک پیکربندی یکسان چند بار استفاده می‌کنید، کارآمدتر است که یک `Sanitizer` بسازید و در صورت نیاز آن را تغییر دهید.

### مقدار بازگشتی

هیچ مقداری (`undefined`).

### استثناها

- `TypeError`
  - : این خطا در موارد زیر پرتاب می‌شود:
    - اگر `input` رشته‌ای باشد در حالی که [Trusted Types](/en-US/docs/Web/API/Trusted_Types_API) توسط [CSP اعمال شده](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) باشند و هیچ سیاست پیش‌فرضی تعریف نشده باشد.
    - اگر به `options.sanitizer` مقدار زیر داده شود:
      - یک {{domxref("SanitizerConfig")}} که [معتبر](/en-US/docs/Web/API/SanitizerConfig#valid_configuration) نیست.
        برای مثال، پیکربندی که هم شامل تنظیمات «allowed» و هم «removed» باشد.
      - رشته‌ای که مقدارش `"default"` نباشد.
      - مقداری که نه {{domxref("Sanitizer")}} باشد، نه {{domxref("SanitizerConfig")}} و نه رشته.

## توضیحات

متد **`setHTMLUnsafe()`** برای تجزیهٔ ورودی HTML به یک {{domxref("DocumentFragment")}} استفاده می‌شود؛ به‌صورت اختیاری آن را از عناصر و ویژگی‌های ناخواسته پاک‌سازی (sanitize) می‌کند و عناصری را که مشخصات HTML در عنصر هدف اجازه نمی‌دهد (مانند {{htmlelement("li")}} درون یک {{htmlelement("div")}}) کنار می‌گذارد.
سپس از این `DocumentFragment` برای جایگزینی زیردرخت عنصر در DOM استفاده می‌شود.

برخلاف {{domxref("Element.innerHTML")}}، [ریشه‌های سایه اعلانی (declarative shadow roots)](/en-US/docs/Web/HTML/Reference/Elements/template#declarative_shadow_dom) موجود در ورودی به‌صورت DOM تجزیه می‌شوند.
اگر رشتهٔ HTML بیش از یک [ریشه سایه اعلانی](/en-US/docs/Web/HTML/Reference/Elements/template#declarative_shadow_dom) در یک میزبان سایه خاص تعریف کند، تنها اولین {{domxref("ShadowRoot")}} ساخته می‌شود — اعلان‌های بعدی به‌عنوان عناصر `<template>` درون همان ریشه سایه تجزیه می‌شوند.

`setHTMLUnsafe()` به‌طور پیش‌فرض هیچ پاک‌سازی‌ای انجام نمی‌دهد.
اگر هیچ پاک‌کننده‌ای به‌عنوان پارامتر ارسال نشود، تمام ساختارهای HTML موجود در ورودی تزریق خواهند شد.
بنابراین این متد به‌طور بالقوه حتی از {{domxref("Element.innerHTML")}} کماستر است، زیرا `innerHTML` هنگام تجزیه، اجرای {{htmlelement("script")}} را غیرفعال می‌کند.

### ملاحظات امنیتی

پسوند «Unsafe» در نام این متد نشان می‌دهد که حذف تمام ساختارهای HTML ناامن در برابر XSS را الزامی نمی‌کند (برخلاف {{domxref("Element.setHTML()")}}).
اگرچه در صورت استفاده از یک پاک‌کنندهٔ مناسب می‌تواند چنین کاری انجام دهد، اما الزامی به استفاده از یک پاک‌کنندهٔ مؤثر یا حتی هیچ پاک‌کننده‌ای ندارد!
بنابراین این متد می‌تواند برداری برای حملات [اسکریپت بین‌سایتی (XSS)](/en-US/docs/Web/Security/Attacks/XSS) باشد؛ در این حالت، رشته‌های بالقوه ناامنی که توسط کاربر ارائه شده‌اند بدون پاک‌سازی قبلی به DOM تزریق می‌شوند.

باید این خطر را با ارسال همیشگی اشیاء {{domxref("TrustedHTML")}} به‌جای رشته‌ها و [اعمال Trusted Types](/en-US/docs/Web/API/Trusted_Types_API#using_a_csp_to_enforce_trusted_types) با استفاده از دستور CSP [`require-trusted-types-for`](/en-US/docs/Web/HTTP/Reference/Headers/Content-Security-Policy/require-trusted-types-for) کاهش دهید.
این کار تضمین می‌کند که ورودی از یک تابع تبدیل عبور کند؛ این تابع شانس این را دارد که ورودی را قبل از تزریق [پاک‌سازی](/en-US/docs/Web/Security/Attacks/XSS#sanitization) کند و نشانه‌گذاری‌های بالقوه خطرناک (مانند عناصر {{htmlelement("script")}} و ویژگی‌های مدیریت رویداد) را حذف کند.

استفاده از `TrustedHTML` این امکان را می‌دهد که کد پاک‌سازی را تنها در چند مکان بررسی و ممیزی کنید، به‌جای اینکه در تمام نقاط تزریق پراکنده باشد.
هنگام استفاده از `TrustedHTML` نباید نیازی به ارسال پاک‌کننده به این متد داشته باشید.

اگر به هر دلیلی نمی‌توانید از `TrustedHTML` (یا حتی بهتر، `setHTML()`) استفاده کنید، ایمن‌ترین گزینه بعدی استفاده از `setHTMLUnsafe()` همراه با [پیکربندی پیش‌فرض پاک‌کننده](/en-US/docs/Web/API/HTML_Sanitizer_API/Default_sanitizer_configuration) است.

### چه زمانی باید از `setHTMLUnsafe()` استفاده کرد؟

اگر {{domxref("Element.setHTML()")}} در دسترس باشد، تقریباً هرگز نباید از `setHTMLUnsafe()` استفاده کرد، زیرا موارد بسیار کمی (اگر وجود داشته باشد) وجود دارد که ورودی HTML ارائه‌شده توسط کاربر باید شامل عناصر ناامن در برابر XSS باشد.
`setHTML()` نه‌تنها امن است، بلکه نیاز به در نظر گرفتن Trusted Types را نیز برطرف می‌کند.

استفاده از `setHTMLUnsafe()` ممکن است در موارد زیر مناسب باشد:

- نمی‌توانید از `setHTML()` یا Trusted Types استفاده کنید (به هر دلیلی) و می‌خواهید ایمن‌ترین فیلتر ممکن را داشته باشید.
  در این حالت می‌توانید از `setHTMLUnsafe()` همراه با {{domxref("Sanitizer")}} پیش‌فرض استفاده کنید تا تمام عناصر ناامن در برابر XSS فیلتر شوند.
- نمی‌توانید از `setHTML()` استفاده کنید و ممکن است ورودی شامل ریشه‌های سایه اعلانی باشد، بنابراین نمی‌توانید از {{domxref("Element.innerHTML")}} استفاده کنید.
- یک حالت مرزی (edge case) دارید که باید ورودی HTML شامل مجموعه‌ای مشخص از ساختارهای ناامن را مجاز کنید.

  در این حالت نمی‌توانید از `setHTML()` استفاده کنید، زیرا تمام ساختارهای ناامن را حذف می‌کند.
  می‌توانید از `setHTMLUnsafe()` بدون پاک‌کننده یا از `innerHTML` استفاده کنید، اما این کار همهٔ ساختارهای ناامن را مجاز می‌کند.

  گزینهٔ بهتر این است که `setHTMLUnsafe()` را با یک پاک‌کننده صدا بزنید که فقط همان عناصر و ویژگی‌های خطرناکی را که واقعاً نیاز داریم مجاز کند.
  اگرچه این کار همچنان ناامن است، اما از مجاز کردن همهٔ آن‌ها امن‌تر است.

برای نکتهٔ آخر، موقعیتی را در نظر بگیرید که کد شما به امکان استفاده از مدیریت‌کننده‌های `onclick` ناامن وابسته است.
کد زیر تأثیر روش‌ها و پاک‌کننده‌های مختلف را در این حالت نشان می‌دهد.

```js
const target = document.querySelector("#target");

const input = "<img src=x onclick=alert('onclick') onerror=alert('onerror')>";

// Safe - removes all XSS-unsafe entities.
target.setHTML(input);

// Removes no event handler attributes
target.setHTMLUnsafe(input);
target.innerHTML = input;

// Safe - removes all XSS-unsafe entities.
const configSafe = new Sanitizer();
target.setHTMLUnsafe(input, { sanitizer: configSafe });

// Removes all XSS-unsafe entities except `onclick`
const configLessSafe = new Sanitizer();
config.allowAttribute("onclick");
target.setHTMLUnsafe(input, { sanitizer: configLessSafe });
```

## مثال‌ها

### setHTMLUnsafe() با Trusted Types

برای کاهش خطر XSS، ابتدا یک شیء `TrustedHTML` از رشتهٔ حاوی HTML می‌سازیم و سپس آن شیء را به `setHTMLUnsafe()` ارسال می‌کنیم.
از آنجا که Trusted Types هنوز در همهٔ مرورگرها پشتیبانی نمی‌شود، [جایگزین کوچک Trusted Types (tinyfill)](/en-US/docs/Web/API/Trusted_Types_API#trusted_types_tinyfill) را تعریف می‌کنیم.
این کار به‌عنوان جایگزینی شفاف برای API جاوااسکریپت Trusted Types عمل می‌کند:

```js
if (typeof trustedTypes === "undefined")
  trustedTypes = { createPolicy: (n, rules) => rules };
```

سپس یک {{domxref("TrustedTypePolicy")}} می‌سازیم که یک {{domxref("TrustedTypePolicy/createHTML", "createHTML()")}} برای تبدیل رشتهٔ ورودی به نمونه‌های {{domxref("TrustedHTML")}} تعریف می‌کند.
معمولاً پیاده‌سازی‌های `createHTML()` از کتابخانه‌ای مانند [DOMPurify](https://github.com/cure53/DOMPurify) برای پاک‌سازی ورودی استفاده می‌کنند، همان‌طور که در زیر نشان داده شده است:

```js
const policy = trustedTypes.createPolicy("my-policy", {
  createHTML: (input) => DOMPurify.sanitize(input),
});
```

سپس از این شیء `policy` برای ساخت یک شیء `TrustedHTML` از رشتهٔ ورودی بالقوه ناامن استفاده می‌کنیم:

```js
// The potentially malicious string
const untrustedString = "abc <script>alert(1)<" + "/script> def";
// Create a TrustedHTML instance using the policy
const trustedHTML = policy.createHTML(untrustedString);
```

حالا که `trustedHTML` را داریم، کد زیر نشان می‌دهد که چگونه می‌توانید از آن با `setHTMLUnsafe()` استفاده کنید.
ورودی از تابع تبدیل عبور کرده است، بنابراین هیچ پاک‌کننده‌ای به متد ارسال نمی‌کنیم.

```js
// Get the target Element with id "target"
const target = document.getElementById("target");

// setHTMLUnsafe() with no sanitizer
target.setHTMLUnsafe(trustedHTML);
```

### استفاده از setHTMLUnsafe() بدون Trusted Types

این مثال حالتی را نشان می‌دهد که از Trusted Types استفاده نمی‌کنیم، بنابراین آرگومان‌های پاک‌کننده را ارسال خواهیم کرد.

کد یک رشتهٔ غیرقابل اعتماد می‌سازد و چند روش مختلف برای ارسال پاک‌کننده به متد را نشان می‌دهد.

```js
// The potentially malicious string
const untrustedString = "abc <script>alert(1)<" + "/script> def";

// Get the target Element with id "target"
const target = document.getElementById("target");

// Define custom Sanitizer and use in setHTMLUnsafe()
// This allows only elements: div, p, button, script
const sanitizer1 = new Sanitizer({
  elements: ["div", "p", "button", "script"],
});
target.setHTMLUnsafe(untrustedString, { sanitizer: sanitizer1 });

// Define custom SanitizerConfig within setHTMLUnsafe()
// Removes the <script> element but allows other potentially unsafe entities.
target.setHTMLUnsafe(untrustedString, {
  sanitizer: { removeElements: ["script"] },
});
```

### مثال زندهٔ `setHTMLUnsafe()`

این مثال یک نمایش «زنده» از این متد را هنگام فراخوانی با پاک‌کننده‌های مختلف ارائه می‌دهد.
کد دکمه‌هایی را تعریف می‌کند که می‌توانید برای تزریق یک رشتهٔ HTML روی آن‌ها کلیک کنید.
یک دکمه HTML را بدون هیچ پاک‌سازی‌ای تزریق می‌کند، و دومی از یک پاک‌کنندهٔ سفارشی استفاده می‌کند که عناصر `<script>` را مجاز می‌کند اما سایر موارد ناامن را نه.
رشتهٔ اصلی و HTML تزریق‌شده در لاگ ثبت می‌شوند تا بتوانید نتایج را در هر حالت بررسی کنید.

> [!NOTE]
> چون می‌خواهیم نحوهٔ استفاده از آرگومان پاک‌کننده را نشان دهیم، کد زیر یک رشته را به‌جای یک نوع مورد اعتماد تزریق می‌کند.
> در کد تولیدی (production) نباید این کار را انجام دهید.

#### HTML

HTML شامل دو عنصر {{htmlelement("button")}} برای فراخوانی متد با پاک‌کننده‌های مختلف، یک دکمهٔ دیگر برای بازنشانی مثال، و یک عنصر {{htmlelement("div")}} برای تزریق رشته به داخل آن است.

```html
<button id="buttonNoSanitizer" type="button">None</button>
<button id="buttonAllowScript" type="button">allowScript</button>

<button id="reload" type="button">Reload</button>
<div id="target">Original content of target element</div>
```

```html hidden
<pre id="log"></pre>
```

```css hidden
#log {
  height: 320px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
  margin: 5px;
}
```

#### JavaScript

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.textContent += text;
}
```

```js hidden
if ("Sanitizer" in window) {
```

ابتدا رشتهٔ موردنظر برای پاک‌سازی را تعریف می‌کنیم که در همهٔ حالت‌ها یکسان خواهد بود.
این رشته شامل عنصر {{htmlelement("script")}} و مدیریت‌کنندهٔ `onclick` است که هر دوی آن‌ها از نظر XSS ناامن در نظر گرفته می‌شوند.
همچنین مدیریت‌کنندهٔ دکمهٔ بارگذاری مجدد (reload) را تعریف می‌کنیم.

```js
// Define unsafe string of HTML
const unsanitizedString = `
  <div>
    <p>Paragraph to inject into shadow DOM.
      <button onclick="alert('You clicked the button!')">Click me</button>
    </p>
    <script src="path/to/a/module.js" type="module"><\/script>
    <p data-id="123">Para with <code>data-</code> attribute</p>
  </div>
`;

const reload = document.querySelector("#reload");
reload.addEventListener("click", () => document.location.reload());
```

سپس مدیریت‌کنندهٔ کلیک را برای دکمه‌ای تعریف می‌کنیم که HTML را بدون پاک‌کننده تنظیم می‌کند.
به‌طور کلی انتظار داریم که متد عناصری از رشته را که در بافتار مجاز نیستند (مانند عناصر مخصوص جدول درون یک عنصر `<div>`) حذف کند، اما در غیر این صورت با رشتهٔ ورودی مطابقت داشته باشد.
در این حالت رشته‌ها باید یکسان باشند.

```js
const buttonNoSanitizer = document.querySelector("#buttonNoSanitizer");
buttonNoSanitizer.addEventListener("click", () => {
  // Set unsafe HTML without specifying a sanitizer
  target.setHTMLUnsafe(unsanitizedString);

  // Log HTML before sanitization and after being injected
  logElement.textContent =
    "No sanitizer: string should be injected without filtering\n\n";
  log(`\nunsanitized: ${unsanitizedString}`);
  log(`\n\nsanitized: ${target.innerHTML}`);
});
```

مدیریت‌کنندهٔ کلیک بعدی، HTML هدف را با استفاده از یک پاک‌کنندهٔ سفارشی تنظیم می‌کند که فقط عناصر {{htmlelement("div")}}، {{htmlelement("p")}} و {{htmlelement("script")}} را مجاز می‌کند.
توجه داشته باشید که چون از متد `setHTMLUnsafe()` استفاده می‌کنیم، عناصر `<script>` حذف نمی‌شوند!

```js
const allowScriptButton = document.querySelector("#buttonAllowScript");
allowScriptButton.addEventListener("click", () => {
  // Set the content of the element using a custom sanitizer
  const sanitizer1 = new Sanitizer({
    elements: ["div", "p", "script"],
  });
  target.setHTMLUnsafe(unsanitizedString, { sanitizer: sanitizer1 });

  // Log HTML before sanitization and after being injected
  logElement.textContent = "Sanitizer: {elements: ['div', 'p', 'script']}\n";
  log(`\nunsanitized: ${unsanitizedString}`);
  log(`\n\nsanitized: ${target.innerHTML}`);
});
```

```js hidden
} else {
  log("The HTML Sanitizer API is NOT supported in this browser.");
  // Provide fallback or alternative behavior
}
```

#### نتایج

برای مشاهدهٔ اثر نبودِ پاک‌کننده و وجود پاک‌کنندهٔ سفارشی، به‌ترتیب روی دکمه‌های «None» و «allowScript» کلیک کنید.

هنگامی که روی دکمهٔ «None» کلیک می‌کنید، باید ببینید که ورودی و خروجی یکسان هستند، زیرا هیچ پاک‌کننده‌ای اعمال نشده است.
وقتی روی دکمهٔ «allowScript» کلیک می‌کنید، عنصر `<script>` همچنان وجود دارد، اما عنصر `<button>` حذف شده است.
با این رویکرد می‌توانید HTML امن ایجاد کنید، اما مجبور نیستید.

{{EmbedLiveSample("setHTMLUnsafe() live example","100","450px")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("ShadowRoot.setHTMLUnsafe()")}}
- {{domxref("Element.innerHTML")}}
- {{domxref("Document.parseHTML_static", "Document.parseHTML()")}} و {{domxref("Document.parseHTMLUnsafe_static", "Document.parseHTMLUnsafe()")}}