---
title: "ARIA: alertdialog role"
source: "https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/alertdialog_role"
translated_by: "n8n + AI"
---

---
title: "ARIA: alertdialog role"
short-title: alertdialog
slug: Web/Accessibility/ARIA/Reference/Roles/alertdialog_role
page-type: aria-role
spec-urls: https://w3c.github.io/aria/#alertdialog
sidebar: accessibilitysidebar
---

نقش **alertdialog** برای استفاده در گفتگوهای هشداردهنده مدال (Modal) است که جریان کار کاربر را برای انتقال یک پیام مهم قطع کرده و نیاز به پاسخ دارند.

## توضیحات

نقش `alertdialog` برای اطلاع‌رسانی به کاربران در مورد اطلاعات فوری که نیاز به توجه فوری کاربر دارد، استفاده می‌شود. قرار دادن `role="alertdialog"` روی عنصر حاوی گفتگو به فناوری کمکی کمک می‌کند تا محتوا را به‌عنوان یک گروه و جدا از بقیه محتوای صفحه شناسایی کند. نمونه‌ها شامل پیام‌های خطا هستند که نیاز به تأیید دارند و سایر اعلان‌های تأیید اقدامات.

همان‌طور که از نام آن پیداست، `alertdialog` ترکیبی از نقش‌های [`dialog`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/dialog_role) و [`alert`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/alert_role) است. `alertdialog` نوعی `dialog` با موارد استفاده مشابه `alert` است، اما برای زمانی که پاسخ کاربر لازم است.

> [!NOTE]
> نقش `alertdialog` فقط باید برای پیام‌های هشدار استفاده شود که دارای کنترل‌های تعاملی مرتبط هستند. اگر یک گفتگوی هشدار فقط حاوی محتوای ایستا است و اصلاً کنترل تعاملی ندارد، به جای آن از [`alert`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/alert_role) استفاده کنید.

به عنوان نوعی `dialog`، حالات، ویژگی‌ها و الزامات تمرکز صفحه‌کلید نقش [`dialog`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/dialog_role) برای نقش `alertdialog` نیز قابل اعمال هستند.

به دلیل ماهیت فوری آن‌ها، که جریان کار کاربر را قطع می‌کند، گفتگوهای هشدار باید [modal](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-modal) باشند.

گفتگوی هشدار باید حداقل یک کنترل قابل تمرکز داشته باشد — مانند تأیید (Confirm)، بستن (Close) و لغو (Cancel) — و هنگام ظاهر شدن گفتگوی هشدار، تمرکز باید به آن کنترل منتقل شود. گفتگوهای هشدار می‌توانند کنترل‌های تعاملی اضافی مانند فیلدهای متنی و چک‌باکس داشته باشند.

نقش `alertdialog` نباید به عنوان جایگزینی برای سایر گفتگوها استفاده شود، از جمله گفتگوهای `alert` بدون نیاز به تأیید ([`Window.alert()`](/en-US/docs/Web/API/Window/alert)) و اعلان‌ها ([`Window.prompt()`](/en-US/docs/Web/API/Window/prompt)).

افزودن `role="alertdialog"` به تنهایی برای قابل دسترس کردن یک گفتگوی هشدار کافی نیست. موارد زیر نیز باید انجام شوند:

- گفتگوی هشدار باید به درستی برچسب‌گذاری شود
- تمرکز صفحه‌کلید باید به درستی مدیریت شود

عنصر `alertdialog` باید دارای نام قابل دسترس (accessible name) باشد که با [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) یا [`aria-label`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) تعریف شده باشد. متن گفتگوی هشدار باید با استفاده از [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) دارای {{glossary("accessible description")}} باشد.

### نقش‌ها، حالات و ویژگی‌های مرتبط WAI-ARIA

- [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby)
  - : از این ویژگی برای برچسب‌گذاری alertdialog استفاده کنید. ویژگی `aria-labelledby` معمولاً شناسه (id) عنصری است که برای عنوان alertdialog استفاده می‌شود.

- [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby)
  - : از این ویژگی برای دربرگرفتن توضیحات محتویات گفتگوی هشدار استفاده کنید. مقدار ویژگی `aria-describedby` معمولاً شناسه (ID) عنصری است که پیام‌های گفتگوی هشدار را شامل می‌شود، معمولاً بلافاصله بعد از عنوان قرار می‌گیرد.

## مثال‌ها

### مثال ۱: یک گفتگوی هشدار پایه

```html
<div
  role="alertdialog"
  aria-labelledby="dialog1Title"
  aria-describedby="dialog1Desc">
  <div role="document" tabindex="0">
    <h2 id="dialog1Title">Your login session is about to expire</h2>
    <p id="dialog1Desc">To extend your session, click the OK button</p>
    <button>OK</button>
  </div>
</div>
```

قطعه کد بالا نشان می‌دهد که چگونه یک گفتگوی هشدار را علامت‌گذاری کنیم که فقط یک پیام و یک دکمه OK ارائه می‌دهد.

### مثال ۲: گفتگوی تأیید با دو گزینه

```html
<div
  id="alert_dialog"
  role="alertdialog"
  aria-modal="true"
  aria-labelledby="dialog_label"
  aria-describedby="dialog_desc">
  <h2 id="dialog_label">Confirmation</h2>
  <div id="dialog_desc">
    <p>Are you sure you want to delete this image?</p>
    <p>This change can't be undone.</p>
  </div>
  <ul>
    <li>
      <button id="close-btn" type="button">No</button>
    </li>
    <li>
      <button id="confirm-btn" type="button" aria-controls="form">Yes</button>
    </li>
  </ul>
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

## مشخصات

{{Specifications}}

## همچنین ببینید

- المان HTML {{HTMLElement("dialog")}}
- [نقش `dialog`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/dialog_role)
- [نقش `alert`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/alert_role)
- [ویژگی `aria-modal`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-modal)
- [`Window.alert()`](/en-US/docs/Web/API/Window/alert)
- [`Window.prompt()`](/en-US/docs/Web/API/Window/prompt)