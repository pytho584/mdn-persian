---
title: "Element: ariaErrorMessageElements property"
short-title: ariaErrorMessageElements
slug: Web/API/Element/ariaErrorMessageElements
page-type: web-api-instance-property
browser-compat: api.Element.ariaErrorMessageElements
---

{{APIRef("DOM")}}

ویژگی **`ariaErrorMessageElements`** در رابط {{domxref("Element")}} آرایه‌ای است شامل عنصر (یا عناصر) که برای عنصرِ اعمال‌شده، پیام خطا فراهم می‌کنند.

مبحث [`aria-errormessage`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-errormessage) اطلاعات بیشتری درباره نحوه استفاده از این صفت و ویژگی ارائه می‌دهد.

## مقدار

آرایه‌ای از زیرکلاس‌های {{domxref("HTMLElement")}}. متن داخلی این عناصر را می‌توان با فاصله (اسپیس) به هم پیوست تا پیام خطا به دست آید.

هنگام خواندن، آرایه بازگشت‌داده‌شده ایستا و فقط‌خواندنی است. هنگام نوشتن، آرایه تخصیص‌یافته کپی می‌شود: تغییرات بعدی در آرایه بر مقدار ویژگی تأثیر نمی‌گذارد.

## توضیحات

این ویژگی جایگزینی انعطاف‌پذیر برای استفاده از صفت [`aria-errormessage`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-errormessage) به منظور تنظیم پیام خطای یک عنصر است. برخلاف `aria-errormessage`، عناصر تخصیص‌یافته به این ویژگی لزومی به داشتن صفت [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) ندارند.

این ویژگی صفت `aria-errormessage` عنصر را بازتاب می‌کند؛ اما فقط برای مقادیر مرجع `id` فهرست‌شده که با عناصر معتبرِ در محدوده مطابقت دارند. اگر این ویژگی تنظیم شود، صفت متناظر پاک می‌شود. برای اطلاعات بیشتر درباره ارجاع‌های بازتاب‌شده عناصر و محدوده، بخش [ارجاع‌های بازتاب‌شده عناصر](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references) را در راهنمای _بازتاب صفت‌ها_ ببینید.

## مثال‌ها

### ورودی ایمیل با پیام خطا

این مثال نشان می‌دهد که چگونه از `aria-errormessage` برای تنظیم پیام خطای گزارش ورود یک آدرس ایمیل نامعتبر استفاده کنیم و چطور می‌توانیم پیام را با استفاده از `ariaErrorMessageElements` دریافت و تنظیم کنیم.

#### HTML

ابتدا یک ورودی ایمیل HTML تعریف می‌کنیم و صفت `aria-errormessage` آن را به عنصری با `id` برابر با `err1` ارجاع می‌دهیم. سپس یک عنصر `<span>` با همین شناسه تعریف می‌کنیم که حاوی پیام خطاست.

```html
<p>
  <label for="email">Email address:</label>
  <input type="email" name="email" id="email" aria-errormessage="err1" />
  <span id="err1" class="errormessage">Error: Enter a valid email address</span>
</p>
```

#### CSS

برای پنهان‌سازی پیش‌فرض پیام خطا، استایل‌هایی ایجاد می‌کنیم؛ اما وقتی `aria-invalid` روی عنصر تنظیم شود، پیام خطا نمایان شده و به‌صورت خطا استایل می‌گیرد.

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

#### JavaScript

سپس ورودی را بررسی کرده و {{domxref("Element/ariaInvalid", "ariaInvalid")}} را بر اساس نقض محدودیت [`typeMismatch`](/en-US/docs/Web/API/ValidityState/typeMismatch) روی `true` یا `false` تنظیم می‌کنیم. به نوبه خود، `ariaInvalid` در صفت `aria-invalid` بازتاب می‌شود که بسته به نیاز، خطا را پنهان یا نمایش می‌دهد.

```js
const email = document.querySelector("#email");

email.addEventListener("input", (event) => {
  if (email.validity.typeMismatch) {
    email.ariaInvalid = true;
  } else {
    email.ariaInvalid = false;
  }
});
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

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

سپس مقدار صفت `aria-errormessage`، `ariaErrorMessageElements` و متن داخلی `ariaErrorMessageElements` را ثبت (log) می‌کنیم.

```js
log(`aria-errormessage: ${email.getAttribute("aria-errormessage")}`);
// Feature test for ariaErrorMessageElements
if ("ariaErrorMessageElements" in Element.prototype) {
  // Get ariaErrorMessageElements
  const propElements = email.ariaErrorMessageElements;
  log(`ariaErrorMessageElements: ${propElements}`);

  // Accessible text from element inner text
  const text = propElements.map((e) => e.textContent.trim()).join(" ");
  log(`Error message details: ${text}`);
} else {
  log("element.ariaErrorMessageElements: not supported by browser");
}
```

#### نتیجه

هنگام وارد کردن آدرس ایمیل، متن خطا تا زمانی که آدرس ایمیل معتبر باشد نمایش داده می‌شود. توجه کنید که گزارش، ارجاع پیام خطای خوانده‌شده از صفت، عنصر بهدست‌آمده از `ariaErrorMessageElements`، و متن داخلی عنصر را نشان می‌دهد که همان پیام خطاست.

{{EmbedLiveSample("Email input with error message","100%","180px")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- صفت [`aria-errormessage`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-errormessage)
- {{domxref("ElementInternals.ariaErrorMessageElements")}}
- [ارجاع‌های بازتاب‌شده عناصر](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references) در راهنمای _بازتاب صفت‌ها_.