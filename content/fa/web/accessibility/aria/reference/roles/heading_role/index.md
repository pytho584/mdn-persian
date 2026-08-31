---
title: "ARIA: heading role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/heading_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: heading role"
short-title: heading
slug: Web/Accessibility/ARIA/Reference/Roles/heading_role
page-type: aria-role
spec-urls:
  - https://w3c.github.io/aria/#heading
  - https://www.w3.org/WAI/ARIA/apg/practices/structural-roles/#when_to_use_structural_roles
sidebar: accessibilitysidebar
---

نقش `heading` این عنصر را به عنوان عنوان یک صفحه یا بخش تعریف می‌کند و ویژگی [`aria-level`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-level) ساختار بیشتری فراهم می‌کند.

## توضیحات

نقش heading به فناوری‌های کمکی نشان می‌دهد که این عنصر باید مانند یک عنوان رفتار شود. صفحه‌خوان‌ها متن را می‌خوانند و نشان می‌دهند که مانند یک عنوان قالب‌بندی شده است. علاوه بر این، سطح به فناوری‌های کمکی می‌گوید که این عنوان کدام بخش از ساختار صفحه را نشان می‌دهد. عنوان سطح ۱، که با `aria-level="1"` نشان داده می‌شود، معمولاً عنوان اصلی یک صفحه را نشان می‌دهد؛ عنوان سطح ۲، که با `aria-level="2"` تعریف می‌شود، اولین زیربخش را نشان می‌دهد؛ سطح ۳ زیربخشی از آن است و به همین ترتیب.

```html
<div role="heading" aria-level="1">This is a main page heading</div>
```

این کار متن درون `<div>` را به عنوان عنوان اصلی صفحه تعریف می‌کند، که با ویژگی `aria-level` در سطح ۱ قرار می‌گیرد. بهتر است به جای آن از عنصر {{HTMLElement("Heading_Elements", "h1")}} (تا {{HTMLElement("Heading_Elements", "h6")}}) استفاده کنید.

```html
<h1>This is a main page heading</h1>
```

### نقش‌ها، حالت‌ها و ویژگی‌های WAI-ARIA مرتبط

- [`aria-level`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-level)
  - : ویژگی `aria-level` سطح عنوان را در ساختار سند مشخص می‌کند. این ویژگی الزامی است: نویسندگان باید سطح تودرتو مناسب را مشخص کنند تا اطمینان حاصل شود عناصری که `role` آن‌ها `heading` است، در یک طرح کلی منطقی سازماندهی می‌شوند. اگر این ویژگی به اشتباه مشخص نشده باشد، مرورگرها از [مقدار جایگزین ۲](https://w3c.github.io/aria/#authorErrorDefaultValuesTable) استفاده می‌کنند.

### تعاملات صفحه‌کلید

این نقش به هیچ ناوبری ویژه صفحه‌کلید نیاز ندارد. مانند هر عنوان، دادن یک ID به آن اطمینان می‌دهد که بتوان از پیوندهای لنگر به آن ارجاع داد و از این طریق با صفحه‌کلید در دسترس باشد.

### ویژگی‌های جاوااسکریپت مورد نیاز

- کنترل‌کننده‌های رویداد مورد نیاز
  - : هیچ.
- تغییر مقادیر ویژگی
  - : معمولاً لازم نیست، مگر در هنگام درج پویای محتوا. در آن صورت، عنوان‌های تازه‌اضافه‌شده به ویژگی‌های `aria-level` نیاز دارند که مقادیرشان با بقیه ساختار سند سازگار باشد.

> [!NOTE]
> به جای استفاده از یک `<div>` یا `<span>` با نقش `heading` و `aria-level`، از عناصر بومی {{HTMLElement("Heading_Elements", "h1")}} تا {{HTMLElement("Heading_Elements", "h6")}} استفاده کنید تا نشان دهید این متن یک عنوان است و کدام بخش از ساختار را نشان می‌دهد.

## مثال‌ها

مثال زیر یک ساختار صفحه معمولی را نشان می‌دهد.

```html
<div id="container">
  <div role="heading" aria-level="1">The main page heading</div>
  <p>This article is about showing a page structure.</p>
  <div role="heading" aria-level="2">Introduction</div>
  <p>An introductory text.</p>
  <div role="heading" aria-level="2">Chapter 1</div>
  <p>Text</p>
  <div role="heading" aria-level="3">Chapter 1.1</div>
  <p>More text in a sub section.</p>
</div>
```

با این حال، در عوض باید این کار را انجام دهید:

```html
<div id="container">
  <h1>The main page heading</h1>
  <p>This article is about showing a page structure.</p>
  <h2>Introduction</h2>
  <p>An introductory text.</p>
  <h2>Chapter 1</h2>
  <p>Text</p>
  <h3>Chapter 1.1</h3>
  <p>More text in a sub section.</p>
</div>
```

## نکات دسترس‌پذیری

> [!WARNING]
> استفاده از [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) یا [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) محتوای عنوان شما را از فناوری‌های کمکی پنهان می‌کند و به جای عنوان، برچسب را می‌خوانند.

اگر مجبور به استفاده از نقش `heading` و ویژگی [`aria-level`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-level) هستید، از سطح ۶ فراتر نروید تا با HTML سازگار باشید. اگرچه از نظر تئوری می‌توانید بالاتر بروید و برخی صفحه‌خوان‌ها ممکن است از آن پشتیبانی کنند، اما نتایج در ترکیب‌های دیگر مرورگر و صفحه‌خوان ممکن است غیرقابل پیش‌بینی باشد.

## بهترین روش‌ها

بهترین راه برای استفاده از این نقش این است که **اصلاً از آن استفاده نکنید** و در عوض از تگ‌های عنوان بومی {{HTMLElement("Heading_Elements", "h1")}} تا {{HTMLElement("Heading_Elements", "h6")}} همانطور که در مثال بالا نشان داده شده استفاده کنید. نقش `heading` و ویژگی `aria-level` فقط باید برای بازسازی دسترس‌پذیری در کدهای قدیمی استفاده شوند که نمی‌توانید تغییرات عمده‌ای در آن‌ها ایجاد کنید.

به جای استفاده از نقش `heading` در ARIA، از عنصر معنایی HTML استفاده کنید:

| عنصر HTML                              | نقش `heading`                        |
| ----------------------------------------- | ------------------------------------- |
| {{HTMLElement("Heading_Elements", "h1")}} | `<div role="heading" aria-level="1">` |
| {{HTMLElement("Heading_Elements", "h2")}} | `<div role="heading" aria-level="2">` |
| {{HTMLElement("Heading_Elements", "h3")}} | `<div role="heading" aria-level="3">` |
| {{HTMLElement("Heading_Elements", "h4")}} | `<div role="heading" aria-level="4">` |
| {{HTMLElement("Heading_Elements", "h5")}} | `<div role="heading" aria-level="5">` |
| {{HTMLElement("Heading_Elements", "h6")}} | `<div role="heading" aria-level="6">` |

### مزایای اضافه

هیچ.

## مشخصات

{{Specifications}}

## ترتیب تقدم

نقش heading بر معنای بومی عنصری که برای آن استفاده می‌شود غلبه می‌کند. علاوه بر این، ویژگی `aria-level` تعیین می‌کند که چه سطحی از عنوان نمایش داده شود.

## همچنین ببینید

- [`<h1>` تا `<h6>`: عناصر عنوان بخش HTML](/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements)