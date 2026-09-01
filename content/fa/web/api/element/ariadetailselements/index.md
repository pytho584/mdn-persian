---
title: "Element: ariaDetailsElements property"
short-title: ariaDetailsElements
slug: Web/API/Element/ariaDetailsElements
page-type: web-api-instance-property
browser-compat: api.Element.ariaDetailsElements
---

{{APIRef("DOM")}}

ویژگی **`ariaDetailsElements`** در رابط {{domxref("Element")}} آرایه‌ای است شامل عنصر (یا عناصری) که برای عنصرِ موردنظر، جزئیات دسترس‌پذیر فراهم می‌کنند. این جزئیات دسترس‌پذیر مشابه توصیف دسترس‌پذیر هستند (به {{domxref("Element/ariaDescribedByElements","ariaDescribedByElements")}} مراجعه کنید)، اما اطلاعات کامل‌تری ارائه می‌دهند.

مبحث [`aria-details`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-details) حاوی اطلاعات بیشتری درباره نحوه استفاده از این ویژگی و خصوصیت است.

## مقدار

آرایه‌ای از زیرکلاس‌های {{domxref("HTMLElement")}}.
متن درونی این عناصر را می‌توان با فاصله به یکدیگر الحاق کرد تا جزئیات دسترس‌پذیر به دست آید.

هنگام خواندن، آرایه بازگردانده‌شده ایستا و فقط‌خواندنی است. هنگام نوشتن، آرایه تخصیص‌داده‌شده کپی می‌شود؛ تغییرات بعدی در آرایه بر مقدار این خصوصیت تأثیری نمی‌گذارد.

## توضیحات

این خصوصیت جایگزینی انعطاف‌پذیر برای استفاده از ویژگی [`aria-details`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-details) به‌منظور تنظیم اطلاعات جزئیات دسترس‌پذیر است. برخلاف `aria-details`، عناصر تخصیص‌داده‌شده به این خصوصیت الزامی به داشتن ویژگی [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) ندارند.

این خصوصیت، ویژگی [`aria-details`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-details) عنصر را — در صورت تعریف‌شدن — بازتاب می‌دهد؛ اما فقط برای مقادیر `id` مرجع فهرست‌شده‌ای که با عناصر معتبر درون‌حوزه مطابقت دارند. اگر این خصوصیت تنظیم شود، ویژگی متناظر پاک می‌شود. برای اطلاعات بیشتر درباره بازتاب ارجاع‌های عنصر و حوزه، به [بازتاب ارجاع‌های عنصر](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references) در راهنمای _بازتاب ویژگی‌ها_ مراجعه کنید.

## مثال‌ها

### دریافت جزئیات دسترس‌پذیر

این مثال نشان می‌دهد که چگونه می‌توان از `ariaDetailsElements` برای دریافت اطلاعات تعریف‌شده با ویژگی `aria-details` در HTML استفاده کرد.

#### HTML

در HTML دو عنصر {{htmlelement("span")}} تعریف شده‌اند و شناسه‌های آن‌ها در ویژگی `aria-details` یک {{htmlelement("button")}} ارجاع داده شده‌اند.

```html
<button aria-details="details1 details2">Button text</button>
…
<span id="details1">Details 1 information about the element.</span>
<span id="details2">Details 2 information about the element.</span>
```

```html hidden
<pre id="log"></pre>
```

```css hidden
#log {
  height: 70px;
  overflow-x: scroll;
  padding: 0.5rem;
  border: 1px solid black;
}
```

#### JavaScript

کد زیر ابتدا مقدار ویژگی `aria-details` را از {{domxref("Element.getAttribute()")}} ثبت می‌کند (رشته‌ای که مقادیر `id` عناصر ارجاع‌شده را فهرست می‌کند). سپس بررسی می‌کند که آیا `ariaDetailsElements` پشتیبانی می‌شود و در صورت پشتیبانی، مقدار آن را ثبت می‌کند. در پایان، رشته دسترس‌پذیر را برمی‌گرداند که با پیمایش عناصر بازگردانده‌شده و الحاق متن درونی آن‌ها محاسبه می‌شود.

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

```js
const buttonElement = document.querySelector("button");
log(`aria-details: ${buttonElement.getAttribute("aria-details")}`);
// Feature test for ariaDetailsElements
if ("ariaDetailsElements" in Element.prototype) {
  // Get ariaDetailsElements
  const buttonElements = buttonElement.ariaDetailsElements;
  log(`ariaDetailsElements: ${buttonElements}`);

  // Accessible details from ariaDetailsElements
  const text = buttonElements.map((e) => e.textContent.trim()).join(" ");
  log(`Accessible details: ${text.trim()}`);
} else {
  log("element.ariaDetailsElements: not supported by browser");
}
```

#### نتیجه

گزارش زیر ارجاع‌های عنصر اصلی، عناصر مرتبط/بازگردانده‌شده و جزئیات دسترس‌پذیر را نشان می‌دهد.

{{EmbedLiveSample("Get the accessible details","100%","150px")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- ویژگی [`aria-details`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-details)
- {{domxref("ElementInternals.ariaDetailsElements")}}
- [بازتاب ارجاع‌های عنصر](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references) در راهنمای _بازتاب ویژگی‌ها_.