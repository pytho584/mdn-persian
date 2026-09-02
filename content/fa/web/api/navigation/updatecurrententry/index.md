---
title: "Navigation: updateCurrentEntry() method"
short-title: updateCurrentEntry()
slug: Web/API/Navigation/updateCurrentEntry
page-type: web-api-instance-method
browser-compat: api.Navigation.updateCurrentEntry
---

{{APIRef("Navigation API")}}

متد **`updateCurrentEntry()`** از رابط {{domxref("Navigation")}}، `state` مربوط به {{domxref("Navigation.currentEntry","currentEntry")}} را به‌روزرسانی می‌کند؛ در مواردی استفاده می‌شود که تغییر وضعیت مستقل از یک پیمایش (navigation) یا بارگذاری مجدد صفحه باشد.

## Syntax

```js-nolint
updateCurrentEntry(options)
```

### پارامترها

- `options`
  - : یک شیء گزینه‌ها شامل خصوصیات زیر:
    - `state`
      - : اطلاعات تعریف‌شده توسط توسعه‌دهنده که پس از تکمیل پیمایش در {{domxref("NavigationHistoryEntry")}} مرتبط ذخیره می‌شود و از طریق {{domxref("NavigationHistoryEntry.getState", "getState()")}} قابل بازیابی است. این می‌تواند هر نوع داده‌ای باشد. برای مثال، ممکن است بخواهید تعداد بازدیدهای صفحه را برای اهداف تحلیلی ذخیره کنید، یا جزئیات وضعیت رابط کاربری را ذخیره کنید تا نمایش دقیقاً همان‌طور که کاربر آن را ترک کرده بود، بازسازی شود. هر داده‌ای که در `state` ذخیره می‌شود باید [قابل شبیه‌سازی ساختاریافته](/en-US/docs/Web/API/Web_Workers_API/Structured_clone_algorithm) باشد.

### مقدار بازگشتی

هیچ (`undefined`).

### استثناها

- `DataCloneError` {{domxref("DOMException")}}
  - : اگر پارامتر `state` شامل مقادیری باشد که قابل شبیه‌سازی ساختاریافته نیستند، پرتاب می‌شود.
- `InvalidStateError` {{domxref("DOMException")}}
  - : اگر {{domxref("Navigation.currentEntry")}} برابر با `null` باشد، یعنی هیچ ورودی تاریخچه جاری وجود نداشته باشد، پرتاب می‌شود. این حالت برای مثال زمانی رخ می‌دهد که صفحه فعلی `about:blank` باشد.

## مثال‌ها

می‌توانید از چیزی شبیه به کد زیر برای به‌روزرسانی وضعیت باز/بسته بودن یک عنصر {{htmlelement("details")}} استفاده کنید تا وضعیت هنگام بارگذاری مجدد صفحه یا بازگشت از جای دیگر بازیابی شود.

```js
detailsElem.addEventListener("toggle", () => {
  navigation.updateCurrentEntry({ state: { detailOpen: detailsElem.open } });
});
```

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## جستارهای وابسته

- [مسیریابی مدرن سمت کلاینت: Navigation API](https://developer.chrome.com/docs/web-platform/navigation-api/)
- [توضیح‌دهنده Navigation API](https://github.com/WICG/navigation-api/blob/main/README.md)