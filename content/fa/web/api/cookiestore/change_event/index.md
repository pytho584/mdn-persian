---
title: "CookieStore: change event"
short-title: change
slug: Web/API/CookieStore/change_event
page-type: web-api-event
browser-compat: api.CookieStore.change_event
---

{{securecontext_header}}{{APIRef("Cookie Store API")}}

هنگامی که در هر کوکی تغییری ایجاد شود، یک رویداد `change` روی شیء {{domxref("CookieStore")}} به راه میافتد.

## نحو (Syntax)

برای استفاده از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} یا تنظیم ویژگی کنترل‌کننده رویداد، از این الگو استفاده کنید:

```js-nolint
addEventListener("change", (event) => { })

onchange = (event) => { }
```

## نوع رویداد

یک {{domxref("CookieChangeEvent")}} که از {{domxref("Event")}} به ارث می‌رسد.

{{InheritanceDiagram("CookieChangeEvent")}}

## مثال‌ها

برای اینکه هنگام تغییر یک کوکی مطلع شوید، می‌توانید یک کنترل‌کننده به نمونه `cookieStore` با استفاده از {{domxref("EventTarget.addEventListener", "addEventListener()")}} اضافه کنید، مانند این:

```js
cookieStore.addEventListener("change", (event) => {
  console.log("1 change event");
});
```

همچنین می‌توانید از ویژگی کنترل‌کننده رویداد `onchange` برای برقراری یک کنترل‌کننده برای رویداد `change` استفاده کنید:

```js
cookieStore.onchange = (event) => {
  console.log("1 change event");
};
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}