---
title: "<rt> HTML ruby text element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/rt"
translated_by: "n8n + AI"
---

المان `<rt>` در HTML بخش متنی یک حاشیه‌نویسی ruby را مشخص می‌کند. این حاشیه‌نویسی معمولاً برای نمایش تلفظ، ترجمه یا نویسه‌گردانی در نوشتارهای شرق آسیا استفاده می‌شود. المان `<rt>` همیشه باید داخل یک المان `<ruby>` قرار بگیرد.

مثال زیر (نمونه تعاملی) کاربرد `<rt>` را نشان می‌دهد:

```html
<ruby>
  漢 <rp>(</rp><rt>kan</rt><rp>)</rp> 字 <rp>(</rp><rt>ji</rt><rp>)</rp>
</ruby>
```

```css
ruby {
  font-size: 2em;
}
```

برای مثال‌های بیشتر، مقاله مربوط به المان `<ruby>` را ببینید.

## ویژگی‌ها (Attributes)

این المان فقط [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) را پشتیبانی می‌کند.

## مثال‌ها

### استفاده از حاشیه‌نویسی ruby

این مثال نویسه‌گردانی روماجی (Romaji) برای نویسه‌های کانجی داخل المان `<ruby>` ارائه می‌دهد:

```html
<ruby> 漢 <rt>Kan</rt> 字 <rt>ji</rt> </ruby>
```

```css
body {
  font-size: 22px;
}
```

#### نتیجه

مثال بالا در مرورگر به صورت یک خط متن با حاشیه‌نویسی کوچک در بالای نویسه‌ها نمایش داده می‌شود.

## خلاصه فنی

<table class="properties">
  <tbody>
    <tr>
      <th scope="row">دسته‌بندی محتوا (Content categories)</th>
      <td>هیچکدام.</td>
    </tr>
    <tr>
      <th scope="row">محتوای مجاز</th>
      <td>
        <a href="/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content">محتواهای جمله‌ای (Phrasing content)</a>.
      </td>
    </tr>
    <tr>
      <th scope="row">حذف تگ</th>
      <td>
        اگر المان <code>&#x3C;rt></code> بلافاصله بعد از یک المان <code>&#x3C;rt></code> یا {{HTMLElement("rp")}} قرار گیرد، یا اگر محتوای دیگری در المان والد وجود نداشته باشد، می‌توان تگ پایانی را حذف کرد.
      </td>
    </tr>
    <tr>
      <th scope="row">المان‌های والد مجاز</th>
      <td>یک المان {{HTMLElement("ruby")}}.</td>
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
      <td>{{domxref("HTMLElement")}}</td>
    </tr>
  </tbody>
</table>

## جستارهای وابسته

- {{HTMLElement("ruby")}}
- {{HTMLElement("rp")}}
- {{HTMLElement("rb")}}
- {{HTMLElement("rtc")}}
- {{CSSXRef("text-transform", "text-transform: full-size-kana")}}
- [ماژول CSS ruby layout](/en-US/docs/Web/CSS/Guides/Ruby_layout)