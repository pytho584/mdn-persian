---
title: "MutationObserver: takeRecords() method"
short-title: takeRecords()
slug: Web/API/MutationObserver/takeRecords
page-type: web-api-instance-method
browser-compat: api.MutationObserver.takeRecords
---

{{APIRef("DOM WHATWG")}}

متد {{domxref("MutationObserver")}} به نام **`takeRecords()`** فهرستی از تمام تغییرات DOM منطبق را برمی‌گرداند که شناسایی شده‌اند اما هنوز توسط تابع callback مشاهده‌گر پردازش نشده‌اند و صف تغییرات را خالی می‌کند.

رایج‌ترین کاربرد این متد این است که درست پیش از قطع کردن مشاهده‌گر، همه‌ی رکوردهای تغییرِ در انتظار بلافاصله دریافت شوند تا هنگام توقف مشاهده‌گر، بتوان هر تغییری را که هنوز در صف است پردازش کرد.

## دستور زبان

```js-nolint
takeRecords()
```

### پارامترها

هیچ.

### مقدار بازگشتی

آرایه‌ای از اشیاء {{domxref("MutationRecord")}} که هر یک یک تغییرِ اعمال‌شده بر بخش مشاهده‌شده‌ی درخت DOM سند را توصیف می‌کند.

> [!NOTE]
> صف تغییراتی که رخ داده‌اند اما هنوز به تابع callback مشاهده‌گر تحویل داده نشده‌اند، پس از فراخوانی `takeRecords()` خالی می‌ماند.

## مثال‌ها

در این مثال، نشان می‌دهیم که چگونه هر {{domxref("MutationRecord")}} تحویل‌نشده‌ای را می‌توان با فراخوانی `takeRecords()` درست پیش از قطع کردن مشاهده‌گر پردازش کرد.

```js
const targetNode = document.querySelector("#someElement");
const observerOptions = {
  childList: true,
  attributes: true,
};

const observer = new MutationObserver(callback);
observer.observe(targetNode, observerOptions);

/* later, when it's time to stop observing… */

/* handle any still-pending mutations */

let mutations = observer.takeRecords();

observer.disconnect();

if (mutations.length > 0) {
  callback(mutations);
}
```

این کد هر رکورد تغییر پردازش‌نشده‌ای را دریافت می‌کند و سپس تابع callback را با آن رکوردها فراخوانی می‌کند تا بتوانند پردازش شوند. این کار بلافاصله پیش از فراخوانی {{domxref("MutationObserver.disconnect", "disconnect()")}} برای توقف مشاهده‌ی DOM انجام می‌شود.

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}