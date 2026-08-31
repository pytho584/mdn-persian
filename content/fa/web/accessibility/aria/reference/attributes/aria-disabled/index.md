---
title: "ARIA: aria-disabled attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-disabled"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-disabled attribute"
short-title: aria-disabled
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-disabled
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-disabled
sidebar: accessibilitysidebar
---

وضعیت `aria-disabled` نشان‌دهنده این است که عنصر قابل درک است اما غیرفعال است، بنابراین قابل ویرایش یا به‌طور دیگری قابل استفاده نیست.

## توضیحات

ویژگی `aria-disabled` وقتی روی `true` تنظیم شود، نشان می‌دهد که عنصری که روی آن تنظیم شده و تمام فرزندان قابل فوکوس آن باید در وضعیت غیرفعال باشند. این اعلام به افرادی که از فناوری‌های کمکی مانند صفحه‌خوان‌ها استفاده می‌کنند، اطلاع می‌دهد که چنین عناصری قرار نیست قابل ویرایش یا به‌طور دیگری قابل استفاده باشند.

برخلاف ویژگی بولی [`disabled`](/en-US/docs/Web/HTML/Reference/Elements/input#disabled) در HTML که یک کنترل فرم را به‌صورت معنایی غیرفعال نشان می‌دهد، استایل آن را برای بازتاب وضعیت تغییر می‌دهد و تمام عملکردها را سرکوب می‌کند و همچنین اجازه نمی‌دهد مقدار عنصر در ارسال فرم شرکت کند، `aria-disabled="true"` <strong>فقط</strong> این عناصر را به‌صورت معنایی به‌عنوان غیرفعال معرفی می‌کند. توسعه‌دهندگان وب باید به‌صورت دستی اطمینان حاصل کنند که چنین عناصری هنگام قرار گرفتن در وضعیت غیرفعال، عملکردشان سرکوب شود.

هنگامی که نیاز به غیرفعال کردن کنترل‌های فرم بومی HTML دارید، توسعه‌دهندگان باید ویژگی `disabled` را مشخص کنند، زیرا این ویژگی به‌طور پیش‌فرض تمام ویژگی‌های مورد انتظار برای غیرفعال کردن یک کنترل را فراهم می‌کند. با این حال، مواردی وجود دارد که عناصر باید به‌عنوان غیرفعال معرفی شوند، اما همچنان برای کاربران در دسترس باشند تا هنگام پیمایش با کلید <kbd>Tab</kbd> پیدا شوند. این کار می‌تواند قابلیت کشف‌پذیری آن‌ها را بهبود بخشد، زیرا آن‌ها از ترتیب فوکوس صفحه وب حذف نمی‌شوند؛ `aria-disabled` قابلیت فوکوس‌شدن چنین عناصری را تغییر نمی‌دهد و عناصر با استایل پیش‌فرض مرورگر کمرنگ نمی‌شوند و خواندن آن‌ها آسان‌تر است. چند نمونه از مواردی که این ممکن است مفید باشد عبارت‌اند از:

- عنصر دکمه سربرگ مرتبط با پنل آکاردئونی غیرقابل جمع‌شدن،
- دکمه‌ای که حفظ آن در ترتیب فوکوس صفحه مهم است، اما عملکردش در حال حاضر در دسترس نیست - مانند ارسال فرم،
- آیتم‌های موقتاً غیرفعال در یک ویجت منو که در غیر این صورت از طریق پیمایش استاندارد صفحه‌کلید رد می‌شدند.

در هر یک از این موارد، ممکن است بخواهید کاربران این عناصر را از طریق پیمایش استاندارد صفحه‌کلید پیدا کنند، اگرچه عملکرد آن کنترل حذف یا «غیرفعال» شده است. توسعه‌دهندگان همچنان باید از JavaScript برای غیرفعال کردن کامل عملکرد عنصر استفاده کنند و همچنین ظاهر عنصر را تغییر دهند تا کاربران بینا بدانند که غیرفعال است.

> [!NOTE]
> حالت غیرفعال بودن برای عنصری با `aria-disabled="true"` و تمام فرزندان قابل فوکوس آن اعمال می‌شود. هنگام استفاده از این ویژگی روی عناصر حاوی احتیاط کنید. به‌ویژه در موردی که یک عنصر حاوی ممکن است هم کنترل‌های فرم و هم پیوندها را داشته باشد - جایی که هدف ممکن است نمایش کنترل‌های فرم در وضعیت غیرفعال باشد، اما <strong>نه</strong> اینکه پیوندها به‌عنوان «غیرفعال» معرفی شوند.

دلیل دیگر برای استفاده از ویژگی `aria-disabled` به‌جای ویژگی `disabled` در HTML این است که شما کنترل‌های سفارشی‌ای ایجاد کرده‌اید که باید به‌عنوان غیرفعال علامت‌گذاری شوند، اما از عنصری استفاده نمی‌کنید که ویژگی `disabled` را بپذیرد. برای مثال، در قطعه کد زیر از یک `<div>` برای ایجاد یک دکمه سفارشی استفاده شده است که باید به‌عنوان غیرفعال علامت‌گذاری شود. با این حال، عنصر `<div>` انتظار ویژگی `disabled` را ندارد و به آن احترام نمی‌گذارد - حتی اگر به آن `role="button"` داده شود تا نقش ARIA نمایشی آن تغییر کند. ویژگی `aria-disabled` برای غیرفعال کردن چنین کنترل‌های سفارشی لازم است.

```html
<div role="button" aria-disabled="true" tabindex="-1">Edit</div>
```

همان‌طور که برای اطمینان از عدم عملکرد عنصری با `aria-disabled="true"` نیاز به استفاده از JavaScript است، این عنصر به تنظیمات استایل نیز نیاز دارد. برخلاف ویژگی `disabled` در HTML که تعیین آن باعث اعمال استایل‌های `:disabled` از طرف عامل کاربر می‌شود، افزودن `aria-disabled="true"` چنین استایلی را اعمال نمی‌کند. می‌توان عنصر را با [انتخابگر ویژگی](/en-US/docs/Web/CSS/Reference/Selectors/Attribute_selectors) `[aria-disabled="true"]` استایل‌دهی کرد.

```css
[aria-disabled="true"] {
  opacity: 0.5;
}
```

اگر عمداً از ویژگی `aria-disabled` استفاده می‌کنید تا یک کنترل فرم در ترتیب فوکوس صفحه‌کلید صفحه باقی بماند، به‌ویژه اگر عنصر محتوای مهمی را نشان می‌دهد که همه کاربران باید بتوانند آن را درک کنند، ممکن است لازم باشد از استایلی استفاده کنید که همچنان الزامات کنتراست رنگ را برآورده کند. برای مثال، یک دکمه/عنوان غیرفعال که یک پنل آکاردئونی غیرقابل جمع‌شدن را معرفی می‌کند، محتوایی است که همچنان باید خوانا باشد.

```css
@media (forced-colors: active) {
  [aria-disabled="true"] {
    border-color: GrayText;
    color: GrayText;
  }
}
```

پرس‌وجوی رسانه‌ای [`forced-colors`](/en-US/docs/Web/CSS/Reference/At-rules/@media/forced-colors) تشخیص می‌دهد که آیا [عامل کاربر](/en-US/docs/Glossary/User_agent) حالت رنگ‌های اجباری را فعال کرده است یا خیر؛ اگر چنین باشد، رنگ متن و حاشیه هر دو به [رنگ سیستم `greyText`](/en-US/docs/Web/CSS/Reference/Values/system-color#syntax) تنظیم می‌شوند.

نکته دیگری که باید در نظر داشته باشید این است که هنگام استفاده از `aria-disabled` به‌جای ویژگی بومی HTML، ویژگی ARIA به استایل‌دهی دستی لازم برای نمایش بصری عنصر به‌عنوان غیرفعال در حالت کنتراست بالای ویندوز نیاز دارد.

> [!NOTE]
> اگر از [`pointer-events: none;`](/en-US/docs/Web/CSS/Reference/Properties/pointer-events) در CSS برای غیرقابل کلیک کردن یک عنصر استفاده می‌کنید، مطمئن شوید که تعامل‌پذیری را نیز با JavaScript غیرفعال می‌کنید. `pointer-events: none;` از کلیک‌های ماوس جلوگیری می‌کند، اما مانع فعال شدن عنصر از طریق صفحه‌کلید نمی‌شود.

```js
function onClick(event) {
  event.preventDefault();
}

function toggleDisabled(element, status, update) {
  if (status) {
    // element.input.disabled = false;
    element.setAttribute("aria-disabled", "false");
    update.textContent = "The element is now enabled.";
    element.addEventListener("click", onClick);
  } else {
    // element.input.disabled = true;
    element.setAttribute("aria-disabled", "true");
    update.textContent = "The element is now disabled.";
    element.removeEventListener("click", onClick);
  }
}
```

هنگام جابه‌جایی از `aria-disabled="true"` به `"false"`، از JavaScript برای موارد زیر استفاده کنید:

1. تغییر مقدار به `false` (یا حذف کامل ویژگی)،
2. فعال کردن عنصر، و
3. به کاربر اطلاع دهید که کنترل اکنون فعال است.

اگر فقط از CSS برای استایل‌دهی وضعیت غیرفعال با استفاده از یک انتخابگر ویژگی استفاده کرده‌اید، انتخابگر دیگر منطبق نخواهد شد و استایل غیرفعال دیگر اعمال نخواهد شد.

## مقادیر

- `true`
  - : عنصر غیرفعال است

- `false`
  - : عنصر غیرفعال نیست

## رابط‌های مرتبط

- {{domxref("Element.ariaDisabled")}}
  - : ویژگی [`ariaDisabled`](/en-US/docs/Web/API/Element/ariaDisabled) که بخشی از رابط {{domxref("Element")}} است، مقدار ویژگی `aria-disabled` را منعکس می‌کند؛ این ویژگی نشان می‌دهد که عنصر قابل درک است اما غیرفعال است، بنابراین قابل ویرایش یا به‌طور دیگری قابل استفاده نیست.
- {{domxref("ElementInternals.ariaDisabled")}}
  - : ویژگی [`ariaDisabled`](/en-US/docs/Web/API/ElementInternals/ariaDisabled) از رابط {{domxref("ElementInternals")}} مقدار ویژگی `aria-disabled` را منعکس می‌کند.

## نقش‌های مرتبط

استفاده‌شده در نقش‌ها:

- [`application`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/application_role)
- [`button`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/button_role)
- [`composite`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/composite_role)
- [`gridcell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role)
- [`group`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role)
- [`input`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/input_role)
- [`link`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/link_role)
- [`menuitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitem_role)
- [`scrollbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/scrollbar_role)
- [`separator`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/separator_role)
- [`tab`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role)

به نقش‌های زیر به ارث می‌رسد:

- [`checkbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/checkbox_role)
- [`columnheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role)
- [`combobox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role)
- [`grid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/grid_role)
- [`listbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listbox_role)
- [`menu`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menu_role)
- [`menubar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menubar_role)
- [`menuitemcheckbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role)
- [`menuitemradio`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role)
- [`option`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/option_role)
- [`radio`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radio_role)
- [`radiogroup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radiogroup_role)
- [`row`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/row_role)
- [`rowheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowheader_role)
- [`searchbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/searchbox_role)
- [`select`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/select_role)
- [`slider`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/slider_role)
- [`spinbutton`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/spinbutton_role)
- [`switch`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/switch_role)
- [`tablist`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tablist_role)
- [`textbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role)
- [`toolbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/toolbar_role)
- [`tree`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tree_role)
- [`treegrid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treegrid_role)
- [`treeitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treeitem_role)

## مشخصات

{{Specifications}}

## همچنین ببینید

- [ایجاد دکمه‌های غیرفعال فراگیرتر](https://css-tricks.com/making-disabled-buttons-more-inclusive/) نوشته ساندرینا پریرا
- [استایل‌دهی برای کنتراست بالای ویندوز با استانداردهای جدید رنگ‌های اجباری](https://blogs.windows.com/msedgedev/2020/09/17/styling-for-windows-high-contrast-with-new-standards-for-forced-colors/)
- [disabled](/en-US/docs/Web/HTML/Reference/Attributes/disabled)
- {{domxref("Element.ariaDisabled")}}
- {{domxref("ElementInternals.ariaDisabled")}}
- [`aria-hidden`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-hidden)
- [`aria-readonly`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-readonly)