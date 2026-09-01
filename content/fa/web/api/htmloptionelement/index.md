---
title: "HTMLOptionElement"
slug: Web/API/HTMLOptionElement
page-type: web-api-interface
browser-compat: api.HTMLOptionElement
---

{{APIRef("HTML DOM")}}

رابط **`HTMLOptionElement`** عناصر {{HTMLElement("option")}} را نمایش می‌دهد و تمام ویژگی‌ها و متدهای رابط {{domxref("HTMLElement")}} را به ارث می‌برد.

{{InheritanceDiagram}}

## سازنده

- {{domxref("HTMLOptionElement.Option", "Option()")}}
  - : یک شیء جدید `HTMLOptionElement` می‌سازد. این سازنده چهار پارامتر دارد: متنی که نمایش داده می‌شود (`text`)، مقدار مرتبط (`value`)، مقدار `defaultSelected` و مقدار `selected`. سه پارامتر آخر اختیاری هستند.

## ویژگی‌های نمونه

_ویژگی‌ها را از والد خود، {{domxref("HTMLElement")}}، به ارث می‌برد._

- {{domxref("HTMLOptionElement.defaultSelected")}}
  - : مقدار آن `true` یا `false` است و مقدار اولیهٔ ویژگی HTML [`selected`](/en-US/docs/Web/HTML/Reference/Elements/option#selected) را نشان می‌دهد؛ یعنی مشخص می‌کند که گزینه به‌صورت پیش‌فرض انتخاب شده است یا نه.
- {{domxref("HTMLOptionElement.disabled")}}
  - : مقدار آن `true` یا `false` است و بیانگر مقدار ویژگی HTML [`disabled`](/en-US/docs/Web/HTML/Reference/Elements/option#disabled) است؛ این ویژگی نشان می‌دهد که گزینه برای انتخاب در دسترس نیست.
- {{domxref("HTMLOptionElement.form")}} {{ReadOnlyInline}}
  - : یک {{domxref("HTMLFormElement")}} که همان مقدار `form` عنصر {{HTMLElement("select")}} متناظر را نمایش می‌دهد، در صورتی که گزینه از نسل یک عنصر {{HTMLElement("select")}} باشد؛ در غیر این صورت مقدار `null` را برمی‌گرداند.
- {{domxref("HTMLOptionElement.index")}} {{ReadOnlyInline}}
  - : یک `long` که جایگاه گزینه را در فهرست گزینه‌هایی که به آن تعلق دارد، به ترتیب درخت (tree-order) نشان می‌دهد. اگر گزینه بخشی از فهرست گزینه‌ها نباشد، مثلاً وقتی بخشی از عنصر {{HTMLElement("datalist")}} باشد، مقدار آن `0` است.
- {{domxref("HTMLOptionElement.label")}}
  - : یک رشته (string) که منعکس‌کنندهٔ مقدار ویژگی HTML [`label`](/en-US/docs/Web/HTML/Reference/Elements/option#label) است و برچسبی برای گزینه فراهم می‌کند. اگر این ویژگی به‌طور خاص تنظیم نشده باشد، خواندن آن محتوای {{domxref("HTMLOptionElement.text", "text")}} عنصر را برمی‌گرداند.
- {{domxref("HTMLOptionElement.selected")}}
  - : مقدار آن `true` یا `false` است و نشان می‌دهد که آیا گزینه در حال حاضر انتخاب شده است.
- {{domxref("HTMLOptionElement.text")}}
  - : یک رشته که محتوای متنی عنصر را در بر می‌گیرد.
- {{domxref("HTMLOptionElement.value")}}
  - : یک رشته که در صورت وجود، مقدار ویژگی HTML [`value`](/en-US/docs/Web/HTML/Reference/Elements/option#value) را منعکس می‌کند؛ در غیر این صورت مقدار ویژگی {{domxref("Node.textContent")}} را منعکس می‌کند.

## روش‌های نمونه

_هیچ روش خاصی را پیاده‌سازی نمی‌کند، اما روش‌ها را از والد خود، {{domxref("HTMLElement")}}، به ارث می‌برد._

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{HTMLElement("option")}}
- {{HTMLElement("select")}}
- {{HTMLElement("datalist")}}
- {{HTMLElement("optgroup")}}
- {{domxref("HTMLOptionsCollection")}}
- {{domxref("HTMLSelectElement")}}
- {{domxref("HTMLOptGroupElement")}}
- {{domxref("HTMLElement")}}
- {{domxref("HTMLCollection")}}