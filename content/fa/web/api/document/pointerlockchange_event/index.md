---
title: "Document: pointerlockchange event"
short-title: pointerlockchange
slug: Web/API/Document/pointerlockchange_event
page-type: web-api-event
browser-compat: api.Document.pointerlockchange_event
---

{{APIRef("Pointer Lock API")}}

رویداد **`pointerlockchange`** زمانی فعال می‌شود که اشاره‌گر قفل یا باز شود.

مدیریت‌کننده رویداد می‌تواند از {{domxref("Document.pointerLockElement")}} برای تعیین اینکه آیا اشاره‌گر قفل شده است و اگر چنین است، به کدام عنصر قفل شده است، استفاده کند.

این رویداد قابل لغو نیست و به بالا منتشر نمی‌شود.

## نحو (Syntax)

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی مدیریت‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("pointerlockchange", (event) => { })

onpointerlockchange = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

استفاده از `addEventListener()`:

```js
addEventListener("pointerlockchange", (event) => {
  if (document.pointerLockElement)
    console.log("The pointer is locked to: ", document.pointerLockElement);
  else {
    console.log("The pointer is not locked");
  }
});
```

استفاده از ویژگی مدیریت‌کننده رویداد `onpointerlockchange`:

```js
document.onpointerlockchange = (event) => {
  if (document.pointerLockElement)
    console.log("The pointer is locked to: ", document.pointerLockElement);
  else {
    console.log("The pointer is not locked");
  }
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [استفاده از API قفل اشاره‌گر](/en-US/docs/Web/API/Pointer_Lock_API)