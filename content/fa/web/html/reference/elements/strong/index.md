---
title: "<strong> HTML strong importance element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/strong"
translated_by: "n8n + AI"
---

عنصر **`<strong>`** در [HTML](/en-US/docs/Web/HTML) نشان‌دهندهٔ محتوایی است که اهمیت، جدیت یا فوریت بالایی دارد. مرورگرها معمولاً محتوای داخل آن را به صورت **bold** (درشت) نمایش می‌دهند.

```html interactive-example
<p>
  ... مهم‌ترین قانون، قانونی که هرگز نباید فراموش کنی، مهم نیست چقدر گریه کند،
  مهم نیست چقدر التماس کند:
  <strong>هرگز بعد از نیمه‌شب بهش غذا نده</strong>.
</p>
```

```css interactive-example
p {
  font-size: 1rem;
}
```

## ویژگی‌ها (Attributes)

این عنصر فقط [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) را شامل می‌شود.

## نکات استفاده

عنصر `<strong>` برای محتوایی با «اهمیت زیاد» به کار می‌رود، از جمله مواردی با جدیت یا فوریت بالا (مثل هشدارها). این می‌تواند یک جملهٔ بسیار مهم در کل صفحه باشد، یا صرفاً اشاره‌ای به این که برخی کلمات در مقایسه با محتوای اطراف اهمیت بیشتری دارند.

به‌طور پیش‌فرض، مرورگرها این عنصر را با وزن قلم bold (درشت) نمایش می‌دهند. اما نباید از `<strong>` فقط برای درشت‌نمایی استفاده کرد؛ برای این کار از خاصیت CSS {{cssxref("font-weight")}} استفاده کنید. برای جلب توجه به یک متن بدون افزایش سطح اهمیت، از عنصر {{HTMLElement("b")}} استفاده کنید. و برای متنی که تأکید (stress emphasis) دارد، عنصر {{HTMLElement("em")}} را به کار ببرید.

یکی دیگر از کاربردهای پذیرفته‌شدهٔ `<strong>`، نشان‌دادن برچسب پاراگراف‌هایی است که در متن یک صفحه، نکته یا هشدار را بیان می‌کنند.

### \<b> در مقابل \<strong>

توسعه‌دهنده‌های تازه‌کار اغلب گیج می‌شوند که چرا راه‌های زیادی برای بیان یک چیز در یک وب‌سایت رندر شده وجود دارد. {{HTMLElement("b")}} و `<strong>` احتمالاً یکی از رایج‌ترین منابع سردرگمی هستند و توسعه‌دهنده‌ها می‌پرسند «آیا باید از `<b>` استفاده کنم یا `<strong>`؟ مگر هر دو یک کار را انجام نمی‌دهند؟»

دقیقاً نه. عنصر `<strong>` برای محتوایی با اهمیت بیشتر است، در حالی که `<b>` برای جلب توجه به متن به کار می‌رود بدون این که نشان دهد اهمیت بیشتری دارد.

برای درک بهتر، به خاطر داشته باشید که هر دو عنصر معتبر و معنایی (semantic) در HTML هستند و این یک تصادف است که هر دو در بیشتر مرورگرها ظاهر پیش‌فرض یکسانی (boldface) دارند (البته برخی مرورگرهای قدیمی‌تر `<strong>` را زیرخط‌دار می‌کردند). هر عنصر برای سناریوهای خاصی طراحی شده است و اگر می‌خواهید متنی را برای تزئین درشت کنید، باید از خاصیت CSS {{cssxref("font-weight")}} استفاده کنید.

معنا یا هدف مورد نظر متن داخل عنصر تعیین می‌کند که از کدام عنصر استفاده کنید. انتقال معنا، هدف اصلی semantic‌هاست.

### \<em> در مقابل \<strong>

سردرگمی را بیشتر می‌کند این که HTML 4 `<strong>` را به عنوان تأکید قوی‌تر تعریف کرده بود، اما HTML 5 آن را به عنوان «اهمیت زیاد برای محتوایش» تعریف می‌کند. این یک تفاوت مهم است.

در حالی که `<em>` برای تغییر معنای یک جمله به‌صورت تأکید گفتاری استفاده می‌شود (مثلاً «من **هویج** را دوست دارم» در مقابل «من هویج را **دوست دارم**»)، `<strong>` برای افزایش اهمیت بخش‌هایی از جمله به کار می‌رود (مثلاً «**هشدار!** این **بسیار خطرناک** است.»). هر دو `<strong>` و `<em>` می‌توانند تو در تو استفاده شوند تا درجهٔ اهمیت یا تأکید نسبی افزایش یابد.

## مثال‌ها

### مثال پایه

```html
<p>
  قبل از ادامه، <strong>حتماً عینک ایمنی خود را بزنید</strong>.
</p>
```

#### نتیجه

{{EmbedLiveSample("Basic_example", 650, 80)}}

### برچسب‌گذاری هشدارها

```html
<p>
  <strong>مهم:</strong> قبل از ادامه، مطمئن شوید که کرهٔ کافی اضافه کرده‌اید.
</p>
```

#### نتیجه

{{EmbedLiveSample("Labeling_warnings", 650, 80)}}

## خلاصهٔ فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">محتوای مجاز (Content categories)</th>
      <td><a href="/en-US/docs/Web/HTML/Reference/Content_categories#flow_content">محتوای جریانی (Flow content)</a>، <a href="/en-US/docs/Web/HTML/Reference/Content_categories#phrasing_content">محتوای عبارتی (Phrasing content)</a>، محتوای لمسی (Palpable content).</td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td><a href="/en-US/docs/Web/HTML/Reference/Content_categories#phrasing_content">محتوای عبارتی</a>.</td>
    </tr>
    <tr>
      <th scope="row">تگ‌های باز و بسته</th>
      <td>تگ آغازین الزامی است، تگ پایانی الزامی است.</td>
    </tr>
    <tr>
      <th scope="row">والد مجاز</th>
      <td>هر عنصری که <a href="/en-US/docs/Web/HTML/Reference/Content_categories#phrasing_content">محتوای عبارتی</a> می‌پذیرد.</td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td><code>strong</code></td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>هر کدام</td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td>{{domxref("HTMLElement")}}</td>
    </tr>
  </tbody>
</table>

| ویژگی | مقدار |
| --- | --- |
| [دسته‌بندی محتوا](/en-US/docs/Web/HTML/Guides/Content_categories) | [Flow content](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content)، [Phrasing content](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content)، palpable content |
| محتوای مجاز | [Phrasing content](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) |
| حذف تگ | هیچ‌کدام؛ باید هم تگ شروع و هم تگ پایان داشته باشد. |
| والدین مجاز | هر عنصری که [phrasing content](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) یا [flow content](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content) را بپذیرد. |
| نقش ضمنی ARIA | [`strong`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles#structural_roles_with_html_equivalents) |
| نقش‌های ARIA مجاز | هر نقشی |
| رابط DOM | `HTMLElement` |

## مشخصات

## سازگاری مرورگر

## همچنین ببینید

- عنصر `<b>`
- عنصر `<em>`
- ویژگی `font-weight`