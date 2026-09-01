---
title: "HTMLAllCollection"
slug: Web/API/HTMLAllCollection
page-type: web-api-interface
browser-compat: api.HTMLAllCollection
---

{{APIRef("DOM")}}{{Deprecated_Header}}

رابط **`HTMLAllCollection`** مجموعه‌ای از _همه_ عناصر سند را نشان می‌دهد که با استفاده از ایندکس (مانند آرایه) و با ویژگی [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) عنصر قابل دسترسی است. این رابط توسط ویژگی {{domxref("document.all")}} بازگردانده می‌شود.

`HTMLAllCollection` از نظر ساختار بسیار شبیه به {{domxref("HTMLCollection")}} است، اما تفاوت‌های رفتاری ظریف زیادی وجود دارد — برای مثال، `HTMLAllCollection` می‌تواند به عنوان یک تابع فراخوانی شود، و متد `item()` آن را می‌توان با یک رشته که نمایانگر ویژگی `id` یا `name` یک عنصر است فراخوانی کرد.

## ویژگی‌های نمونه

- {{domxref("HTMLAllCollection.length")}} {{ReadOnlyInline}}
  - : تعداد آیتم‌های موجود در مجموعه را بازمی‌گرداند.

## روش‌های نمونه

- {{domxref("HTMLAllCollection.item()")}}
  - : عنصری را که در افست مشخص شده در مجموعه قرار دارد، یا عنصری را که دارای مقدار مشخص شده برای ویژگی `id` یا `name` است بازمی‌گرداند. اگر هیچ عنصری یافت نشود، `null` بازمی‌گرداند.
- {{domxref("HTMLAllCollection.namedItem()")}}
  - : اولین [عنصر](/en-US/docs/Web/API/Element) در مجموعه را که ویژگی [`id`](/en-US/docs/Web/HTML/Reference/Global_attributes/id) یا `name` آن با نام رشته داده شده مطابقت دارد بازمی‌گرداند، یا اگر هیچ عنصری مطابقت نداشت `null` بازمی‌گرداند.

## استفاده در جاوا اسکریپت

### دسترسی ایندکسی

علاوه بر متدهای فوق، عناصر موجود در یک `HTMLAllCollection` می‌توانند با ایندکس‌های صحیح و نام‌های ویژگی رشته‌ای نیز قابل دسترسی باشند. ویژگی `id` در HTML ممکن است حاوی کاراکترهای معتبر `:` و `.` باشد که برای دسترسی به ویژگی نیاز به استفاده از نماد براکت (bracket notation) دارد. `collection[i]` معادل `collection.item(i)` است، که در آن `i` می‌تواند یک عدد صحیح، یک رشته حاوی عدد صحیح، یا یک رشته نمایانگر یک `id` باشد.

### فراخوانی به عنوان تابع

یک شیء `HTMLAllCollection` قابل فراخوانی است. هنگامی که بدون آرگومان یا با `undefined` فراخوانی شود، `null` بازمی‌گرداند. در غیر این صورت، همان مقدار متد {{domxref("HTMLAllCollection/item", "item()")}} را با همان آرگومان‌ها بازمی‌گرداند.

### رفتار ویژه تبدیل نوع

به دلایل تاریخی، `document.all` یک شیء است که به روش‌های زیر مانند `undefined` رفتار می‌کند:

- این شیء با `undefined` و `null` [برابر سست](/en-US/docs/Web/JavaScript/Reference/Operators/Equality) است.
- در زمینه‌های بولی [falsy](/en-US/docs/Glossary/Falsy) است.
- [`typeof`](/en-US/docs/Web/JavaScript/Reference/Operators/typeof) آن `"undefined"` است.

این رفتارهای خاص تضمین می‌کنند که کدی مانند:

```js
if (document.all) {
  // فرض می‌کنیم در IE هستیم؛ منطق ویژه ارائه دهید
}
// فرض می‌کنیم در یک مرورگر مدرن هستیم
```

حتی اگر کد در مرورگری اجرا شود که `document.all` را به دلایل سازگاری پیاده‌سازی کرده است، به ارائه رفتار مدرن ادامه خواهد داد.

با این حال، در سایر زمینه‌ها، `document.all` یک شیء باقی می‌ماند. برای مثال:

- این شیء با `undefined` یا `null` [به طور مساوی سخت‌گیرانه](/en-US/docs/Web/JavaScript/Reference/Operators/Strict_equality) برابر نیست.
- هنگامی که در سمت چپ [عملگر nullish coalescing](/en-US/docs/Web/JavaScript/Reference/Operators/Nullish_coalescing) (`??`) یا [عملگر زنجیره اختیاری](/en-US/docs/Web/JavaScript/Reference/Operators/Optional_chaining) (`?.`) استفاده شود، باعث اتصال کوتاه (short-circuit) عبارت نمی‌شود.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("HTMLCollection")}}