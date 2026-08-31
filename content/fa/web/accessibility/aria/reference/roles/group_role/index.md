---
title: "ARIA: group role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: group role"
short-title: group
slug: Web/Accessibility/ARIA/Reference/Roles/group_role
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#group
sidebar: accessibilitysidebar
---

نقش `group` مجموعه‌ای از اشیاء رابط کاربری را شناسایی می‌کند که در نظر گرفته نشده‌اند توسط فناوری‌های کمکی در خلاصه صفحه یا فهرست مطالب گنجانده شوند.

## توضیحات

نقش ساختار سند `group`، که بیشترین نزدیکی را به عنصر {{HTMLElement('fieldset')}} در HTML دارد، برای شناسایی مجموعه‌ای از اشیاء رابط کاربری استفاده می‌شود که در مقایسه با [`region`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/region_role)، برای گنجانده شدن در خلاصه یا فهرست مطالب صفحه در نظر گرفته نشده است.

نقش `group` باید برای تشکیل مجموعه‌ای منطقی از موارد با عملکرد مرتبط استفاده شود، مانند فرزندان در ویجت [`tree`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tree_role) که مجموعه‌ای از خواهر و برادرها را در یک سلسله‌مراتب تشکیل می‌دهند، یا مجموعه‌ای از مواردی که در [`directory`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/directory_role) دارای ظرف یکسانی هستند.

هنگامی که `group` در زمینه [`list`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/list_role) استفاده می‌شود، فرزندان `group` را به عناصر [`listitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listitem_role) محدود کنید. در این مورد، توصیه می‌شود از چند فهرست مرتب یا نامرتب، {{HTMLElement('ol')}} یا {{HTMLElement('ul')}}، با فرزندان تو در توی {{HTMLElement('li')}} استفاده کنید.

هنگامی که در زمینه [`listbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listbox_role) استفاده می‌شود، تنها فرزندان مجاز عناصر {{HTMLElement('option')}} هستند. در این مورد، توصیه می‌شود به جای آن از {{HTMLElement('select')}}، {{HTMLElement('option')}} و {{HTMLElement('optgroup')}} استفاده کنید.

عناصر `گروه` ممکن است تودرتو باشند.

نقش `group` نباید برای بخش‌های اصلی و قابل درک صفحه استفاده شود. اگر بخشی به اندازه‌ای قابل توجه است که باید در فهرست مطالب صفحه گنجانده شود، از نقش `region` یا یک [نقش نشانه (landmark)](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles#3._landmark_roles) استاندارد استفاده کنید.

هنگامی که نقش به یک عنصر اضافه می‌شود، مرورگر یک رویداد گروه قابل دسترس به محصولات فناوری کمکی ارسال می‌کند که می‌توانند سپس کاربر را در مورد آن مطلع کنند.

## مثال‌ها

مثال کد HTML زیر از نقش `group` با نمای `tree` استفاده می‌کند:

```html
<div id="tree1" role="tree" tabindex="-1">
  <div
    id="animals"
    class="groupHeader"
    role="presentation"
    aria-owns="animalGroup"
    aria-expanded="true">
    <img
      role="presentation"
      tabindex="-1"
      src="images/treeExpanded.gif"
      alt="" />
    <span role="treeitem" tabindex="0">Animals</span>
  </div>
  <div id="animalGroup" role="group">
    <div id="birds" role="treeitem">
      <span tabindex="-1">Birds</span>
    </div>
    <div
      id="cats"
      class="groupHeader"
      role="presentation"
      aria-owns="catGroup"
      aria-expanded="false">
      <img
        role="presentation"
        tabindex="-1"
        src="images/treeContracted.gif"
        alt="" />
      <span role="treeitem" tabindex="0">Cats</span>
    </div>
    <div id="catGroup" role="group">
      <div id="siamese" role="treeitem">
        <span tabindex="-1">Siamese</span>
      </div>
      <div id="tabby" role="treeitem">
        <span tabindex="-1">Tabby</span>
      </div>
    </div>
  </div>
</div>
```

مثال زیر از نقش `group` با یک [`menu`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menu_role) کشویی حاوی [`menuitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitem_role)ها استفاده می‌کند:

```html
<div role="menu">
  <ul role="group">
    <li role="menuitem">Inbox</li>
    <li role="menuitem">Archive</li>
    <li role="menuitem">Trash</li>
  </ul>
  <ul role="group">
    <li role="menuitem">Custom Folder 1</li>
    <li role="menuitem">Custom Folder 2</li>
    <li role="menuitem">Custom Folder 3</li>
  </ul>
  <ul role="group">
    <li role="menuitem">New Folder</li>
  </ul>
</div>
```

این منو را می‌توان با استفاده از عناصر {{HTMLElement('select')}} و {{HTMLElement('option')}} ساخت. در این حالت، نقش `group` بیشترین شباهت را به عنصر {{HTMLElement('optgroup')}} خواهد داشت.

## مشخصات

{{Specifications}}

## همچنین ببینید

- عنصر {{HTMLElement('fieldset')}}
- [ARIA: `section` role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/section_role)
- [ARIA: `row` role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role)
- [ARIA: `select` role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/select_role)
- [ARIA: `toolbar` role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/toolbar_role)