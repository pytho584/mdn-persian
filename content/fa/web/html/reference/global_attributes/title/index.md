---
title: "title HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/title"
translated_by: "n8n + AI"
---

# ویژگی سراسری `title`

ویژگی سراسری **`title`** حاوی متنی است که اطلاعات تکمیلی درباره‌ی عنصر مربوطه ارائه می‌دهد. این متن معمولاً به‌صورت یک tooltip هنگام قرار گرفتن نشانگر روی عنصر نمایش داده می‌شود.

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

کاربرد اصلی ویژگی `title` برچسب‌گذاری عناصر `<iframe>` برای فناوری‌های کمکی است.

ویژگی `title` همچنین می‌تواند برای برچسب‌گذاری کنترلها در [جدول‌های داده](/en-US/docs/Web/HTML/Reference/Elements/table) استفاده شود.

اگر `title` به [`<link rel="stylesheet">`](/en-US/docs/Web/HTML/Reference/Elements/link) اضافه شود، یک استایل‌شیت جایگزین ایجاد می‌کند. هنگام تعریف استایل‌شیت جایگزین با `<link rel="alternate">`، این ویژگی الزامی است و باید به یک رشته‌ی غیرخالی تنظیم شود.

اگر روی تگ آغازین `<abbr>` قرار گیرد، `title` باید نمایش کامل مخفف یا سرواژه باشد. به‌جای استفاده از `title`، در صورت امکان، در نخستین استفاده، مخفف را به‌صورت متن ساده کامل بنویسید و از `<abbr>` برای نشانه‌گذاری مخفف استفاده کنید. این کار باعث می‌شود همه‌ی کاربران بدانند مخفف یا سرواژه به کدام نام یا عبارت اشاره دارد و در عین حال به عامل‌های کاربر (user agents) راهنمایی می‌دهد که محتوا را چگونه اعلام کنند.

در حالی که می‌توان از `title` برای ارائه‌ی یک برچسب مرتبط به‌صورت برنامه‌نویسی برای عنصر `<input>` استفاده کرد، این کار روش خوبی نیست. به‌جای آن از `<label>` استفاده کنید.

## چندخطی بودن title

ویژگی `title` می‌تواند شامل چند خط باشد. هر کاراکتر `U+000A LINE FEED` (`LF`) نشان‌دهنده‌ی یک خط جدید است. باید احتیاط کرد، چون این یعنی در مثال زیر محتوا در دو خط رندر می‌شود:

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

می‌توانیم ویژگی `title` را پرس‌وجو کنیم و آن را در عنصر `<pre>` خالی به‌صورت زیر نمایش دهیم:

```js
const span = document.querySelector("span");
const output = document.querySelector("#output");
output.textContent = span.title;
```

## ارث‌بری ویژگی title

اگر عنصری ویژگی `title` نداشته باشد، آن را از والد خود به ارث می‌برد؛ والد نیز ممکن است از والد خود به ارث ببرد و همین‌طور ادامه پیدا کند.

اگر این ویژگی برابر رشته‌ی خالی تنظیم شود، یعنی `title`های اجداد مرتبط نیستند و نباید در tooltip این عنصر استفاده شوند.

### HTML

```html
<div title="CoolTip">
  <p>Hovering here will show "CoolTip".</p>
  <p title="">Hovering here will show nothing.</p>
</div>
```

این مشکل به دلیل پشتیبانی نامنظم مرورگرها و همچنین تحلیل اضافی‌ای است که فناوری کمکی روی صفحهٔ رندر شده توسط مرورگر انجام می‌دهد. اگر به اثری شبیه tooltip نیاز دارید، بهتر است از [use a more accessible technique](https://inclusive-components.design/tooltips-toggletips/) استفاده کنید که با روش‌های مرور بالا قابل دسترسی است.

- [3.2.5.1. The title attribute | W3C HTML 5.2: 3. Semantics, structure, and APIs of HTML documents](https://html.spec.whatwg.org/multipage/dom.html#the-title-attribute)
- [Using the HTML title attribute – updated | Vispero](https://vispero.com/resources/using-the-html-title-attribute-updated/)
- [Tooltips & Toggletips - Inclusive Components](https://inclusive-components.design/tooltips-toggletips/)
- [The Trials and Tribulations of the Title Attribute - 24 Accessibility](https://www.24a11y.com/2017/the-trials-and-tribulations-of-the-title-attribute/)

## همچنین ببینید

- همهٔ [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes).