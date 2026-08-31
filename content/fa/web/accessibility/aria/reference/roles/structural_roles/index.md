---
title: "ARIA: document structural roles"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles"
translated_by: "n8n + AI"
---

---
title: "ARIA: document structural roles"
short-title: Structural
slug: Web/Accessibility/ARIA/Reference/Roles/structural_roles
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#document_structure_roles
sidebar: accessibilitysidebar
---

نقش‌های ساختار سند ARIA برای ارائه توصیف ساختاری از یک بخش از محتوا به کار می‌روند.

نقش‌های ساختاری ARIA در ابتدا به عنوان پلی برای اطلاع‌رسانی به فناوری‌های کمکی درباره عناصر HTML5 که هنوز در مرورگرها به‌طور کامل پشتیبانی نمی‌شدند، ایجاد شدند. برخی از نقش‌ها، مانند `presentation`، `toolbar` و `tooltip`، در مواردی که عناصر بومی HTML معادل وجود ندارند، اطلاعاتی درباره ساختار سند به فناوری‌های کمکی ارائه می‌دهند. سایر نقش‌ها، از جمله آن‌هایی که در جدول زیر فهرست شده‌اند، ضروری نیستند، زیرا عناصر معنایی HTML با همان معانی وجود دارند. در بسیاری از موارد، این عناصر HTML معادل از ابتدا پشتیبانی شده‌اند.

> [!WARNING]
> همه این نقش‌های ساختاری دارای معادل‌های معنایی HTML هستند. آن‌ها برای کامل بودن مستندات در اینجا گنجانده شده‌اند. بهتر است توسط نویسندگان وب استفاده نشوند. در عوض، عناصر معنایی HTML را انتخاب کنید.

برخی از نقش‌های ساختاری، مانند [`suggestion`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/suggestion_role)، معادل HTML ندارند و بنابراین مستندات جداگانه‌ای دارند. برخی از نقش‌های ساختاری با معادل HTML، مانند [`heading`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/heading_role)، الزامات ویژگی ARIA دارند. آن‌ها در زیر با پیوند به مستندات نقش جداگانه‌شان فهرست شده‌اند.

بیشتر نقش‌های زیر هرگز ضروری نبودند، اما برای کامل بودن به ARIA اضافه شدند. ما نیز برای کامل بودن آن‌ها را در اینجا گنجانده‌ایم.

## نقش‌های ساختاری با معادل‌های HTML

نقش‌های ساختاری با معادل‌های HTML در زیر فهرست شده‌اند:

| نقش ARIA و توضیحات | معادل HTML |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **`associationlist`** <br> فقط شامل فرزندان `associationlistitemkey` و خواهر/برادرشان `associationlistitemvalue` است. | {{HTMLElement('dl')}} |
| **`associationlistitemkey`** <br/> باید در یک `associationlist` قرار گیرد. | {{HTMLElement('dt')}} |
| **`associationlistitemvalue`** <br/> همیشه یک خواهر/برادر است که پس از `associationlistitemkey` می‌آید. | {{HTMLElement('dd')}} |
| **`blockquote`** <br/> بخشی از محتوا که از منبع دیگری نقل قول شده است. | {{HTMLElement('blockquote')}} |
| **`caption`** <br>محتوای قابل مشاهده که یک `figure`، `table`، `grid` یا `treegrid` را نام‌گذاری می‌کند و همچنین ممکن است آن را توصیف کند.<br/> فقط در این ۴ نقش یافت می‌شود. شناسه (`id`) این عنوان معمولاً توسط ویژگی `aria-labelledby` یک `figure`، `grid`، `table` یا `treegrid` ارجاع داده می‌شود.<br/> ویژگی‌های ممنوع: `aria-label` و `aria-labelledby`. | {{HTMLElement('caption')}} <br/> {{HTMLElement('figcaption')}} |
| **`code`** <br/> بخشی که نمایانگر یک قطعه از کد رایانه‌ای است. <br/> ویژگی‌های ممنوع: `aria-label` و `aria-labelledby`. | {{HTMLElement('code')}} |
| **`deletion`** <br/>محتوایی که به عنوان حذف‌شده علامت خورده یا برای حذف پیشنهاد شده است.<br/> ویژگی‌های ممنوع: `aria-label` و `aria-labelledby`. | {{HTMLElement('del')}} |
| **`emphasis`** <br/> برای تأکید یا برجسته‌کردن محتوا استفاده می‌شود، اما برای نشان دادن اهمیت نیست.<br/>ویژگی‌های ممنوع: `aria-label` و `aria-labelledby`. | {{HTMLElement('em')}} |
| [`figure`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/figure_role) <br/>ظرفی برای یک سند گرافیکی، تصاویر، قطعات کد یا متن مثال. | {{HTMLElement('figure')}} |
| [`heading`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/heading_role) <br/> یک عنوان برای بخشی از صفحه.<br/>ویژگی `aria-level` برای نشان دادن سطح تودرتویی الزامی است.<br/>برای اطلاعات بیشتر، [نقش `heading`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/heading_role) را ببینید. | {{HTMLElement("Heading_Elements", "h1")}}, {{HTMLElement("Heading_Elements", "h2")}}, {{HTMLElement("Heading_Elements", "h3")}}, {{HTMLElement("Heading_Elements", "h4")}}, {{HTMLElement("Heading_Elements", "h5")}}, و {{HTMLElement("Heading_Elements", "h6")}} |
| **`image`** <br/>ظرفی برای مجموعه‌ای از عناصر که یک تصویر را تشکیل می‌دهند. مترادفی برای نقش `img`. | {{HTMLElement('img')}} |
| [`img`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/img_role) <br/>ظرفی برای مجموعه‌ای از عناصر که یک تصویر را تشکیل می‌دهند.<br/>نام قابل دسترس الزامی است.<br/>برای اطلاعات بیشتر، [نقش `img`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/img_role) را ببینید. | {{HTMLElement('img')}} |
| **`insertion`** <br/>محتوایی که به عنوان اضافه‌شده علامت خورده یا محتوایی که برای افزودن پیشنهاد می‌شود.<br/> ویژگی‌های ممنوع: `aria-label` و `aria-labelledby`. | {{HTMLElement('ins')}} |
| [`list`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/list_role)<br/>بخشی که شامل عناصر `listitem` است.<br/> برای اطلاعات بیشتر، [نقش `list`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/list_role) را ببینید | {{HTMLElement('ol')}}<br/>{{HTMLElement('ul')}} |
| [`listitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listitem_role)<br/>یک مورد واحد در یک `list` یا `directory`.<br/>باید در یک `list` (مانند `<li>`) قرار گیرد.<br>برای اطلاعات بیشتر، [نقش `listitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listitem_role) را ببینید. | {{HTMLElement('li')}} |
| [`mark`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/mark_role)<br/>برای اهداف ارجاع یا یادداشت علامت‌گذاری یا برجسته شده است.<br>برای اطلاعات بیشتر، [نقش `mark`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/mark_role) را ببینید. | {{HTMLElement('mark')}} |
| [`meter`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/meter_role) <br/>یک اندازه‌گیری عددی در یک محدوده شناخته‌شده، یا یک مقدار کسری.<br/>نام قابل دسترس الزامی است. `aria-valuenow` الزامی است.<br/>برای اطلاعات بیشتر، [نقش `meter`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/meter_role) را ببینید. | {{HTMLElement('meter')}} |
| **`paragraph`** <br/>یک پاراگراف از محتوا.<br/> ویژگی‌های ممنوع: `aria-label` و `aria-labelledby`. | {{HTMLElement('p')}} |
| **`strong`** <br/>محتوای مهم، جدی یا فوری.<br/> ویژگی‌های ممنوع: `aria-label` و `aria-labelledby`. | {{HTMLElement('strong')}} |
| **`subscript`** <br/>یک یا چند نویسه زیرنویس.<br/>فقط در صورتی استفاده کنید که نبود نقش معنای محتوا را تغییر دهد.<br/> ویژگی‌های ممنوع: `aria-label` و `aria-labelledby`. | {{HTMLElement('sub')}} |
| **`superscript`** <br/>یک یا چند نویسه بالانویس.<br/>فقط در صورتی استفاده کنید که نبود نقش معنای محتوا را تغییر دهد.<br/> ویژگی‌های ممنوع: `aria-label` و `aria-labelledby`. | {{HTMLElement('sup')}} |
| [`term`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/term_role)<br/>یک کلمه یا عبارت با تعریف متناظر اختیاری.<br/> ویژگی‌های ممنوع: `aria-label` و `aria-labelledby`.<br/>برای اطلاعات بیشتر، [نقش `term`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/term_role) را ببینید. | {{HTMLElement('dfn')}} |
| **`time`** <br> یک قالب رشته تاریخ یا زمان معتبر که یک نقطه زمانی خاص را نشان می‌دهد.<br/> ویژگی‌های ممنوع: `aria-label` و `aria-labelledby`. | {{HTMLElement('time')}} |

> [!NOTE]
> ویژگی‌های `aria-label` و `aria-labelledby` بر روی `code`, `caption`, `deletion`, `emphasis`, `generic`, `insertion`, `mark`, `paragraph`, `presentation`, `none`, `strong`, `subscript`, `superscript`, `suggestion`, `term`, و `time` ممنوع هستند و فقط باید در محتوای تعاملی استفاده شوند.

## مشخصات

{{Specifications}}