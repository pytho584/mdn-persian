---
title: "Document: getSelection() method"
short-title: getSelection()
slug: Web/API/Document/getSelection
page-type: web-api-instance-method
browser-compat: api.Document.getSelection
---

{{APIRef("DOM")}}

متد **`getSelection()`** در رابط {{DOMxRef("Document")}}، شیء {{DOMxRef("Selection")}} مرتبط با این سند را برمی‌گرداند که محدوده متنی انتخاب‌شده توسط کاربر یا موقعیت فعلی مکان‌نما را نشان می‌دهد.

## نحو (Syntax)

```js-nolint
getSelection()
```

### پارامترها

هیچ.

### مقدار بازگشتی

یک شیء {{DOMxRef("Selection")}}، یا اگر سند دارای [زمینه مرور (browsing context)](/en-US/docs/Glossary/Browsing_context) نباشد (مثلاً سند یک {{htmlelement("iframe")}} که به سندی متصل نیست)، مقدار `null` برمی‌گرداند.

## مثال‌ها

### به دست آوردن یک شیء Selection

```js
const selection = document.getSelection();
const selRange = selection.getRangeAt(0);
// کارهای لازم با range انجام دهید

console.log(selection); // شیء Selection
```

### نمایش رشته‌ای از شیء Selection

برخی توابع (مانند {{DOMxRef("Window.alert()")}}) به‌طور خودکار {{JSxRef("Object.toString", "toString()")}} را فراخوانی می‌کنند و مقدار بازگشتی به تابع ارسال می‌شود. در نتیجه، این کار متن انتخاب‌شده را برمی‌گرداند و نه شیء `Selection` را:

```js
alert(selection);
```

با این حال، همه توابع به‌طور خودکار `toString()` را فراخوانی نمی‌کنند.
برای استفاده از یک شیء `Selection` به‌عنوان رشته، متد `toString()` آن را مستقیماً فراخوانی کنید:

```js
let selectedText = selection.toString();
```

## اشیاء مرتبط

می‌توانید {{domxref("Window.getSelection()")}} را فراخوانی کنید که با `window.document.getSelection()` یکسان است.

شایان ذکر است که در حال حاضر `getSelection()` روی محتوای عناصر {{htmlelement("input")}} در فایرفاکس کار نمی‌کند.
برای دور زدن این مشکل می‌توان از {{domxref("HTMLInputElement.setSelectionRange()")}} استفاده کرد.

همچنین به تفاوت بین _selection_ (انتخاب) و _focus_ (تمرکز) توجه کنید.
{{domxref("Document.activeElement")}} عنصر دارای تمرکز را برمی‌گرداند.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}