---
title: "ARIA: aria-expanded attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-expanded"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-expanded attribute"
short-title: aria-expanded
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-expanded
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-expanded
sidebar: accessibilitysidebar
---

ویژگی `aria-expanded` بر روی یک عنصر تنظیم می‌شود تا مشخص کند که یک کنترل باز (expanded) است یا بسته (collapsed)، و اینکه عناصر تحت کنترل نمایش داده می‌شوند یا پنهان.

## توضیحات

ویجت‌های متعددی وجود دارند که می‌توانند باز و بسته شوند، از جمله منوها، دیالوگ‌ها و پنل‌های accordion. هر یک از این اشیا به نوبه خود دارای یک عنصر تعاملی هستند که باز و بسته شدن آن‌ها را کنترل می‌کند. ویژگی `aria-expanded` به این کنترل تعاملی قابل تمرکز اعمال می‌شود که قابلیت نمایش شیء را تغییر می‌دهد.

به عنوان مثال، `aria-expanded` به آیتم والد در یک درخت DOM اعمال می‌شود تا نشان دهد که شاخه فرزند آن نمایش داده شده است یا خیر. والد همچنین قابلیت نمایش شاخه فرزند مرتبط را کنترل می‌کند.

دو اعلان وجود دارند که می‌توانند به اشیایی که قابلیت نمایش شیء دیگری را کنترل می‌کنند اعمال شوند: [`aria-controls`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-controls) یا [`aria-owns`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-owns) به همراه `aria-expanded`. `aria-controls` و `aria-owns` رابطه بین عنصر کنترل‌کننده و عنصر تحت کنترل را نشان می‌دهند. `aria-expanded` به فناوری کمکی نشان می‌دهد که عنصر تحت کنترل باز است یا بسته.

از ویژگی `aria-owns` بر روی عناصری استفاده کنید که دارای ظروف گروه‌بندی قابل باز شدن هستند. اگر ظرف گروه‌بندی قابل باز و بسته شدن متعلق به عنصری نیست که دارای ویژگی `aria-expanded` است، به جای آن از ویژگی `aria-controls` برای ارجاع به ظرف گروه‌بندی استفاده کنید.

### دکمه‌ها

یک دکمه که یک ویجت را تغییر حالت می‌دهد باید دارای `aria-controls` تنظیم شده به [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) ویجت تغییر یافته و `aria-expanded` تنظیم شده به وضعیت فعلی ویجت باشد.

```html
<button aria-expanded="false" aria-controls="widget1">Toggle widget</button>
```

هنگامی که ویجت قابل مشاهده است، شیء کنترل‌کننده این اطلاعات را با تنظیم `aria-expanded="true"` بر روی خود منتقل می‌کند. نام قابل دسترسی شیء کنترل‌کننده باید این تغییر را منعکس کند.

```html
<button aria-expanded="true" aria-controls="widget1">Toggle widget</button>
```

### منو

هنگامی که یک [`menu`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menu_role) نمایش داده می‌شود، شیء دکمه‌ای که قابلیت نمایش آن منو را تغییر می‌دهد دارای `aria-expanded="true"` تنظیم شده است. هنگامی که منو پنهان است، `aria-expanded` می‌تواند حذف شود. اگر هنگام پنهان بودن منو مشخص شود، باید به صورت `aria-expanded="false"` تنظیم شود. هنگامی که یک منوی فرزند قابل مشاهده نیست، [`menuitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitem_role) والد آن دارای `aria-expanded` است. هنگامی که منوی فرزند قابل مشاهده است، باید به `true` تنظیم شود.

### Combobox

به طور پیش‌فرض، برخی نقش‌ها پنهان یا بسته هستند و برخی دیگر باز یا گسترده هستند. عناصر با نقش [`combobox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role) دارای مقدار پیش‌فرض `false` برای `aria-expanded` هستند. هنگامی که پنجره بازشوی combobox قابل مشاهده نیست، عنصر با نقش `combobox` دارای `aria-expanded` تنظیم شده به `false` است. این وضعیت پیش‌فرض است. هنگامی که عنصر پنجره بازشو قابل مشاهده است، `aria-expanded` باید به `true` تنظیم شود.

```html
<label for="username">Username</label>
<input id="username" name="username" aria-describedby="username-desc" />
<button
  aria-expanded="false"
  aria-controls="username-desc"
  aria-label="Help about username"
  type="button">
  <span aria-hidden="true">?</span>
</button>
<p id="username-desc" hidden>
  Your username is the name that you use to log in to this service.
</p>
```

> [!NOTE]
> وجود ویژگی `aria-expanded` نشان‌دهنده کنترل است. از قرار دادن آن بر روی عناصری که وضعیت باز شدن عناصر دیگر را کنترل نمی‌کنند خودداری کنید.

### Treeitems

هر عنصر با نقش [`treeitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treeitem_role) که به عنوان یک گره والد عمل می‌کند، هنگامی که گره در حالت بسته است دارای `aria-expanded="false"` و هنگامی که گره در حالت باز است دارای `aria-expanded="true"` است. گره‌های انتهایی، گره‌هایی که هیچ گره فرزندی ندارند، نباید ویژگی `aria-expanded` را داشته باشند، زیرا اگر داشته باشند، به اشتباه به فناوری‌های کمکی به عنوان گره‌های والد توصیف می‌شوند.

### ردیف‌ها

یک ردیف والد در یک [`treegrid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treegrid_role) ردیفی است که می‌تواند برای نمایش یا پنهان کردن مجموعه‌ای از ردیف‌های فرزند در یک جدول یا شبکه باز یا بسته شود. هر ردیف والد دارای حالت `aria-expanded` است که بر روی عنصر ردیف یا بر روی یک سلول موجود در ردیف تنظیم می‌شود. هنگامی که ردیف‌های فرزند پنهان هستند، `aria-expanded="false"` تنظیم می‌شود. `aria-expanded="true"` هنگامی تنظیم می‌شود که ردیف‌های فرزند نمایش داده می‌شوند. ردیف‌هایی که نمایش ردیف‌های فرزند را کنترل نمی‌کنند به هیچ وجه نباید ویژگی `aria-expanded` را شامل شوند، زیرا شامل شدن ویژگی آن‌ها را به عنوان ردیف‌های والد تعریف می‌کند.

## مقادیر

- `false`
  - : عنصر گروه‌بندی که این عنصر مالک یا کنترل آن است، بسته (collapsed) است.
- `true`
  - : عنصر گروه‌بندی که این عنصر مالک یا کنترل آن است، باز (expanded) است.
- `undefined` (پیش‌فرض)
  - : عنصر مالک یا کنترل‌کننده یک عنصر گروه‌بندی قابل باز شدن نیست.

## رابط‌های مرتبط

- {{domxref("Element.ariaExpanded")}}
  - : ویژگی [`ariaExpanded`](/en-US/docs/Web/API/Element/ariaExpanded)، بخشی از رابط {{domxref("Element")}}، مقدار ویژگی `aria-expanded` را منعکس می‌کند.
- {{domxref("ElementInternals.ariaExpanded")}}
  - : ویژگی [`ariaExpanded`](/en-US/docs/Web/API/Element/ariaExpanded)، بخشی از رابط {{domxref("ElementInternals")}}، مقدار ویژگی `aria-expanded` را منعکس می‌کند.

## نقش‌های مرتبط

استفاده شده در نقش‌ها:

- [`application`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/application_role)
- [`button`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role)
- [`checkbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/checkbox_role)
- [`combobox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role)
- [`gridcell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role)
- [`link`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/link_role)
- [`listbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listbox_role)
- [`menuitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitem_role)
- [`row`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role)
- [`rowheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowheader_role)
- [`tab`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role)
- [`treeitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treeitem_role)

به ارث برده شده در نقش‌ها:

- [`columnheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role)
- [`menuitemcheckbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role)
- [`menuitemradio`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role)
- [`rowheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowheader_role)
- [`switch`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/switch_role)

## مشخصات

{{Specifications}}

## همچنین ببینید

- [`aria-controls`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-controls)
- [`aria-owns`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-owns)
- [`aria-hidden`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-hidden)
- ویژگی HTML [`hidden`](/en-US/docs/Web/HTML/Reference/Global_attributes/hidden)