---
title: "HTMLElement: editContext property"
short-title: editContext
slug: Web/API/HTMLElement/editContext
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.HTMLElement.editContext
---

{{APIRef("EditContext API")}}{{SeeCompatTable}}

ویژگی **`editContext`** از رابط {{domxref("HTMLElement")}}، شیء {{domxref("EditContext")}} مرتبط با یک عنصر را دریافت و تنظیم می‌کند.

از {{domxref("EditContext API", "", "", "nocode")}} می‌توان برای ساخت ویرایشگرهای متن غنی در وب استفاده کرد که از تجربه‌های پیشرفته ورود متن پشتیبانی می‌کنند؛ مانند ترکیب {{glossary("Input Method Editor")}} (IME)، انتخاب‌گر ایموجی، یا هر رابط کاربری مرتبط با ویرایش که مختص پلتفرم خاصی است.

## مقدار

یک شیء {{domxref("EditContext")}} یا `null`.

### عناصر مجاز

تنظیم ویژگی `editContext` فقط روی انواع خاصی از عناصر کار می‌کند:

- یکی از این عناصر HTML: [`<article>`](/en-US/docs/Web/HTML/Reference/Elements/article)، [`<aside>`](/en-US/docs/Web/HTML/Reference/Elements/aside)، [`<blockquote>`](/en-US/docs/Web/HTML/Reference/Elements/blockquote)، [`<body>`](/en-US/docs/Web/HTML/Reference/Elements/body)، [`<div>`](/en-US/docs/Web/HTML/Reference/Elements/div)، [`<footer>`](/en-US/docs/Web/HTML/Reference/Elements/footer)، [`<h1>`](/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements)، [`<h2>`](/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements)، [`<h3>`](/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements)، [`<h4>`](/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements)، [`<h5>`](/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements)، [`<h6>`](/en-US/docs/Web/HTML/Reference/Elements/Heading_Elements)، [`<header>`](/en-US/docs/Web/HTML/Reference/Elements/header)، [`<main>`](/en-US/docs/Web/HTML/Reference/Elements/main)، [`<nav>`](/en-US/docs/Web/HTML/Reference/Elements/nav)، [`<p>`](/en-US/docs/Web/HTML/Reference/Elements/p)، [`<section>`](/en-US/docs/Web/HTML/Reference/Elements/section)، یا [`<span>`](/en-US/docs/Web/HTML/Reference/Elements/span).
- یک [عنصر سفارشی](/en-US/docs/Web/API/Web_components/Using_custom_elements) معتبر.
- یک عنصر [`<canvas>`](/en-US/docs/Web/HTML/Reference/Elements/canvas).

اگر بخواهید ویژگی `editContext` را روی عنصری که در فهرست بالا نیست تنظیم کنید، یک {{domxref("DOMException")}} از نوع `NotSupportedError` پرتاب می‌شود.

### ارتباط عنصر

تنظیم ویژگی `editContext` یک عنصر به یک نمونه {{domxref("EditContext")}}، آن عنصر را با آن نمونه `EditContext` مرتبط می‌کند.

این ارتباط یک‌به‌یک است:

- هر عنصر فقط می‌تواند با یک نمونه `EditContext` مرتبط شود.
- هر نمونه `EditContext` فقط می‌تواند با یک عنصر مرتبط شود.

اگر بخواهید یک نمونه `EditContext` که قبلاً با عنصری مرتبط شده را به عنصر دیگری متصل کنید، یک {{domxref("DOMException")}} پرتاب می‌شود.

همچنین اگر بخواهید یک نمونه `EditContext` دیگر را به عنصری که قبلاً با نمونه‌ای مرتبط شده متصل کنید، یک {{domxref("DOMException")}} پرتاب می‌شود.

برای بررسی اینکه آیا عنصری قبلاً با یک نمونه `EditContext` مرتبط شده است یا نه، از روش {{domxref("EditContext.attachedElements()")}} استفاده کنید.

### جمع‌آوری زباله

یک نمونه `EditContext` عنصر مرتبط خود را زنده نگه می‌دارد اگر ارجاعات زنده دیگری به آن وجود داشته باشد، حتی اگر عنصر مرتبط از DOM حذف شده باشد.

اگر می‌خواهید مطمئن شوید که عنصر توسط جمع‌آوری زباله آزاد می‌شود، ویژگی `editContext` عنصر را پاک کنید.

## مثال‌ها

### تنظیم ویژگی `editContext` یک عنصر

این مثال نشان می‌دهد که چگونه ویژگی `editContext` یک عنصر `<canvas>` را روی یک نمونه جدید `EditContext` تنظیم کنید تا آن عنصر قابل ویرایش شود.

```html
<canvas id="editor-canvas"></canvas>
```

```js
const canvas = document.getElementById("editor-canvas");
const editContext = new EditContext();
canvas.editContext = editContext;
```

### پاک کردن ویژگی `editContext` یک عنصر

این مثال نشان می‌دهد که چگونه ویژگی `editContext` یک عنصر `<canvas>` قابل ویرایش را پاک کنید تا عنصر به‌طور امن از DOM حذف شود.

```html
<canvas id="editor-canvas"></canvas>
```

```js
// ایجاد EditContext و ارتباط آن با عنصر canvas.
const canvas = document.getElementById("editor-canvas");
const editContext = new EditContext();
canvas.editContext = editContext;

// بعداً، ویژگی editContext را پاک کرده و عنصر را حذف کنید.
canvas.editContext = null;
canvas.remove();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- رابط {{DOMxRef("EditContext")}}.
