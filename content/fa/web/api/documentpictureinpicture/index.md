---
title: "DocumentPictureInPicture"
---

---
title: DocumentPictureInPicture
slug: Web/API/DocumentPictureInPicture
page-type: web-api-interface
browser-compat: api.DocumentPictureInPicture
---

{{APIRef("Document Picture-in-Picture API")}}{{securecontext_header}}

**`DocumentPictureInPicture`** یک رابط (interface) از {{domxref("Document Picture-in-Picture API", "Document Picture-in-Picture API", "", "nocode")}} است که نقطه ورود برای ایجاد و مدیریت پنجره‌های تصویر-در-تصویر سند به شمار می‌رود.

از طریق ویژگی {{domxref("Window.documentPictureInPicture")}} قابل دسترسی است.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

_ویژگی‌های والد خود، یعنی {{DOMxRef("EventTarget")}} را به ارث می‌برد._

- {{domxref("DocumentPictureInPicture.window", "window")}} {{ReadOnlyInline}}
  - : یک نمونه {{domxref("Window")}} را برمی‌گرداند که زمینه مرور داخل پنجره تصویر-در-تصویر را نشان می‌دهد.

## روش‌های نمونه

_روش‌های والد خود، یعنی {{DOMxRef("EventTarget")}} را به ارث می‌برد._

- {{domxref("DocumentPictureInPicture.requestWindow", "requestWindow()")}}
  - : پنجره تصویر-در-تصویر را برای زمینه مرور اصلی فعلی باز می‌کند. یک {{jsxref("Promise")}} برمی‌گرداند که با یک نمونه {{domxref("Window")}}، نشان‌دهنده زمینه مرور داخل پنجره تصویر-در-تصویر، برآورده (fulfill) می‌شود.

## رویدادها

_رویدادهای والد خود، یعنی {{DOMxRef("EventTarget")}} را به ارث می‌برد._

- {{domxref("DocumentPictureInPicture/enter_event", "enter")}}
  - : زمانی که پنجره تصویر-در-تصویر با موفقیت باز شود، این رویداد فعال می‌شود.

## مثال‌ها

```js
const videoPlayer = document.getElementById("player");

// …

// Open a Picture-in-Picture window.
const pipWindow = await window.documentPictureInPicture.requestWindow({
  width: videoPlayer.clientWidth,
  height: videoPlayer.clientHeight,
});

// …
```

برای مشاهده یک دموی کامل و کاربردی، به [Document Picture-in-Picture API Example](https://mdn.github.io/dom-examples/document-picture-in-picture/) مراجعه کنید (همچنین [source code](https://github.com/mdn/dom-examples/tree/main/document-picture-in-picture) کامل را ببینید).

## مشخصات

{{Specifications}}

## سازگاری مرورگرها

{{Compat}}

## همچنین ببینید

- {{domxref("Document Picture-in-Picture API", "Document Picture-in-Picture API", "", "nocode")}}
- [Using the Document Picture-in-Picture API](/en-US/docs/Web/API/Document_Picture-in-Picture_API/Using)