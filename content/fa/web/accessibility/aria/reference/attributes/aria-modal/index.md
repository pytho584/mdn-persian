---
title: "ARIA: aria-modal attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-modal"
translated_by: "n8n + AI"
---

---
title: "ARIA: aria-modal attribute"
short-title: aria-modal
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-modal
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-modal
sidebar: accessibilitysidebar
---

ویژگی `aria-modal` نشان می‌دهد که آیا یک عنصر هنگام نمایش، modal است یا خیر.

## توضیحات

بخشی از محتوا به معنای "modal" بودن این است که ناوبری به خود آن بخش محدود می‌شود و پس‌زمینه (اجداد و خواهر و برادرهای modal) پنهان می‌شود. تنظیم `aria-modal="true"` روی ظرف‌های [`dialog`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/dialog_role) و [نقش `alertdialog`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/alertdialog_role) به کاربران فناوری کمکی وجود یک عنصر "modal" را اطلاع می‌دهد، اما عملاً عنصر را modal نمی‌کند. ویژگی‌هایی که عنصر را واقعاً modal می‌کنند باید توسط توسعه‌دهنده پیاده‌سازی شوند.

> [!NOTE]
> ARIA فقط درخت دسترس‌پذیری را تغییر می‌دهد و نحوه ارائه محتوا به کاربران توسط فناوری کمکی را تغییر می‌دهد. ARIA هیچ چیزی را در عملکرد یا رفتار یک عنصر تغییر نمی‌دهد. برای ایجاد جلوه modal باید از JavaScript برای مدیریت رفتار، تمرکز و حالت‌های ARIA استفاده کنید.

تنها در ظرف‌های `dialog` و `alertdialog` مرتبط است؛ تنظیم `aria-modal="true"` به فناوری‌های کمکی می‌گوید که به کاربر اطلاع دهند توانایی تعامل با یا دسترسی به محتوای دیگر صفحه مستلزم بسته شدن یا از دست دادن تمرکز گفتگوی modal است.

دیالوگ‌های modal زمانی هستند که محتوا نمایش داده می‌شود و تعامل کاربر فقط به آن بخش محدود می‌شود تا زمانی که dismissed (بسته) شود.

هنگام ایجاد دیالوگ‌های modal، `aria-modal="true"` به فناوری‌های کمکی می‌گوید که پنجره‌های زیر دیالوگ فعلی بخشی از محتوای modal نیستند.

هنگامی که یک عنصر modal نمایش داده می‌شود، تمرکز باید در modal قرار گیرد. تمرکز باید تا زمانی که modal قابل مشاهده است و تا زمان بسته شدن، داخل آن "به دام بیفتد". فناوری کمکی (<abbr>AT</abbr>) سپس می‌تواند محتوای modal را مرور کند و دامنه محتوای modal را درک کند. ویژگی `aria-modal` به فناوری کمکی کمک می‌کند مرزهای modal را ارتباط دهد و آن را از بقیه محتوای صفحه متمایز کند. هنگام dismissed شدن، تمرکز باید به عنصری که modal را فعال کرده بازگردد.

اطمینان حاصل کنید که modal فقط با استفاده از عناصر فرزند آن قابل کنترل است. اگر یک دیالوگ modal دکمه بستن داشته باشد، این دکمه باید یک فرزند باشد که در DOM درون ظرف modal قرار دارد.

هنگامی که یک عنصر modal نمایش داده می‌شود، نویسندگان **باید** تمام محتوای دیگر را به عنوان inert (مانند "زیردرختان inert" در HTML) علامت‌گذاری کنند. محتوای disabled محتوای inert نیست. محتوای inert را نمی‌توان با حالت‌های مرور عادی و تخصصی مانند مرور caret که به کاربر فناوری کمکی اجازه می‌دهد صفحه را با جزئیات کاوش کند، تعامل کرد. این شامل محتوای disabled نیز می‌شود که ممکن است محتوای معنی‌داری فراهم کند.

ویژگی [`inert`](/en-US/docs/Web/HTML/Reference/Global_attributes/inert) یک ویژگی بولی است که با حضور خود نشان می‌دهد که آن عنصر و تمام فرزندان شامل سایه آن باید inert شوند.

افزودن `aria-modal="true"` به یک [`dialog`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/dialog_role) یا [`alertdialog`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/alertdialog_role) نیاز به قرار دادن [`aria-hidden`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-hidden) را روی محتوای پس‌زمینه حذف می‌کند، زیرا `aria-modal` به فناوری‌های کمکی اطلاع می‌دهد که محتوای خارج از دیالوگ inert است. توجه داشته باشید که اگرچه پشتیبانی از عنصر {{HTMLElement("dialog")}} خوب است، آزمایش کامل پیاده‌سازی شما بسیار حیاتی است.

اگر یک دیالوگ modal نیست — پس‌زمینه inert وجود ندارد و تمرکز به دیالوگ محدود نیست — یا `aria-modal="false"` را شامل کنید یا ویژگی را به طور کلی حذف کنید.

## مثال

```html
<div id="backdrop" class="no-scroll">
  <div
    role="alertdialog"
    aria-modal="true"
    aria-labelledby="dialog_label"
    aria-describedby="dialog_desc">
    <h2 id="dialog_label">Confirmation</h2>
    <div id="dialog_desc">
      <p>Are you sure you want to delete this file?</p>
    </div>
    <button id="close-btn" type="button">No. Close this popup.</button>
    <button id="confirm-btn" type="button">Yes. Delete the file.</button>
  </div>
</div>
```

```js
document.getElementById("close-btn").addEventListener("click", () => {
  closeDialog();
});

document.getElementById("confirm-btn").addEventListener("click", (event) => {
  deleteFile();
});
```

این مثال جزئی شامل یک `alertdialog` است که در یک پس‌زمینه تمام‌صفحه و غیرقابل پیمایش قرار گرفته است.

[نقش `alertdialog`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/alertdialog_role) عنصری را که به عنوان ظرف دیالوگ هشدار عمل می‌کند شناسایی می‌کند. [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) با اشاره به عنصری که عنوان دیالوگ هشدار را فراهم می‌کند، یک نام قابل دسترس به دیالوگ هشدار می‌دهد. ویژگی [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) به دیالوگ هشدار یک {{glossary("accessible description")}} می‌دهد با اشاره به محتوای دیالوگ هشدار که پیام اصلی یا هدف دیالوگ هشدار را توصیف می‌کند.

`aria-modal="true"` به کاربر فناوری کمکی اطلاع می‌دهد که محتوای زیر دیالوگ تا زمانی که عنصر با اعلام `role="alertdialog"` دارای تمرکز باشد، تعاملی نیست.

ویژگی `aria-modal` وجود modal را به فناوری‌های کمکی افشا می‌کند تا غیرفعال کردن محتوای پشت modal به کاربران AT منتقل شود. مانند همه ویژگی‌های ARIA، `aria-modal` به خودی خود تأثیری بر عملکرد صفحه ندارد؛ مدیریت تمرکز و غیرفعال‌سازی، تعامل‌پذیری روی عناصر پس‌زمینه، و قابلیت حذف تمرکز از alertdialog همه باید با JavaScript مدیریت شوند.

## مقادیر

- `false` (پیش‌فرض)
  - : عنصر modal نیست.
- `true`
  - : عنصر modal است.

## رابط‌های مرتبط

- {{domxref("Element.ariaModal")}}
  - : ویژگی [`ariaModal`](/en-US/docs/Web/API/Element/ariaModal) که بخشی از رابط {{domxref("Element")}} است، مقدار ویژگی `aria-modal` را بازتاب می‌دهد.
- {{domxref("ElementInternals.ariaModal")}}
  - : ویژگی [`ariaModal`](/en-US/docs/Web/API/ElementInternals/ariaModal) که بخشی از رابط {{domxref("ElementInternals")}} است، مقدار ویژگی `aria-modal` را بازتاب می‌دهد.

## نقش‌های مرتبط

استفاده شده در نقش‌ها:

- [`window`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/window_role)

به ارث رفته در نقش‌ها:

- [`alertdialog`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/alertdialog_role)
- [`dialog`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/dialog_role)

## مشخصات

{{Specifications}}

## همچنین ببینید

- عنصر HTML {{HTMLElement("dialog")}}
- [نقش `alertdialog`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/alertdialog_role)
- [نقش `dialog`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/dialog_role)
- HTML [ویژگی سراسری `inert`](/en-US/docs/Web/HTML/Reference/Global_attributes/inert)
- ویژگی [`inert`](/en-US/docs/Web/API/HTMLElement/inert) در API عنصر HTML