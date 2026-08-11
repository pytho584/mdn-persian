---
title: "<cite> HTML citation element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/cite"
translated_by: "n8n + AI"
---

المان `<cite>` در HTML برای نشان‌دادن عنوان یک اثر هنری یا علمی استفاده می‌شود. ارجاع می‌تواند به صورت خلاصه‌شده و مطابق با قراردادهای مربوط به فرادادهٔ استناد (citation metadata) باشد.

```html interactive-example
<figure>
  <blockquote>
    <p>
      It was a bright cold day in April, and the clocks were striking thirteen.
    </p>
  </blockquote>
  <figcaption>
    First sentence in
    <cite
      ><a href="http://www.george-orwell.org/1984/0.html"
        >Nineteen Eighty-Four</a
      ></cite
    >
    by George Orwell (Part 1, Chapter 1).
  </figcaption>
</figure>
```

```css interactive-example
cite {
  /* Add your styles here */
}
```

## ویژگی‌ها (Attributes)

این المان فقط شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

## نکات استفاده

در زمینهٔ المان `<cite>`، یک اثر هنری یا علمی می‌تواند مثلاً یکی از موارد زیر باشد:

- کتاب
- مقالهٔ پژوهشی
- جستار
- شعر
- نت موسیقی
- آهنگ
- فیلمنامه یا نمایشنامه
- فیلم
- برنامهٔ تلویزیونی
- بازی
- مجسمه
- نقاشی
- اجرای تئاتر
- نمایش
- اپرا
- موزیکال
- نمایشگاه
- گزارش پروندهٔ حقوقی
- برنامهٔ کامپیوتری
- وب‌سایت
- صفحهٔ وب
- پست وبلاگ یا دیدگاه
- پست انجمن یا دیدگاه
- توییت
- پست فیسبوک
- بیانیهٔ نوشتاری یا شفاهی
- و غیره.

برای ارجاع به منبع محتوای نقل‌قول‌شده که درون یک المان {{HTMLElement("blockquote")}} یا {{HTMLElement("q")}} قرار دارد، از ویژگی [`cite`](/en-US/docs/Web/HTML/Reference/Elements/blockquote#cite) روی آن المان استفاده کنید.

به‌طور پیش‌فرض، مرورگرها محتوای المان `<cite>` را به صورت ایتالیک (مورب) نمایش می‌دهند. برای جلوگیری از این رفتار، می‌توانید با استفاده از خاصیت CSS {{cssxref("font-style")}} آن را تغییر دهید.

## مثال‌ها

```html
<p>More information can be found in <cite>[ISO-0000]</cite>.</p>
```

### نتیجه

{{EmbedLiveSample("Example", 640, 80)}}

## خلاصهٔ فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories"
          >دسته‌بندی محتوا</a
        >
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >محتوی جریانی (Flow content)</a
        >،
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >محتوی متنی (Phrasing content)</a
        >، محتوای قابل لمس.
      </td>
    </tr>
    <tr>
      <th scope="row">محتوی مجاز</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >محتوی متنی (Phrasing content)</a
        >.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>هیچکدام؛ هر دو تگ شروع و پایان اجباری هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
      <td>
        هر المانی که
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >محتوی متنی (Phrasing content)</a
        > را بپذیرد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td>
        <a href="https://w3c.github.io/html-aria/#dfn-no-corresponding-role"
          >نقش متناظری ندارد</a
        >
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>هر نقشی</td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td>
        {{domxref("HTMLElement")}} تا Gecko 1.9.2 (Firefox 4) به صورت فراگیر، فایرفاکس از رابط {{domxref("HTMLSpanElement")}} برای این المان استفاده می‌کند.
      </td>
    </tr>
  </tbody>
</table>

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## جستارهای وابسته

- المان `<blockquote>` برای نقل‌قول‌های طولانی.
- المان `<q>` برای نقل‌قول‌های درون‌خطی (inline) و attribute [`cite`](/en-US/docs/Web/HTML/Reference/Elements/q#cite).