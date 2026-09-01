---
title: "Element: ariaControlsElements property"
---

---
title: "Element: ariaControlsElements property"
short-title: ariaControlsElements
slug: Web/API/Element/ariaControlsElements
page-type: web-api-instance-property
browser-compat: api.Element.ariaControlsElements
---

{{APIRef("DOM")}}

ویژگی **`ariaControlsElements`** از رابط {{domxref("Element")}} یک آرایه شامل عناصری است که توسط عنصر مورد نظر کنترل می‌شوند. به عنوان مثال، این ویژگی ممکن است روی یک [combobox](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role) (جعبه ترکیبی) تنظیم شود تا عنصری که باز می‌شود را مشخص کند، یا روی یک [`scrollbar`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/scrollbar_role) (نوار پیمایش) برای نشان دادن شناسه عنصری که کنترل می‌کند، تنظیم شود.

مبحث [`aria-controls`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-controls) حاوی اطلاعات بیشتری در مورد نحوه استفاده از این صفت و ویژگی است.

## مقدار

یک آرایه از زیرکلاس‌های {{domxref("HTMLElement")}} که نشان‌دهنده عناصر کنترل‌شده توسط این عنصر است. هنگام خواندن، آرایه بازگشتی ایستا و فقط‌خواندنی است. هنگام نوشتن، آرایه تخصیص‌یافته کپی می‌شود: تغییرات بعدی در آرایه بر مقدار ویژگی تأثیر نمی‌گذارد.

## توضیحات

این ویژگی یک جایگزین انعطاف‌پذیر برای استفاده از صفت [`aria-controls`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-controls) جهت تنظیم عناصر کنترل‌شده است. بر خلاف `aria-controls`، عناصر تخصیص‌یافته به این ویژگی نیازی به داشتن صفت [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) ندارند. این ویژگی منعکس‌کننده صفت [`aria-controls`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-controls) در زمانی است که تعریف شده باشد، اما فقط برای مقادیر `id` مرجع فهرست‌شده‌ای که با عناصر معتبر درون‌حوزه مطابقت دارند. اگر ویژگی تنظیم شود، صفت مربوطه پاک می‌شود. برای اطلاعات بیشتر در مورد مراجع عناصر منعکس‌شده و حوزه، به [مراجع عناصر منعکس‌شده](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references) در راهنمای _Reflected attributes_ مراجعه کنید.

## مثال‌ها

### دریافت عناصر کنترل‌شده

این مثال نحوه استفاده از `ariaControlsElements` را برای دریافت عناصر کنترل‌شده‌ای که با استفاده از `aria-controls` تنظیم شده‌اند نشان می‌دهد.

#### HTML

HTML ابتدا یک عنصر {{htmlelement("button")}} و دو عنصر {{htmlelement("div")}} به نام‌های `panel1` و `panel2` که توسط آن کنترل می‌شوند را تعریف می‌کند. ارجاع به پنل‌های کنترل‌شده در صفت `aria-controls` دکمه فهرست شده است.

```html
<button id="toggleButton" aria-controls="panel1 panel2" aria-expanded="false">
  Show Details
</button>

<div class="panel" id="panel1" aria-hidden="true">
  <p>Panel1 opened/closed by button.</p>
</div>

<div class="panel" id="panel2" aria-hidden="true">
  <p>Panel2 opened/closed by button.</p>
</div>
```

```css
.panel {
  display: none; /* Initially hidden */
  border: 1px solid #cccccc;
  padding: 5px;
  margin-top: 5px;
}
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

کد ابتدا پنل‌ها را طوری تنظیم می‌کند که بر اساس صفت [`aria-expanded`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-expanded) دکمه باز یا پنهان شوند.

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

```js
const toggleButton = document.querySelector("#toggleButton");
const panel1 = document.querySelector("#panel1");
const panel2 = document.querySelector("#panel2");

toggleButton.addEventListener("click", () => {
  const isExpanded = toggleButton.getAttribute("aria-expanded") === "true";

  toggleButton.setAttribute("aria-expanded", !isExpanded);
  panel1.style.display = isExpanded ? "none" : "block";
  panel1.setAttribute("aria-hidden", isExpanded); // true when hidden, false when shown.

  panel2.style.display = isExpanded ? "none" : "block";
  panel2.setAttribute("aria-hidden", isExpanded); // true when hidden, false when shown.
});
```

سپس مثال مقدار صفت `aria-controls` را با استفاده از {{domxref("Element.getAttribute()")}} (یک رشته که مقادیر `id` عناصر ارجاع‌شده را فهرست می‌کند) دریافت می‌کند. سپس بررسی می‌کند که آیا ویژگی `ariaControlsElements` پشتیبانی می‌شود یا خیر، و در صورت پشتیبانی، مقدار آن را ثبت می‌کند. در نهایت، متن درونی هر یک از عناصر کنترل‌شده را بازگردانده و ثبت می‌کند.

```js
log(`aria-controls: ${toggleButton.getAttribute("aria-controls")}`);
// Feature test for ariaControlsElements
if ("ariaControlsElements" in Element.prototype) {
  // Get ariaControlsElements
  const controlledElements = toggleButton.ariaControlsElements;
  log(`ariaControlsElements: ${controlledElements}`);

  // List innerText for each of the ariaControlsElements
  controlledElements.forEach((controlled) => {
    log(` Controlled element text: ${controlled.textContent.trim()}`);
  });
} else {
  log("element.ariaControlsElements: not supported by browser");
}
```

#### نتیجه

روی دکمه زیر کلیک کنید تا پنل‌ها را نشان داده و پنهان کنید. لاگ، مراجع عناصر اصلی، عناصر مرتبط/بازگشتی، و متن درونی هر عنصر را نشان می‌دهد.

{{EmbedLiveSample("Get the controlled elements","100%","280px")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- صفت [`aria-controls`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-controls)
- {{domxref("ElementInternals.ariaControlsElements")}}
- [مراجع عناصر منعکس‌شده](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references) در راهنمای _Attribute reflection_