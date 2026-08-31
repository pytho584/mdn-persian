---
title: "ARIA: menu role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menu_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: menu role"
short-title: menu
slug: Web/Accessibility/ARIA/Reference/Roles/menu_role
page-type: aria-role
spec-urls:
  - https://w3c.github.io/aria/#menu
  - https://www.w3.org/WAI/ARIA/apg/patterns/menubar/examples/menubar-navigation/
sidebar: accessibilitysidebar
---

نقش `menu` نوعی ویجت ترکیبی است که فهرستی از گزینه‌ها را به کاربر ارائه می‌دهد.

## توضیحات

یک `menu` معمولاً نشان‌دهنده گروه‌بندی از اقدامات یا عملکردهای رایج است که کاربر می‌تواند آن‌ها را فراخوانی کند. نقش `menu` زمانی مناسب است که فهرستی از آیتم‌های منو به‌گونه‌ای مشابه منوی یک برنامه دسکتاپ ارائه شود. زیرمنوها که به منوهای پاپ‌آپ نیز معروف هستند، نقش `menu` را دارند.

در حالی که اصطلاح "menu" به‌طور کلی برای توصیف پیمایش سایت استفاده می‌شود، نقش `menu` برای فهرستی از اقدامات یا عملکردهایی است که نیاز به قابلیت پیچیده دارند، مانند مدیریت فوکوس ویجت ترکیبی و پیمایش با حرف اول.

یک منو می‌تواند فهرستی دائماً قابل مشاهده از کنترل‌ها یا یک ویجت باشد که می‌توان آن را باز و بسته کرد. یک ویجت `menu` بسته معمولاً با فعال کردن دکمه منو، انتخاب یک آیتم در منویی که یک زیرمنو را باز می‌کند، یا با فراخوانی یک دستور مانند <kbd>Shift + F10</kbd> در ویندوز که یک منوی متنی را باز می‌کند، باز یا قابل مشاهده می‌شود.

هنگامی که کاربر گزینه‌ای را در یک منوی باز شده فعال می‌کند، منو معمولاً بسته می‌شود. اگر عمل انتخاب منو یک زیرمنو را فراخوانی کند، منو باز می‌ماند و زیرمنو نمایش داده می‌شود.

هنگامی که یک منو باز می‌شود، فوکوس صفحه‌کلید روی اولین آیتم منو قرار می‌گیرد. برای دسترسی‌پذیری با صفحه‌کلید، باید [فوکوس را مدیریت کنید](https://primer.style/accessibility/design-guidance/focus-management/) برای همه فرزندان: همه آیتم‌های منو درون `menu` قابل فوکوس هستند. دکمه منو که منو را باز می‌کند و آیتم‌های منو، به جای خود منو، عناصر قابل فوکوس هستند.

آیتم‌های منو شامل [`menuitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitem_role)، [`menuitemcheckbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role) و [`menuitemradio`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role) هستند. آیتم‌های منوی [غیرفعال](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-disabled) قابل فوکوس هستند اما نمی‌توان آن‌ها را فعال کرد.

آیتم‌های منو می‌توانند در عناصری با نقش [`group`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role) گروه‌بندی شوند و با عناصری با نقش [`separator`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/separator_role) از هم جدا شوند. نه `group` و نه `separator` فوکوس دریافت نمی‌کنند و تعاملی نیستند.

اگر یک `menu` در نتیجه یک عمل زمینه‌ای باز شود، <kbd>Escape</kbd> یا <kbd>Enter</kbd> ممکن است فوکوس را به زمینه فراخواننده بازگردانند. اگر فوکوس روی دکمه منو بود، <kbd>Enter</kbd> منو را باز کرده و فوکوس را به اولین آیتم منو می‌دهد. اگر فوکوس روی خود منو باشد، <kbd>Escape</kbd> منو را بسته و فوکوس را به دکمه منو یا آیتم منوی والد (یا عمل زمینه‌ای که منو را باز کرد) برمی‌گرداند.

عناصر با نقش `menu` به‌طور ضمنی دارای مقدار [`aria-orientation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-orientation) برابر `vertical` هستند. برای منوی افقی، از [`aria-orientation="horizontal"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-orientation) استفاده کنید.

اگر منو از نظر بصری پایدار است، به جای آن نقش [`menubar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menubar_role) را در نظر بگیرید.

### نقش‌ها، حالت‌ها و ویژگی‌های مرتبط WAI-ARIA

- نقش‌های [`menuitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitem_role)، [`menuitemcheckbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role) و [`menuitemradio`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role)
  - : نقش‌هایی از آیتم‌های موجود در یک `menu` یا `menubar` که به طور جمعی «آیتم‌های منو» نامیده می‌شوند. این آیتم‌ها باید قادر به دریافت فوکوس باشند.
- نقش [`group`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role)
  - : آیتم‌های منو می‌توانند در یک [`group`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role) تودرتو شوند.
- نقش [`separator`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/separator_role)
  - : یک جداکننده که بخش‌های محتوا یا گروه‌های آیتم‌های منو را درون منو از هم جدا و متمایز می‌کند.
- ویژگی [`tabindex`](/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex)
  - : ظرف `menu` دارای `tabindex` برابر `-1` یا `0` است و هر آیتم در منو دارای `tabindex` برابر `-1` است.
- [`aria-activedescendant`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-activedescendant)
  - : به شناسه آیتم متمرکز شده تنظیم می‌شود، در صورت وجود.
- [`aria-orientation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-orientation)
  - : نشان می‌دهد که جهت‌گیری منو افقی است یا عمودی؛ در صورت عدم ذکر، پیش‌فرض `vertical` است.
- [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) یا [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby)
  - : `menu` باید دارای یک نام دسترس‌پذیر باشد. اگر یک برچسب قابل مشاهده وجود دارد از `aria-labelledby` استفاده کنید، در غیر این صورت از `aria-label` استفاده کنید. یا `aria-labelledby` را روی `id` `menuitem` یا `button` که نمایش آن را کنترل می‌کند تنظیم کنید، یا از `aria-label` برای تعریف برچسب استفاده کنید.
- [`aria-owns`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-owns)
  - : فقط روی ظرف منو تنظیم می‌شود تا عناصری را که فرزندان DOM ظرف نیستند شامل شود. در صورت تنظیم، آن عناصر به ترتیب ارجاع و پس از هر آیتمی که فرزند DOM است در ترتیب خواندن ظاهر می‌شوند. هنگام مدیریت فوکوس، اطمینان حاصل کنید که ترتیب فوکوس بصری با این ترتیب خواندن فناوری کمکی مطابقت دارد.

### تعاملات صفحه‌کلید

- <kbd>Space</kbd> / <kbd>Enter</kbd>
  - : اگر آیتم یک آیتم منوی والد باشد، زیرمنو را باز کرده و فوکوس را به اولین آیتم در زیرمنو منتقل می‌کند. در غیر این صورت، آیتم منو را فعال می‌کند که محتوای جدید را بارگذاری کرده و فوکوس را روی عنوانی که محتوا را عنوان‌گذاری می‌کند قرار می‌دهد.
- <kbd>Escape</kbd>
  - : هنگامی که در یک زیرمنو هستید، زیرمنو را بسته و فوکوس را به منوی والد یا آیتم menubar منتقل می‌کند.
- <kbd>Right Arrow</kbd>
  - : در یک menubar، فوکوس را به آیتم بعدی در menubar منتقل می‌کند. اگر فوکوس روی آخرین آیتم باشد، فوکوس را به اولین آیتم منتقل می‌کند. اگر در یک زیرمنو باشد و فوکوس روی آیتمی باشد که زیرمنو ندارد، زیرمنو را بسته و فوکوس را به آیتم بعدی در menubar منتقل می‌کند. در غیر این صورت، زیرمنوی آیتم menubar تازه متمرکز شده را باز کرده و فوکوس را روی آن آیتم menubar والد نگه می‌دارد. اگر در menubar یا زیرمنو نباشد و روی یک `menuitem` با زیرمنو نباشد، اگر فوکوس آخرین عنصر قابل فوکوس در منو نباشد، به صورت اختیاری فوکوس را به عنصر قابل فوکوس بعدی منتقل می‌کند.
- <kbd>Left Arrow </kbd>
  - : فوکوس را به آیتم قبلی در menubar منتقل می‌کند. اگر فوکوس روی اولین آیتم باشد، فوکوس را به آخرین آیتم منتقل می‌کند. اگر در یک زیرمنو باشد، زیرمنو را بسته و فوکوس را به آیتم منوی والد منتقل می‌کند. اگر در menubar یا زیرمنو نباشد، اگر فوکوس اولین عنصر قابل فوکوس در منو نباشد، به صورت اختیاری فوکوس را به آخرین عنصر قابل فوکوس منتقل می‌کند.
- <kbd>Down Arrow</kbd>
  - : زیرمنو را باز کرده و فوکوس را به اولین آیتم در زیرمنو منتقل می‌کند.
- <kbd>Up Arrow</kbd>
  - : زیرمنو را باز کرده و فوکوس را به آخرین آیتم در زیرمنو منتقل می‌کند.
- <kbd>Home</kbd>
  - : فوکوس را به اولین آیتم در menubar منتقل می‌کند.
- <kbd>End</kbd>
  - : فوکوس را به آخرین آیتم در menubar منتقل می‌کند.
- هر کلید کاراکتری
  - : فوکوس را به آیتم بعدی در menubar که نام آن با کاراکتر تایپ شده شروع می‌شود منتقل می‌کند. اگر هیچ کدام از آیتم‌ها نامی با کاراکتر تایپ شده نداشته باشند، فوکوس حرکت نمی‌کند.

## مثال‌ها

در زیر دو پیاده‌سازی مثال از منو آورده شده است.

### مثال ۱: منوی پیمایش

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

برای بهبود تدریجی این ویجت پیمایش که به‌طور پیش‌فرض دسترس‌پذیر است، کلاس مخفی‌سازی `menu` و افزودن `tabindex="-1"` روی محتوای تعاملی menuitem باید با جاوااسکریپت هنگام بارگذاری اضافه شود.

هنگام گنجاندن یک «menu» برای پیمایش سایت، از نقش `menu` استفاده نکنید. بلکه برای پیمایش اصلی سایت از عنصر بومی HTML {{HTMLElement('nav')}} یا صرفاً یک فهرست از پیوندها استفاده کنید. نقش `menu` باید برای ویجت‌های ترکیبی که نیاز به مدیریت فوکوس دارند محفوظ بماند. برای توضیح و مثال‌های بیشتر به [روش‌های ARIA برای پیمایش افشا](https://www.w3.org/WAI/ARIA/apg/patterns/disclosure/examples/disclosure-navigation/) مراجعه کنید.

### مثال ۲: انتخاب‌گر گزینه زیرمنوی menubar

قطعه کد زیر یک منوی پاپ‌آپ است که در یک menubar تودرتو شده است. وقتی دکمه منو فعال شود نمایش داده می‌شود. این منویی برای انتخاب رنگ متن از فهرستی از گزینه‌های رنگی است:

```html
<div>
  <button
    type="button"
    aria-haspopup="menu"
    aria-controls="colormenu"
    tabindex="0"
    aria-label="Text Color: purple">
    Purple
  </button>
  <ul role="menu" id="colormenu" aria-label="Color Options" tabindex="-1">
    <li
      role="menuitemradio"
      aria-checked="true"
      style="color: purple"
      tabindex="-1">
      Purple
    </li>
    <li
      role="menuitemradio"
      aria-checked="false"
      style="color: magenta"
      tabindex="-1">
      Magenta
    </li>
    <li
      role="menuitemradio"
      aria-checked="false"
      style="color: black;"
      tabindex="-1">
      Black
    </li>
  </ul>
</div>
```

دکمه‌ای که منو را باز می‌کند دارای [`aria-haspopup="menu"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-haspopup) است که به صراحت نشان می‌دهد پاپ‌آپی که کنترل می‌کند یک `menu` است.

برای باز شدن یک منو، کاربر معمولاً با یک دکمه منو به عنوان بازکننده تعامل می‌کند. دکمه منو باید قابل فوکوس باشد و به رویدادهای کلیک و صفحه‌کلید پاسخ دهد. هنگامی که متمرکز است، انتخاب <kbd>Enter</kbd>، <kbd>Space</kbd>، <kbd>Down Arrow</kbd> یا <kbd>Up Arrow</kbd> باید منو را باز کرده و فوکوس را روی یک آیتم منو قرار دهد.

باز و بسته شدن منو باعث تغییر ویژگی [`aria-expanded="true"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-expanded) روی دکمه می‌شود. این ویژگی زمانی که منو باز است اضافه می‌شود. هنگامی که منو بسته است حذف می‌شود یا به `false` تنظیم می‌شود. مقدار `true` نشان می‌دهد که منو نمایش داده شده است و فعال کردن دکمه منو آن را می‌بندد.

هنگامی که منو باز است، خود دکمه معمولاً فوکوس دریافت نمی‌کند زیرا کاربران با کلیدهای جهت‌نما در میان آیتم‌های منو حرکت می‌کنند. بلکه <kbd>Escape</kbd> و به صورت اختیاری <kbd>Shift + Tab</kbd> منو را بسته و فوکوس را به دکمه منو برمی‌گرداند.

نقش `menu` روی {{HTMLElement('ul')}} تنظیم شد که عنصر `<ul>` را به عنوان یک منو شناسایی می‌کند.

نمایش و مخفی‌سازی منو می‌تواند با CSS انجام شود. به عنوان مثال، در این مثال‌های کد می‌توانیم از انتخاب‌گرهای ویژگی و خواهر و برادر بعدی برای تغییر وضعیت دید منو استفاده کنیم:

```css
[role="menu"] {
  display: none;
}
[aria-expanded="true"] + [role="menu"] {
  display: block;
}
```

مثال پیمایش دارای یک دکمه ایستا است. مثال زیرمنو دارای یک دکمه است که با انتخاب مقدار جدید توسط کاربر به‌روزرسانی می‌شود. در این مورد، `aria-label="Text Color: purple"` روی عنصر `menu` تنظیم شده است. این نام دسترس‌پذیر برای منو را به عنوان "رنگ متن: بنفش" تعریف می‌کند؛ هدف منو (انتخاب رنگ متن) و مقدار فعلی (بنفش) را شناسایی می‌کند. هنگامی که یک رنگ جدید انتخاب می‌شود، مقدار ویژگی `aria-label` نیز باید به‌روزرسانی شود.

## مشخصات

{{Specifications}}

## همچنین ببینید

- [`menubar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menubar_role)
- [`menuitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitem_role)
- [`menuitemcheckbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role)
- [`menuitemradio`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role)
- [`aria-haspopup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-haspopup)