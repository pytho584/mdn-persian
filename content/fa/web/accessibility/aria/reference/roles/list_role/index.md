---
title: "ARIA: list role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/list_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: list role"
short-title: list
slug: Web/Accessibility/ARIA/Reference/Roles/list_role
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#list
sidebar: accessibilitysidebar
---

نقش ARIA `list` می‌تواند برای شناسایی فهرستی از موارد استفاده شود. این نقش معمولاً همراه با نقش `listitem` که برای شناسایی یک مورد فهرست درون فهرست استفاده می‌شود، به کار می‌رود.

```html
<div role="list">
  <div role="listitem">List item 1</div>
  <div role="listitem">List item 2</div>
  <div role="listitem">List item 3</div>
</div>
```

## توضیحات

هر محتوایی که از یک ظرف بیرونی با فهرستی از عناصر درون آن تشکیل شده باشد، می‌تواند با استفاده از ظرف‌های `list` و `listitem` به ترتیب برای فناوری‌های کمکی شناسایی شود. یک `list` فقط می‌تواند صفر یا بیشتر فرزند `listitem` داشته باشد.

هیچ قانون سخت و سریعی در مورد اینکه از کدام عناصر برای نشانه‌گذاری فهرست و موارد فهرست استفاده کنید وجود ندارد، اما باید مطمئن شوید که موارد فهرست در زمینه یک فهرست معنادار هستند، به عنوان مثال، فهرست خرید، مراحل دستور پخت، مسیرهای رانندگی.

> [!NOTE]
> بهترین روش‌ها حکم می‌کنند که از عناصر معنایی HTML مناسب به جای نقش‌های ARIA برای نشانه‌گذاری فهرست‌ها و موارد فهرست استفاده شود — {{HTMLElement("ul")}}، {{HTMLElement("ol")}} و {{HTMLElement("li")}}. برای یک مثال کامل، [بهترین روش‌ها](#best_practices) را ببینید.

### نقش‌ها، حالت‌ها و ویژگی‌های مرتبط WAI-ARIA

- [`listitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listitem_role) role
  - : یک مورد منفرد در یک فهرست. عناصر با نقش `listitem` فقط می‌توانند در عنصری با نقش `list` یافت شوند.

## بهترین روش‌ها

فقط در صورت لزوم از `role="list"` و `role="listitem"` استفاده کنید — به عنوان مثال اگر کنترلی بر HTML خود ندارید اما می‌توانید پس از آن به صورت پویا با جاوااسکریپت دسترسی‌پذیری را بهبود ببخشید.

برخلاف {{HTMLElement("ol")}} و {{HTMLElement("ul")}} در HTML، نقش‌های `list` در ARIA بین فهرست‌های مرتب و نامرتب تمایز قائل نمی‌شوند. در صورت امکان، باید از عناصر معنایی HTML مناسب برای نشانه‌گذاری فهرست ({{HTMLElement("ol")}} و {{HTMLElement("ul")}}) و موارد فهرست ({{HTMLElement("li")}}) استفاده کنید. به عنوان مثال، مثال بالا باید به صورت زیر بازنویسی شود:

```html
<ul>
  <li>List item 1</li>
  <li>List item 2</li>
  <li>List item 3</li>
</ul>
```

یا اگر ترتیب موارد فهرست مهم است از یک فهرست مرتب استفاده کنید:

```html
<ol>
  <li>List item 1</li>
  <li>List item 2</li>
  <li>List item 3</li>
</ol>
```

> [!NOTE]
> نقش‌های `list` / `listitem` در ARIA بین فهرست‌های مرتب و نامرتب تمایز قائل نمی‌شوند.

به عنوان یک نکته جانبی، توجه داشته باشید که اگر از عناصر HTML معنایی `<ol>` یا `<ul>` استفاده می‌کنید و نقش [`presentation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role) را اعمال می‌کنید، هر عنصر فرزند `<li>` نقش `presentation` را به ارث می‌برد، زیرا ARIA ایجاب می‌کند که عناصر `listitem` دارای عنصر والد `list` باشند. بنابراین، عناصر `<li>` در معرض فناوری‌های کمکی قرار نمی‌گیرند، اما عناصر موجود در داخل آن عناصر `<li>`، از جمله فهرست‌های تودرتو، برای فناوری‌های کمکی قابل مشاهده هستند.

> [!NOTE]
> اگر در حال نشانه‌گذاری فهرستی از موارد هستید که به عنوان رابط برگه‌ای عمل می‌کنند، در عوض باید از نقش‌های [`tab`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role)، [`tabpanel`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tabpanel_role) و [`tablist`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tablist_role) استفاده کنید.

## مشخصات

{{Specifications}}

## همچنین ببینید

- عنصر {{HTMLElement("ul")}}
- عنصر {{HTMLElement("ol")}}
- عنصر {{HTMLElement("li")}}
- [ARIA: listitem role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listitem_role)
- [ARIA Lists examples](https://www.scottohara.me/blog/2018/05/26/aria-lists.html) — توسط Scott O'Hara
- [Accessibility Object Model](https://wicg.github.io/aom/spec/)
- [ARIA in HTML](https://w3c.github.io/html-aria/)