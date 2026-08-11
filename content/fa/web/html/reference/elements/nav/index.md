---
title: "<nav> HTML navigation section element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/nav"
translated_by: "n8n + AI"
---

عنصر **`<nav>`** در [HTML](/en-US/docs/Web/HTML) نمایانگر بخشی از صفحه است که هدف آن ارائه لینک‌های ناوبری است؛ چه درون سند جاری و چه به اسناد دیگر. نمونه‌های رایج بخش‌های ناوبری شامل منوها، فهرست مطالب و فهرست‌ها هستند.

```html interactive-example
<nav class="crumbs">
  <ol>
    <li class="crumb"><a href="#">Bikes</a></li>
    <li class="crumb"><a href="#">BMX</a></li>
    <li class="crumb">Jump Bike 3000</li>
  </ol>
</nav>

<h1>Jump Bike 3000</h1>
<p>
  This BMX bike is a solid step into the pro world. It looks as legit as it
  rides and is built to polish your skills.
</p>
```

```css interactive-example
nav {
  border-bottom: 1px solid black;
}

.crumbs ol {
  list-style-type: none;
  padding-left: 0;
}

.crumb {
  display: inline-block;
}

.crumb a::after {
  display: inline-block;
  color: black;
  content: ">";
  font-size: 80%;
  font-weight: bold;
  padding: 0 3px;
}
```

## ویژگی‌ها

این عنصر فقط [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) را شامل می‌شود.

## نکات استفاده

- لزومی ندارد همهٔ لینک‌ها داخل یک عنصر `<nav>` قرار بگیرند. `<nav>` فقط برای بلوک اصلی لینک‌های ناوبری در نظر گرفته شده است؛ معمولاً عنصر `<footer>` فهرستی از لینک‌ها دارد که نیازی به قرار گرفتن در `<nav>` ندارند.
- یک سند می‌تواند چندین عنصر `<nav>` داشته باشد، مثلاً یکی برای ناوبری سایت و یکی برای ناوبری داخل صفحه. در این حالت می‌توان از [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) برای بهبود دسترس‌پذیری استفاده کرد؛ به [مثال](/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements#labeling_section_content) مراجعه کنید.
- عامل کاربر (user agent)، مانند صفحه‌خوان‌هایی که برای کاربران دارای معلولیت استفاده می‌شوند، می‌تواند از این عنصر استفاده کند تا تشخیص دهد آیا رندر اولیهٔ محتوای صرفاً ناوبری را حذف کند یا نه.

## مثال‌ها

در این مثال، یک بلوک `<nav>` برای نگه‌داری یک فهرست نامرتب ({{HTMLElement("ul")}}) از لینک‌ها استفاده شده است. با CSS مناسب می‌توان این بخش را به‌صورت نوار کناری، نوار ناوبری یا منوی کشویی نمایش داد.

```html live-sample___unordered-list
<nav class="menu">
  <ul>
    <li><a href="#">Home</a></li>
    <li><a href="#">About</a></li>
    <li><a href="#">Contact</a></li>
  </ul>
</nav>
```

معنای عنصر `nav` ارائه‌دادن لینک است. با این حال، یک عنصر `nav` لزوماً نباید شامل یک فهرست باشد؛ می‌تواند انواع دیگری از محتوا را هم در خود جای دهد. در این بلوک ناوبری، لینک‌ها به‌صورت متن روان ارائه شده‌اند:

```html live-sample___prose
<nav>
  <h2>Navigation</h2>
  <p>
    You are on my home page. To the north lies <a href="/blog">my blog</a>, from
    whence the sounds of battle can be heard. To the east you can see a large
    mountain, upon which many <a href="/school">school papers</a> are littered.
    Far up this mountain you can spy a little figure who appears to be me,
    desperately scribbling a <a href="/school/thesis">thesis</a>.
  </p>
  <p>
    To the west are several exits. One fun-looking exit is labeled
    <a href="https://games.example.com/">"games"</a>. Another more
    boring-looking exit is labeled <a href="https://isp.example.net/">ISP™</a>.
  </p>
  <p>
    To the south lies a dark and dank <a href="/about">contacts page</a>.
    Cobwebs cover its disused entrance, and at one point you see a rat run
    quickly out of the page.
  </p>
</nav>
```

## خلاصه فنی

| ویژگی | مقدار |
| --- | --- |
| [دسته‌بندی محتوا](/en-US/docs/Web/HTML/Guides/Content_categories) | [محتوای جریانی](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content)، [محتوای بخش‌بندی](/en-US/docs/Web/HTML/Guides/Content_categories#sectioning_content)، محتوای محسوس (palpable content). |
| محتوای مجاز | [محتوای جریانی](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content). |
| حذف تگ | هیچ‌کدام؛ هر دو تگ شروع و پایان الزامی هستند. |
| والدهای مجاز | هر عنصری که [محتوای جریانی](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content) را می‌پذیرد. |
| نقش ARIA ضمنی | [`navigation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/navigation_role) |
| نقش‌های ARIA مجاز | هیچ `role` مجاز نیست. |
| رابط DOM | `HTMLElement` |

## همچنین ببینید

- سایر عناصر مرتبط با بخش‌بندی: `<body>`، `<article>`، `<section>`، `<aside>`، `<h1>`، `<h2>`، `<h3>`، `<h4>`، `<h5>`، `<h6>`، `<hgroup>`، `<header>`، `<footer>`، `<address>`؛
- [بخش‌ها و ساختار کلی یک سند HTML](/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements).
- [ARIA: نقش navigation](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/navigation_role)