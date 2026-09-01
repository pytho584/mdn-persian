---
title: "HTMLSelectElement"
---

---
title: HTMLSelectElement
slug: Web/API/HTMLSelectElement
page-type: web-api-interface
browser-compat: api.HTMLSelectElement
---

{{APIRef("HTML DOM")}}

اینترفیس **`HTMLSelectElement`** نمایانگر یک عنصر HTML {{HTMLElement("select")}} است. این عناصر همچنین تمام ویژگی‌ها و روش‌های سایر عناصر HTML را از طریق اینترفیس {{domxref("HTMLElement")}} به اشتراک می‌گذارند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_این اینترفیس ویژگی‌های {{domxref("HTMLElement")}} و همچنین {{domxref("Element")}} و {{domxref("Node")}} را به ارث می‌برد._

- {{domxref("HTMLSelectElement.autocomplete")}}
  - : یک مقدار رشته‌ای که منعکس‌کننده ویژگی [`autocomplete`](/en-US/docs/Web/HTML/Reference/Elements/select#autocomplete) است؛ مشخص می‌کند که آیا مقدار کنترل می‌تواند به‌طور خودکار توسط مرورگر تکمیل شود.
- {{domxref("HTMLSelectElement.disabled")}}
  - : یک مقدار بولی که ویژگی [`disabled`](/en-US/docs/Web/HTML/Reference/Elements/select#disabled) HTML را منعکس می‌کند؛ مشخص می‌کند که آیا کنترل غیرفعال است. اگر غیرفعال باشد، کلیک‌ها را نمی‌پذیرد.
- {{domxref("HTMLSelectElement.form")}} {{ReadOnlyInline}}
  - : یک {{domxref("HTMLFormElement")}} که به فرم مرتبط با این عنصر اشاره می‌کند. اگر عنصر با هیچ عنصر {{HTMLElement("form")}} مرتبط نباشد، `null` برمی‌گرداند.
- {{domxref("HTMLSelectElement.labels")}} {{ReadOnlyInline}}
  - : یک {{domxref("NodeList")}} از عناصر {{HTMLElement("label")}} مرتبط با عنصر.
- {{domxref("HTMLSelectElement.length")}}
  - : یک `unsigned long`؛ تعداد عناصر {{HTMLElement("option")}} در این عنصر `select`.
- {{domxref("HTMLSelectElement.multiple")}}
  - : یک مقدار بولی که ویژگی [`multiple`](/en-US/docs/Web/HTML/Reference/Elements/select#multiple) HTML را منعکس می‌کند؛ مشخص می‌کند که آیا می‌توان چندین مورد را انتخاب کرد.
- {{domxref("HTMLSelectElement.name")}}
  - : یک رشته که ویژگی [`name`](/en-US/docs/Web/HTML/Reference/Elements/select#name) HTML را منعکس می‌کند و شامل نام این کنترل است که توسط سرورها و توابع جستجوی DOM استفاده می‌شود.
- {{domxref("HTMLSelectElement.options")}} {{ReadOnlyInline}}
  - : یک {{domxref("HTMLOptionsCollection")}} که مجموعه عناصر {{HTMLElement("option")}} ({{domxref("HTMLOptionElement")}}) موجود در این عنصر را نشان می‌دهد.
- {{domxref("HTMLSelectElement.required")}}
  - : یک مقدار بولی که ویژگی [`required`](/en-US/docs/Web/HTML/Reference/Elements/select#required) HTML را منعکس می‌کند؛ مشخص می‌کند که آیا کاربر ملزم است قبل از ارسال فرم یک مقدار انتخاب کند.
- {{domxref("HTMLSelectElement.selectedIndex")}}
  - : یک `long` که ایندکس نخستین عنصر {{HTMLElement("option")}} انتخاب‌شده را منعکس می‌کند. مقدار `-1` نشان می‌دهد هیچ عنصری انتخاب نشده است.
- {{domxref("HTMLSelectElement.selectedOptions")}} {{ReadOnlyInline}}
  - : یک {{domxref("HTMLCollection")}} که مجموعه عناصر {{HTMLElement("option")}} انتخاب‌شده را نشان می‌دهد.
- {{domxref("HTMLSelectElement.size")}}
  - : یک `long` که ویژگی [`size`](/en-US/docs/Web/HTML/Reference/Elements/select#size) HTML را منعکس می‌کند و شامل تعداد موارد قابل مشاهده در کنترل است. مقدار پیش‌فرض ۱ است، مگر اینکه `multiple` برابر `true` باشد که در آن صورت ۴ است.
- {{domxref("HTMLSelectElement.type")}} {{ReadOnlyInline}}
  - : یک رشته که نوع کنترل فرم را نشان می‌دهد. وقتی `multiple` برابر `true` است، `"select-multiple"` و در غیر این صورت `"select-one"` برمی‌گرداند.
- {{domxref("HTMLSelectElement.validationMessage")}} {{ReadOnlyInline}}
  - : یک رشته که یک پیام محلی‌سازی‌شده را توصیف می‌کند و محدودیت‌های اعتبارسنجی‌ای را که کنترل برآورده نمی‌کند (در صورت وجود) بیان می‌کند. اگر کنترل کاندیدای اعتبارسنجی محدودیت‌ها نباشد (`willValidate` برابر `false` باشد) یا محدودیت‌های خود را برآورده کند، این ویژگی رشته خالی است.
- {{domxref("HTMLSelectElement.validity")}} {{ReadOnlyInline}}
  - : یک {{domxref("ValidityState")}} که وضعیت اعتبارسنجی این کنترل را منعکس می‌کند.
- {{domxref("HTMLSelectElement.value")}}
  - : یک رشته که مقدار کنترل فرم را منعکس می‌کند. اگر اولین عنصر گزینه انتخاب‌شده وجود داشته باشد، مقدار ویژگی `value` آن را برمی‌گرداند؛ در غیر این صورت رشته خالی.
- {{domxref("HTMLSelectElement.willValidate")}} {{ReadOnlyInline}}
  - : یک مقدار بولی که نشان می‌دهد آیا کنترل کاندیدای اعتبارسنجی محدودیت‌ها است یا خیر. اگر هر شرطی آن را از اعتبارسنجی محدودیت‌ها بازدارد، مقدار آن `false` است.

## روش‌های نمونه

_این اینترفیس روش‌های {{domxref("HTMLElement")}} و همچنین {{domxref("Element")}} و {{domxref("Node")}} را به ارث می‌برد._

- {{domxref("HTMLSelectElement.add()")}}
  - : یک عنصر به مجموعه عناصر `option` این عنصر `select` اضافه می‌کند.
- {{domxref("HTMLSelectElement.checkValidity()")}}
  - : بررسی می‌کند که آیا عنصر محدودیتی دارد و آیا آن‌ها را برآورده می‌کند. اگر عنصر محدودیت‌های خود را نقض کند، مرورگر یک رویداد قابل‌لغو {{domxref("HTMLInputElement/invalid_event", "invalid")}} روی عنصر فعال می‌کند (و `false` برمی‌گرداند).
- {{domxref("HTMLSelectElement.item()")}}
  - : یک مورد از مجموعه گزینه‌های این عنصر {{HTMLElement("select")}} دریافت می‌کند. همچنین می‌توانید با مشخص کردن ایندکس در کروشه یا پرانتز، بدون فراخوانی صریح این روش، به مورد دسترسی پیدا کنید.
- {{domxref("HTMLSelectElement.namedItem()")}}
  - : موردی را با نام مشخص‌شده از مجموعه گزینه‌ها دریافت می‌کند. رشته نام می‌تواند با ویژگی `id` یا `name` یک گره گزینه مطابقت داشته باشد. همچنین می‌توانید با مشخص کردن نام در کروشه یا پرانتز، بدون فراخوانی صریح این روش، به مورد دسترسی پیدا کنید.
- {{domxref("HTMLSelectElement.remove()")}}
  - : عنصر را در ایندکس مشخص‌شده از مجموعه گزینه‌های این عنصر `select` حذف می‌کند.
- {{domxref("HTMLSelectElement.reportValidity()")}}
  - : این روش مشکلات محدودیت‌های عنصر (در صورت وجود) را به کاربر گزارش می‌دهد. اگر مشکلی وجود داشته باشد، یک رویداد قابل‌لغو {{domxref("HTMLInputElement/invalid_event", "invalid")}} روی عنصر فعال می‌کند و `false` برمی‌گرداند؛ اگر مشکلی نباشد، `true` برمی‌گرداند.
- {{domxref("HTMLSelectElement.setCustomValidity()")}}
  - : پیام اعتبارسنجی سفارشی عنصر انتخاب را به پیام مشخص‌شده تنظیم می‌کند. از رشته خالی استفاده کنید تا نشان دهید عنصر خطای اعتبارسنجی سفارشی _ندارد_.
- {{domxref("HTMLSelectElement.showPicker()", "showPicker()")}}
  - : انتخاب‌گر گزینه‌ها را نمایش می‌دهد.

## رویدادها

_این اینترفیس رویدادهای {{domxref("HTMLElement")}} و همچنین {{domxref("Element")}} و {{domxref("Node")}} را به ارث می‌برد._

به این رویدادها با استفاده از {{domxref("EventTarget/addEventListener", "addEventListener()")}} یا با انتساب یک شنونده رویداد به ویژگی `oneventname` این اینترفیس گوش دهید:

- رویداد {{domxref("HTMLElement/change_event", "change")}}
  - : زمانی فعال می‌شود که کاربر یک گزینه را انتخاب کند.
- رویداد {{domxref("Element/input_event", "input")}}
  - : زمانی فعال می‌شود که `value` یک عنصر {{HTMLElement("input")}}، {{HTMLElement("select")}} یا {{HTMLElement("textarea")}} تغییر کرده باشد.

## مثال

### دریافت اطلاعات درباره گزینه انتخاب‌شده

```js
/* assuming we have the following HTML
<select id='s'>
    <option>First</option>
    <option selected>Second</option>
    <option>Third</option>
</select>
*/

const select = document.getElementById("s");

// return the index of the selected option
console.log(select.selectedIndex); // 1

// return the value of the selected option
console.log(select.options[select.selectedIndex].value); // Second
```

روش بهتر برای پیگیری تغییرات انتخاب کاربر این است که رویداد {{domxref("HTMLElement/change_event", "change")}} را روی `<select>` زیر نظر بگیرید. این کار به شما می‌گوید چه زمانی مقدار تغییر می‌کند و می‌توانید هر چیزی را که لازم است به‌روزرسانی کنید. برای جزئیات، [مثال ارائه‌شده](/en-US/docs/Web/API/HTMLElement/change_event#select_element) را در مستندات رویداد `change` ببینید.

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- عنصر HTML {{HTMLElement("select")}} که این اینترفیس را پیاده‌سازی می‌کند.