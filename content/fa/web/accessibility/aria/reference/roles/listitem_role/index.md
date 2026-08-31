---
title: "ARIA: listitem role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listitem_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: listitem role"
short-title: listitem
slug: Web/Accessibility/ARIA/Reference/Roles/listitem_role
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#listitem
sidebar: accessibilitysidebar
---

نقش `listitem` در ARIA می‌تواند برای شناسایی یک آیتم درون فهرستی از آیتم‌ها استفاده شود. این نقش معمولاً همراه با نقش [`list`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/list_role) استفاده می‌شود که برای شناسایی ظرف فهرست به کار می‌رود.

```html
<section role="list">
  <div role="listitem">List item 1</div>
  <div role="listitem">List item 2</div>
  <div role="listitem">List item 3</div>
</section>
```

## توضیحات

هر محتوایی که از یک ظرف بیرونی با فهرستی از عناصر درون آن تشکیل شده باشد، می‌تواند با استفاده از ظرف‌های `list` و `listitem` به ترتیب برای فناوری‌های کمکی شناسایی شود.

قوانین سخت‌گیرانه‌ای درباره عناصری که باید برای نشانه‌گذاری فهرست و آیتم‌های فهرست استفاده کنید وجود ندارد، اما باید مطمئن شوید که آیتم‌های فهرست در بافت یک فهرست منطقی هستند؛ مانند فهرست خرید، مراحل دستور پخت، یا مسیر رانندگی.

> [!NOTE]
> اگر در کارتان امکان‌پذیر است، باید از عناصر HTML معنایی مناسب برای نشانه‌گذاری یک فهرست و آیتم‌های آن استفاده کنید — {{HTMLElement("ul")}}/{{HTMLElement("ol")}} و {{HTMLElement("li")}}. برای مثال کامل به [بهترین روش‌ها](#best_practices) مراجعه کنید.

### نقش‌ها، حالت‌ها و ویژگی‌های WAI-ARIA مرتبط

- [`list`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/list_role)
  - : فهرستی از آیتم‌ها. عناصر با نقش `list` باید یک یا چند عنصر با نقش `listitem` به عنوان فرزند داشته باشند، یا یک یا چند عنصر با نقش `group` که یک یا چند عنصر با نقش `listitem` را به عنوان فرزند دارند.
- [`group`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role)
  - : مجموعه‌ای از اشیاء مرتبط که وقتی در یک فهرست تودرتو هستند به آیتم‌های فهرست محدود می‌شوند و به اندازه کافی مهم نیستند که جایگاه جداگانه‌ای در فهرست مطالب صفحه داشته باشند.

## بهترین روش‌ها

فقط در صورت اجبار از `role="list"` و `role="listitem"` استفاده کنید — مثلاً اگر کنترل HTML خود را ندارید اما می‌توانید دسترس‌پذیری را به‌صورت پویا و پس از بارگذاری با جاوااسکریپت بهبود دهید.

اگر امکان‌پذیر است، باید از عناصر HTML معنایی مناسب برای نشانه‌گذاری فهرست و آیتم‌های آن استفاده کنید — {{HTMLElement("ol")}}، {{HTMLElement("ul")}} و {{HTMLElement("li")}}. برای مثال، مثال بالا باید به شکل زیر بازنویسی شود:

```html
<ul>
  <li>List item 1</li>
  <li>List item 2</li>
  <li>List item 3</li>
</ul>
```

یا اگر ترتیب آیتم‌های فهرست مهم است، از فهرست مرتب استفاده کنید:

```html
<ol>
  <li>List item 1</li>
  <li>List item 2</li>
  <li>List item 3</li>
</ol>
```

> [!NOTE]
> نقش‌های `list` / `listitem` در ARIA بین فهرست‌های مرتب و نامرتب تمایز قائل نمی‌شوند.

> [!NOTE]
> استایل دادن به یک فهرست با `list-style: none;` در CSS، معنای فهرست را حذف می‌کند. افزودن `role="listitem"` معنا را بازمی‌گرداند.

> [!NOTE]
> اگر در حال نشانه‌گذاری فهرستی از آیتم‌ها هستید که به عنوان رابط تب‌ها عمل می‌کند، باید به جای آن از نقش‌های [`tab`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role)، [`tabpanel`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tabpanel_role) و [`tablist`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tablist_role) استفاده کنید.

## مشخصات

{{Specifications}}

## همچنین ببینید

- [عنصر HTML `<li>`](/en-US/docs/Web/HTML/Reference/Elements/li)
- [عنصر HTML `<ul>`](/en-US/docs/Web/HTML/Reference/Elements/ul)
- [عنصر HTML `<ol>`](/en-US/docs/Web/HTML/Reference/Elements/ol)
- [نقش ARIA: `list`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/list_role)
- [نقش ARIA: `group`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role)
- [مدل شیء دسترس‌پذیری](https://wicg.github.io/aom/spec/)
- [ARIA در HTML](https://w3c.github.io/html-aria/)
- [نمونه‌های فهرست‌های ARIA](https://www.scottohara.me/blog/2018/05/26/aria-lists.html) — نوشته اسکات اوهارا