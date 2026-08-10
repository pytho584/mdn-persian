---
title: "<ol> HTML ordered list element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/ol"
translated_by: "n8n + AI"
---

# `<ol>`: عنصر لیست مرتب HTML

عنصر **`<ol>`** در HTML یک لیست مرتب از آیتم‌ها را نشان می‌دهد که معمولاً به‌صورت یک لیست شماره‌دار نمایش داده می‌شود.

```html
<ol>
  <li>Mix flour, baking powder, sugar, and salt.</li>
  <li>In another bowl, mix eggs, milk, and oil.</li>
  <li>Stir both mixtures together.</li>
  <li>Fill muffin tray 3/4 full.</li>
  <li>Bake for 20 minutes.</li>
</ol>
```

```css
li {
  font:
    1rem "Fira Sans",
    sans-serif;
  margin-bottom: 0.5rem;
}
```

## ویژگی‌ها

این عنصر ویژگی‌های سراسری HTML را نیز می‌پذیرد.

- `compact` (منسوخ، غیر استاندارد)
  - : این ویژگی Boolean نشان می‌دهد که لیست باید به‌صورت فشرده نمایش داده شود. نحوهٔ تفسیر آن به مرورگر بستگی دارد. به‌جای آن از CSS استفاده کنید: برای رسیدن به اثری مشابه، می‌توانید از ویژگی CSS `line-height` با مقدار `80%` استفاده کنید.
- `reversed`
  - : این ویژگی Boolean ترتیب آیتم‌های لیست را برعکس می‌کند. شماره‌ها از بزرگ به کوچک نمایش داده می‌شوند.
- `start`
  - : یک عدد صحیح که شمارش آیتم‌های لیست را از آن شروع می‌کند. همیشه به‌صورت عدد عربی (۱، ۲، ۳ و...) نوشته می‌شود، حتی اگر نوع شماره‌گذاری (`type`) حروف یا اعداد رومی باشد. برای مثال، برای شروع شماره‌گذاری از حرف «d» یا عدد رومی «iv» از `start="4"` استفاده کنید.
- `type`
  - : نوع شماره‌گذاری را تعیین می‌کند:
    - `a` برای حروف کوچک انگلیسی
    - `A` برای حروف بزرگ انگلیسی
    - `i` برای اعداد رومی کوچک
    - `I` برای اعداد رومی بزرگ
    - `1` برای اعداد (پیش‌فرض)

    نوع مشخص‌شده برای کل لیست به‌کار می‌رود، مگر اینکه درون یکی از عنصرهای {{HTMLElement("li")}} از ویژگی `type` متفاوتی استفاده شده باشد.

    > [!NOTE]
    > اگر نوع شمارهٔ لیست اهمیت خاصی ندارد (مثلاً در اسناد حقوقی یا فنی که به شماره یا حرف آیتم‌ها ارجاع داده می‌شود)، به‌جای این ویژگی از CSS و پراپرتی `list-style-type` استفاده کنید.

## نکات استفاده

معمولاً آیتم‌های لیست مرتب با یک نشانگر (marker) در ابتدا نمایش داده می‌شوند؛ مثل یک عدد یا حرف.

عنصر `<ol>` و {{HTMLElement("ul")}} (یا عنصر معادل {{HTMLElement("menu")}}) می‌توانند به‌دلخواه درون یکدیگر تودرتو شوند و هر جا لازم بود بین `<ol>`، `<ul>` (یا `<menu>`) جابجا شوید.

هر دو عنصر `<ol>` و {{HTMLElement("ul")}} یک لیست از آیتم‌ها را نشان می‌دهند. تفاوت در این است که در `<ol>` ترتیب آیتم‌ها معنی‌دار است. برای نمونه:

- مراحل یک دستور پخت
- راهنمای گام‌به‌گام مسیر
- فهرست مواد تشکیل‌دهنده بر اساس نسبت کاهشی در برچسب‌های اطلاعات تغذیه‌ای

برای تشخیص اینکه از کدام لیست استفاده کنید، ترتیب آیتم‌ها را تغییر دهید؛ اگر معنا عوض شد، از `<ol>` استفاده کنید، در غیر این صورت می‌توانید از {{HTMLElement("ul")}} یا اگر لیست شما یک منو است، از {{HTMLElement("menu")}} بهره ببرید.

## مثال‌ها

### مثال ساده

```html
<ol>
  <li>Fee</li>
  <li>Fi</li>
  <li>Fo</li>
  <li>Fum</li>
</ol>
```

نتیجه: نمایش یک لیست شماره‌دار با آیتم‌های Fee, Fi, Fo, Fum.

### استفاده از نوع اعداد رومی

```html
<ol type="i">
  <li>Introduction</li>
  <li>List of Grievances</li>
  <li>Conclusion</li>
</ol>
```

نتیجه: لیستی شماره‌گذاری‌شده با اعداد رومی کوچک (i, ii, iii).

### استفاده از ویژگی start

```html
<p>Finishing places of contestants not in the winners' circle:</p>

<ol start="4">
  <li>Speedwalk Stu</li>
  <li>Saunterin' Sam</li>
  <li>Slowpoke Rodriguez</li>
</ol>
```

نتیجه: لیست شماره‌گذاری از ۴ شروع می‌شود و آیتم‌ها به‌ترتیب ۴، ۵، ۶ نمایش داده می‌شوند.

### لیست‌های تودرتو

```html
<ol>
  <li>first item</li>
  <li>
    second item
    <ul>
      <li>sub item</li>
      <li>sub item</li>
    </ul>
  </li>
  <li>third item</li>
</ol>
```

نتیجه: یک لیست مرتب که درون آیتم دوم آن یک لیست نامرتب تودرتو قرار دارد.

```html
<ol>
  <li>first item</li>
  <li>
    second item
    <!-- closing </li> tag is not here! -->
    <ol>
      <li>second item first subitem</li>
      <li>second item second subitem</li>
      <li>second item third subitem</li>
    </ol>
  </li>
  <!-- Here's the closing </li> tag -->
  <li>third item</li>
</ol>
```

### لیست نامرتب درون لیست مرتب

```html
<ol>
  <li>first item</li>
  <li>
    second item
    <!-- closing </li> tag is not here! -->
    <ul>
      <li>second item first subitem</li>
      <li>second item second subitem</li>
      <li>second item third subitem</li>
    </ul>
  </li>
  <!-- Here's the closing </li> tag -->
  <li>third item</li>
</ol>
```

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        دسته‌بندی‌های محتوا (Content categories)
      </th>
      <td>
        محتوای جریانی (Flow content)، و در صورتی که عنصر <code>&#x3C;ol></code> حداقل یک عنصر <code>&#x3C;li></code> به عنوان فرزند داشته باشد، محتوای محسوس (palpable content).
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز (Permitted content)</th>
      <td>
        صفر یا چند عنصر <code>&#x3C;li></code>، <code>&#x3C;script></code> و <code>&#x3C;template></code>.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ (Tag omission)</th>
      <td>هیچ‌کدام، هر دو تگ شروع و پایان اجباری هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدهای مجاز (Permitted parents)</th>
      <td>
        هر عنصری که محتوای جریانی (Flow content) را بپذیرد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی (Implicit ARIA role)</th>
      <td>
        <code>list</code>
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز (Permitted ARIA roles)</th>
      <td>
        <code>directory</code>, <code>group</code>,
        <code>listbox</code>, <code>menu</code>,
        <code>menubar</code>, <code>none</code>,
        <code>presentation</code>,
        <code>radiogroup</code>, <code>tablist</code>,
        <code>toolbar</code>, <code>tree</code>
      </td>
    </tr>
    <tr>
      <th scope="row">رابط DOM (DOM interface)</th>
      <td><code>HTMLOListElement</code></td>
    </tr>
  </tbody>
</table>

- سایر عناصر HTML مرتبط با لیست: {{HTMLElement("ul")}}, {{HTMLElement("li")}}, {{HTMLElement("menu")}}
- ویژگی‌های CSS که می‌توانند برای استایل‌دهی عنصر `<ol>` مفید باشند:
  - ویژگی {{CSSxRef("list-style")}} برای انتخاب نحوه نمایش شماره ترتیب
  - [CSS counters](/en-US/docs/Web/CSS/Guides/Counter_styles/Using_counters)، برای مدیریت لیست‌های تودرتوی پیچیده
  - ویژگی {{CSSxRef("line-height")}} برای شبیه‌سازی ویژگی منسوخ‌شده‌ی `compact`
  - ویژگی {{CSSxRef("margin")}} برای کنترل تورفتگی لیست