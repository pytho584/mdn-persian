---
title: "<aside> HTML aside element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/aside"
translated_by: "n8n + AI"
---

عنصر HTML `<aside>` نمایانگر بخشی از یک سند است که محتوای آن فقط به‌طور غیرمستقیم با محتوای اصلی سند مرتبط است. معمولاً از `<aside>` برای نمایش نوار کناری (sidebar) یا جعبه‌های نقل‌قول (call-out box) استفاده می‌شود.

```html interactive-example
<p>
  Salamanders are a group of amphibians with a lizard-like appearance, including
  short legs and a tail in both larval and adult forms.
</p>

<aside>
  <p>The Rough-skinned Newt defends itself with a deadly neurotoxin.</p>
</aside>

<p>
  Several species of salamander inhabit the temperate rainforest of the Pacific
  Northwest, including the Ensatina, the Northwestern Salamander and the
  Rough-skinned Newt. Most salamanders are nocturnal, and hunt for insects,
  worms and other small creatures.
</p>
```

```css interactive-example
aside {
  width: 40%;
  padding-left: 0.5rem;
  margin-left: 0.5rem;
  float: right;
  box-shadow: inset 5px 0 5px -5px #29627e;
  font-style: italic;
  color: #29627e;
}

aside > p {
  margin: 0.5rem;
}
```

## ویژگی‌ها (Attributes)

این عنصر فقط شامل [global attributes](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

## نکات استفاده

- از عنصر `<aside>` برای مشخص کردن متن داخل پرانتز استفاده نکنید، چون این نوع متن جزئی از جریان اصلی محتوا محسوب می‌شود.

## مثال‌ها

### استفاده از `<aside>`

این مثال از `<aside>` برای علامت‌گذاری یک پاراگراف در یک مقاله استفاده می‌کند. این پاراگراف فقط به‌طور غیرمستقیم با محتوای اصلی مقاله مرتبط است:

```html
<article>
  <p>
    The Disney movie <cite>The Little Mermaid</cite> was first released to
    theatres in 1989.
  </p>
  <aside>
    <p>The movie earned $87 million during its initial release.</p>
  </aside>
  <p>More info about the movie…</p>
</article>
```

| ویژگی | مقدار |
|-------|-------|
| دسته‌بندی محتوا (Content categories) | [Flow content](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content)، [sectioning content](/en-US/docs/Web/HTML/Guides/Content_categories#sectioning_content)، [palpable content](/en-US/docs/Web/HTML/Guides/Content_categories#palpable_content) |
| محتوای مجاز (Permitted content) | [Flow content](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content) |
| حذف تگ (Tag omission) | هیچکدام؛ تگ شروع و پایان هر دو اجباری هستند. |
| والدین مجاز (Permitted parents) | هر عنصری که [Flow content](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content) را بپذیرد. توجه: عنصر `<aside>` نباید از نوادگان عنصر `<address>` باشد. |
| نقش ARIA ضمنی (Implicit ARIA role) | [`complementary`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/complementary_role) |
| نقش‌های ARIA مجاز (Permitted ARIA roles) | [`feed`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/feed_role)، [`none`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/none_role)، [`note`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/note_role)، [`presentation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role)، [`region`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/region_role)، [`search`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/search_role) |
| رابط DOM (DOM interface) | `HTMLElement` |

## مشخصات

## سازگاری با مرورگر

## بیشتر بخوانید

- سایر عناصر مرتبط با بخش‌بندی: `<body>`، `<article>`، `<section>`، `<nav>`، `<h1>`، `<h2>`، `<h3>`، `<h4>`، `<h5>`، `<h6>`، `<hgroup>`، `<header>`، `<footer>`، `<address>`
- [Using HTML sections and outlines](/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements)
- [ARIA: Complementary role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/complementary_role)