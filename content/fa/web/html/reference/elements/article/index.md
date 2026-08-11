---
title: "<article> HTML article contents element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/article"
translated_by: "n8n + AI"
---

عنصر **`<article>`** (مقاله) در HTML یک بخش خودکفا از یک سند، صفحه، برنامه یا سایت را نشان می‌دهد که به‌صورت مستقل قابل توزیع یا استفاده مجدد است (مثلاً در syndication). نمونه‌ها عبارت‌اند از: یک پست فروم، مقالهٔ مجله یا روزنامه، یک ورودی بلاگ، کارت محصول، دیدگاه ارسال‌شده توسط کاربر، یک ویجت یا ابزار تعاملی، یا هر محتوای مستقلی دیگر.

```html interactive-example
<article class="forecast">
  <h1>Weather forecast for Seattle</h1>
  <article class="day-forecast">
    <h2>03 March 2018</h2>
    <p>Rain.</p>
  </article>
  <article class="day-forecast">
    <h2>04 March 2018</h2>
    <p>Periods of rain.</p>
  </article>
  <article class="day-forecast">
    <h2>05 March 2018</h2>
    <p>Heavy rain.</p>
  </article>
</article>
```

```css interactive-example
.forecast {
  margin: 0;
  padding: 0.3rem;
  background-color: #eeeeee;
}

.forecast > h1,
.day-forecast {
  margin: 0.5rem;
  padding: 0.3rem;
  font-size: 1.2rem;
}

.day-forecast {
  background: right/contain content-box border-box no-repeat
    url("/shared-assets/images/examples/rain.svg") white;
}

.day-forecast > h2,
.day-forecast > p {
  margin: 0.2rem;
  font-size: 1rem;
}
```

یک سند می‌تواند چندین `<article>` داشته باشد. مثلاً در یک بلاگ که هر پست به‌صورت پشت‌سرهم نمایش داده می‌شود، هر پست درون یک `<article>` قرار می‌گیرد (احتمالاً با یک یا چند `<section>` درون خود).

## ویژگی‌ها

این عنصر فقط شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) می‌شود.

## نکات استفاده

- هر `<article>` باید مشخص شود؛ معمولاً با قرار دادن یک heading (عنصر [`<h1>` تا `<h6>`](/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements)) به عنوان فرزند مستقیم `<article>`.
- وقتی یک `<article>` تو در تو (nested) می‌شود، عنصر داخلی یک مقالهٔ مرتبط با عنصر بیرونی را نشان می‌دهد. برای مثال، دیدگاه‌های یک پست بلاگ می‌توانند به صورت `<article>`هایی درون `<article>` اصلی بلاگ قرار گیرند.
- اطلاعات نویسندهٔ یک `<article>` را می‌توان با عنصر {{HTMLElement("address")}} ارائه داد، اما این اطلاعات برای `<article>`های تو در تو اعمال نمی‌شود.
- تاریخ و زمان انتشار یک `<article>` را می‌توان با استفاده از ویژگی [`datetime`](/en-US/docs/Web/HTML/Reference/Elements/time#datetime) در عنصر {{HTMLElement("time")}} مشخص کرد.

## مثال‌ها

```html
<article class="film_review">
  <h2>Jurassic Park</h2>
  <section class="main_review">
    <h3>Review</h3>
    <p>Dinos were great!</p>
  </section>
  <section class="user_reviews">
    <h3>User reviews</h3>
    <article class="user_review">
      <h4>Too scary!</h4>
      <p>Way too scary for me.</p>
      <footer>
        <p>
          Posted on
          <time datetime="2015-05-16 19:00">May 16</time>
          by Lisa.
        </p>
      </footer>
    </article>
    <article class="user_review">
      <h4>Love the dinos!</h4>
      <p>I agree, dinos are my favorite.</p>
      <footer>
        <p>
          Posted on
          <time datetime="2015-05-17 19:00">May 17</time>
          by Tom.
        </p>
      </footer>
    </article>
  </section>
  <footer>
    <p>
      Posted on
      <time datetime="2015-05-15 19:00">May 15</time>
      by Staff.
    </p>
  </footer>
</article>
```

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories">دسته‌های محتوا</a>
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">Flow content</a>,
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#sectioning_content">sectioning content</a>,
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#palpable_content">palpable content</a>
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">Flow content</a>.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>هیچ، هر دو تگ شروع و پایان اجباری هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
      <td>هر عنصری که <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">Flow content</a> می‌پذیرد. توجه داشته باشید که یک عنصر <code>&#x3C;article></code> نباید از نوادگان عنصر <code>&#x3C;address></code> باشد.</td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td><code><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/article_role">article</a></code></td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/application_role"><code>application</code></a>,
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/document_role"><code>document</code></a>,
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/feed_role"><code>feed</code></a>,
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/main_role"><code>main</code></a>,
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/none_role"><code>none</code></a>,
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role"><code>presentation</code></a>,
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/region_role"><code>region</code></a>
      </td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td><code>HTMLElement</code></td>
    </tr>
  </tbody>
</table>

## همچنین ببینید

- دیگر عناصر مرتبط با بخش‌بندی: `<body>`, `<nav>`, `<section>`, `<aside>`, `<h1>`, `<h2>`, `<h3>`, `<h4>`, `<h5>`, `<h6>`, `<hgroup>`, `<header>`, `<footer>`, `<address>`
- [استفاده از بخش‌های HTML و ساختار کلی](/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements)