---
title: "Element: ariaFlowToElements property"
---

---
title: "Element: ariaFlowToElements property"
short-title: ariaFlowToElements
slug: Web/API/Element/ariaFlowToElements
page-type: web-api-instance-property
browser-compat: api.Element.ariaFlowToElements
---

{{APIRef("DOM")}}

خاصیت **`ariaFlowToElements`** از رابط {{domxref("Element")}} آرایه‌ای شامل عنصر (یا عناصر) است که ترتیب خواندن جایگزینی برای محتوا فراهم می‌کنند و به صلاحدید کاربر، ترتیب خواندن پیش‌فرض عمومی را نادیده می‌گیرند. اگر فقط یک عنصر ارائه شده باشد، آن عنصر، عنصر بعدی در ترتیب خواندن است. اگر چند عنصر ارائه شده باشد، هر عنصر نشان‌دهنده یک مسیر ممکن است که باید برای انتخاب به کاربر ارائه شود.

مبحث [`aria-flowto`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-flowto) حاوی اطلاعات بیشتری درباره نحوه استفاده از ویژگی و خاصیت مذکور است.

## مقدار

یک آرایه از زیرکلاس‌های {{domxref("HTMLElement")}}.

هنگام خواندن، آرایه بازگردانده‌شده ایستا و فقط‌خواندنی است. هنگام نوشتن، آرایه تخصیص‌داده‌شده کپی می‌شود: تغییرات بعدی در آرایه، بر مقدار خاصیت تأثیری ندارند.

## توضیحات

این خاصیت جایگزینی انعطاف‌پذیر برای استفاده از ویژگی [`aria-flowto`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-flowto) به‌منظور تنظیم ترتیب خواندن جایگزین است. برخلاف `aria-flowto`، عناصری که به این خاصیت تخصیص داده می‌شوند لزومی ندارد ویژگی [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) داشته باشند.

این خاصیت، ویژگی [`aria-flowto`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-flowto) عنصر را در صورت تعریف‌شدن بازتاب می‌دهد، اما فقط برای مقادیر `id` مرجعِ فهرست‌شده‌ای که با عناصر معتبر در محدوده (in-scope) مطابقت دارند. اگر این خاصیت تنظیم شود، ویژگی متناظر پاک می‌شود. برای اطلاعات بیشتر درباره ارجاع‌های عنصرِ بازتاب‌یافته و محدوده، به [ارجاع‌های عنصر بازتاب‌یافته](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references) در راهنمای _Reflected attributes_ مراجعه کنید.

## مثال‌ها

### Get the flow-to element

این مثال جریان عادی را از میان سه عنصر `section1`، `section2` و `section3` به ترتیب نشان می‌دهد و نیز ترتیبی جایگزین که از `section1` به `section3` می‌پرد و دوباره به عقب برمی‌گردد. توجه داشته باشید که این مثال صرفاً جنبه نمایشی دارد، مگر اینکه ابزارهای دسترس‌پذیری در حال اجرا داشته باشید: ما در واقع این مسیر جایگزین را دنبال نمی‌کنیم.

#### HTML

HTML سه عنصر {{htmlelement("div")}} تعریف می‌کند که بخش‌ها را مشخص می‌کنند، با کلاس `"section"` و مقادیر `id` زیر: `section1`، `section2` و `section3`. هر بخش یک جریان عادی دارد که با ترتیب آن تعریف می‌شود و از `section1` شروع شده و به `section3` ختم می‌شود. یک جریان جایگزین در بخش‌های ۱ و ۳ با استفاده از ویژگی `aria-flowto` تعریف شده است.

```html hidden
<pre id="log"></pre>
```

```css hidden
#log {
  height: 200px;
  overflow: scroll;
  padding: 0.5rem;
  margin: 5px;
  border: 1px solid black;
}
```

```html
<div id="section1" class="section" aria-flowto="section3">
  <h2>Section 1</h2>
  <p>First section in normal flow. Section 3 is alternate flow.</p>
  <a href="#section2">Jump to Section 2 (normal flow)</a>
</div>

<div id="section2" class="section">
  <h2>Section 2</h2>
  <p>Second section in normal flow.</p>
  <a href="#section3">Jump to Section 3 (normal flow)</a>
</div>

<div id="section3" class="section" aria-flowto="section1">
  <h2>Section 3</h2>
  <p>
    Third section in normal flow (end of flow). Section 1 is alternate flow.
  </p>
</div>
```

#### JavaScript

کد ابتدا بررسی می‌کند که آیا `ariaFlowToElements` پشتیبانی می‌شود و اگر پشتیبانی شود، مقدار آن را ثبت می‌کند. سپس روی بخش‌ها تکرار می‌کند و `id` بخش، مقدار ویژگی `aria-flowto` و مقدار خاصیت `ariaFlowToElements` را ثبت می‌کند.

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

```js
// Feature test for ariaFlowToElements
if ("ariaFlowToElements" in Element.prototype) {
  const sections = document.querySelectorAll(".section");
  sections.forEach((sectionDivElement) => {
    log(`${sectionDivElement.id}`);
    log(` aria-flowto: ${sectionDivElement.getAttribute("aria-flowto")}`);
    log(" ariaFlowToElements:");
    // Get the ids of each of the elements in the array
    sectionDivElement.ariaFlowToElements?.forEach((elem) => {
      log(`  id: ${elem.id}`);
    });
  });
} else {
  log("element.ariaFlowToElements: not supported by browser");
}
```

#### نتیجه

گزارش زیر هر یک از بخش‌ها (شناسایی‌شده با `id`) و شناسه‌های عنصرِ flow-to متناظر را نشان می‌دهد که ممکن است توسط ابزارهای دسترس‌پذیری انتخاب شوند. در اینجا خاطرنشان می‌کنیم که ویژگی و خاصیت، عناصر flow-to یکسانی را شناسایی می‌کنند.

{{EmbedLiveSample("Get the flow-to element","100%","570px")}}

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- ویژگی [`aria-flowto`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-flowto)
- {{domxref("ElementInternals.ariaFlowToElements")}}
- [ارجاع‌های عنصر بازتاب‌یافته](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references) در راهنمای _Attribute reflection_