---
title: "HTMLImageElement: loading property"
---

---
title: "HTMLImageElement: loading property"
short-title: loading
slug: Web/API/HTMLImageElement/loading
page-type: web-api-instance-property
browser-compat: api.HTMLImageElement.loading
---

{{APIRef("HTML DOM")}}

ویژگی **`loading`** در رابط {{domxref("HTMLImageElement")}} به مرورگر راهنمایی می‌کند که بارگذاری تصویری را که در حال حاضر خارج از {{Glossary("visual viewport")}} پنجره است چگونه مدیریت کند. این ویژگی با به‌تأخیر انداختن بارگذاری تصویر تا زمانی که انتظار می‌رود به آن نیاز باشد — به‌جای بارگذاری فوری هنگام بارگذاری اولیهٔ صفحه — به بهینه‌سازی بارگذاری محتوای سند کمک می‌کند. این ویژگی، ویژگی محتوایی [`loading`](/en-US/docs/Web/HTML/Reference/Elements/img#loading) عنصر `<img>` را منعکس می‌کند.

## مقدار

رشته‌ای که مقدار آن یکی از `eager` یا `lazy` است. برای آشنایی با معانی این مقادیر، به مرجع HTML عنصر [`<img>`](/en-US/docs/Web/HTML/Reference/Elements/img#loading) مراجعه کنید.

## مثال‌ها

### استفادهٔ پایه

تابع `addImageToList()` که در زیر نشان داده شده است، یک تصویر بندانگشتی به فهرستی از آیتم‌ها اضافه می‌کند و از بارگذاری تنبل (lazy-loading) استفاده می‌کند تا تصویر تا زمانی که واقعاً به آن نیاز نیست از شبکه بارگذاری نشود.

```js
function addImageToList(url) {
  const list = document.querySelector("div.photo-list");

  const newItem = document.createElement("div");
  newItem.className = "photo-item";

  const newImg = document.createElement("img");
  newImg.loading = "lazy";
  newImg.width = 320;
  newImg.height = 240;
  newImg.src = url;

  newItem.appendChild(newImg);
  list.appendChild(newItem);
}
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- عنصر {{HTMLElement("img")}}
- [عملکرد وب](/en-US/docs/Learn_web_development/Extensions/Performance) در بخش یادگیری MDN
- [بارگذاری تنبل](/en-US/docs/Web/Performance/Guides/Lazy_loading) در راهنمای عملکرد وب MDN