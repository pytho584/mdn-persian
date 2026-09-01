---
title: "Element: ariaLabelledByElements property"
short-title: ariaLabelledByElements
slug: Web/API/Element/ariaLabelledByElements
page-type: web-api-instance-property
browser-compat: api.Element.ariaLabelledByElements
---

{{APIRef("DOM")}}

ویژگی **`ariaLabelledByElements`** در رابط {{domxref("Element")}} یک آرایه شامل عنصر (یا عناصری) است که نام دسترس‌پذیر (accessible name) را برای عنصری که این ویژگی روی آن اعمال شده فراهم می‌کنند.

این ویژگی منعکس‌کننده [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) (در برخی شرایط) است و به همین ترتیب برای ارائه برچسب به عناصری در نظر گرفته شده است که روش استانداردی برای تعریف نام دسترس‌پذیر خود ندارند.
تفاوت اصلی این است که از این ویژگی می‌توان برای ارائه متن برچسب از عناصری استفاده کرد که `id` ندارند، و بر همه روش‌های دیگر تنظیم برچسب ARIA اولویت دارد.

## مقدار

آرایه‌ای از عناصر.
متن داخلی این عناصر را می‌توان با فاصله به هم چسباند تا نام دسترس‌پذیر به دست آید.

هنگام خواندن، آرایه بازگشتی ثابت (static) و فقط‌خواندنی است.
هنگام نوشتن، آرایه اختصاص‌داده‌شده کپی می‌شود: تغییرات بعدی در آرایه بر مقدار ویژگی تأثیر نمی‌گذارد.

## توضیحات

این ویژگی جایگزینی انعطاف‌پذیر برای استفاده از ویژگی [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) برای تنظیم نام دسترس‌پذیر است.
برخلاف `aria-labelledby`، عناصری که به این ویژگی اختصاص داده می‌شوند لزوماً نباید دارای ویژگی [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) باشند.

برای مثال، می‌توان از این ویژگی برای برچسب‌گذاری یک عنصر محتوا مانند {{htmlelement("div")}} یا {{htmlelement("span")}} استفاده کرد (به شرطی که [نقش ARIA مناسب](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby#associated_roles) به آن داده شده باشد).
این ویژگی بر سایر سازوکارهای ارائه نام دسترس‌پذیر برای عناصر اولویت دارد و بنابراین می‌تواند برای ارائه نام به عناصری نیز استفاده شود که به طور معمول نام خود را از محتوای داخلی یا از عنصر مرتبطی مانند برچسب (label) می‌گیرند.

این ویژگی وقتی تعریف شده باشد، ویژگی [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) عنصر را منعکس می‌کند، اما فقط برای مقادیر `id` ارجاع‌شده‌ای که با عناصر معتبر درون‌حوزه (in-scope) مطابقت دارند.
اگر این ویژگی تنظیم شود، ویژگی متناظر (attribute) پاک می‌شود.
برای اطلاعات بیشتر درباره ارجاع‌های عنصر منعکس‌شده و حوزه، به [ارجاع‌های عنصر منعکس‌شده](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references) در راهنمای _ویژگی‌های منعکس‌شده_ مراجعه کنید.

برای اطلاعات بیشتر درباره نحوه استفاده از ویژگی و این خاصیت، به [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) مراجعه کنید.

## مثال‌ها

### دریافت نام دسترس‌پذیر

این مثال نشان می‌دهد که چگونه می‌توان از `ariaLabelledByElements` برای دریافت برچسب ARIA تعریف‌شده با `aria-labelledby` استفاده کرد.

#### HTML

HTML دو عنصر {{htmlelement("span")}} تعریف می‌کند و شناسه‌های آن‌ها را در ویژگی `aria-labelledby` یک عنصر {{htmlelement("input")}} ارجاع می‌دهد.
نام دسترس‌پذیرِ `<input>` برابر با الحاق متن داخلی دو عنصر ارجاع‌شده، با جداکننده فاصله، است.

```html
<span id="label_1">Street name</span>
<input aria-labelledby="label_1 label_2" />
<span id="label_2">(just the name, no "Street" or "Road" or "Place")</span>
```

```html hidden
<pre id="log"></pre>
```

```css hidden
#log {
  height: 70px;
  overflow: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

#### JavaScript

کد زیر ابتدا مقدار ویژگی `aria-labelledby` را از {{domxref("Element.getAttribute()")}} ثبت می‌کند (رشته‌ای که مقادیر `id` عناصر ارجاع‌شده را فهرست می‌کند).
سپس بررسی می‌کند که آیا `ariaLabelledByElements` پشتیبانی می‌شود یا خیر، و اگر پشتیبانی شود، مقدار آن را ثبت می‌کند.
در نهایت رشته دسترس‌پذیر را برمی‌گرداند که با مرور عناصر و الحاق متن داخلی آن‌ها محاسبه می‌شود.

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

```js
const inputElement = document.querySelector("input");
log(`aria-labelledby: ${inputElement.getAttribute("aria-labelledby")}`);
// تست ویژگی ariaLabelledByElements
if ("ariaLabelledByElements" in Element.prototype) {
  // دریافت ariaLabelledByElements
  const labelElements = inputElement.ariaLabelledByElements;
  log(`ariaLabelledByElements: ${labelElements}`);

  // ثبت متن داخلی عناصر برای دریافت نام دسترس‌پذیر
  const text = labelElements.map((e) => e.textContent.trim()).join(" ");
  log(`Accessible name: ${text.trim()}`);
} else {
  log("element.ariaLabelledByElements: not supported by browser");
}
```

#### نتیجه

گزارش (log) زیر ارجاع‌های اصلی عنصر، عناصر مرتبط/بازگشتی و نام دسترس‌پذیر را نشان می‌دهد.
توجه داشته باشید که مثال هیچ کاری با متنی که در `<input>` نام خیابان وارد می‌شود انجام نمی‌دهد.

{{EmbedLiveSample("Get the accessible name","100%","150px")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby)
- {{domxref("ElementInternals.ariaLabelledByElements")}}
- [ارجاع‌های عنصر منعکس‌شده](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references) در راهنمای _بازتاب ویژگی (Attribute reflection)_.