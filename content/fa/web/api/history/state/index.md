---
title: "History: state property"
short-title: state
slug: Web/API/History/state
page-type: web-api-instance-property
browser-compat: api.History.state
---

{{APIRef("History API")}}

ویژگی فقط‌خواندنی **`state`** در رابط {{DOMxRef("History")}} مقداری را برمی‌گرداند که بیانگر وضعیت در بالای پشتهٔ تاریخچه است. این روشی برای مشاهدهٔ وضعیت است، بدون اینکه لازم باشد منتظر رویداد {{domxref("Window/popstate_event", "popstate")}} بمانید.

## مقدار

وضعیت بالای پشتهٔ تاریخچه. این مقدار تا زمانی که از متد {{domxref("History.pushState","pushState()")}} یا {{domxref("History.replaceState","replaceState()")}} استفاده نشود، [`null`](/en-US/docs/Web/JavaScript/Reference/Operators/null) است.

## مثال‌ها

کد زیر مقدار `history.state` را پیش از استفاده از متد {{domxref("History.pushState","pushState()")}} برای افزودن یک مقدار به پشتهٔ تاریخچه، در کنسول ثبت می‌کند. خط بعدی دوباره مقدار را در کنسول ثبت می‌کند و نشان می‌دهد که `history.state` حالا دارای مقدار است.

```js
// Should be null because we haven't modified the history stack yet
console.log("History.state before pushState: ", history.state);

// Now push something on the stack
history.pushState({ name: "Example" }, "pushState example", "page3.html");

// Now state has a value.
console.log("History.state after pushState: ", history.state);
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [کار با History API](/en-US/docs/Web/API/History_API/Working_with_the_History_API)
- [`History.pushState()`](/en-US/docs/Web/API/History/pushState)
- [`History.replaceState()`](/en-US/docs/Web/API/History/replaceState)
- [`PopStateEvent.state`](/en-US/docs/Web/API/PopStateEvent/state)