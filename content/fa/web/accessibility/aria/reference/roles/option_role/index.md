---
title: "ARIA: option role"
short-title: option
slug: Web/Accessibility/ARIA/Reference/Roles/option_role
page-type: aria-role
spec-urls:
  - https://w3c.github.io/aria/#option
  - https://www.w3.org/WAI/ARIA/apg/patterns/listbox/examples/listbox-scrollable/
sidebar: accessibilitysidebar
translated_by: "n8n + AI"
---

نقش `option` برای آیتم‌های قابل انتخاب در یک `listbox` استفاده می‌شود.

## توضیحات

نقش `option` برای شناسایی انتخاب‌هایی استفاده می‌شود که کاربر می‌تواند در یک [`listbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listbox_role) انجام دهد. این گزینه‌ها مشابه عناصر {{HTMLElement('option')}} در یک عنصر {{HTMLElement('select')}} هستند، اما می‌توانند تصاویر را نیز شامل شوند.

همه گزینه‌های قابل انتخاب باید [`aria-selected`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-selected) را مطابق با وضعیت‌شان داشته باشند، `true` در حالت انتخاب‌شده و `false` در حالت غیرانتخابی. اگر یک گزینه قابل انتخاب نباشد، `aria-selected` را می‌توان حذف کرد. یک گزینه غیرفعال می‌تواند [`aria-disabled="true"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-disabled) و `aria-selected="false"` داشته باشد تا به کاربر اطلاع دهد که گزینه وجود دارد، هرچند غیرفعال است.

نقش `option` برای شناسایی انتخاب‌های قابل انتخاب یک `listbox` است. گزینه‌ها باید یک نام دسترس‌پذیر داشته باشند. به طور کلی، نام دسترس‌پذیر برای یک گزینه باید از محتوای عناصر فرزند آن بیاید.

نویسندگان همچنین می‌توانند با تعیین [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) یا [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) بر روی عنصر دارای نقش `option`، یک نام دسترس‌پذیر به طور صریح ارائه دهند. اگر از `aria-label` یا `aria-labelledby` استفاده می‌کنید و گزینه همچنین یک برچسب متنی قابل مشاهده را نمایش می‌دهد، نویسندگان باید اطمینان حاصل کنند که با <a href="https://www.w3.org/WAI/WCAG21/Understanding/label-in-name.html">معیار موفقیت WCAG 2.5.3 برچسب در نام</a> مطابقت دارند.

به شدت توصیه می‌شود در صورت امکان از یک عنصر {{HTMLElement('select')}} یا یک عنصر {{HTMLElement('input')}} با نوع `checkbox` یا `radio` استفاده کنید. این عناصر بومی HTML تعامل کیبورد را برای مدیریت فوکوس همه فرزندان به طور خودکار برای شما فراهم می‌کنند.

### همه فرزندان نمایشی هستند

برخی از انواع اجزای رابط کاربری، وقتی در یک API دسترس‌پذیری پلتفرم نمایش داده می‌شوند، فقط می‌توانند متن داشته باشند. APIهای دسترس‌پذیری راهی برای نمایش عناصر معنایی موجود در یک `option` ندارند. برای مقابله با این محدودیت، مرورگرها به طور خودکار نقش [`presentation`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/presentation_role) را به همه عناصر فرزند هر عنصر `option` اعمال می‌کنند، زیرا این نقشی است که فرزندان معنایی را پشتیبانی نمی‌کند.

برای مثال، عنصر `option` زیر را در نظر بگیرید که شامل یک عنوان است.

```html
<div role="option"><h3>Title of my option</h3></div>
```

از آنجا که فرزندان `option` نمایشی هستند، کد زیر معادل است:

```html
<div role="option"><h3 role="presentation">Title of my option</h3></div>
```

از دیدگاه کاربر فناوری کمکی، عنوان وجود ندارد، زیرا قطعه کدهای قبلی با موارد زیر در [درخت دسترس‌پذیری](/en-US/docs/Glossary/Accessibility_tree) معادل هستند:

```html
<div role="option">Title of my option</div>
```

### نقش‌ها، حالت‌ها و ویژگی‌های ARIA مرتبط

#### نقش‌های مرتبط

- [`listbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listbox_role)
  - : یک `option` باید در یک `listbox` قرار داشته باشد یا متعلق به آن باشد.

#### حالت‌ها و ویژگی‌ها

- [`aria-selected`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-selected)
  - : برای توصیف وضعیت انتخاب یک گزینه استفاده می‌شود.

- [`aria-checked`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-checked)
  - : برای توصیف وضعیت علامت‌خورده وقتی گزینه‌ها به صورت انتخاب چندگانه استفاده می‌شوند، به کار می‌رود. مقادیر `true`، `false` و `mixed` را پشتیبانی می‌کند. اختیاری.

- [`aria-posinset`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-posinset)
  - : برای توصیف موقعیت گزینه در مجموعه گزینه‌ها زمانی که با DOM مطابقت ندارد، مانند اسکرول مجازی که در آن فقط برخی گزینه‌ها در یک زمان حضور دارند، استفاده می‌شود. اختیاری.

- [`aria-setsize`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-setsize)
  - : همراه با `aria-posinset` برای اعلام تعداد کل گزینه‌ها استفاده می‌شود. اختیاری.

- [`aria-disabled`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-disabled)
  - : برای نشان دادن اینکه گزینه وجود دارد اما قابل ویرایش نیست، استفاده می‌شود. اختیاری.

- [`aria-hidden`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-hidden)
  - : برای پنهان کردن گزینه از ابزارهای دسترس‌پذیری استفاده می‌شود. فقط باید برای پنهان کردن محتوای غیرقابل مشاهده یا محتوای قابل مشاهده‌ای که تجربه فناوری کمکی را بهبود می‌بخشد، مانند محتوای تکراری، استفاده شود. اختیاری.

- [`aria-invalid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-invalid)
  - : برای نشان دادن اینکه مقدار گزینه توسط برنامه نامعتبر تلقی می‌شود، استفاده می‌شود. اختیاری.

- [`aria-busy`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-busy)
  - : برای نشان دادن اینکه یک عنصر در حال تغییر است، مثلاً در حال بارگذاری، استفاده می‌شود. اختیاری.

- [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby)
  - : برای نشان دادن اینکه کدام عنصر برچسب گزینه را فراهم می‌کند استفاده می‌شود. در صورت مناسب بودن، باید از محتوای خود گزینه استفاده شود. اختیاری.

- [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label)
  - : برای برچسب‌گذاری گزینه استفاده می‌شود. اگر برچسب در DOM وجود دارد، باید به جای آن از `aria-labelledby` استفاده شود. اختیاری.

## مشخصات

{{Specifications}}

## همچنین ببینید

- عنصر HTML {{HTMLElement('select')}}
- عنصر HTML {{HTMLElement('label')}}
- عنصر HTML {{HTMLElement('option')}}
- [ARIA: نقش `combobox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role)
- [ARIA: نقش `list`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/list_role)
- [ARIA: نقش `listbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listbox_role)