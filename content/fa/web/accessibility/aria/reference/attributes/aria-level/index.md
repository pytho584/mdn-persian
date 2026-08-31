---
title: "ARIA: aria-level attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-level"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-level attribute"
short-title: aria-level
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-level
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-level
sidebar: accessibilitysidebar
---

ویژگی `aria-level` سطح سلسله‌مراتبی یک عنصر را در یک ساختار تعریف می‌کند.

## توضیحات

سطوح سلسله‌مراتب در عنوان‌ها، درخت‌ها، شبکه‌های تودرتو، فهرست‌های برگه‌ای تودرتو و موارد دیگر ظاهر می‌شوند. اگر نسب‌های DOM به‌دقت سطح را نشان ندهند، باید از ویژگی `aria-level` برای تعریف سطح سلسله‌مراتبی عناصر در ساختارهای سلسله‌مراتبی آن‌ها استفاده کرد. سطوح با عمق افزایش می‌یابند. مقدار `aria-level` یک عدد صحیح بزرگ‌تر یا مساوی با `1` است.

وقتی صحبت از عنوان‌ها در ساختار یک سند می‌شود، می‌توانید عنوان‌های سطح اول، سطح دوم، سطح سوم و غیره داشته باشید. در درخت‌ها، عنصر ریشه، فرزندان آن، فرزندان فرزندان (یا نوه‌ها) و غیره دارید.

ویژگی `aria-level` سلسله‌مراتب را در اختیار فناوری‌های کمکی قرار می‌دهد تا بتوان آن را به کاربران منتقل کرد. مانند همه ویژگی‌های ARIA، تأثیری بر عامل کاربر ندارد و بنابراین تأثیری بر تعیین ساختار سند توسط عامل کاربر ندارد.

اگر نسب‌های DOM سطح را به‌دقت نشان دهند، عامل کاربر می‌تواند سطح یک مورد را از ساختار سند محاسبه کند، که این نه‌تنها `aria-level` را اضافی می‌کند بلکه خطر ایجاد اطلاعات نادرست را نیز به همراه دارد. `aria-level` در واقع فقط باید برای ارائه نشانه صریح سطح زمانی که محاسبه آن از ساختار سند ممکن نیست استفاده شود. آزمایش کنید که آیا این ویژگی مورد نیاز است یا خیر. اگر عامل کاربر بتواند سطح را محاسبه کند، بهتر است ویژگی `aria-level` حذف شود.

### با نقش `heading`

ویژگی `aria-level` یک ویژگی الزامی برای نقش [`heading`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/heading_role) است که به فناوری‌های کمکی نشان می‌دهد که عنصر باید به عنوان یک عنوان در نظر گرفته شود. `<div role="heading" aria-level="1">` عنصر `<div>` را به عنوان عنوان اصلی صفحه تعریف می‌کند. یک عنوان سطح 2 که با `aria-level="2"` تعریف می‌شود، اولین زیربخش است، سطح 3 زیربخشی از آن و غیره.

```html
<div role="heading" aria-level="3">Heading for this sub section</div>
```

در عوض بهتر است از عناصر {{htmlelement("Heading_Elements", "h1")}} تا {{htmlelement("Heading_Elements", "h6")}} استفاده کنید.

### در نقش `treegrid`

در مورد [`treegrid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treegrid_role)، ویژگی `aria-level` روی عناصر دارای نقش [`row`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role) پشتیبانی می‌شود، نه روی عناصر دارای نقش [`gridcell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role). ردیف‌ها به عنوان گره‌های برگ در جهت عمودی شبکه عمل می‌کنند. خانه‌های شبکه گره‌های برگ در جهت افقی هر ردیف هستند. `Aria-level` روی سلول‌های داخل ردیف‌ها پشتیبانی نمی‌شود. بنابراین، در شبکه‌های درختی، ویژگی `aria-level` روی عنصر دارای نقش `row` اعمال می‌شود.

اگر به دلیل بارگذاری پویا هنگام حرکت تمرکز کاربر یا اسکرول در درخت، مجموعه کاملی از گره‌های موجود در DOM وجود نداشته باشد، هر گره شامل `aria-level`، [`aria-setsize`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-setsize) و [`aria-posinset`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-posinset) است.

## مقادیر

- `<integer>`
  - : یک عدد صحیح بزرگ‌تر یا مساوی با 1

## رابط‌های مرتبط

- {{domxref("Element.ariaLevel")}}
  - : ویژگی [`ariaLevel`](/en-US/docs/Web/API/Element/ariaLevel) که بخشی از رابط {{domxref("Element")}} است، مقدار ویژگی `aria-level` را منعکس می‌کند.
- {{domxref("ElementInternals.ariaLevel")}}
  - : ویژگی [`ariaLevel`](/en-US/docs/Web/API/ElementInternals/ariaLevel) که بخشی از رابط {{domxref("ElementInternals")}} است، مقدار ویژگی `aria-level` را منعکس می‌کند.

## نقش‌های مرتبط

استفاده شده در نقش‌ها:

- [`associationlistitemkey`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`comment`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/comment_role)
- [`heading`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/heading_role)
- [`row`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role)

## مشخصات

{{Specifications}}

## همچنین ببینید

- [`<h1>` تا `<h6>`: عناصر عنوان بخش HTML](/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements) ({{htmlelement("Heading_Elements", "h1")}}، {{htmlelement("Heading_Elements", "h2")}}، {{htmlelement("Heading_Elements", "h3")}}، {{htmlelement("Heading_Elements", "h4")}}، {{htmlelement("Heading_Elements", "h5")}} و {{htmlelement("Heading_Elements", "h6")}})