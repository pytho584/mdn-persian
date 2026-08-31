---
title: "ARIA: aria-errormessage attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-errormessage"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-errormessage attribute"
short-title: aria-errormessage
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-errormessage
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-errormessage
sidebar: accessibilitysidebar
---

ویژگی `aria-errormessage` روی یک شیء، عنصر(هایی) را مشخص می‌کند که پیام خطا برای آن شیء را ارائه می‌دهند.

## توضیحات

وقتی خطایی از طرف کاربر ایجاد می‌شود، باید به کاربر اطلاع دهید که خطا وجود دارد و نحوه رفع آن را به او بگویید. دو ویژگی وجود دارد که باید استفاده کنید: [`aria-invalid="true"`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-invalid) را برای تعریف شیء به عنوان حالت خطا تنظیم کنید، سپس ویژگی `aria-errormessage` را با مقدار `id` عنصر (یا عناصری) که حاوی متن پیام خطا برای آن شیء است، اضافه کنید.

ویژگی `aria-errormessage` فقط زمانی باید استفاده شود که مقدار یک شیء معتبر نباشد؛ یعنی زمانی که [`aria-invalid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-invalid) روی `true` تنظیم شده باشد. اگر شیء معتبر است و شما ویژگی `aria-errormessage` را اضافه کرده‌اید، مطمئن شوید که عنصر ارجاع‌داده‌شده پنهان است، زیرا پیام موجود در آن مرتبط نیست.

وقتی `aria-errormessage` مرتبط است، عنصر(هایی) که به آن ارجاع می‌دهد باید قابل مشاهده باشند تا کاربران بتوانند پیام خطا را ببینند یا بشنوند.

اغلب اوقات، می‌خواهید عنصر حاوی پیام خطا یک [ناحیه زنده ARIA](/en-US/docs/Web/Accessibility/ARIA/Guides/Live_regions) باشد، مانند زمانی که یک پیام خطا پس از ارائه مقدار نامعتبر به کاربر نمایش داده می‌شود. پیام خطا باید توضیح دهد که چه چیزی اشتباه است و به کاربر اطلاع دهد که برای معتبر کردن شیء چه چیزی لازم است. افزودن پیام خطا به عنوان یک ناحیه زنده ARIA به فناوری‌های کمکی اطلاع می‌دهد که کاربر ممکن است از محتوای پیام خطا بهره‌مند شود حتی اگر پیام خطا به طور دیگری به کاربر منتقل نشود.

اگر شکست از نظر بصری آشکار است و توضیح صریح خطا ضروری است، یک پیام خطای قابل مشاهده قرار دهید و شیء نامعتبر را با ویژگی `aria-errormessage` پیوند دهید.

## مثال

ما چند استایل ایجاد می‌کنیم تا:

1. همه پیام‌های خطا را پنهان کنیم،
2. اشیاء نامعتبر را به صورت نامعتبر نشان دهیم، و
3. پیام‌های خطایی که خواهر/برادر بعد از یک شیء نامعتبر هستند را نشان دهیم.

از `aria-invalid="true"` برای شناسایی اشیاء نامعتبر استفاده می‌کنیم:

```css
.errormessage {
  visibility: hidden;
}

[aria-invalid="true"] {
  outline: 2px solid red;
}

[aria-invalid="true"] ~ .errormessage {
  visibility: visible;
}
```

وقتی یک شیء نامعتبر است، از جاوااسکریپت برای اضافه کردن `aria-invalid="true"` استفاده می‌کنیم. CSS بالا باعث می‌شود `.errormessage` که بعد از یک شیء نامعتبر قرار دارد قابل مشاهده شود.

```html
<p>
  <label for="email">Email address:</label>
  <input
    type="email"
    name="email"
    id="email"
    aria-invalid="true"
    aria-errormessage="err1" />
  <span id="err1" class="errormessage">Error: Enter a valid email address</span>
</p>
```

وقتی از حالت معتبر به نامعتبر رفتیم، تنها تغییر جاوااسکریپت برای این مثال به‌روزرسانی `aria-invalid` روی شیء ورودی ایمیل بود. از آنجایی که پیام خطا بعد از ورودی قرار دارد و قابل مشاهده و در دسترس در درخت دسترسی‌پذیری می‌شود، توانستیم مثال خود را ساده نگه داریم. همچنین می‌توانستیم از یک ویژگی [`aria-live`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-live) یا یک نقش ناحیه زنده مانند [`alert`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/alert_role) استفاده کنیم.

## مقادیر

- لیست ارجاع‌های ID
  - : `id` یا لیست جدا شده با فاصله از `id`های عناصری که حاوی پیام خطا برای عنصر فعلی هستند.

## رابط‌های مرتبط

- {{domxref("Element.ariaErrorMessageElements")}}
  - : ویژگی `ariaErrorMessageElements` بخشی از رابط هر عنصر است. مقدار آن یک آرایه از زیرکلاس‌های {{domxref("Element")}} است که ارجاع‌های `id` در ویژگی `aria-errormessage` را منعکس می‌کند ([با برخی ملاحظات](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references)).
- {{domxref("ElementInternals.ariaErrorMessageElements")}}
  - : ویژگی `ariaErrorMessageElements` بخشی از رابط هر عنصر سفارشی است. مقدار آن یک آرایه از زیرکلاس‌های {{domxref("Element")}} است که ارجاع‌های `id` در ویژگی `aria-errormessage` را منعکس می‌کند ([با برخی ملاحظات](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references)).

## نقش‌های مرتبط

استفاده شده در نقش‌ها:

- [`application`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/application_role)
- [`checkbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/checkbox_role)
- [`combobox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role)
- [`gridcell`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/gridcell_role)
- [`listbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listbox_role)
- [`radiogroup`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/radiogroup_role)
- [`slider`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/slider_role)
- [`spinbutton`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/spinbutton_role)
- [`textbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role)
- [`tree`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/tree_role)

به ارث برده از نقش‌ها:

- [`columnheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role)
- [`rowheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowheader_role)
- [`searchbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/searchbox_role)
- [`switch`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/switch_role)
- [`treegrid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treegrid_role)

## مشخصات

{{Specifications}}

## همچنین ببینید

- شبه‌کلاس CSS {{CSSxref(':invalid')}}
- [`aria-invalid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-invalid)
- [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby)
- [`aria-live`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-live)