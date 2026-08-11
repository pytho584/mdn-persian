---
title: "<header> HTML header element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/header"
translated_by: "n8n + AI"
---

المان **`<header>`** [HTML](/en-US/docs/Web/HTML) محتوای مقدماتی را نمایش می‌دهد؛ معمولاً گروهی از ابزارهای مقدماتی یا ناوبری است. ممکن است شامل عناصر heading (مانند h1 تا h6) و همچنین لوگو، فرم جستجو، نام نویسنده و سایر المان‌ها باشد.

```html interactive-example
<header>
  <a class="logo" href="#">Cute Puppies Express!</a>
</header>

<article>
  <header>
    <h1>Beagles</h1>
    <time>08.12.2014</time>
  </header>
  <p>
    I love beagles <em>so</em> much! Like, really, a lot. They're adorable and
    their ears are so, so snugly soft!
  </p>
</article>
```

```css interactive-example
.logo {
  background: left / cover
    url("/shared-assets/images/examples/puppy-header.jpg");
  display: flex;
  height: 120px;
  align-items: center;
  justify-content: center;
  font:
    bold calc(1em + 2 * (100vw - 120px) / 100) "Dancing Script",
    fantasy;
  color: #ff0083;
  text-shadow: black 2px 2px 0.2rem;
}

header > h1 {
  margin-bottom: 0;
}

header > time {
  font: italic 0.7rem sans-serif;
}
```

## نکات استفاده

وقتی `<header>` درون [محتوای بخش‌بندی (sectioning content)](/en-US/docs/Web/HTML/Guides/Content_categories#sectioning_content)، `<main>` یا المانی با همان نقش ARIA ضمنی این عناصر قرار نگیرد، معنایی مشابه نقش نشانه‌گذاری (landmark) سراسری [`banner`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/banner_role) دارد. در این حالت یک هدر سراسری سایت تعریف می‌کند که معمولاً شامل لوگو، نام شرکت، قابلیت جستجو و احتمالاً ناوبری عمومی یا شعار است. این هدر معمولاً در بالای صفحه قرار می‌گیرد.

در غیر این صورت، وقتی درون عناصر یادشده تودرتو باشد، وضعیت landmark خود را از دست می‌دهد و به‌عنوان گروهی از ابزارهای مقدماتی یا ناوبری برای بخش اطراف عمل می‌کند. معمولاً شامل heading بخش اطراف (یک المان `h1` تا `h6`) و زیرheading اختیاری است، اما این **الزامی** نیست.

### استفادهٔ تاریخی

المان `<header>` در ابتدای HTML برای heading‌ها وجود داشت. در [اولین وب‌سایت](https://info.cern.ch/) دیده می‌شود. در مقطعی heading‌ها به [`<h1>` تا `<h6>`](/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements) تبدیل شدند تا `<header>` برای نقش دیگری آزاد شود.

## ویژگی‌ها

این المان فقط شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

## دسترسی‌پذیری

المان `<header>` یک نقش نشانه‌گذاری (landmark) [`banner`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/banner_role) تعریف می‌کند وقتی زمینهٔ آن المان `<body>` باشد.

وقتی درون `<article>`، `<main>`، `<section>`، `<nav>`، `<aside>` یا المانی با همان نقش ARIA ضمنی این عناصر قرار گیرد، المان `<header>` به‌جای آن نقش [`generic`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/generic_role) می‌گیرد و دیگر یک نشانه‌گذاری (landmark) محسوب نمی‌شود. در این حالت نمی‌توان آن را با [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) یا [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) برچسب‌گذاری کرد.

## مثال‌ها

### هدر صفحه

```html
<header>
  <h1>Main Page Title</h1>
  <img src="mdn-logo-sm.png" alt="MDN logo" />
</header>
```

#### نتیجه

### هدر مقاله

## مثال

در مثال زیر، عنصر `<header>` به‌عنوان سربرگ یک مقاله استفاده شده است:

```html
<article>
  <header>
    <h2>The Planet Earth</h2>
    <p>
      Posted on Wednesday, <time datetime="2017-10-04">4 October 2017</time> by
      Jane Smith
    </p>
  </header>
  <p>
    We live on a planet that's blue and green, with so many things still unseen.
  </p>
  <p><a href="https://example.com/the-planet-earth/">Continue reading…</a></p>
</article>
```

## خلاصه فنی

| ویژگی | مقدار |
| --- | --- |
| دسته‌بندی محتوا | [محتوای جریانی (Flow content)](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content)، [محتوای قابل لمس (palpable content)](/en-US/docs/Web/HTML/Guides/Content_categories#palpable_content) |
| محتوای مجاز | محتوای جریانی، اما بدون هیچ عنصر `<header>` یا `<footer>` در داخل (descendant) |
| حذف تگ | هیچ. هر دو تگ شروع و پایان اجباری هستند. |
| والدین مجاز | هر عنصری که محتوای جریانی را بپذیرد. توجه داشته باشید که یک عنصر `<header>` نمی‌تواند درون عنصر `<address>`، `<footer>` یا یک `<header>` دیگر باشد. |
| نقش ARIA ضمنی | [banner](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/banner_role)؛ یا اگر درون یکی از عناصر [article](/en-US/docs/Web/HTML/Reference/Elements/article)، [aside](/en-US/docs/Web/HTML/Reference/Elements/aside)، [main](/en-US/docs/Web/HTML/Reference/Elements/main)، [nav](/en-US/docs/Web/HTML/Reference/Elements/nav) یا [section](/en-US/docs/Web/HTML/Reference/Elements/section) باشد، یا داخل عنصری با نقش [article](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/article_role)، [complementary](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/complementary_role)، [main](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/main_role)، [navigation](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/navigation_role) یا [region](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/region_role) باشد، نقش [generic](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/generic_role) خواهد بود. |
| نقش‌های ARIA مجاز | [group](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role)، [presentation](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role) یا [none](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/none_role) |
| رابط DOM | [HTMLElement](/en-US/docs/Web/API/HTMLElement) |

- سایر عناصر مرتبط با بخش: `<body>`، `<nav>`، `<article>`، `<aside>`، `<h1>` تا `<h6>`، `<footer>`، `<section>`، `<address>`.