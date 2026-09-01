---
title: "Document: readyState property"
short-title: readyState
slug: Web/API/Document/readyState
page-type: web-api-instance-property
browser-compat: api.Document.readyState
---

{{APIRef("DOM")}}

ویژگی **`Document.readyState`** وضعیت بارگذاری {{domxref("document")}} را توصیف می‌کند.
هنگامی که مقدار این ویژگی تغییر می‌کند، رویداد {{domxref("Document/readystatechange_event", "readystatechange")}} روی شیء {{domxref("document")}} فعال می‌شود.

## مقدار

`readyState` یک سند می‌تواند یکی از موارد زیر باشد:

- `loading`
  - : {{domxref("document")}} هنوز در حال بارگذاری است (یعنی تجزیه‌کننده HTML هنوز در حال کار است).
- `interactive`
  - : سند تجزیه شده است، اما زیرمنابعی مانند اسکریپت‌های {{domxref("HTMLScriptElement/defer", "deferred", "", "nocode")}} و [ماژول](/en-US/docs/Web/JavaScript/Guide/Modules)، تصاویر، برگه‌های سبک و فریم‌ها هنوز در حال بارگذاری هستند. هنگامی که به این حالت برسد و اسکریپت‌های معوق و ماژول اجرا شوند، رویداد {{domxref("Document/DOMContentLoaded_event", "DOMContentLoaded")}} فعال می‌شود.
- `complete`
  - : سند و تمام زیرمنابع بارگذاری شده‌اند. این حالت نشان می‌دهد که رویداد {{domxref("Window/load_event", "load")}} به زودی فعال می‌شود.

## مثال‌ها

### حالت‌های مختلف آمادگی

```js
switch (document.readyState) {
  case "loading":
    // سند در حال بارگذاری است.
    break;
  case "interactive": {
    // سند بارگذاری شده است و می‌توانیم به عناصر DOM دسترسی داشته باشیم.
    // زیرمنابعی مانند اسکریپت‌ها، تصاویر، برگه‌های سبک و فریم‌ها هنوز در حال بارگذاری هستند.
    const span = document.createElement("span");
    span.textContent = "A <span> element.";
    document.body.appendChild(span);
    break;
  }
  case "complete":
    // صفحه کاملاً بارگذاری شده است.
    console.log(
      `The first CSS rule is: ${document.styleSheets[0].cssRules[0].cssText}`,
    );
    break;
}
```

### readystatechange به عنوان جایگزینی برای رویداد DOMContentLoaded

```js
// جایگزین رویداد DOMContentLoaded
document.onreadystatechange = () => {
  if (document.readyState === "interactive") {
    initApplication();
  }
};
```

### readystatechange به عنوان جایگزینی برای رویداد load

```js
// جایگزین رویداد load
document.onreadystatechange = () => {
  if (document.readyState === "complete") {
    initApplication();
  }
};
```

### readystatechange به عنوان شنونده رویداد برای درج یا تغییر DOM قبل از DOMContentLoaded

```js
document.addEventListener("readystatechange", (event) => {
  if (event.target.readyState === "interactive") {
    initLoader();
  } else if (event.target.readyState === "complete") {
    initApp();
  }
});
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- رویدادهای مرتبط:
  - {{domxref("Document/readystatechange_event", "readystatechange")}}
  - {{domxref("Document/DOMContentLoaded_event", "DOMContentLoaded")}}
  - {{domxref("Window/load_event", "load")}}