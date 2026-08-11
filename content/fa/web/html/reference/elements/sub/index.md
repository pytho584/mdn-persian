---
title: "<sub> HTML subscript element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/sub"
translated_by: "n8n + AI"
---

عنصر `<sub>` در HTML — زیرنویس تایپوگرافی

عنصر **`<sub>`** در [HTML](/en-US/docs/Web/HTML) برای نمایش متن‌های درون‌خطی‌ای به‌کار می‌رود که به دلایل صرفاً تایپوگرافی به صورت زیرنویس (subscript) نمایش داده شوند. زیرنویس‌ها معمولاً با خط پایه‌ای پایین‌تر و با فونتی کوچک‌تر رندر می‌شوند.

```html
<p>
  تقریباً مولکول مورد علاقه هر توسعه‌دهنده‌ای
  C<sub>8</sub>H<sub>10</sub>N<sub>4</sub>O<sub>2</sub> است، که با نام «کافئین» شناخته می‌شود.
</p>
```

```css
p {
  font:
    1rem "Fira Sans",
    sans-serif;
}
```

## ویژگی‌ها

این عنصر فقط شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

## نکات استفاده

عنصر `<sub>` فقط برای اهداف تایپوگرافی باید استفاده شود — یعنی برای تغییر موقعیت متن به منظور رعایت قراردادها یا استانداردهای تایپوگرافی، نه صرفاً برای ظاهر یا زیبایی‌سازی.

به‌عنوان مثال، استفاده از `<sub>` برای استایل‌دهی به نام یک شرکت که در نشانواره (wordmark) خود از خط پایه‌ای تغییر یافته استفاده می‌کند، مناسب نیست؛ در عوض باید از CSS استفاده شود. مثلاً می‌توانید از ویژگی {{cssxref("vertical-align")}} با مقداری مانند `vertical-align: sub` یا برای کنترل دقیق‌تر جابه‌جایی خط پایه، از `vertical-align: -25%` استفاده کنید.

موارد استفاده مناسب برای `<sub>` شامل (اما نه محدود به) موارد زیر است:

- علامت‌گذاری شماره پانوشت‌ها. برای نمونه به [شماره‌های پانوشت](#footnote_numbers) مراجعه کنید.
- علامت‌گذاری زیرنویس در متغیرهای ریاضی (البته می‌توانید از یک فرمول [MathML](/en-US/docs/Web/MathML) نیز برای این کار استفاده کنید). به [زیرنویس متغیرها](#variable_subscripts) مراجعه کنید.
- نمایش تعداد اتم‌های یک عنصر در فرمول شیمیایی (مانند مولکول محبوب هر توسعه‌دهنده، C<sub>8</sub>H<sub>10</sub>N<sub>4</sub>O<sub>2</sub> که با نام «کافئین» شناخته می‌شود). به [فرمول‌های شیمیایی](#chemical_formulas) مراجعه کنید.

## نمونه‌ها

### شماره‌های پانوشت

پانوشت‌های سنتی با اعدادی که به صورت زیرنویس نمایش داده می‌شوند مشخص می‌گردند. این یک کاربرد رایج برای `<sub>` است:

```html
<p>
  طبق محاسبات ناکامورا، جانسون و میسون<sub>1</sub>، این اتفاق منجر به نابودی کامل هر دو ذره خواهد شد.
</p>
```

### زیرنویس متغیرها

در ریاضیات، خانواده‌هایی از متغیرها که به یک مفهوم مرتبط هستند (مانند فاصله‌ها در امتداد یک محور) با استفاده از یک نام متغیر یکسان و یک زیرنویس نمایش داده می‌شوند. به‌عنوان مثال:

```html-nolint
<p>
  موقعیت مختصات افقی در امتداد محور X به صورت
  <var>x<sub>1</sub></var> … <var>x<sub>n</sub></var> نمایش داده می‌شود.
</p>
```

### فرمول‌های شیمیایی

هنگام نوشتن یک فرمول شیمیایی، مانند H<sub>2</sub>O، تعداد اتم‌های یک عنصر در مولکول توصیف‌شده با یک عدد زیرنویس نمایش داده می‌شود؛ در مورد آب، عدد زیرنویس «2» نشان می‌دهد که دو اتم هیدروژن در مولکول وجود دارد.

مثال دیگر:

```html
<p>
  تقریباً مولکول مورد علاقه هر توسعه‌دهنده‌ای
  C<sub>8</sub>H<sub>10</sub>N<sub>4</sub>O<sub>2</sub> است، که معمولاً با نام «کافئین» شناخته می‌شود.
</p>
```

## خلاصه فنی

(متن کامل خلاصه فنی در ورودی ارائه نشده بود، بنابراین این بخش ترجمه نمی‌شود.)

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories">دسته‌های محتوا</a>
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">Flow content</a>،
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">phrasing content</a>،
        محتوای قابل لمس (palpable content).
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">Phrasing content</a>.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>هیچ‌کدام؛ هر دو تگ شروع و پایان الزامی هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
      <td>
        هر عنصری که
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">phrasing content</a>
        را بپذیرد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td>
        <code><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles#structural_roles_with_html_equivalents">subscript</a></code>
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>هر نقشی</td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td>{{domxref("HTMLElement")}}</td>
    </tr>
  </tbody>
</table>

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- عنصر HTML {{HTMLElement("sup")}} که زیرنویس (superscript) تولید می‌کند. توجه داشته باشید که نمی‌توانید `sup` و `sub` را همزمان استفاده کنید؛ برای نمایش هم‌زمان زیرنویس و فوق‌نویس در کنار نماد شیمیایی یک عنصر (عدد اتمی و عدد جرمی)، باید از [MathML](/en-US/docs/Web/MathML) استفاده کنید.
- عناصر MathML [`<msub>`](/en-US/docs/Web/MathML/Reference/Element/msub)، [`<msup>`](/en-US/docs/Web/MathML/Reference/Element/msup) و [`<msubsup>`](/en-US/docs/Web/MathML/Reference/Element/msubsup).
- ویژگی CSS {{cssxref("vertical-align")}}.