---
title: Using the EditContext API
slug: Web/API/EditContext_API/Guide
page-type: guide
---

{{DefaultAPISidebar("EditContext API")}}

می‌توان از **[EditContext API](/en-US/docs/Web/API/EditContext_API)** برای ساخت ویرایشگرهای متنی پیشرفته در وب استفاده کرد که از تجربه‌های ورود متن پیچیده، مانند ترکیب نویسه‌ها با {{glossary("Input Method Editor")}} (IME)، انتخاب‌گر ایموجی، یا هر رابط کاربری مرتبط با ویرایشِ مختص یک پلتفرم پشتیبانی می‌کنند.

این مقاله مراحل لازم برای ساخت یک ویرایشگر متنی با استفاده از EditContext API را توضیح می‌دهد. در این راهنما، مراحل اصلی ساخت یک ویرایشگر کد HTML ساده را مرور خواهید کرد که هنگام تایپ، نحو کد را هایلایت می‌کند و از ترکیب IME پشتیبانی می‌کند.

## کد نهایی و دموی زنده

برای مشاهده کد نهایی، به [source code](https://github.com/mdn/dom-examples/tree/main/edit-context/html-editor) در گیت‌هاب مراجعه کنید. بهتر است هنگام مطالعه، کد منبع را باز نگه دارید، زیرا این آموزش فقط مهم‌ترین بخش‌های کد را نشان می‌دهد.

کد منبع در فایل‌های زیر سازماندهی شده است:

- [index.html](https://github.com/mdn/dom-examples/blob/main/edit-context/html-editor/index.html) شامل عنصر رابط کاربری ویرایشگر است و CSS و جاوااسکریپت لازم برای دمو را بارگیری می‌کند.
- [styles.css](https://github.com/mdn/dom-examples/blob/main/edit-context/html-editor/styles.css) شامل استایل‌های مربوط به رابط کاربری ویرایشگر است.
- [editor.js](https://github.com/mdn/dom-examples/blob/main/edit-context/html-editor/editor.js) شامل کد جاوااسکریپت است که رابط کاربری ویرایشگر را راه‌اندازی می‌کند، کد HTML را رندر می‌کند و ورودی کاربر را مدیریت می‌کند.
- [tokenizer.js](https://github.com/mdn/dom-examples/blob/main/edit-context/html-editor/tokenizer.js) شامل کد جاوااسکریپت است که کد HTML را به توکن‌های جداگانه تقسیم می‌کند، مانند تگ‌های آغازین، تگ‌های پایانی و گره‌های متنی.
- [converter.js](https://github.com/mdn/dom-examples/blob/main/edit-context/html-editor/converter.js) شامل کد جاوااسکریپت است که بین آفست‌های نویسه‌ای (character offsets) که EditContext API استفاده می‌کند و گره‌های DOM که مرورگر برای انتخاب متن استفاده می‌کند، تبدیل انجام می‌دهد.

برای استفاده از دموی زنده، [Edit Context API: HTML editor demo](https://mdn.github.io/dom-examples/edit-context/html-editor/) را در مرورگری باز کنید که از EditContext API پشتیبانی می‌کند.

## ایجاد رابط کاربری ویرایشگر

اولین قدم ایجاد رابط کاربری برای ویرایشگر است. ویرایشگر یک عنصر {{HTMLElement("div")}} با ویژگی [`spellcheck`](/en-US/docs/Web/HTML/Reference/Global_attributes/spellcheck) تنظیم‌شده روی `false` برای غیرفعال کردن بررسی املا است:

```html
<div id="html-editor" spellcheck="false"></div>
```

برای استایل‌دهی به عنصر ویرایشگر، از کد CSS زیر استفاده می‌شود. این کد باعث می‌شود ویرایشگر کل viewport را پر کند و وقتی محتوا بیش از حد جا شود، اسکرول شود. از ویژگی {{cssxref("white-space")}} نیز برای حفظ نویسه‌های فضای خالی در متن ورودی HTML استفاده می‌شود و ویژگی {{cssxref("tab-size")}} باعث می‌شود نویسه‌های تب به صورت دو فاصله نمایش داده شوند. در نهایت، رنگ‌های پیش‌فرض برای پس‌زمینه، متن و مکان‌نما تنظیم می‌شود:

```css
#html-editor {
  box-sizing: border-box;
  width: 100%;
  height: 100%;
  border-radius: 0.5rem;
  padding: 1rem;
  overflow: auto;
  white-space: pre;
  tab-size: 2;
  caret-color: red;
  background: black;
  line-height: 1.6;
  color: red;
}
```

## قابل ویرایش کردن ویرایشگر

در وب، برای قابل ویرایش کردن یک عنصر، در بیشتر مواقع از عنصر {{HTMLElement("input")}}، عنصر {{HTMLElement("textarea")}} یا ویژگی [`contenteditable`](/en-US/docs/Web/HTML/Reference/Global_attributes/contenteditable) استفاده می‌کنید.

با این حال، با EditContext API می‌توانید انواع دیگری از عناصر را بدون استفاده از ویژگی، قابل ویرایش کنید. برای مشاهده فهرست عناصری که می‌توان با EditContext API استفاده کرد، به بخش [Possible elements](/en-US/docs/Web/API/HTMLElement/editContext#possible_elements) در صفحه ویژگی `editContext` در مرجع HTMLElement مراجعه کنید.

برای قابل ویرایش کردن ویرایشگر، برنامه دمو یک نمونه {{domxref("EditContext")}} می‌سازد، متنی ابتدایی از HTML را به سازنده آن می‌دهد و سپس ویژگی {{domxref("HTMLElement.editContext", "editContext")}} عنصر ویرایشگر را روی آن نمونه `EditContext` تنظیم می‌کند:

```js
// Retrieve the editor element from the DOM.
const editorEl = document.getElementById("html-editor");

// Create the EditContext instance.
const editContext = new EditContext({
  text: "<html>\n  <body id=foo>\n    <h1 id='header'>Cool Title</h1>\n    <p class=\"wow\">hello<br/>How are you? test</p>\n  </body>\n</html>",
});

// Set the editor's editContext property value.
editorEl.editContext = editContext;
```

این خطوط کد عنصر ویرایشگر را قابل فوکوس می‌کنند. وارد کردن متن در عنصر، رویداد {{domxref("EditContext.textupdate_event", "textupdate")}} را روی نمونه `EditContext` فعال می‌کند.

## رندر کردن متن و انتخاب کاربر

برای رندر کردن کد HTML با هایلایت نحو در ویرایشگر هنگام ورود کاربر، برنامه دمو از تابعی به نام `render()` استفاده می‌کند که هنگام وارد شدن متن جدید، حذف شدن نویسه‌ها یا تغییر انتخاب، فراخوانی می‌شود.

### توکن‌سازی کد HTML

یکی از اولین کارهایی که تابع `render()` انجام می‌دهد، توکن‌سازی محتوای متنی HTML است. توکن‌سازی محتوای متنی HTML برای برجسته کردن نحو HTML لازم است و شامل خواندن رشته کد HTML و تعیین مکان شروع و پایان هر تگ آغازین، تگ پایانی، ویژگی، گره دیدگاه (comment) و گره متنی است.

برنامه دمو برای این کار از تابع `tokenizeHTML()` استفاده می‌کند که با حفظ یک ماشین حالت، رشته را نویسه به نویسه پیمایش می‌کند. می‌توانید کد منبع تابع `tokenizeHTML()` را در فایل [tokenizer.js](https://github.com/mdn/dom-examples/blob/main/edit-context/html-editor/tokenizer.js) در گیت‌هاب ببینید.

این تابع در فایل HTML برنامه دمو به شکل زیر ایمپورت می‌شود:

```js
import { tokenizeHTML } from "./tokenizer.js";
```

### رندر کردن متن

هر بار که تابع `render()` فراخوانی می‌شود — یعنی وقتی کاربر متن وارد می‌کند یا انتخاب تغییر می‌کند — تابع محتوای عنصر ویرایشگر را پاک می‌کند و سپس هر توکن را به عنوان یک عنصر HTML جداگانه رندر می‌کند:

```js
// Stores the list of HTML tokens.
let currentTokens = [];

function render(text, selectionStart, selectionEnd) {
  // Empty the editor. We're re-rendering everything.
  editorEl.textContent = "";

  // Tokenize the text.
  currentTokens = tokenizeHTML(text);

  for (const token of currentTokens) {
    // Render each token as a span element.
    const span = document.createElement("span");
    span.classList.add(`token-${token.type}`);
    span.textContent = token.value;

    // Attach the span to the editor element.
    editorEl.appendChild(span);

    // Store the new DOM node as a property of the token
    // in the currentTokens array. We will need it again
    // later in fromOffsetsToRenderedTokenNodes.
    token.node = span;
  }

  // Code to render the text selection is omitted for brevity.
  // See "Rendering the selection", below.
  // …
}
```

EditContext API به شما امکان می‌دهد نحوه رندر شدن متن ویرایش‌شده را کنترل کنید. تابع بالا متن را با استفاده از عناصر HTML رندر می‌کند، اما می‌توان آن را به هر شکل دیگری نیز رندر کرد، از جمله رندر کردن آن در یک عنصر `<canvas>`.

برنامه دمو تابع `render()` را در صورت نیاز اجرا می‌کند. این شامل یک بار هنگام شروع برنامه و سپس دوباره هنگام وارد شدن متن توسط کاربر، با گوش دادن به رویداد {{domxref("EditContext.textupdate_event", "textupdate")}} است:

```js
// Listen to the EditContext's textupdate event.
// This tells us when text input happens. We use it to re-render the view.
editContext.addEventListener("textupdate", (e) => {
  render(editContext.text, e.selectionStart, e.selectionEnd);
});

// Do the initial render.
render(editContext.text, editContext.selectionStart, editContext.selectionEnd);
```

### استایل‌دهی به توکن‌ها

همان‌طور که در مثال کد تابع `render()` دیدید، به هر توکن یک نام کلاس داده می‌شود که با نوع توکن مطابقت دارد. برنامه دمو از این نام کلاس برای استایل‌دهی به توکن‌ها با استفاده از CSS استفاده می‌کند، همان‌طور که در زیر نشان داده شده است:

```css
.token-openTagStart,
.token-openTagEnd,
.token-closeTagStart,
.token-closeTagEnd,
.token-selfClose {
  background: rgb(7 53 92);
  margin: 0 2px;
  color: white;
  border-radius: 0.25rem;
}

.token-equal {
  color: white;
}

.token-tagName {
  font-weight: bold;
  color: rgb(117 186 242);
}

.token-attributeName {
  color: rgb(207 81 198);
}

.token-attributeValue {
  font-style: italic;
  color: rgb(127 230 127);
  border: 1px dashed #8c8c8c;
  border-width: 1px 0;
}

.token-quoteStart,
.token-quoteEnd {
  font-weight: bold;
  color: rgb(127 230 127);
  border: 1px solid #8c8c8c;
  border-width: 1px 0 1px 1px;
  border-radius: 0.25rem 0 0 0.25rem;
}

.token-quoteEnd {
  border-width: 1px 1px 1px 0;
  border-radius: 0 0.25rem 0.25rem 0;
}

.token-text {
  color: #6a6a6a;
  padding: 0 0.25rem;
}
```

### رندر کردن انتخاب

با وجود اینکه برنامه دمو از یک عنصر `<div>` برای ویرایشگر استفاده می‌کند که از نمایش مکان‌نمای چشمک‌زن و برجسته کردن انتخاب‌های کاربر پشتیبانی می‌کند، EditContext API همچنان نیاز به رندر کردن انتخاب دارد. این به این دلیل است که EditContext API می‌تواند با انواع دیگری از عناصر که این رفتارها را پشتیبانی نمی‌کنند استفاده شود. رندر کردن انتخاب توسط خودمان همچنین کنترل بیشتری بر نحوه نمایش انتخاب به ما می‌دهد. در نهایت، چون تابع `render()` هر بار که اجرا می‌شود محتوای HTML عنصر ویرایشگر را پاک می‌کند، هر انتخابی که کاربر ممکن است انجام داده باشد در اجرای بعدی تابع `render()` از بین می‌رود.

برای رندر کردن انتخاب، برنامه دمو از روش {{domxref("Selection.setBaseAndExtent()")}} در انتهای تابع `render()` استفاده می‌کند. برای استفاده از روش `setBaseAndExtent()`، به یک جفت گره DOM و آفست‌های نویسه‌ای نیاز داریم که شروع و پایان انتخاب را نشان می‌دهند. با این حال، EditContext API وضعیت انتخاب فعلی را فقط به صورت یک جفت آفست شروع و پایان در کل بافر ویرایش نگه می‌دارد. کد برنامه دمو از تابع دیگری به نام `fromOffsetsToSelection()` استفاده می‌کند که این آفست‌های نویسه‌ای را به چهار مقدار تبدیل می‌کند:

- گره DOM که شامل شروع انتخاب است.
- عددی که موقعیت نویسه‌ای شروع انتخاب را درون گره شروع نشان می‌دهد.
- گره DOM که شامل پایان انتخاب است.
- عددی که موقعیت نویسه‌ای پایان انتخاب را درون گره پایانی نشان می‌دهد.

```js
function render(text, selectionStart, selectionEnd) {
  // …
  // The beginning of the render function is omitted for brevity.

  // Convert the start/end offsets to a DOM selection.
  const { anchorNode, anchorOffset, extentNode, extentOffset } =
    fromOffsetsToSelection(selectionStart, selectionEnd, editorEl);

  // Render the selection in the editor element.
  document
    .getSelection()
    .setBaseAndExtent(anchorNode, anchorOffset, extentNode, extentOffset);
}
```

می‌توانید کد تابع `fromOffsetsToSelection()` را در فایل [converter.js](https://github.com/mdn/dom-examples/blob/main/edit-context/html-editor/converter.js) ببینید.

## به‌روزرسانی مرزهای کنترل

EditContext API به ما انعطاف‌پذیری زیادی برای تعریف رابط کاربری ویرایشگر متنی خودمان می‌دهد. با این حال، این بدان معناست که باید برخی موارد را که معمولاً توسط مرورگر یا سیستم عامل (OS) مدیریت می‌شوند، خودمان مدیریت کنیم.

برای مثال، باید به سیستم عامل بگوییم که ناحیه متنی قابل ویرایش در کجای صفحه قرار دارد. به این ترتیب، سیستم عامل می‌تواند هر رابط کاربری ویرایش متنی را که کاربر ممکن است با آن متن را ترکیب کند، مانند پنجره ترکیب IME، به درستی مکان‌یابی کند.

برنامه دمو از روش {{domxref("EditContext.updateControlBounds()")}} استفاده می‌کند و یک شی {{domxref("DOMRect")}} که مرزهای ناحیه متنی قابل ویرایش را نشان می‌دهد، به آن می‌دهد. برنامه دمو این روش را هنگام راه‌اندازی ویرایشگر و دوباره هنگام تغییر اندازه پنجره فراخوانی می‌کند:

```js
function updateControlBounds() {
  // Get the DOMRect object for the editor element.
  const editorBounds = editorEl.getBoundingClientRect();

  // Update the control bounds of the EditContext instance.
  editContext.updateControlBounds(editorBounds);
}

// Call the updateControlBounds function when the editor is initialized,
updateControlBounds();

// And call it again when the window is resized.
window.addEventListener("resize", updateControlBounds);
```

## مدیریت کلیدهای Tab، Enter و سایر کلیدهای ویرایش متن

رویداد `textupdate` که در بخش قبلی استفاده شد، وقتی کاربر کلید <kbd>Tab</kbd> یا <kbd>Enter</kbd> را فشار می‌دهد فعال نمی‌شود، بنابراین باید این کلیدها را جداگانه مدیریت کنیم.

برای مدیریت این کلیدها، برنامه دمو یک شنونده رویداد برای رویداد {{domxref("Element.keydown_event", "keydown")}} روی عنصر ویرایشگر استفاده می‌کند و از این شنونده برای به‌روزرسانی محتوای متنی و انتخاب نمونه `EditContext` استفاده می‌کند، همان‌طور که در زیر نشان داده شده است:

```js
// Handle key presses that are not already handled by the EditContext.
editorEl.addEventListener("keydown", (e) => {
  // EditContext.updateText() expects the start and end offsets
  // to be in the correct order, but the current selection state
  // might be backwards.
  const start = Math.min(editContext.selectionStart, editContext.selectionEnd);
  const end = Math.max(editContext.selectionStart, editContext.selectionEnd);

  // Handling the Tab key.
  if (e.key === "Tab") {
    // Prevent the