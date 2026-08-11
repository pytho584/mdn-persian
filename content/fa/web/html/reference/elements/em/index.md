---
title: "<em> HTML emphasis element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/em"
translated_by: "n8n + AI"
---

# `<em>`: المان تأکید HTML

المان `<em>` در HTML متنی را مشخص می‌کند که روی آن تأکید (stress emphasis) وجود دارد. این المان می‌تواند تو در تو قرار بگیرد؛ هر سطح تودرتویی، میزان تأکید بیشتری را نشان می‌دهد.

## Attributes

این المان فقط شامل global attributes می‌شود.

## نکات استفاده

المان `<em>` برای کلماتی به کار می‌رود که در مقایسه با متن اطراف، تأکید دارند؛ این تأکید معمولاً به یک یا چند کلمه از جمله محدود است و روی معنای خود جمله اثر می‌گذارد.

این المان معمولاً به صورت ایتالیک نمایش داده می‌شود. با این حال، نباید از آن برای اعمال استایل ایتالیک استفاده کرد؛ برای این کار باید از خاصیت `font-style` در CSS استفاده کنید. از المان `<cite>` برای نشان دادن عنوان یک اثر (کتاب، نمایشنامه، آهنگ و…) استفاده کنید. از المان `<i>` برای متنی که لحن یا حال‌وهوای متفاوتی دارد استفاده کنید؛ این مورد شامل موقعیت‌های رایج ایتالیک مثل نام‌های علمی یا کلماتی از زبان‌های دیگر می‌شود. از المان `<strong>` برای متنی که اهمیت بیشتری نسبت به متن اطراف دارد استفاده کنید.

### تفاوت `<i>` و `<em>`

بعضی از توسعه‌دهندگان ممکن است از اینکه چند المان نتیجه بصری مشابهی تولید می‌کنند گیج شوند. `<em>` و `<i>` مثال رایجی هستند، چون هر دو متن را ایتالیک می‌کنند. تفاوت در چیست؟ کدام را باید استفاده کنید؟

به طور پیش‌فرض، نتیجه تصویری یکسان است؛ اما معنای معنایی (semantic) متفاوت است. المان `<em>` نشان‌دهنده تأکید بر محتوای خودش است، در حالی که المان `<i>` متنی را نشان می‌دهد که از نثر عادی جدا شده است؛ مثل یک کلمه خارجی، افکار یک شخصیت داستانی، یا وقتی که متن به تعریف یک کلمه اشاره دارد نه به معنای کاربردی آن. (عنوان یک اثر، مثل نام کتاب یا فیلم، باید با `<cite>` مشخص شود.)

بنابراین انتخاب المان درست به موقعیت بستگی دارد. هیچ‌کدام برای تزئین صرف نیستند؛ برای آن کار باید از استایل CSS استفاده کنید.

مثال‌هایی برای `<em>`:

```html
<p>Just <em>do</em> it already!</p>
<p>We <em>had</em> to do something about it.</p>
```

فرد یا نرم‌افزاری که متن را می‌خواند، کلماتی که ایتالیک شده‌اند را با تأکید و با استرس کلامی تلفظ می‌کند.

مثال‌هایی برای `<i>`:

```html
<p>The word <i>the</i> is an article.</p>
<p>The <i>Queen Mary</i> sailed last night.</p>
```

در اینجا هیچ تأکید یا اهمیت اضافه‌ای روی عبارت «Queen Mary» وجود ندارد. فقط مشخص شده که موضوع مورد نظر یک ملکه به نام Mary نیست، بلکه یک کشتی به نام «Queen Mary» است.

## مثال

در این مثال، المان `<em>` برای برجسته کردن تضاد ضمنی یا آشکار بین دو فهرست از مواد تشکیل‌دهنده استفاده شده است:

```html
<p>
  Ice cream is made with milk, sweetener, and cream. Frozen custard, on the
  other hand, is made of milk, cream, sweetener, and <em>egg yolks</em>.
</p>
```

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories"
          >دسته‌بندی محتوا (Content categories)</a
        >
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >Flow content</a
        >،
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >phrasing content</a
        >، palpable content.
      </td>
    </tr>
    <tr>
      <th scope="row">محتواي مجاز (Permitted content)</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >Phrasing content</a
        >.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ (Tag omission)</th>
      <td>هیچ‌کدام؛ هر دو تگ شروع و پایان اجباری هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز (Permitted parents)</th>
      <td>
        هر عنصری که
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >phrasing content</a
        > را بپذیرد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی (Implicit ARIA role)</th>
      <td>
        <code
          ><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles#structural_roles_with_html_equivalents">emphasis</a
          ></code
        >
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز (Permitted ARIA roles)</th>
      <td>هر نقشی</td>
    </tr>
    <tr>
      <th scope="row">رابط DOM (DOM interface)</th>
      <td>
        HTMLElement. تا Gecko 1.9.2 (Firefox 4) به‌طور کامل، Firefox از رابط HTMLSpanElement برای این عنصر استفاده می‌کند.
      </td>
    </tr>
  </tbody>
</table>