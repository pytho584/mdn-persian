---
title: "HTMLInputElement: search event"
---

---
title: "HTMLInputElement: search event"
short-title: search
slug: Web/API/HTMLInputElement/search_event
page-type: web-api-event
status:
  - non-standard
browser-compat: api.HTMLInputElement.search_event
---

{{APIRef("HTML DOM")}}{{non-standard_header}}

رویداد **`search`** زمانی شلیک می‌شود که یک جستجو با استفاده از عنصر {{HTMLElement("input")}} با `type="search"` آغاز شود.

راه‌های متعددی برای شروع جستجو وجود دارد؛ برای مثال، فشار دادن <kbd>Enter</kbd> در حالی که {{HTMLElement("input")}} فوکوس شده است، یا اگر ویژگی [`incremental`](/en-US/docs/Web/HTML/Reference/Elements/input#incremental) موجود باشد، پس از گذشت یک مهلت زمانی تعریف‌شده توسط مرورگر (UA) از آخرین ضربه کلید (با این که هر ضربه کلید جدید مهلت زمانی را از نو تنظیم می‌کند، بنابراین فعال شدن رویداد {{glossary("debounce", "debounced")}} به تعویق می‌افتد).

پیاده‌سازی‌های فعلی مرورگر (UA) از `<input type="search">` دارای یک کنترل اضافی برای پاک کردن فیلد هستند. استفاده از این کنترل همچنین رویداد `search` را فعال می‌کند. در این حالت، `value` عنصر {{HTMLElement("input")}} رشتهٔ خالی خواهد بود.

این رویداد قابل لغو (cancelable) نیست.

## سینتکس

از نام رویداد در روش‌هایی مانند {{domxref("EventTarget.addEventListener", "addEventListener()")}} استفاده کنید، یا یک ویژگی کنترل‌کننده رویداد (event handler) تنظیم کنید.

```js-nolint
addEventListener("search", (event) => { })

onsearch = (event) => { }
```

## نوع رویداد

یک {{domxref("Event")}} عمومی.

## مثال‌ها

```js
// addEventListener version
const input = document.querySelector('input[type="search"]');

input.addEventListener("search", () => {
  console.log(`The term searched for was ${input.value}`);
});
```

```js
// onsearch version
const input = document.querySelector('input[type="search"]');

input.onsearch = () => {
  console.log(`The term searched for was ${input.value}`);
};
```

## مشخصات

این رویداد بخشی از هیچ مشخصاتی نیست.

## سازگاری مرورگر

{{Compat}}