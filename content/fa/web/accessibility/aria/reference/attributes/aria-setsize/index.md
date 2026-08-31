---
title: "ARIA: aria-setsize attribute"
short-title: aria-setsize
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-setsize
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-setsize
sidebar: accessibilitysidebar
---

ویژگی `aria-setsize` تعداد آیتم‌ها را در مجموعه فعلی از listitems یا treeitems زمانی که همه آیتم‌های مجموعه در DOM وجود ندارند، تعریف می‌کند.

## توضیحات

مرورگرها به طور خودکار اندازه و موقعیت مجموعه را برای هر آیتم در یک گروه از آیتم‌ها محاسبه می‌کنند، مانند تعداد {{HTMLelement('li')}}ها در یک لیست، دکمه‌ها در یک گروه هم‌نام از [دکمه‌های رادیویی](/en-US/docs/Web/HTML/Reference/Elements/input/radio)، و {{HTMLelement('option')}}ها در یک {{HTMLelement('select')}}. فناوری‌های کمکی، مانند صفحه‌خوان‌ها، از این مدیریت وضعیت برای گزارش اندازه مجموعه به کاربر بهره می‌برند.

وقتی DOM کامل نیست، محاسبه مرورگر از تعداد آیتم‌های یک مجموعه می‌تواند نادرست باشد. وقتی فقط زیرمجموعه‌ای از آیتم‌ها، مانند آیتم‌های لیست، در DOM بارگذاری شده‌اند، مرورگر تعداد آیتم‌ها را فقط بر اساس موارد موجود محاسبه می‌کند. ویژگی `aria-setsize` باید برای نادیده گرفتن شمارش نادرست مرورگر استفاده شود. این ویژگی تعداد آیتم‌ها را در مجموعه فعلی از listitems یا treeitems در صورت بارگذاری کامل مجموعه تعریف می‌کند.

ویژگی `aria-setsize` بر روی هر آیتم تنظیم می‌شود، نه بر روی عنصر محتوا. مقدار برای هر آیتم یکسان است: یک عدد صحیح که تعداد آیتم‌های مجموعه کامل را منعکس می‌کند، یا `-1` اگر اندازه مجموعه نامشخص باشد. اگر همه آیتم‌ها در DOM وجود داشته باشند، مرورگر می‌تواند اندازه مجموعه و موقعیت هر آیتم را محاسبه کند، و هر دو `aria-setsize` و `aria-posinset` غیرضروری می‌شوند.

عناصر دارای `aria-setsize` معمولاً ویژگی [`aria-posinset`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-posinset) را نیز شامل می‌شوند تا موقعیت آن آیتم را در مجموعه نشان دهند. مقدار `aria-posinset` بین `1` و مقدار مثبت `aria-setsize` است.

به عنوان مثال، در بخش نظرات یک صفحه، وقتی همه نظرات در DOM نیستند، مانند زمانی که نظرات صفحه‌بندی شده‌اند، سطح، تعداد کل نظرات و موقعیت هر نظر باید با ARIA تنظیم شود. سطح سلسله‌مراتبی نظرات را می‌توان با [`aria-level`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-level) نشان داد. اطلاعات موقعیت گروه با `aria-posinset` و `aria-setsize` نشان داده می‌شود.

وقتی یک فید تعداد ثابتی مقاله دارد، `aria-setsize` می‌تواند به هر عنصر مقاله اضافه شود با مقداری که یا تعداد کل مقالات بارگذاری شده یا تعداد کل در فید است. مقدار انتخاب شده بستگی به این دارد که کدام مقدار برای کاربران مفیدتر است. اگر تعداد مقالات بسیار زیاد، نامعین یا اغلب در حال تغییر است، می‌توان `aria-setsize="-1"` را تنظیم کرد تا نشان دهد اندازه مجموعه نامشخص است.

در یک [`listbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listbox_role)، وقتی مجموعه کامل گزینه‌های موجود به دلیل بارگذاری پویا در حین پیمایش در DOM وجود ندارد، می‌توان `aria-setsize` و `aria-posinset` را بر روی هر [`option`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/option_role) تنظیم کرد.

در نمای درختی، اگر مجموعه کامل گره‌های موجود به دلیل بارگذاری پویا در هنگام حرکت فوکوس کاربر یا پیمایش درخت در DOM وجود نداشته باشد، هر گره دارای `aria-level`، `aria-setsize` و `aria-posinset` تنظیم شده است.

در یک منو، `aria-setsize` بر روی تمام نقش‌های [`menuitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitem_role)، [`menuitemcheckbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role) یا [`menuitemradio`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role) تنظیم می‌شود، با مقداری برابر با تعداد کل آیتم‌های منو، به استثنای هر جداکننده.

## مثال

مثال زیر آیتم‌های ۵ تا ۸ را در یک مجموعه ۱۶ تایی نشان می‌دهد.

```html
<h2 id="label_fruit">Available Fruit</h2>
<ul role="listbox" aria-labelledby="label_fruit">
  <li role="option" aria-setsize="16" aria-posinset="5">apples</li>
  <li role="option" aria-setsize="16" aria-posinset="6">bananas</li>
  <li role="option" aria-setsize="16" aria-posinset="7">cantaloupes</li>
  <li role="option" aria-setsize="16" aria-posinset="8">dates</li>
</ul>
```

برای راهنمایی کاربر، فناوری‌های کمکی موزهای بالا را به عنوان «آیتم ۶ از ۱۶» فهرست می‌کنند.

## مقادیر

- `<integer>`
  - : تعداد آیتم‌های مجموعه کامل یا `-1` اگر اندازه مجموعه نامشخص باشد.

## رابط‌های مرتبط

- {{domxref("Element.ariaSetSize")}}
  - : ویژگی [`ariaSetSize`](/en-US/docs/Web/API/Element/ariaSetSize) که بخشی از رابط {{domxref("Element")}} است، مقدار ویژگی `aria-setsize` را منعکس می‌کند.
- {{domxref("ElementInternals.ariaSetSize")}}
  - : ویژگی [`ariaSetSize`](/en-US/docs/Web/API/ElementInternals/ariaSetSize) که بخشی از رابط {{domxref("ElementInternals")}} است، مقدار ویژگی `aria-setsize` را منعکس می‌کند.

## نقش‌های مرتبط

نقش‌های استفاده‌شده:

- [`article`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/article_role)
- [`associationlistitemkey`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`associationlistitemvalue`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/structural_roles)
- [`comment`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/comment_role)
- [`listitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listitem_role)
- [`menuitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitem_role)
- [`option`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/option_role)
- [`radio`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radio_role)
- [`row`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role)
- [`tab`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role)

نقش‌های به ارث برده شده:

- [`comment`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/comment_role)
- [`menuitemcheckbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role)
- [`menuitemradio`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role)
- [`treeitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treeitem_role)

## مشخصات

{{Specifications}}

## همچنین ببینید

- [`aria-posinset`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-posinset)
- شیوه‌های W3C WAI-ARIA:
  - [Treegrid Email Inbox example](https://www.w3.org/WAI/ARIA/apg/patterns/treegrid/examples/treegrid-1/)
  - [Navigation Treeview example](https://www.w3.org/WAI/ARIA/apg/patterns/treeview/examples/treeview-navigation/)
  - [File Directory Treeview Example Using Declared Properties](https://www.w3.org/WAI/ARIA/apg/patterns/treeview/examples/treeview-1b/)