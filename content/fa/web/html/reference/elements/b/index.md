---
title: "<b> HTML bring attention to element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/b"
translated_by: "n8n + AI"
---

# `<b>` عنصر HTML برای جلب توجه

element **`<b>`** در [HTML](/en-US/docs/Web/HTML) برای جلب توجه خواننده به محتوای خود استفاده می‌شود؛ محتوایی که اهمیت ویژه‌ای ندارد. این element قبلاً با نام Boldface شناخته می‌شد و هنوز هم اکثر browserها متن را به صورت bold نمایش می‌دهند. با این حال، نباید از `<b>` برای استایل‌دهی به متن یا نشان دادن اهمیت استفاده کنید. اگر می‌خواهید متنی bold داشته باشید، از ویژگی CSS [`font-weight`](/en-US/docs/Web/CSS/font-weight) استفاده کنید و اگر می‌خواهید اهمیت ویژه یک element را نشان دهید، از element [`<strong>`](/en-US/docs/Web/HTML/Element/strong) استفاده کنید.

## Attributes

این element فقط [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes) را شامل می‌شود.

## نکات استفاده

- از `<b>` برای مواردی مانند کلمات کلیدی در یک خلاصه، نام محصولات در یک نقد، یا سایر بخش‌های متنی که نمایش معمول آن‌ها bold است استفاده کنید (بدون اینکه اهمیت ویژه‌ای داشته باشند).
- element `<b>` را با [`<strong>`](/en-US/docs/Web/HTML/Element/strong)، [`<em>`](/en-US/docs/Web/HTML/Element/em) یا [`<mark>`](/en-US/docs/Web/HTML/Element/mark) اشتباه نگیرید. element `<strong>` متنی با _اهمیت_ خاص را نشان می‌دهد، `<em>` روی متن تأکید (emphasis) می‌گذارد و element `<mark>` متنی با _ارتباط_ معین را نشان می‌دهد. element `<b>` چنین اطلاعات معنایی ویژه‌ای را منتقل نمی‌کند؛ فقط وقتی از آن استفاده کنید که هیچ‌کدام از موارد دیگر مناسب نباشند.
- به همین ترتیب، عنوان‌ها و تیترها را با `<b>` مشخص نکنید. برای این منظور از تگ‌های [`h1`](/en-US/docs/Web/HTML/Element/Heading_Elements) تا [`h6`](/en-US/docs/Web/HTML/Element/Heading_Elements) استفاده کنید. علاوه بر این، استایل‌شیت‌ها می‌توانند استایل پیش‌فرض این elementها را تغییر دهند؛ در نتیجه این elementها لزوماً به صورت bold نمایش داده نمی‌شوند.
- بهتر است از attribute [`class`](/en-US/docs/Web/HTML/Reference/Global_attributes/class) روی element `<b>` استفاده کنید تا اطلاعات معنایی بیشتری در صورت نیاز منتقل شود (مثلاً `<b class="lead">` برای جمله اول یک پاراگراف). این کار مدیریت موارد استفاده متعدد `<b>` را در صورت تغییر نیازهای استایلی آسان‌تر می‌کند، بدون اینکه نیاز به تغییر همه کاربردهای آن در HTML باشد.
- از نظر تاریخی، element `<b>` برای bold کردن متن استفاده می‌شد. اطلاعات استایلی از HTML4 به بعد منسوخ (deprecated) شده است، بنابراین معنای element `<b>` تغییر کرده است.
- اگر استفاده از element `<b>` هدف معنایی خاصی ندارد، برای bold کردن متن از ویژگی CSS [`font-weight`](/en-US/docs/Web/CSS/font-weight) با مقدار `"bold"` استفاده کنید.

## مثال‌ها

```html
<p>
  This article describes several <b class="keywords">text-level</b> elements. It
  explains their usage in an <b class="keywords">HTML</b> document.
</p>
Keywords are displayed with the default style of the
<b>element, likely in bold.</b>
```

## خلاصه فنی

## ویژگی‌ها

| دسته‌بندی محتوا (Content categories) | [Flow content](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#flow_content) ، [phrasing content](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) ، palpable content |
|--------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| محتوای مجاز                          | [Phrasing content](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content)                                                                                                                                    |
| حذف تگ (Tag omission)                | هیچکدام؛ تگ شروع و پایان اجباری هستند.                                                                                                                                                                                                             |
| والدین مجاز                          | هر عنصری که [phrasing content](https://developer.mozilla.org/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) را بپذیرد.                                                                                                            |
| نقش ARIA پیش‌فرض (Implicit ARIA role) | `<a href="https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/generic_role">generic</a>`                                                                                                                               |
| نقش‌های ARIA مجاز                    | هر نقش                                                                                                                                                                                                                                              |
| رابط DOM (DOM interface)             | `HTMLElement`                                                                                                                                                                                                                                       |

## همچنین ببینید

- سایر عناصر مرتبط با معناشناسی سطح متن:  
  `<a>` ، `<em>` ، `<strong>` ، `<small>` ، `<cite>` ، `<q>` ، `<dfn>` ، `<abbr>` ، `<time>` ، `<code>` ، `<var>` ، `<samp>` ، `<kbd>` ، `<sub>` ، `<sup>` ، `<i>` ، `<mark>` ، `<ruby>` ، `<rp>` ، `<rt>` ، `<bdo>` ، `<span>` ، `<br>` ، `<wbr>`
- [Using `<b>` and `<i>` elements (W3C)](https://www.w3.org/International/questions/qa-b-and-i-tags)