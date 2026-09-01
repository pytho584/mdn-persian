---
title: "HTMLScriptElement: async property"
---

{{APIRef("HTML DOM")}}

ویژگی **`async``** از رابط {{domxref("HTMLScriptElement")}} یک مقدار بولین است که نحوه اجرای اسکریپت را کنترل می‌کند. برای اسکریپت‌های کلاسیک، اگر این ویژگی روی `true` تنظیم شود، اسکریپت خارجی همزمان با تجزیه (parsing) واکشی شده و به محض در دسترس بودن ارزیابی می‌شود. برای [اسکریپت‌های ماژول](/en-US/docs/Web/JavaScript/Guide/Modules)، اگر `async` روی `true` تنظیم شود، اسکریپت و تمام وابستگی‌های آن همزمان با تجزیه واکشی شده و به محض در دسترس بودن ارزیابی می‌شوند.

این ویژگی منعکس‌کننده ویژگی `async` عنصر {{HTMLElement("script")}} است.

## مقدار

یک مقدار بولین.

## مثال‌ها

```html
<script id="el" src="/example.js" async></script>
```

```js
const el = document.getElementById("el");
console.log(el.async); // Output: true
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLScriptElement.defer")}}