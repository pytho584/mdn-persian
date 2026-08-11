---
title: "<caption> HTML table caption element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/caption"
translated_by: "n8n + AI"
---

عنصر `<caption>` در HTML عنوان یا شرح یک جدول را مشخص می‌کند. این عنوان به جدول یک **accessible name** (نام قابل دسترس) یا **accessible description** (توضیح قابل دسترس) می‌دهد.

```html interactive-example
<table>
  <caption>
    He-Man and Skeletor facts
  </caption>
  <tbody>
    <tr>
      <td></td>
      <th scope="col" class="heman">He-Man</th>
      <th scope="col" class="skeletor">Skeletor</th>
    </tr>
    <tr>
      <th scope="row">Role</th>
      <td>Hero</td>
      <td>Villain</td>
    </tr>
    <tr>
      <th scope="row">Weapon</th>
      <td>Power Sword</td>
      <td>Havoc Staff</td>
    </tr>
    <tr>
      <th scope="row">Dark secret</th>
      <td>Expert florist</td>
      <td>Cries at romcoms</td>
    </tr>
  </tbody>
</table>
```

```css interactive-example
caption {
  caption-side: bottom;
  padding: 10px;
  font-weight: bold;
}

table {
  border-collapse: collapse;
  border: 2px solid rgb(140 140 140);
  font-family: sans-serif;
  font-size: 0.8rem;
  letter-spacing: 1px;
}

th,
td {
  border: 1px solid rgb(160 160 160);
  padding: 8px 10px;
}

th {
  background-color: rgb(230 230 230);
}

td {
  text-align: center;
}

tr:nth-child(even) td {
  background-color: rgb(250 250 250);
}

tr:nth-child(odd) td {
  background-color: rgb(240 240 240);
}

.heman {
  font:
    1.4rem "molot",
    sans-serif;
  text-shadow:
    1px 1px 1px white,
    2px 2px 1px black;
}

.skeletor {
  font:
    1.7rem "rapscallion",
    fantasy;
  letter-spacing: 3px;
  text-shadow:
    1px 1px 0 white,
    0 0 9px black;
}
```

## Attributes

این عنصر شامل [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes) می‌شود.

### ویژگی‌های منسوخ (Deprecated)

ویژگی‌های زیر منسوخ شده‌اند و نباید استفاده شوند. در اینجا فقط برای مرجع هنگام به‌روزرسانی کدهای قدیمی و برای اطلاع تاریخی مستند شده‌اند.

- `align` {{deprecated_inline}}
  - : مشخص می‌کند caption در کدام سمت جدول نمایش داده شود. مقادیر ممکن (enumerated) عبارتند از: `left`, `top`, `right`, یا `bottom`. به جای این ویژگی از خصوصیات CSS {{cssxref("caption-side")}} و {{cssxref("text-align")}} استفاده کنید.

## نکات استفاده

- اگر از `<caption>` استفاده می‌کنید، باید اولین فرزند عنصر والد یعنی {{htmlelement("table")}} باشد.
- وقتی یک `<table>` داخل {{HTMLElement("figure")}} قرار می‌گیرد و تنها محتوای آن `<figure>` است، بهتر است به جای `<caption>` داخل `<table>`، از {{HTMLElement("figcaption")}} برای `<figure>` استفاده کنید.
- هر {{cssxref("background-color")}} که به جدول اعمال شود، روی caption آن تأثیر نخواهد داشت. اگر می‌خواهید پس‌زمینه یکسانی پشت هر دو باشد، `background-color` را مستقیماً به عنصر `<caption>` اضافه کنید.

## مثال

برای مشاهده یک مثال کامل از جدول با استانداردها و بهترین روش‌ها، به {{HTMLElement("table")}} مراجعه کنید.

### جدول به همراه caption

این مثال یک جدول ساده را نشان می‌دهد که شامل یک caption توصیف‌کننده داده‌های ارائه‌شده است.

چنین «عنوانی» برای کاربرانی که صفحه را سریع مرور می‌کنند مفید است، و به‌ویژه برای کاربران کم‌بینا سودمند است؛ زیرا به آن‌ها امکان می‌دهد بدون نیاز به screen reader برای خواندن محتوای سلول‌ها و فهمیدن موضوع جدول، به‌سرعت ارتباط جدول را تشخیص دهند.

#### HTML

یک عنصر `<caption>` به عنوان اولین فرزند {{HTMLElement("table")}} استفاده شده است، با متن مشابه یک عنوان که داده‌های جدول را توصیف می‌کند. سه ردیف (ردیف اول شامل سرستون‌ها) با دو ستون با استفاده از عناصر {{HTMLElement("tr")}}، {{HTMLElement("th")}} و {{HTMLElement("td")}} پس از `<caption>` ایجاد شده‌اند.

```html
<table>
  <caption>
    آدرس‌های ایمیل ورود کاربران
  </caption>
  <thead>
    <tr>
      <th>نام کاربری</th>
      <th>ایمیل</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>user1</td>
      <td>user1@example.com</td>
    </tr>
    <tr>
      <td>user2</td>
      <td>user2@example.com</td>
    </tr>
  </tbody>
</table>
```

#### CSS

چند خط CSS ساده برای تراز و برجسته‌سازی `<caption>` به کار رفته است.

```css
caption {
  caption-side: top;
  text-align: left;
  padding-bottom: 10px;
  font-weight: bold;
}
```

```css hidden
table {
  border-collapse: collapse;
  border: 2px solid rgb(140 140 140);
  font-family: sans-serif;
  font-size: 0.8rem;
  letter-spacing: 1px;
}

th,
td {
  border: 1px solid rgb(160 160 160);
  padding: 8px 10px;
}

th {
  background-color: rgb(230 230 230);
}

td {
  text-align: center;
}
```

#### نتیجه

(نتیجه در اینجا نمایش داده می‌شود)

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories"
          >دسته‌بندی محتوا</a
        >
      </th>
      <td>هیچ‌کدام.</td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#flow_content"
          >محتوای جریانی (Flow content)</a
        >.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>
        تگ بسته شدن می‌تواند حذف شود اگر بلافاصله بعد از آن فضای خالی ASCII یا یک کامنت قرار نداشته باشد.
      </td>
    </tr>
    <tr>
      <th scope="row">والدین مجاز</th>
      <td>
        یک عنصر {{HTMLElement("table")}} به عنوان اولین فرزند خود.
      </td>
    </tr>
    <tr>
      <th scope="row">نقش ARIA ضمنی</th>
      <td>
        <code
          ><a href="/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles#structural_roles_with_html_equivalents">caption</a
          ></code
        >
      </td>
    </tr>
    <tr>
      <th scope="row">نقش‌های ARIA مجاز</th>
      <td>هیچ <code>role</code> مجاز نیست</td>
    </tr>
    <tr>
      <th scope="row">رابط DOM</th>
      <td>{{domxref("HTMLTableCaptionElement")}}</td>
    </tr>
  </tbody>
</table>

## مشخصات فنی

(مشخصات فنی در اینجا قرار می‌گیرد)

## سازگاری مرورگرها

(جدول سازگاری مرورگرها در اینجا قرار می‌گیرد)

## همچنین ببینید

- [یادگیری: مبانی جدول HTML](/en-US/docs/Learn_web_development/Core/Structuring_content/HTML_table_basics)
- {{HTMLElement("col")}}, {{HTMLElement("colgroup")}}, {{HTMLElement("table")}}, {{HTMLElement("tbody")}}, {{HTMLElement("td")}}, {{HTMLElement("tfoot")}}, {{HTMLElement("th")}}, {{HTMLElement("thead")}}, {{HTMLElement("tr")}}: سایر عناصر مرتبط با جدول
- {{cssxref("caption-side")}}: ویژگی CSS برای موقعیت‌دهی `<caption>` نسبت به والد {{HTMLElement("table")}} خود
- {{cssxref("text-align")}}: ویژگی CSS برای تراز افقی محتوای متنی `<caption>`</summary>