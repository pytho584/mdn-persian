---
title: "ARIA: aria-selected attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-selected"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-selected attribute"
short-title: aria-selected
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-selected
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-selected
sidebar: accessibilitysidebar
---

ویژگی `aria-selected` وضعیت «انتخاب‌شده» فعلی ویجت‌های مختلف را نشان می‌دهد.

## توضیحات

ویژگی `aria-selected` وضعیت «انتخاب‌شده» فعلی را برای نقش‌های [`gridcell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role)، [`option`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/option_role)، [`row`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role) و [`tab`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role) نشان می‌دهد.

این ویژگی برای نشان‌دادن اینکه کدام عناصر درون ویجت‌های ترکیبی تک‌انتخابی و چندانتخابی انتخاب شده‌اند، استفاده می‌شود. اگر بیش از یک عنصر به‌طور هم‌زمان قابل انتخاب باشد، `aria-multiselectable="true"` را روی grid، listbox، tablist یا سایر نقش‌های والد قرار دهید، در حالی که `aria-selected` را فقط روی سلول‌ها، گزینه‌ها و تب‌های قابل انتخاب قرار می‌دهید.

برای سایر نقش‌ها، وضعیت انتخاب‌شده فعلی با [`aria-current`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-current)، یا احتمالاً [`aria-checked`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-checked) یا [`aria-pressed`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-pressed) بسته به نقش تنظیم می‌شود.

ویجت‌هایی که هم‌زمان از `aria-selected` و `aria-current` پشتیبانی می‌کنند، برای هر یک معانی متفاوتی دارند. برای مثال، `aria-current="page"` می‌تواند در یک درخت پیمایش استفاده شود تا نشان دهد کدام صفحه در حال حاضر نمایش داده می‌شود، در حالی که `aria-selected="true"` نشان می‌دهد در صورت فعال کردن `treeitem` توسط کاربر، کدام صفحه نمایش داده خواهد شد.

### گرید

تنظیم `aria-selected="false"` روی یک gridcell قابل تمرکز نشان می‌دهد که سلول قابل انتخاب است. اگر گرید اجازه می‌دهد بیش از یک gridcell هم‌زمان انتخاب شود، `aria-multiselectable="true"` را روی عنصر با نقش [`grid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role) تنظیم کنید. تنظیم `aria-selected` روی gridcell سرستون یا سرردیف، وضعیت را به سلول‌های دیگر در ستون یا ردیف منتقل نمی‌کند.

### گزینه

هم `aria-selected` و هم `aria-checked` برای [`option`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/option_role) معتبر هستند. برخی رابط‌های کاربری، انتخاب را در فهرست‌های تک‌انتخابی با `aria-selected` و در فهرست‌های چندانتخابی با `aria-checked` نشان می‌دهند.

هم `aria-selected` و هم `aria-checked` را روی عناصر `option` موجود در یک `listbox` مشخص نکنید، مگر اینکه معنا و هدف `aria-selected` با معنا و هدف aria-checked در رابط کاربری متفاوت باشد، معنا و هدف هر وضعیت آشکار باشد، و رابط کاربری روش‌های جداگانه‌ای برای کنترل هر وضعیت فراهم کند.

### ردیف

ویژگی `aria-selected` روی `row` پشتیبانی می‌شود، اما روی `column` پشتیبانی نمی‌شود. اگر یک گرید از انتخاب پشتیبانی کند، وقتی یک سلول یا ردیف انتخاب می‌شود، عنصر انتخاب‌شده دارای `aria-selected="true"` است.

اگر گرید از انتخاب ستون پشتیبانی کند و یک ستون انتخاب شود، همه سلول‌های ستون دارای `aria-selected` با مقدار `true` خواهند بود.

### تب

در یک tablist، `aria-selected` روی یک تب استفاده می‌شود تا [`tabpanel`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tabpanel_role) نمایش‌داده‌شده در حال حاضر را نشان دهد.

تب انتخاب‌شده در یک [`tablist`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tablist_role) باید دارای ویژگی `aria-selected="true"` باشد. همه تب‌های غیرفعال در tablist باید دارای `aria-selected="false"` باشند. تنظیم این وضعیت فقط بر درخت دسترس‌پذیری تأثیر می‌گذارد: مطمئن شوید تب فعال را به‌گونه‌ای استایل می‌دهید که وضعیت انتخاب‌شدن آن به‌صورت بصری نشان داده شود. مقدار پیش‌فرض `aria-selected` برای نقش `tab` برابر با `false` است.

اگر بیش از یک تب به‌طور هم‌زمان قابل انتخاب باشد، `aria-multiselectable` را روی `tablist` قرار دهید.

## مثال‌ها

در این مثال `tablist`، اولین `tab` انتخاب شده است:

```html
<div class="tab-interface">
  <div role="tablist" aria-label="Sample Tabs">
    <span
      role="tab"
      aria-selected="true"
      aria-controls="panel-1"
      id="tab-1"
      tabindex="0">
      First Tab
    </span>
    <span
      role="tab"
      aria-selected="false"
      aria-controls="panel-2"
      id="tab-2"
      tabindex="-1">
      Second Tab
    </span>
    <span
      role="tab"
      aria-selected="false"
      aria-controls="panel-3"
      id="tab-3"
      tabindex="-1">
      Third Tab
    </span>
  </div>
  <div id="panel-1" role="tabpanel" tabindex="0" aria-labelledby="tab-1">
    <p>Content for the first panel</p>
  </div>
  <div id="panel-2" role="tabpanel" tabindex="0" aria-labelledby="tab-2" hidden>
    <p>Content for the second panel</p>
  </div>
  <div id="panel-3" role="tabpanel" tabindex="0" aria-labelledby="tab-3" hidden>
    <p>Content for the third panel</p>
  </div>
</div>
```

> [!NOTE]
> ARIA فقط درخت دسترس‌پذیری یک عنصر و نحوه ارائه محتوا به کاربران توسط فناوری‌های کمکی را تغییر می‌دهد. ARIA هیچ چیزی را در عملکرد یا رفتار یک عنصر تغییر نمی‌دهد.

## مقادیر

- `true`
  - : عنصر قابل انتخاب، انتخاب شده است.
- `false`
  - : عنصر قابل انتخاب، انتخاب نشده است. مقدار پیش‌فرض ضمنی برای [`tab`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role).
- `undefined` (پیش‌فرض)
  - : عنصر قابل انتخاب نیست.

## رابط‌های مرتبط

- {{domxref("Element.ariaSelected")}}
  - : ویژگی [`ariaSelected`](/en-US/docs/Web/API/Element/ariaSelected) که بخشی از رابط {{domxref("Element")}} است، مقدار ویژگی `aria-selected` را بازتاب می‌دهد.
- {{domxref("ElementInternals.ariaSelected")}}
  - : ویژگی [`ariaSelected`](/en-US/docs/Web/API/ElementInternals/ariaSelected) که بخشی از رابط {{domxref("ElementInternals")}} است، مقدار ویژگی `aria-selected` را بازتاب می‌دهد.

## نقش‌های مرتبط

استفاده‌شده در نقش‌ها:

- [`gridcell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role)
- [`option`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/option_role)
- [`row`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role)
- [`tab`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role)

به ارث برده‌شده در نقش‌ها:

- [`columnheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role)
- [`rowheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowheader_role)
- [`treeitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treeitem_role)

## مشخصات

{{Specifications}}

## همچنین ببینید

- [`aria-pressed`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-pressed)
- [`aria-checked`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-checked)