---
title: "ARIA: menuitemradio role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: menuitemradio role"
short-title: menuitemradio
slug: Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role
page-type: aria-role
spec-urls:
  - https://w3c.github.io/aria/#menuitemradio
  - https://www.w3.org/WAI/ARIA/apg/patterns/menubar/examples/menubar-navigation/
sidebar: accessibilitysidebar
---

یک `menuitemradio` یک آیتم منوی قابل بررسی در مجموعه‌ای از عناصر با نقش یکسان است که تنها یکی از آن‌ها در یک زمان می‌تواند بررسی شود.

## توضیحات

آیتم‌های موجود در منوها و نوارهای منو، آیتم‌های منو هستند. سه نوع آیتم منو وجود دارد: [`menuitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitem_role)، [`menuitemcheckbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role) و `menuitemradio`. برای محدود کردن تعداد آیتم‌های منوی بررسی‌شده به یک آیتم در یک گروه، از نقش `menuitemradio` روی همه عناصر گروه استفاده کنید.

یک `menuitemradio` یک آیتم منوی قابل بررسی در مجموعه‌ای از عناصر با نقش یکسان است که تنها یکی از آن‌ها در یک زمان می‌تواند بررسی شود.

سه عنصر آیتم منو فقط می‌توانند درون یک عنصر با نقش [`menu`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menu_role) یا [`menubar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menubar_role) قرار گیرند یا متعلق به آن باشند، و به صورت اختیاری درون یک عنصر گروه‌بندی با نقش [`group`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role) تودرتو شده باشند. تودرتو بودن یا به صورت دیگر متعلق بودن (به [`aria-owns`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-owns) مراجعه کنید) به یک `menu` یا `menubar`، آیتم‌های منو را به عنوان ویجت‌های مرتبط شناسایی می‌کند.

وقتی همه آیتم‌های یک زیرمنو اعضای یک گروه رادیویی یکسان باشند، `group` توسط عنصر منو تعریف می‌شود و عنصر `group` ضروری نیست.

آیتم‌های منوی حاوی نقش `menuitemradio` باید شامل ویژگی [`aria-checked`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-checked) باشند تا وضعیت دکمه رادیویی را برای فناوری کمکی آشکار کنند، مگر اینکه از [`<input type="radio">`](/en-US/docs/Web/HTML/Reference/Elements/input/checkbox) استفاده شود، که در این صورت باید از ویژگی [`checked`](/en-US/docs/Web/HTML/Reference/Elements/input/checkbox#checked) استفاده شود.

مشابه ویژگی `checked` در {{HTMLElement('input')}}های نوع `radio`، ویژگی `aria-checked` یک `menuitemradio` نشان می‌دهد که آیا آیتم منو بررسی شده است (`true`) یا بررسی نشده است (`false`). برخلاف `menuitemcheckbox`، مقدار `mixed` وجود ندارد.

فقط یک `menuitemradio` در یک گروه می‌تواند همزمان بررسی شود. وقتی یک آیتم در گروه بررسی می‌شود، ویژگی `aria-checked` به `true` تنظیم می‌شود، در حالی که عنصر `menuitemradio` قبلاً بررسی‌شده در همان گروه، اگر وجود داشته باشد، با تغییر مقدار ویژگی `aria-checked` به `false`، بررسی‌نشده می‌شود.

اگر می‌خواهید بیش از یک آیتم در یک گروه بررسی شود، یا می‌خواهید امکان بررسی و لغو بررسی یک آیتم را فعال کنید، از `menuitemcheckbox` استفاده کنید.

اگر یک `menu` یا `menubar` شامل بیش از یک گروه از عناصر `menuitemradio` باشد، یا اگر `menu` شامل یک گروه از عناصر `menuitemradio` به همراه سایر عناصر `menuitem` نامرتبط و/یا عناصر `menuitemcheckbox` باشد، هر مجموعه از عناصر `menuitemradio` مرتبط را در یک عنصر `group` قرار دهید یا گروه عناصر `menuitemradio` را از سایر آیتم‌های منو با یک عنصر `separator` (یا یک عنصر HTML با نقش معادل مانند یک {{HTMLElement('fieldset')}} گروه‌بندی یا یک جداکننده موضوعی {{HTMLElement('hr')}}) جدا کنید.

یک نام قابل دسترسی الزامی است. در حالت ایده‌آل، نام قابل دسترسی باید از یک عنصر {{htmlelement('label')}} مرتبط (در صورت استفاده از `<input type="radio">`) یا محتوای قابل مشاهده و فرزند به دست آید. توجه داشته باشید که اگر برچسب یا محتوای فرزند کافی نباشد و ترجیحاً از [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) با ارجاع به محتوای غیرفرزند یا [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) استفاده شود، این دو ویژگی ARIA سایر محتوای فرزند را از فناوری‌های کمکی پنهان خواهند کرد.

اگر همه عناصر موجود در مجموعه در DOM حضور ندارند، ویژگی‌های [`aria-setsize`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-setsize) و [`aria-posinset`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-posinset) را شامل کنید. هنگام مشخص کردن `aria-setsize` و `aria-posinset` روی یک `menuitemradio`، مقدار را با توجه به تعداد کل آیتم‌های موجود در منو، به استثنای هر جداکننده، تنظیم کنید.

عنصر `menuitemradio` می‌تواند محتوای عبارتی داشته باشد، اما نمی‌تواند محتوای تعاملی به عنوان فرزند داشته باشد و هیچ فرزندی با ویژگی `tabindex` مشخص شده نداشته باشد.

### همه فرزندان ارائه‌ای هستند

برخی از انواع اجزای رابط کاربری وجود دارند که وقتی در یک API دسترسی‌پذیری پلتفرم نمایش داده می‌شوند، فقط می‌توانند حاوی متن باشند. APIهای دسترسی‌پذیری راهی برای نمایش عناصر معنایی موجود در یک `menuitemradio` ندارند. برای مقابله با این محدودیت، مرورگرها به طور خودکار نقش [`presentation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role) را به همه عناصر فرزند هر عنصر `menuitemradio` اعمال می‌کنند، زیرا این نقشی است که از فرزندان معنایی پشتیبانی نمی‌کند.

به عنوان مثال، عنصر `menuitemradio` زیر را در نظر بگیرید که شامل یک عنوان است.

```html
<div role="menuitemradio"><h6>Name of my radio button</h6></div>
```

از آنجایی که فرزندان `menuitemradio` ارائه‌ای هستند، کد زیر معادل است:

```html
<div role="menuitemradio">
  <h6 role="presentation">Name of my radio button</h6>
</div>
```

از دیدگاه کاربر فناوری کمکی، عنوان وجود ندارد، زیرا قطعه کدهای قبلی با موارد زیر در [درخت دسترسی‌پذیری](/en-US/docs/Glossary/Accessibility_tree) معادل هستند:

```html
<div role="menuitemradio">Name of my radio button</div>
```

### نقش‌ها، حالت‌ها و ویژگی‌های WAI-ARIA مرتبط

- نقش [`menu`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menu_role)
  - : ویجتی که فهرستی از اقدامات یا عملکردهای رایجی را که کاربر می‌تواند فراخوانی کند، ارائه می‌دهد.
- نقش [`menubar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menubar_role)
  - : مشابه `menu` برای مجموعه‌ای ثابت از دستورات پرکاربرد که قابل مشاهده باقی می‌مانند و معمولاً به صورت افقی نمایش داده می‌شوند.
- نقش [`group`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role)
  - : ظرفی برای گروهی از عناصر `menuitem`، از جمله عناصر `menuitemradio` درون یک `menu` یا `menubar`.
- [`aria-checked`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-checked) (الزامی)
  - : تنظیم شده به `true` یا `false`، وضعیت فعلی "بررسی شده" `menuitemradio` را نشان می‌دهد.

### تعاملات صفحه‌کلید

وقتی یک `menu` باز می‌شود، یا وقتی یک `menubar` فوکوس دریافت می‌کند، فوکوس صفحه‌کلید روی اولین آیتم قرار می‌گیرد. همه آیتم‌ها در هر دو قابل فوکوس هستند، از جمله همه عناصر `menuitemradio`.

اگر `menuitemradio` در یک زیرمنو در یک `menubar` یا یک منوی باز شده با یک دکمه منو باشد، تعاملات صفحه‌کلید زیر باید برنامه‌ریزی شوند:

- <kbd>Enter</kbd>
  - : اگر بررسی نشده باشد، `menuitemradio` متمرکز را بررسی می‌کند و هر عنصر `menuitemradio` دیگری را که در همان گروه بررسی شده است، لغو بررسی می‌کند. همچنین منو را می‌بندد.
- <kbd>Space</kbd>
  - : اگر بررسی نشده باشد، `menuitemradio` متمرکز را بررسی می‌کند و هر عنصر `menuitemradio` دیگری را که در همان گروه بررسی شده است، بدون بستن منو لغو بررسی می‌کند.
- <kbd>Escape</kbd>
  - : منو را می‌بندد. در نوار منو، فوکوس را به آیتم نوار منوی والد منتقل می‌کند.
- <kbd>Right Arrow</kbd>
  - : زیرمنو را می‌بندد. در نوار منو، فوکوس را به آیتم بعدی در نوار منو منتقل می‌کند و در صورت وجود زیرمنو، آن را باز می‌کند.
- <kbd>Left Arrow</kbd>
  - : منو را می‌بندد. در نوار منو، فوکوس را به آیتم قبلی در نوار منو منتقل می‌کند و در صورت وجود زیرمنو، آن را باز می‌کند.
- <kbd>Down Arrow</kbd>
  - : فوکوس را به آیتم بعدی در منو منتقل می‌کند. اگر فوکوس روی آخرین آیتم باشد، فوکوس را به اولین آیتم منتقل می‌کند.
- <kbd>Up Arrow</kbd>
  - : فوکوس را به آیتم قبلی در منو منتقل می‌کند. اگر فوکوس روی اولین آیتم باشد، فوکوس را به آخرین آیتم منتقل می‌کند.
- <kbd>Home</kbd>
  - : فوکوس را به اولین آیتم در منو منتقل می‌کند.
- <kbd>End</kbd>
  - : فوکوس را به آخرین آیتم در منو منتقل می‌کند.
- <kbd>Character</kbd>
  - : فوکوس را به آیتم بعدی که نامی با حرف تایپ شده شروع می‌شود، منتقل می‌کند. اگر هیچ یک از آیتم‌ها نامی با حرف تایپ شده شروع نشود، فوکوس حرکت نمی‌کند.

### جاوااسکریپت مورد نیاز

#### کنترل‌کننده‌های رویداد مورد نیاز

- `onclick`
  - : کلیک‌های ماوس را روی دکمه رادیویی و برچسب مرتبط مدیریت می‌کند که وضعیت دکمه رادیویی را با تغییر مقدار ویژگی `aria-checked` و ظاهر دکمه رادیویی تغییر می‌دهد تا برای کاربر بینا به صورت بررسی‌شده یا بررسی‌نشده به نظر برسد.
- `onKeyDown`
  - : موردی را مدیریت می‌کند که کاربر کلید <kbd>Space</kbd> را برای تغییر وضعیت دکمه رادیویی با تغییر مقدار ویژگی `aria-checked` و ظاهر دکمه رادیویی فشار می‌دهد تا برای کاربر بینا به صورت بررسی‌شده یا بررسی‌نشده به نظر برسد. همچنین تمام کلیدهای ذکر شده در بخش پیمایش صفحه‌کلید بالا را مدیریت می‌کند.

## مثال‌ها

```html
<li role="menuitemradio" tabindex="-1" aria-checked="false">Purple</li>
```

[`tabindex="-1"`](/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex) باعث می‌شود `menuitemradio` قابل فوکوس باشد اما بخشی از ترتیب زبانه صفحه نباشد. اگر `aria-checked="true"` را گنجانده بودیم، نشان می‌داد که `menuitemradio` بررسی شده است، و ما حالت انتخاب‌شده را به صورت بصری با استفاده از انتخابگر ویژگی `[role='menuitemradio'][aria-checked='true']` به صورت بررسی‌شده طراحی می‌کردیم. در عوض، وجود `aria-checked="false"` به فناوری‌های کمکی نشان می‌دهد که `menuitemradio` قابل بررسی است اما در حال حاضر بررسی نشده است. نام قابل دسترسی "purple" از محتوا می‌آید.

ظاهر بصری حالت انتخاب‌شده یک دکمه رادیویی بررسی‌شده است که می‌توانیم با استفاده از [محتوای تولیدشده](/en-US/docs/Web/CSS/Guides/Generated_content) آن را ایجاد کنیم، آن را قابل مشاهده کرده و با همرنگ کردن محتوا با مقدار `aria-checked` با استفاده از [انتخابگرهای ویژگی](/en-US/docs/Web/CSS/Reference/Selectors/Attribute_selectors) CSS و تغییر {{cssxref("background-color")}} همگام‌سازی کنیم.

```css
[role="menuitemradio"]::before {
  display: inline-block;
  content: "";
  width: 1em;
  height: 1em;
  padding: 0.1em;
  border: 2px solid #333333;
  border-radius: 50%;
  box-sizing: border-box;
  background-clip: content-box;
  margin-inline-end: 2px;
}
[role="menuitemradio"][aria-checked="true"]::before {
  background-color: purple;
}
```

از ویژگی کوتاه‌نویس {{cssxref("background")}} استفاده نکنید، زیرا ویژگی {{cssxref("background-clip")}} را که برای ایجاد اثر دکمه رادیویی استفاده کرده‌ایم، لغو می‌کند.

### HTML را ترجیح دهید

اولین قانون ARIA این است: اگر یک عنصر یا ویژگی HTML بومی دارای معناشناسی و رفتاری است که نیاز دارید، از آن استفاده کنید به جای اینکه عنصری را تغییر کاربری داده و نقش، حالت یا ویژگی ARIA به آن اضافه کنید تا قابل دسترسی شود. بنابراین، توصیه می‌شود به جای بازسازی عملکرد یک دکمه رادیویی با جاوااسکریپت و ARIA، از کنترل فرم بومی [دکمه رادیویی HTML](/en-US/docs/Web/HTML/Reference/Elements/input/radio) استفاده کنید.

## مشخصات

{{Specifications}}

## همچنین ببینید

- نقش [`radio`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radio_role)
- [`<input type="radio">`](/en-US/docs/Web/HTML/Reference/Elements/input/radio)