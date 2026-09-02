---
title: "IntersectionObserver: unobserve() method"
---

---
title: "IntersectionObserver: unobserve() method"
short-title: unobserve()
slug: Web/API/IntersectionObserver/unobserve
page-type: web-api-instance-method
browser-compat: api.IntersectionObserver.unobserve
---

{{APIRef("Intersection Observer API")}}

متد **`unobserve()`** در رابط {{domxref("IntersectionObserver")}} به `IntersectionObserver` دستور می‌دهد تا مشاهدهٔ عنصر هدف مشخص‌شده را متوقف کند.

## نحو

```js-nolint
unobserve(target)
```

### پارامترها

- `target`
  - : عنصری از نوع {{domxref("Element")}} که باید از مشاهده خارج شود. اگر عنصر مشخص‌شده در حال مشاهده نباشد، این متد هیچ کاری انجام نمی‌دهد و هیچ استثنایی پرتاب نمی‌شود.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

## مثال‌ها

این قطعه‌کد نشان می‌دهد که یک observer ساخته می‌شود، یک عنصر تحت مشاهده قرار می‌گیرد و سپس مشاهدهٔ آن متوقف می‌شود.

```js
const observer = new IntersectionObserver(callback);
observer.observe(document.getElementById("elementToObserve"));

// …

observer.unobserve(document.getElementById("elementToObserve"));
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [Intersection Observer API](/en-US/docs/Web/API/Intersection_Observer_API)
- {{domxref("IntersectionObserver.observe()")}}