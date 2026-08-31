---
title: "ARIA: tab role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tab_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: tab role"
short-title: tab
slug: Web/Accessibility/ARIA/Reference/Roles/tab_role
page-type: aria-role
spec-urls:
  - https://w3c.github.io/aria/#tab
  - https://www.w3.org/WAI/ARIA/apg/patterns/tabs/examples/tabs-manual/
sidebar: accessibilitysidebar
---

نقش `tab` در ARIA، یک عنصر تعاملی درون یک `tablist` را نشان می‌دهد که با فعال‌سازی، `tabpanel` مرتبط با خود را نمایش می‌دهد.

```html
<button role="tab" aria-selected="true" aria-controls="tabpanel-id" id="tab-id">
  برچسب زبانه
</button>
```

## توضیحات

یک عنصر با نقش `tab`، دیدِ یک عنصر مرتبط با نقش [`tabpanel`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tabpanel_role) را کنترل می‌کند. الگوی رایج تجربه کاربری، گروهی از زبانه‌های بصری در بالا یا کنار یک ناحیه محتوا است و انتخاب یک زبانه متفاوت، محتوا را تغییر داده و زبانه انتخاب‌شده را برجسته‌تر از سایر زبانه‌ها می‌کند.

عناصر دارای نقش `tab` _باید_ یا فرزند عنصری با نقش `tablist` باشند، یا `id` آن‌ها بخشی از ویژگی [`aria-owns`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-owns) یک `tablist` باشد. این ترکیب به فناوری کمکی اعلام می‌کند که عنصر بخشی از یک گروه از عناصر مرتبط است. برخی فناوری‌های کمکی تعداد عناصر دارای نقش `tab` درون یک `tablist` را ارائه می‌دهند و به کاربران اطلاع می‌دهند که در حال حاضر کدام `tab` را هدف گرفته‌اند. علاوه بر این، یک عنصر با نقش `tab` _باید_ شامل ویژگی [`aria-controls`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-controls) باشد که `tabpanel` مربوطه (دارای نقش `tabpanel`) را با `id` آن عنصر مشخص می‌کند. هنگامی که یک عنصر با نقش `tabpanel` یا فرزندی از آن فوکوس داشته باشد، نشان می‌دهد که عنصر متصل با نقش `tab`، زبانه فعال در یک `tablist` است.

هنگامی که عناصر دارای نقش `tab` انتخاب یا فعال هستند، باید ویژگی [`aria-selected`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-selected) آن‌ها روی `true` تنظیم شود. در غیر این صورت، ویژگی `aria-selected` آن‌ها باید روی `false` تنظیم شود. هنگامی که یک `tablist` تک‌گزین انتخاب یا فعال می‌شود، ویژگی `hidden` سایر tabpanel‌ها باید تا زمانی که کاربر زبانه مرتبط با آن tabpanel را انتخاب کند، روی `true` تنظیم شود. هنگامی که یک `tablist` چندگزین انتخاب یا فعال می‌شود، `tabpanel` کنترل‌شده مربوطه باید ویژگی [`aria-expanded`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-expanded) خود را روی `true` و ویژگی `hidden` خود را روی `false` تنظیم کند، در غیر این صورت برعکس.

### همه نوادگان نمایشی هستند

برخی از انواع اجزای رابط کاربری، هنگامی که در یک API دسترسی‌پذیری پلتفرم نمایش داده می‌شوند، فقط می‌توانند شامل متن باشند. APIهای دسترسی‌پذیری راهی برای نمایش عناصر معنایی موجود در یک `tab` ندارند. برای مقابله با این محدودیت، مرورگرها به طور خودکار نقش [`presentation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role) را به تمام عناصر فرزند هر عنصر `tab` اعمال می‌کنند، زیرا این نقشی است که از فرزندان معنایی پشتیبانی نمی‌کند.

به عنوان مثال، عنصر `tab` زیر را در نظر بگیرید که شامل یک عنوان است.

```html
<div role="tab"><h3>عنوان زبانه من</h3></div>
```

از آنجایی که نوادگان `tab` نمایشی هستند، کد زیر معادل است:

```html
<div role="tab"><h3 role="presentation">عنوان زبانه من</h3></div>
```

از دید کاربر فناوری کمکی، عنوان وجود ندارد، زیرا قطعه کدهای قبلی با موارد زیر در [درخت دسترسی‌پذیری](/en-US/docs/Glossary/Accessibility_tree) معادل هستند:

```html
<div role="tab">عنوان زبانه من</div>
```

### نقش‌ها و ویژگی‌های مرتبط

- [`aria-selected`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-selected)
  - : boolean
- [`aria-controls`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-controls)
  - : `id` عنصر با نقش `tabpanel`
- [id](/en-US/docs/Web/HTML/Reference/Global_attributes/id)
  - : محتوا

### تعاملات صفحه‌کلید

| کلید                              | عملکرد                                                                                                                                                                                                                            |
| --------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <kbd>Tab</kbd>                    | هنگامی که فوکوس خارج از `tablist` است، فوکوس را به زبانه فعال منتقل می‌کند. اگر فوکوس روی زبانه فعال باشد، فوکوس را به عنصر بعدی در ترتیب فوکوس صفحه‌کلید، ترجیحاً `tabpanel` مرتبط با زبانه فعال، منتقل می‌کند.                     |
| <kbd>→</kbd>                      | فوکوس را به زبانه بعدی در لیست زبانه‌ها منتقل کرده و به صورت اختیاری آن را فعال می‌کند. اگر زبانه فعلی آخرین زبانه در لیست زبانه‌ها باشد، اولین زبانه را فعال می‌کند.                                                              |
| <kbd>←</kbd>                      | فوکوس را به زبانه قبلی در لیست زبانه‌ها منتقل کرده و به صورت اختیاری آن را فعال می‌کند. اگر زبانه فعلی اولین زبانه در لیست زبانه‌ها باشد، آخرین زبانه را فعال می‌کند.                                                              |
| <kbd>Enter</kbd>/<kbd>Space</kbd> | هنگامی که یک زبانه فوکوس دارد، زبانه را فعال کرده و باعث می‌شود پنل مرتبط با آن نمایش داده شود.                                                                                                                                    |
| <kbd>Home</kbd>                   | فوکوس را به اولین زبانه در لیست زبانه‌ها منتقل کرده و به صورت اختیاری آن را فعال می‌کند.                                                                                                                                          |
| <kbd>End</kbd>                    | فوکوس را به آخرین زبانه در لیست زبانه‌ها منتقل کرده و به صورت اختیاری آن را فعال می‌کند.                                                                                                                                          |
| <kbd>Delete</kbd>                 | در صورت مجاز بودن، زبانه انتخاب‌شده فعلی را از لیست زبانه‌ها حذف می‌کند.                                                                                                                                                          |

### ویژگی‌های جاوااسکریپت مورد نیاز

> [!NOTE]
> اگرچه راه‌هایی برای ساخت عملکردهای مشابه زبانه بدون جاوااسکریپت وجود دارد، اما هیچ ترکیب جایگزینی با استفاده از HTML و CSS به تنهایی وجود ندارد که مجموعه عملکردهای مشابه مورد نیاز برای زبانه‌های دسترسی‌پذیر با محتوا را فراهم کند.

## مثال

این مثال نقش `tab` را با `tablist` و عناصر دارای `tabpanel` ترکیب می‌کند تا یک گروه تعاملی از محتوای زبانه‌ای ایجاد کند. در اینجا گروه محتوای خود را در یک `div` محصور می‌کنیم، که `tablist` ما دارای یک `aria-label` است که آن را برای فناوری کمکی برچسب‌گذاری می‌کند. هر `tab` یک `button` با ویژگی‌های ذکر شده قبلی است. اولین `tab` دارای `tabindex="0"` و `aria-selected="true"` اعمال شده است. این دو ویژگی باید همیشه به این صورت هماهنگ باشند - به طوری که وقتی زبانه دیگری انتخاب می‌شود، آنگاه `tabindex="0"` و `aria-selected="true"` روی آن اعمال می‌شود. تمام زبانه‌های انتخاب‌نشده باید دارای `aria-selected="false"` و `tabindex="-1"` باشند.

همه عناصر `tabpanel` دارای `tabindex="0"` هستند تا قابل فوکوس با Tab باشند و همه به جز یک عنصر فعال فعلی، دارای ویژگی `hidden` هستند. ویژگی `hidden` هنگامی که یک `tabpanel` با جاوااسکریپت قابل مشاهده می‌شود، حذف خواهد شد.

> [!NOTE]
> تنظیم `tabindex` روی پنل زبانه در صورتی که اولین عنصر در پنل زبانه قابل فوکوس (مانند یک پیوند) باشد، ضروری نیست، زیرا فوکوس با Tab روی پیوند همچنین باعث شروع خواندن محتوای پنل می‌شود. با این حال، اگر هر پنلی در مجموعه وجود داشته باشد که اولین عنصر محتوای آن قابل فوکوس نباشد، آنگاه تمام عناصر `tabpanel` در یک مجموعه زبانه باید قابل فوکوس باشند تا کاربران صفحه‌خوان بتوانند به طور ثابت به محتوای پنل پیمایش کنند.

```html
<div class="tabs">
  <div role="tablist" aria-label="سیستم عامل خود را انتخاب کنید">
    <button
      role="tab"
      aria-selected="true"
      aria-controls="panel-1"
      id="tab-1"
      tabindex="0">
      ویندوز
    </button>
    <button
      role="tab"
      aria-selected="false"
      aria-controls="panel-2"
      id="tab-2"
      tabindex="-1">
      macOS
    </button>
    <button
      role="tab"
      aria-selected="false"
      aria-controls="panel-3"
      id="tab-3"
      tabindex="-1">
      لینوکس
    </button>
  </div>
  <div class="tab-panels">
    <div id="panel-1" role="tabpanel" tabindex="0" aria-labelledby="tab-1">
      <p>نحوه اجرای این برنامه در ویندوز</p>
    </div>
    <div
      id="panel-2"
      role="tabpanel"
      tabindex="0"
      aria-labelledby="tab-2"
      hidden>
      <p>نحوه اجرای این برنامه در macOS</p>
    </div>
    <div
      id="panel-3"
      role="tabpanel"
      tabindex="0"
      aria-labelledby="tab-3"
      hidden>
      <p>نحوه اجرای این برنامه در لینوکس</p>
    </div>
  </div>
</div>
```

برخی استایل‌های پایه اعمال شده است که دکمه‌ها را تغییر شکل می‌دهد و {{cssxref("z-index")}} عناصر `tab` را تغییر می‌دهد تا توهم اتصال آن به `tabpanel` برای عناصر فعال و توهم غیرفعال بودن عناصر غیرفعال در پشت `tabpanel` فعال ایجاد شود. شما باید زبانه فعال را به وضوح از زبانه‌های غیرفعال متمایز کنید، مانند حاشیه‌های ضخیم‌تر یا اندازه بزرگ‌تر.

```css hidden
.tabs {
  padding: 1em;
}

[role="tablist"] {
  margin-bottom: -1px;
}

[role="tab"] {
  position: relative;
  z-index: 1;
  background: white;
  border-radius: 5px 5px 0 0;
  border: 1px solid grey;
  border-bottom: 0;
  padding: 0.2em;
}

[role="tab"][aria-selected="true"] {
  z-index: 3;
  border-top-width: 4px;
}

[role="tabpanel"] {
  position: relative;
  padding: 0 0.5em 0.5em 0.7em;
  border: 1px solid grey;
  border-radius: 0 0 5px 5px;
  background: white;
  z-index: 2;
}

[role="tabpanel"]:focus {
  border-color: #356fb3;
  outline: 1px solid #356fb3;
}
```

تعامل کاربر با جاوااسکریپت مدیریت می‌شود. ابتدا ارجاعاتی به `tablist`، تمام عناصر `tab` درون آن، ظرف عناصر `tabpanel` و تمام عناصر `tabpanel` درون آن ظرف دریافت می‌کنیم. این بر اساس برخی فرضیات در مورد ساختار HTML ما است، بنابراین اگر ساختار را تغییر دهید، باید این کد را تغییر دهید. اگر چندین رابط زبانه‌ای در یک صفحه دارید، می‌توانید این کد را در یک تابع بپیچید و `tabsContainer` را به عنوان آرگومان پاس دهید.

```js
const tabsContainer = document.querySelector(".tabs");
const tabList = tabsContainer.querySelector(':scope > [role="tablist"]');
const tabs = Array.from(tabList.querySelectorAll(':scope > [role="tab"]'));
const tabPanelsContainer = tabsContainer.querySelector(":scope > .tab-panels");
const tabPanels = Array.from(
  tabPanelsContainer.querySelectorAll(':scope > [role="tabpanel"]'),
);
```

برای تعاملات صفحه‌کلید، به رویداد [`keydown`](/en-US/docs/Web/API/Element/keydown_event) روی `tablist` گوش می‌دهیم. در این نسخه نمایشی، تصمیم گرفتیم هنگام پیمایش کاربر با کلیدهای جهت‌نما، `tab` را فعال نکنیم، بلکه فقط فوکوس را جابجا کنیم. اگر می‌خواهید هنگام دریافت فوکوس، `tab` را نمایش دهید، می‌توانید تابع `showTab()` (که بعداً تعریف شده) را فراخوانی کنید به جای اینکه فقط `focus()` را روی زبانه جدید فراخوانی کنید.

```js
tabList.addEventListener("keydown", (e) => {
  const currentTab = e.target;
  const currentIndex = tabs.indexOf(currentTab);
  if (currentIndex === -1) return; // اگر عنصر فوکوس‌شده یک زبانه نیست، خارج شوید
  let newIndex = 0;

  switch (e.key) {
    case "ArrowRight":
      newIndex = (currentIndex + 1) % tabs.length;
      break;
    case "ArrowLeft":
      newIndex = (currentIndex - 1 + tabs.length) % tabs.length;
      break;
    case "Home":
      newIndex = 0;
      break;
    case "End":
      newIndex = tabs.length - 1;
      break;
    default:
      return; // اگر کلید شناسایی نشد، خارج شوید
  }

  e.preventDefault();
  e.stopPropagation();
  tabs[newIndex].focus();
});
```

پنل زبانه فقط با فشار دادن <kbd>Enter</kbd> یا <kbd>Space</kbd> در حالی که یک `tab` فوکوس دارد، یا با کلیک روی یک `tab` فعال می‌شود. ابتدا یک تابع `showTab()` تعریف می‌کنیم که عنصر `tab` مورد نظر برای نمایش را دریافت می‌کند.

```js
function showTab(targetTab) {
  // سایر زبانه‌ها را لغو انتخاب کرده و این زبانه را به عنوان انتخاب‌شده تنظیم کنید
  for (const tab of tabs) {
    if (tab === targetTab) continue;
    tab.setAttribute("aria-selected", false);
    tab.tabIndex = -1;
  }
  targetTab.setAttribute("aria-selected", true);
  targetTab.tabIndex = 0;

  // سایر پنل‌های زبانه را مخفی کرده و پنل انتخاب‌شده را نمایش دهید
  const targetTabPanel = document.getElementById(
    targetTab.getAttribute("aria-controls"),
  );
  for (const panel of tabPanels) {
    if (panel === targetTabPanel) continue;
    panel.hidden = true;
  }
  targetTabPanel.hidden = false;
}
```

اکنون می‌توانیم این تابع را یا در رویداد `click` یا در رویداد `keydown` فراخوانی کنیم.

```js
tabs.forEach((tab) => {
  tab.addEventListener("click", (e) => {
    showTab(e.target);
  });
  tab.addEventListener("keydown", (e) => {
    if (e.key === "Enter" || e.key === " ") {
      e.preventDefault();
      e.stopPropagation();
      showTab(e.target);
    }
  });
});
```

{{EmbedLiveSample("Example", 600, 130)}}

## بهترین روش‌ها

توصیه می‌شود از یک عنصر {{HTMLElement('button')}} با نقش `tab` برای ویژگی‌های عملکردی و دسترسی‌پذیری داخلی آن استفاده کنید، به جای اینکه نیاز به اضافه کردن آن‌ها خودتان داشته باشید. برای کنترل عملکرد کلید Tab برای عناصر دارای نقش `tab`، توصیه می‌شود تمام عناصر غیرفعال را روی `tabindex="-1"` و عنصر فعال را روی `tabindex="0"` تنظیم کنید.

## ترتیب اولویت

ویژگی‌های مرتبط کدامند و این ویژگی یا ویژگی به چه ترتیبی خوانده می‌شود، کدام ویژگی بر این یکی اولویت خواهد داشت، و کدام ویژگی بازنویسی می‌شود.

## مشخصات

{{Specifications}}

## همچنین ببینید

- عنصر HTML {{HTMLElement('button')}}
- [KeyboardEvent.key](/en-US/docs/Web/API/KeyboardEvent/key)
- [نقش `tabpanel` در ARIA](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tabpanel_role)