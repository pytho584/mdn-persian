```markdown
---
title: "Element: خاصیت ariaActiveDescendantElement"
short-title: ariaActiveDescendantElement
slug: Web/API/Element/ariaActiveDescendantElement
page-type: web-api-instance-property
browser-compat: api.Element.ariaActiveDescendantElement
---

{{APIRef("DOM")}}

خاصیت **`ariaActiveDescendantElement`** از رابط {{domxref("Element")}}، عنصر فعال فعلی را هنگامی که تمرکز (focus) روی یک ویجت [`composite`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/composite_role)، [`combobox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/combobox_role)، [`textbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/textbox_role)، [`group`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/group_role) یا [`application`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/application_role) است، نمایش می‌دهد.

مبحث [`aria-activedescendant`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-activedescendant) حاوی اطلاعات بیشتری در مورد نحوه استفاده از صفت (attribute) و خاصیت (property) است.

## مقدار

یک زیرکلاس از {{domxref("HTMLElement")}} که نمایانگر عنصر descendant فعال است، یا `null` اگر هیچ descendant فعالی وجود نداشته باشد.

## توضیحات

این خاصیت یک جایگزین انعطاف‌پذیر برای استفاده از صفت [`aria-activedescendant`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-activedescendant) است. برخلاف `aria-activedescendant`، عنصری که به این خاصیت اختصاص داده می‌شود نیازی به داشتن صفت [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) ندارد.

این خاصیت صفت [`aria-activedescendant`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-errormessage) عنصر را هنگامی که تعریف شده است، منعکس می‌کند، اما فقط برای مقادیر `id` ارجاع که با عناصر معتبر درون-دامنه (in-scope) مطابقت دارند. اگر خاصیت تنظیم شود، صفت مربوطه پاک می‌شود. برای اطلاعات بیشتر در مورد ارجاعات عناصر منعکس‌شده و دامنه، به [ارجاعات عناصر منعکس‌شده](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references) در راهنمای _صفت‌های منعکس‌شده_ مراجعه کنید.

## مثال‌ها

### دریافت descendant فعال

این مثال نشان می‌دهد که چگونه می‌توان از `ariaActiveDescendantElement` برای دریافت descendant فعال فعلی استفاده کرد.

#### HTML

HTML یک جعبه فهرست (listbox) برای انتخاب انواع مختلف خیابان‌ها تعریف می‌کند که شامل یک عنصر {{htmlelement("div")}} با [نقش `listbox`](/en-US/docs/Web/Accessibility/ARIA/Reference/Roles/listbox_role) و آیتم‌های `<div>` تو در تو برای هر یک از گزینه‌ها است. descendant فعال در ابتدا با استفاده از `aria-activedescendant` به عنصری با `id` برابر `avenue` تنظیم می‌شود.

```html
<div id="streetType" role="listbox" aria-activedescendant="avenue">
  <div>Street</div>
  <div id="avenue">Avenue</div>
  <div>Lane</div>
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

کد زیر ابتدا بررسی می‌کند که آیا `ariaActiveDescendantElement` پشتیبانی می‌شود یا خیر. اگر خاصیت پشتیبانی شود، کد سپس مقدار `aria-activedescendant` (یعنی `id` عنصر ارجاع‌شده) را با استفاده از {{domxref("Element.getAttribute()")}}، عنصر خاصیت، و محتوای متنی آن عنصر را ثبت می‌کند.

```js hidden
const logElement = document.querySelector("#log");
function log(text) {
  logElement.innerText = `${logElement.innerText}${text}\n`;
  logElement.scrollTop = logElement.scrollHeight;
}
```

```js
// آزمایش ویژگی برای ariaActiveDescendantElement
if ("ariaActiveDescendantElement" in Element.prototype) {
  log(`getAttribute(): ${streetType.getAttribute("aria-activedescendant")}`);
  log(`ariaActiveDescendantElement: ${streetType.ariaActiveDescendantElement}`);
  log(`text: ${streetType.ariaActiveDescendantElement?.textContent.trim()}`);
} else {
  log("ariaActiveDescendantElement توسط مرورگر پشتیبانی نمی‌شود");
}
```

#### نتیجه

لاگ زیر خروجی کد بالا را نشان می‌دهد. مقدار بازگشتی از خاصیت `aria-activedescendant` باید `"avenue"` باشد، عنصر مرتبط باید یک عنصر `HTMLDivElement` باشد، و متن داخل آن عنصر باید `Avenue` باشد.

{{EmbedLiveSample("Get the active descendant","100%","190px")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- صفت [`aria-activedescendant`](/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-activedescendant)
- {{domxref("ElementInternals.ariaActiveDescendantElement")}}
- [ارجاعات عناصر منعکس‌شده](/en-US/docs/Web/API/Document_Object_Model/Reflected_attributes#reflected_element_references) در راهنمای _انعکاس صفت (Attribute reflection)_
```