---
title: "<map> HTML image map element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/map"
translated_by: "n8n + AI"
---

عنصر `<map>` در HTML به همراه عناصر `<area>` برای تعریف یک **image map** (ناحیه لینک قابل کلیک روی تصویر) استفاده می‌شود.

```html interactive-example
<map name="infographic">
  <area
    shape="poly"
    coords="130,147,200,107,254,219,130,228"
    href="https://developer.mozilla.org/docs/Web/HTML"
    alt="HTML" />
  <area
    shape="poly"
    coords="130,147,130,228,6,219,59,107"
    href="https://developer.mozilla.org/docs/Web/CSS"
    alt="CSS" />
  <area
    shape="poly"
    coords="130,147,200,107,130,4,59,107"
    href="https://developer.mozilla.org/docs/Web/JavaScript"
    alt="JavaScript" />
</map>
<img
  usemap="#infographic"
  src="/shared-assets/images/examples/mdn-info2.png"
  alt="MDN infographic" />
```

```css interactive-example
img {
  display: block;
  margin: 0 auto;
  width: 260px;
  height: 232px;
}
```

## ویژگی‌ها (Attributes)

این عنصر از [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) پشتیبانی می‌کند.

- **`name`**  
  ویژگی `name` یک نام برای map تعیین می‌کند تا بتوان به آن ارجاع داد. این ویژگی باید وجود داشته باشد و مقدار آن غیرخالی و بدون فاصله باشد. مقدار `name` نباید با مقدار `name` هیچ `<map>` دیگری در همان سند یکسان باشد. اگر ویژگی [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) هم مشخص شده باشد، هر دو ویژگی باید مقدار یکسانی داشته باشند.

## مثال‌ها

### image map با دو ناحیه

برای دیدن مستندات JavaScript روی طوطی سمت چپ و برای CSS روی طوطی سمت راست کلیک کنید.

#### HTML

```html
<!-- Photo by Juliana e Mariana Amorim on Unsplash -->
<map name="primary">
  <area
    shape="circle"
    coords="75,75,75"
    href="https://developer.mozilla.org/docs/Web/JavaScript"
    target="_blank"
    alt="JavaScript" />
  <area
    shape="circle"
    coords="275,75,75"
    href="https://developer.mozilla.org/docs/Web/CSS"
    target="_blank"
    alt="CSS" />
</map>
<img
  usemap="#primary"
  src="parrots.jpg"
  alt="350 x 150 picture of two parrots" />
```

#### نتیجه

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">دسته‌بندی محتوا (Content categories)</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content">Flow content</a>،
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">phrasing content</a>، محتوای قابل لمس (palpable content).
      </td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز (Permitted content)</th>
      <td>هر عنصر <a href="/en-US/docs/Web/HTML/Guides/Content_categories#transparent_content_model">transparent</a>.</td>
    </tr>
    <tr>
      <th scope="row">حذف تگ (Tag omission)</th>
      <td>هیچ‌کدام؛ هر دو تگ شروع و پایان اجباری هستند.</td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز (Permitted parents)</th>
      <td>هر عنصری که <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">phrasing content</a> را می‌پذیرد.</td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی (Implicit ARIA role)</th>
      <td><a href="https://w3c.github.io/html-aria/#dfn-no-corresponding-role">نقش متناظری ندارد</a></td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز (Permitted ARIA roles)</th>
      <td>هیچ `role` مجاز نیست</td>
    </tr>
    <tr>
      <th scope="row">رابط DOM (DOM interface)</th>
      <td>HTMLMapElement</td>
    </tr>
  </tbody>
</table>

## مشخصات

## سازگاری مرورگر

## همچنین ببینید

- `<a>`
- `<area>`