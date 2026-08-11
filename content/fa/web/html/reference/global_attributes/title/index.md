---
title: "title HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/title"
translated_by: "n8n + AI"
---

The **`title`** [global attribute](/en-US/docs/Web/HTML/Reference/Global_attributes) متنی را نگه می‌دارد که اطلاعات راهنمایی درباره عنصری که به آن تعلق دارد ارائه می‌دهد.

```html interactive-example
<p>
  Use the <code>title</code> attribute on an <code>iframe</code> to clearly
  identify the content of the <code>iframe</code> to screen readers.
</p>

<iframe
  title="Wikipedia page for the HTML language"
  src="https://en.m.wikipedia.org/wiki/HTML"></iframe>
<iframe
  title="Wikipedia page for the CSS language"
  src="https://en.m.wikipedia.org/wiki/CSS"></iframe>
```

```css interactive-example
iframe {
  height: 200px;
  margin-bottom: 24px;
  width: 100%;
}
```

کاربرد اصلی `title` برای برچسب‌گذاری عناصر {{HTMLElement("iframe")}} است تا فناوری‌های کمکی (assistive technology) بتوانند آن‌ها را تشخیص دهند.

همچنین می‌توان از `title` برای برچسب‌گذاری کنترل‌ها در [جدول‌های داده](/en-US/docs/Web/HTML/Reference/Elements/table) استفاده کرد.

وقتی `title` به [`<link rel="stylesheet">`](/en-US/docs/Web/HTML/Reference/Elements/link) اضافه شود، یک stylesheet جایگزین (alternate stylesheet) ایجاد می‌کند. هنگام تعریف stylesheet جایگزین با `<link rel="alternate">`، این attribute الزامی است و باید یک رشته غیرخالی باشد.

اگر `title` روی تگ شروع {{htmlelement('abbr')}} قرار بگیرد، باید شکل کامل آن مخفف یا سرواژه را نشان دهد. در صورت امکان، به جای استفاده از `title`، شکل کامل مخفف را در اولین استفاده به صورت متن ساده بنویسید و از `<abbr>` برای نشانه‌گذاری مخفف استفاده کنید. این کار باعث می‌شود همه کاربران بدانند مخفف به چه نام یا عبارتی اشاره دارد و در عین حال به user agentها هم راهنمایی می‌دهد که محتوا را چگونه اعلام کنند.

اگرچه می‌توان از `title` برای ارائه برچسب مرتبط برنامه‌نویسی‌شده (programmatically associated label) برای عنصر {{HTMLElement("input")}} استفاده کرد، این کار توصیه نمی‌شود. به جای آن از {{HTMLElement("label")}} استفاده کنید.

## عنوان‌های چندخطی (Multiline titles)

attribute `title` می‌تواند چند خط داشته باشد. هر کاراکتر `U+000A LINE FEED` (`LF`) نشان‌دهنده یک خط جدید است. باید دقت کنید، چون این یعنی مثال زیر در دو خط نمایش داده می‌شود:

### HTML

```html
<p>
  Newlines in <code>title</code> should be taken into account. This
  <span
    title="This is a
multiline title">
    example span
  </span>
  has a title attribute with a newline.
</p>
<hr />
<pre id="output"></pre>
```

### JavaScript

می‌توانیم attribute `title` را دریافت کرده و آن را در عنصر خالی `<pre>` به این صورت نمایش دهیم:

```js
const span = document.querySelector("span");
const output = document.querySelector("#output");
output.textContent = span.title;
```

### نتیجه

{{EmbedLiveSample('Multiline_titles')}}

## ارث‌بری attribute عنوان

اگر عنصری attribute `title` نداشته باشد، آن را از parent خودش به ارث می‌برد؛ و parent هم به نوبه خود ممکن است آن را از parent خودش به ارث ببرد و همین طور ادامه پیدا می‌کند.

اگر این attribute برابر با رشته خالی (`""`) باشد، یعنی titleهای ancestorها نامرتبط هستند و نباید در tooltip این عنصر استفاده شوند.

### HTML

```html
<div title="CoolTip">
  <p>Hovering here will show "CoolTip".</p>
  <p title="">Hovering here will show nothing.</p>
</div>
```

### نتیجه

{{EmbedLiveSample('Title_attribute_inheritance')}}

## نکات دسترس‌پذیری

استفاده از attribute `title` برای این گروه‌ها بسیار مشکل‌ساز است:

- افرادی که فقط از دستگاه‌های لمسی استفاده می‌کنند
- افرادی که با صفحه‌کلید کار می‌کنند
- افرادی که از فناوری‌های کمکی مثل screen reader یا ذره‌بین استفاده می‌کنند
- افرادی که اختلال در مهارت‌های حرکتی ظریف دارند
- افرادی که مشکلات شناختی دارند

این مشکل به‌دلیل پشتیبانی ناسازگار browser ها رخ می‌دهد و با تجزیه‌ی صفحه‌ی رندر شده توسط فناوری‌های کمکی (assistive technology) تشدید می‌شود. اگر افکت tooltip مد نظر است، بهتر است از [تکنیک دسترس‌پذیرتری](https://inclusive-components.design/tooltips-toggletips/) استفاده کنید که با روش‌های مرور ذکرشده قابل دسترسی باشد.

- [3.2.5.1. The title attribute | W3C HTML 5.2: 3. Semantics, structure, and APIs of HTML documents](https://html.spec.whatwg.org/multipage/dom.html#the-title-attribute)
- [Using the HTML title attribute – updated | Vispero](https://vispero.com/resources/using-the-html-title-attribute-updated/)
- [Tooltips & Toggletips - Inclusive Components](https://inclusive-components.design/tooltips-toggletips/)
- [The Trials and Tribulations of the Title Attribute - 24 Accessibility](https://www.24a11y.com/2017/the-trials-and-tribulations-of-the-title-attribute/)

## مشخصات

## سازگاری مرورگر

## همچنین ببینید

- همه‌ی [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes).
- `HTMLElement.title` که این attribute را بازتاب می‌دهد.