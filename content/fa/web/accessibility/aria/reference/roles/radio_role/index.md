---
title: "ARIA: radio role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radio_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: radio role"
short-title: radio
slug: Web/Accessibility/ARIA/Reference/Roles/radio_role
page-type: aria-role
sidebar: accessibilitysidebar
---

نقش `radio` یکی از گروه دکمههای رادیویی قابل انتخاب در یک `radiogroup` است که در آن در هر زمان تنها یک دکمه رادیویی میتواند انتخاب شود.

## توضیحات

دکمه رادیویی یک ورودی قابل انتخاب است که وقتی با سایر دکمههای رادیویی مرتبط میشود، تنها یکی از آنها میتواند در هر زمان انتخاب شود. دکمههای رادیویی باید در یک [`radiogroup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radiogroup_role) گروهبندی شوند تا مشخص شود کدامیک بر روی مقدار یکسانی تأثیر میگذارند.

```html
<div role="radiogroup" aria-labelledby="legend25" id="radiogroup25">
  <p id="legend25">Ipsum and lorem?</p>
  <div>
    <span
      role="radio"
      aria-checked="false"
      tabindex="0"
      aria-labelledby="q25_radio1-label"
      data-value="True"></span>
    <label id="q25_radio1-label">True</label>
  </div>
  <div>
    <span
      role="radio"
      aria-checked="false"
      tabindex="0"
      aria-labelledby="q25_radio2-label"
      data-value="False"></span>
    <label id="q25_radio2-label">False</label>
  </div>
  <div>
    <span
      role="radio"
      aria-checked="true"
      tabindex="0"
      aria-labelledby="q25_radio3-label"
      data-value="huh?"></span>
    <label id="q25_radio3-label">What is the question?</label>
  </div>
</div>
```

ویژگی `role` فقط معناشناسی اضافه میکند؛ تمام عملکردهایی که به‌طور بومی در [HTML radio](/en-US/docs/Web/HTML/Reference/Elements/input/radio) وجود دارد باید با جاوااسکریپت و ویژگی HTML [`tabindex`](/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex) اضافه شوند.

> [!NOTE]
> اولین قانون ARIA این است که اگر یک عنصر یا ویژگی HTML بومی دارای معناشناسی و رفتاری است که به آن نیاز دارید، به جای تغییر کاربری یک عنصر و افزودن ARIA از آن استفاده کنید. در عوض از [HTML `<input type="radio">`](/en-US/docs/Web/HTML/Reference/Elements/input/radio) بومی (با یک {{HTMLElement('label')}} مرتبط) استفاده کنید که به صورت بومی تمام عملکردهای مورد نیاز را فراهم می‌کند:

```html
<fieldset>
  <legend>Ipsum and lorem?</legend>
  <div>
    <input type="radio" value="True" id="q25_radio1" name="q25" />
    <label for="q25_radio1">True</label>
  </div>
  <div>
    <input type="radio" value="False" id="q25_radio2" name="q25" />
    <label for="q25_radio2">False</label>
  </div>
  <div>
    <input type="radio" value="huh?" id="q25_radio3" name="q25" checked />
    <label for="q25_radio3">What is the question?</label>
  </div>
</fieldset>
```

کنترل فرم رادیویی HTML بومی ([`<input type="radio">`](/en-US/docs/Web/HTML/Reference/Elements/input/radio)) دو حالت دارد («انتخاب شده» یا «انتخاب نشده»). به همین ترتیب، یک عنصر با `role="radio"` می‌تواند دو حالت را از طریق ویژگی [`aria-checked`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-checked) نشان دهد: `true` وضعیت انتخاب شده و `false` وضعیت انتخاب نشده را نشان می‌دهد. مقدار `mixed` برای `aria-checked` برای دکمه رادیویی معتبر نیست.

اگر یک دکمه رادیویی انتخاب شده باشد، عنصر radio دارای `aria-checked` با مقدار `true` است. اگر انتخاب نشده باشد، دارای `aria-checked` با مقدار `false` است.

هر عنصر دکمه رادیویی دارای نقش `radio` است. نقش radio باید همیشه همراه با سایر radioهای مرتبط در یک `radiogroup` تودرتو باشد. اگر امکان تودرتو کردن دکمه رادیویی در یک گروه رادیویی وجود ندارد، از `id` آن رادیوی غیرگروه‌بندی‌شده در فهرستی از مقادیر جدا شده با فاصله به عنوان مقدار ویژگی [`aria-owns`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-owns) در عنصر `radiogroup` استفاده کنید تا رابطه `radiogroup` با اعضای radio خود را نشان دهد.

هر عنصر radio با محتوای خود برچسب‌گذاری می‌شود، دارای برچسب قابل مشاهده است که توسط `aria-labelledby` ارجاع داده می‌شود، یا دارای برچسبی است که با `aria-label` مشخص شده است. عنصر `radiogroup` والد نیز باید دارای برچسب قابل مشاهده باشد که توسط `aria-labelledby` ارجاع داده شود یا برچسبی که با `aria-label` مشخص شده باشد. اگر عناصری حاوی اطلاعات اضافی درباره گروه رادیویی یا هر دکمه رادیویی وجود داشته باشند، باید توسط عنصر `radiogroup` یا عناصر radio با ویژگی [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) ارجاع داده شوند.

از آنجا که `radio` یک کنترل تعاملی است؛ باید قابل دریافت تمرکز و قابل دسترسی با صفحه‌کلید باشد. اگر نقش روی یک عنصر غیرقابل تمرکز اعمال شود، از ویژگی [`tabindex`](/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex) برای تغییر آن استفاده کنید. میانبر صفحه‌کلید مورد انتظار برای فعال کردن یک radio کلید <kbd>Space</kbd> است. از جاوااسکریپت استفاده کنید تا ویژگی `aria-checked` را به `true` تغییر دهید وقتی radio انتخاب می‌شود و اطمینان حاصل کنید که تمام نقش‌های radio دیگر در گروه روی `aria-checked="false"` تنظیم شده‌اند.

برای نشان دادن برنامه‌نویسی که یک دکمه رادیویی باید از یک گروه رادیویی انتخاب شود، ویژگی [`aria-required`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-required) با مقدار `true` باید روی عنصر `radiogroup` مشخص شود. انتظار نمی‌رود که از ویژگی `aria-required` روی دکمه‌های رادیویی ARIA جداگانه استفاده شود.

### همگی فرزندان نمایشی هستند

برخی از انواع اجزای رابط کاربری وجود دارند که وقتی در یک API دسترس‌پذیری پلتفرم نمایش داده می‌شوند، فقط می‌توانند متن داشته باشند. APIهای دسترس‌پذیری راهی برای نمایش عناصر معنایی موجود در یک `radio` ندارند. برای مقابله با این محدودیت، مرورگرها به طور خودکار نقش [`presentation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role) را روی تمام عناصر فرزند هر عنصر `radio` اعمال می‌کنند، زیرا این نقشی است که فرزندان معنایی را پشتیبانی نمی‌کند.

برای مثال، عنصر `radio` زیر را در نظر بگیرید که شامل یک عنوان است.

```html
<div role="radio"><h6>name of my radio</h6></div>
```

از آنجا که فرزندان `radio` نمایشی هستند، کد زیر معادل است:

```html
<div role="radio"><h6 role="presentation">name of my radio</h6></div>
```

از دیدگاه کاربر فناوری کمکی، عنوان وجود ندارد، زیرا قطعه‌کدهای قبلی با الگوی زیر در [درخت دسترس‌پذیری](/en-US/docs/Glossary/Accessibility_tree) معادل هستند:

```html
<div role="radio">name of my radio</div>
```

### نقش‌ها، حالت‌ها و ویژگی‌های WAI-ARIA مرتبط

- [`radiogroup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radiogroup_role) نقش
  - : دکمه‌های رادیویی در یک عنصر با نقش `radiogroup` قرار دارند یا توسط آن مالکیت می‌شوند. اگر نتوان آن‌ها را در یک `radiogroup` در نشانه‌گذاری تودرتو کرد، ویژگی `aria-owns` از `radiogroup` حاوی مقادیر `id` دکمه‌های رادیویی غیرتودرتوی گروه است.

- [`aria-checked`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-checked)
  - : مقدار `aria-checked` وضعیت یک radio را تعریف می‌کند. وقتی با عناصر radio استفاده می‌شود، ویژگی یکی از دو مقدار ممکن را دارد:
    - `true`
      - : radio انتخاب شده است.
    - `false`
      - : radio انتخاب نشده است.

> [!NOTE]
> اگر از `role="radio"` روی عنصری استفاده شود که به صورت بومی تمرکز صفحه‌کلید را نمی‌پذیرد، از [ویژگی `tabindex`](/en-US/docs/Web/HTML/Reference/Global_attributes/tabindex) استفاده کنید. به عنوان مثال، یک `<div>` یا `<span>`.

### تعاملات صفحه‌کلید

- <kbd>Tab</kbd> + <kbd>Shift</kbd>
  - : تمرکز را به داخل و خارج از گروه رادیویی منتقل می‌کند. وقتی تمرکز به یک گروه رادیویی منتقل می‌شود و یک دکمه رادیویی قبلاً انتخاب شده است، تمرکز روی دکمه انتخاب شده قرار می‌گیرد. اگر هیچ‌کدام از دکمه‌های رادیویی انتخاب نشده باشند، تمرکز روی اولین دکمه رادیویی در گروه قرار می‌گیرد.

- <kbd>Space</kbd>
  - : اگر radio قبلاً انتخاب نشده باشد، آن را انتخاب می‌کند. یک دکمه رادیویی که قبلاً در گروه رادیویی انتخاب شده بود را از انتخاب خارج می‌کند.

- <kbd>Right Arrow</kbd> و <kbd>Down Arrow</kbd>
  - : تمرکز را به دکمه رادیویی بعدی در گروه منتقل کرده و آن را انتخاب می‌کند و دکمه رادیویی قبلی را از انتخاب خارج می‌کند. اگر تمرکز روی آخرین دکمه رادیویی باشد، تمرکز به اولین دکمه رادیویی منتقل می‌شود.

- <kbd>Left Arrow</kbd> و <kbd>Up Arrow</kbd>
  - : تمرکز را به دکمه رادیویی قبلی در گروه منتقل کرده و آن را انتخاب می‌کند و دکمه رادیویی قبلی را از انتخاب خارج می‌کند. اگر تمرکز روی اولین دکمه رادیویی باشد، تمرکز به آخرین دکمه رادیویی منتقل می‌شود.

### رادیوها در نوار ابزار

از آنجا که از کلیدهای جهت‌نما برای پیمایش بین عناصر یک نوار ابزار استفاده می‌شود و کلید <kbd>Tab</kbd> تمرکز را به داخل و خارج از نوار ابزار منتقل می‌کند، وقتی یک گروه رادیویی در داخل یک نوار ابزار تودرتو باشد، تعامل صفحه‌کلید گروه رادیویی کمی با گروه رادیویی که داخل نوار ابزار نیست متفاوت است. برای اطلاعات بیشتر به [تعاملات صفحه‌کلید `radiogroup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radiogroup_role#keyboard_interactions) مراجعه کنید.

### جاوااسکریپت مورد نیاز

- `onClick`
  - : کلیک‌های ماوس را روی radio و برچسب مرتبط مدیریت می‌کند که وضعیت radio را با تغییر مقدار ویژگی `aria-checked` و ظاهر radio تغییر می‌دهد تا برای کاربر بینا انتخاب شده یا نشده به نظر برسد.

- `onKeyPress`
  - : موردی را مدیریت می‌کند که کاربر کلید <kbd>Space</kbd> را فشار می‌دهد تا وضعیت radio را با تغییر مقدار ویژگی `aria-checked` و ظاهر radio تغییر دهد، به طوری که برای کاربر بینا انتخاب شده یا نشده به نظر برسد.

## مثال‌ها

مثال زیر از ARIA برای تغییر عناصر عمومی به دکمه‌های رادیویی استفاده می‌کند. CSS و JavaScript برای تغییر بصری و برنامه‌نویسی وضعیت انتخاب شده یا نشده عنصر استفاده می‌شوند.

### HTML

```html
<div role="radiogroup" aria-labelledby="legend" id="radiogroup">
  <p id="legend">
    Should you be using the <code>radio</code> role or
    <code>&lt;input type="radio"></code>?
  </p>
  <div>
    <span
      role="radio"
      aria-checked="true"
      tabindex="0"
      aria-labelledby="ariaLabel"
      data-value="True"></span>
    <label id="ariaLabel">ARIA role</label>
  </div>
  <div>
    <span
      role="radio"
      aria-checked="false"
      tabindex="0"
      aria-labelledby="htmllabel"
      data-value="False"></span>
    <label id="htmllabel">HTML <code>&lt;input type="radio"></code></label>
  </div>
</div>
```

### CSS

```css
[role="radio"] {
  padding: 5px;
}

[role="radio"][aria-checked="true"]::before {
  content: "(x)";
  font-family: monospace;
}

[role="radio"][aria-checked="false"]::before {
  content: "( )";
  font-family: monospace;
}
```

### JavaScript

جاوااسکریپت زیادی برای تبدیل HTML غیر معنایی به دکمه‌های رادیویی مورد نیاز است.

```js
// initialize all the radio role elements

const radioGroups = document.querySelectorAll('[role="radiogroup"]');

for (const radioGroup of radioGroups) {
  const radios = radioGroup.querySelectorAll("[role=radio]");
  for (const radio of radios) {
    radio.addEventListener("keydown", handleKeydown);
    radio.addEventListener("click", handleClick);
  }
}

// handle mouse and touch events
function handleClick(event) {
  setChecked(this);
  event.stopPropagation();
  event.preventDefault();
}

// handle key presses
function handleKeydown(event) {
  switch (event.code) {
    case "Space":
    case "Enter":
      currentChecked();
      break;

    case "ArrowUp":
    case "ArrowLeft":
      previousRadioChecked();
      break;

    case "ArrowDown":
    case "ArrowRight":
      nextItemChecked();
      break;

    default:
      break;
  }
  event.stopPropagation();
  event.preventDefault();
}

// when a radio is selected, give it focus, set checked to true;
// ensure all other radios in radio group are not checked

function setChecked() {
  // uncheck all the radios in group
  // iterated through all the radios in radio group
  // eachRadio.tabIndex = -1;
  // eachRadio.setAttribute('aria-checked', 'false');
  // set the selected radio to checked
  // thisRadio.setAttribute('aria-checked', 'true');
  // thisRadio.tabIndex = 0;
  // thisRadio.focus();
  // set the value of the radioGroup to the value of the currently selected radio
}
```

<!-- {{EmbedLiveSample("Examples", 230, 250)}} -->

اگر از عنصر HTML معنایی استفاده کرده بودیم که نام هر دکمه رادیویی در یک گروه از دکمه‌های رادیویی یکسان بود، هیچ جاوااسکریپت (یا حتی CSS) مورد نیاز نبود:

```html
<fieldset>
  <legend>
    Should you be using the <code>radio</code> role or
    <code>&lt;input type="radio"></code>?
  </legend>
  <div>
    <input type="radio" name="bestPractices" id="ariaLabel" value="True" />
    <label for="ariaLabel">ARIA role</label>
  </div>
  <div>
    <input type="radio" name="bestPractices" id="htmllabel" value="False" />
    <label for="htmllabel">HTML <code>&lt;input type="radio"></code></label>
  </div>
</fieldset>
```

## بهترین روش‌ها

اولین قانون ARIA این است: اگر یک عنصر یا ویژگی HTML بومی دارای معناشناسی و رفتاری است که به آن نیاز دارید، از آن استفاده کنید به جای اینکه یک عنصر را تغییر کاربری داده و یک نقش، حالت یا ویژگی ARIA به آن اضافه کنید تا قابل دست