---
title: DocumentFragment
slug: Web/API/DocumentFragment
page-type: web-api-interface
browser-compat: api.DocumentFragment
---

{{ APIRef("DOM") }}

رابط **`DocumentFragment`** یک شیء سند حداقلی و بدون والد را نمایش می‌دهد.

این رابط به عنوان یک نسخه سبک‌وزن از {{domxref("Document")}} استفاده می‌شود که بخشی از ساختار یک سند را شامل گره‌ها (nodes) ذخیره می‌کند، درست مانند یک سند استاندارد. تفاوت اصلی در این است که قطعه سند (document fragment) بخشی از ساختار درخت فعال سند نیست. تغییراتی که در قطعه ایجاد می‌شود بر سند تأثیر نمی‌گذارد.

{{InheritanceDiagram}}

## سازنده

- {{ domxref("DocumentFragment.DocumentFragment()", "DocumentFragment()") }}
  - : یک شیء `DocumentFragment` جدید ایجاد و بازمی‌گرداند.

## ویژگی‌های نمونه

_این رابط ویژگی خاصی ندارد، اما ویژگی‌های والد خود، {{domxref("Node")}} را به ارث می‌برد._

- {{ domxref("DocumentFragment.childElementCount") }} {{ReadOnlyInline}}
  - : تعداد {{domxref("Element","عناصر")}} فرزند `DocumentFragment` را برمی‌گرداند.
- {{ domxref("DocumentFragment.children") }} {{ReadOnlyInline}}
  - : یک {{domxref("HTMLCollection")}} زنده شامل تمام اشیاء از نوع {{domxref("Element")}} که فرزندان شیء `DocumentFragment` هستند را برمی‌گرداند.
- {{ domxref("DocumentFragment.firstElementChild") }} {{ReadOnlyInline}}
  - : اولین {{domxref("Element")}} فرزند شیء `DocumentFragment` را برمی‌گرداند، یا اگر وجود نداشته باشد `null` را برمی‌گرداند.
- {{ domxref("DocumentFragment.lastElementChild") }} {{ReadOnlyInline}}
  - : آخرین {{domxref("Element")}} فرزند شیء `DocumentFragment` را برمی‌گرداند، یا اگر وجود نداشته باشد `null` را برمی‌گرداند.

## روش‌های نمونه

_این رابط روش‌های والد خود، {{domxref("Node")}} را به ارث می‌برد._

- {{DOMxRef("DocumentFragment.append()")}}
  - : مجموعه‌ای از اشیاء {{domxref("Node")}} یا رشته‌ها را بعد از آخرین فرزند قطعه سند درج می‌کند.
- {{DOMxRef("DocumentFragment.prepend()")}}
  - : مجموعه‌ای از اشیاء {{domxref("Node")}} یا رشته‌ها را قبل از اولین فرزند قطعه سند درج می‌کند.
- {{domxref("DocumentFragment.querySelector()")}}
  - : اولین گره {{domxref("Element")}} را درون `DocumentFragment`، به ترتیب سند، که با انتخاب‌گرهای مشخص شده مطابقت دارد، برمی‌گرداند.
- {{domxref("DocumentFragment.querySelectorAll()")}}
  - : یک {{domxref("NodeList")}} از تمام گره‌های {{domxref("Element")}} درون `DocumentFragment` که با انتخاب‌گرهای مشخص شده مطابقت دارند، برمی‌گرداند.
- {{DOMxRef("DocumentFragment.moveBefore()")}}
  - : یک {{domxref("Node")}} داده شده را درون `DocumentFragment` فراخواننده به عنوان یک فرزند مستقیم، قبل از یک گره مرجع معین، بدون حذف و سپس درج کردن گره، جابه‌جا می‌کند.
- {{DOMxRef("DocumentFragment.replaceChildren()")}}
  - : فرزندان موجود یک `DocumentFragment` را با مجموعه جدید مشخصی از فرزندان جایگزین می‌کند.
- {{domxref("DocumentFragment.getElementById()")}}
  - : اولین گره {{domxref("Element")}} را درون `DocumentFragment`، به ترتیب سند، که با شناسه مشخص شده مطابقت دارد، برمی‌گرداند. از نظر عملکردی معادل {{domxref("Document.getElementById()")}} است.

## نکات استفاده

یک کاربرد رایج `DocumentFragment` این است که یک نمونه از آن ایجاد کنید، یک زیردرخت DOM درون آن بسازید، سپس قطعه را با استفاده از روش‌های رابط {{domxref("Node")}} مانند {{domxref("Node.appendChild", "appendChild()")}}، {{domxref("Element.append", "append()")}} یا {{domxref("Node.insertBefore", "insertBefore()")}} به DOM اضافه یا درون آن درج کنید. با این کار، گره‌های قطعه به DOM منتقل می‌شوند و یک `DocumentFragment` خالی باقی می‌ماند.

این رابط همچنین در کامپوننت‌های وب (Web components) بسیار مفید است: عناصر {{HTMLElement("template")}} یک `DocumentFragment` را در ویژگی {{domxref("HTMLTemplateElement.content")}} خود دارند.

یک `DocumentFragment` خالی را می‌توان با استفاده از روش {{domxref("document.createDocumentFragment()")}} یا سازنده ایجاد کرد.

## عملکرد

مزیت عملکردی `DocumentFragment` اغلب بیش از حد برآورد می‌شود. در واقع، در برخی موتورها، استفاده از `DocumentFragment` کندتر از افزودن مستقیم به سند در یک حلقه است، همانطور که در [این بنچمارک](https://jsbench.me/02l63eic9j/1) نشان داده شده است. با این حال، تفاوت بین این مثال‌ها به قدری ناچیز است که بهتر است به جای عملکرد، روی خوانایی بهینه‌سازی کنید.

## مثال

### HTML

```html
<ul></ul>
```

### JavaScript

```js
const ul = document.querySelector("ul");
const fruits = ["Apple", "Orange", "Banana", "Melon"];

const fragment = new DocumentFragment();

for (const fruit of fruits) {
  const li = document.createElement("li");
  li.textContent = fruit;
  fragment.append(li);
}

ul.append(fragment);
```

### نتیجه

{{EmbedLiveSample('Example')}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}