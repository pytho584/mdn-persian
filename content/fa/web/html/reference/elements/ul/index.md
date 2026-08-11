---
title: "<ul> HTML unordered list element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/ul"
translated_by: "n8n + AI"
---

المان `<ul>` در HTML یک لیست نامرتب از آیتم‌ها را نشان می‌دهد که معمولاً به صورت یک لیست با گلوله (bullet) نمایش داده می‌شود.

```html interactive-example
<ul>
  <li>Milk</li>
  <li>
    Cheese
    <ul>
      <li>Blue cheese</li>
      <li>Feta</li>
    </ul>
  </li>
</ul>
```

```css interactive-example
li {
  list-style-type: circle;
}

li li {
  list-style-type: square;
}
```

## ویژگی‌ها (Attributes)

این المان شامل [ویژگی‌های global](/en-US/docs/Web/HTML/Reference/Global_attributes) می‌شود.

- `compact` {{Deprecated_inline}}
  - : این ویژگی Boolean نشان می‌دهد که لیست باید به صورت فشرده نمایش داده شود. نحوه تفسیر این ویژگی به مرورگر بستگی دارد. به جای آن از [CSS](/en-US/docs/Web/CSS) استفاده کنید: برای ایجاد اثری مشابه با ویژگی `compact`، می‌توانید از ویژگی CSS {{cssxref("line-height")}} با مقدار `80%` استفاده کنید.
- `type` {{Deprecated_inline}}
  - : این ویژگی سبک گلوله (bullet) لیست را تعیین می‌کند. مقادیر تعریف‌شده در HTML 3.2 و نسخه انتقالی HTML 4.0/4.01 عبارتند از:
    - `circle`
    - `disc`
    - `square`
    - یک نوع گلوله چهارم به نام `triangle` در رابط WebTV تعریف شده است، اما همه مرورگرها از آن پشتیبانی نمی‌کنند.

    اگر این ویژگی وجود نداشته باشد و هیچ ویژگی CSS {{ cssxref("list-style-type") }} روی المان اعمال نشود، مرورگر با توجه به سطح تودرتویی (nesting level) لیست، نوع گلوله را انتخاب می‌کند.

    > [!WARNING]
    > از این ویژگی استفاده نکنید؛ منسوخ شده است. به جای آن از ویژگی CSS {{ cssxref("list-style-type") }} استفاده کنید.

## نکات استفاده

- المان `<ul>` برای گروه‌بندی مجموعه‌ای از آیتم‌هایی استفاده می‌شود که ترتیب عددی ندارند و ترتیب آنها در لیست بی‌معناست. معمولاً آیتم‌های لیست نامرتب با یک گلوله نمایش داده می‌شوند که می‌تواند اشکال مختلفی مانند نقطه، دایره یا مربع داشته باشد. سبک گلوله در توضیحات HTML صفحه تعریف نمی‌شود، بلکه در CSS مرتبط با آن با استفاده از ویژگی {{ cssxref("list-style-type") }} تعیین می‌گردد.
- المان‌های `<ul>` و {{HTMLElement("ol")}} را می‌توان به هر تعداد که لازم است تودرتو (nest) کرد. همچنین می‌توان لیست‌های تودرتو را بدون محدودیت بین `<ol>` و `<ul>` جابه‌جا کرد.
- المان‌های {{ HTMLElement("ol") }} و `<ul>` هر دو یک لیست از آیتم‌ها را نشان می‌دهند. تفاوت در این است که در المان {{ HTMLElement("ol") }} ترتیب اهمیت دارد. برای تصمیم‌گیری درباره استفاده از کدام یک، ترتیب آیتم‌های لیست را تغییر دهید؛ اگر معنا تغییر کرد، از {{ HTMLElement("ol") }} استفاده کنید، در غیر این صورت می‌توانید از `<ul>` استفاده کنید.

## مثال‌ها

### مثال پایه

```html
<ul>
  <li>first item</li>
  <li>second item</li>
  <li>third item</li>
</ul>
```

### لیست تودرتو

```html
<ul>
  <li>first item</li>
  <li>
    second item
    <!-- توجه: تگ بسته‌ شدن </li> اینجا قرار نگرفته است! -->
    <ul>
      <li>second item first subitem</li>
      <li>
        second item second subitem
        <!-- برای دومین لیست تودرتو هم همینطور -->
        <ul>
          <li>second item second subitem first sub-subitem</li>
          <li>second item second subitem second sub-subitem</li>
          <li>second item second subitem third sub-subitem</li>
        </ul>
      </li>
      <!-- تگ بسته‌ شدن </li> برای آیتمی که شامل سومین لیست تودرتو است -->
      <li>second item third subitem</li>
    </ul>
    <!-- اینجا تگ بسته‌ شدن </li> قرار دارد -->
  </li>
  <li>third item</li>
</ul>
```

### لیست مرتب درون لیست نامرتب

```html
<ul>
  <li>first item</li>
  <li>
    second item
    <!-- در اینجا یک لیست مرتب (ordered) درون لیست نامرتب داریم -->
    <ol>
      <li>second item first subitem</li>
      <li>second item second subitem</li>
      <li>second item third subitem</li>
    </ol>
  </li>
  <li>third item</li>
</ul>
```

```markdown
```html
<ul>
  <li>first item</li>
  <li>
    second item
    <!-- Look, the closing </li> tag is not placed here! -->
    <ol>
      <li>second item first subitem</li>
      <li>second item second subitem</li>
      <li>second item third subitem</li>
    </ol>
    <!-- Here is the closing </li> tag -->
  </li>
  <li>third item</li>
</ul>
```

#### نتیجه

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories"
          >دسته‌های محتوا</a
        >
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >Flow content</a
        >، و اگر فرزندان المان <code>&#x3C;ul></code> حداقل شامل یک
        المان <code>&#x3C;li></code> باشند،
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#palpable_content"
          >palpable content</a
        >.
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>
        صفر یا چند المان <code>&#x3C;li></code>،
        <code>&#x3C;script></code> و
        <code>&#x3C;template></code>.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>هیچ‌کدام؛ هم تگ شروع و هم تگ پایان اجباری هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
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
        <code
          ><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/list_role"
            >list</a
          ></code
        >
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/directory_role"><code>directory</code></a>, <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role"><code>group</code></a>,
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listbox_role"><code>listbox</code></a>, <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menu_role"><code>menu</code></a>,
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menubar_role"><code>menubar</code></a>, <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/none_role"><code>none</code></a>,
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role"><code>presentation</code></a>,
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radiogroup_role"><code>radiogroup</code></a>, <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tablist_role"><code>tablist</code></a>,
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/toolbar_role"><code>toolbar</code></a>, <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tree_role"><code>tree</code></a>
      </td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td><code>HTMLUListElement</code></td>
    </tr>
  </tbody>
</table>

## مشخصات

## سازگاری مرورگر

## جستارهای وابسته

- دیگر المان‌های HTML مرتبط با لیست: <code>&lt;ol&gt;</code>، <code>&lt;li&gt;</code>، <code>&lt;menu&gt;</code>
- خواص CSS که مخصوصاً برای استایل‌دهی به المان `<ul>` مفید هستند:
  - ویژگی <code>list-style</code> برای انتخاب نحوه نمایش شماره‌ها.
  - [CSS counters](/en-US/docs/Web/CSS/Guides/Counter_styles/Using_counters) برای مدیریت لیست‌های تودرتوی پیچیده.
  - ویژگی <code>line-height</code> برای شبیه‌سازی attribute منسوخ [`compact`](#compact).
  - ویژگی <code>margin</code> برای کنترل تورفتگی لیست.
```