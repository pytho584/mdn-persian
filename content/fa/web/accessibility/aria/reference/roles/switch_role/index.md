---
title: "ARIA: switch role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/switch_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: switch role"
short-title: switch
slug: Web/Accessibility/ARIA/Reference/Roles/switch_role
page-type: aria-role
spec-urls:
  - https://w3c.github.io/aria/#switch
  - https://w3c.github.io/html-aria/#index-aria-switch
sidebar: accessibilitysidebar
---

نقش ARIA **`switch`** از نظر عملکردی با نقش [checkbox](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/checkbox_role) یکسان است، با این تفاوت که به‌جای نمایش حالت‌های «تیک‌خورده» و «تیک‌نخورده» که از نظر معنایی نسبتاً عمومی هستند، نقش `switch` حالت‌های «روشن» و «خاموش» را نمایش می‌دهد.

این مثال یک ویجت می‌سازد و نقش ARIA `switch` را به آن اختصاص می‌دهد.

```html
<button
  type="button"
  role="switch"
  aria-checked="true"
  id="speakerPower"
  class="switch">
  <span aria-hidden="true">off</span>
  <span aria-hidden="false">on</span>
</button>
<label for="speakerPower" class="switch">Speaker power</label>
```

## توضیحات

نقش ARIA **`switch`** با نقش [checkbox](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/checkbox_role) یکسان است، با این تفاوت که به‌جای «تیک‌خورده» یا «تیک‌نخورده» بودن، «روشن» یا «خاموش» است. مانند نقش [checkbox](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/checkbox_role)، ویژگی [`aria-checked`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-checked) الزامی است. دو مقدار ممکن `true` و `false` هستند. برخلاف `<input type="checkbox">` یا `role="checkbox"`، حالت `indeterminate` یا `mixed` وجود ندارد. نقش `switch` از مقدار `mixed` برای ویژگی `aria-checked` پشتیبانی نمی‌کند؛ در صورت اختصاص مقدار `mixed` به یک `switch`، مقدار به‌جای آن روی `false` تنظیم می‌شود.

فناوری‌های کمکی ممکن است انتخاب کنند که ویجت‌های `switch` را با ارائه‌ای تخصصی نمایش دهند تا مفهوم کلید روشن/خاموش را بازتاب کنند.

از آنجا که یک سوئیچ یک کنترل تعاملی است، باید قابل فوکوس و قابل دسترسی با صفحه‌کلید باشد. اگر نقش روی عنصری اعمال شود که قابل فوکوس نیست، از ویژگی `tabindex` برای تغییر این وضعیت استفاده کنید. میانبر صفحه‌کلید مورد انتظار برای تغییر مقدار یک سوئیچ، کلید <kbd>Space</kbd> است. توسعه‌دهنده موظف است هنگام تغییر وضعیت سوئیچ، مقدار ویژگی `aria-checked` را به‌صورت پویا تغییر دهد.

### همه فرزندان، نمایشی (presentational) هستند

برخی از انواع اجزای رابط کاربری، وقتی در API دسترس‌پذیری یک پلتفرم نمایش داده می‌شوند، فقط می‌توانند متن داشته باشند. APIهای دسترس‌پذیری راهی برای نمایش عناصر معنایی داخل یک `switch` ندارند. برای مقابله با این محدودیت، مرورگرها به‌طور خودکار نقش [`presentation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role) را به همه عناصر فرزند هر عنصر `switch` اعمال می‌کنند، زیرا این نقشی است که از فرزندان معنایی پشتیبانی نمی‌کند.

برای مثال، عنصر `switch` زیر را در نظر بگیرید که شامل یک عنوان است.

```html
<div role="switch"><h3>Title of my switch</h3></div>
```

چون فرزندان `switch` نمایشی هستند، کد زیر معادل است:

```html
<div role="switch"><h3 role="presentation">Title of my switch</h3></div>
```

از دید کاربر فناوری کمکی، عنوان وجود ندارد، زیرا قطعه‌کدهای قبلی با کد زیر در [درخت دسترس‌پذیری](/en-US/docs/Glossary/Accessibility_tree) معادل هستند:

```html
<div role="switch">Title of my switch</div>
```

### نقش‌ها، حالت‌ها و ویژگی‌های ARIA مرتبط

- ویژگی [`aria-checked`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-checked)
  - : ویژگی `aria-checked` هنگام استفاده از نقش `switch` **الزامی** است، زیرا حالت فعلی ویجتی را نشان می‌دهد که نقش `switch` روی آن اعمال شده است. مقدار `true` حالت «روشن» و مقدار `false` حالت «خاموش» را نشان می‌دهد؛ مقدار `mixed` توسط نقش `switch` پشتیبانی نمی‌شود و به‌عنوان `false` در نظر گرفته می‌شود.
- ویژگی [`aria-readonly`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-readonly)
  - : ویژگی `aria-readonly` توسط نقش `switch` پشتیبانی می‌شود. مشخص می‌کند که آیا حالت ویجت توسط کاربر قابل ویرایش است یا خیر. مقدار `false` یعنی کاربر _می‌تواند_ حالت ویجت را تغییر دهد؛ مقدار `true` یعنی کاربر _نمی‌تواند_ حالت ویجت را تغییر دهد. مقدار پیش‌فرض `false` است.

### ویژگی‌های جاوااسکریپت مورد نیاز

- کنترل‌کننده رویداد کلیک
  - : وقتی کاربر روی ویجت سوئیچ کلیک می‌کند، یک [رویداد کلیک](/en-US/docs/Web/API/Element/click_event) رخ می‌دهد که برای تغییر حالت ویجت باید مدیریت شود.
- تغییر ویژگی `aria-checked`
  - : وقتی رویداد کلیک روی ویجت سوئیچ رخ می‌دهد، کنترل‌کننده باید مقدار ویژگی `aria-checked` را از `true` به `false` یا برعکس تغییر دهد.

### اثرات احتمالی بر عامل‌های کاربر و فناوری‌های کمکی

هنگامی که نقش `switch` به یک عنصر اضافه می‌شود، {{Glossary("user agent")}} آن را به این صورت مدیریت می‌کند:

- عنصر به زیرساخت دسترس‌پذیری سیستم به‌عنوان عنصری با نقش `switch` معرفی می‌شود.
- وقتی مقدار ویژگی `aria-checked` تغییر کند، در صورت وجود API دسترس‌پذیری سیستم و پشتیبانی آن از نقش `switch`، یک رویداد دسترس‌پذیر از طریق API ارسال می‌شود.
- همه عناصری که فرزند عنصری با نقش `switch` هستند به‌طور خودکار نقش `presentation` می‌گیرند. این کار از تعامل جداگانه فناوری‌های کمکی با عناصری که برای ساخت سوئیچ استفاده شده‌اند جلوگیری می‌کند. متن موجود در این عناصر برای عامل کاربر قابل مشاهده می‌ماند و ممکن است برای کاربر خوانده شود یا به شکل دیگری ارائه شود، مگر اینکه صریحاً با {{cssxref("display", "display: none")}} یا `aria-hidden="true"` پنهان شده باشد.

فناوری کمکی، در صورت پشتیبانی از نقش `switch`، به این صورت واکنش نشان می‌دهد:

- صفحه‌خوان‌ها باید عنصر را به‌عنوان یک سوئیچ اعلام کنند و به‌صورت اختیاری دستورالعمل‌هایی برای فعال کردن سوئیچ ارائه دهند.

> [!NOTE]
> دیدگاه‌های متفاوتی درباره نحوه مدیریت این نقش توسط فناوری‌های کمکی وجود دارد؛ مطالب بالا یک رویه پیشنهادی است و ممکن است با منابع دیگر متفاوت باشد.

## مثال‌ها

مثال‌های زیر به شما کمک می‌کنند تا نحوه اعمال و استفاده از نقش `switch` را درک کنید.

### افزودن نقش switch در ARIA

این مثال یک ویجت می‌سازد و نقش ARIA `switch` را به آن اختصاص می‌دهد. دکمه با ظاهری شبیه به کلید روشن/خاموش برق استایل‌دهی شده است.

#### HTML

یک سوئیچ به‌صورت عنصر {{HTMLElement("button")}} پیاده‌سازی می‌شود که ابتدا به لطف قرار گرفتن ویژگی `aria-checked` روی `"true"`، در حالت تیک‌خورده قرار دارد. سوئیچ دو عنصر فرزند دارد که برچسب‌های «خاموش» و «روشن» را شامل می‌شوند و به دنبال آن یک {{HTMLElement("label")}} قرار دارد که سوئیچ را شناسایی می‌کند.

```html
<button role="switch" aria-checked="true" id="speakerPower" class="switch">
  <span>off</span>
  <span>on</span>
</button>
<label for="speakerPower" class="switch">Speaker power</label>
```

#### JavaScript

این کد جاوااسکریپت تابعی را تعریف و اعمال می‌کند که رویدادهای کلیک روی ویجت‌های سوئیچ را مدیریت می‌کند. این تابع مقدار ویژگی `aria-checked` را از `true` به `false` یا برعکس تغییر می‌دهد.

```js
document.querySelectorAll(".switch").forEach((theSwitch) => {
  theSwitch.addEventListener("click", handleClickEvent);
});

function handleClickEvent(evt) {
  const el = evt.target;

  if (el.getAttribute("aria-checked") === "true") {
    el.setAttribute("aria-checked", "false");
  } else {
    el.setAttribute("aria-checked", "true");
  }
}
```

#### CSS

هدف CSS ایجاد ظاهر و حسی برای سوئیچ است که یادآور الگوی کلید برق باشد.

```css
button.switch {
  margin: 0;
  padding: 0;
  width: 70px;
  height: 26px;
  border: 2px solid black;
  display: inline-block;
  margin-right: 0.25em;
  vertical-align: middle;
  text-align: center;
  font:
    12px / 20px "Open Sans",
    "Arial",
    serif;
}

button.switch span {
  padding: 0 4px;
  pointer-events: none;
}

[role="switch"][aria-checked="false"] :first-child,
[role="switch"][aria-checked="true"] :last-child {
  background: #226622;
  color: #eeeeff;
}

[role="switch"][aria-checked="false"] :last-child,
[role="switch"][aria-checked="true"] :first-child {
  color: #bbbbdd;
}

label.switch {
  font:
    16px "Open Sans",
    "Arial",
    sans-serif;
  line-height: 20px;
  vertical-align: middle;
  user-select: none;
}
```

جالب‌ترین بخش احتمالاً استفاده از انتخابگرهای ویژگی و شبه‌کلاس‌های {{cssxref(":first-child")}} و {{cssxref(":last-child")}} است که کار اصلی تغییر ظاهر سوئیچ را بر اساس روشن یا خاموش بودن آن انجام می‌دهند.

#### نتیجه

نتیجه به این شکل است:

{{EmbedLiveSample("Adding_the_switch_role_in_ARIA", 600, 40)}}

## مشخصات

{{Specifications}}

## همچنین ببینید

- [ARIA: checkbox role](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/checkbox_role)
- [`<input type="checkbox">`](/en-US/docs/Web/HTML/Reference/Elements/input/checkbox)
- [`aria-hidden`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-hidden)