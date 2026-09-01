---
title: "Element: activeViewTransition property"
short-title: activeViewTransition
slug: Web/API/Element/activeViewTransition
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.Element.activeViewTransition
---

{{APIRef("View Transition API")}}{{SeeCompatTable}}

ویژگی فقط‌خواندنی **`activeViewTransition`** در رابط {{domxref("Element")}} یک نمونه از {{domxref("ViewTransition")}} را برمی‌گرداند که نمایانگر [view transition](/en-US/docs/Web/API/View_Transition_API) (انتقال نما) فعال فعلی روی یک عنصر است. این ویژگی یک روش یکپارچه برای دسترسی به یک [view transition با دامنه عنصر](/en-US/docs/Web/API/View_Transition_API/Using_element-scoped) (element-scoped view transition) فعال فراهم می‌کند، بدون نیاز به ذخیره یک مرجع به آن برای استفاده بعدی.

همچنین می‌توان یک {{domxref("ViewTransition")}} با دامنه عنصر را از طریق مقدار بازگشتی {{domxref("Element.startViewTransition()")}} نیز به دست آورد.

## مقدار

یک {{domxref("ViewTransition")}} یا `null` اگر عنصر هیچ view transition فعالی نداشته باشد.

## مثال‌ها

### استفاده پایه

این قطعه کد نشان می‌دهد که چگونه از `activeViewTransition` برای دریافت یک مرجع به یک view transition در حال انجام استفاده کنید.

```js
const myElement = document.querySelector(".my-element");

// ...

function handleVT() {
  const vt = myElement.startViewTransition(() => {
    updateDOMSomehow();
  });
}

// Returns a reference to vt if the transition is still ongoing
myElement.activeViewTransition;
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- {{domxref("Element.startViewTransition()")}}
- {{domxref("Document.activeViewTransition")}}
- [استفاده از view transitions با دامنه عنصر](/en-US/docs/Web/API/View_Transition_API/Using_element-scoped)
- [API انتقال نما](/en-US/docs/Web/API/View_Transition_API)
- {{domxref("ViewTransition")}}