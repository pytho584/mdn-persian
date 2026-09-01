---
title: HTMLButtonElement
slug: Web/API/HTMLButtonElement
page-type: web-api-interface
browser-compat: api.HTMLButtonElement
---

{{APIRef("HTML DOM")}}

رابط (interface) **`HTMLButtonElement`** ویژگی‌ها و روش‌هایی (فراتر از رابط معمول {{domxref("HTMLElement")}} که به‌طور ارث‌بری در دسترس آن است) برای دستکاری عناصر {{HTMLElement("button")}} فراهم می‌کند.

{{InheritanceDiagram}}

## ویژگی‌های نمونه (Instance properties)

_ویژگی‌های والد خود، {{domxref("HTMLElement")}} را به ارث می‌برد._

- {{domxref("HTMLButtonElement.command")}}
  - : یک مقدار رشتهای که عملیاتی را که باید روی عنصری تحت کنترل این دکمه انجام شود، مشخص می‌کند.
- {{domxref("HTMLButtonElement.commandForElement")}}
  - : ارجاعی به یک {{domxref("Element")}} موجود که دکمه آن را کنترل می‌کند.
- {{domxref("HTMLButtonElement.disabled")}}
  - : یک مقدار بولی (Boolean) که نشان می‌دهد آیا کنترل غیرفعال است یا خیر؛ یعنی هیچ کلیکی را نمی‌پذیرد.
- {{domxref("HTMLButtonElement.form")}} {{ReadOnlyInline}}
  - : یک {{domxref("HTMLFormElement")}} که فرم مرتبط با این دکمه را منعکس می‌کند. اگر دکمه از نوادگان یک عنصر فرم باشد، این ویژگی ارجاعی به `HTMLFormElement` مرتبط با آن فرم است. اگر دکمه از نوادگان یک عنصر فرم نباشد، این ویژگی می‌تواند ارجاعی به هر عنصر `HTMLFormElement` در همان سند باشد که با آن مرتبط است، یا در صورت عدم تطابق، مقدار `null` باشد.
- {{domxref("HTMLButtonElement.formAction")}}
  - : یک رشته که URI منبعی را نشان می‌دهد که اطلاعات ارسال‌شده توسط دکمه را پردازش می‌کند. در صورت مشخص شدن، این ویژگی ویژگی [`action`](/en-US/docs/Web/HTML/Reference/Elements/form#action) عنصر {{HTMLElement("form")}} که مالک این عنصر است را نادیده می‌گیرد.
- {{domxref("HTMLButtonElement.formEnctype")}}
  - : یک رشته که نوع محتوای مورد استفاده برای ارسال فرم به سرور را نشان می‌دهد. در صورت مشخص شدن، این ویژگی ویژگی [`enctype`](/en-US/docs/Web/HTML/Reference/Elements/form#enctype) عنصر {{HTMLElement("form")}} که مالک این عنصر است را نادیده می‌گیرد.
- {{domxref("HTMLButtonElement.formMethod")}}
  - : یک رشته که روش HTTP مورد استفاده مرورگر برای ارسال فرم را نشان می‌دهد. در صورت مشخص شدن، این ویژگی ویژگی [`method`](/en-US/docs/Web/HTML/Reference/Elements/form#method) عنصر {{HTMLElement("form")}} که مالک این عنصر است را نادیده می‌گیرد.
- {{domxref("HTMLButtonElement.formNoValidate")}}
  - : یک مقدار بولی که نشان می‌دهد هنگام ارسال فرم نباید اعتبارسنجی شود. در صورت مشخص شدن، این ویژگی ویژگی [`novalidate`](/en-US/docs/Web/HTML/Reference/Elements/form#novalidate) عنصر {{HTMLElement("form")}} که مالک این عنصر است را نادیده می‌گیرد.
- {{domxref("HTMLButtonElement.formTarget")}}
  - : یک رشته که نام یا کلیدواژه‌ای را نشان می‌دهد که محل نمایش پاسخ دریافت‌شده پس از ارسال فرم را مشخص می‌کند. در صورت مشخص شدن، این ویژگی ویژگی [`target`](/en-US/docs/Web/HTML/Reference/Elements/form#target) عنصر {{HTMLElement("form")}} که مالک این عنصر است را نادیده می‌گیرد.
- {{domxref("HTMLButtonElement.interestForElement")}} {{experimental_inline}} {{non-standard_inline}}
  - : عنصر هدف یک فراخوان‌کننده علاقه (interest invoker) را در مواردی که عنصر {{htmlelement("button")}} مرتبط به عنوان یک [فراخوان‌کننده علاقه](/en-US/docs/Web/API/Popover_API/Using_interest_invokers#creating_an_interest_invoker) مشخص شده است، دریافت یا تنظیم می‌کند.
- {{domxref("HTMLButtonElement.labels")}} {{ReadOnlyInline}}
  - : یک {{domxref("NodeList")}} که فهرستی از عناصر {{HTMLElement("label")}} را نشان می‌دهد که برچسب‌های این دکمه هستند.
- {{domxref("HTMLButtonElement.name")}}
  - : یک رشته که نام شیء را هنگام ارسال با یک فرم نشان می‌دهد. در صورت مشخص شدن، نباید رشته خالی باشد.
- {{domxref("HTMLButtonElement.popoverTargetAction")}}
  - : عملیاتی که باید روی یک عنصر پاپ‌اور تحت کنترل یک دکمه کنترلی انجام شود (`"hide"`، `"show"` یا `"toggle"`) را دریافت و تنظیم می‌کند. این ویژگی مقدار ویژگی HTML [`popovertargetaction`](/en-US/docs/Web/HTML/Reference/Elements/button#popovertargetaction) را منعکس می‌کند.
- {{domxref("HTMLButtonElement.popoverTargetElement")}}
  - : عنصر پاپ‌اوری را که باید از طریق یک دکمه کنترل شود، دریافت و تنظیم می‌کند. معادل جاوااسکریپتی ویژگی HTML [`popovertarget`](/en-US/docs/Web/HTML/Reference/Elements/button#popovertarget).
- {{domxref("HTMLButtonElement.type")}}
  - : یک رشته که رفتار دکمه را نشان می‌دهد. این یک ویژگی شمارشی با مقادیر ممکن زیر است:
    - `submit`: دکمه فرم را ارسال می‌کند. این مقدار پیش‌فرض در صورت عدم مشخص شدن ویژگی یا تغییر پویای آن به مقدار خالی یا نامعتبر است.
    - `reset`: دکمه فرم را بازنشانی می‌کند.
    - `button`: دکمه هیچ کاری انجام نمی‌دهد.
    - `menu`: دکمه یک منو را نمایش می‌دهد. {{experimental_inline}}

- {{domxref("HTMLButtonElement.willValidate")}} {{ReadOnlyInline}}
  - : یک مقدار بولی که نشان می‌دهد آیا دکمه کاندیدای اعتبارسنجی محدودیت (constraint validation) است یا خیر. اگر هر شرطی آن را از اعتبارسنجی محدودیت منع کند، `false` است؛ از جمله: ویژگی `type` آن `reset` یا `button` باشد؛ دارای یک جد {{HTMLElement("datalist")}} باشد؛ یا ویژگی `disabled` روی `true` تنظیم شده باشد.
- {{domxref("HTMLButtonElement.validationMessage")}} {{ReadOnlyInline}}
  - : یک رشته که پیام بومی‌سازی‌شده‌ای را نشان می‌دهد که محدودیت‌های اعتبارسنجی را که کنترل برآورده نمی‌کند (در صورت وجود) توصیف می‌کند. اگر کنترل کاندیدای اعتبارسنجی محدودیت نباشد (`willValidate` برابر `false` است) یا محدودیت‌های خود را برآورده کند، این ویژگی رشته خالی است.
- {{domxref("HTMLButtonElement.validity")}} {{ReadOnlyInline}}
  - : یک {{domxref("ValidityState")}} که حالت‌های اعتبارسنجی این دکمه را نشان می‌دهد.
- {{domxref("HTMLButtonElement.value")}}
  - : یک رشته که مقدار فعلی کنترل فرم دکمه را نشان می‌دهد.

## روش‌های نمونه (Instance methods)

_روش‌ها را از والد خود، {{domxref("HTMLElement")}} به ارث می‌برد._

- {{domxref("HTMLButtonElement.checkValidity()")}}
  - : اگر مقدار عنصر هیچ مشکل اعتبارسنجی نداشته باشد، `true` را برمی‌گرداند؛ در غیر این صورت `false` را برمی‌گرداند.
- {{domxref("HTMLButtonElement.reportValidity()")}}
  - : همان عمل `checkValidity()` را انجام می‌دهد، اما در صورت لغو نشدن رویداد `invalid`، نتیجه را نیز به کاربر گزارش می‌دهد.
- {{domxref("HTMLButtonElement.setCustomValidity()")}}
  - : پیام اعتبارسنجی سفارشی را برای عنصر تنظیم می‌کند. از رشته خالی استفاده کنید تا نشان دهید عنصر خطای اعتبارسنجی سفارشی _ندارد_.

## مشخصات (Specifications)

{{Specifications}}

## سازگاری مرورگر (Browser compatibility)

{{Compat}}

## همچنین ببینید (See also)

- عنصر HTML که این رابط را پیاده‌سازی می‌کند: {{HTMLElement("button")}}