---
title: "<h1>–<h6> HTML section heading elements"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements"
translated_by: "n8n + AI"
---

المان‌های **`<h1>`** تا **`<h6>`** شش سطح از سربرگ‌های بخش‌بندی (section heading) را در HTML مشخص می‌کنند. `<h1>` بالاترین سطح و `<h6>` پایین‌ترین سطح است. به‌طور پیش‌فرض، همهٔ المان‌های heading یک جعبهٔ block-level در چیدمان ایجاد می‌کنند که از خط جدید شروع شده و تمام عرض موجود در بلوک والد را می‌گیرد.

```html interactive-example
<h1>Beetles</h1>
<h2>External morphology</h2>
<h3>Head</h3>
<h4>Mouthparts</h4>
<h3>Thorax</h3>
<h4>Prothorax</h4>
<h4>Pterothorax</h4>
```

```css interactive-example
h1,
h2,
h3,
h4 {
  margin: 0.1rem 0;
}

h1 {
  font-size: 2rem;
}

h2 {
  font-size: 1.5rem;
  padding-left: 20px;
}

h3 {
  font-size: 1.2rem;
  padding-left: 40px;
}

h4 {
  font-size: 1rem;
  font-style: italic;
  padding-left: 60px;
}
```

## ویژگی‌ها

این المان‌ها فقط [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) را می‌پذیرند.

## نکات استفاده

- عامل کاربر (user agent) می‌تواند از اطلاعات heading برای ساخت خودکار فهرست مطالب یک سند استفاده کند.
- از المان‌های heading برای تغییر اندازهٔ متن استفاده نکنید؛ به جای آن از ویژگی {{glossary("CSS")}} {{cssxref("font-size")}} استفاده کنید.
- سطح heading را نپرید: همیشه از `<h1>` شروع کنید، سپس `<h2>` و به همین ترتیب.

### از به‌کارگیری چند `<h1>` در یک صفحه خودداری کنید

اگرچه استاندارد HTML استفاده از چند المان `<h1>` در یک صفحه را مجاز می‌داند (تا زمانی که [تودرتو (nested)](#nesting) نباشند)، این کار بهترین روش محسوب نمی‌شود. معمولاً یک صفحه باید تنها یک المان `<h1>` داشته باشد که محتوای صفحه را توصیف کند (مشابه المان [`<title>`](/en-US/docs/Web/HTML/Reference/Elements/title) سند).

> **توجه:**
> تودرتوسازی چند المان `<h1>` درون [المان‌های بخش‌بندی (sectioning elements)](/en-US/docs/Web/HTML/Reference/Elements#content_sectioning) در نسخه‌های قدیمی‌تر استاندارد HTML مجاز بود. اما این کار هرگز به‌عنوان یک روش خوب در نظر گرفته نشد و اکنون غیراستاندارد (non-conforming) محسوب می‌شود. بیشتر بخوانید در [There Is No Document Outline Algorithm](https://adrianroselli.com/2016/08/there-is-no-document-outline-algorithm.html).

توصیه می‌شود در هر صفحه فقط یک `<h1>` داشته باشید و [heading‌ها را](#nesting) بدون پرش از سطح‌ها تودرتو کنید.

### تعیین اندازهٔ قلم ثابت برای `<h1>`

پیش از می ۲۰۲۵، [استاندارد HTML](https://html.spec.whatwg.org/multipage/rendering.html#sections-and-headings) مشخص کرده بود که المان‌های `<h1>` درون `<section>`، `<article>`، `<aside>` یا `<nav>` باید مانند `<h2>` رندر شوند (با {{cssxref("font-size")}} کوچک‌تر و {{cssxref("margin-block")}} تنظیم‌شده)، یا اگر یک سطح دیگر تودرتو بودند مانند `<h3>` و الی آخر. این سبک پیش‌فرض وابسته به بافت (context-dependent) اکنون [حذف شده است](https://github.com/whatwg/html/issues/7867).

برای اطمینان از رندر یکسان `<h1>` در مرورگرهایی که سبک پیش‌فرض قدیمی وابسته به بافت را پیاده‌سازی کرده‌اند، از قانون سبک زیر استفاده کنید:

```css
h1 {
  margin-block: 0.67em;
  font-size: 2em;
}
```

همچنین می‌توانید برای جلوگیری از بازنویسی سایر قوانین سبکی که `<h1>` را هدف قرار می‌دهند، از {{cssxref(":where()")}} استفاده کنید که اختصاصی بودن (specificity) صفر دارد:

```css
:where(h1) {
  margin-block: 0.67em;
  font-size: 2em;
}
```

## دسترس‌پذیری (Accessibility)

### پیمایش

یک تکنیک رایج برای کاربران نرم‌افزارهای صفحه‌خوان (screen readers) این است که برای تعیین محتوای صفحه، سریعاً از یک heading به heading بعدی می‌پرند. به همین دلیل مهم است که یک یا چند سطح heading را پرش نکنید. این کار ممکن است باعث سردرگمی شود، زیرا فردی که از این طریق پیمایش می‌کند ممکن است فکر کند heading گمشده کجاست.

**این کار را انجام ندهید:**

```html example-bad
<h1>Heading level 1</h1>
<h3>Heading level 3</h3>
<h4>Heading level 4</h4>
```

**بهتر است این را بنویسید:**

```html example-good
<h1>Heading level 1</h1>
<h2>Heading level 2</h2>
<h3>Heading level 3</h3>
```

#### تودرتو کردن (Nesting)

برای نشان دادن سازمان‌دهی محتوای صفحه می‌توان عنوان‌ها را به‌صورت زیربخش تودرتو کرد. اکثر صفحه‌خوان‌ها همچنین می‌توانند فهرست مرتبی از همهٔ عنوان‌های صفحه بسازند؛ این قابلیت به کاربر کمک می‌کند تا سلسله‌مراتب محتوا را سریع تشخیص دهد و به بخش‌های مختلف برود.

ساختار صفحهٔ زیر را در نظر بگیرید:

```html
<h1>Beetles</h1>

<h2>Etymology</h2>

<h2>Distribution and Diversity</h2>

<h2>Evolution</h2>
<h3>Late Paleozoic</h3>
<h3>Jurassic</h3>
<h3>Cretaceous</h3>
<h3>Cenozoic</h3>

<h2>External Morphology</h2>
<h3>Head</h3>
<h4>Mouthparts</h4>
<h3>Thorax</h3>
<h4>Prothorax</h4>
<h4>Pterothorax</h4>
<h3>Legs</h3>
<h3>Wings</h3>
<h3>Abdomen</h3>
```

صفحه‌خوان‌ها فهرستی مانند زیر تولید می‌کنند:

1. `h1` سوسک‌ها
   1. `h2` ریشه‌شناسی
   2. `h2` پراکندگی و تنوع
   3. `h2` تکامل
      1. `h3` پالئوزوئیک پسین
      2. `h3` ژوراسیک
      3. `h3` کرتاسه
      4. `h3` سنوزوئیک

   4. `h2` ریخت‌شناسی بیرونی
      1. `h3` سر
         1. `h4` قطعات دهان

      2. `h3` سینه
         1. `h4` پیش‌سینه
         2. `h4` پس‌سینه

      3. `h3` پاها
      4. `h3` بال‌ها
      5. `h3` شکم

وقتی عنوان‌ها تودرتو هستند، هنگام بستن یک زیربخش ممکن است سطح‌های عنوان «پرش» شوند.

- [Headings • Page Structure • WAI Web Accessibility Tutorials](https://www.w3.org/WAI/tutorials/page-structure/headings/)
- [MDN Understanding WCAG, Guideline 1.3 explanations](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Perceivable#guideline_1.3_—_create_content_that_can_be_presented_in_different_ways)
- [Understanding Success Criterion 1.3.1 | W3C Understanding WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/content-structure-separation-programmatic.html)
- [MDN Understanding WCAG, Guideline 2.4 explanations](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Operable#guideline_2.4_—_navigable_provide_ways_to_help_users_navigate_find_content_and_determine_where_they_are)
- [Understanding Success Criterion 2.4.1 | W3C Understanding WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-skip.html)
- [Understanding Success Criterion 2.4.6 | W3C Understanding WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-descriptive.html)
- [Understanding Success Criterion 2.4.10 | W3C Understanding WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/navigation-mechanisms-headings.html)

### برچسب‌گذاری محتوای بخش

یکی دیگر از روش‌های متداول ناوبری برای کاربران نرم‌افزارهای صفحه‌خوان، تولید فهرستی از [sectioning content](/en-US/docs/Web/HTML/Reference/Elements#content_sectioning) و استفاده از آن برای تعیین چیدمان صفحه است.

می‌توان محتوای sectioning را با ترکیبی از attributeهای [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) و [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) برچسب‌گذاری کرد؛ برچسب باید به‌طور خلاصه هدف بخش را توصیف کند. این روش زمانی مفید است که بیش از یک المان sectioning در صفحه وجود داشته باشد.

#### نمونه‌هایی از محتوای sectioning

```html
<header>
  <nav aria-labelledby="primary-navigation">
    <h2 id="primary-navigation">Primary navigation</h2>
    <!-- navigation items -->
  </nav>
</header>

<!-- page content -->

<footer>
  <nav aria-labelledby="footer-navigation">
    <h2 id="footer-navigation">Footer navigation</h2>
    <!-- navigation items -->
  </nav>
</footer>
```

در این مثال، فناوری صفحه‌خوان (screen reader) اعلام می‌کند که دو بخش `<nav>` وجود دارد؛ یکی «Primary navigation» و دیگری «Footer navigation». اگر برچسب‌ها (labels) مشخص نشده باشند، کاربرِ نرم‌افزار صفحه‌خوان ممکن است لازم باشد محتوای تک‌تک المان‌های `nav` را بررسی کند تا هدف هرکدام را بفهمد.

- [Using the aria-labelledby attribute](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby)
- [Labeling Regions • Page Structure • W3C WAI Web Accessibility Tutorials](https://www.w3.org/WAI/tutorials/page-structure/labels/#using-aria-labelledby)

## مثال‌ها

### همهٔ عنوان‌ها

کد زیر همهٔ سطح‌های heading را در حال استفاده نشان می‌دهد.

```html
<h1>Heading level 1</h1>
<h2>Heading level 2</h2>
<h3>Heading level 3</h3>
<h4>Heading level 4</h4>
<h5>Heading level 5</h5>
<h6>Heading level 6</h6>
```

### صفحهٔ مثال

کد زیر چند heading را همراه با بخشی از محتوا در زیر آن‌ها نشان می‌دهد.

```html
<h1>Heading elements</h1>
<h2>Summary</h2>
<p>Some text here…</p>

<h2>Examples</h2>
<h3>Example 1</h3>
<p>Some text here…</p>

<h3>Example 2</h3>
<p>Some text here…</p>

<h2>See also</h2>
<p>Some text here…</p>
```

## خلاصهٔ فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories"
          >Content categories</a
        >
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >Flow content</a
        >, heading content, palpable content.
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >Phrasing content</a
        >.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>هیچ‌کدام؛ هم تگ شروع و هم تگ پایان اجباری هستند.</td>
    </tr>
    <tr>
      <th scope="row">المان‌های والد مجاز</th>
      <td>
        هر المانی که
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >flow content</a
        > را بپذیرد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td>
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/heading_role"
          >heading</a
        >
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role"><code>tab</code></a>, <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role"><code>presentation</code></a> یا
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/none_role"><code>none</code></a>
      </td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td><code>HTMLHeadingElement</code></td>
    </tr>
  </tbody>
</table>

## مشخصات

## سازگاری مرورگر

## همچنین ببینید

- `<p>`
- `<div>`
- `<section>`