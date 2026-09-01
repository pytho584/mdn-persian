```
---
title: "ElementInternals: ariaLabelledByElements property"
short-title: ariaLabelledByElements
slug: Web/API/ElementInternals/ariaLabelledByElements
page-type: web-api-instance-property
browser-compat: api.ElementInternals.ariaLabelledByElements
---

{{APIRef("DOM")}}

ویژگی **`ariaLabelledByElements`** از رابط {{domxref("ElementInternals")}} آرایه‌ای شامل عنصر (یا عناصر) است که نام قابل‌دسترس (accessible name) را برای عنصری که به آن اعمال شده فراهم می‌کنند.

این ویژگی عمدتاً برای فراهم‌کردن برچسب (label) برای عناصری در نظر گرفته شده است که روش استانداردی برای تعریف نام قابل‌دسترس ندارند. برای مثال، می‌توان از آن برای نام‌گذاری یک عنصر قالبی (generic container) مانند {{htmlelement("div")}} یا {{htmlelement("span")}}، یا گروهی از عناصر مانند تصویری با یک لغزنده (slider) که برای تغییر شفافیت به کار می‌رود، استفاده کرد. این ویژگی بر سایر سازوکارهای فراهم‌کردن نام قابل‌دسترس برای عناصر اولویت دارد؛ بنابراین می‌توان از آن برای نام‌گذاری عناصری نیز استفاده کرد که به‌طور معمول نام خود را از محتوای داخلی یا از یک عنصر مرتبط مانند برچسب دریافت می‌کنند.

موضوع [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) حاوی اطلاعات بیشتری درباره نحوه استفاده از این ویژگی (attribute) و این خاصیت (property) است.

## مقدار

آرایه‌ای از عناصر. برای به دست آوردن نام قابل‌دسترس، می‌توان متن داخلی این عناصر را با فاصله به هم پیوست.

هنگام خواندن، آرایه بازگشتی ایستا و فقط‌خواندنی است. هنگام نوشتن، آرایه اختصاص‌داده‌شده کپی می‌شود؛ تغییرات بعدی در آرایه تأثیری بر مقدار خاصیت نخواهد گذاشت.

## توضیحات

این خاصیت جایگزینی منعطف برای استفاده از ویژگی [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) برای تنظیم نام قابل‌دسترس است. برخلاف `aria-labelledby`، عناصر اختصاص‌داده‌شده به این خاصیت لازم نیست دارای ویژگی [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) باشند.

این خاصیت ویژگی [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby) عنصر را هنگام‌که تعریف شده است بازتاب می‌دهد، اما فقط برای مقادیر `id` ارجاع‌داده‌شده در فهرست که با عناصر معتبر در حوزه (in-scope) مطابقت دارند. اگر این خاصیت تنظیم شود، ویژگی متناظر پاک می‌شود. برای اطلاعات بیشتر درباره ارجاع‌های بازتاب‌یافته عناصر و حوزه، به [ارجاع‌های بازتاب‌یافته عناصر](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references) در راهنمای _بازتاب ویژگی‌ها_ مراجعه کنید.

## مثال‌ها

### Get the accessible name

این مثال نشان می‌دهد که چگونه می‌توان از `ariaLabelledByElements` برای دریافت برنامه‌نویسی برچسبی که با استفاده از `aria-labelledby` درون shadow root تعریف شده است استفاده کرد.

#### HTML

اچ‌تی‌ام‌ال دو عنصر {{htmlelement("span")}} را تعریف می‌کند و شناسه‌های آنها را در ویژگی `aria-labelledby` یک {{htmlelement("input")}} ارجاع می‌دهد. بنابراین نام قابل‌دسترس `<input>` برابر با الحاق متن داخلی آن دو عنصر ارجاع‌داده‌شده است.

```html
<div id="host">
  <template shadowrootmode="open">
    <span id="label_1">Street name</span>
    <input aria-labelledby="label_1 label_2" />
    <span id="label_2">(just the name, no "Street" or "Road" or "Place")</span>
  </template>
</div>
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

کد زیر ابتدا بررسی می‌کند که آیا `ariaLabelledByElements` پشتیبانی می‌شود؛ اگر پشتیبانی نشود، نتیجه را در لاگ ثبت می‌کند و خارج می‌شود. اگر این خاصیت پشتیبانی شود، ابتدا مقدار خاصیت را در لاگ ثبت می‌کند. سپس روی عناصر بازگشتی پیمایش می‌کند، متن داخلی آنها را به هم می‌چسباند و نام قابل‌دسترس حاصل از عنصر را در لاگ ثبت می‌کند.

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

```js
// Get access to the input within shadowRoot
const hostElement = document.getElementById("host");
const shadowRoot = hostElement.shadowRoot;
const inputElement = shadowRoot.querySelector("input");

// Feature test for ariaLabelledByElements
if ("ariaLabelledByElements" in ElementInternals.prototype) {
  // Get and log attribute that provides the accessible name
  log(`aria-labelledby: ${inputElement.getAttribute("aria-labelledby")}`);

  // Get and log elements that provide the accessible name
  const labelElements = inputElement.ariaLabelledByElements;
  log(`ariaLabelledByElements: ${labelElements}`);

  // Log inner text of elements to get accessible name
  const text = labelElements.map((e) => e.textContent.trim()).join(" ");
  log(`Accessible name: ${text.trim()}`);
} else {
  log("ariaLabelledByElements not supported by browser");
}
```

#### نتیجه

لاگ زیر خروجی کد بالا را نشان می‌دهد. این باید آرایه‌ای از عناصر {{domxref("HTMLSpanElement")}} ارجاع‌داده‌شده و نام قابل‌دسترس حاصل از متن داخلی آنها را نشان دهد.

{{EmbedLiveSample("Get the accessible name","100%","150px")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی [`aria-labelledby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-labelledby)
- {{domxref("Element.ariaLabelledByElements")}}
- [ارجاع‌های بازتاب‌یافته عناصر](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references) در راهنمای _بازتاب ویژگی‌ها_
```