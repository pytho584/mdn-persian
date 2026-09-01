---
title: "DocumentFragment: append() method"
source: "https://developer.mozilla.org/en-US/docs/Web/API/DocumentFragment/append"
---

---
title: "DocumentFragment: append() method"
short-title: append()
slug: Web/API/DocumentFragment/append
page-type: web-api-instance-method
browser-compat: api.DocumentFragment.append
---

{{APIRef("DOM")}}

متد **`DocumentFragment.append()`** مجموعه‌ای از اشیاء {{domxref("Node")}} یا رشته‌ها را پس از آخرین فرزندِ قطعه سند (document fragment) درج می‌کند. رشته‌ها به‌صورت گره‌های متنی معادل ({{domxref("Text")}}) درج می‌شوند.

این متد یک فرزند به `DocumentFragment` اضافه می‌کند. برای افزودن به یک عنصر دلخواه در درخت DOM، به {{domxref("Element.append()")}} مراجعه کنید.

## نحو (Syntax)

```js-nolint
append(param1)
append(param1, param2)
append(param1, param2, /* …, */ paramN)
```

### پارامترها

- `param1`، …, `paramN`
  - : مجموعه‌ای از اشیاء {{domxref("Node")}} یا رشته‌ها که باید درج شوند.

### مقدار بازگشتی

هیچ ({{jsxref("undefined")}}).

### استثناها

- `HierarchyRequestError` {{DOMxRef("DOMException")}}
  - : زمانی پرتاب می‌شود که گره نتواند در نقطه مشخص‌شده از سلسله‌مراتب درج شود.

## مثال‌ها

### افزودن یک عنصر به قطعه سند

```js
let fragment = new DocumentFragment();
let div = document.createElement("div");
fragment.append(div);

fragment.children; // HTMLCollection [<div>]
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- {{domxref("DocumentFragment.prepend()")}}
- {{domxref("Element.append()")}}