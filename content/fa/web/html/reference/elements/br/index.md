---
title: "<br> HTML line break element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/br"
translated_by: "n8n + AI"
---

عنصر `<br>` برای شکست خط در HTML
---

عنصر **`<br>`** در HTML یک شکست خط (Carriage-return) در متن ایجاد می‌کند. این عنصر در جاهایی مانند شعر یا آدرس که تفکیک خطوط اهمیت دارد، بسیار کاربردی است.

> [!NOTE]  
> از `<br>` برای ایجاد فاصله بین پاراگراف‌ها استفاده نکنید. متن را درون عنصر {{htmlelement("p")}} قرار دهید و با ویژگی CSS {{cssxref('margin')}} اندازه فاصله را تنظیم کنید.

## ویژگی‌ها (Attributes)

ویژگی‌های این عنصر، شامل [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) هستند.

### ویژگی منسوخ

- `clear` {{Deprecated_Inline}}  
  - : مشخص می‌کند که خط بعدی پس از شکست از کجا شروع شود.

## استایل‌دهی با CSS

عنصر `<br>` تنها یک کار مشخص دارد: ایجاد شکست خط در یک بلوک متنی. به همین دلیل، خود این عنصر هیچ بُعد یا خروجی بصری مستقلی ندارد و امکانات استایل‌دهی آن بسیار محدود است.

می‌توانید ویژگی {{cssxref("margin")}} را روی خود عناصر `<br>` تنظیم کنید تا فاصله بین خطوط بیشتر شود، اما این کار نادرست است. به‌جای آن باید از ویژگی {{cssxref("line-height")}} که دقیقاً برای همین منظور طراحی شده استفاده کنید.

## دسترسی‌پذیری (Accessibility)

استفاده از `<br>` برای جداسازی پاراگراف‌ها نه‌تنها روش نادرستی است، بلکه برای افرادی که با فناوری‌های صفحه‌خوان (screen reader) وبگردی می‌کنند مشکل‌ساز می‌شود. صفحه‌خوان‌ها ممکن است حضور این عنصر را اعلام کنند، اما محتوایی که داخل `<br>`هاست را نمی‌خوانند. این مسئله می‌تواند تجربه‌ای گیج‌کننده و آزاردهنده برای کاربر صفحه‌خوان ایجاد کند.

به‌جای این کار از عنصر `<p>` استفاده کنید و با ویژگی‌های CSS مانند {{cssxref("margin")}} فاصله‌ها را تنظیم نمایید.

## مثال‌ها

### `<br>` ساده

در مثال زیر برای شکستن خطوط یک آدرس پستی از عنصر `<br>` استفاده کرده‌ایم:

```html
Mozilla<br />
331 E. Evelyn Avenue<br />
Mountain View, CA<br />
94041<br />
USA<br />
```

#### نتیجه

خروجی به صورت زیر نمایش داده می‌شود:

Mozilla  
331 E. Evelyn Avenue  
Mountain View, CA  
94041  
USA

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories"
          >دسته‌بندی‌های محتوا</a
        >
      </th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >محتوای جریانی</a
        >،
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >محتوای عبارتی</a
        >.
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>هیچ‌کدام؛ یک عنصر void است.</td>
    </tr>
    <tr>
      <th scope="row">حذف برچسب</th>
      <td>
        باید برچسب آغازین داشته باشد و نباید برچسب پایانی داشته باشد. در مستندات XHTML، این عنصر را به صورت <code>&#x3C;br /></code> بنویسید.
      </td>
    </tr>
    <tr>
      <th scope="row">والدهای مجاز</th>
      <td>
        هر عنصری که
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >محتوای عبارتی</a
        >
        را بپذیرد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ضمنی ARIA</th>
      <td>
        <a href="https://w3c.github.io/html-aria/#dfn-no-corresponding-role"
          >نقش متناظری ندارد</a
        >
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های مجاز ARIA</th>
      <td>
        <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/none_role"><code>none</code></a>، <a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role"><code>presentation</code></a>
      </td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td><code>HTMLBRElement</code></td>
    </tr>
  </tbody>
</table>

## جستارهای وابسته

- <code>&lt;address&gt;</code> element
- <code>&lt;p&gt;</code> element
- <code>&lt;wbr&gt;</code> element