---
title: "tabindex HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex"
translated_by: "n8n + AI"
---

[ویژگی سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) **`tabindex`** به توسعه‌دهندگان امکان می‌دهد تا عناصر HTML را قابل فوکوس کنند، اجازه دهند یا مانع از فوکوس ترتیبی آن‌ها شوند (معمولاً با کلید <kbd>Tab</kbd>، از این رو نام آن) و ترتیب نسبی آن‌ها را در پیمایش ترتیبی فوکوس تعیین کنند.

```html interactive-example
<p>Click anywhere in this pane, then try tabbing through the elements.</p>

<label>First in tab order:<input type="text" /></label>

<div tabindex="0">Tabbable due to tabindex.</div>

<div>Not tabbable: no tabindex.</div>

<label>Third in tab order:<input type="text" /></label>
```

```css interactive-example
p {
  font-style: italic;
  font-weight: bold;
}

div,
label {
  display: block;
  letter-spacing: 0.5px;
  margin-bottom: 1rem;
}

div:focus {
  font-weight: bold;
}
```

این ویژگی یک عدد صحیح را به عنوان مقدار می‌پذیرد و نتیجه بسته به مقدار آن عدد متفاوت است:

> [!NOTE]
> اگر یک عنصر HTML رندر شود و ویژگی `tabindex` با هر مقدار صحیحی داشته باشد، می‌توان آن را با جاوااسکریپت (با فراخوانی متد [`focus()`](/en-US/docs/Web/API/HTMLElement/focus)) یا به‌صورت دیداری با کلیک ماوس فوکوس کرد. مقدار خاص `tabindex` تعیین می‌کند که آیا عنصر «قابل تب» (tabbable) است؛ یعنی آیا می‌توان از طریق پیمایش ترتیبی صفحه‌کلید، معمولاً با کلید <kbd>Tab</kbd>، به آن دسترسی داشت.

- یک _مقدار منفی_ (مقدار دقیق منفی مهم نیست، معمولاً `tabindex="-1"`) یعنی عنصر از طریق پیمایش ترتیبی صفحه‌کلید قابل دسترسی نیست.

  > [!NOTE]
  > `tabindex="-1"` ممکن است برای عناصری مفید باشد که نباید مستقیماً با کلید <kbd>Tab</kbd> به آن‌ها ناوبری شود، اما باید فوکوس صفحه‌کلید روی آن‌ها قرار گیرد. مثال‌ها شامل یک پنجرهٔ modal خارج از صفحه است که باید وقتی نمایش داده می‌شود فوکوس گیرد، یا پیام خطای ارسال فرم که باید بلافاصله هنگام ارسال فرم نامعتبر فوکوس شود.

- `tabindex="0"` یعنی عنصر باید در پیمایش ترتیبی صفحه‌کلید قابل فوکوس باشد، بعد از هر مقدار مثبت `tabindex`. ترتیب ناوبری فوکوس این عناصر با ترتیب آن‌ها در سند منبع تعیین می‌شود.

- یک _مقدار مثبت_ یعنی عنصر باید در پیمایش ترتیبی صفحه‌کلید قابل فوکوس باشد و ترتیب آن با مقدار عدد مشخص شود. یعنی `tabindex="4"` قبل از `tabindex="5"` و `tabindex="0"` فوکوس می‌شود، اما بعد از `tabindex="3"`. اگر چند عنصر مقدار مثبت یکسانی برای `tabindex` داشته باشند، ترتیب آن‌ها نسبت به یکدیگر بر اساس جایگاهشان در سند منبع است. حداکثر مقدار مجاز برای `tabindex` برابر ۳۲۷۶۷ است.

- اگر ویژگی `tabindex` بدون مقدار مشخص شده باشد، این user agent است که تعیین می‌کند آیا عنصر قابل فوکوس است یا خیر.

  > [!WARNING]
  > توصیه می‌شود فقط از `0` و `1-` به عنوان مقادیر `tabindex` استفاده کنید. از استفاده از مقادیر بزرگ‌تر از `0` برای `tabindex` و از ویژگی‌های CSS که می‌توانند ترتیب عناصر قابل فوکوس HTML را تغییر دهند ([ترتیب آیتم‌های فلکس](/en-US/docs/Web/CSS/Guides/Flexible_box_layout/Ordering_items)) خودداری کنید. این کار برای افرادی که برای ناوبری یا استفاده از فناوری کمکی به صفحه‌کلید وابسته‌اند، پیمایش و کار با محتوای صفحه را دشوار می‌کند. در عوض، سند را طوری بنویسید که عناصر در توالی منطقی قرار داشته باشند.

بعضی از عناصر HTML قابل‌فوکوس به‌طور پیش‌فرض توسط [عامل کاربری (user agent)](/en-US/docs/Glossary/User_agent) یک مقدار `tabindex` برابر با `0` دریافت می‌کنند. این عناصر عبارتند از: `<a>` یا `<area>` دارای ویژگی `href`، `<button>`، `<frame>` (منسوخ شده)، `<iframe>`، `<input>`، `<object>`، `<select>`، `<textarea>`، عنصر SVG `<a>` و `<summary>` که خلاصه‌ای برای `<details>` فراهم می‌کند. توسعه‌دهندگان نباید ویژگی `tabindex` را به این عناصر اضافه کنند مگر اینکه رفتار پیش‌فرض را تغییر دهد (مثلاً مقدار منفی باعث می‌شود عنصر از ترتیب ناوبری فوکوس حذف شود).

> [!WARNING]
> ویژگی `tabindex` نباید روی عنصر `<dialog>` استفاده شود.

## نکات دسترسی‌پذیری (Accessibility)

از به‌کارگیری `tabindex` همراه با [محتوای غیرتعاملی (non-interactive content)](/en-US/docs/Web/HTML/Guides/Content_categories#interactive_content) برای قابل‌فوکوس کردن چیزی که قرار است تعاملی باشد، خودداری کنید. مثلاً استفاده از `<div>` به جای `<button>` برای نمایش یک دکمه.

اجزای تعاملی که با عناصر غیرتعاملی ساخته می‌شوند در [درخت دسترسی‌پذیری (accessibility tree)](/en-US/docs/Learn_web_development/Core/Accessibility/What_is_accessibility#accessibility_apis) قرار نمی‌گیرند. این موضوع باعث می‌شود فناوری‌های کمکی نتوانند به این اجزا برسند و آن‌ها را کنترل کنند. محتوا باید به‌صورت معنایی با عناصر تعاملی (`<a>`، `<button>`، `<details>`، `<input>`، `<select>`، `<textarea>` و غیره) توصیف شود. این عناصر نقش‌ها و حالت‌های داخلی دارند که وضعیت را به دسترسی‌پذیری اعلام می‌کنند – در غیر این صورت باید با [ARIA](/en-US/docs/Web/Accessibility/ARIA) مدیریت می‌شد.

- [Using the tabindex attribute | Vispero](https://vispero.com/resources/using-the-tabindex-attribute/)

## مشخصات

## سازگاری با مرورگرها

## همچنین ببینید

- تمام [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes)
- `HTMLElement.tabIndex` که این attribute را منعکس می‌کند
- مشکلات دسترسی‌پذیری `tabindex`: [Don't Use Tabindex Greater than 0](https://adrianroselli.com/2014/11/dont-use-tabindex-greater-than-0.html) نوشتهٔ Adrian Roselli
- Reading order