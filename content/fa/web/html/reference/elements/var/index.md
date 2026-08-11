---
title: "<var> HTML variable element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/var"
translated_by: "n8n + AI"
---

عنصر `<var>` در HTML نام یک متغیر در یک عبارت ریاضی یا یک زمینهٔ برنامه‌نویسی را مشخص می‌کند. معمولاً با فونت ایتالیک (مورب) از همان فونت جاری نمایش داده می‌شود، هرچند این رفتار به مرورگر بستگی دارد.

```html
<p>
  حجم یک جعبه برابر است با <var>l</var> × <var>w</var> × <var>h</var> که در آن
  <var>l</var> طول، <var>w</var> عرض و <var>h</var> ارتفاع جعبه را نشان می‌دهد.
</p>
```

```css
var {
  font-weight: bold;
}
```

## ویژگی‌ها

این عنصر فقط شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

## نکات استفاده

### عناصر مرتبط

دیگر عناصری که معمولاً در کنار `<var>` استفاده می‌شوند عبارتند از:

- {{HTMLElement("code")}} – عنصر کد در HTML
- {{HTMLElement("kbd")}} – عنصر ورودی صفحه‌کلید در HTML
- {{HTMLElement("samp")}} – عنصر خروجی نمونه در HTML

اگر در کدی از `<var>` به‌اشتباه برای اهداف ظاهری (نه معنایی) استفاده شده است، بهتر است از {{HTMLElement("span")}} با CSS مناسب یا یکی از عناصر معنایی زیر استفاده کنید:

- {{HTMLElement("em")}}
- {{HTMLElement("i")}}
- {{HTMLElement("q")}}

### استایل پیش‌فرض

اکثر مرورگرها هنگام رندر `<var>` از {{cssxref("font-style")}} با مقدار `"italic"` استفاده می‌کنند. می‌توان این رفتار را در CSS بازنویسی کرد:

```css
var {
  font-style: normal;
}
```

## مثال‌ها

### مثال ساده

مثال زیر از `<var>` برای نشان دادن نام متغیرها در یک معادلهٔ ریاضی استفاده می‌کند.

```html
<p>یک معادلهٔ جبری: <var>x</var> = <var>y</var> + 2</p>
```

#### نتیجه

{{EmbedLiveSample("Basic_example", 650,80)}}

### بازنویسی استایل پیش‌فرض

با استفاده از CSS می‌توان استایل پیش‌فرض عنصر `<var>` را تغییر داد. در این مثال، نام متغیرها به صورت bold و با فونت Courier (در صورت وجود) و در غیر این صورت با فونت monospace پیش‌فرض نمایش داده می‌شوند.

#### CSS

```css
var {
  font:
    bold 15px "Courier",
    "Courier New",
    monospace;
}
```

#### HTML

```html
<p>
  متغیرهای <var>minSpeed</var> و <var>maxSpeed</var> حداقل و حداکثر سرعت دستگاه را
  بر حسب دور در دقیقه (RPM) کنترل می‌کنند.
</p>
```

این HTML از `<var>` برای در برگرفتن نام دو متغیر استفاده می‌کند.

#### نتیجه

{{EmbedLiveSample("Overriding_the_default_style", 650, 140)}}

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories">دسته‌بندی محتوا</a>
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">محتوای جریانی (Flow content)</a>،
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">محتوای عبارتی (Phrasing content)</a>،
        محتوای قابل لمس (Palpable content).
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">محتوای عبارتی (Phrasing content)</a>.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>هیچ‌کدام؛ تگ شروع و پایان هر دو اجباری هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
      <td>
        هر عنصری که <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">محتوای عبارتی (Phrasing content)</a> را بپذیرد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td>
        <a href="https://w3c.github.io/html-aria/#dfn-no-corresponding-role">نقش متناظری ندارد</a>
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>هر نقشی</td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td>HTMLElement</td>
    </tr>
  </tbody>
</table>