---
title: "Event: defaultPrevented property"
short-title: defaultPrevented
slug: Web/API/Event/defaultPrevented
page-type: web-api-instance-property
browser-compat: api.Event.defaultPrevented
---

{{APIRef("DOM")}}{{AvailableInWorkers}}

ویژگی فقط‌خواندنی **`defaultPrevented`** از رابط {{domxref("Event")}} یک مقدار بولی برمی‌گرداند که نشان می‌دهد آیا فراخوانی {{ domxref("Event.preventDefault()") }} رویداد را لغو کرده است یا خیر.

## مقدار

یک مقدار بولی، که `true` نشان می‌دهد که عملکرد پیش‌فرض {{glossary("user agent")}} (عامل کاربر) جلوگیری شده است، و `false` نشان می‌دهد که این کار انجام نشده است.

## مثال

این مثال تلاش برای بازدید از پیوندهای دو عنصر {{htmlElement("a")}} را ثبت می‌کند. از جاوااسکریپت برای جلوگیری از کار کردن پیوند دوم استفاده شده است.

### HTML

```html
<p><a id="link1" href="#link1">Visit link 1</a></p>
<p><a id="link2" href="#link2">Try to visit link 2</a> (you can't)</p>
<p id="log"></p>
```

### JavaScript

```js
function stopLink(event) {
  event.preventDefault();
}

function logClick(event) {
  const log = document.getElementById("log");

  if (event.target.tagName === "A") {
    log.innerText = event.defaultPrevented
      ? `Sorry, but you cannot visit this link!\n${log.innerText}`
      : `Visiting link…\n${log.innerText}`;
  }
}

const a = document.getElementById("link2");
a.addEventListener("click", stopLink);
document.addEventListener("click", logClick);
```

### نتیجه

{{EmbedLiveSample("Example")}}

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}