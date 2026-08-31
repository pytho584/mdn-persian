---
title: "ARIA: radiogroup role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radiogroup_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: radiogroup role"
short-title: radiogroup
slug: Web/Accessibility/ARIA/Reference/Roles/radiogroup_role
page-type: aria-role
spec-urls:
  - https://w3c.github.io/aria/#radiogroup
  - https://www.w3.org/WAI/ARIA/apg/patterns/radio/examples/radio/
sidebar: accessibilitysidebar
---

نقش `radiogroup` گروهی از دکمه‌های `radio` است.

## توضیحات

گروه‌های رادیویی مجموعه‌ای هستند که مجموعه‌ای از گزینه‌های [`radio`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radio_role) مرتبط را توصیف می‌کنند. یک `radiogroup` نوعی فهرست [`select`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/select_role) است که در هر زمان فقط یک ورودی یا `radio` می‌تواند علامت‌خورده باشد.

هنگام استفاده از دکمه رادیویی بومی HTML، [`<input type="radio">`](/en-US/docs/Web/HTML/Reference/Elements/input/radio)، دکمه‌های رادیویی زمانی گروه‌بندی می‌شوند که به هر یک از دکمه‌های رادیویی ورودی در گروه، همان [`name`](/en-US/docs/Web/HTML/Reference/Elements/input#name) داده شود. پس از ایجاد گروهی از دکمه‌های رادیویی ورودی با نام یکسان، انتخاب هر دکمه رادیویی ورودی در آن گروه به‌طور خودکار هر دکمه رادیویی ورودیِ انتخاب‌شدهٔ فعلی را در همان گروه از انتخاب خارج می‌کند. اگرچه این کار دکمه‌های رادیویی را به هم مرتبط می‌کند، برای نمایش صریح گروهی از دکمه‌های رادیویی به‌عنوان `radiogroup`، نقش ARIA را به‌طور صریح تنظیم کنید.

توصیه می‌شود گروه‌های رادیویی با استفاده از دکمه‌های رادیویی ورودی HTML با نام یکسان ایجاد شوند، اما اگر به‌جای کنترل‌های فرم HTML معنایی باید از نقش‌ها و ویژگی‌های ARIA استفاده کنید، دکمه‌های `radio` سفارشی می‌توانند و باید مانند دکمه‌های رادیویی ورودی HTML بومی عمل کنند.

هنگام استفاده از عناصر غیرمعنایی به‌عنوان دکمه‌های رادیویی، باید مطمئن شوید که کاربران شما می‌توانند در هر زمان فقط یک دکمه رادیویی از گروه را انتخاب کنند. وقتی یک مورد در گروه علامت‌خورده است و ویژگی [`aria-checked`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-checked) آن روی `true` تنظیم شده است، مورد قبلاً انتخاب‌شده از انتخاب خارج می‌شود و ویژگی `aria-checked` آن به `false` تبدیل می‌شود. ویژگی `aria-checked` روی نقش‌های `radio` مرتبط تنظیم می‌شود، نه روی خود `radiogroup`.

برخی پیاده‌سازی‌های `radiogroup` مجموعه را با تمام دکمه‌ها در حالت بدون علامت مقداردهی اولیه می‌کنند. پس از علامت‌خورده شدن یک `radio` در یک `radiogroup`، معمولاً بازگشت به حالت تمام بدون علامت ممکن نیست.

`radiogroup` باید یک نام قابل‌دسترس داشته باشد، یا با یک برچسب قابل مشاهده که توسط [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) ارجاع داده می‌شود، یا دارای برچسبی باشد که با [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) مشخص شده است. اگر عناصری اطلاعات بیشتری درباره گروه رادیویی فراهم می‌کنند، آن عناصر توسط عنصر `radiogroup` با ویژگی [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) ارجاع داده می‌شوند.

### نقش‌ها، حالت‌ها و ویژگی‌های مرتبط WAI-ARIA

- [`radio`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radio_role) نقش
  - : یکی از گروهی از دکمه‌های قابل‌علامت، در یک `radiogroup`، که در آن در هر زمان بیش از یکی از دکمه‌ها نمی‌تواند علامت‌خورده باشد.
- [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) / [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label)
  - : `radiogroup` باید یک نام قابل‌دسترس داشته باشد، یا با یک برچسب قابل مشاهده که توسط `aria-labelledby` ارجاع داده می‌شود، یا دارای برچسبی باشد که با `aria-label` مشخص شده است.
- [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby)
  - : ارجاع به عناصری که اطلاعات بیشتری درباره `radiogroup` فراهم می‌کنند.
- [`aria-required`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-required)
  - : نشان می‌دهد که قبل از ارسال فرم، یکی از `radio`های داخل گروه باید `aria-checked="true"` تنظیم شده باشد. حالت الزامی روی عنصر `radiogroup` مشخص می‌شود نه روی یکی از عناصر `radio`، برخلاف دکمه‌های رادیویی HTML که در آن‌ها ویژگی [`required`](/en-US/docs/Web/HTML/Reference/Attributes/required) مستقیماً روی یک یا چند {{HTMLElement('input')}} رادیویی تنظیم می‌شود.
- [`aria-errormessage`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-errormessage)
  - : عنصری را که در صورت وجود خطا، پیام خطا را برای `radiogroup` فراهم می‌کند، مشخص می‌کند. آن پیام باید تا زمانی که مرتبط نیست پنهان بماند.

### تعاملات صفحه‌کلید

برای دکمه‌های `radio` در یک `radiogroup` که در یک [`toolbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/toolbar_role) نیست، تعاملات صفحه‌کلید زیر باید پشتیبانی شوند:

- <kbd>Tab</kbd> و <kbd>Shift + Tab</kbd>
  - : فوکوس را به داخل و خارج از `radiogroup` منتقل می‌کند. وقتی فوکوس وارد یک `radiogroup` می‌شود، اگر یک دکمه رادیویی علامت‌خورده باشد، فوکوس روی دکمه علامت‌خورده قرار می‌گیرد. اگر هیچ‌کدام از دکمه‌های رادیویی علامت‌خورده نباشند، فوکوس روی اولین دکمه رادیویی در گروه قرار می‌گیرد.
- <kbd>Space</kbd>
  - : دکمه رادیویی متمرکز را اگر قبلاً علامت نخورده باشد، علامت می‌زند.
- <kbd>Right Arrow</kbd> و <kbd>Down Arrow</kbd>
  - : فوکوس را به دکمه رادیویی بعدی در گروه منتقل می‌کند، دکمه قبلی را از علامت خارج می‌کند و دکمه جدید متمرکز را علامت می‌زند. اگر فوکوس روی آخرین دکمه باشد، فوکوس به اولین دکمه منتقل می‌شود.
- <kbd>Left Arrow</kbd> و <kbd>Up Arrow</kbd>
  - : فوکوس را به دکمه رادیویی قبلی در گروه منتقل می‌کند، دکمه قبلی را از علامت خارج می‌کند و دکمه جدید متمرکز را علامت می‌زند. اگر فوکوس روی اولین دکمه باشد، فوکوس به آخرین دکمه منتقل می‌شود.

از کلیدهای جهت‌نما برای پیمایش بین عناصر یک نوار ابزار استفاده می‌شود. وقتی یک `radiogroup` درون یک نوار ابزار قرار می‌گیرد، کاربران باید بتوانند بین تمام عناصر نوار ابزار، از جمله دکمه‌های رادیویی، بدون تغییر دکمه رادیویی علامت‌خورده پیمایش کنند. بنابراین، هنگام پیمایش در یک `radiogroup` در یک [`toolbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/toolbar_role) با کلیدهای جهت‌نما، دکمه‌ای که علامت‌خورده است تغییر نمی‌کند. در عوض، وقتی داخل یک `toolbar` هستید، کلیدهای <kbd>Space</kbd> و <kbd>Enter</kbd> دکمه `radio` متمرکز را اگر قبلاً علامت نخورده باشد علامت می‌زنند، و <kbd>Tab</kbd> فوکوس را به داخل و خارج از `toolbar` منتقل می‌کند.

### ویژگی‌های جاوااسکریپت مورد نیاز

تعاملات کاربر برای `radiogroup`ها باید تعامل کاربر را هنگام ورود به گروهی از دکمه‌های رادیویی HTML با نام یکسان بازتولید کنند. رویدادهای صفحه‌کلید برای Tab، Space و کلیدهای جهت‌نما باید ضبط شوند. رویدادهای کلیک روی عناصر رادیویی و برچسب‌های مرتبط با آن‌ها نیز باید ضبط شوند. علاوه بر این، [فوکوس باید مدیریت شود](https://primer.style/accessibility/design-guidance/focus-management/).

در حالی که معمولاً دور شدن از یک عنصر متمرکز شما را به عنصر قابل فوکوس بعدی در ترتیب DOM می‌برد، استفاده از کلیدهای جهت‌نما برای پیمایش در گروهی از دکمه‌های رادیویی شما را در گروه نگه می‌دارد و وقتی <kbd>Right Arrow</kbd> یا <kbd>Down Arrow</kbd> در حالی که فوکوس روی آخرین رادیو در گروه بود آزاد می‌شود، فوکوس به اولین دکمه رادیویی منتقل می‌شود و اگر <kbd>Left Arrow</kbd> یا <kbd>Up Arrow</kbd> در حالی که فوکوس روی اولین رادیو بود آزاد شود، فوکوس به آخرین رادیو منتقل می‌شود. مدیریت [`tabindex`](/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex) چرخشی یکی از روش‌های مدیریت رویدادهای کلید جهت‌نما است.

### ویژگی‌های CSS مورد نیاز

از [انتخابگر ویژگی](/en-US/docs/Web/CSS/Reference/Selectors/Attribute_selectors) `[aria-checked="true"]` برای استایل‌دهی حالت علامت‌خورده دکمه‌های رادیویی علامت‌خورده استفاده کنید.

برای استایل‌دهی فوکوس بصری صفحه‌کلید و هاور از شبه‌کلاس‌های CSS {{CSSXRef(':hover')}} و {{CSSXRef(':focus')}} استفاده کنید. اثر فوکوس و هاور باید هم دکمه رادیویی و هم برچسب را در بر بگیرد تا درک اینکه کدام گزینه در حال انتخاب است آسان‌تر شود و نشان دهد که کلیک روی برچسب یا دکمه، دکمه رادیویی را فعال می‌کند.

## مثال‌ها

راه‌اندازی اولیه برای یک `radiogroup` با استفاده از نقش‌های ARIA غیرمعنایی به‌جای HTML معنایی به صورت زیر است:

```html
<div role="radiogroup" aria-labelledby="question">
  <div id="question">Which is the best color?</div>
  <div id="radioGroup">
    <p>
      <span
        id="colorOption_0"
        tabindex="0"
        role="radio"
        aria-checked="false"
        aria-labelledby="purple"></span>
      <span id="purple">Purple</span>
    </p>
    <p>
      <span
        id="colorOption_1"
        tabindex="-1"
        role="radio"
        aria-checked="false"
        aria-labelledby="aubergine"></span>
      <span id="aubergine">Aubergine</span>
    </p>
    <p>
      <span
        id="colorOption_2"
        tabindex="-1"
        role="radio"
        aria-checked="false"
        aria-labelledby="magenta"></span>
      <span id="magenta">Magenta</span>
    </p>
    <p>
      <span
        id="colorOption_3"
        tabindex="-1"
        role="radio"
        aria-checked="false"
        aria-labelledby="all"></span>
      <span id="all">All of the above</span>
    </p>
  </div>
</div>
```

این می‌توانست با استفاده از HTML معنایی نوشته شود که به هیچ CSS یا جاوااسکریپتی نیاز ندارد:

```html
<fieldset>
  <legend>Which is the best color?</legend>
  <p>
    <input name="colorOption" type="radio" id="purple" />
    <label for="purple">Purple</label>
  </p>
  <p>
    <input name="colorOption" type="radio" id="aubergine" />
    <label for="aubergine">Aubergine</label>
  </p>
  <p>
    <input name="colorOption" type="radio" id="magenta" />
    <label for="magenta">Magenta</label>
  </p>
  <p>
    <input name="colorOption" type="radio" id="all" />
    <label for="all">All of the above</label>
  </p>
</fieldset>
```

در این مثال {{HTMLElement('fieldset')}}، اگرچه `role="radiogroup"` ضروری نیست، برای اینکه این گروه‌بندی به‌طور صریح به‌عنوان `radiogroup` اعلام شود، نقش ARIA را اضافه کنید.

## مشخصات

{{Specifications}}

## همچنین ببینید

- عنصر HTML {{HTMLElement('fieldset')}}
- عنصر دکمه رادیویی HTML {{HTMLElement('input/radio', '&lt;input type="radio">')}}
- نقش [ARIA `radio`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radio_role)
- [`aria-errormessage`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-errormessage)
- [`aria-invalid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-invalid)
- [`aria-readonly`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-readonly)
- [`aria-required`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-required)