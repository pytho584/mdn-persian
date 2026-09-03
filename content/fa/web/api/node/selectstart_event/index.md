---
title: "Node: selectstart event"
short-title: selectstart
slug: Web/API/Node/selectstart_event
page-type: web-api-event
browser-compat: api.Node.selectstart_event
---

{{APIRef("Selection API")}}

رویداد **`selectstart`** از [Selection API](/en-US/docs/Web/API/Selection) زمانی رخ می‌دهد که کاربر یک انتخاب جدید را آغاز می‌کند.

اگر رویداد لغو شود، انتخاب تغییر نمی‌کند.

## Syntax

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد تنظیم کنید.

```js-nolint
addEventListener("selectstart", (event) => { })

onselectstart = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

```js
// نسخه addEventListener
document.addEventListener("selectstart", () => {
  console.log("Selection started");
});

// نسخه onselectstart
document.onselectstart = () => {
  console.log("Selection started.");
};
```

## Specifications

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Document/selectionchange_event", "selectionchange")}}