---
title: "<li> HTML list item element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/li"
translated_by: "n8n + AI"
---

عنصر **`<li>`** در [HTML](/en-US/docs/Web/HTML) برای نمایش یک آیتم در فهرست استفاده می‌شود. این عنصر باید داخل یک عنصر والد قرار بگیرد: یک فهرست مرتب (`<ol>`)، یک فهرست نامرتب (`<ul>`)، یا یک منو (`<menu>`). در منوها و فهرست‌های نامرتب، آیتم‌ها معمولاً با نقطه (بولت) نمایش داده می‌شوند. در فهرست‌های مرتب، معمولاً با یک شمارندهٔ صعودی در سمت چپ نمایش داده می‌شوند؛ مثل عدد یا حرف.

```html interactive-example
<p>Apollo astronauts:</p>

<ul>
  <li>Neil Armstrong</li>
  <li>Alan Bean</li>
  <li>Peter Conrad</li>
  <li>Edgar Mitchell</li>
  <li>Alan Shepard</li>
</ul>
```

```css interactive-example
p,
li {
  font:
    1rem "Fira Sans",
    sans-serif;
}

p {
  font-weight: bold;
}
```

## ویژگی‌ها (Attributes)

این عنصر شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) می‌شود.

- `value`
  - : این attribute عدد صحیح، مقدار ترتیبی فعلی آیتم فهرست را مشخص می‌کند، همان‌طور که عنصر `<ol>` تعریف کرده است. تنها مقدار مجاز برای این attribute عدد است؛ حتی اگر فهرست با اعداد رومی یا حروف نمایش داده شود. آیتم‌هایی که بعد از این آیتم قرار می‌گیرند، شماره‌گذاری را از این مقدار ادامه می‌دهند. این attribute برای فهرست‌های نامرتب (`<ul>`) یا منوها (`<menu>`) معنایی ندارد.

- `type` (منسوخ‌شده)
  - : این attribute کاراکتری، نوع شماره‌گذاری را مشخص می‌کند:
    - `a`: حروف کوچک انگلیسی
    - `A`: حروف بزرگ انگلیسی
    - `i`: اعداد رومی کوچک
    - `I`: اعداد رومی بزرگ
    - `1`: اعداد

    این نوع، نوع شماره‌گذاری عنصر والد `<ol>` را (در صورت وجود) لغو می‌کند.

    > [!NOTE]
    > این attribute منسوخ شده است؛ به جای آن از ویژگی CSS `list-style-type` استفاده کنید.

## مثال‌ها

برای مثال‌های بیشتر، صفحات `<ol>` و `<ul>` را ببینید.

### فهرست مرتب

```html
<ol>
  <li>first item</li>
  <li>second item</li>
  <li>third item</li>
</ol>
```

#### نتیجه

### فهرست مرتب با مقدار سفارشی

```html
<ol type="I">
  <li value="3">third item</li>
  <li>fourth item</li>
  <li>fifth item</li>
</ol>
```

#### نتیجه

### فهرست نامرتب

```html
<ul>
  <li>first item</li>
  <li>second item</li>
  <li>third item</li>
</ul>
```

#### نتیجه

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories">رده‌های محتوا</a>
      </th>
      <td>هیچکدام.</td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">Flow content</a>.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>
        اگر بعد از آیتم لیست بلافاصله یک <code>&lt;li&gt;</code> دیگر بیاید، یا اگر در عنصر والد محتوای دیگری نباشد، تگ بسته شدن می‌تواند حذف شود.
      </td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
      <td>
        یک عنصر <code>&lt;ul&gt;</code>، <code>&lt;ol&gt;</code> یا <code>&lt;menu&gt;</code>. اگرچه استفاده معتبری نیست، <code>&lt;dir&gt;</code> منسوخ نیز می‌تواند والد باشد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td>
        <code><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listitem_role">listitem</a></code> زمانی که فرزند <code><a href="/en-US/docs/Web/HTML/Reference/Elements/ol">ol</a></code>، <code><a href="/en-US/docs/Web/HTML/Reference/Elements/ul">ul</a></code> یا <code><a href="/en-US/docs/Web/HTML/Reference/Elements/menu">menu</a></code> باشد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitem_role"><code>menuitem</code></a>،
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role"><code>menuitemcheckbox</code></a>،
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role"><code>menuitemradio</code></a>، <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/option_role"><code>option</code></a>،
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/none_role"><code>none</code></a>، <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role"><code>presentation</code></a>،
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radio_role"><code>radio</code></a>، <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/separator_role"><code>separator</code></a>،
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role"><code>tab</code></a>، <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treeitem_role"><code>treeitem</code></a>
      </td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td><code>HTMLLIElement</code></td>
    </tr>
  </tbody>
</table>

## مشخصات

## سازگاری با مرورگرها

## جستارهای وابسته

- سایر عناصر HTML مرتبط با لیست: `<ul>`، `<ol>`، `<menu>` و `<dir>` منسوخ
- ویژگی‌های CSS که می‌توانند برای استایل‌دهی `<li>` مفید باشند:
  - ویژگی `list-style` برای انتخاب نحوه نمایش شماره‌ها
  - [شمارنده‌های CSS (CSS counters)](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Counter_styles/Using_counters) برای مدیریت لیست‌های تو در تو
  - ویژگی `margin` برای کنترل فاصله از حاشیه آیتم لیست