---
title: "<wbr> HTML line break opportunity element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/wbr"
translated_by: "n8n + AI"
---

عنصر HTML **`<wbr>`** (مخفف word break opportunity) یک نقطهٔ اختیاری برای شکست خط در متن مشخص می‌کند. به عبارت دیگر، جایی درون متن است که مرورگر می‌تواند (در صورت نیاز) خط را بشکند، حتی اگر قوانین عادی شکست‌خط در آن موقعیت شکستی ایجاد نکنند.

```html
<div id="example-paragraphs">
  <p>Fernstraßenbauprivatfinanzierungsgesetz</p>
  <p>Fernstraßen<wbr />bau<wbr />privat<wbr />finanzierungs<wbr />gesetz</p>
  <p>Fernstraßen&shy;bau&shy;privat&shy;finanzierungs&shy;gesetz</p>
</div>
```

```css
#example-paragraphs {
  background-color: white;
  overflow: hidden;
  resize: horizontal;
  width: 9rem;
  border: 2px dashed #999999;
}
```

## ویژگی‌ها (Attributes)

این عنصر فقط شامل [ویژگی‌های سراسری (global attributes)](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

## نکات

`<wbr>` دقیقاً مانند نقطه‌کد `U+200B ZERO-WIDTH SPACE` رفتار می‌کند؛ یعنی از نظر ترتیب دوجهتی (bidi) مانند یک نقطه‌کد `BN` عمل می‌کند و تأثیری بر ترتیب نمایش در راستای راست‌به‌چپ یا چپ‌به‌راست ندارد. به عنوان مثال: `<div dir=rtl>123,<wbr>456</div>` در حالتی که خط شکسته نشود، `123,456` نمایش می‌دهد، نه `456,123`.

به همین دلیل، عنصر `<wbr>` در محل شکست خط، خط تیره (hyphen) اضافه نمی‌کند. اگر می‌خواهید خط تیره فقط در انتهای خط ظاهر شود، از نهاد کاراکتر soft hyphen (`&shy;`) استفاده کنید.

## مثال‌ها

[راهنمای سبک یاهو](https://web.archive.org/web/20121014054923/http://styleguide.yahoo.com/) توصیه می‌کند که URLها را _پیش از_ علامت‌های نگارشی بشکنید تا علامت نگارشی در انتهای خط باقی نماند و خواننده آن را اشتباه با پایان URL نگیرد.

```html
<p>
  http://this<wbr />.is<wbr />.a<wbr />.really<wbr />.long<wbr />.example<wbr />.com/With<wbr />/deeper<wbr />/level<wbr />/pages<wbr />/deeper<wbr />/level<wbr />/pages<wbr />/deeper<wbr />/level<wbr />/pages<wbr />/deeper<wbr />/level<wbr />/pages<wbr />/deeper<wbr />/level<wbr />/pages
</p>
```

### نتیجه

مثال تعاملی بالا در مرورگر نمایش داده می‌شود.

## خلاصهٔ فنی

| ویژگی | مقدار |
|-------|-------|
| **دسته‌بندی محتوا** | [Flow content](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content), [Phrasing content](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) |
| **محتوای مجاز** | خالی (empty) |
| **حذف تگ** | باید تگ شروع داشته باشد و نباید تگ پایانی داشته باشد. |
| **والدین مجاز** | هر عنصری که [Phrasing content](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) را بپذیرد. |
| **نقش ARIA ضمنی** | [نقش متناظری ندارد](https://w3c.github.io/html-aria/#dfn-no-corresponding-role) |
| **نقش‌های ARIA مجاز** | هر نقشی |
| **رابط DOM** | {{domxref("HTMLElement")}} |

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{cssxref("overflow-wrap")}}
- {{cssxref("word-break")}}
- {{cssxref("hyphens")}}
- عنصر {{HTMLElement("br")}}