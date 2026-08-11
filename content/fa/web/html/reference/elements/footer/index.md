---
title: "<footer> HTML footer element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/footer"
translated_by: "n8n + AI"
---

# `<footer>` HTML

المان **`<footer>`** در HTML نمایانگر فوتر (پاصفحه) نزدیک‌ترین ancestor (جد) خود است که از نوع محتوای بخش‌بندی (sectioning content) یا ریشهٔ بخش‌بندی (sectioning root) باشد. یک `<footer>` معمولاً شامل اطلاعاتی دربارهٔ نویسندهٔ بخش، داده‌های کپی‌رایت یا پیوندهایی به اسناد مرتبط است.

## Attributes

این المان فقط شامل [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

## نکات استفاده

- اطلاعات نویسنده را در یک المان `<address>` قرار دهید که می‌تواند درون المان `<footer>` گنجانده شود.
- اگر نزدیک‌ترین ancestor از نوع محتوای بخش‌بندی یا ریشهٔ بخش‌بندی، المان `body` باشد، فوتر به کل صفحه اعمال می‌شود.
- المان `<footer>` محتوای بخش‌بندی نیست و بنابراین بخش جدیدی در [outline](/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements) ایجاد نمی‌کند.

## دسترس‌پذیری

قبل از انتشار Safari 13، نقش `contentinfo` از نوع [landmark role](/en-US/docs/Learn_web_development/Core/Accessibility/WAI-ARIA_basics#signpostslandmarks) توسط [VoiceOver](https://help.apple.com/voiceover/info/guide/) به درستی پشتیبانی نمی‌شد. اگر نیاز به پشتیبانی از مرورگرهای قدیمی Safari دارید، `role="contentinfo"` را به المان `footer` اضافه کنید تا landmark به درستی نمایش داده شود.

- مرتبط: [WebKit Bugzilla: 146930 – AX: HTML native elements (header, footer, main, aside, nav) should work the same as ARIA landmarks, sometimes they don't](https://webkit.org/b/146930)

## مثال‌ها

```html
<body>
  <h3>FIFA World Cup top goalscorers</h3>
  <ol>
    <li>Miroslav Klose, 16</li>
    <li>Ronaldo Nazário, 15</li>
    <li>Gerd Müller, 14</li>
  </ol>

  <footer>
    <small>
      Copyright © 2023 Football History Archives. All Rights Reserved.
    </small>
  </footer>
</body>
```

```css
footer {
  text-align: center;
  padding: 5px;
  background-color: #abbaba;
  color: black;
}
```

## خصوصیات عنصر `<footer>`

| ویژگی | توضیحات |
|-------|---------|
| دسته‌بندی محتوا (Content categories) | محتوای جریانی (Flow content)، محتوای قابل لمس (palpable content) |
| محتوای مجاز (Permitted content) | محتوای جریانی، اما بدون فرزند `<footer>` یا `<header>` |
| حذف برچسب (Tag omission) | هیچکدام؛ هر دو برچسب شروع و پایان اجباری هستند |
| والدین مجاز (Permitted parents) | هر عنصری که محتوای جریانی را بپذیرد. توجه داشته باشید که یک عنصر `<footer>` نباید از نوادگان عنصر `<address>`، `<header>` یا `<footer>` دیگری باشد |
| نقش ARIA ضمنی (Implicit ARIA role) | نقش `contentinfo`، یا `generic` اگر از نوادگان عنصر `article`، `aside`، `main`، `nav` یا `section` باشد، یا عنصری با نقش `article`، `complementary`، `main`، `navigation` یا `region` |
| نقش‌های ARIA مجاز (Permitted ARIA roles) | `group`، `presentation` یا `none` |
| رابط DOM (DOM interface) | `HTMLElement` |

## همچنین ببینید

- سایر عناصر مرتبط با بخش‌بندی: `<body>`، `<nav>`، `<article>`، `<aside>`، `<h1>`، `<h2>`، `<h3>`، `<h4>`، `<h5>`، `<h6>`، `<hgroup>`، `<header>`، `<section>`، `<address>`
- [استفاده از بخش‌ها و طرح‌بندی HTML](/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements)
- [نقش Contentinfo در ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/contentinfo_role)