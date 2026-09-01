---
title: "Element: setHTML() method"
short-title: setHTML()
slug: Web/API/Element/setHTML
page-type: web-api-instance-method
browser-compat: api.Element.setHTML
---

{{APIRef("HTML Sanitizer API")}}

متد **`setHTML()`** در رابط {{domxref("Element")}} روشی امن در برابر XSS ارائه می‌دهد که یک رشته HTML را تجزیه و پاک‌سازی (sanitize) کرده و آن را به‌صورت زیردرختی از عنصر، در DOM وارد می‌کند.

این متد هر عنصر و ویژگی‌ای را که ناامن در برابر XSS تلقی می‌شود حذف می‌کند، حتی اگر توسط یک پاک‌ساز (sanitizer) عبوری مجاز شده باشد.
به‌طور قابل توجه، عناصر زیر همیشه حذف می‌شوند: {{HTMLElement("script")}}، {{HTMLElement("frame")}}، {{HTMLElement("iframe")}}، {{HTMLElement("embed")}}، {{HTMLElement("object")}}، {{SVGElement("use")}} و ویژگی‌های مدیریت رویداد (event handler attributes).

توصیه می‌شود (در صورت پشتیبانی) به‌عنوان جایگزینی مستقیم برای {{domxref("Element.innerHTML")}} هنگام تنظیم رشته HTML ارائه‌شده توسط کاربر استفاده شود.

## Syntax

```js-nolint
setHTML(input)
setHTML(input, options)
```

### پارامترها

- `input`
  - : رشته‌ای که HTML مورد نظر برای پاک‌سازی و تزریق به عنصر را تعریف می‌کند.
- `options` {{optional_inline}}
  - : یک شیء گزینه‌ها با پارامترهای اختیاری زیر:
    - `sanitizer`
      - : یک شیء {{domxref("Sanitizer")}} یا {{domxref("SanitizerConfig")}} که مشخص می‌کند کدام عناصر ورودی مجاز یا حذف شوند، یا رشته `"default"` برای پیکربندی پیش‌فرض.
        این متد هر عنصر و ویژگی ناامن در برابر XSS را حذف می‌کند، حتی اگر توسط پاک‌ساز مجاز شده باشد.
        اگر مشخص نشود، از [پیکربندی پیش‌فرض پاک‌ساز](/en-US/docs/Web/API/HTML_Sanitizer_API/Default_sanitizer_configuration) استفاده می‌شود.

        توجه داشته باشید که اگر از همان پیکربندی چندین بار استفاده می‌کنید، انتظار می‌رود استفاده از یک شیء `Sanitizer` و تغییر آن در صورت نیاز، کارآمدتر باشد.

### مقدار بازگشتی

هیچ (`undefined`).

### استثناها

- `TypeError`
  - : اگر `options.sanitizer` یکی از موارد زیر باشد پرتاب می‌شود:
    - یک {{domxref("SanitizerConfig")}} که [معتبر](/en-US/docs/Web/API/SanitizerConfig#valid_configuration) نیست.
      برای مثال، پیکربندی که شامل هر دو تنظیمات «مجاز» (allowed) و «حذف‌شده» (removed) باشد.
    - رشته‌ای که مقدار آن `"default"` نباشد.
    - مقداری که نه {{domxref("Sanitizer")}} باشد، نه {{domxref("SanitizerConfig")}} و نه رشته.

## توضیحات

متد **`setHTML()`** یک روش امن در برابر XSS برای تجزیه و پاک‌سازی یک رشته HTML به یک {{domxref("DocumentFragment")}} ارائه می‌دهد و سپس آن را به‌صورت زیردرختی از عنصر، در DOM وارد می‌کند.

`setHTML()` هر عنصری را در رشته HTML ورودی که در بافت عنصر جاری نامعتبر است، مانند یک عنصر {{htmlelement("col")}} خارج از {{htmlelement("table")}}، حذف می‌کند.
سپس هر موجودیت HTML که توسط پیکربندی پاک‌ساز مجاز نیست را حذف می‌کند و علاوه بر آن، هر عنصر یا ویژگی ناامن در برابر XSS را — صرف‌نظر از اینکه توسط پاک‌ساز مجاز شده باشند یا نه — حذف می‌کند.

اگر در پارامتر `options.sanitizer` پاک‌سازی مشخص نشود، `setHTML()` با [پیکربندی پیش‌فرض پاک‌ساز](/en-US/docs/Web/API/HTML_Sanitizer_API/Default_sanitizer_configuration) استفاده می‌شود.
این پیکربندی برای اکثر موارد استفاده مناسب است، زیرا از حملات XSS و همچنین حملات دیگری مانند clickjacking یا جعل (spoofing) جلوگیری می‌کند.

می‌توان یک `Sanitizer` یا `SanitizerConfig` سفارشی مشخص کرد تا تعیین شود کدام عناصر، ویژگی‌ها و دیدگاه‌ها (comments) مجاز یا حذف شوند.
توجه داشته باشید که حتی اگر گزینه‌های ناامن توسط پاک‌ساز مجاز شوند، هنگام استفاده از این متد همچنان حذف خواهند شد (همان عناصری را حذف می‌کند که یک پاک‌ساز که روی آن {{domxref('Sanitizer.removeUnsafe()')}} فراخوانی شده است).

`setHTML()` باید به‌جای {{domxref("Element.innerHTML")}} برای درج رشته‌های HTML غیرقابل اعتماد در یک عنصر استفاده شود.
همچنین باید به‌جای {{domxref("Element.setHTMLUnsafe()")}} استفاده شود، مگر اینکه نیاز خاصی به مجاز دانستن عناصر و ویژگی‌های ناامن وجود داشته باشد.

توجه داشته باشید که از آنجا که این متد همیشه رشته‌های ورودی را از موجودیت‌های ناامن در برابر XSS پاک‌سازی می‌کند، با استفاده از [Trusted Types API](/en-US/docs/Web/API/Trusted_Types_API) امن یا اعتبارسنجی نمی‌شود.

### تجزیه مجدد و XSS جهش‌یافته (mXSS)

حتی پس از پاک‌سازی ورودی HTML با `setHTML()`، باز هم безопасن نیست که HTML را سریال‌سازی کرده و با `innerHTML` دوباره تجزیه کنید.
برای مثال، کد زیر ناامن است.

```js example-bad
div.setHTML(unsafeString); // امن
const serializedHTML = div.innerHTML; // دیگر پاک‌سازی نشده است!
otherElement.innerHTML = serializedHTML;
```

دلیل این امر آن است که پاک‌سازی به بافت (context) وابسته است.
وقتی `setHTML()` را روی یک عنصر خاص فراخوانی می‌کنید، عناصر و ویژگی‌های ناامن برای آن بافت حذف می‌شوند.
اگر HTML را سریال‌سازی کرده و مستقیماً در عنصر دیگری استفاده کنید، ممکن است همچنان حاوی عناصری باشد که در آن عنصر ناامن هستند.

این کار امن است (هرچند بی‌فایده):

```js example-good
div.setHTML(unsafeString); // امن
const serializedHTML = div.innerHTML; // به‌صورت یک رشته ساده سریال‌سازی شد
otherDiv.setHTML(serializedHTML); // امن — دوباره توسط setHTML() پاک‌سازی شد
```

دسته‌ای از حملات وجود دارند که از این نقص بهره می‌برند و به آنها [mutation XSS](https://html.spec.whatwg.org/multipage/dynamic-markup-insertion.html#sanitizer-security-mxss) گفته می‌شود.
قانون ساده برای جلوگیری از این مشکل این است که فقط و فقط رشته‌های HTML را با روش‌های امن مانند `setHTML()` تزریق کنید.

## مثال‌ها

### استفاده پایه

این مثال برخی از روش‌های استفاده از `setHTML()` برای پاک‌سازی و تزریق یک رشته HTML را نشان می‌دهد.

```js
// تعریف رشته HTML پاک‌سازی‌نشده
const unsanitizedString = "abc <script>alert(1)<" + "/script> def";
// دریافت عنصر هدف با شناسه "target"
const target = document.getElementById("target");

// setHTML() با پاک‌ساز پیش‌فرض
target.setHTML(unsanitizedString);

// تعریف Sanitizer سفارشی و استفاده در setHTML()
// این فقط عناصر div، p، button را مجاز می‌کند (script ناامن است و حذف می‌شود)
const sanitizer1 = new Sanitizer({
  elements: ["div", "p", "button", "script"],
});
target.setHTML(unsanitizedString, { sanitizer: sanitizer1 });

// تعریف SanitizerConfig سفارشی درون setHTML()
// این عناصر div، p، button، script و هر عنصر/ویژگی ناامن دیگر را حذف می‌کند
target.setHTML(unsanitizedString, {
  sanitizer: { removeElements: ["div", "p", "button", "script"] },
});
```

### مثال زنده `setHTML()`

این مثال یک نمایش «زنده» از این متد را زمانی که با پاک‌سازهای مختلف فراخوانی می‌شود ارائه می‌دهد.
کد دکمه‌هایی را تعریف می‌کند که با کلیک روی آنها می‌توان یک رشته HTML را با استفاده از پاک‌ساز پیش‌فرض و یک پاک‌ساز سفارشی پاک‌سازی و تزریق کرد.
رشته اصلی و HTML پاک‌سازی‌شده ثبت (log) می‌شوند تا بتوانید نتایج را در هر مورد بررسی کنید.

#### HTML

HTML شامل دو عنصر {{htmlelement("button")}} برای اعمال پاک‌سازهای مختلف، یک دکمه دیگر برای بازنشانی مثال، و یک عنصر {{htmlelement("div")}} برای تزریق رشته به داخل آن است.

```html
<button id="buttonDefault" type="button">Default</button>
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

ابتدا رشته‌ای را که باید پاک‌سازی شود تعریف می‌کنیم؛ این رشته برای همه موارد یکسان خواهد بود.
این رشته شامل عنصر {{htmlelement("script")}} و مدیریت‌کننده `onclick` است که هر دو ناامن در برابر XSS تلقی می‌شوند.
همچنین مدیریت‌کننده رویداد برای دکمه بازنشانی را تعریف می‌کنیم.

```js
// تعریف رشته HTML ناامن
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

سپس مدیریت‌کننده کلیک برای دکمه‌ای که HTML را با پاک‌ساز پیش‌فرض تنظیم می‌کند تعریف می‌کنیم.
این کار باید همه موجودیت‌های ناامن را قبل از درج رشته HTML حذف کند.
توجه داشته باشید که می‌توانید دقیقاً ببینید کدام عناصر در [مثال‌های سازنده `Sanitizer()`](/en-US/docs/Web/API/Sanitizer/Sanitizer#creating_the_default_sanitizer) حذف می‌شوند.

```js
const defaultSanitizerButton = document.querySelector("#buttonDefault");
defaultSanitizerButton.addEventListener("click", () => {
  // تنظیم محتوای عنصر با استفاده از پاک‌ساز پیش‌فرض
  target.setHTML(unsanitizedString);

  // ثبت HTML قبل از پاک‌سازی و پس از تزریق
  logElement.textContent =
    "Default sanitizer: remove script element, onclick attribute, data- attribute\n\n";
  log(`\nunsanitized: ${unsanitizedString}`);
  log(`\n\nsanitized: ${target.innerHTML}`);
});
```

مدیریت‌کننده کلیک بعدی، HTML هدف را با استفاده از یک پاک‌ساز سفارشی که فقط عناصر {{htmlelement("div")}}، {{htmlelement("p")}} و {{htmlelement("script")}} را مجاز می‌کند تنظیم می‌کند.
توجه داشته باشید که چون از متد `setHTML` استفاده می‌کنیم، `<script>` نیز حذف خواهد شد!

```js
const allowScriptButton = document.querySelector("#buttonAllowScript");
allowScriptButton.addEventListener("click", () => {
  // تنظیم محتوای عنصر با استفاده از یک پاک‌ساز سفارشی
  const sanitizer1 = new Sanitizer({
    elements: ["div", "p", "script"],
  });
  target.setHTML(unsanitizedString, { sanitizer: sanitizer1 });

  // ثبت HTML قبل از پاک‌سازی و پس از تزریق
  logElement.textContent =
    "Sanitizer: {elements: ['div', 'p', 'script']}\n Script removed even though allowed\n";
  log(`\nunsanitized: ${unsanitizedString}`);
  log(`\n\nsanitized: ${target.innerHTML}`);
});
```

```js hidden
} else {
  log("The HTML Sanitizer API is NOT supported in this browser.");
  // ارائه رفتار جایگزین یا بازگشتی
}
```

#### نتایج

روی دکمه‌های «Default» و «allowScript» کلیک کنید تا اثرات پاک‌ساز پیش‌فرض و سفارشی را به‌ترتیب مشاهده کنید.

توجه داشته باشید که چون از یک روش پاک‌سازی امن استفاده می‌کنیم، در هر دو حالت عنصر `<script>` و مدیریت‌کننده `onclick` حذف می‌شوند، حتی اگر به‌صراحت توسط پاک‌ساز مجاز شده باشند.
با این حال، در حالی که ویژگی `data-` با پاک‌ساز پیش‌فرض حذف می‌شود، زمانی که یک پاک‌ساز سفارشی ارسال می‌کنیم مجاز است.

{{EmbedLiveSample("setHTML() live example","100","450px")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.setHTMLUnsafe()")}}
- {{domxref("ShadowRoot.setHTML()")}} و {{domxref("ShadowRoot.setHTMLUnsafe()")}}
- {{domxref("Document.parseHTML_static", "Document.parseHTML()")}} و {{domxref("Document.parseHTMLUnsafe_static", "Document.parseHTMLUnsafe()")}}
- [HTML Sanitizer API](/en-US/docs/Web/API/HTML_Sanitizer_API)