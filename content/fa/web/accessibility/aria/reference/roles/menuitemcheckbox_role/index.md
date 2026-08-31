---
title: "ARIA: menuitemcheckbox role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: menuitemcheckbox role"
short-title: menuitemcheckbox
slug: Web/Accessibility/ARIA/Reference/Roles/menuitemcheckbox_role
page-type: aria-role
spec-urls:
  - https://w3c.github.io/aria/#menuitemcheckbox
  - https://www.w3.org/WAI/ARIA/apg/patterns/menubar/examples/menubar-navigation/
sidebar: accessibilitysidebar
---

یک `menuitemcheckbox` یک `menuitem` با حالت علامت‌پذیر است که مقادیر ممکن آن `true`، `false` یا `mixed` هستند.

## توضیحات

آیتم‌های موجود در منوها و نوارهای منو، آیتم‌های منو هستند. سه نوع آیتم منو وجود دارد: [`menuitem`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitem_role)، [`menuitemradio`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role) و `menuitemcheckbox`.

این سه عنصر فقط می‌توانند در یک عنصر با نقش [`menu`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menu_role) یا [`menubar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menubar_role) قرار گیرند یا متعلق به آن باشند، و به‌صورت اختیاری در یک عنصر گروه‌بندی با نقش [`group`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role) تودرتو شوند. تودرتو بودن یا به شکل دیگری متعلق بودن (به [`aria-owns`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-owns) مراجعه کنید) به یک `menu` یا `menubar`، آیتم‌های منو را به‌عنوان ویجت‌های مرتبط شناسایی می‌کند.

آیتم‌های منو، از جمله عناصر `menuitemcheckbox`، ممکن است در عناصر `group` گروه‌بندی شوند یا با عناصری که نقش `separator` دارند یا سایر نقش‌های بومی معادل مانند {{HTMLElement('fieldset')}} و {{HTMLElement('hr')}} از هم جدا شوند.

آیتم‌های منویی که نقش `menuitemcheckbox` را دارند باید ویژگی [`aria-checked`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-checked) را شامل شوند تا حالت چک‌باکس را در معرض فناوری کمکی قرار دهند، مگر اینکه از [`<input type="checkbox">`](/en-US/docs/Web/HTML/Reference/Elements/input/checkbox) استفاده شود که در آن صورت باید از ویژگی [`checked`](/en-US/docs/Web/HTML/Reference/Elements/input/checkbox#checked) استفاده کرد.

مشابه ویژگی `checked` در {{HTMLElement('input')}} های نوع `checkbox`، ویژگی `aria-checked` یک `menuitemcheckbox` نشان می‌دهد که آیتم منو علامت خورده است (`true`)، علامت نخورده است (`false`)، یا نمایانگر یک زیرمنو از سایر آیتم‌های منو است که ترکیبی از مقادیر علامت‌خورده و علامت‌نخورده دارند (`mixed`). مقدار `mixed` مشابه ویژگی [`indeterminate`](/en-US/docs/Web/HTML/Reference/Elements/input/checkbox#indeterminate_state_checkboxes) چک‌باکس است که ظاهر حالت سومی را می‌دهد که نه علامت‌خورده و نه علامت‌نخورده است.

یک نام دسترس‌پذیر الزامی است. در حالت ایده‌آل، نام دسترس‌پذیر باید از یک عنصر {{htmlelement('label')}} مرتبط، در صورت استفاده از `<input type="checkbox">`، یا از محتوای نمایان و فرزند بیاید. توجه داشته باشید که اگر برچسب یا محتوای فرزند کافی نباشد و ترجیحاً از [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) برای ارجاع به محتوای غیرفرزند استفاده شود یا از [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) استفاده شود، این دو ویژگی ARIA سایر محتوای فرزند را از فناوری‌های کمکی پنهان خواهند کرد.

اگر همه عناصر مجموعه در DOM حضور ندارند، ویژگی‌های [`aria-setsize`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-setsize) و [`aria-posinset`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-posinset) را لحاظ کنید. هنگام تعیین `aria-setsize` و `aria-posinset` روی یک `menuitemcheckbox`، مقدار را بر اساس تعداد کل آیتم‌های منو، به‌جز هرگونه جداکننده، تنظیم کنید.

عنصر `menuitemcheckbox` می‌تواند محتوای عبارتی (phrasing content) داشته باشد، اما نمی‌تواند محتوای تعاملی به‌عنوان فرزند داشته باشد و هیچ فرزندی با ویژگی `tabindex` مشخص‌شده نیز نداشته باشد.

### همهٔ فرزندان، نمایشی هستند

برخی از انواع اجزای رابط کاربری، وقتی در یک API دسترس‌پذیری پلتفرم نمایش داده می‌شوند، فقط می‌توانند متن داشته باشند. APIهای دسترس‌پذیری راهی برای نمایش عناصر معنایی موجود در یک `menuitemcheckbox` ندارند. برای مقابله با این محدودیت، مرورگرها به‌طور خودکار نقش [`presentation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role) را به همه عناصر فرزند هر عنصر `menuitemcheckbox` اعمال می‌کنند، زیرا این نقشی است که فرزندان معنایی را پشتیبانی نمی‌کند.

برای مثال، عنصر `menuitemcheckbox` زیر را در نظر بگیرید که شامل یک عنوان است.

```html
<div role="menuitemcheckbox"><h6>Name of my checkbox</h6></div>
```

چون فرزندان `menuitemcheckbox` نمایشی هستند، کد زیر معادل است:

```html
<div role="menuitemcheckbox">
  <h6 role="presentation">Name of my checkbox</h6>
</div>
```

از دید کاربر فناوری کمکی، عنوان وجود ندارد، زیرا قطعه‌کدهای قبلی با مورد زیر در [درخت دسترس‌پذیری](/en-US/docs/Glossary/Accessibility_tree) معادل هستند:

```html
<div role="menuitemcheckbox">Name of my checkbox</div>
```

### نقش‌ها، حالت‌ها و ویژگی‌های WAI-ARIA مرتبط

- نقش [`menu`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menu_role)
  - : ویجتی که فهرستی از اقدامات یا عملکردهای رایج را ارائه می‌دهد که کاربر می‌تواند آن‌ها را فراخوانی کند.
- نقش [`menubar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menubar_role)
  - : مشابه `menu` برای مجموعه‌ای ثابت از فرمان‌های پرکاربرد که همواره قابل مشاهده هستند و معمولاً به‌صورت افقی نمایش داده می‌شوند.
- نقش [`group`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role)
  - : ظرفی برای گروهی از عناصر `menuitem`، از جمله عناصر `menuitemcheckbox` درون یک `menu` یا `menubar`.
- [`aria-checked`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-checked) (الزامی)
  - : روی `true`، `false` یا `mixed` تنظیم می‌شود و حالت «علامت‌خورده» فعلی menuitemcheckbox را نشان می‌دهد.

### تعاملات صفحه‌کلید

وقتی یک `menu` باز می‌شود، یا وقتی یک `menubar` فوکوس می‌گیرد، فوکوس صفحه‌کلید روی اولین آیتم قرار می‌گیرد. همه آیتم‌ها در هر دو، از جمله همه عناصر `menuitemcheckbox`، فوکوس‌پذیر هستند.

اگر `menuitemcheckbox` در یک زیرمنو در `menubar` یا در منویی باشد که با دکمه منو باز شده است، تعاملات صفحه‌کلید زیر باید برنامه‌ریزی شوند:

- <kbd>Enter</kbd>
  - : حالت `aria-checked` آیتم `menuitemcheckbox` را تغییر می‌دهد و منو را می‌بندد.
- <kbd>Space</kbd>
  - : حالت `aria-checked` آیتم `menuitemcheckbox` را تغییر می‌دهد. منو را نمی‌بندد.
- <kbd>Escape</kbd>
  - : منو را می‌بندد. در menubar، فوکوس را به آیتم والد menubar منتقل می‌کند.
- <kbd>Right Arrow</kbd>
  - : زیرمنو را می‌بندد. در menubar، فوکوس را به آیتم بعدی در menubar منتقل می‌کند و در صورت وجود زیرمنو، آن را باز می‌کند.
- <kbd>Left Arrow</kbd>
  - : منو را می‌بندد. در menubar، فوکوس را به آیتم قبلی در menubar منتقل می‌کند و در صورت وجود زیرمنو، آن را باز می‌کند.
- <kbd>Down Arrow</kbd>
  - : فوکوس را به آیتم بعدی در منو منتقل می‌کند. اگر فوکوس روی آخرین آیتم باشد، فوکوس به اولین آیتم منتقل می‌شود.
- <kbd>Up Arrow</kbd>
  - : فوکوس را به آیتم قبلی در منو منتقل می‌کند. اگر فوکوس روی اولین آیتم باشد، فوکوس به آخرین آیتم منتقل می‌شود.
- <kbd>Home</kbd>
  - : فوکوس را به اولین آیتم در منو منتقل می‌کند.
- <kbd>End</kbd>
  - : فوکوس را به آخرین آیتم در منو منتقل می‌کند.
- <kbd>Character</kbd>
  - : فوکوس را به آیتم بعدی که نامش با نویسه تایپ‌شده شروع می‌شود منتقل می‌کند. اگر هیچ‌یک از آیتم‌ها نامی نداشته باشند که با نویسه تایپ‌شده شروع شود، فوکوس جابه‌جا نمی‌شود.

### جاوااسکریپت موردنیاز

#### کنترل‌کننده‌های رویداد موردنیاز

- `onclick`
  - : کلیک‌های ماوس را روی چک‌باکس و برچسب مرتبط مدیریت می‌کند. این کار با تغییر مقدار ویژگی `aria-checked` و ظاهر چک‌باکس، حالت آن را تغییر می‌دهد تا برای کاربر بینا علامت‌خورده یا علامت‌نخورده به نظر برسد.
- `onKeyDown`
  - : حالتی را مدیریت می‌کند که کاربر کلید <kbd>Space</kbd> را فشار می‌دهد تا با تغییر مقدار ویژگی `aria-checked` و ظاهر چک‌باکس، حالت چک‌باکس تغییر کند و برای کاربر بینا علامت‌خورده یا علامت‌نخورده به نظر برسد. همچنین همه کلیدهای ذکرشده در بخش پیمایش صفحه‌کلید بالا را مدیریت می‌کند.

## مثال‌ها

```html
<li role="menuitemcheckbox" tabindex="-1" aria-checked="false">Purple</li>
```

ویژگی [`tabindex="-1"`](/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex) باعث می‌شود `menuitemcheckbox` فوکوس‌پذیر باشد اما بخشی از توالی تب صفحه نباشد. اگر `aria-checked="true"` را گنجانده بودیم، نشان می‌داد که `menuitemcheckbox` علامت خورده است و با استفاده از انتخاب‌گر ویژگی `[role='menuitemcheckbox'][aria-checked='true']` حالت انتخاب‌شده را به‌صورت بصری علامت‌خورده استایل می‌دادیم. در عوض، وجود `aria-checked="false"` به فناوری‌های کمکی نشان می‌دهد که `menuitemcheckbox` قابل علامت‌گذاری است اما در حال حاضر علامت نخورده است. نام دسترس‌پذیر «purple» از محتوا می‌آید.

نمای بصری حالت انتخاب‌شده، یک چک‌باکس علامت‌خورده است که می‌توانیم با استفاده از [محتواهای تولیدشده](/en-US/docs/Web/CSS/Guides/Generated_content) آن را ایجاد کنیم و با همگام‌سازی با مقدار `aria-checked` به کمک [انتخاب‌گرهای ویژگی](/en-US/docs/Web/CSS/Reference/Selectors/Attribute_selectors) و [ارث‌بری](/en-US/docs/Web/CSS/Reference/Values/inherit) رنگ، آن را قابل مشاهده و هم‌رنگ محتوا کنیم.

```css
[role="menuitemcheckbox"]::before {
  display: inline-block;
  content: "";
  color: transparent;
  width: 1em;
  text-align: center;
  outline: 1px solid;
  margin-inline-end: 2px;
  font-family: sans-serif;
}
[role="menuitemcheckbox"][aria-checked="true"]::before {
  color: inherit;
  content: "X";
}
```

### HTML را ترجیح دهید

اولین قانون ARIA این است: اگر یک عنصر یا ویژگی HTML بومی دارای معناشناسی و رفتاری است که به آن نیاز دارید، به‌جای تغییر کاربری یک عنصر و افزودن نقش، حالت یا ویژگی ARIA برای دسترس‌پذیر کردن آن، از همان عنصر یا ویژگی استفاده کنید. بنابراین، توصیه می‌شود به‌جای بازسازی عملکرد چک‌باکس با جاوااسکریپت و ARIA، از کنترل فرم بومی [چک‌باکس HTML](/en-US/docs/Web/HTML/Reference/Elements/input/checkbox) استفاده کنید.

## مشخصات

{{Specifications}}

## همچنین ببینید

- [نقش `menuitemradio`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/menuitemradio_role)
- [نقش `checkbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/checkbox_role)
- [`<input type="checkbox">`](/en-US/docs/Web/HTML/Reference/Elements/input/checkbox)