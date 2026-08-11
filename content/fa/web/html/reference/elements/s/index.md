---
title: "<s> HTML strikethrough element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/s"
translated_by: "n8n + AI"
---

عنصر `<s>` در HTML متن را با خط روی آن (strikethrough) نمایش می‌دهد. از `<s>` برای نشان دادن چیزهایی استفاده کنید که دیگر مرتبط یا دقیق نیستند. با این حال، `<s>` برای نشان دادن ویرایش‌های سند مناسب نیست؛ برای این کار از عناصر `<del>` و `<ins>` استفاده کنید.

## ویژگی‌ها

این عنصر فقط شامل ویژگی‌های سراسری (global attributes) می‌شود.

## دسترس‌پذیری

حضور عنصر `s` به طور پیش‌فرض توسط بسیاری از فناوری‌های صفحه‌خوان اعلام نمی‌شود. می‌توان با استفاده از ویژگی CSS `content` و شبه‌عنصرهای `::before` و `::after` آن را قابل اعلام کرد.

```css
s::before,
s::after {
  clip-path: inset(100%);
  clip: rect(1px, 1px, 1px, 1px);
  height: 1px;
  overflow: hidden;
  position: absolute;
  white-space: nowrap;
  width: 1px;
}

s::before {
  content: " [start of stricken text] ";
}

s::after {
  content: " [end of stricken text] ";
}
```

برخی از کاربران صفحه‌خوان عمداً اعلام محتوایی که پرگویی ایجاد می‌کند را غیرفعال می‌کنند. به همین دلیل مهم است که از این تکنیک سوءاستفاده نکنید و فقط در شرایطی آن را به کار ببرید که دانستن خط خوردن محتوا برای درک مطلب ضروری است.

- [یادداشت کوتاه درباره قابل‌دسترس‌تر کردن نشانه‌گذاری | Vispero](https://vispero.com/resources/short-note-on-making-your-mark-more-accessible/)
- [تنظیم مجدد استایل‌های سطح متن | Adrian Roselli](https://adrianroselli.com/2025/04/tweaking-text-level-styles-reprised.html)

## مثال‌ها

```css
.sold-out {
  text-decoration: line-through;
}
```

```html
<s>Today's Special: Salmon</s> SOLD OUT<br />
<span class="sold-out">Today's Special: Salmon</span> SOLD OUT
```

### نتیجه

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
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >Phrasing content</a
        >,
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >flow content</a
        >.
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >Phrasing content</a
        >.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>هیچ؛ تگ شروع و پایان هر دو الزامی هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
      <td>
        هر عنصری که
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content"
          >phrasing content</a
        >
        را می‌پذیرد.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td>
        <code
          ><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles#structural_roles_with_html_equivalents">deletion</a
          ></code
        >
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

## سازگاری مرورگر

## همچنین ببینید

- عنصر {{HTMLElement("strike")}} که همتای عنصر `<s>` است، منسوخ شده و دیگر نباید در وب‌سایت‌ها استفاده شود.
- اگر داده‌ای _حذف شده_ است، باید به جای آن از عنصر {{HTMLElement("del")}} استفاده کنید.
- برای دستیابی به ظاهر قبلی عنصر `<s>`، باید از ویژگی CSS {{cssxref("text-decoration-line")}} استفاده شود.