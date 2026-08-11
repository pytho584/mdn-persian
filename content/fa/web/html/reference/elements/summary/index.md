---
title: "<summary> HTML disclosure summary element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/summary"
translated_by: "n8n + AI"
---

عنصر `<summary>` یک عنصر HTML است که برای نمایش عنوان، شرح یا برچسب جعبه بازشونده (disclosure box) عنصر `<details>` به کار می‌رود. با کلیک روی `<summary>`، وضعیت عنصر والد `<details>` بین باز و بسته تغییر می‌کند.

## ویژگی‌ها

این عنصر تنها شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

## نکات استفاده

محتوای عنصر `<summary>` می‌تواند هر نوع محتوای عنوان، متن ساده یا HTML باشد که درون یک پاراگراف قابل استفاده است.

یک عنصر `<summary>` تنها می‌تواند به عنوان اولین فرزند یک عنصر `<details>` استفاده شود. وقتی کاربر روی خلاصه کلیک می‌کند، عنصر والد `<details>` باز یا بسته می‌شود و یک رویداد `toggle` به عنصر `<details>` ارسال می‌گردد که می‌توانید از آن برای اطلاع از تغییر وضعیت استفاده کنید.

محتوای عنصر `<details>` به عنوان توضیح قابل دسترسی (accessible description) برای `<summary>` عمل می‌کند.

### برچسب پیش‌فرض

اگر اولین فرزند یک عنصر `<details>` یک عنصر `<summary>` نباشد، مرورگر (user agent) از یک رشته پیش‌فرض (معمولاً «جزئیات») به عنوان برچسب جعبه بازشونده استفاده می‌کند.

### استایل پیش‌فرض

طبق مشخصات HTML، استایل پیش‌فرض برای عناصر `<summary` شامل `display: list-item` است. این امکان را می‌دهد که آیکون پیش‌فرض (معمولاً یک مثلث) که در کنار برچسب نمایش داده می‌شود، تغییر داده یا حذف شود. همچنین می‌توانید استایل را به `display: block` تغییر دهید تا مثلث بازشونده حذف شود.

برای جزئیات بیشتر به بخش [سازگاری مرورگر](#browser_compatibility) مراجعه کنید، زیرا همه مرورگرها از تمام قابلیت‌های این عنصر پشتیبانی نمی‌کنند.

در مرورگرهای مبتنی بر WebKit مانند Safari، می‌توانید نمایش آیکون را با استفاده از شبه‌عنصر غیراستاندارد CSS `::-webkit-details-marker` کنترل کنید. برای حذف مثلث بازشونده از `summary::-webkit-details-marker { display: none }` استفاده کنید.

## مثال‌ها

در زیر چند مثال از استفاده از `<summary>` آورده شده است. مثال‌های بیشتر را در مستندات عنصر {{HTMLElement("details")}} می‌توانید پیدا کنید.

### مثال پایه

یک مثال ساده از استفاده از `<summary>` درون یک عنصر {{HTMLElement("details")}}:

```html
<details open>
  <summary>خلاصه</summary>
  <ol>
    <li>وجه نقد موجود: ۵۰۰٫۰۰ دلار</li>
    <li>فاکتور جاری: ۷۵٫۳۰ دلار</li>
    <li>تاریخ سررسید: ۵/۶/۱۹</li>
  </ol>
</details>
```

### استفاده از عنوان‌ها درون خلاصه

می‌توانید از عناصر عنوان درون `<summary>` استفاده کنید:

```html
<details open>
  <summary><h4>خلاصه</h4></summary>
  <ol>
    <li>وجه نقد موجود: ۵۰۰٫۰۰ دلار</li>
    <li>فاکتور جاری: ۷۵٫۳۰ دلار</li>
    <li>تاریخ سررسید: ۵/۶/۱۹</li>
  </ol>
</details>
```

این مثال ممکن است مشکلات فاصله‌گذاری داشته باشد که با CSS قابل رفع است.

> [!WARNING]
> نقش (role) اختصاص‌داده‌شده به عنصر `<summary>` در مرورگرهای مختلف متفاوت است. برخی مرورگرها هنوز نقش پیش‌فرض [`button`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role) را به آن می‌دهند، که باعث می‌شود تمام نقش‌های فرزندانش حذف شود. این ناهماهنگی می‌تواند برای کاربران فناوری‌های کمکی مثل صفحه‌خوان‌ها مشکل ایجاد کند (مثلاً `<h4>` در مثال قبلی نقش خود را از دست می‌دهد و به‌عنوان heading در نظر گرفته نمی‌شود). بهتر است پیاده‌سازی `<summary>` خود را در چند پلتفرم تست کنید تا از پشتیبانی سازگار دسترسی (accessibility) مطمئن شوید.

### HTML درون summaries

این مثال به عنصر `<summary>` معنای بیشتری می‌دهد تا برچسب به‌عنوان مهم نشان داده شود:

```html
<details open>
  <summary><strong>Overview</strong></summary>
  <ol>
    <li>Cash on hand: $500.00</li>
    <li>Current invoice: $75.30</li>
    <li>Due date: 5/6/19</li>
  </ol>
</details>
```

#### نتیجه

### تغییر آیکون summary

نشانگر (marker) عنصر `<summary>` (مثلث بازشونده) را می‌توان با CSS سفارشی‌سازی کرد. با استفاده از شبه‌عنصر {{cssxref("::marker")}} می‌توان به نشانگر دسترسی داشت. این شبه‌عنصر ویژگی کوتاه‌نویس {{cssxref("list-style")}} و ویژگی‌های جزء آن مثل {{cssxref("list-style-type")}} را می‌پذیرد. با این کار می‌توان مثلث را به یک تصویر (معمولاً با {{cssxref("list-style-image")}}) یا یک رشته (شامل اموجی) تبدیل کرد. در این مثال، محتوای یک disclose widget را جایگزین می‌کنیم و آیکون دیگری را با تنظیم `list-style: none` و افزودن یک آیکون سفارشی از طریق محتوای تولیدشده (generated content) حذف می‌کنیم.

#### CSS

در اولین disclose widget، `::marker` را استایل می‌دهیم و {{cssxref("content")}} را بر اساس ویژگی `[open]` عنصر `<details>` تغییر می‌دهیم. در widget دوم، نشانگر را با ویژگی‌های `list-style` حذف می‌کنیم و سپس با شبه‌عنصر {{cssxref("::after")}} یک محتوای تولیدشده با استایل دلخواه اضافه می‌کنیم. همچنین استایل‌های `::-webkit-details-marker` را برای مرورگر Safari قرار می‌دهیم. انتخابگر شبه‌عنصر مخصوص مرورگر درون {{cssxref(":is()")}} قرار می‌گیرد تا در صورت نامعتبر بودن، کل لیست انتخابگر باطل نشود.

```css
details {
  font-size: 1rem;
  font-family: "Open Sans", "Calibri", sans-serif;
  border: solid;
  padding: 2px 6px;
  margin-bottom: 1em;
}

details:first-of-type summary::marker,
:is(::-webkit-details-marker) {
  content: "+ ";
  font-family: monospace;
  color: red;
  font-weight: bold;
}

details[open]:first-of-type summary::marker {
  content: "− ";
}

details:last-of-type summary {
  list-style: none;
  &::after {
    content: "+";
    color: white;
    background-color: darkgreen;
    border-radius: 1em;
    font-weight: bold;
    padding: 0 5px;
    margin-inline-start: 5px;
  }
  [open] &::after {
    content: "−";
  }
}
details:last-of-type summary::-webkit-details-marker {
  display: none;
}
```

CSS از [attribute selector](/en-US/docs/Web/CSS/Reference/Selectors/Attribute_selectors) `[open]` استفاده می‌کند که فقط زمانی اعمال می‌شود که ویژگی `open` وجود داشته باشد (یعنی وقتی `<details>` باز است). شبه‌کلاس‌های {{cssxref(":first-of-type")}} و {{cssxref(":last-of-type")}} اولین و آخرین عنصر هم‌نوع را هدف قرار می‌دهند. شبه‌عنصر prefixed با `-webkit-` را درون {{cssxref(":is()")}} قرار دادیم چون این شبه‌کلاس یک [forgiving selector list](/en-US/docs/Web/CSS/Reference/Selectors/Selector_list#forgiving_selector_list) می‌پذیرد و در صورت نامعتبر بودن شبه‌عنصر در یک مرورگر، کل بلوک انتخابگر باطل نمی‌شود. همچنین از [تودرتوی CSS (nesting)](/en-US/docs/Web/CSS/Reference/Selectors/Nesting_selector) استفاده شده است. برای اطلاعات بیشتر به [ماژول انتخابگرهای CSS](/en-US/docs/Web/CSS/Guides/Selectors) مراجعه کنید.

#### HTML

```html-nolint
<h1>Quotes from Helen Keller</h1>
```

<details>
  <summary>On women's rights</summary>
  <p>
    <q>We have prayed, we have coaxed, we have begged, for the vote, with the
      hope that men, out of chivalry, would bestow equal rights upon women and
      take them into partnership in the affairs of the state. We hoped that
      their common sense would triumph over prejudices and stupidity. We thought
      their boasted sense of justice would overcome the errors that so often
      fetter the human spirit; but we have always gone away empty-handed. We
      shall beg no more.</q>
  </p>
</details>

<details>
  <summary>On optimism</summary>
  <p>
    <q>Optimism is the faith that leads to achievement; nothing can be done
      without hope.</q>
  </p>
</details>

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">دسته‌بندی محتوا</th>
      <td>هیچ</td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>Phrasing content، به‌صورت اختیاری همراه با Heading content</td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>هیچ; هر دو تگ شروع و پایان اجباری هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
      <td>عنصر <code>&lt;details&gt;</code></td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td>نقش متناظری وجود ندارد</td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>هیچ <code>role</code> مجاز نیست</td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td>HTMLElement</td>
    </tr>
  </tbody>
</table>

## مشخصات

## سازگاری با مرورگرها

## همچنین ببینید

- `<details>`