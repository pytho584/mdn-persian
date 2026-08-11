---
title: "<output> HTML output element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/output"
translated_by: "n8n + AI"
---

المنت `<output>` [HTML](/en-US/docs/Web/HTML) یک المنت ظرف است که سایت یا اپ می‌تواند نتیجهٔ یک محاسبه یا خروجی یک اقدام کاربر را داخل آن قرار دهد.

## Attributes

این المنت شامل [attributes سراسری](/en-US/docs/Web/HTML/Reference/Global_attributes) است.

- [`for`](/en-US/docs/Web/HTML/Reference/Attributes/for)
  - : یک فهرست جداشده با فاصله از `id`های سایر المنت‌ها که نشان می‌دهد آن المنت‌ها مقادیر ورودی به محاسبه داده‌اند (یا به نحوی دیگر بر آن تأثیر گذاشته‌اند).
- [`form`](/en-US/docs/Web/HTML/Reference/Attributes/form)
  - : المنت `<form>` که خروجی با آن مرتبط می‌شود (_form owner_). مقدار این attribute باید `id` یک `<form>` در همان سند باشد. (اگر این attribute تنظیم نشود، `<output>` با المنت `<form>` والد خود، در صورت وجود، مرتبط می‌شود.)

    این attribute به شما اجازه می‌دهد المنت‌های `<output>` را به `<form>`هایی در هر جای سند مرتبط کنید، نه فقط داخل یک `<form>`. همچنین می‌تواند ارتباط با یک `<form>` والد را لغو کند. نام و محتوای المنت `<output>` هنگام ارسال فرم ارسال نمی‌شوند.

- `name`
  - : نام المنت. در API {{domxref("HTMLFormElement.elements", "form.elements")}} استفاده می‌شود.

مقدار، نام و محتویات `<output>` هنگام ارسال فرم ارسال **نمی‌شوند**.

## دسترس‌پذیری

بسیاری از مرورگرها این المنت را به‌صورت یک منطقهٔ [`aria-live`](/en-US/docs/Web/Accessibility/ARIA/Guides/Live_regions) پیاده‌سازی می‌کنند. در نتیجه، فناوری کمکی نتایج تعاملات UI را که داخل آن درج می‌شود اعلام می‌کند، بدون اینکه نیاز باشد فوکوس از کنترل‌هایی که آن نتایج را تولید می‌کنند جابه‌جا شود.

## مثال‌ها

در مثال زیر، فرم یک اسلایدر دارد که مقدار آن می‌تواند بین `0` و `100` باشد، و یک المنت {{HTMLElement("input")}} که می‌توانید عدد دوم را در آن وارد کنید. این دو عدد با هم جمع می‌شوند و نتیجه هر بار که مقدار هر یک از کنترل‌ها تغییر کند در المنت `<output>` نمایش داده می‌شود.

```html
<form id="example-form">
  <input type="range" id="b" name="b" value="50" /> +
  <input type="number" id="a" name="a" value="10" /> =
  <output name="result" for="a b">60</output>
</form>
```

```js
const form = document.getElementById("example-form");
const a = form.elements["a"];
const b = form.elements["b"];
const result = form.elements["result"];

function updateResult() {
  const aValue = a.valueAsNumber;
  const bValue = b.valueAsNumber;
  result.value = aValue + bValue;
}

form.addEventListener("input", updateResult);

updateResult();
```

| دسته‌بندی محتوا | [Flow content](/en-US/docs/Web/HTML/Guides/Content_categories#flow_content)، [phrasing content](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content)، [listed](/en-US/docs/Web/HTML/Guides/Content_categories#listed)، [labelable](/en-US/docs/Web/HTML/Guides/Content_categories#labelable)، [resettable](/en-US/docs/Web/HTML/Guides/Content_categories#resettable)، [form-associated element](/en-US/docs/Web/HTML/Guides/Content_categories#form-associated_content)، palpable content |
| محتوای مجاز | [Phrasing content](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) |
| حذف تگ | هیچ‌کدام؛ تگ شروع و پایان هر دو اجباری هستند. |
| والدهای مجاز | هر عنصری که [phrasing content](/en-US/docs/Web/HTML/Guides/Content_categories#phrasing_content) را می‌پذیرد. |
| نقش ARIA ضمنی | [`status`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/status_role) |
| نقش‌های ARIA مجاز | هر نقشی |
| رابط DOM | `HTMLOutputElement` |

## مشخصات

## سازگاری مرورگرها