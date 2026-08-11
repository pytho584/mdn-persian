---
title: "<tt> HTML teletype text element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/tt"
translated_by: "n8n + AI"
---

عنصر **`<tt>`** [HTML](/en-US/docs/Web/HTML) متنی درون‌خطی می‌سازد که با فونت monospace پیش‌فرض عامل کاربر (user agent) نمایش داده می‌شود. این عنصر برای رندر متنی طراحی شده بود که روی نمایشگرهای تک‌فاصله مثل تله‌تایپ، صفحه‌نمایش متنی یا چاپگر خطی دیده می‌شد.

اصطلاح‌های **non-proportional**، **monotype** و **monospace** به جای یکدیگر استفاده می‌شوند و معنای مشترکی دارند: آن‌ها فونت‌هایی را توصیف می‌کنند که همه نویسه‌هایشان عرض یکسانی دارند.

با این حال، این عنصر اکنون منسوخ (obsolete) شده است. برای متن درون‌خطی که باید با فونت monospace نمایش داده شود، از عناصر معنادارتر `<code>`، `<kbd>`، `<samp>` یا `<var>` استفاده کنید. برای محتوایی که باید به‌صورت یک بلوک جدا نمایش داده شود هم تگ `<pre>` مناسب است.

> [!NOTE]
> اگر هیچ‌کدام از عناصر معنایی برای کار شما مناسب نیستند (مثلاً اگر نیاز دارید محتوایی را با فونت غیرهم‌عرض نشان دهید)، بهتر است از عنصر `<span>` استفاده کنید و با CSS آن را استایل دهید. ویژگی `font-family` نقطه شروع خوبی است.

## ویژگی‌ها

این عنصر فقط شامل ویژگی‌های سراسری (Global Attributes) می‌شود.

## مثال‌ها

### مثال پایه

این مثال از `<tt>` برای نمایش متنی استفاده می‌کند که در یک برنامه ترمینال وارد شده و توسط آن خروجی گرفته شده است.

```html
<p>
  Enter the following at the telnet command prompt:
  <code>set localecho</code><br />

  The telnet client should display: <tt>Local Echo is on</tt>
</p>
```

#### نتیجه

### بازنویسی فونت پیش‌فرض

می‌توانید فونت پیش‌فرض مرورگر را با CSS بازنویسی کنید—البته فقط اگر مرورگر اجازه دهد؛ مرورگر الزامی به این کار ندارد:

#### CSS

```css
tt {
  font-family: "Lucida Console", "Menlo", "Monaco", "Courier New", monospace;
}
```

#### HTML

```html
<p>
  Enter the following at the telnet command prompt:
  <code>set localecho</code><br />

  The telnet client should display: <tt>Local Echo is on</tt>
</p>
```

#### نتیجه

## نکات استفاده

عنصر `<tt>` به‌طور پیش‌فرض با فونت غیرهم‌عرض (non-proportional) پیش‌فرض مرورگر رندر می‌شود. می‌توانید این رفتار را با تعریف یک قانون CSS و انتخابگر `tt` بازنویسی کنید؛ همان‌طور که در مثال [بازنویسی فونت پیش‌فرض](#overriding_the_default_font) در بالا دیدید.

> [!NOTE]
> تغییراتی که کاربر در تنظیم فونت monospace پیش‌فرض مرورگر اعمال کرده ممکن است بر CSS شما اولویت داشته باشد.

اگرچه این عنصر در HTML 4.01 به‌صورت رسمی منسوخ اعلام نشده بود، استفاده از آن به نفع عناصر معنایی و CSS توصیه نمی‌شد. عنصر `<tt>` در HTML 5 منسوخ است.

## خلاصه فنی

| ویژگی | مقدار |
|-------|-------|
| دسته‌بندی محتوا | [محتوای جریانی (flow content)](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content)، [محتوای عبارتی (phrasing content)](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content)، محتوای قابل لمس (palpable content) |
| محتوای مجاز | [محتوای عبارتی (phrasing content)](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) |
| حذف تگ | هیچ؛ هر دو تگ شروع و پایان الزامی هستند. |
| والدین مجاز | هر عنصری که [محتوای عبارتی (phrasing content)](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) را می‌پذیرد. |
| نقش‌های ARIA مجاز | هر نقشی |
| رابط DOM | `HTMLElement` |

## مشخصات

## سازگاری مرورگر

## همچنین ببینید

- عناصر معنایی `code`، `var`، `kbd` و `samp`
- عنصر `pre` برای نمایش بلوک‌های متنی از پیش قالب‌بندی‌شده