---
title: "ARIA: aria-invalid attribute"
short-title: aria-invalid
slug: Web/Accessibility/ARIA/Reference/Attributes/aria-invalid
page-type: aria-attribute
spec-urls: https://w3c.github.io/aria/#aria-invalid
sidebar: accessibilitysidebar
translated_by: "n8n + AI"
---

حالت `aria-invalid` نشان می‌دهد که مقدار وارد شده با قالب مورد انتظار برنامه مطابقت ندارد.

## توضیحات

ویژگی `aria-invalid` برای نشان دادن این استفاده می‌شود که مقدار وارد شده در یک فیلد ورودی در قالبی نیست یا مقداری نیست که برنامه بپذیرد. این می‌تواند شامل قالب‌هایی مانند آدرس‌های ایمیل یا شماره تلفن باشد. همچنین می‌توان از `aria-invalid` برای نشان دادن خالی بودن یک فیلد اجباری استفاده کرد.

ویژگی `aria-invalid` می‌تواند با هر عنصر فرم HTML معمولی استفاده شود و محدود به عناصری نیست که نقش ARIA به آنها اختصاص داده شده است.

این ویژگی باید با استفاده از جاوااسکریپت در نتیجه یک فرآیند اعتبارسنجی تنظیم شود. اگر مقداری نامعتبر یا خارج از محدوده تشخیص داده شد، `aria-invalid="true"` تنظیم کنید **و** به کاربر اطلاع دهید که خطایی وجود دارد. برای تجربه کاربری بهتر، پیشنهاداتی برای نحوه اصلاح خطا ارائه دهید. `aria-invalid="true"` را روی عناصر اجباری خالی تنظیم نکنید مگر اینکه کاربر تلاش کرده باشد فرم را ارسال کند. ممکن است هنوز در حال تکمیل آن باشند.

> [!NOTE]
> هنگامی که از `aria-invalid` همراه با ویژگی `aria-required` استفاده می‌شود، `aria-invalid` نباید قبل از ارسال فرم روی true تنظیم شود - فقط در پاسخ به اعتبارسنجی.

در حال حاضر چهار مقدار وجود دارد: علاوه بر `true` و `false`، `grammar` داریم که می‌تواند زمانی که خطای دستوری تشخیص داده شود استفاده شود و `spelling` برای خطاهای املایی. اگر ویژگی وجود نداشته باشد، یا مقدار آن false باشد، یا مقدار آن یک رشته خالی باشد، مقدار پیش‌فرض false اعمال می‌شود. هر مقدار دیگری به عنوان `true` در نظر گرفته می‌شود.

### اعتبارسنجی بومی HTML

HTML دارای اعتبارسنجی فرم بومی است. هنگامی که کاربر فرمی را با یک کنترل حاوی خطا ارسال می‌کند، اولین کنترل فرم با مقدار نامعتبر یک پیام خطا را به صورت بومی نمایش می‌دهد.

اگر یک ویژگی [`required`](/en-US/docs/Web/HTML/Reference/Attributes/required) روی یک کنترل فرم وجود داشته باشد که پر نشده باشد، فرم ارسال نمی‌شود و یک پیام خطا با عنوان "لطفاً این فیلد را پر کنید" یا مشابه آن ظاهر می‌شود. پیام‌دهی برای اعتبارسنجی بومی بسته به مرورگر متفاوت است و قابل استایل‌دهی نیست.

```html
<input type="number" step="2" min="0" max="100" required />
```

اگر کاربر مقداری در مثال ورودی بالا وارد کرده باشد که بیشتر از حداکثر، کمتر از حداقل، یا مطابق با مقدار step نباشد، یک پیام خطا ظاهر می‌شود. اگر کاربر "3" را وارد کرده باشد، پیام خطای بومی مشابه "لطفاً یک مقدار معتبر وارد کنید" خواهد بود.

اگر در حال ایجاد اسکریپت‌های اعتبارسنجی فرم خود هستید، حتماً `aria-invalid` را روی کنترل‌های فرم نامعتبر قرار دهید، همراه با استایل‌دهی (با استفاده از انتخابگر ویژگی `[aria-invalid="true"]`) و پیام‌دهی (با [`aria-errormessage`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-errormessage)) برای کمک به کاربران در درک محل اشتباه و نحوه رفع آن.

## مقادیر

- `grammar`
  - : یک خطای دستوری تشخیص داده شد.
- `false` (پیش‌فرض)
  - : هیچ خطای تشخیص داده شده‌ای در مقدار وجود ندارد.
- `spelling`
  - : یک خطای املایی تشخیص داده شد.
- `true`
  - : مقدار وارد شده توسط کاربر از اعتبارسنجی عبور نکرده است.

هر مقداری که در این لیست نباشد به عنوان `true` در نظر گرفته می‌شود.

## مثال

قطعه کد زیر یک نسخه ساده‌شده از دو فیلد فرم را با یک تابع اعتبارسنجی متصل به رویداد blur نشان می‌دهد. توجه داشته باشید که از آنجایی که مقدار پیش‌فرض برای `aria-invalid` برابر با `false` است، افزودن ویژگی به input ضروری نیست.

```html
<ul>
  <li>
    <label for="name">نام کامل</label>
    <input
      type="text"
      name="name"
      id="name"
      aria-required="true"
      aria-invalid="false" />
  </li>
  <li>
    <label for="email">آدرس ایمیل</label>
    <input
      type="email"
      name="email"
      id="email"
      aria-required="true"
      aria-invalid="false" />
  </li>
</ul>
```

```js
document.getElementById("name").addEventListener("blur", () => {
  checkValidity(
    "name",
    " ",
    "نام نامعتبر وارد شده است (نیاز به نام و نام خانوادگی دارد)",
  );
});

document.getElementById("email").addEventListener("blur", () => {
  checkValidity("email", "@", "آدرس ایمیل نامعتبر");
});
```

توجه داشته باشید که نیازی به اعتبارسنجی فوری فیلدها در رویداد blur نیست؛ برنامه می‌تواند تا زمان ارسال فرم صبر کند (البته این کار لزوماً توصیه نمی‌شود).

قطعه کد زیر یک تابع اعتبارسنجی را نشان می‌دهد که فقط وجود یک کاراکتر خاص را بررسی می‌کند (در دنیای واقعی، اعتبارسنجی احتمالاً پیچیده‌تر خواهد بود):

```js
function checkValidity(id, searchTerm, msg) {
  const elem = document.getElementById(id);
  if (elem.value.includes(searchTerm)) {
    elem.setAttribute("aria-invalid", "false");
    updateAlert();
  } else {
    elem.setAttribute("aria-invalid", "true");
    updateAlert(msg);
  }
}
```

قطعه کد زیر توابع هشدار را نشان می‌دهد که پیام خطا را اضافه (یا حذف) می‌کنند:

```js
function updateAlert(msg) {
  const oldAlert = document.getElementById("alert");
  if (oldAlert) {
    oldAlert.remove();
  }

  if (msg) {
    const newAlert = document.createElement("div");
    newAlert.setAttribute("role", "alert");
    newAlert.setAttribute("id", "alert");
    const content = document.createTextNode(msg);
    newAlert.appendChild(content);
    document.body.appendChild(newAlert);
  }
}
```

توجه داشته باشید که هشدار دارای ویژگی نقش ARIA تنظیم شده بر روی [`alert`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/alert_role) است.

## واسط‌های مرتبط

- {{domxref("Element.ariaInvalid")}}
  - : ویژگی [`ariaInvalid`](/en-US/docs/Web/API/Element/ariaInvalid)، بخشی از واسط {{domxref("Element")}}، مقدار ویژگی `aria-invalid` را منعکس می‌کند که نشان می‌دهد آیا عنصر در معرض یک API دسترس‌پذیری قرار دارد یا خیر.
- {{domxref("ElementInternals.ariaInvalid")}}
  - : ویژگی [`ariaInvalid`](/en-US/docs/Web/API/ElementInternals/ariaInvalid)، بخشی از واسط {{domxref("ElementInternals")}}، مقدار ویژگی `aria-invalid` را منعکس می‌کند.

## نقش‌های مرتبط

مورد استفاده در نقش‌ها:

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

به ارث رسیده به نقش:

- [`columnheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/columnheader_role)
- [`rowheader`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/rowheader_role)
- [`searchbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/searchbox_role)
- [`switch`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/switch_role)
- [`treegrid`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/treegrid_role)

## مشخصات

{{Specifications}}

## همچنین ببینید

- [`aria-errormessage`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-errormessage)
- شبه‌کلاس CSS {{CSSXRef(':valid')}}
- شبه‌کلاس CSS {{CSSXRef(':invalid')}}
- آموزش [اعتبارسنجی فرم](/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation)
```