---
title: "PopStateEvent: state property"
short-title: state
slug: Web/API/PopStateEvent/state
page-type: web-api-instance-property
browser-compat: api.PopStateEvent.state
---

{{ APIRef("History API") }}

ویژگی فقط‌خواندنی **`state`** از رابط {{domxref("PopStateEvent")}}، وضعیت (state) ذخیره‌شده هنگام ایجاد رویداد را نشان می‌دهد.

در عمل، این همان `state`ای است که هنگام فراخوانی {{domxref("history.pushState()")}} یا {{domxref("history.replaceState()")}} تنظیم شده است.

## مقدار

یک شیء، یا `null`.

## مثال‌ها

کد زیر مقدار `state` را هنگام استفاده از متد {{domxref("History.pushState","pushState()")}} برای افزودن یک مقدار به تاریخچه، در لاگ ثبت می‌کند.

```js
// Log the state of
addEventListener("popstate", (event) => {
  console.log("State received: ", event.state);
});

// Now push something on the stack
history.pushState({ name: "Example" }, "pushState example", "page1.html");
history.pushState(
  { name: "Another example" },
  "pushState example",
  "page1.html",
);
```

خروجی زیر در لاگ ثبت می‌شود:

```plain
State received: { name: "Example" }
State received: { name: "Another example" }
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- سازنده {{domxref("PopStateEvent()")}}
- {{domxref("History.state")}}