---
title: "HTMLTemplateElement: content property"
short-title: content
slug: Web/API/HTMLTemplateElement/content
page-type: web-api-instance-property
browser-compat: api.HTMLTemplateElement.content
---

{{APIRef("Web Components")}}

ویژگی **`content`** در رابط {{domxref("HTMLTemplateElement")}}، محتوای الگوی عنصر `<template>` را به‌صورت یک {{domxref("DocumentFragment")}} (بخش‌ی مستند) برمی‌گرداند. ویژگی {{domxref("Node/ownerDocument", "ownerDocument")}} این محتوا، یک {{domxref("Document")}} جداگانه است، نه همان سندی که عنصر `<template>` در آن قرار دارد — مگر اینکه خود سندِ حاوی، به‌طور خاص برای نگه‌داشتن محتوای الگو ساخته شده باشد.

هر دو روش {{domxref("Node.cloneNode()")}} و {{domxref("Document.importNode()")}} یک کپی از یک گره ایجاد می‌کنند. تفاوت در این است که `importNode()` گره را در بافت سندِ فراخواننده شبیه‌سازی می‌کند، در حالی که `cloneNode()` از سندِ متعلق به همان گره استفاده می‌کند. بافتِ سند تعیین می‌کند که {{domxref("CustomElementRegistry")}} برای ساخت هر عنصر سفارشی، کدام باشد. به همین دلیل، برای شبیه‌سازیِ بخشِ `content` از `document.importNode()` استفاده کنید تا عناصر سفارشیِ فرزند، با تعاریفِ موجود در سندِ فعلی ساخته شوند، نه با آن سندِ جداگانه‌ای که مالکِ محتوای الگوست. برای جزئیات بیشتر، مثال‌های صفحه {{domxref("Node.cloneNode()")}} را ببینید.

## مقدار

یک {{domxref("DocumentFragment")}}.

## مثال‌ها

### استفاده از importNode() با محتوای الگو

```js
const templateElement = document.querySelector("#foo");
const documentFragment = document.importNode(templateElement.content, true);
// Now you can insert the documentFragment into the DOM
```

### ownerDocument محتوای الگو

برای عناصر `<template>` که در بافت یک سند HTML معمولی ساخته شده‌اند، `ownerDocument` مربوط به `content` یک سند جداگانه و تازه‌ساخته است:

```js
const template = document.createElement("template");
console.log(template.content.ownerDocument === document); // false
console.log(template.content.ownerDocument.URL); // "about:blank"
```

اگر عنصر `<template>` در بافت سندی ساخته شود که خودش برای نگه‌داشتن محتوای الگو ایجاد شده است، آنگاه `ownerDocument` مربوط به `content` همان سندِ حاوی خواهد بود:

```js
const template1 = document.createElement("template");
const docForTemplate = template1.content.ownerDocument;
const template2 = docForTemplate.createElement("template");
console.log(template2.content.ownerDocument === docForTemplate); // true
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLTemplateElement")}}