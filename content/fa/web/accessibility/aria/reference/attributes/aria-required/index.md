---
title: "ARIA: aria-required attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-required"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-required attribute"
short-title: aria-required
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-required
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-required
sidebar: accessibilitysidebar
---

ویژگی `aria-required` نشان می‌دهد که ورودی کاربر در آن عنصر قبل از ارسال فرم ضروری است.

## توضیحات

زمانی که یک عنصر معنایی HTML مانند {{htmlelement("input")}}، {{htmlelement("select")}} یا {{htmlelement("textarea")}} باید دارای مقدار باشد، باید ویژگی [`required`](/en-US/docs/Web/HTML/Reference/Elements/input#required) به آن اعمال شود. ویژگی `required` در HTML از ارسال فرم جلوگیری می‌کند مگر اینکه کنترل‌های فرم ضروری دارای مقادیر معتبر باشند، و در عین حال اطمینان حاصل می‌کند که افرادی که با کمک فناوری‌های کمکی پیمایش می‌کنند، متوجه می‌شوند کدام کنترل‌های فرم معنایی نیاز به محتوای معتبر دارند.

هنگامی که کنترل‌های فرم با استفاده از عناصر غیر معنایی، مانند یک {{HTMLElement('div')}} با [نقش](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles) [`checkbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/checkbox_role) ساخته می‌شوند، باید ویژگی `aria-required` با مقدار `true` گنجانده شود تا به فناوری‌های کمکی نشان دهد که ورودی کاربر در آن عنصر برای قابل ارسال بودن فرم ضروری است. ویژگی `aria-required` می‌تواند با عناصر فرم HTML استفاده شود؛ محدود به عناصری نیست که دارای نقش ARIA هستند.

مشابه ویژگی `required` در HTML که روی کنترل‌های فرم معنایی تنظیم می‌شود، ویژگی `aria-required` به صراحت به فناوری‌های کمکی اعلام می‌کند که عنصر قبل از ارسال فرم ضروری است. ویژگی `required` روی یک کنترل فرم معنایی HTML از ارسال کنترل فرم در صورت отсутствие مقدار جلوگیری می‌کند و در برخی مرورگرها پیام خطای بومی ارائه می‌دهد اگر مقدار ضروری در هنگام تلاش کاربر برای ارسال فرم نامعتبر باشد. ویژگی `aria-required`، مانند تمام حالات و ویژگی‌های ARIA، تأثیری بر عملکرد عنصر ندارد. عملکرد و رفتار باید با جاوااسکریپت اضافه شود.

> [!NOTE]
> ARIA تنها درخت دسترسی را تغییر می‌دهد و نحوه ارائه محتوا به کاربران توسط فناوری کمکی را تغییر می‌دهد. ARIA چیزی در مورد عملکرد یا رفتار یک عنصر تغییر نمی‌دهد. هنگامی که از عناصر HTML معنایی برای هدف مورد نظر و عملکرد پیش‌فرض آنها استفاده نمی‌کنید، باید از جاوااسکریپت برای مدیریت رفتار، فوکوس و حالات ARIA استفاده کنید.

شبه‌کلاس‌های CSS {{CSSXRef(':required')}} و {{CSSXRef(':optional')}} به ترتیب عناصر {{htmlelement("input")}}، {{htmlelement("select")}} و {{htmlelement("textarea")}} را بر اساس ضروری یا اختیاری بودن آنها مطابقت می‌دهند. هنگام استفاده از عناصر غیر معنایی به عنوان کنترل‌های فرم، از این مزیت انتخاب‌گر شبه‌کلاس CSS برخوردار نیستید. با این حال، می‌توانید از انتخاب‌گرهای ویژگی در صورت وجود ویژگی استفاده کنید: `[aria-required="true"]` یا `[aria-required="false"]`.

اگر یک فرم شامل عناصر فرم ضروری و اختیاری باشد، عناصر ضروری باید به صورت بصری با استفاده از روشی که صرفاً به رنگ وابسته نیست، نشان داده شوند. معمولاً از متن توصیفی و/یا یک نماد استفاده می‌شود.

> [!NOTE]
> باید برای همه کاربران مشخص باشد که کدام عناصر ضروری هستند. اطمینان حاصل کنید که نمایش بصری کنترل فرم را به صورت ضروری و به شیوه‌ای ثابت و قابل مشاهده نشان می‌دهد، و به خاطر داشته باشید که رنگ به تنهایی برای انتقال اطلاعات کافی نیست.

## مثال‌ها

ویژگی باید به نقش کنترل فرم اضافه شود. اگر کاربر نیاز به پر کردن آدرس ایمیل [`textbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role) دارد، `aria-required="true"` را روی جعبه متن قرار دهید.

```html
<div id="tbLabel">آدرس ایمیل *</div>
<div
  role="textbox"
  contenteditable
  aria-labelledby="tblabel"
  aria-required="true"
  id="email1"></div>
```

> [!NOTE]
> اگر برچسب فیلد از قبل شامل کلمه «ضروری» است، توصیه می‌شود ویژگی `aria-required` را حذف کنید. این کار از خواندن دوباره عبارت «ضروری» توسط صفحه‌خوان‌ها جلوگیری می‌کند.

در این مثال، باید از جاوااسکریپت استفاده شود تا از ارسال فرم حاوی آن در صورت نداشتن محتوای جعبه متن جلوگیری شود.

این می‌تواند به صورت معنایی و بدون نیاز به جاوااسکریپت نوشته شود:

```html
<label for="email1">آدرس ایمیل (ضروری)</label>
<input type="email" id="email1" required />
```

## مقادیر

- `true`
  - : عنصر نیاز به مقدار دارد یا باید برای قابل ارسال بودن فرم علامت‌گذاری شود.
- `false`
  - : عنصر ضروری نیست.

## رابط‌های مرتبط

- {{domxref("Element.ariaRequired")}}
  - : ویژگی [`ariaRequired`](/en-US/docs/Web/API/Element/ariaRequired) که بخشی از رابط {{domxref("Element")}} است، مقدار ویژگی `aria-required` را منعکس می‌کند.
- {{domxref("ElementInternals.ariaRequired")}}
  - : ویژگی [`ariaRequired`](/en-US/docs/Web/API/ElementInternals/ariaRequired) که بخشی از رابط {{domxref("ElementInternals")}} است، مقدار ویژگی `aria-required` را منعکس می‌کند.

## نقش‌های مرتبط

مورد استفاده در نقش‌ها:

- [`checkbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/checkbox_role)
- [`combobox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role)
- [`gridcell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role)
- [`listbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listbox_role)
- [`radiogroup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radiogroup_role)
- [`spinbutton`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/spinbutton_role)
- [`textbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role)
- [`tree`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tree_role)

به ارث برده شده در نقش‌ها:

- [`columnheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role)
- [`rowheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowheader_role)
- [`searchbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/searchbox_role)
- [`switch`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/switch_role)
- [`treegrid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treegrid_role)

## مشخصات

{{Specifications}}

## همچنین ببینید

- ویژگی HTML [`required`](/en-US/docs/Web/HTML/Reference/Elements/input#required)
- [شبه‌کلاس `:optional`](/en-US/docs/Web/CSS/Reference/Selectors/:optional)
- [شبه‌کلاس `:required`](/en-US/docs/Web/CSS/Reference/Selectors/:required)
- [ویژگی `aria-invalid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-invalid)
- [MDN Understanding WCAG, Guideline 3.3 توضیحات](/en-US/docs/Web/Accessibility/Guides/Understanding_WCAG/Understandable#guideline_3.3_%e2%80%94_input_assistance_help_users_avoid_and_correct_mistakes)
- [Understanding Success Criterion 3.3.2 | W3C Understanding WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/minimize-error-cues.html)