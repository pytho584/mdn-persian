---
title: "HighlightRegistry: highlightsFromPoint() method"
short-title: highlightsFromPoint()
slug: Web/API/HighlightRegistry/highlightsFromPoint
page-type: web-api-instance-method
browser-compat: api.HighlightRegistry.highlightsFromPoint
---

{{APIRef("CSS Custom Highlight API")}}

متد **`highlightsFromPoint()`** از رابط {{domxref("HighlightRegistry")}} آرایه‌ای از اشیا را برمی‌گرداند که هایلایت‌های سفارشی اعمال‌شده در نقطه‌ای خاص در viewport را نشان می‌دهند.

## نحو

```js-nolint
highlightsFromPoint(x, y)
highlightsFromPoint(x, y, options)
```

### پارامترها

- `x`
  - : مختصات x نقطه‌ای در viewport که اطلاعات هایلایت سفارشی از آن برگردانده می‌شود.
- `y`
  - : مختصات y نقطه‌ای در viewport که اطلاعات هایلایت سفارشی از آن برگردانده می‌شود.
- `options` {{optional_inline}}
  - : شیءای حاوی گزینه‌ها که می‌تواند شامل موارد زیر باشد:
    - `shadowRoots`
      - : آرایه‌ای از اشیاء {{domxref("ShadowRoot")}}. هایلایت‌های سفارشی که در نقطه مشخص‌شده داخل shadow rootهای موجود در این آرایه قرار دارند، علاوه بر آن‌هایی که در light DOM هستند، در مقدار بازگشتی نیز گنجانده می‌شوند. به‌طور پیش‌فرض، هایلایت‌های داخل shadow rootها بازگردانده نمی‌شوند.

### مقدار بازگشتی

آرایه‌ای از اشیا که نمایانگر هایلایت‌های سفارشی اعمال‌شده در نقطه viewport مشخص‌شده توسط پارامترهای `x` و `y` هستند.

هر شی شامل ویژگی‌های زیر است:

- `highlight`
  - : یک شی {{domxref("Highlight")}} که نمایانگر هایلایت سفارشی اعمال‌شده است.
- `ranges`
  - : آرایه‌ای از اشیاء {{domxref("AbstractRange")}} که نمایانگر محدوده‌هایی هستند که هایلایت سفارشی روی آن‌ها اعمال شده است.

اگر هیچ هایلایت سفارشی در نقطه مشخص‌شده اعمال نشده باشد، یا نقطه مشخص‌شده خارج از viewport باشد، متد یک آرایه خالی برمی‌گرداند.

## مثال‌ها

### بازیابی هایلایت‌های سفارشی اعمال‌شده در موقعیت اشاره‌گر ماوس

این مثال نشان می‌دهد که چگونه می‌توان از متد `highlightsFromPoint()` برای بازگرداندن محتوای تمام هایلایت‌های سفارشی که در مختصات اشاره‌گر ماوس هنگام دوبار کلیک کاربر قرار دارند، استفاده کرد.

در این مثال، روی یک پاراگراف متن می‌توان چند هایلایت سفارشی ایجاد کرد و هایلایت‌ها می‌توانند با هم همپوشانی داشته باشند. وقتی کاربر پس از انتخاب متنی، کلید <kbd>h</kbd> را فشار می‌دهد، یک {{domxref("Highlight")}} جدید نام‌گذاری و ثبت می‌شود. این مثال در هر زمان از حداکثر سه هایلایت سفارشی پشتیبانی می‌کند. وقتی کاربر در ناحیه هایلایت‌شده دوبار کلیک می‌کند، محتوای تمام هایلایت‌های موجود در آن نقطه (در صورت وجود) در ناحیه خروجی نمایش داده می‌شود.

#### HTML

این مارک‌آپ شامل یک عنصر {{htmlelement("p")}} و یک عنصر {{htmlelement("section")}} است. `<section>` به‌عنوان ناحیه خروجی عمل می‌کند که محتوای هایلایت‌های دوبار کلیک‌شده در آن نمایش داده می‌شود.

```html live-sample___highlights-from-point-example
<h1>highlightsFromPoint() demo</h1>
<h2>Highlightable content</h2>
<p class="highlightable-text">
  Select a portion of text, and then press the "h" key. The selected text gets a
  custom highlight, colored yellow, red, or blue, in that order. After the third
  highlight, each new one replaces the oldest, cycling through the colors in the
  same order. Next, double-click any highlighted text. The highlighted text will
  appear in the output. If multiple highlights overlap a section, you'll see
  multiple text sections in the output.
</p>
<h2>Text in double-clicked highlights</h2>
<section></section>
```

#### CSS

در CSS، استایل سه هایلایت سفارشی به نام‌های `highlight1`، `highlight2` و `highlight3` را تعریف می‌کنیم. هر هایلایت سفارشی را با استفاده از شبه‌عنصر {{cssxref("::highlight()")}} هدف قرار می‌دهیم و پس‌زمینه آن‌ها را به‌ترتیب زرد، قرمز و آبی نیمه‌شفاف می‌کنیم. در جایی که هایلایت‌ها همپوشانی دارند، پس‌زمینه‌های نیمه‌شفاف ترکیب می‌شوند و یک رنگ ترکیبی ظاهر می‌شود.

```css live-sample___highlights-from-point-example
::highlight(highlight1) {
  background-color: rgb(255 255 0 / 0.75);
}

::highlight(highlight2) {
  background-color: rgb(255 0 0 / 0.3);
}

::highlight(highlight3) {
  background-color: rgb(0 0 255 / 0.3);
}
```

```css hidden live-sample___highlights-from-point-example
* {
  box-sizing: border-box;
}

body {
  background-color: white;
  color: #333333;
  font:
    1em / 1.4 "Helvetica Neue",
    "Helvetica",
    "Arial",
    sans-serif;
  padding: 1em;
  max-width: 800px;
  margin: 0 auto;
}

section {
  display: flex;
  gap: 10px;
}

.highlightable-text,
article {
  padding: 10px;
  background-color: #eeeeee;
  border: 2px solid #dddddd;
  border-radius: 5px;
}
```

#### JavaScript

این مثال دو بخش مجزای عملکردی دارد. ابتدا هنگام فشاردادن کلید <kbd>h</kbd> توسط کاربر پس از انتخاب متن، امکان ایجاد هایلایت‌های سفارشی را فراهم می‌کنیم. سپس هنگام دوبار کلیک کاربر روی یک یا چند هایلایت سفارشی، امکان نوشتن محتوای هایلایت‌شده در صفحه را فراهم می‌کنیم.

##### ایجاد و اعمال هایلایت‌های سفارشی

برای ایجاد هایلایت‌های سفارشی، ابتدا ارجاع‌هایی به عنصر `<p>` و گره متنی داخل آن می‌گیریم. همچنین متغیری به نام `highlightCount` ایجاد می‌کنیم که در ابتدا `1` است و برای مشخص کردن اینکه کدام هایلایت سفارشی بعداً اعمال شود استفاده می‌شود.

وقتی کاربر پس از انتخاب متنی، کلید <kbd>h</kbd> را فشار می‌دهد، باید یک شی {{domxref("Highlight")}} جدید ثبت و نام‌گذاری کنیم، به‌طوری‌که در هر زمان حداکثر سه هایلایت سفارشی پشتیبانی شود. برای این کار، یک کنترل‌کننده رویداد [`keydown`](/en-US/docs/Web/API/Element/keydown_event) تعریف می‌کنیم که در صورت فشرده‌شدن کلید <kbd>h</kbd> روی صفحه‌کلید، یک هایلایت سفارشی روی هر متن انتخاب‌شده اعمال کند. در داخل آن، ابتدا متن انتخاب‌شده را با استفاده از {{domxref("Window.getSelection()")}} می‌گیریم و آن را با {{domxref("Selection.getRangeAt()")}} به یک {{domxref("Range")}} تبدیل می‌کنیم.

بررسی می‌کنیم که [`startContainer`](/en-US/docs/Web/API/AbstractRange/startContainer) و [`endContainer`](/en-US/docs/Web/API/AbstractRange/endContainer) شیء `selectedRange` هر دو با `textNode` پاراگراف برابر باشند تا مطمئن شویم هیچ هایلایت بین‌کانتینری (cross-container) مجاز نیست. اگر این شرط برقرار بود، نام سفارشی `highlightName` موردنظرم‌ان را با استفاده از `highlight${highlightCount++}` روی `selectedRange` تنظیم می‌کنیم. از آنجا که `highlightCount` را افزایش می‌دهیم اما فقط سه هایلایت داریم، وقتی شمارنده به `4` می‌رسد، آن را به `1` برمی‌گردانیم و عملاً به ترتیب تنظیم، از میان هایلایت‌های موجود می‌چرخیم.

در نهایت، برای کنترل‌کننده رویداد `keydown`، یک شیء جدید `highlight` با استفاده از سازنده {{domxref("Highlight.Highlight", "Highlight()")}} می‌سازیم و `selectedRange` را که قبلاً ایجاد کرده‌ایم به آن می‌دهیم. سپس هایلایت سفارشی انتخابی که در `highlightName` به آن ارجاع داده شده است را با استفاده از متد {{domxref("HighlightRegistry.set()")}} روی `highlight` اعمال می‌کنیم.

```js live-sample___highlights-from-point-example
window.addEventListener("keydown", (event) => {
  if (event.key === "h") {
    const selection = window.getSelection();
    const selectedRange = selection.getRangeAt(0);
    if (
      selectedRange.startContainer === textNode &&
      selectedRange.endContainer === textNode
    ) {
      const highlightName = `highlight${highlightCount++}`;
      if (highlightCount === 4) {
        highlightCount = 1;
      }
      const highlight = new Highlight(selectedRange);
      CSS.highlights.set(highlightName, highlight);
    }
  }
});
```

##### بازگرداندن هایلایت‌های سفارشی از یک نقطه

حالا که می‌توانیم هایلایت‌های سفارشی ایجاد و اعمال کنیم، می‌توانیم از متد `highlightsFromPoint()` برای بازگرداندن هایلایت‌های سفارشی اعمال‌شده در یک نقطه خاص استفاده کنیم.

یک ارجاع به عنصر `<section>` می‌گیریم، سپس یک تابع کنترل‌کننده رویداد [`dblclick`](/en-US/docs/Web/API/Element/dblclick_event) تعریف می‌کنیم تا هنگام فعال‌شدن رویداد، خروجی متن هایلایت‌شده در موقعیت مکان‌نمای ماوس را مدیریت کند. در داخل کنترل‌کننده، مختصات فعلی ماوس را به یک فراخوانی `highlightsFromPoint()` می‌دهیم، محتویات عنصر `<section>` را پاک می‌کنیم، سپس در یک حلقه، هر هایلایت در آرایه `highlights` را پیمایش می‌کنیم.

برای هر `highlight`، اولین محدوده را از آرایه [`ranges`](#ranges) می‌گیریم (در این مورد، در هر هایلایت فقط یک محدوده وجود دارد)، سپس رشته دقیق هایلایت‌شده را با استفاده از {{domxref("Range.toString()")}} به‌دست می‌آوریم و آن را داخل یک عنصر `<article>` به `innerHTML` عنصر `<section>` اضافه می‌کنیم.

```js live-sample___highlights-from-point-example
const section = document.querySelector("section");

pElem.addEventListener("dblclick", (event) => {
  const highlights = CSS.highlights.highlightsFromPoint(
    event.clientX,
    event.clientY,
  );

  section.innerHTML = "";
  for (highlight of highlights) {
    const range = highlight.ranges[0];
    const textSelection = range.toString();
    section.innerHTML += `<article>${textSelection}</article>`;
  }
});
```

#### نتیجه

{{EmbedLiveSample("Examples", "100%", "600")}}

برای ایجاد یک هایلایت، پس از انتخاب متنی، کلید <kbd>h</kbd> را فشار دهید. می‌توانید حداکثر سه هایلایت ایجاد کنید. روی هایلایت‌هایی که ایجاد کرده‌اید، ترجیحاً در جایی که همپوشانی دارند، دوبار کلیک کنید تا محتوای هایلایت‌های کلیک‌شده در صفحه نوشته شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("css_custom_highlight_api", "CSS Custom Highlight API", "", "nocode")}}
- ماژول [CSS custom highlight API](/en-US/docs/Web/CSS/Guides/Custom_highlight_API)