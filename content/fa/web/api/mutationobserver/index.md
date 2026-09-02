---
title: "MutationObserver"
---

---
title: MutationObserver
slug: Web/API/MutationObserver
page-type: web-api-interface
browser-compat: api.MutationObserver
---

{{APIRef("DOM WHATWG")}}

رابط **`MutationObserver`** امکان نظارت بر تغییراتی را فراهم می‌کند که در درخت [DOM](/en-US/docs/Web/API/Document_Object_Model) انجام می‌شوند. این رابط به‌عنوان جایگزینی برای ویژگی قدیمی [Mutation Events](/en-US/docs/Web/API/MutationEvent) طراحی شده است که بخشی از مشخصات DOM3 Events بود.

## سازنده

- {{domxref("MutationObserver.MutationObserver", "MutationObserver()")}}
  - : یک شیء `MutationObserver` جدید ایجاد و بازمی‌گرداند که هنگام وقوع تغییرات در DOM، یک تابع callback مشخص را فراخوانی می‌کند.

## متدهای نمونه

- {{domxref("MutationObserver.disconnect()", "disconnect()")}}
  - : دریافت اعلان‌های بیشتر توسط نمونهٔ `MutationObserver` را متوقف می‌کند، مگر اینکه دوباره {{domxref("MutationObserver.observe", "observe()")}} فراخوانی شود.

- {{domxref("MutationObserver.observe()", "observe()")}}
  - : `MutationObserver` را طوری پیکربندی می‌کند که از طریق تابع callback خود، وقتی تغییرات DOM مطابق با گزینه‌های داده‌شده رخ دهد، شروع به دریافت اعلان‌ها کند.

- {{domxref("MutationObserver.takeRecords()", "takeRecords()")}}
  - : همهٔ اعلان‌های در انتظار را از صف اعلان‌های `MutationObserver` حذف می‌کند و آن‌ها را در یک {{jsxref("Array")}} جدید از اشیاء {{domxref("MutationRecord")}} بازمی‌گرداند.

## مثال

مثال زیر از [این پست وبلاگ](https://hacks.mozilla.org/2012/05/dom-mutationobserver-reacting-to-dom-changes-without-killing-browser-performance/) اقتباس شده است.

```js
// Select the node that will be observed for mutations
const targetNode = document.getElementById("some-id");

// Options for the observer (which mutations to observe)
const config = { attributes: true, childList: true, subtree: true };

// Callback function to execute when mutations are observed
const callback = (mutationList, observer) => {
  for (const mutation of mutationList) {
    if (mutation.type === "childList") {
      console.log("A child node has been added or removed.");
    } else if (mutation.type === "attributes") {
      console.log(`The ${mutation.attributeName} attribute was modified.`);
    }
  }
};

// Create an observer instance linked to the callback function
const observer = new MutationObserver(callback);

// Start observing the target node for configured mutations
observer.observe(targetNode, config);

// Later, you can stop observing
observer.disconnect();
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref('PerformanceObserver')}}
- {{domxref('ResizeObserver')}}
- {{domxref('IntersectionObserver')}}
- [یک مرور کوتاه](https://developer.chrome.com/blog/detect-dom-changes-with-mutation-observers/)
- [یک بحث عمیق‌تر](https://hacks.mozilla.org/2012/05/dom-mutationobserver-reacting-to-dom-changes-without-killing-browser-performance/)
- [یک اسکرین‌کست از رافائل واینستین، توسعه‌دهنده کرومیوم](https://www.youtube.com/watch?v=eRZ4pO0gVWw)