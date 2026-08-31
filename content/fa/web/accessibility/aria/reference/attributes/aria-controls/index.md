---
title: "ARIA: aria-controls attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-controls"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-controls attribute"
short-title: aria-controls
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-controls
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-controls
sidebar: accessibilitysidebar
---

ویژگی سراسری `aria-controls` عنصر (یا عناصری) را مشخص می‌کند که محتوا یا وجود آن‌ها توسط عنصری که این ویژگی روی آن تنظیم شده است، کنترل می‌شود.

## توضیحات

هنگامی که یک ابزارک یا عنصر تعاملی، خواه یک جعبه ترکیبی، برگه، دکمه و غیره، برای تنظیم یا تغییر عنصر یا مؤلفه دیگری در یک سند یا برنامه استفاده می‌شود، می‌توان از ویژگی `aria-controls` برای ارتباط برنامه‌نویسی عنصر یا عناصر متناظر با عنصر کنترل‌کننده استفاده کرد. ویژگی `aria-controls` عنصر (یا عناصری) را مشخص می‌کند که محتوا یا وجود آن‌ها توسط عنصری که ویژگی روی آن تنظیم شده است، کنترل می‌شود، صرف‌نظر از نوع تعاملی که رفتار تأثیرپذیر را آغاز می‌کند.

یک عنصر [جعبه ترکیبی](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role) دارای `aria-controls` است که به مقداری اشاره می‌کند که به عنصر عمل‌کننده به عنوان پاپ‌آپ اشاره دارد. `aria-controls` فقط زمانی نیاز به تنظیم دارد که پاپ‌آپ قابل مشاهده باشد، اما معتبر و آسان‌تر برای برنامه‌نویسی است که به عنصری که قابل مشاهده نیست اشاره کند.

نمونه‌های دیگر از کنترل‌ها عبارتند از:

- بخش‌های دکمه‌ای یک ابزارک آکاردئونی که قابلیت مشاهده محتوای پنل مرتبط خود را تغییر می‌دهند. هر دکمه ممکن است دارای `aria-controls` باشد که به شناسه عنصر حاوی محتوای مرتبط با کنترل فراخوانی‌کننده اشاره می‌کند.
- یک عنصر با نقش [`scrollbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/scrollbar_role): نوار پیمایش نیاز به یک ویژگی `aria-controls` دارد که به شناسه عنصری که کنترل می‌کند اشاره کند.
- یک گروه از برگه‌ها که هر کدام یک پنل برگه متفاوت را نمایش می‌دهند: هر عنصر با [`role="tab"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role) دارای یک ویژگی `aria-controls` است که به [`tabpanel`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tabpanel_role) مرتبط خود اشاره می‌کند.

## مثال

در این مثال از برگه‌ها، هر برگه یک پنل برگه را کنترل می‌کند:

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
  <div
    id="panel-2"
    role="tabpanel"
    tabindex="0"
    aria-labelledby="tab-2"
    class="display-none">
    <p>Content for the second panel</p>
  </div>
  <div
    id="panel-3"
    role="tabpanel"
    tabindex="0"
    aria-labelledby="tab-3"
    class="display-none">
    <p>Content for the third panel</p>
  </div>
</div>
```

> [!NOTE]
> ARIA فقط درخت دسترسی‌پذیری یک عنصر را اصلاح می‌کند و مشخص می‌کند که فناوری کمکی چگونه می‌تواند محتوا را به کاربران ارائه دهد. ARIA هیچ عملکرد یا سبک ضمنی را تغییر نمی‌دهد.

## مقادیر

- `id` list
  - : یک فهرست جدا شده با فاصله از یک یا چند مقدار شناسه که به عناصر کنترل‌شده توسط عنصر جاری اشاره می‌کند.

## رابط‌های مرتبط

- {{domxref("Element.ariaControlsElements")}}
  - : ویژگی `ariaControlsElements` بخشی از رابط هر عنصر است. مقدار آن آرایه‌ای از نمونه‌های زیرکلاس‌های {{domxref("Element")}} است که ارجاعات `id` در ویژگی `aria-controls` را منعکس می‌کند ([با برخی ملاحظات](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references)).
- {{domxref("ElementInternals.ariaControlsElements")}}
  - : ویژگی `ariaControlsElements` بخشی از رابط هر عنصر سفارشی است. مقدار آن آرایه‌ای از نمونه‌های زیرکلاس‌های {{domxref("Element")}} است که ارجاعات `id` در ویژگی `aria-controls` را منعکس می‌کند ([با برخی ملاحظات](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references)).

## نقش‌های مرتبط

در **همه** نقش‌ها استفاده می‌شود.

## مشخصات

{{Specifications}}

## همچنین ببینید

- [`aria-owns`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-owns)