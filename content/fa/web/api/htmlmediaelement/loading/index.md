---
title: "HTMLMediaElement: loading property"
short-title: loading
slug: Web/API/HTMLMediaElement/loading
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.HTMLMediaElement.loading
---

{{APIRef("HTML DOM")}}{{SeeCompatTable}}

ویژگی **`loading`** در رابط {{domxref("HTMLMediaElement")}} راهنمایی به مرورگر می‌دهد که بارگذاری رسانه‌ای که در حال حاضر خارج از {{Glossary("visual viewport")}} پنجره است چگونه مدیریت شود. این کار با به تعویق انداختن بارگذاری رسانه تا زمانی که انتظار می‌رود به آن نیاز باشد، بارگذاری محتوای سند را بهینه می‌کند؛ به جای اینکه بلافاصله در بارگذاری اولیه صفحه انجام شود. این ویژگی، ویژگی محتوایی [`loading`](/en-US/docs/Web/HTML/Reference/Elements/audio#loading) عنصر `<audio>` یا ویژگی محتوایی [`loading`](/en-US/docs/Web/HTML/Reference/Elements/video#loading) عنصر `<video>` را بازتاب می‌دهد.

## Value

یک رشته که مقدار آن یکی از `eager` یا `lazy` است. برای معانی هر یک، به مرجع HTML [`<audio loading>`](/en-US/docs/Web/HTML/Reference/Elements/audio#loading) یا [`<video loading>`](/en-US/docs/Web/HTML/Reference/Elements/video#loading) مراجعه کنید.

## Examples

### استفادهٔ پایه

تابع `addVideoToList()` که در زیر نشان داده شده است، یک تصویر بندانگشتی ویدیو به فهرستی از موارد اضافه می‌کند و از بارگذاری تنبل (lazy-loading) استفاده می‌کند تا از بارگذاری ویدیو از شبکه تا زمانی که واقعاً به آن نیاز نیست جلوگیری کند.

```js
function addVideoToList(url) {
  const list = document.querySelector("div.video-list");

  const newItem = document.createElement("div");
  newItem.className = "video-item";

  const newVideo = document.createElement("video");

  // Lazy-load if supported
  if ("loading" in HTMLVideoElement.prototype) {
    newVideo.loading = "lazy";
  } else {
    // If native lazy-loading is not supported you may want to consider
    // alternatives, though this may be fine as a progressive enhancement.
  }

  newVideo.width = 320;
  newVideo.height = 240;
  newVideo.src = url;

  newItem.appendChild(newVideo);
  list.appendChild(newItem);
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- عنصر {{HTMLElement("audio")}}
- عنصر {{HTMLElement("video")}}
- [کارایی وب](/en-US/docs/Learn_web_development/Extensions/Performance) در بخش آموزش MDN
- [بارگذاری تنبل](/en-US/docs/Web/Performance/Guides/Lazy_loading) در راهنمای کارایی وب MDN