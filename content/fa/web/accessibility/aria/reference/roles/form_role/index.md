---
title: "ARIA: form role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/form_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: form role"
short-title: form
slug: Web/Accessibility/ARIA/Reference/Roles/form_role
page-type: aria-role
spec-urls:
  - https://w3c.github.io/aria/#form
  - https://www.w3.org/WAI/ARIA/apg/patterns/landmarks/examples/form.html
sidebar: accessibilitysidebar
---

نقش `form` می‌تواند برای شناسایی گروهی از عناصر در یک صفحه استفاده شود که عملکردی معادل یک فرم HTML ارائه می‌دهند. فرم به عنوان یک منطقه نشانه‌گذاری در دسترس قرار نمی‌گیرد مگر اینکه [نام قابل دسترس](/en-US/docs/Glossary/Accessible_name) داشته باشد.

```html
<div role="form" id="contact-info" aria-label="Contact information">
  <!-- form content -->
</div>
```

این یک فرم است که اطلاعات تماس کاربر را جمع‌آوری و ذخیره می‌کند.

> [!WARNING]
> برای نگهداری کنترل‌های فرم خود از عنصر HTML {{htmlelement("form")}} استفاده کنید، نه نقش ARIA `form`، مگر اینکه دلیل بسیار خوبی داشته باشید.
> عنصر HTML `<form>` برای اطلاع‌رسانی به فناوری‌های کمکی مبنی بر وجود یک فرم کافی است.

## توضیحات

یک [نشانه‌گذاری] `form` (/en-US/docs/Web/Accessibility/ARIA/Reference/Roles#3._landmark_roles) منطقه‌ای از محتوا را شناسایی می‌کند که شامل مجموعه‌ای از موارد و اشیاء است که در مجموع یک فرم را ایجاد می‌کنند، زمانی که هیچ نشانه‌گذاری نام‌دار دیگری مناسب نباشد (مانند [`main`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/main_role) یا [`search`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/search_role)).

> [!NOTE]
> استفاده از عنصر {{HTMLElement('form')}} به طور خودکار یک بخش از محتوا را به عنوان نشانه‌گذاری `form` معرفی می‌کند، در صورتی که نام قابل دسترسی داشته باشد. توسعه‌دهندگان باید همیشه استفاده از عنصر معنایی صحیح HTML را به استفاده از ARIA ترجیح دهند.

در صورت امکان از عنصر HTML {{HTMLElement('form')}} استفاده کنید. عنصر `<form>` یک نشانه‌گذاری `form` را تعریف می‌کند زمانی که نام قابل دسترسی داشته باشد (مانند [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby)، [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) یا [`title`](/en-US/docs/Web/HTML/Reference/Global_attributes/title)). اطمینان حاصل کنید که هر فرم در یک سند برچسب منحصربه‌فرد دارد تا به کاربران در درک هدف فرم کمک کند. این برچسب باید برای همه کاربران قابل مشاهده باشد، نه فقط کاربران فناوری‌های کمکی. هنگامی که فرم برای عملکرد جستجو استفاده می‌شود، به جای نشانه‌گذاری `form` از نشانه‌گذاری `search` استفاده کنید.

از `role="form"` برای شناسایی یک ناحیه از صفحه استفاده کنید؛ از آن برای شناسایی هر فیلد فرم استفاده نکنید. حتی اگر از نشانه‌گذاری form به جای `<form>` استفاده می‌کنید، توصیه می‌شود از کنترل‌های بومی فرم HTML مانند {{HTMLElement('button')}}، {{HTMLElement('input')}}، {{HTMLElement('select')}} و {{HTMLElement('textarea')}} استفاده کنید.

### نقش‌ها، حالت‌ها و ویژگی‌های مرتبط WAI-ARIA

هیچ حالت یا ویژگی خاصی برای این نقش وجود ندارد.

### تعاملات صفحه‌کلید

هیچ تعامل صفحه‌کلید خاصی برای این نقش وجود ندارد.

### ویژگی‌های جاوااسکریپت مورد نیاز

- `onsubmit`
  - : کنترل‌کننده رویداد onSubmit رویدادی را که هنگام ارسال فرم ایجاد می‌شود مدیریت می‌کند. هر چیزی که `<form>` نباشد قابل ارسال نیست، بنابراین باید از جاوااسکریپت برای ساخت یک مکانیزم جایگزین ارسال داده استفاده کنید، به عنوان مثال با {{domxref("Window/fetch", "fetch()")}}.

## مثال‌ها

```html
<div role="form" id="send-comment" aria-label="Add a comment">
  <label for="username">Username</label>
  <input
    id="username"
    name="username"
    autocomplete="nickname"
    autocorrect="off"
    type="text" />

  <label for="email">Email</label>
  <input
    id="email"
    name="email"
    autocomplete="email"
    autocapitalize="off"
    autocorrect="off"
    spellcheck="false"
    type="text" />

  <label for="comment">Comment</label>
  <textarea id="comment" name="comment"></textarea>

  <input value="Comment" type="submit" />
</div>
```

توصیه می‌شود به جای آن از `<form>` استفاده کنید.

```html
<form id="send-comment" aria-label="Add a comment">…</form>
```

## ملاحظات دسترس‌پذیری

### استفاده محدود

[نقش‌های نشانه‌گذاری](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles#3._landmark_roles) برای شناسایی بخش‌های بزرگ‌تر و کلی سند طراحی شده‌اند. استفاده از تعداد زیاد نقش‌های نشانه‌گذاری می‌تواند در صفحه‌خوان‌ها «نویز» ایجاد کند و درک چیدمان کلی صفحه را دشوار کند.

### ورودی‌ها فرم نیستند

نیازی به اعلام `role="form"` روی هر [عنصر فرم](/en-US/docs/Web/HTML/Reference/Elements#forms) (ورودی‌ها، ناحیه‌های متنی، انتخاب‌ها و غیره) ندارید. این نقش باید روی عنصر HTML که عناصر فرم را در بر می‌گیرد اعلام شود. در حالت ایده‌آل، از عنصر {{HTMLElement('form')}} به عنوان عنصر پوشاننده استفاده کنید و `role="form"` را اعلام نکنید.

### جستجو

اگر فرمی برای جستجو استفاده می‌شود، باید از مقدار تخصصی‌تر [`role="search"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/search_role) استفاده کنید.

### برچسب‌گذاری نشانه‌ها

به هر عنصر {{HTMLElement('form')}} و نقش `form` که نیاز است به عنوان نشانه‌گذاری در دسترس قرار گیرد، باید یک نام قابل دسترسی داده شود. این نام به کاربر فناوری کمکی امکان می‌دهد تا به سرعت هدف نشانه‌گذاری فرم را درک کند.

از `aria-labelledby`، `aria-label` یا `title` روی همان عنصری که `role="form"` به آن داده شده است استفاده کنید تا نام قابل دسترسی برای آن فراهم شود.

#### استفاده از `role="form"`

```html
<div role="form" id="gift-cards" aria-label="Purchase a gift card">
  <!-- form content -->
</div>
```

#### توصیف‌های تکراری

صفحه‌خوان‌ها نوع نقشی را که نشانه‌گذاری دارد اعلام می‌کنند. به همین دلیل، نیازی به توصیف چیستی نشانه‌گذاری در برچسب آن نیست. به عنوان مثال، اعلام `role="form"` با `aria-label="Contact form"` ممکن است به صورت تکراری به عنوان «فرم تماس فرم» اعلام شود.

## بهترین روش‌ها

### اولویت با HTML

استفاده از عنصر {{HTMLElement('form')}} به طور خودکار ارتباط می‌دهد که عنصر دارای نقش `form` است. در صورت امکان، استفاده از عنصر معنایی `<form>` را به نقش `form` ترجیح دهید.

## مشخصات

{{Specifications}}

## همچنین ببینید

- عنصر {{HTMLElement('form')}}
- عنصر {{HTMLElement('legend')}}