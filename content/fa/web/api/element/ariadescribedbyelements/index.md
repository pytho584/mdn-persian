---
title: "Element: ariaDescribedByElements property"
short-title: ariaDescribedByElements
slug: Web/API/Element/ariaDescribedByElements
page-type: web-api-instance-property
browser-compat: api.Element.ariaDescribedByElements
---

{{APIRef("DOM")}}

ویژگی **`ariaDescribedByElements`** از رابط {{domxref("Element")}} یک آرایه است که شامل عنصر (یا عناصری) است که یک توضیح دسترس‌پذیر (accessible description) برای عنصری که به آن اعمال شده است فراهم می‌کنند. توضیح دسترس‌پذیر مشابه برچسب دسترس‌پذیر (accessible label) است (به {{domxref("Element/ariaLabelledByElements","ariaLabelledByElements")}} مراجعه کنید)، اما اطلاعات دقیق‌تری ارائه می‌دهد.

موضوع [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) حاوی اطلاعات اضافی در مورد نحوه استفاده از این ویژگی (attribute) و خاصیت (property) است.

## مقدار

یک آرایه از زیرکلاس‌های {{domxref("HTMLElement")}}. متن داخلی این عناصر را می‌توان با فاصله به هم متصل کرد تا توضیح دسترس‌پذیر به دست آید.

هنگام خواندن، آرایه بازگردانده‌شده ایستا و فقط‌خواندنی است. هنگام نوشتن، آرایه تخصیص‌داده‌شده کپی می‌شود: تغییرات بعدی در آرایه بر مقدار خاصیت تأثیر نمی‌گذارد.

## توضیحات

این خاصیت یک جایگزین انعطاف‌پذیر برای استفاده از ویژگی [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) برای تنظیم توضیح دسترس‌پذیر است. برخلاف `aria-describedby`، عناصر تخصیص‌یافته به این خاصیت نیازی به داشتن ویژگی [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) ندارند.

این خاصیت منعکس‌کننده ویژگی [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby) عنصر است، اما فقط برای مقادیر `id` مرجع فهرست‌شده که با عناصر معتبر درون‌دامنه مطابقت دارند. اگر خاصیت تنظیم شود، ویژگی مربوطه پاک می‌شود. برای اطلاعات بیشتر در مورد مراجع عناصر بازتاب‌شده و دامنه، به [مراجع عناصر بازتاب‌شده](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references) در راهنمای _ویژگی‌های بازتاب‌شده_ مراجعه کنید.

## مثال‌ها

### دریافت توضیح دسترس‌پذیر

این مثال نشان می‌دهد که چگونه می‌توان از `ariaDescribedByElements` برای دریافت توضیح دسترس‌پذیر تعریف‌شده با استفاده از `aria-describedby` استفاده کرد.

#### HTML

HTML دو عنصر {{htmlelement("span")}} تعریف می‌کند و شناسه‌های آن‌ها را در ویژگی `aria-describedby` یک {{htmlelement("button")}} ارجاع می‌دهد.

```html
<button aria-describedby="trash-desc1 trash-desc2">Move to trash</button>
…
<span id="trash-desc1">Trash will be permanently removed after 30 days.</span>
<span id="trash-desc2">Or Else!</span>
```

```html hidden
<pre id="log"></pre>
```

#### CSS

در اینجا فقط عناصر `<span>` که حاوی متن دسترس‌پذیر ما هستند را پنهان می‌کنیم.

```css
span {
  display: none;
}
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

کد زیر ابتدا مقدار ویژگی `aria-describedby` را از {{domxref("Element.getAttribute()")}} (یک رشته که مقادیر `id` عناصر مرجع را فهرست می‌کند) ثبت می‌کند. سپس بررسی می‌کند که آیا `ariaDescribedByElements` پشتیبانی می‌شود یا خیر، و در صورت پشتیبانی، مقدار آن را ثبت می‌کند. در نهایت رشته دسترس‌پذیر را با پیمایش عناصر بازگردانده‌شده و الحاق متن داخلی آن‌ها برمی‌گرداند.

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

```js
const buttonElement = document.querySelector("button");
log(`aria-describedby: ${buttonElement.getAttribute("aria-describedby")}`);
// Feature test for ariaDescribedByElements
if ("ariaDescribedByElements" in Element.prototype) {
  // Get ariaDescribedByElements
  const buttonElements = buttonElement.ariaDescribedByElements;
  log(`ariaDescribedByElements: ${buttonElements}`);

  // Accessible description from the elements
  const text = buttonElements.map((e) => e.textContent.trim()).join(" ");
  log(`Accessible description: ${text.trim()}`);
} else {
  log("element.ariaDescribedByElements: not supported by browser");
}
```

#### نتیجه

لاگ زیر مراجع عناصر اصلی، عناصر مرتبط/بازگردانده‌شده، و توضیح دسترس‌پذیر را نشان می‌دهد.

{{EmbedLiveSample("Get the accessible description","100%","150px")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی [`aria-describedby`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-describedby)
- {{domxref("ElementInternals.ariaDescribedByElements")}}
- [مراجع عناصر بازتاب‌شده](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references) در راهنمای _بازتاب ویژگی_