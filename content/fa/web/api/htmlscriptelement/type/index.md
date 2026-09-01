---
title: "HTMLScriptElement: type property"
---

---
title: "HTMLScriptElement: type property"
short-title: type
slug: Web/API/HTMLScriptElement/type
page-type: web-api-instance-property
browser-compat: api.HTMLScriptElement.type
---

{{APIRef("HTML DOM")}}

ویژگی **`type`** در رابط {{domxref("HTMLScriptElement")}} یک رشته است که نوع اسکریپت را منعکس می‌کند.

این ویژگی بازتاب‌دهنده ویژگی `type` عنصر {{HTMLElement("script")}} است.

## مقدار

یک رشته. مقدار این ویژگی می‌تواند یکی از موارد زیر باشد:

- **ویژگی تنظیم نشده (پیش‌فرض)، یک رشته خالی، یا یک نوع MIME جاوااسکریپت**
  - : نشان می‌دهد که اسکریپت یک «اسکریپت کلاسیک» است و شامل کد جاوااسکریپت است.
- `module`
  - : این مقدار باعث می‌شود کد به‌عنوان یک ماژول جاوااسکریپت در نظر گرفته شود.
- `importmap`
  - : این مقدار نشان می‌دهد که بدنه عنصر شامل یک نقشه واردات (import map) است.
- `speculationrules` {{experimental_inline}}
  - : این مقدار نشان می‌دهد که بدنه عنصر شامل قوانین حدس‌زنی (speculation rules) است.
- **هر مقدار دیگری**
  - : محتوای جاسازی‌شده به‌عنوان یک بلوک داده در نظر گرفته می‌شود و توسط مرورگر پردازش نخواهد شد.

برای اطلاعات بیشتر، به ویژگی [`type`](/en-US/docs/Web/HTML/Reference/Elements/script/type) عنصر {{HTMLElement("script")}} مراجعه کنید.

## نمونه‌ها

```html
<script id="el" type="module"></script>
```

```js
const el = document.getElementById("el");
console.log(el.type); // Output: "module"
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}
