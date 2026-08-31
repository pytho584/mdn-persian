---
title: "ARIA: aria-posinset attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-posinset"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-posinset attribute"
short-title: aria-posinset
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-posinset
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-posinset
sidebar: accessibilitysidebar
---

ویژگی `aria-posinset` شماره یا موقعیت یک عنصر را در مجموعه فعلی از listitem ها یا treeitem ها تعریف می‌کند، زمانی که همه آیتم‌ها در DOM وجود ندارند.

## توضیحات

ویژگی `aria-posinset` که مخفف «position in set» (موقعیت در مجموعه) است، موقعیت عنصر را در کل مجموعه listitem ها یا treeitem ها تعریف می‌کند، زمانی که تنها زیرمجموعه‌ای از آیتم‌ها در DOM وجود دارند.

اگر همه آیتم‌های یک فهرست در DOM موجود باشند، مرورگر می‌تواند تعداد کل و موقعیت هر آیتم را محاسبه کند و در نتیجه `aria-posinset` ضروری نیست. زمانی که تنها بخشی از یک مجموعه در DOM وجود دارد، `aria-posinset` را به‌همراه [`aria-setsize`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-setsize) وارد کنید تا به کاربر اطلاع دهد در مجموعه کامل چند آیتم وجود دارد.

مثال زیر یک جعبه‌فهرست (listbox) با چهار گزینه عنصر از میان ۱۱۸ عنصر جدول تناوبی عناصر شیمیایی را نشان می‌دهد.

```html
<h2 id="periodic-table">Periodic table of chemical elements</h2>
<ul role="listbox" aria-labelledby="periodic-table">
  <li role="option" aria-setsize="118" aria-posinset="1">Hydrogen</li>
  <li role="option" aria-setsize="118" aria-posinset="3">Lithium</li>
  <li role="option" aria-setsize="118" aria-posinset="11">Sodium</li>
  <li role="option" aria-setsize="118" aria-posinset="19">Potassium</li>
</ul>
```

مقدار هر `aria-posinset` یک عدد صحیح بزرگ‌تر یا مساوی `1` و کوچک‌تر یا مساوی اندازه مجموعه است، زمانی که آن اندازه مشخص باشد.

> [!NOTE]
> هنگام استفاده از `aria-posinset` باید مقدار [`aria-setsize`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-setsize) را نیز وارد کنید که اندازه کل مجموعه است. اگر اندازه کل مجموعه نامشخص است، مقدار `aria-setsize="-1"` را تنظیم کنید.

برای [`menuitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitem_role)، [`menuitemcheckbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role) یا [`menuitemradio`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role)، مقدار `aria-posinset` را با توجه به تعداد کل آیتم‌های منو، به‌جز جداکننده‌ها، تنظیم کنید.

در یک [`feed`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/feed_role)، هر عنصر {{HTMLElement('article')}} دارای `aria-posinset` است که به مقداری تنظیم شده که موقعیت آن را در فید نشان می‌دهد. همچنین `aria-setsize` یا به تعداد مقاله‌های بارگذاری‌شده یا به تعداد کل مقاله‌های موجود در فید تنظیم می‌شود، بسته به اینکه کدام مقدار برای کاربران مفیدتر است.

## مقادیر

- `<integer>`
  - : عدد صحیح بزرگ‌تر یا مساوی 1 و کوچک‌تر یا مساوی مقدار `aria-setsize`.

## رابط‌های مرتبط

- {{domxref("Element.ariaPosInSet")}}
  - : ویژگی [`ariaPosInSet`](/en-US/docs/Web/API/Element/ariaPosInSet) که بخشی از رابط {{domxref("Element")}} است، مقدار ویژگی `aria-posinset` را بازتاب می‌دهد.
- {{domxref("ElementInternals.ariaPosInSet")}}
  - : ویژگی [`ariaPosInSet`](/en-US/docs/Web/API/ElementInternals/ariaPosInSet) که بخشی از رابط {{domxref("ElementInternals")}} است، مقدار ویژگی `aria-posinset` را بازتاب می‌دهد.

## نقش‌های مرتبط

استفاده‌شده در نقش‌ها:

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

به نقش‌های زیر به ارث می‌رسد:

- [`comment`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/comment_role)
- [`menuitemcheckbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role)
- [`menuitemradio`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role)
- [`treeitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treeitem_role)

## مشخصات

{{Specifications}}

## همچنین ببینید

- [`aria-setsize`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-setsize)