```
---
title: "ARIA: menuitem role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitem_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: menuitem role"
short-title: menuitem
slug: Web/Accessibility/ARIA/Reference/Roles/menuitem_role
page-type: aria-role
spec-urls:
  - https://w3c.github.io/aria/#menuitem
  - https://www.w3.org/WAI/ARIA/apg/patterns/menubar/examples/menubar-navigation/
sidebar: accessibilitysidebar
---

نقش `menuitem` نشان می‌دهد که عنصر یک گزینه در مجموعه‌ای از انتخاب‌ها است که توسط یک `menu` یا `menubar` نگهداری می‌شود.

## توضیحات

یک `menuitem` یکی از سه نوع گزینه در مجموعه‌ای از انتخاب‌ها است که توسط یک [`menu`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menu_role) یا [`menubar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menubar_role) نگهداری می‌شود؛ دو نوع دیگر [`menuitemcheckbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role) و [`menuitemradio`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role) هستند. `menuitem` فقط به‌عنوان فرزند یا متعلق به عناصری با نقش `menu` یا `menubar` یافت می‌شود، و به‌صورت اختیاری در داخل یک عنصر با نقش [`group`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role) قرار می‌گیرد که در یک منو نگهداری می‌شود یا متعلق به آن است.

اگر `menuitem` در DOM فرزند یک منو نباشد، ویژگی [`aria-owns`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-owns) را روی منو قرار دهید تا رابطه را نشان دهید. اگر `aria-owns` روی ظرف منو تنظیم شود تا عناصری که فرزندان DOM آن ظرف نیستند را شامل شود، آن عناصر در ترتیب خواندن به ترتیب ارجاع و پس از هر آیتمی که فرزند DOM هستند در فناوری‌های کمکی ظاهر می‌شوند. اطمینان حاصل کنید که ترتیب فوکوس دیداری با ترتیب خواندن فناوری کمکی مطابقت دارد.

هر `menuitem` در یک منو قابل فوکوس است، چه غیرفعال باشد چه نباشد. برای نشان دادن غیرفعال بودن یک `menuitem`، ویژگی [`aria-disabled="true"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-disabled) را روی عنصر دارای این نقش تنظیم کنید.

اگر یک `menuitem` زیرمنو دارد، آن را طوری برنامه‌ریزی کنید که هنگام فعال شدن آیتم منو، یک زیرمنوی جدید نمایش دهد و [`aria-haspopup="menu"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-haspopup) یا مقدار `true` را شامل شود تا به فناوری‌های کمکی نشان دهد که آیتم منو برای باز کردن زیرمنو استفاده می‌شود.

یک قرارداد رایج برای نشان دادن اینکه یک `menuitem` یک کادر گفتگو را باز می‌کند، افزودن «…» (بیضی) به برچسب آیتم منو است، به عنوان مثال «Save as …».

هر `menuitem` باید یک نام قابل دسترس داشته باشد. این نام به‌طور پیش‌فرض از محتویات عنصر می‌آید. اگر محتویات نام قابل دسترس مفیدی ارائه ندهند، می‌توان از [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) برای ارجاع به برچسب قابل مشاهده استفاده کرد. اگر محتوای قابل مشاهده‌ای برای ارائه نام قابل دسترس موجود نباشد، می‌توان نام قابل دسترس را با [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) ارائه کرد.

### نقش‌ها، حالت‌ها و ویژگی‌های مرتبط WAI-ARIA

- [نقش \`menu\`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menu_role)
  - : ویجتی که فهرستی از انتخاب‌ها را ارائه می‌دهد. نقش زمینه‌ای الزامی (یا `menubar`)
- [نقش \`menubar\`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menubar_role)
  - : نمایشی از یک `menu` که معمولاً قابل مشاهده باقی می‌ماند و معمولاً به‌صورت افقی ارائه می‌شود. نقش زمینه‌ای الزامی (یا `menu`)
- [نقش \`group\`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role)
  - : می‌تواند برای شناسایی مجموعه‌ای از `menuitem`های مرتبط در داخل یا متعلق به یک `menu` یا `menubar` استفاده شود.
- [`aria-disabled`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-disabled)
  - : نشان می‌دهد که عنصر قابل درک است اما غیرفعال است، بنابراین قابل اجرا نیست.
- [`aria-haspopup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-haspopup)
  - : نشان‌دهنده دسترس‌پذیری و نوع پنجره بازشوی تعاملی است که می‌تواند توسط `menuitem` فعال شود.

### تعاملات صفحه‌کلید

- <kbd>Enter</kbd> و <kbd>Space</kbd>
  - : اگر `menuitem` زیرمنو داشته باشد، زیرمنو را باز کرده و فوکوس را روی اولین آیتم آن قرار می‌دهد. در غیر این صورت، آیتم را فعال کرده و منو را می‌بندد.
- <kbd>Down Arrow</kbd>
  - : روی یک `menuitem` که در یک `menubar` زیرمنو دارد، زیرمنو را باز کرده و فوکوس را روی اولین آیتم زیرمنو قرار می‌دهد. در غیر این صورت، فوکوس را به آیتم بعدی می‌برد، و به‌صورت اختیاری از آخر به اول چرخش می‌کند.
- <kbd>Up Arrow</kbd>
  - : فوکوس را به آیتم قبلی می‌برد، و به‌صورت اختیاری از اول به آخر چرخش می‌کند. به‌صورت اختیاری، اگر `menuitem` در یک menubar باشد و زیرمنو داشته باشد، زیرمنو را باز کرده و فوکوس را روی آخرین آیتم زیرمنو قرار می‌دهد.
- <kbd>Right Arrow</kbd>
  - : اگر در یک `menu` که با یک دکمه منو باز شده و در یک `menubar` نباشد، اگر menuitem زیرمنو نداشته باشد، هیچ کاری نمی‌کند. وقتی فوکوس در یک `menubar` است، فوکوس را به آیتم بعدی می‌برد، و به‌صورت اختیاری از آخر به اول چرخش می‌کند. وقتی فوکوس در یک `menu` و روی یک `menuitem` است که زیرمنو دارد، زیرمنو را باز کرده و فوکوس را روی اولین آیتم آن قرار می‌دهد. وقتی فوکوس در یک `menu` و روی آیتمی است که زیرمنو ندارد، زیرمنو و هر منوی والد را می‌بندد، فوکوس را به آیتم بعدی در `menubar` می‌برد، و اگر فوکوس حالا روی یک `menuitem` با زیرمنو است، یا زیرمنوی آن `menuitem` را بدون حرکت فوکوس به داخل زیرمنو باز می‌کند، یا زیرمنوی آن `menuitem` را باز کرده و فوکوس را روی اولین آیتم زیرمنو قرار می‌دهد.
- <kbd>Left Arrow</kbd>
  - : وقتی فوکوس در یک `menubar` است، فوکوس را به آیتم قبلی می‌برد، و به‌صورت اختیاری از اول به آخر چرخش می‌کند. وقتی فوکوس در زیرمنوی یک آیتم در یک منو است، زیرمنو را می‌بندد و فوکوس را به `menuitem` والد بازمی‌گرداند. وقتی فوکوس در زیرمنوی یک آیتم در یک `menubar` است، زیرمنو را می‌بندد، فوکوس را به آیتم قبلی در `menubar` می‌برد، و اگر فوکوس حالا روی یک `menuitem` با زیرمنو است، یا زیرمنوی آن `menuitem` را بدون حرکت فوکوس به داخل زیرمنو باز می‌کند، یا زیرمنوی آن `menuitem` را باز کرده و فوکوس را روی اولین آیتم زیرمنو قرار می‌دهد.
- <kbd>Home</kbd>
  - : اگر چرخش با کلیدهای جهت‌نما پشتیبانی نمی‌شود، فوکوس را به اولین آیتم در `menu` یا `menubar` فعلی می‌برد.
- <kbd>End</kbd>
  - : اگر چرخش با کلیدهای جهت‌نما پشتیبانی نمی‌شود، فوکوس را به آخرین آیتم در `menu` یا `menubar` فعلی می‌برد.
- هر کلیدی که با یک کاراکتر قابل چاپ مطابقت دارد (اختیاری)
  - : فوکوس را به آیتم بعدی در منوی فعلی می‌برد که برچسب آن با آن کاراکتر قابل چاپ شروع می‌شود.
- <kbd>Escape</kbd>
  - : منوی حاوی فوکوس را ببندید و فوکوس را به عنصر یا زمینه‌ای، مانند دکمه منو یا `menuitem` والد، که منو از آن باز شده است، بازگردانید.
- <kbd>Tab</kbd>
  - : فوکوس را به عنصر بعدی در توالی تب می‌برد، و اگر آیتمی که فوکوس داشت در یک menubar نباشد، منوی آن و تمام ظروف منوی والد باز را می‌بندد.
- <kbd>Shift + Tab</kbd>
  - : فوکوس را به عنصر قبلی در توالی تب می‌برد، و اگر آیتمی که فوکوس داشت در یک menubar نباشد، منوی آن و تمام ظروف منوی والد باز را می‌بندد.

اگر یک منو باز شود یا یک نوار منو در نتیجه یک عمل زمینه‌ای فوکوس دریافت کند، <kbd>Escape</kbd> یا <kbd>Enter</kbd> ممکن است فوکوس را به زمینه فراخوان بازگرداند.

برخی پیاده‌سازی‌های نوار منوی پیمایش ممکن است عناصر menuitem داشته باشند که هم یک عملکرد را انجام می‌دهند و هم زیرمنویی را باز می‌کنند. در چنین پیاده‌سازی‌هایی، <kbd>Enter</kbd> و <kbd>Space</kbd> یک عملکرد پیمایش را انجام می‌دهند در حالی که <kbd>Down Arrow</kbd>، در یک نوار منوی افقی، زیرمنوی مرتبط با همان menuitem را باز می‌کند.

وقتی آیتم‌های یک `menubar` به‌صورت عمودی و آیتم‌های ظروف منو به‌صورت افقی چیده شده‌اند، <kbd>Down Arrow</kbd> همان عملکردی را دارد که برای <kbd>Right Arrow</kbd> در بالا توضیح داده شد، <kbd>Up Arrow</kbd> همان عملکردی را دارد که برای <kbd>Left Arrow</kbd> در بالا توضیح داده شد، و برعکس.

## نمونه‌ها

```html
<div>
  <button id="menubutton" aria-haspopup="true" aria-controls="menu">
    <img src="hamburger.svg" alt="Page Sections" />
  </button>
  <ul id="menu" role="menu" aria-labelledby="menubutton">
    <li role="presentation">
      <a role="menuitem" href="#description">Description</a>
    </li>
    <li role="presentation">
      <a
        role="menuitem"
        href="#associated_wai-aria_roles_states_and_properties">
        Associated WAI-ARIA roles, states, and properties
      </a>
    </li>
    <li role="presentation">
      <a role="menuitem" href="#keyboard_interactions">
        Keyboard interactions
      </a>
    </li>
    <li role="presentation">
      <a role="menuitem" href="#examples">Examples</a>
    </li>
    <li role="presentation">
      <a role="menuitem" href="#specifications">Specifications</a>
    </li>
    <li role="presentation">
      <a role="menuitem" href="#see_also">See Also</a>
    </li>
  </ul>
</div>
```

## مشخصات

{{Specifications}}

## همچنین ببینید

- [نقش \`menuitemcheckbox\`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role)
- [نقش \`menuitemradio\`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role)
- [نقش \`listitem\`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listitem_role)
- [نقش \`option\`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/option_role)
```