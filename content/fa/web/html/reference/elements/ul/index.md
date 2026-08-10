---
title: "<ul> HTML unordered list element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/ul"
translated_by: "n8n + AI"
---

# عنصر `<ul>` در HTML: لیست نامرتب

عنصر **`<ul>`** در HTML یک لیست نامرتب از آیتم‌ها را نشان می‌دهد که معمولاً به‌صورت یک لیست گلوله‌ای (bullet) نمایش داده می‌شود.

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

## attributes

این عنصر از [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes) پشتیبانی می‌کند.

- `compact` (منسوخ‌شده)
  - : این attribute از نوع Boolean به مرورگر پیشنهاد می‌دهد که لیست را به‌صورت فشرده نمایش دهد. نحوهٔ تفسیر این attribute وابسته به مرورگر است. امروزه به‌جای آن از [CSS](/en-US/docs/Web/CSS) استفاده کنید: برای رسیدن به اثری مشابه، می‌توانید ویژگی {{cssxref("line-height")}} را با مقدار `80%` به‌کار ببرید.
- `type` (منسوخ‌شده)
  - : این attribute سبک گلولهٔ لیست را مشخص می‌کند. مقادیر تعریف‌شده در HTML 3.2 و نسخهٔ انتقالی HTML 4.0/4.01 عبارت‌اند از:
    - `circle`
    - `disc`
    - `square`

    یک نوع گلولهٔ چهارم به نام `triangle` نیز در رابط WebTV تعریف شده بود، اما همهٔ مرورگرها از آن پشتیبانی نمی‌کنند.

    اگر این attribute وجود نداشته باشد و هیچ ویژگی {{cssxref("list-style-type")}} از CSS روی عنصر اعمال نشده باشد، مرورگر بر اساس سطح تودرتو بودن لیست، یک نوع گلوله را انتخاب می‌کند.

    > [!WARNING]
    > از این attribute استفاده نکنید؛ منسوخ شده است. به‌جای آن از ویژگی {{cssxref("list-style-type")}} در CSS استفاده کنید.

## نکات کاربردی

- عنصر `<ul>` برای گروه‌بندی مجموعه‌ای از آیتم‌ها به‌کار می‌رود که ترتیب عددی ندارند و جایگاه آن‌ها در لیست بی‌معنی است. معمولاً آیتم‌های لیست نامرتب با یک گلوله نمایش داده می‌شوند که می‌تواند به‌شکل‌های مختلفی مانند نقطه، دایره یا مربع باشد. سبک گلوله در خود HTML تعریف نمی‌شود، بلکه در CSS مرتبط و با استفاده از ویژگی {{cssxref("list-style-type")}} مشخص می‌شود.
- عناصر `<ul>` و {{HTMLElement("ol")}} را می‌توان تا هر عمقی به‌صورت تودرتو به‌کار برد. همچنین می‌توانید بدون محدودیت، لیست‌های تودرتوی `<ol>` و `<ul>` را به‌صورت یکی‌درمیان استفاده کنید.
- هر دو عنصر {{HTMLElement("ol")}} و `<ul>` یک لیست از آیتم‌ها را نشان می‌دهند. تفاوت آن‌ها در این است که در عنصر {{HTMLElement("ol")}} ترتیب اهمیت دارد. برای تشخیص اینکه از کدام یک استفاده کنید، ترتیب آیتم‌ها را تغییر دهید؛ اگر با تغییر ترتیب، معنا عوض شد، باید از {{HTMLElement("ol")}} استفاده کنید، در غیر این صورت `<ul>` مناسب است.

## مثال‌ها

### مثال ساده

```html
<ul>
  <li>first item</li>
  <li>second item</li>
  <li>third item</li>
</ul>
```

#### نتیجه

### لیست تودرتو

```html
<ul>
  <li>first item</li>
  <li>
    second item
    <!-- Look, the closing </li> tag is not placed here! -->
    <ul>
      <li>second item first subitem</li>
      <li>
        second item second subitem
        <!-- Same for the second nested unordered list! -->
        <ul>
          <li>second item second subitem first sub-subitem</li>
          <li>second item second subitem second sub-subitem</li>
          <li>second item second subitem third sub-subitem</li>
        </ul>
      </li>
      <!-- Closing </li> tag for the li that
                  contains the third unordered list -->
      <li>second item third subitem</li>
    </ul>
    <!-- Here is the closing </li> tag -->
  </li>
  <li>third item</li>
</ul>
```

#### نتیجه

### لیست مرتب داخل لیست نامرتب

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

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories">دسته‌بندی محتوا</a>
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">محتوای جریانی</a> (flow content) و اگر فرزندان عنصر <code>&#x3C;ul></code> حداقل یک عنصر {{HTMLElement("li")}} داشته باشند،
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#palpable_content">محتوای قابل لمس</a> (palpable content).
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>
        صفر یا چند عنصر {{HTMLElement("li")}}،
        {{HTMLElement("script")}} و
        {{HTMLElement("template")}}.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>هیچ‌کدام؛ هر دو تگ شروع و پایان الزامی هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدهای مجاز</th>
      <td>
        هر عنصری که
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">محتوای جریانی</a> را بپذیرد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td>
        <code><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/list_role">list</a></code>
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/directory_role"><code>directory</code></a>، <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role"><code>group</code></a>،
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listbox_role"><code>listbox</code></a>، <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menu_role"><code>menu</code></a>،
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menubar_role"><code>menubar</code></a>، <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/none_role"><code>none</code></a>،
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role"><code>presentation</code></a>،
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radiogroup_role"><code>radiogroup</code></a>، <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tablist_role"><code>tablist</code></a>،
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/toolbar_role"><code>toolbar</code></a>، <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tree_role"><code>tree</code></a>
      </td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td>{{domxref("HTMLUListElement")}}</td>
    </tr>
  </tbody>
</table>

## همچنین ببینید

- دیگر عناصر HTML مرتبط با لیست: {{HTMLElement("ol")}}، {{HTMLElement("li")}}، {{HTMLElement("menu")}}
- ویژگی‌های CSS که ممکن است برای استایل‌دهی به عنصر `<ul>` مفید باشند:
  - ویژگی {{CSSxRef("list-style")}}، برای انتخاب نحوه نمایش نشانگر ترتیب.
  - [شمارنده‌های CSS](/en-US/docs/Web/CSS/Guides/Counter_styles/Using_counters)، برای مدیریت لیست‌های تودرتو پیچیده.
  - ویژگی {{CSSxRef("line-height")}}، برای شبیه‌سازی صفت منسوخ شدهٔ [`compact`](#compact).
  - ویژگی {{CSSxRef("margin")}}، برای کنترل تورفتگی لیست.