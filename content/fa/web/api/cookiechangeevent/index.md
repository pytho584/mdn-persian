---
title: CookieChangeEvent
slug: Web/API/CookieChangeEvent
page-type: web-api-interface
browser-compat: api.CookieChangeEvent
---

{{securecontext_header}}{{APIRef("Cookie Store API")}}

رابط **`CookieChangeEvent`** از {{domxref("Cookie Store API", "", "", "nocode")}} نوع رویداد {{domxref("CookieStore/change_event", "change")}} است که در یک {{domxref("CookieStore")}} هنگامی که هر کوکی ایجاد یا حذف می‌شود، فعال می‌گردد.

> [!NOTE]
> کوکی‌ای که به دلیل درج کوکی دیگری با نام، دامنه و مسیر یکسان جایگزین می‌شود، نادیده گرفته شده و رویداد change را فعال نمی‌کند.

{{InheritanceDiagram}}

## سازنده

- {{domxref("CookieChangeEvent.CookieChangeEvent", "CookieChangeEvent()")}}
  - : یک `CookieChangeEvent` جدید ایجاد می‌کند.

## ویژگی‌های نمونه

_این رابط همچنین ویژگی‌هایی را از {{domxref("Event")}} به ارث می‌برد._

- {{domxref("CookieChangeEvent.changed")}} {{ReadOnlyInline}}
  - : یک آرایه شامل تمام کوکی‌های تازه ایجاد شده. توجه داشته باشید که این شامل کوکی‌هایی که با تاریخ انقضا در گذشته ایجاد شده‌اند نمی‌شود، زیرا این کوکی‌ها بلافاصله حذف می‌شوند.
- {{domxref("CookieChangeEvent.deleted")}} {{ReadOnlyInline}}
  - : یک آرایه شامل تمام کوکی‌هایی که حذف شده‌اند، چه به دلیل منقضی شدن و چه به دلیل حذف صریح. توجه داشته باشید که این شامل کوکی‌هایی که با تاریخ انقضا در گذشته ایجاد شده‌اند نیز می‌شود.

## روش‌های نمونه

_این رابط همچنین روش‌هایی را از {{domxref("Event")}} به ارث می‌برد._

## مثال‌ها

در این مثال، هنگامی که کوکی تنظیم می‌شود، شنونده رویداد، رویداد را در کنسول ثبت می‌کند. این یک شیء `CookieChangeEvent` است که ویژگی {{domxref("CookieChangeEvent.changed","changed")}} آن شامل یک شیء نمایش‌دهنده کوکی است که به تازگی تنظیم شده است.

```js
cookieStore.addEventListener("change", (event) => {
  console.log(event);
});

const oneDay = 24 * 60 * 60 * 1000;
cookieStore.set({
  name: "cookie1",
  value: "cookie1-value",
  expires: Date.now() + oneDay,
  domain: "example.com",
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}