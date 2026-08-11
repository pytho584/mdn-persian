---
title: "<rp> HTML ruby fallback parenthesis element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/rp"
translated_by: "n8n + AI"
---

عنصر **`<rp>`** در HTML برای ارائهٔ پرانتزهای جایگزین (fallback) در مرورگرهایی استفاده می‌شود که از نمایش حاشیه‌نویسی‌های ruby با عنصر {{HTMLElement("ruby")}} پشتیبانی نمی‌کنند. هر عنصر `<rp>` باید یکی از پرانتزهای باز یا بسته‌ای را در بر بگیرد که دور عنصر {{HTMLElement("rt")}} (حاوی متن حاشیه‌نویسی) قرار می‌گیرند.

```html interactive-example
<ruby>
  漢 <rp>(</rp><rt>kan</rt><rp>)</rp> 字 <rp>(</rp><rt>ji</rt><rp>)</rp>
</ruby>
```

```css interactive-example
ruby {
  font-size: 2em;
}
```

## ویژگی‌ها

این عنصر فقط شامل [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

## نکات استفاده

- حاشیه‌نویسی‌های ruby برای نمایش تلفظ نویسه‌های شرق آسیا به کار می‌روند، مثلاً فوریگانای ژاپنی یا بُپوموفوی تایوانی. عنصر `<rp>` در مواقعی استفاده می‌شود که مرورگر از عنصر {{HTMLElement("ruby")}} پشتیبانی نمی‌کند؛ محتوای `<rp>` مشخص می‌کند که چه چیزی باید نمایش داده شود تا وجود حاشیه‌نویسی ruby را نشان دهد – معمولاً پرانتز.

## مثال‌ها

### استفاده از حاشیه‌نویسی ruby

در این مثال، معادل روماجی هر نویسه با حاشیه‌نویسی ruby نمایش داده شده است.

```html
<ruby>
  漢 <rp>(</rp><rt>Kan</rt><rp>)</rp> 字 <rp>(</rp><rt>ji</rt><rp>)</rp>
</ruby>
```

```css hidden
body {
  font-size: 22px;
}
```

#### نتیجه

مثال تعاملی بالا را ببینید.

برای نمونه‌های بیشتر به مقالهٔ عنصر {{HTMLElement("ruby")}} مراجعه کنید.

### بدون پشتیبانی از ruby

اگر مرورگر شما از حاشیه‌نویسی ruby پشتیبانی نکند، خروجی به این شکل دیده می‌شود:

```html hidden
漢 (Kan) 字 (ji)
```

```css hidden
body {
  font-size: 22px;
}
```

(مثال تعاملی در صورت عدم پشتیبانی)

## خلاصهٔ فنی

| ویژگی | مقدار |
|------|-------|
| [دسته‌بندی محتوا](/en-US/docs/Web/HTML/Guides/Content_categories) | هیچ‌کدام |
| محتوای مجاز | متن |
| حذف تگ | تگ پایان را می‌توان حذف کرد اگر عنصر بلافاصله با {{HTMLElement("rt")}} یا یک `<rp>` دیگر دنبال شود، یا اگر محتوای دیگری در عنصر والد وجود نداشته باشد. |
| والد مجاز | یک عنصر {{HTMLElement("ruby")}}. `<rp>` باید بلافاصله قبل یا بعد از یک عنصر {{HTMLElement("rt")}} قرار گیرد. |
| نقش ARIA ضمنی | [نقش متناظری وجود ندارد](https://w3c.github.io/html-aria/#dfn-no-corresponding-role) |
| نقش‌های ARIA مجاز | هر کدام |
| رابط DOM | {{domxref("HTMLElement")}} |

## مشخصات

(مشخصات در نسخهٔ اصلی)

## سازگاری مرورگر

(جدول سازگاری در نسخهٔ اصلی)

## همچنین ببینید

- {{HTMLElement("ruby")}}
- {{HTMLElement("rt")}}
- {{HTMLElement("rb")}}
- {{HTMLElement("rtc")}}
- [ماژول CSS ruby layout](/en-US/docs/Web/CSS/Guides/Ruby_layout)