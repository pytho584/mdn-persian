---
title: "class HTML global attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/class"
translated_by: "n8n + AI"
---

```markdown
ویژگی سراسری **`class`** لیستی از کلاس‌های عنصر است که با [فاصله‌های ASCII](/en-US/docs/Glossary/Whitespace#in_html) از هم جدا می‌شوند.

```html
<p>نقل‌کننده: این شروع نمایشنامه است.</p>

<p class="note editorial">نکته بالا کمی واضح به نظر می‌رسد. حذف/بازنویسی شود؟</p>

<p>نقل‌کننده: باید به شما دوستان هشدار بدهم که این شروع بسیار هیجان‌انگیز است.</p>

<p class="note">[چراغ‌ها روشن می‌شوند و باد می‌وزد؛ کاسپین از سمت راست صحنه وارد می‌شود]</p>
```

```css
.note {
  font-style: italic;
  font-weight: bold;
}

.editorial {
  background: rgb(255 0 0 / 0.25);
  padding: 10px;
}

.editorial::before {
  content: "Editor: ";
}
```

## نحو (Syntax)

ویژگی `class` یک لیست از مقادیر کلاس است که با [فاصله‌های ASCII](/en-US/docs/Glossary/Whitespace#in_html) از هم جدا می‌شوند.

هر مقدار کلاس می‌تواند شامل هر کاراکتر Unicode باشد (به جز فاصله‌های ASCII). با این حال، وقتی در CSS Selectors استفاده می‌شود – چه از طریق JavaScript با APIهایی مثل {{domxref("Document.querySelector()")}} و چه در CSS Stylesheets – مقادیر ویژگی `class` باید [شناسه‌های CSS معتبر](/en-US/docs/Web/CSS/Reference/Values/ident) باشند. یعنی اگر یک مقدار ویژگی `class` شناسه CSS معتبری نباشد (مثلاً `my?class` یا `1234`)، باید قبل از استفاده در یک selector، escape شود – یا با متد {{domxref("CSS.escape_static", "CSS.escape()")}} یا به صورت [دستی](/en-US/docs/Web/CSS/Reference/Values/ident#escaping_characters).

به همین دلیل توصیه می‌شود توسعه‌دهندگان برای ویژگی `class` مقادیری انتخاب کنند که شناسه‌های CSS معتبری باشند و نیازی به escape نداشته باشند.

## توضیحات

کلاس‌ها به CSS و JavaScript امکان می‌دهند عناصر خاصی را از طریق [class selectors](/en-US/docs/Web/CSS/Reference/Selectors/Class_selectors) یا توابعی مانند {{domxref("document.getElementsByClassName()")}} انتخاب کرده و به آن‌ها دسترسی پیدا کنند.

اگرچه مشخصات هیچ الزامی برای نام کلاس‌ها تعیین نمی‌کند، اما توسعه‌دهندگان وب تشویق می‌شوند از نام‌هایی استفاده کنند که هدف معنایی (semantic) عنصر را توصیف می‌کنند، نه ظاهر آن. به عنوان مثال، از `attribute` برای توصیف یک ویژگی استفاده کنید نه `italic`، حتی اگر ممکن است عنصری از این کلاس به صورت _ایتالیک_ نمایش داده شود. نام‌های معنایی حتی اگر ظاهر صفحه تغییر کند، منطقی باقی می‌مانند.

## مشخصات

## سازگاری با مرورگرها

## همچنین ببینید

- همه [ویژگی‌های سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes)
- {{domxref('element.className')}}
- {{domxref('element.classList')}}
- [مقدمه‌ای بر CSS](/en-US/docs/Learn_web_development/Core/Styling_basics)
```