---
title: NavigationTransition
slug: Web/API/NavigationTransition
page-type: web-api-interface
browser-compat: api.NavigationTransition
---

{{APIRef("Navigation API")}}

رابطِ **`NavigationTransition`** از {{domxref("Navigation API", "Navigation API", "", "nocode")}} یک ناوبریِ در حال انجام را نمایش می‌دهد؛ ناوبری‌ای که هنوز به مرحلهٔ {{domxref("Navigation/navigatesuccess_event", "navigatesuccess")}} یا {{domxref("Navigation/navigateerror_event", "navigateerror")}} نرسیده است.

از طریق ویژگی {{domxref("Navigation.transition")}} قابل دسترسی است.
توجه داشته باشید که این ویژگی فقط تا زمانی مقدار دارد که هندلر [`intercept()`](/en-US/docs/Web/API/NavigateEvent/intercept) هنوز به نتیجه نرسیده باشد (یعنی هنگام [رهگیری ناوبری](/en-US/docs/Web/API/Navigation/navigate_event#handling_a_navigation_using_intercept))؛ در غیر این صورت مقدار آن `null` است.

{{InheritanceDiagram}}

## ویژگی‌های نمونه

- {{domxref("NavigationTransition.committed", "committed")}} {{ReadOnlyInline}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند که وقتی {{domxref("Navigation.currentEntry")}} به‌روزرسانی می‌شود و نشانی وب جدید در مرورگر نمایش داده می‌شود، برآورده می‌شود؛ این یعنی ناوبری به‌عنوان قطعی‌شده (committed) علامت‌گذاری می‌گردد.
- {{domxref("NavigationTransition.finished", "finished")}} {{ReadOnlyInline}}
  - : یک {{jsxref("Promise")}} برمی‌گرداند که هم‌زمان با رویداد {{domxref("Navigation/navigatesuccess_event", "navigatesuccess")}} برآورده می‌شود یا هم‌زمان با رویداد {{domxref("Navigation/navigateerror_event", "navigateerror")}} رد می‌شود.
- {{domxref("NavigationTransition.from", "from")}} {{ReadOnlyInline}}
  - : یک {{domxref("NavigationHistoryEntry")}} برمی‌گرداند که انتقال از آن آغاز شده است.
- {{domxref("NavigationTransition.navigationType", "navigationType")}} {{ReadOnlyInline}}
  - : نوع ناوبریِ در حال انجام را برمی‌گرداند.
- {{domxref("NavigationTransition.to", "to")}} {{ReadOnlyInline}} {{Experimental_Inline}}
  - : یک {{domxref("NavigationDestination")}} برمی‌گرداند که ناوبری به سمت آن انجام می‌شود.

## مثال‌ها

```js
async function cleanupNavigation() {
  await navigation.transition.finished;
  // Navigation has completed successfully
  // Cleanup any ongoing monitoring
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}

## همچنین ببینید

- [مسیریابی مدرن سمت کلاینت: Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [سند توضیحی Navigation API](https://github.com/WICG/navigation-api/blob/main/README.md)
- [دموی زندهٔ Navigation API](https://mdn.github.io/dom-examples/navigation-api/) ([مشاهدهٔ سورس دمو](https://github.com/mdn/dom-examples/tree/main/navigation-api))