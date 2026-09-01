---
title: "Document: hidden property"
---

---
title: "Document: hidden property"
short-title: hidden
slug: Web/API/Document/hidden
page-type: web-api-instance-property
browser-compat: api.Document.hidden
---

{{ ApiRef("DOM") }}

ویژگی فقطخواندنی **`Document.hidden`** یک مقدار بولین برمیگرداند که نشان میدهد آیا صفحه پنهان در نظر گرفته شده است یا خیر. میتوانید از این ویژگی برای بررسی اینکه آیا سند در پسزمینه است، در یک پنجرهٔ کوچکشده قرار دارد، یا به هر شکل دیگری برای کاربر قابل مشاهده نیست، استفاده کنید.

ویژگی {{domxref("Document.visibilityState")}} روشی جایگزین برای تعیین پنهان بودن صفحه ارائه میدهد.

## مقدار

یک مقدار بولین؛ اگر صفحه پنهان باشد `true` و در غیر این صورت `false`.

## نمونهها

```js
document.addEventListener("visibilitychange", () => {
  console.log(document.hidden);
  // Modify behavior…
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("Document.visibilityState")}}