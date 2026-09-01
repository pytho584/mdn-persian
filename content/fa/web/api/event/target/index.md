---
title: "Event: target property"
short-title: target
slug: Web/API/Event/target
page-type: web-api-instance-property
browser-compat: api.Event.target
---

{{APIRef("DOM")}}{{AvailableInWorkers}}

ویژگی فقط‑خواندنی **`target`** در رابط {{domxref("Event")}} ارجاعی به شیئی است که رویداد به آن ارسال شده است. این ویژگی با {{domxref("Event.currentTarget")}} تفاوت دارد زمانی که تابع‌گردان رویداد در مرحله‌ی حباب یا گرفتن رویداد فراخوانی می‌شود.

## مقدار

{{domxref("EventTarget")}} مرتبط.

## مثال

از ویژگی `event.target` می‌توان برای پیاده‌سازی **تفویض رویداد** استفاده کرد.

```js
// ساخت یک لیست
const ul = document.createElement("ul");
document.body.appendChild(ul);

const li1 = document.createElement("li");
const li2 = document.createElement("li");
ul.appendChild(li1);
ul.appendChild(li2);

function hide(evt) {
  // evt.target به عنصر <li> کلیک‌شده اشاره دارد
  // این با evt.currentTarget که در این زمینه به <ul> والد اشاره می‌کند متفاوت است
  evt.target.style.visibility = "hidden";
}

// الصاق شنونده به لیست
// این شنونده هنگام کلیک روی هر <li> فعال می‌شود
ul.addEventListener("click", hide);
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [یادگیری: حباب رویداد](/en-US/docs/Learn_web_development/Core/Scripting/Event_bubbling)