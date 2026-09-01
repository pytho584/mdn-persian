---
title: "EventSource: EventSource() constructor"
short-title: EventSource()
slug: Web/API/EventSource/EventSource
page-type: web-api-constructor
browser-compat: api.EventSource.EventSource
---

{{APIRef("Server Sent Events")}}{{AvailableInWorkers}}

سازندهٔ **`EventSource()`** یک شیء {{domxref("EventSource")}} تازهساختهشده را برمیگرداند که یک منبع راه‌دور را نمایش می‌دهد.

## Syntax

```js-nolint
new EventSource(url)
new EventSource(url, options)
```

### پارامترها

- `url`
  - : یک رشته که مکان منبع راه‌دوری را نشان می‌دهد که رویدادها/پیام‌ها را سرو می‌کند.
- `options` {{optional_inline}}
  - : گزینه‌هایی برای پیکربندی اتصال جدید فراهم می‌کند. ورودی‌های ممکن عبارت‌اند از:
    - `withCredentials` {{optional_inline}}
      - : یک مقدار بولی، که پیش‌فرض آن `false` است، نشان می‌دهد که آیا CORS باید برای شامل‌کردن اعتبارنامه‌ها (credentials) روی `include` تنظیم شود یا نه.

## مثال‌ها

```js
const evtSource = new EventSource("sse.php");
const eventList = document.querySelector("ul");

evtSource.onmessage = (e) => {
  const newElement = document.createElement("li");

  newElement.textContent = `message: ${e.data}`;
  eventList.appendChild(newElement);
};
```

> [!NOTE]
> می‌توانید یک مثال کامل را در GitHub بیابید — [نمونهٔ سادهٔ SSE با استفاده از PHP](https://github.com/mdn/dom-examples/tree/main/server-sent-events).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("EventSource")}}